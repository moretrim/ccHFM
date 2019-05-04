Piggy Flavoured HFM
===================

A custom-tailored [HFM].

[HFM]: https://github.com/SighPie/HFM

[Obtain the latest release here.][RELEASE]

[RELEASE]: https://github.com/moretrim/PFH/releases/latest

Release history
===============

The 0.1.x series of releases is based on [HFM 1.27F Beta] and is backward compatible with it. This series comes with a
few flag tweaks as well the following:

[HFM 1.27F Beta]: https://github.com/SighPie/HFM/tree/38ca75c40063e08cbf696140e0ea68d76e6ace9d

0.1.1-dev (in development)
--------------------------

### Bugfixes

- An uncivilized country can only lose one port per unequal treaty they've been forced to sign.

  This can result in races, e.g. if two countries fighting the same uncivilized target peace out in quick succession. AI
  countries should be prompt enough that nothing unexpected happens. Human players finding themselves in such a
  situation are advised to pause when they win the war and to pick their port as soon as possible.

### Ported bugfixes

- Fix conflicting Treaty Port event triggers ([HFM/#117])

[HFM/#117]: https://github.com/SighPie/HFM/pull/117

0.1.0
-----

### Ported features

- Make colonial railroading an option decision ([HFM/#157])

[HFM/#157]: https://github.com/SighPie/HFM/pull/157

### Ported bugfixes

- [HFM/#141]\:

  > At line 518 (ENG choice to not intervene) I've added `set_global_flag = anglo_persian_war` to signify the crisis has
  > occurred, otherwise the event will continuously spawn.

[HFM/#141]: https://github.com/SighPie/HFM/pull/141
