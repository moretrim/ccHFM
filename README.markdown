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

Releases are save compatible across patch releases for a given minor version. For instance 0.2.0,
0.2.1, and 0.2.4 would all be save compatible with one another.

[The history of editorial changes is collated separately.](./Editorial.markdown#history)

### 0.2

The 0.2 series of releases is based on [HFM 1.27I]. It is **not** backward compatible with it.

#### 0.2.0-dev (in development)

##### Bugfixes

- Add a guard condition to the “Establish the Karafuto Prefecture“ decision ([#28], pending
  [HFM/#164]).

  [#28]: https://github.com/moretrim/PFH/pull/28
  [HFM/#164]: https://github.com/SighPie/HFM/pull/164

- Restrict “Restore Democracy in South America“ decision ([#42], pending [HFM/#168]).

  [#42]: https://github.com/moretrim/PFH/pull/42
  [HFM/#168]: https://github.com/SighPie/HFM/pull/168

- Leave Ryukyu independent during Meiji Restoration ([#51], pending [HFM/#169]).

  [#51]: https://github.com/moretrim/PFH/pull/51
  [HFM/#169]: https://github.com/SighPie/HFM/pull/169

- Prevent the Papal States (aka Lazio aka the Roman Republic) from being outright annexed when Italy
  forms by event (“Il Risorgimento”). They instead get a say into the matter, and can challenge
  Italy ([#19], [HPM/#3] + [HPM/93c5ca], pending [HFM/#163]).

  [#19]: https://github.com/moretrim/PFH/issues/19
  [HPM/#3]: https://github.com/arkhometha/Historical-Project-Mod/pull/3
  [HPM/93c5ca]: https://github.com/arkhometha/Historical-Project-Mod/commit/93c5ca17481d738a3dba84581be258b28343ffda
  [HFM/#163]: https://github.com/SighPie/HFM/pull/163

- Preserve the state religion of the Heavenly Kingdom upon Westernisation ([#40], pending
  [HFM/#172]).

  [#40]: https://github.com/moretrim/PFH/issues/40
  [HFM/#172]: https://github.com/SighPie/HFM/pull/172

- Remove correct Basotho cores in Mfecane Matabele ([HFM/#171], [HPM/#131]).

  [HFM/#171]: https://github.com/SighPie/HFM/issues/171
  [HPM/#131]: https://github.com/arkhometha/Historical-Project-Mod/pull/131

- Correct requirements of the “Occupation of the Congo Basin” decision, resolving ineffective use
  ([#26], pending [HFM/#174]).

  [#26]: https://github.com/moretrim/PFH/issues/26
  [HFM/#174]: https://github.com/SighPie/HFM/pull/174

- Really release Ezo when choosing to play as them (pending [HFM/#176], [HPM/#161]).

  [HFM/#176]: https://github.com/SighPie/HFM/pull/176
  [HPM/#161]: https://github.com/arkhometha/Historical-Project-Mod/pull/161

##### Tweaks

- Flag tweaks for Korea under a monarchy ([4f0f02], pending [HFM/#166]).

  [4f0f02]: https://github.com/moretrim/PFH/commit/4f0f02e18710d29ba5d8b98615b186ec98648619
  [HFM/#166]: https://github.com/SighPie/HFM/pull/166

- Text fixes for the France minimod, German Namibia, and a couple other things ([906735], pending
  [HFM/#170]).

  [906735]: https://github.com/moretrim/PFH/commit/9067354d70610e4f12644ef68f479ac109827172
  [HFM/#170]: https://github.com/SighPie/HFM/pull/170

### [0.1](https://github.com/moretrim/PFH/tree/v0.1)

The 0.1 series of releases is based on [HFM 1.27I] and is backward compatible with it.

#### [0.1.1](https://github.com/moretrim/PFH/tree/v0.1.1)

##### Tweaks

- Reduce the amount of notifications from the Witwatersrand Gold Rush ([#7], pending [HFM/#162]).

  [#7]: https://github.com/moretrim/PFH/pull/7
  [HFM/#162]: https://github.com/SighPie/HFM/pull/162

- Flag tweaks:

  * enable the flag of the British dominion of Newfoundland ([#5])
  * use the correct flag for uncivilised or absolute Dahomey ([#6])

  [#5]: https://github.com/moretrim/PFH/pull/5
  [#6]: https://github.com/moretrim/PFH/pull/6

#### [0.1.0](https://github.com/moretrim/PFH/tree/v0.1.0)

##### Ported features

- Make colonial railroading an option decision (PR [HFM/#157])

  [HFM/#157]: https://github.com/SighPie/HFM/pull/157

##### Ported bugfixes

- PR [HFM/#141]\:

  > At line 518 (ENG choice to not intervene) I've added `set_global_flag = anglo_persian_war` to
  > signify the crisis has occurred, otherwise the event will continuously spawn.

  [HFM/#141]: https://github.com/SighPie/HFM/pull/141

[HFM 1.27I]: https://github.com/SighPie/HFM/tree/38ca75c40063e08cbf696140e0ea68d76e6ace9d
