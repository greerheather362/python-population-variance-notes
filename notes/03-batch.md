# Ordered batch processing for Measure population variance

`batch.py` accepts an outer JSON array containing separate inputs. This is an extra level of nesting when `solve` itself accepts a list. It produces one result envelope per item, preserving input order and zero-based position.

```sh
python3 batch.py < samples/batch.json
```

The batch covers these three input/output pairs:

## Case 1

Input:
```json
[
  1,
  2,
  3
]
```

Result:
```json
0.6666666666666666
```

## Case 2

Input:
```json
[
  5
]
```

Result:
```json
0
```

## Case 3

Input:
```json
[
  4,
  4,
  4
]
```

Result:
```json
0
```

## Partial failures

Each successful item has `ok: true` and `result`. A failed item has `ok: false` and an exception type; later items still run. Exit status 1 means at least one item failed, while status 2 means the batch envelope itself was invalid. An empty outer array is a valid empty batch.

pvariance divides by n and describes the supplied population. Use sample variance when estimating a wider population from a sample.

The implementation processes sequentially, avoiding shared-state concurrency and keeping output order predictable. Input is limited to one MiB and 1000 items; this version materializes all results in memory. The next lesson removes that whole-batch memory requirement with line-oriented processing.
