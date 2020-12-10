---
layout: post
title:  "First Steps with BERT"
date:   2020-12-10 13:23:00 -0600
categories: nlp
---

I'm trying both BERT for the first time and I wanted to document it
using Jekyll/Github Pages, which I'm also new to.

The [README.md file on the BERT github
page](https://github.com/google-research/bert) is pretty long and
there are many variations on the BERT model provided there.  

Since data a model is not trainable or testable without data, I
started by [downloading the glue
data](https://github.com/google-research/bert#sentence-and-sentence-pair-classification-tasks). I
had to make some changes to the [download script
gist](https://gist.github.com/W4ngatang/60c2bdb54d156a41194446737ce03e2e)
that was linked in this section.  

```{bash}
python3 download_glue_data.py --data_dir glue_data --tasks all
```

Then I downloaded and unzipped a model.  There were many models provided and I
chose [the one that was "recommended",
multi_cased_L-12_H-768_A-12](https://storage.googleapis.com/bert_models/2018_11_23/multi_cased_L-12_H-768_A-12.zip)


Then I ran the commands from the README:

```{bash}
export BERT_BASE_DIR=multi_cased_L-12_H-768_A-12
export GLUE_DIR=glue_data

python run_classifier.py \
  --task_name=MRPC \
  --do_train=true \
  --do_eval=true \
  --data_dir=$GLUE_DIR/MRPC \
  --vocab_file=$BERT_BASE_DIR/vocab.txt \
  --bert_config_file=$BERT_BASE_DIR/bert_config.json \
  --init_checkpoint=$BERT_BASE_DIR/bert_model.ckpt \
  --max_seq_length=128 \
  --train_batch_size=32 \
  --learning_rate=2e-5 \
  --num_train_epochs=3.0 \
  --output_dir=/tmp/mrpc_output/
```

I realized I needed some libraries and I also ought to be in a
virtualenv:

```{bash]
mkvirtualenv bert
workon bert
pip install -r requirements.txt
```

Now trying to run the run_classifier.py script, I get the following
error:

```{bash}
Traceback (most recent call last):
  File "run_classifier.py", line 25, in <module>
    import optimization
  File "/Users/kaze7539/proj/bert/optimization.py", line 87, in <module>
    class AdamWeightDecayOptimizer(tf.train.Optimizer):
AttributeError: module 'tensorflow._api.v2.train' has no attribute 'Optimizer'

```

Googling led to [this](https://github.com/tensorflow/tensorflow/issues/30092)

so I tried import tf.keras.optimizers and changing the line 87 in
bert/optimization.py to

```{python}
class AdamWeightDecayOptimizer(tf.keras.optimizers.Optimizer):
```

That seemed to solve that problem but I got another error:

```{bash}
Traceback (most recent call last):
  File "run_classifier.py", line 29, in <module>
    flags = tf.flags
AttributeError: module 'tensorflow' has no attribute 'flags'

```

according to
[this](https://github.com/tensorflow/tensor2tensor/issues/1754) it seems like it's a version issue that can be fixed by changing line 29 to

```{python}
flags = tf.compat.v1.flags
```

but still another error:

```{bash}
Traceback (most recent call last):
  File "run_classifier.py", line 102, in <module>
    tf.flags.DEFINE_string(
AttributeError: module 'tensorflow' has no attribute 'flags'
```

To fix this there were a few lines that I changed `tf.flags` to just
`flags`


After fixing that, another error:

```{bash}
Traceback (most recent call last):
  File "run_classifier.py", line 981, in <module>
    tf.app.run()
AttributeError: module 'tensorflow' has no attribute 'app'
```

to fix, based on reading
[this](https://stackoverflow.com/questions/58258003/attributeerror-module-tensorflow-has-no-attribute-app)
change line 24 to:

```{python}
import tensorflow.compat.v1 as tf
```

New error:

```{bash}
Traceback (most recent call last):
  File "run_classifier.py", line 981, in <module>
    tf.app.run()
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/tensorflow/python/platform/app.py", line 40, in run
    _run(main=main, argv=argv, flags_parser=_parse_flags_tolerate_undef)
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/absl/app.py", line 303, in run
    _run_main(main, args)
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/absl/app.py", line 251, in _run_main
    sys.exit(main(argv))
  File "run_classifier.py", line 793, in main
    tokenization.validate_case_matches_checkpoint(FLAGS.do_lower_case,
  File "/Users/kaze7539/proj/bert/tokenization.py", line 69, in validate_case_matches_checkpoint
    raise ValueError(
```

it seems that the command I was using should be modified to

```{bash}
python run_classifier.py \
  --task_name=MRPC \
  --do_train=true \
  --do_eval=true \
  --data_dir=$GLUE_DIR/MRPC \
  --vocab_file=$BERT_BASE_DIR/vocab.txt \
  --bert_config_file=$BERT_BASE_DIR/bert_config.json \
  --init_checkpoint=$BERT_BASE_DIR/bert_model.ckpt \
  --max_seq_length=128 \
  --train_batch_size=32 \
  --learning_rate=2e-5 \
  --num_train_epochs=3.0 \
  --output_dir=/tmp/mrpc_output/ \
  --do_lower_case=false  /
```

now I'm getting an error about gfile

```{bash}
Traceback (most recent call last):
  File "run_classifier.py", line 981, in <module>
    tf.app.run()
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/tensorflow/python/platform/app.py", line 40, in run
    _run(main=main, argv=argv, flags_parser=_parse_flags_tolerate_undef)
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/absl/app.py", line 303, in run
    _run_main(main, args)
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/absl/app.py", line 251, in _run_main
    sys.exit(main(argv))
  File "run_classifier.py", line 800, in main
    bert_config = modeling.BertConfig.from_json_file(FLAGS.bert_config_file)
  File "/Users/kaze7539/proj/bert/modeling.py", line 93, in from_json_file
    with tf.gfile.GFile(json_file, "r") as reader:
AttributeError: module 'tensorflow' has no attribute 'gfile'
```

according to
[this](https://github.com/google-research/bert/issues/977) we need to
patch like this

```{python}
tf.gfile = tf.io.gfile
```

in the files that use gfile (run_classifier.py and modeling.py)


new error

```{bash}
  File "run_classifier.py", line 982, in <module>
    tf.app.run()
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/tensorflow/python/platform/app.py", line 40, in run
    _run(main=main, argv=argv, flags_parser=_parse_flags_tolerate_undef)
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/absl/app.py", line 303, in run
    _run_main(main, args)
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/absl/app.py", line 251, in _run_main
    sys.exit(main(argv))
  File "run_classifier.py", line 809, in main
    tf.gfile.MakeDirs(FLAGS.output_dir)
AttributeError: module 'tensorflow.compat.v1.io.gfile' has no attribute 'MakeDirs'
```

try changeing that line to "makedirs" (lowercase) according to [this](https://www.tensorflow.org/api_docs/python/tf/io/gfile/makedirs)


new error

```{bash}

Traceback (most recent call last):
  File "run_classifier.py", line 982, in <module>
    tf.app.run()
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/tensorflow/python/platform/app.py", line 40, in run
    _run(main=main, argv=argv, flags_parser=_parse_flags_tolerate_undef)
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/absl/app.py", line 303, in run
    _run_main(main, args)
  File "/Users/kaze7539/.virtualenvs/bert/lib/python3.8/site-packages/absl/app.py", line 251, in _run_main
    sys.exit(main(argv))
  File "run_classifier.py", line 828, in main
    is_per_host = tf.contrib.tpu.InputPipelineConfig.PER_HOST_V2
AttributeError: module 'tensorflow.compat.v1' has no attribute 'contrib'
```


Okay, this is kind of ridiculous.  I figured that instead of trying to use the compatibility layers, I actually just  need to use the older version of tensor flow which also requires an older version of python

```{bash}
rmvirtualenv bert
# update requirements to
# tensorflow == 1.14   # CPU Version of TensorFlow.
mkvirtualenv -p /usr/local/bin/python3.7  bert
workon bert
# update requirements to
# tensorflow == 1.14   # CPU Version of TensorFlow.
pip install -r requirements.text
```

this seems to be working now but there was a subset of the glue data
that we need to download separately for legal reasons.  My patience
was running thin so I tried a different task, CoLA (corpus of
linguistic acceptability):

```{bash}
python run_classifier.py \
  --task_name=COLA \
  --do_train=true \
  --do_eval=true \
  --data_dir=$GLUE_DIR/CoLA \
  --vocab_file=$BERT_BASE_DIR/vocab.txt \
  --bert_config_file=$BERT_BASE_DIR/bert_config.json \
  --init_checkpoint=$BERT_BASE_DIR/bert_model.ckpt \
  --max_seq_length=128 \
  --train_batch_size=32 \
  --learning_rate=2e-5 \
  --num_train_epochs=3.0 \
  --output_dir=/tmp/mrpc_output/ \
  --do_lower_case=false  /
```

The fan turned on so it seems to be running.  To be continued...

