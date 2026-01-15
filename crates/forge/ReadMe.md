# Tracers compatibility

## Phoenix tracers for forge

Any Phoenix tracer relying on `TracingInspector` under the hood can be used on forge too. 
There are two blocks of code marked with a `@tracing` comment that can be used to enable and configure a tracer.
**N.B.** Configuration can be copy-pasted from the Phoenix repo.

Reinstall forge after the changes are made:
```
cargo install --path ./crates/forge --profile release --force --locked
```

Run the test with `-vvv` or a higher verbosity level. 


### Other tracers

If need be, more tracers can be supported by adding an extra tracer to `InspectorStack` and updating its `Inspector` implementation.


## Forge tracer for Phoenix

Forge tracer is compatible with Phoenix, but it doesn't make much sense to use it without vizualisation which is rather inconvenient to import to Phoenix.
If it becomes necessary at some point, `@trace_visualization` comments indicate the code to be imported.
