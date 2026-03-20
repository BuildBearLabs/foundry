# Running forge tests with Phoenix

Phoenix doesn't allow direct interaction with the EVM, only transactions, so a kind of compatibility layer is required to port the test. This fork's aim is to generate a `bbOut.json` file for any test run; it contains all the info necessary to reproduce the test:
- initial blockchain state & test data (under the `data` key, `db` and `test` respectively);
- a list of all cheatcodes being used for the run;
- all external data being used by the cheatcodes (e.g. files and envs).

**N.B.** Phoenix cheatcodes affect only one transaction / call, so all test steps must be wrapped into a single transaction / call


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
