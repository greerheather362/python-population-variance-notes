# Measure population variance: implementation

## What the example does

pvariance divides by n and describes the supplied population. Use sample variance when estimating a wider population from a sample.

The public function is `solve(value)`. The JSON input contract can be seen in this concrete example:

```json
[
  1,
  2,
  3
]
```

Expected result:

```json
0.6666666666666666
```

Run `python3 example.py` for the Python representation of the result. `solution.py` contains the full implementation and can also be imported by another script.

## Scope

The function implements exactly the behavior described above. It does not perform network or filesystem access. Python exceptions indicate unsupported input; the next lesson turns them into a command-line error response. Review the limitations before reusing it in an application.
