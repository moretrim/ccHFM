Piggy Flavoured HFM
===================

A custom-tailored HFM.

[Obtain the latest release here.][RELEASE]

[RELEASE]: https://github.com/moretrim/PFH/releases/latest

Release history
===============

0.1.0
-----

Based on [HFM 1.27F Beta].

[HFM 1.27F Beta]: https://github.com/SighPie/HFM/tree/38ca75c40063e08cbf696140e0ea68d76e6ace9d

### Ported features

- Make colonial railroading an option decision ([HFM/#157])

[HFM/#157]: https://github.com/SighPie/HFM/pull/157

### Bugfixes

- (Partial) An uncivilized country can only lose one port per unequal treaty they've been forced to sign.

  This can result in races, e.g. if two countries fighting the same uncivilized target peace out in quick succession. AI
  countries should be prompt enough that nothing unexpected happens. Human players finding themselves in such a
  situation are advised to pause when they win the war and to pick their port as soon as possible.

### Ported bugfixes

- [HFM/#141]\:

  > At line 518 (ENG choice to not intervene) I've added `set_global_flag = anglo_persian_war` to signify the crisis has
  > occurred, otherwise the event will continuously spawn.

[HFM/#141]: https://github.com/SighPie/HFM/pull/141

- Fix conflicting Treaty Port event triggers ([HFM/#117])

[HFM/#117]: https://github.com/SighPie/HFM/pull/117
