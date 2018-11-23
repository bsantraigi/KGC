# KGC

## Run the code

### Compile C++ Operator

Go to `ndkgc/ops/__sampling`, run

```bash
cmake .
cmake --build .
```

to compile the negative sampling operator using CMake and TensorFlow.

**If you can not compile this C++ operator, please consider downgrade your TensorFlow to 1.3.**

### Download pre-trained model snapshot

Download DB50 from 

https://drive.google.com/file/d/1qw8d0LGT18D_3p2_dNmyqztkgZO4ageW/view?usp=sharing

put the DB50 dataset under `ConMask/data`.

Download pre-trained ConMask model from

https://drive.google.com/file/d/1OsSwP2LTHiPzP_gManIrjdAxUjj9nl8t/view?usp=sharing

put the snapshot directly under `ConMask/`

And use the following command under `ConMask/`:

```bash
# Closed-World Evaluation
python3 -m ndkgc.models.fcn_model_v2 checkpoint_db50_v2_dr_uniweight_2 data/dbpedia50 --force_eval --layer 3 --conv 2 --lr 1e-2 --keep_prob 0.5 --max_content 512 --pos 1 --neg 4 --noopen --neval 5000 --eval --nofilter
# Open-World Evaluation
python3 -m ndkgc.models.fcn_model_v2 checkpoint_db50_v2_dr_uniweight_2 data/dbpedia50 --force_eval --layer 3 --conv 2 --lr 1e-2 --keep_prob 0.5 --max_content 512 --pos 1 --neg 4 --open --neval 5000 --eval --filter
``` 

You can also find the DB500 dataset at 
https://drive.google.com/file/d/1Tx1gyMoj-9RkbdRvKzHYZ5EZmSrUywVF/view?usp=sharing

### Results and Analysis

Find summarized results at https://docs.google.com/spreadsheets/d/1KKZtoz1fYolANbaWvfAFvQhRWkJrQXzslxP2c7Jlh28/edit?usp=sharing

Find complete results and analysis at https://drive.google.com/open?id=1FWhHdqVImrer1CKCdZ6NgyWKDDu12DDR
