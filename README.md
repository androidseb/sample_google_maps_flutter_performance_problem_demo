# Sample Google Maps Flutter Performance Problem Demo

A demo project to illustrate the issues mentioned in this github issue: https://github.com/flutter/flutter/issues/146041

This project was copied from [the official Google Maps example project](https://github.com/flutter/packages/tree/main/packages/google_maps_flutter/google_maps_flutter/example) and reduced to the strict minimum to demonstrate how updating a single marker in a large dataset (about 12k markers in this example) poses performance problems.

The majority of the custom code for the demo can be found under the file `lib/delta_performance_problem.dart`.
