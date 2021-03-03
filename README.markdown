Piggy Flavoured HFM
===================

Build status:
[![Github Workflow][github-workflow-badge]][github-workflow-dashboard]

[github-workflow-badge]:
    https://github.com/moretrim/PFH/actions/workflows/ci-on-push.yaml/badge.svg
[github-workflow-dashboard]:
    https://github.com/moretrim/PFH/actions/workflows/ci-on-push.yaml
    "Github Workflows"

A custom-tailored [HFM].

[HFM]: https://github.com/SighPie/HFM

[Obtain the latest release here.][RELEASE]

[RELEASE]: https://github.com/moretrim/PFH/releases/latest

Release history
---------------

[The history of editorial changes is collated separately.][editorial]

[editorial]: Editorial.markdown

Releases are save compatible across patch releases for a given minor version. For instance 0.2.0,
0.2.1, and 0.2.4 would all be save compatible with one another.

* [0.2](#02)
* [0.1](#01)

### 0.2

The 0.2 series of releases is based on [HFM 1.27I]. It is **not** backward compatible with it.

#### 0.2.0-dev (in development)

##### Changes

- Leaders now display their personality & background all at once, together with a stat summary with
  highlights. This makes it vastly simpler for the player to figure out at a glance how good or bad
  a leader is:

  <figure>

  [![Leader selection screen][leader-selection-screen]][leader-selection-picture]

  [leader-selection-screen]:
    media/leader-selection.png?raw=true
    "Selecting a general for Austria’s third army from among many candidates"
  [leader-selection-picture]:
    media/leader-selection.png?raw=true

    <figcaption>

    Selecting a general for Austria’s third army from among many candidates. From higher up to lower
    down the list, some of the leaders that stand out:

    - Alois von Grünne: the speediest hellbent armchair general there is with +50% speed
    - Werner von Hötzendorf: a decent all-rounder with +2 attack +1 defence and a little bit extra
      as indicated by the green ‘?’ question mark (in his case, a small bonus to morale)
    - Alfons Remmele (highlighted, with tooltip): this defiant cartographer is an ever present rock
      at +3 defence and +40% speed, with some extras (in this case, small bonuses to morale and
      organisation)
    - Ludwig Held (immediately after Alois Eisner, name hidden): while he could be considered for
      the post for defence, he should not be employed on the offence due to a disappointing -2
      attack

    </figcaption
  </figure>

  The stat summary consists of the following, with appropriate colour coding:

    * **attack score, defence score, speed modifier, extras**

  Extras, if present, denote one or two remarkable modifier to organisation and/or morale—think of
  it as a tiebreaker for generals with otherwise similar stats. Leader prestige, indicated by the
  column to the left of the portrait, plays a similar role. Extras are displayed as one of the
  following from best to worst: ‘!!!’, ‘?’, blank when unremarkable, ‘¿’, ‘¡¡¡’.

  A stat is displayed as blank when neutral (e.g. no bonus to attack, no speed modifier) or
  unremarkable. Great care has been taken that stat summaries have pixel-perfect alignment with one
  another at all times in the leader selection panel, and you can think of all aggregate stats as
  being displayed in columns (e.g. for attack) as well as in leader rows.

  This change has been achieved by storing the formerly separate personalities & backgrounds of
  leaders as a single trait under the hood, which acts as a combination of the two. This does *not*
  affect how powerful generals or admirals can be, or how unlikely it is to roll e.g. a +5 attack/+5
  defence general.

  Known limitations include:
  - An inability to sort leaders in any useful order when clicking on the “Personality & Background”
    column header. Unfortunately this appears to be a base game limitation.
  - The leader list in the military country screen “leaks” tooltips to the areas just under it. This
    is a little bit disorientating when trying to use the UI elements in this area: the Create
    General/Admiral buttons, as well as the leader management checkboxes. This however doesn’t
    prevent their normal use or displaying their own tooltips. This also appears to be a base game
    limitation, when trying to fit the longer unified trait descriptions in the leader list.

- **(Experimental)** Turn the “Restore Democracy in South America” decision into a casus belli. As a
  decision, it had several flaws:

  - It had a hidden infamy cost.
  - Its requirement were not strict enough, leading to unintended wars e.g. against a communist
    European power with land in South America.
  - Even if the above were taken care of, a decision cannot accurately check that all conditions for
    a valid war are met. This is generally the case for all decisions or events that start wars, but
    is more prominent for a decision that is not a one-shot button.
  - The communist defender of the war received a free “Make Puppet” counter-CB. This lead to all
    kinds of oddities.

  The intent behind the decision is better reflected as a proper casus belli. This change is still
  labelled as experimental because it does get rid of the counter-CB of the original approach
  altogether. As a result communist governements in South America are in perpetual danger from their
  democratic neighbours.

##### Bugfixes

- Add a guard condition to the “Establish the Karafuto Prefecture“ decision ([#28], pending
  [HFM/#164]).

  [#28]: https://github.com/moretrim/PFH/pull/28
  [HFM/#164]: https://github.com/SighPie/HFM/pull/164

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

- Fixes to the “Annex Korea” decision, aiming to resolve the following two situations (pending
  [HFM/#177], [HPM/#189]):
  * late game liberation crises that would fizzle when going to war over Korea
  * Japanese conquest of Korea against the player

  [HFM/#177]: https://github.com/SighPie/HFM/pull/177
  [HPM/#189]: https://github.com/arkhometha/Historical-Project-Mod/pull/189

- Improve the Boer War call to arms to be infamy neutral (it was deducting 3 extra), and make it AI
  only. The player now gets notified of the new alliance (pending [HFM/#179]).

  [HFM/#179]: https://github.com/SighPie/HFM/pull/179

- Prevent follow-up event to “The Mysterious Lands of Guatemala” archaeological chain from granting
  prestige to non-existing countries ([8c3aa2]).

  [8c3aa2]: https://github.com/moretrim/PFH/commit/8c3aa2bed5bebfb7369cc7c5f7836304edf79a85

- Extend player protection of Neuchâtel crisis ([#76]). Note that there still are extant
  event-driven annexations of Neuchâtel, and as such it should still be considered an advanced start
  for dedicated players.

  [#76]: https://github.com/moretrim/PFH/issues/76

##### Ported bugfixes

- Fix typo in `PEACE_TIME_FACTOR_NO_GOALS` define (pending [HFM/#175]).

  [HFM/#175]: https://github.com/SighPie/HFM/pull/175

##### Tweaks

- Flag tweaks for Korea under a monarchy ([4f0f02], pending [HFM/#166]).

  [4f0f02]: https://github.com/moretrim/PFH/commit/4f0f02e18710d29ba5d8b98615b186ec98648619
  [HFM/#166]: https://github.com/SighPie/HFM/pull/166

##### Other

- 4 [editorial][] changes.

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
