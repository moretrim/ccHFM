Community Curated HFM
=====================

Build status:
[![Github Workflow][github-workflow-badge]][github-workflow-dashboard]

[github-workflow-badge]:
    https://github.com/moretrim/ccHFM/actions/workflows/ci-on-push.yaml/badge.svg
[github-workflow-dashboard]:
    https://github.com/moretrim/ccHFM/actions/workflows/ci-on-push.yaml
    "Github Workflows"

An unauthorised, unaffiliated effort to maintain [HFM].

[HFM]: https://github.com/SighPie/HFM

[Obtain the latest release here.][RELEASE]

[RELEASE]: https://github.com/moretrim/ccHFM/releases/latest

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

##### Features

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

- **(Experimental)** Turn the *Restore Democracy in South America* decision into a casus belli. As a
  decision, it had several flaws:

  - It had a hidden infamy cost.
  - Its requirement were not strict enough, leading to unintended wars e.g. against a communist
    European power with land in South America.
  - Even if the above were taken care of, a decision cannot accurately check that all conditions for
    a valid war are met. This is generally the case for all decisions or events that start wars, but
    is more prominent for a decision that is not a one-shot button.
  - The communist defender of the war received a free *Make Puppet* counter-CB. This lead to all
    kinds of oddities.

  The intent behind the decision is better reflected as a proper casus belli. This change is still
  labelled as experimental because it does get rid of the counter-CB of the original approach
  altogether. As a result communist governements in South America are in perpetual danger from their
  democratic neighbours.

##### Ported Features

- Port the dismantlement system from HPM 0.4.5. In order to make this work, a couple other
  supporting features have also been ported—these are described separately.

  Extra fixes:

  * Part of arkhometha/Historical-Project-Mod@104f7a310fbea427e82935a26d8eaf20953d6652:

    > * Increased Infamy from fighting colonies that refuse to submit during a dismantlement. It can
    >   go now up to an additional 5, depending on how bit the colony is.
    > * NNM distribution of colonies during dismantlement should now avoid countries that already
    >   refused to get more colonies.
    > * Ottoman dismantlement will now try to give Montenegro and Serbia their cores back,
    >   regardless of truce, and first. That way the region doesn't end controlled by
    >   Bosnia/Albania. Greece can also get their cores back regardless of truce IF they are not a
    >   SP/GP or if their sphere master/overlord has a truce with the Ottomans.

  * Part of arkhometha/Historical-Project-Mod@a9984f55990ab54124f0550170ce170a9e92b2e4:

    > * Another attempt at trying to stop the dismantlement event from happening over and over if
    >   you already decided to not take part anymore. Please let me know if the problem still pops
    >   up.

  * Part of arkhometha/Historical-Project-Mod@7aab423e9f38d9d5f8d5a957a83532d866d473d2

    > * Fixed NNM event 96065 that could give a dismantle nation CB on a nation you have a truce
    >   with.

  * Part of arkhometha/Historical-Project-Mod@1209fbbf169fd797749b6e2af060348f5caf1982

- Port the starting year for unlocking Great Wars from HPM: 1890 (same as unmodded), instead of 1900
  previously. The starting year for World Wars is still 1905, unchanged from both HPM and
  previously.

  This is not technically part of the dismantlement system, which only allows use of the CB after
  discovering Mass Politics no earlier than 1900 anyway. However the ten-year lag was being felt
  acutely when it comes to the power dynamics of the second half of a full campaign.

  Moving up the earliest unlock date makes room for about one extra (dismantlement-less) Great War.
  This can allow a crafty diplomat to set the stage for momentous dismantlements later down the
  line, but requires either skill or luck.

- Port the colonial organisation system from HPM 0.4.5 and later. This is ***not*** the colonial
  casus belli system. Features include:

  * A colonial country for nearly every part of sub-Saharan Africa. As a colonial conqueror from
    outside Africa, you can supersede and organise native countries into a colonial country that
    takes on your primary culture and state religion.

    This includes the addition of colonial country Ghana, separate from native country Ashanti which
    used to pull double duties.

  * Other countries outside of Africa that can also be organised (though not always as a colonial
    country) include:

    - Indonesia
    - Timor
    - Lebanon

  * Re-evaluated colonial organisation conditions. Relative to the older system organisation is a
    little more free-form now, typically requiring control of half the states that make up a
    colonial country. In comparison the older system normally required control of set key provinces.

    Likewise whereas the older system required 1870 culture tech *Revolution & Counterrevolution*,
    organisation now requires 1870 army tech *Machine Guns* and 1850 commerce tech *Market
    Regulations*.

  * Re-evaluated colonial organisation RGOs. Quoting from the 0.4 HPM patch notes:

    > * "Organizing Colony" decisions now need Machine Guns and Market Regulations. They also will
    >   change a few RGOs to cash-crop/mining RGOs, making the decisions more worthwhile. Reduced the
    >   number of cash crops/mining operations in African uncivs and moved them to the "organize"
    >   decisions—these nations were more focused on subsistence than export-economy.
    > * Nigeria RGOs redone. The source is (An Economic History of Nigeria 186o-196o Sahistory.org.za
    >   uploads /r._olufemi_ekundare_an_economic_history_of_nigerbook4you.org_.pdf )
    > * South Africa got a few more iron and coal provinces. Mostly based on Saimm.co.za and
    >   Isc.hbs.edu Africa_Iron Ore_2013.pdf
    > * Indonesia got a few iron provinces that will appear later. Based on Aig.org.au the history of
    >   coal development in indonesia.pdf
    > * Mauritania gets an iron province in the north.
    > * Senegal gets a few cotton provinces. Saint-Louis changed to cotton. Source: Persee.fr pp303
    >   and "La crise trentenaire de l’économie arachidière" by Mohamed Mbodj pp3
    > * Upper Volta will produce cotton in the south. Diversified starting RGOs a bit (previously it
    >   was only grain). Based on Icac.org and Lefaso.net
    > * Mali will now produce cotton in the south. Diversified starting RGOs and made sure cattle is
    >   in the cattle zone while fruits/grain start in the south. They will no longer start producing
    >   cotton either. Based on Fews.net copy.jpg?itok=NA3ukgKa and Haskovi.org
    > * Ivory Coast has a big cash-crop centered economy once colonized. The south will turn to coffee
    >   production while the north has cotton and rubber. Based on Legacy.lib.utexas.edu and
    >   Horizon.documentation.ird.fr
    > * Sierra Leone gets Coffee in Freetown after they are organized. Based on Universityofmakeni.com
    > * Guinea has an economy focusing on Rubber. Other productions are fruit (bananas) and a gold
    >   mine. Source: Persee.fr
    > * The Gambia is unchanged, as it exported groundnuts for most of its history. Source
    >   Stclements.edu
    > * When Guinea-Bissau is organized they will export timber and rubber. Based on En.wikipedia.org
    > * Niger, when organized, gets a 2 cotton producing provinces. Based on Persee.fr and Persee.fr
    >   and en.wikipedia.org

    Because the player debt system of HPM was *not* ported, players should take note that they
    should probably have enough treasury reserves on hand before undertaking the following lucrative
    investments:

    | Country | Maximum cost |
    | -------:|:------------ |
    Nigeria | £200k
    Indonesia | £200k
    Sierra Leone | £100k
    Zambia | £100k
    Mali | £100k
    Sudan | £100k

    These amounts are displayed as reminders in the description of their respective colonial
    organisation decision, before the player is presented with a final choice to make.

    Other colonial RGO decisions have been brought closer in line to HPM in terms of
    requirements (but rarely effects). This was done for consistency e.g. in the amount of
    importance that these decisions lend to economic techs, and include:

    - *Economic Reforms in the Uzbek Homeland*
    - *Economic Reforms in the Kyrgyz Homeland*
    - *Economic Reforms in the Turkmen Homeland*
    - *Economic Reforms in the Tajik Homeland*
    - *Economic Reforms in the Philippines*
    - *An End to Natural Dyes?*

- Ported the decision organisation & de-clutter system from HPM 0.4.5 and later.

- Ported the *Disable Trade Policy Decisions* option decision: turn off the recurring trade policy
  decisions from the start.

- To support the ported colonial organisation system from HPM, crises now follow the rules of HPM
  0.4.5 and later. They are unlocked as soon as a country researches *Revolution &
  Counterrevolution* **after** 1886, to avoid interfering with the Scramble for Africa.

  Players have access to a new option decision to go by the previous rule: crises unlock as soon as
  a country researches *Revolution & Counterrevolution*. There is also still the option to unlock
  crises from the start.

##### Changes

- Control over the *Splendid Isolation* diplomatic policy of the United Kingdom is now done through
  an option decision. The policy is active by default, and the option disables it.

##### Bugfixes

- Add a guard condition to the *Establish the Karafuto Prefecture* decision ([#28], pending
  [HFM/#164]).

  [#28]: https://github.com/moretrim/ccHFM/pull/28
  [HFM/#164]: https://github.com/SighPie/HFM/pull/164

- Leave Ryukyu independent during Meiji Restoration ([#51], pending [HFM/#169]).

  [#51]: https://github.com/moretrim/ccHFM/pull/51
  [HFM/#169]: https://github.com/SighPie/HFM/pull/169

- Prevent the Papal States (aka Lazio aka the Roman Republic) from being outright annexed when Italy
  forms by event (*Il Risorgimento*). They instead get a say into the matter, and can challenge
  Italy ([#19], [HPM/#3] + [HPM/93c5ca], pending [HFM/#163]).

  [#19]: https://github.com/moretrim/ccHFM/issues/19
  [HPM/#3]: https://github.com/arkhometha/Historical-Project-Mod/pull/3
  [HPM/93c5ca]: https://github.com/arkhometha/Historical-Project-Mod/commit/93c5ca17481d738a3dba84581be258b28343ffda
  [HFM/#163]: https://github.com/SighPie/HFM/pull/163

- Preserve the state religion of the Heavenly Kingdom upon Westernisation ([#40], pending
  [HFM/#172]).

  [#40]: https://github.com/moretrim/ccHFM/issues/40
  [HFM/#172]: https://github.com/SighPie/HFM/pull/172

- Remove correct Basotho cores in Mfecane Matabele ([HFM/#171], [HPM/#131]).

  [HFM/#171]: https://github.com/SighPie/HFM/issues/171
  [HPM/#131]: https://github.com/arkhometha/Historical-Project-Mod/pull/131

- Correct requirements of the *Occupation of the Congo Basin* decision, resolving ineffective use
  ([#26], pending [HFM/#174]).

  [#26]: https://github.com/moretrim/ccHFM/issues/26
  [HFM/#174]: https://github.com/SighPie/HFM/pull/174

- Really release Ezo when choosing to play as them (pending [HFM/#176], [HPM/#161]).

  [HFM/#176]: https://github.com/SighPie/HFM/pull/176
  [HPM/#161]: https://github.com/arkhometha/Historical-Project-Mod/pull/161

- Fixes to the *Annex Korea* decision, aiming to resolve the following two situations (pending
  [HFM/#177], [HPM/#189]):
  * late game liberation crises that would fizzle when going to war over Korea
  * Japanese conquest of Korea against the player

  [HFM/#177]: https://github.com/SighPie/HFM/pull/177
  [HPM/#189]: https://github.com/arkhometha/Historical-Project-Mod/pull/189

- Improve the Boer War call to arms to be infamy neutral (it was deducting 3 extra), and make it AI
  only. The player now gets notified of the new alliance (pending [HFM/#179]).

  [HFM/#179]: https://github.com/SighPie/HFM/pull/179

- Prevent follow-up event to *The Mysterious Lands of Guatemala* archaeological chain from granting
  prestige to non-existing countries ([8c3aa2]).

  [8c3aa2]: https://github.com/moretrim/ccHFM/commit/8c3aa2bed5bebfb7369cc7c5f7836304edf79a85

- Extend player protection of Neuchâtel crisis ([#76]). Note that there still are extant
  event-driven annexations of Neuchâtel, and as such it should still be considered an advanced start
  for dedicated players.

  [#76]: https://github.com/moretrim/ccHFM/issues/76

- Correct condition on the *Colonial Incorporation* event for Western Sahara. The event incorrectly
  happened for African countries other than Morocco.

- Correct typo in condition of the *Found the International African Association* decision that
  incorrectly allowed it to be available under certain circumstances when colonial railroading was
  disabled.

- Add a name and improved information to call-to-arms wars. They will now be called e.g. *7th
  British Call to Arms* while the associated casus belli sports a more fitting icon. A missing
  translation string in the description of the latter has also been added.

  These wars used to fall back to a generic name e.g. *7th War of British Aggression*. Combined with
  their unusual appearance this made them rather confusing at first glance. (Call to arms have no
  actual defender and feature the placeholder rebel flag on that side.)

- Simplify *Italia Irredenta*. The decision has an over-complicated design, leading to two flaws:

  * Non obvious hidden conditions, potentially confusing the player as to when the decision is
    available, and for which purpose.
  * Conditions & effects were out of sync. In some circumstances, this led to Italy repeatedly
    activating the decision with ruinous consequences on game performance.

  The simplification only mitigates the latter aspect by turning the decision into a more typical
  claiming button—though with multiple stages same as before. A knock-on consequence is that the
  decision is now somewhat less powerful than before, though some of the things it allowed before
  (e.g. granting claims while at war) were of dubious value.

  The decision might be revisited again in the future ([#39]).

  [#39]: https://github.com/moretrim/ccHFM/issues/39

##### Ported bugfixes

- Fix typo in `PEACE_TIME_FACTOR_NO_GOALS` define (pending [HFM/#175]).

  [HFM/#175]: https://github.com/SighPie/HFM/pull/175

##### Tweaks

- Flag tweaks for Korea under a monarchy ([4f0f02], pending [HFM/#166]).

  [4f0f02]: https://github.com/moretrim/ccHFM/commit/4f0f02e18710d29ba5d8b98615b186ec98648619
  [HFM/#166]: https://github.com/SighPie/HFM/pull/166

##### Other

- 4 [editorial][] changes.

### [0.1](https://github.com/moretrim/ccHFM/tree/v0.1)

The 0.1 series of releases is based on [HFM 1.27I] and is backward compatible with it.

#### [0.1.1](https://github.com/moretrim/ccHFM/tree/v0.1.1)

##### Tweaks

- Reduce the amount of notifications from the Witwatersrand Gold Rush ([#7], pending [HFM/#162]).

  [#7]: https://github.com/moretrim/ccHFM/pull/7
  [HFM/#162]: https://github.com/SighPie/HFM/pull/162

- Flag tweaks:

  * enable the flag of the British dominion of Newfoundland ([#5])
  * use the correct flag for uncivilised or absolute Dahomey ([#6])

  [#5]: https://github.com/moretrim/ccHFM/pull/5
  [#6]: https://github.com/moretrim/ccHFM/pull/6

#### [0.1.0](https://github.com/moretrim/ccHFM/tree/v0.1.0)

##### Ported features

- Make colonial railroading an option decision (PR [HFM/#157])

  [HFM/#157]: https://github.com/SighPie/HFM/pull/157

##### Ported bugfixes

- PR [HFM/#141]\:

  > At line 518 (ENG choice to not intervene) I've added `set_global_flag = anglo_persian_war` to
  > signify the crisis has occurred, otherwise the event will continuously spawn.

  [HFM/#141]: https://github.com/SighPie/HFM/pull/141

[HFM 1.27I]: https://github.com/SighPie/HFM/tree/38ca75c40063e08cbf696140e0ea68d76e6ace9d
