# Sample Google Maps Flutter Performance Problem Demo

A demo project to illustrate the issues mentioned in this github issue: https://github.com/flutter/flutter/issues/146041

This project was copied from [the official Google Maps example project](https://github.com/flutter/packages/tree/main/packages/google_maps_flutter/google_maps_flutter/example) and reduced to the strict minimum to demonstrate how updating a single marker in a large dataset (about 12k markers in this example) poses performance problems.

The majority of the custom code for the demo can be found under the file `lib/delta_performance_problem.dart`.

Steps to reproduce the issue:

* Set the an env variable called `MAPS_API_KEY` containing a valid Google Maps API key for Android
* Launch an Android device / emulator
* Launch the project on that device / emulator
* Open the dart dev performance overview
* Click "Add" a few times to add a few markers on the map
* Try clicking the markers on the map and notice how they are selected on click in a responsive manner
* Click the "AddK" button, this will add about 12 thousand markers
* Try clicking the markers on the map
    * Expected: UI remains responsive and the performance overview dev tool displays no jank
    * Actual: UI noticeably freezes each time a new marker is clicked and the performance overview displays jank

Note: that I timed the `_onMarkerTapped` method, and it seems to take less than a millisecond even with thousands of markers, so it seems this performance issue is coming from the GoogleMap widget `markers` field change.
