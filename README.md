## How To Use The Calculation Command

**Note:** For the duration of this guide, the prefix will be assumed to be the default: `!`
<details>
  <summary><b>Part 1: Command Formatting</b></summary>

The way this command works is that you provide it with all of the various different buffs, effects, etc. that you and the enemy have, and then Eresh will run everything you provided through the damage and NP formula and return the result for you.

There will be a list of all the different arguments you can provide later on, but for now, just know that: attack30 would stand for 30% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up and npmod20 would stand for 20% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_310.png" alt="NP Dmg Up" width="15" height="15"> NP Damage Up.

Now, say you wanted to calculate how much damage Ereshkigal's Noble Phantasm would deal with 30% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up and 20% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_310.png" alt="NP Dmg Up" width="15" height="15"> NP Damage up. Keeping in mind the arguments listed before, you could do so with the following command:

`!calc Ereshkigal attack30 npmod20`

The arguments following Ereshkigal can be in any order, and you can also repeat. You must, however, begin with `!calc NameOfServant`.
If you were to do `!calc Ereshkigal attack30 npmod10 npmod10`, Eresh would interpret that as `!calc Ereshkigal attack30 npmod20`, adding the two 10's together.

<img src="https://user-images.githubusercontent.com/56235026/126912862-959d81f6-f008-4ec9-b2f8-72acb647d7bd.png" width="400">

Note that unlike most other commands with Eresh bot, the calculation command **cannot** accept spaces in servant names. So if you want to calculate Sei Shonagon's NP damage, you could either use an alias like `!calc sei`, put their name in quotation marks `!calc "sei shonagon"`, or squish the name together like `!calc seishonagon`).
</details>


<details>
  <summary><b>Part 2: What's Included By Default?</b></summary>
  
  Consider the example from the previous section:
  
  `!calc Ereshkigal attack30 npmod20`
  
  <img src="https://user-images.githubusercontent.com/56235026/126912862-959d81f6-f008-4ec9-b2f8-72acb647d7bd.png" width="400">
  
  
Since all we provided in our sample was:
- The name of the servant (Ereshkigal)
- 30% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up
- 20% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_310.png" alt="NP Dmg Up" width="15" height="15"> NP Damage Up

The bot had to make some assumptions to fill in the rest. By default, unless you tell it otherwise, Eresh will assume:
- Your servant is max leveled, without grails. (Ex. Level 90 for an SSR (★★★★★), Level 80 for an SR (★★★★), etc.)
- Your servant has 1,000 ATK Fous <img src="https://static.wikia.nocookie.net/fategrandorder/images/9/95/AllAtkUpIcon3.png/revision/latest/" width="15">
- Your servant is NP5

In addition to the assumptions, Eresh will also automatically include:
- Your servant's passives (for example, Ereshkigal has 11% arts up and 225 damage plus. The arts up won't affect her NP as it is buster, but the 225 damage plus will).
- All of your servant's internal stats, such as their innate ATK stat, their class multiplier, etc.
  
Note that as Append Passives need to be unlocked and leveled like skills, they are not included by default.
  
Finally, if the servant is available in NA, Eresh will automatically default to the highest available strengthening for the NP in NA. If the servant is not in NA yet, it will default to the highest available strengthening in JP.
  
Note that all of these automatic inclusions / assumptions can be changed via the arguments you will see in the arguments list at the bottom of this page.

It does **not**, however, include things like Class Affinity or Attribute Affinity by default, as it does not know what type of enemy you are up against. So, for example, if you calculate with a berserker, be sure to include the class you are fighting against, otherwise the result returned would assume you get no class advantage, when in reality a berserker will probably be getting 1.5x class advantage.

Thus, in our example above, what Eresh is returning is the amount of damage Ereshkigal's Noble Phantasm will deal per enemy given a Level 90, 1,000 ATK Fou <img src="https://static.wikia.nocookie.net/fategrandorder/images/9/95/AllAtkUpIcon3.png/revision/latest/" width="15">, NP5 Ereshkigal with 30% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up and 20% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_310.png" alt="NP Dmg Up" width="15" height="15"> NP Damage Up, assuming Ereshkigal gets no class advantage and no attribute advantage over the enemy.

There is a bit of random chance involved in the FGO Damage Formula to ensure that you don't do the same damage in the same conditions every single time, so Eresh returns:
- The average damage you can deal (in this case, **32,275**)
- The minimum damage you can deal (in this case, **29,070**)
- The maximum damage you can deal (in this case, **35,448**)
  
</details>

<details>
  <summary><b>Part 3: Card Calculations</b></summary>

In addition to calculating noble phantasm damage, you can also calculate the damage of cards themselves.
For these, you will include one additional argument between the servant's name and your buffs etc. that indicates what card type you wish to test.

So, say you wanted to test how much damage Ereshkigal's quick card would deal with 30% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up. You would use:

`!calc Ereshkigal quick attack30`

<img src="https://user-images.githubusercontent.com/56235026/126913971-f35210f0-ca73-4d55-9da5-402f7aa6422d.png" width="400">
</details>

<details>
  <summary><b>Part 4: What About CEs?</b></summary>

Including Craft Essences in calculations is very simple. You only need to treat their effects as buffs the same as any other buffs. So if you want to use, say, an MLB black grail, just add `npmod80` for the 80% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_310.png" alt="NP Dmg Up" width="15" height="15"> NP Damage Up just like we did for the 20% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_310.png" alt="NP Dmg Up" width="15" height="15"> NP Damage Up earlier.

As for the CE's attack, you can use the `ce` argument followed by the amount of attack the CE has, for example `ce2400`.

So, lets take our calculation from earlier (`!calc Ereshkigal attack30 npmod20`) and add a Level 100 MLB Black Grail to the mix. The command you'd give would look like this:

`!calc Ereshkigal attack30 npmod20 npmod80 ce2400`

<img src="https://user-images.githubusercontent.com/56235026/126914094-f7ceaa61-57f7-4c72-b8bb-7c8d46da0221.png" width="400">

</details>

<details>
  <summary><b>Part 5: Calculating NP Refund</b></summary>

Calculating damage is great, but what about calculating the amount of NP you'll generate from your attack or noble phantasm? This is important to know for looping, like with Skadi or Caster Artoria, and Eresh will let you calculate this as well.

While there are more arguments you _should_ include if you are going to test refund, the only thing you _have_ to include is the HP of the enemy you are fighting. This is because the remaining HP of the enemy you are up against influences how much NP you generate.

At a basic level then, if you wanted to test how much NP Edmund Dantes would get back after using his NP, you could use:

`!calc Dantes hp10000`

<img src="https://user-images.githubusercontent.com/56235026/126914221-46341ab0-c9cc-41aa-ac3a-deea8dcc73bd.png" width="400">

Here, we can see that on an enemy with 10,000 HP, if Dantes does not have any buffs, he will get between 6.2% and 6.51% NP back after using his Noble Phantasm. Eresh also provides a breakdown of how much NP each individual hit of Dantes' Noble Phantasm will generate. The breakdown uses the **minimum** damage value, but if you look to the bottom, you will see Eresh also provides you with the maximum amount of NP that Dantes could get back from his NP. The reason it is different (6.51% vs 6.2%) is that if Dantes deals the maximum amount of damage (remember earlier it was noted that there is a bit of randomness) with his NP, he will kill the enemy one hit earlier than he would if he deals the minimum, and that means one extra hit would get the overkill bonus that grants additional NP.

Keep in mind that the class of the enemy you are fighting, card buffs (like quick up and arts up), np gain buffs, and the position of the card (for non NPs) all impact the amount of NP you generate, so while this example did not include them for simplicity, you should include those values in your actual calculations.
</details>


## Argument List

Arguments will be broken down into 5 categories:
- **General**: These arguments can be useful everywhere, no matter what type of calculation you are doing
- **NP**: These arguments have **NO EFFECT** on regular face cards, they are **ONLY** used on Noble Phantasms.
- **FaceCard**: The opposite of NP, these arguments have **NO EFFECT** on Noble Phantasms, they are **ONLY** used for regular cards.
- **Refund**: These arguments are only useful for calculating NP refund.
- **Special**: These arguments are shortcuts to apply commonly used buffs.

### General Arguments:

<details>
  <summary><b>fou/f <img src="https://static.wikia.nocookie.net/fategrandorder/images/9/95/AllAtkUpIcon3.png/revision/latest/" width="15"></b></summary>

**Examples:**
- `!calc Ereshkigal fou1500`
- `!calc Ereshkigal f2000`

**Usage:**
Provides the servant with the designated amount of ATK stat from applied <img src="https://static.wikia.nocookie.net/fategrandorder/images/9/95/AllAtkUpIcon3.png/revision/latest/" width="15"> fous. If you do not use this argument, your servant will be assumed to have 1,000 ATK worth of fous applied.

**Note:**
This argument is not additive. If you supply `!calc Ereshkigal fou1500 fou2000`, it will set fou to 2000, not 3500.
</details>

<details>
  <summary><b>ce</b></summary>

**Examples:**
- `!calc Ereshkigal ce1000`
- `!calc Ereshkigal ce2400`

**Usage:**
Provides the servant with the designated amount of ATK stat from a Craft Essence.

**Note:**
This argument is not additive. If you supply `!calc Ereshkigal ce1500 ce2000`, it will set ce to 2000, not 3500.
</details>

<details>
  <summary><b>totalattack/ta</b></summary>
  
**Examples:**
- `!calc Ereshkigal ta15000`
- `!calc Ereshkigal totalattack13450`

**Usage:**
Sets your servant's total attack stat. This will **override** any other source of attack stat. So if you set this value, it does not matter what level your servant is, what CE ATK you provided, or how much Fou attack you set. All of those will be ignored and instead this value will be used.

**Note:**
This argument is not additive. If you supply `!calc Ereshkigal ta1500 ta2000`, it will set total attack to 2000, not 3500.
</details>

<details>
  <summary><b>cardmod/m [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_314.png" alt="Buster Up" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_313.png" alt="Arts Up" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_312.png" alt="Quick Up" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_541.png" alt="Buster Resist Down" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_540.png" alt="Arts Resist Down" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_539.png" alt="Quick Resist Down" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_517.png" alt="Buster Down" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_516.png" alt="Arts Down" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_515.png" alt="Quick Down" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_347.png" alt="Buster Resist Up" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_346.png" alt="Arts Resist Up" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_345.png" alt="Quick Resist Up" width="15" height="15">]</b></summary>
  
**Examples:**
- `!calc Ereshkigal cardmod50`
- `!calc Ereshkigal m-25`

**Usage:**
Used to set all things color buff related. For <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_314.png" alt="Buster Up" width="15" height="15"> **Card Up** on you and <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_541.png" alt="Buster Resist Down" width="15" height="15"> **Card Resist Down** on the enemy, use a positive value, like `m20`. For <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_517.png" alt="Buster Down" width="15" height="15"> **Card Down** on you and <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_347.png" alt="Buster Resist Up" width="15" height="15"> **Card Resist Up** on the enemy, use a negative value, like `m-20`.
</details>

<details>
  <summary><b>atkmod/atk/attack/a [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_503.png" alt="ATK Down" width="15" height="15">]</b></summary>
  
**Examples:**
- `!calc Ereshkigal atkmod20`
- `!calc Ereshkigal atk-50`
- `!calc Ereshkigal a13`
- `!calc Ereshkigal attack-80`

**Usage:**
Use a positive value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up and a negative value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_503.png" alt="ATK Down" width="15" height="15"> Attack Down.
</details>

<details>
  <summary><b>defmod/def/defense/d [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_301.png" alt="Def Up" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_504.png" alt="Def Down" width="15" height="15">]</b></summary>
  
**Examples:**
- `!calc Ereshkigal defmod20`
- `!calc Ereshkigal def-50`
- `!calc Ereshkigal defense23`
- `!calc Ereshkigal d65`

**Usage:**
This sets **enemy** Defense Up and Down. So keep in mind that setting defense up on the enemy will lower your damage, and setting defense down on the enemy will raise it. Use a positive value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_301.png" alt="Def Up" width="15" height="15"> Defense Up, and a negative value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_504.png" alt="Def Down" width="15" height="15"> Defense Down. Again, keep in mind that in this case, `d-20` is beneficial for you and `d20` is detrimental.
</details>

<details>
  <summary><b>powermod/power/p [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_302.png" alt="PowerMod Up" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_505.png" alt="PowerMod Down" width="15" height="15">]</b></summary>
  
**Examples:**
- `!calc Ereshkigal powermod40`
- `!calc Ereshkigal power-30`
- `!calc Ereshkigal p20`

**Usage:**
This is for PowerMod / Special ATK. Some examples where you might use this are in [Musashi's First Skill](https://apps.atlasacademy.io/db/JP/skill/327550) or with the [ATK Strength Up](https://apps.atlasacademy.io/db/JP/skill/991615) effects of Event CEs. This is **NOT** used for cases like Gilgamesh's Enuma Elish, which deals additional damage to [Weak to Enuma Elish] targets. That is Super Effective Mod, and it is in the NP args section.
</details>

<details>
  <summary><b>flatdamage/ad/fdmg/fd/dmg [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="Damage Plus" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_301.png" alt="Damage Cut" width="15" height="15">]</b></summary>
  
**Examples:**
- `!calc Ereshkigal flatdamage1000`
- `!calc Ereshkigal ad-2300`
- `!calc Ereshkigal fdmg1500`
- `!calc Ereshkigal fd650
- `!calc Ereshkigal dmg-50`

**Usage:**
This is for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="Damage Plus" width="15" height="15"> flat damage up (damage plus) on you and <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_301.png" alt="Damage Cut" width="15" height="15"> flat damage down (damage cut) on the enemy, such as with Waver's skills. Use a positive value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="Damage Plus" width="15" height="15"> damage plus and negative for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_301.png" alt="Damage Cut" width="15" height="15"> damage cut.
</details>


<details>
  <summary><b>specialdefensemod/sdm [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_334.png" alt="Special Defense Up" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_529.png" alt="Special Defense Down" width="15" height="15">]</b></summary>
  
**Examples:**
- `!calc Ereshkigal specialdefensemod30`
- `!calc Ereshkigal sdm-50`

**Usage:**
This is for **Special Defense**, which is given to some bosses like Gawain. Use a positive value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_334.png" alt="Special Defense Up" width="15" height="15"> Special Defense Up (reduces your damage) and a negative value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_529.png" alt="Special Defense Down" width="15" height="15"> Special Defense Down.
</details>

<details>
  <summary><b>cardmultiplieroverride/cmv</b></summary>
  
**Examples:**
- `!calc Ereshkigal cardmultiplieroverride1.5`
- `!calc Ereshkigal cmv0.8`

**Usage:**
This can be used if you need to override the default cardtype multiplier, which is based on card color and position in the chain.

|   | First | Second | Third |
| ------------- | ------------- | ------------- | ------------- |
| Arts  | 1.0  | 1.2  | 1.4 |
| Buster  | 1.5  | 1.8 | 2.1  |
| Quick  | 0.8 | 0.96 | 1.12  |

Extra cards are always 1.0, and Noble Phantasms are always the **First** column value of their respective card type.
</details>

<details>
  <summary><b>classadvantageoverride/cao</b></summary>
  
**Examples:**
- `!calc Ereshkigal classadvantageoverride1.5`
- `!calc Ereshkigal cao2`

**Usage:**
This can be used to set a custom class advantage.
</details>

<details>
  <summary><b>saber, lancer, archer, mooncancer, etc...</b></summary>
  
**Examples:**
- `!calc Ereshkigal archer`
- `!calc Ereshkigal alterego`

**Usage:**
This can be used to set the opponent's class. For classes that are two words, like Moon Cancer or Alter Ego, you will need to squish them together (i.e. `alterego`). Note that unlike setting class advantage manually with the `cao` argument, this argument will also properly set the enemy's Serverrate (which is important for determining NP refund).
</details>

<details>
  <summary><b>sky, earth, etc...</b></summary>
  
**Examples:**
- `!calc Ereshkigal sky`
- `!calc Ereshkigal human`

**Usage:**
This can be used to set the opponent's attribute.
</details>

### NP Arguments:

<details>
  <summary><b>np</b></summary>

**Examples:**
- `!calc Ereshkigal np1`
- `!calc Ereshkigal np5`

**Usage:**
Sets the servant's Noble Phantasm level. If this argument is not provided, NP level is assumed to be 5.
</details>

<details>
  <summary><b>npvalue/npv/npo/npoverride</b></summary>

**Examples:**
- `!calc Ereshkigal npv1000`
- `!calc Ereshkigal npo600`
- `!calc Ereshkigal npvalue1200`
- `!calc Ereshkigal npoverride1600`

**Usage:**
Sets a custom Noble Phantasm multiplier. This is useful for servants like Arash or Chen Gong who deal additional damage with overcharge.
</details>

<details>
  <summary><b>strengthen/str/lewd/interlude</b></summary>

**Examples:**
- `!calc Ereshkigal strengthen0`
- `!calc Ereshkigal str1`
- `!calc Ereshkigal lewd2`
- `!calc Ereshkigal interlude1`

**Usage:**
Specify what interlude / strengthening level you want for an NP. If you try to specify a strengthening beyond what a servant actually has, it will ignore the argument. By default, if no argument is provided, strengthening level is assumed to be:
  
  - The highest available strengthening on NA servers for servants that are in NA.
  - The highest available strengthening on JP servers for servants that are NOT in NA.
  
If you want to test a servant without any strengthenings, you should use strengthening 0. 0 is no strengthening, 1 is strengthening level 1, 2 is strengthening level 2, etc.
  
Additionally, you can use strengthening to switch between Noble Phantasms for Emiya, Space Ishtar, and Fairy Knight Lancelot.
</details>

<details>
  <summary><b>npmod/n [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_310.png" alt="NP Damage Up" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_508.png" alt="NP Damage Down" width="15" height="15">]</b></summary>

**Examples:**
- `!calc Ereshkigal npmod50`
- `!calc Ereshkigal n20`

**Usage:**
Use a positive value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_310.png" alt="NP Damage Up" width="15" height="15"> NP Damage Up, and a negative value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_508.png" alt="NP Damage Down" width="15" height="15"> NP Damage Down.
</details>

<details>
  <summary><b>supereffectivemod/se/super/s <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_302.png" alt="Super Effective Modifier" width="15" height="15"></b></summary>

**Examples:**
- `!calc Ereshkigal supereffectivemod150`
- `!calc Ereshkigal super200`
- `!calc Ereshkigal se300`
- `!calc Ereshkigal s125`

**Usage:**
This is for Super Effective Modifier, so for cases like Gilgamesh whose NP deals extra damage vs a specific trait. Note that 150 = 50% bonus. Defaults to 100 if nothing is provided (no bonus).
</details>

### FaceCard Arguments:

<details>
  <summary><b>buster, arts, quick, extra</b></summary>

**Examples:**
- `!calc Ereshkigal buster`
- `!calc Ereshkigal arts`
- `!calc Ereshkigal quick`
- `!calc Ereshkigal extra`

**Usage:**
This is used to set which card type you want to test. Note that you **must** include this a the second value, after the servant's name. If you include it, the test will switch from being an NP test to a card test.
</details>

<details>
  <summary><b>first, second, third</b></summary>

**Examples:**
- `!calc Ereshkigal first`
- `!calc Ereshkigal second`
- `!calc Ereshkigal third`

**Usage:**
This is used to set card position, which is important for both damage and refund. If you do not provide anything here, the card is assumed to be in the first position. Also, if your card type is buster or arts, the appropriate first card bonus will be applied if you either specify first or do not specify a position.
</details>

<details>
  <summary><b>bf</b></summary>

**Examples:**
- `!calc Ereshkigal bf`

**Usage:**
Used to manually apply the buster first bonus, which is a damage bonus all of your Non-NP cards get if the first card in your attack sequence is buster. So, if you are trying to calculate a quick card, but intend to use that card in a buster-quick-quick chain for instance, you would want to apply the buster first bonus to the quick card.
</details>

<details>
  <summary><b>bbb/busterchain</b></summary>

**Examples:**
- `!calc Ereshkigal bbb`
- `!calc Ereshkigal busterchain`

**Usage:**
This is used to indicate that your card is in a full buster chain. This will apply **BOTH** the buster chain bonus as well as the buster first bonus, as a full buster chain will always have a buster first bonus.
</details>

<details>
  <summary><b>crit [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_324.png" alt="Critical Damage Up" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_514.png" alt="Critical Damage Down" width="15" height="15">] OR by itself to only set the card as a critical with no bonus.</b></summary>

**Examples:**
- `!calc Ereshkigal crit`
- `!calc Ereshkigal crit50`
- `!calc Ereshkigal crit-25`

**Usage:**
This argument can be used in **two ways**. The first way is just to include `crit` by itself, for example `!calc Ereshkigal buster crit`. This would not give any bonus critical damage up, but it would set the card as a critical hit, which will increase damage on its own, as well as factor in any passive critical damage.
    
The second way to use it is to include `crit` with a number, for example `!calc Ereshkigal buster crit50` or `crit-50`. This will **BOTH** set the card as a critical hit **AND** apply the given amount of critical damage up or down. Use a positive value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_324.png" alt="Critical Damage Up" width="15" height="15"> Critical Damage Up, and a negative value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_514.png" alt="Critical Damage Down" width="15" height="15"> Critical Damage Down.
</details>

<details>
  <summary><b>extracardmodifier/ecm</b></summary>

**Examples:**
- `!calc Ereshkigal extracardmodifier`
- `!calc Ereshkigal ecm`

**Usage:**
This sets the extra card modifier to a special value for specific types of card chains.

This value is: 2 if the Extra card in a Brave Chain and 3.5 if Extra card in a Buster/Quick/Arts Brave Chain.
  
You should not use this argument unless you are testing an extra card.
</details>

<details>
  <summary><b>paw/foupaw/print/footprint</b></summary>

**Examples:**
- `!calc Ereshkigal paw500`
- `!calc Ereshkigal print100`
- `!calc Ereshkigal print250`
- `!calc Ereshkigal footprint475`

**Usage:**
Adds extra attack stat from Beast's Footprints.
</details>

### Refund Arguments:

<details>
  <summary><b>enemyhp/hp</b></summary>

**Examples:**
- `!calc Ereshkigal hp20000`
- `!calc Ereshkigal enemyhp150000`

**Usage:**
This sets the enemy's HP. This is required to set for refund calculations, as refund depends on how many overkill hits you get.
</details>

<details>
  <summary><b>npgain/npgen/ng [Positive:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_303.png" alt="NP Generation Up" width="15" height="15">] [Negative:<img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_509.png" alt="NP Generation Down" width="15" height="15">]</b></summary>

**Examples:**
- `!calc Ereshkigal npgain20`
- `!calc Ereshkigal npgen-20`
- `!calc Ereshkigal ng60`

**Usage:**
Sets NP Generation buffs and debuffs. Use a positive value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_303.png" alt="NP Generation Up" width="15" height="15"> NP Generation Up, and a negative value for <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_509.png" alt="NP Generation Down" width="15" height="15"> NP Generation Down.
</details>

<details>
  <summary><b>cardrefundvalue/crv</b></summary>

**Examples:**
- `!calc Ereshkigal cardrefundvalue1.2`
- `!calc Ereshkigal crv3`

**Usage:**
This sets a custom card refund value for a card type. By default this is determined by the type of card and the card's position.
</details>

<details>
  <summary><b>enemyservermod/esm/sm</b></summary>

**Examples:**
- `!calc Ereshkigal enemyservermod1.2`
- `!calc Ereshkigal esm1`
- `!calc Ereshkigal sm0.9`

**Usage:**
Sets a custom enemy server rate which impacts how much NP you generate. If you set the enemy class, this value is automatically set to the appropriate value.
</details>

<details>
  <summary><b>af/aaa (Cards Only)</b></summary>

**Examples:**
- `!calc Ereshkigal af`
- `!calc Ereshkigal aaa`

**Usage:**
Used to manually apply the arts first bonus, which is an NP generation bonus all of your Non-NP cards get if the first card in your attack sequence is arts. So, if you are trying to calculate a quick card, but intend to use that card in a arts-quick-quick chain for instance, you would want to apply the arts first bonus to the quick card. You can also use aaa to apply this, as that would imply arts first, but do note that calcs do NOT include the 10% additional NP added at the start if your chain for using an arts chain.
</details>

<details>
  <summary><b>ocfix</b></summary>

**Examples:**
- `!calc ChenGong ocfix`

**Usage:**
Doubles np refund. This is for use with Chen Gong's NP, and only in cases where you do **not** overkill the enemy. This argument will not check whether you overkilled, nor will it check if you are using Chen Gong, it will only double the final result, so ensure you are only using this argument when you know Chen Gong will not overkill the enemy. Additionally, this argument can only be used on NPs. 
</details>

### Special Arguments:

Note that unlike other arguments which can be in any order, **for servants who can change card type, like Space Ishtar,** you will want to make sure you change their card type BEFORE using one of the special args. Space Ishtar has an arts NP by default, so if you were to use `!calc Spishtar xss str2` it would first try to apply double skadi buffs, see that the card is not quick, and not apply the buffs, and only AFTER doing so would it switch your card to quick. Thus, you would instead want to do `!calc Spishtar str2 xss`, as in this case, it would see your card is quick and apply the buffs. For all other servants aside from ones that can change card type however, this is not an issue and the argument can be in any order just like any others.

<details>
  <summary><b>xss <img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/503900/card_servant_1.png" alt="Skadi" width="20"><img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/503900/card_servant_1.png" alt="Skadi" width="20"></b></summary>

**Examples:**
- `!calc Sei xss`

**Usage:**
Applies the following buffs: 100% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_312.png" alt="Quick Up" width="15" height="15"> Quick Damage Up (`m100`) & 200% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_312.png" alt="Quick Up" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_324.png" alt="Critical Damage Up" width="15" height="15"> Quick Critical Damage Up (`crit200`).
  
Note that this does not make your card critical, it only adds the buffs. So if you want your card to be a critical hit, you will need to use the `crit` argument. See the crit argument section in FaceCards for details.

Additionally, if you use the `xss` argument on an arts or buster card, the cardmod and critical damage bonus will not be applied, as they both only work on quick cards.
</details>

<details>
  <summary><b>xssd <img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/503900/card_servant_1.png" alt="Skadi" width="20"><img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/503900/card_servant_1.png" alt="Skadi" width="20"></b></summary>

**Examples:**
- `!calc Sei xssd`

**Usage:**
Applies the following buffs: 100% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_312.png" alt="Quick Up" width="15" height="15"> Quick Damage Up (`m100`), 200% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_312.png" alt="Quick Up" width="15" height="15"><img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_324.png" alt="Critical Damage Up" width="15" height="15"> Quick Critical Damage Up (`crit200`), and 60% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_504.png" alt="Def Down" width="15" height="15"> Defense Down (`d-60`).
  
Note that this does not make your card critical, it only adds the buffs. So if you want your card to be a critical hit, you will need to use the `crit` argument. See the crit argument section in FaceCards for details.

Additionally, if you use the `xssd` argument on an arts or buster card, the cardmod and critical damage bonus will not be applied, as they both only work on quick cards. The defense down will still be applied, however.
</details>

<details>
  <summary><b>xcc <img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/504500/card_servant_1.png" alt="Castoria" width="20"><img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/504500/card_servant_1.png" alt="Castoria" width="20"></b></summary>

**Examples:**
- `!calc SummerMusashi xcc`

**Usage:**
Applies the following buffs: 100% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_313.png" alt="Arts Up" width="15" height="15"> Arts Damage Up (`m100`) & 40% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up (`a40`).

Note that if you use the `xcc` argument on a quick or buster card, the cardmod will not be applied, as it only works on arts cards. The attack up will still be applied, however.
</details>

<details>
  <summary><b>xccng <img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/504500/card_servant_1.png" alt="Castoria" width="20"><img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/504500/card_servant_1.png" alt="Castoria" width="20"></b></summary>

**Examples:**
- `!calc SummerMusashi xccng`

**Usage:**
Applies the following buffs: 100% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_313.png" alt="Arts Up" width="15" height="15"> Arts Damage Up (`m100`), 40% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up (`a40`), and 60% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_303.png" alt="NP Generation Up" width="15" height="15"> NP Gain Up (`ng60`).

Note that if you use the `xccng` argument on a quick or buster card, the cardmod will not be applied, as it only works on arts cards. The attack up and NP gain up will still be applied, however.
</details>

<details>
  <summary><b>xmm <img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/500800/card_servant_1.png" alt="Merlin" width="20"><img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/500800/card_servant_1.png" alt="Merlin" width="20"></b></summary>

**Examples:**
- `!calc Ereshkigal xmm`

**Usage:**
Applies the following buffs: 100% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_314.png" alt="Buster Up" width="15" height="15"> Buster Damage Up (`m100`) & 40% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up (`a40`).

Note that if you use the `xmm` argument on an arts or quick card, the cardmod will not be applied, as it only works on buster cards. The attack up will still be applied, however.
</details>

<details>
  <summary><b>xmmc <img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/500800/card_servant_1.png" alt="Merlin" width="20"><img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/500800/card_servant_1.png" alt="Merlin" width="20"></b></summary>

**Examples:**
- `!calc Ereshkigal xmmc`

**Usage:**
Applies the following buffs: 100% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_314.png" alt="Buster Up" width="15" height="15"> Buster Damage Up (`m100`), 40% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up (`a40`), & 200% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_324.png" alt="Critical Damage Up" width="15" height="15"> Critical Damage Up (`crit200`).

Note that this does not make your card critical, it only adds the buffs. So if you want your card to be a critical hit, you will need to use the `crit` argument. See the crit argument section in FaceCards for details.

Additionally, if you use the `xmmc` argument on a quick or arts card, the cardmod will not be applied, as it only works on buster cards. The attack up and critical damage up will still be applied, however.
</details>

<details>
  <summary><b>xww <img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/501900/card_servant_1.png" alt="Waver" width="20"><img src="https://assets.atlasacademy.io/GameData/JP/Servants/Commands/501900/card_servant_1.png" alt="Waver" width="20"></b></summary>

**Examples:**
- `!calc Ereshkigal xww`

**Usage:**
Applies the following buffs: 60% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Attack Up (`a60`), 1,000 <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_300.png" alt="ATK Up" width="15" height="15"> Flat Damage (`fd1000`), & 100% <img src="https://assets.atlasacademy.io/GameData/JP/BuffIcons/bufficon_324.png" alt="Critical Damage Up" width="15" height="15"> Critical Damage Up (`crit100`).

Note that this does not make your card critical, it only adds the buffs. So if you want your card to be a critical hit, you will need to use the `crit` argument. See the crit argument section in FaceCards for details.
</details>
