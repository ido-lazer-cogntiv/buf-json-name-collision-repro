# buf v1.68 JSON name collision bug

Minimal reproduction for [bufbuild/buf#4477](https://github.com/bufbuild/buf/issues/4475).

`buf build` fails on proto3 enums with 2-character `[A-Z][a-z]` values (e.g. `Ab`, `Xq`), reporting false JSON name collisions.

## Reproduce

```bash
buf build .
```

### Expected

Build succeeds (as it does on buf <= 1.67.1 and on `protoc`).

### Actual (buf >= 1.68.0)

```
example.proto:8:3:enum values have the same JSON name
```
