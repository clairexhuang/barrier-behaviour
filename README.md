# Evaluation of Barrier Behaviour

This repository contains the configuration files and raw running script result files from my 2022 summer project (supervised by Professor Steve Blackburn).

These are the instructions on how to use refined measurement framework that I used for this project. It requires a full and correct implementation of the barrier that is being measured in MMTk. Here, we will use the object barrier, which is already implemented in the MMTk: 
1. Set up running-ng using the instructions on https://running-ng.zcai.org/.
2. Set up the OpenJDK binding of MMTk using the tutorial: https://www.mmtk.io/mmtk-core/tutorial/preliminaries/set_up.html. Make sure to set the path to the mmtk-core repo.
3. Navigate to mmtk-core/src/plan/generational/mod.rs.
4. Set `FULL_NURSERY_GC` to `true` (L40) and `ACTIVE_BARRIER` to `BarrierSelector::NoBarrier` (L38). Produce an MMTk build using the tutorial instructions in step 2 and rename the build to `no-bar`. 
5. Keep `FULL_NURSERY_GC` as `true` (L40) and change `ACTIVE_BARRIER` to `BarrierSelector::ObjectBarrier` (L38). Produce an MMTk build using the tutorial instructions in step 2 and rename the build to `ob-bar`.
6. Use the running scripts to take the barrier measurements. A configuration file template is provided at https://github.com/clairexhuang/barrier-behaviour/blob/master/measurement-template.yml.

Note: If the running scripts fail, it may be necessary to change this line https://github.com/mmtk/mmtk-core/blob/master/src/plan/generational/mod.rs#L60 to be 'if true' due to an issue with the side-metadata layout in the master branch. 