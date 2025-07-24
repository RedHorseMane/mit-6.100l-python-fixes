## Fix: `unittest.makeSuite()` removal in Python 3.13

### Background
MIT's 6.100L Problem Set 4 test harness (2022 edition) uses  
```python
suite = unittest.makeSuite(TestPS4BC)
```

unittest.makeSuite() was deprecated in Python 3.11 and removed in Python 3.13, so running the file on modern Python raises:
```python
AttributeError: module 'unittest' has no attribute 'makeSuite'
```

(See Python 3.13 “What’s New” – removal list)  ￼

One-line patch

Replace the call with the loader API that has existed since Python 2.7:

```python
suite = unittest.TestLoader().loadTestsFromTestCase(TestPS4BC)
```

This is completely backward-compatible and works on every Python ≥ 3.6.
A similar change is already propagating through open-source projects (e.g. conda-forge/pycosat).  ￼

Where to look
  * ORIGINAL_test_ps4bc_student.py – verbatim upstream file
  * FIXED_test_ps4bc_student.py – ready-to-run on Python 3.10-3.13
  * CHANGELOG.md – list of edits & why they were needed 
### Running the Test
```python 
python FIXED_test_ps4bc_student.py
```

or, inside the folder: 

```python
python -m unittest FIXED_test_ps4bc_student
```
