Piggy Flavoured HFM
===================

Build status:
[![travis-master][travis-master-image]](https://travis-ci.org/moretrim/PFH/branches)

[travis-master-image]: https://travis-ci.org/moretrim/PFH.svg?branch=master

A custom-tailored [HFM].

[HFM]: https://github.com/SighPie/HFM

[Obtain the latest release here.][RELEASE]

[RELEASE]: https://github.com/moretrim/PFH/releases/latest

Release history
---------------

### 0.2.0-dev (in development)

The 0.2.x series of releases is based on [HFM 1.27I]. It is **not** backward compatible with it. This series comes
with a few flag tweaks as well the following changes:

#### Bugfixes

- Add a guard condition to the 'Establish the Karafuto Prefecture' decision ([#28], pending [HFM/#164]).

  [#28]: https://github.com/moretrim/PFH/pull/28
  [HFM/#164]: https://github.com/SighPie/HFM/pull/164

- Restrict 'Restore Democracy in South America' decision ([#42], pending [HFM/#168]).

  [#42]: https://github.com/moretrim/PFH/pull/42
  [HFM/#168]: https://github.com/SighPie/HFM/pull/168

- Leave Ryukyu independent during Meiji Restoration ([#51], pending [HFM/#169]).

  [#51]: https://github.com/moretrim/PFH/pull/51
  [HFM/#169]: https://github.com/SighPie/HFM/pull/169

#### Tweaks

- Flag tweak for Korea as part of [#34] (pending [HFM/#166]).

  [#34]: https://github.com/moretrim/PFH/issues/34
  [HFM/#166]: https://github.com/SighPie/HFM/pull/166

- Text fixes for the France minimod, German Namibia, and a couple other things ([906735], pending [HFM/#170]).

  [906735]: https://github.com/moretrim/PFH/commit/9067354d70610e4f12644ef68f479ac109827172
  [HFM/#170]: https://github.com/SighPie/HFM/pull/170

### 0.1.1

The 0.1.x series of releases is based on [HFM 1.27I] and is backward compatible with it. This series comes with a
few flag tweaks as well the following changes:

[HFM 1.27I]: https://github.com/SighPie/HFM/tree/38ca75c40063e08cbf696140e0ea68d76e6ace9d

#### Tweaks

- Reduce the amount of notifications from the Witwatersrand Gold Rush ([#7], pending [HFM/#162]).

  [#7]: https://github.com/moretrim/PFH/pull/7
  [HFM/#162]: https://github.com/SighPie/HFM/pull/162

### 0.1.0

#### Ported features

- Make colonial railroading an option decision (PR [HFM/#157])

  [HFM/#157]: https://github.com/SighPie/HFM/pull/157

#### Ported bugfixes

- PR [HFM/#141]\:

  > At line 518 (ENG choice to not intervene) I've added `set_global_flag = anglo_persian_war` to signify the crisis has
  > occurred, otherwise the event will continuously spawn.

  [HFM/#141]: https://github.com/SighPie/HFM/pull/141
