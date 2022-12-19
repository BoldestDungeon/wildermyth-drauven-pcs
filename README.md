# WILDERMYTH - PLAYABLE DRAUVEN

This mod attempts to add the ability to recruit Drauven characters to join your party and forge their own legacy.

**This is a work in progress!** The end goal is to produce a full-fledged unlockable race to go out adventuring in the Yondering lands, but each journey begins with a single step! We will do our best to make sure that the `main` branch is always kept in a working state, but expect things to change rapidly right now.

## GETTING STARTED

* Clone the repo into a new folder in your Wildermyth user mods. Example: `[Wildermyth Directory]/mods/user/drauven_pcs`

## CONTRIBUTING

You don't have to be a coder to contribute! 

* Ideas are all welcome - if you have any, please add them through the `Issues` tab in this repo!
* [We have Discord!](https://discord.com/invite/uftGyUa8GS) Drop in to discuss ideas, share art, etc!

## NAMING CONVENTIONS

The following naming conventions have been established to help us cooridinate our efforts. 

### RIGS

When the game looks up images to draw on the body of any of the models, it looks for the name of the image file prefixed by the character's rig name and an underscore.  For example, if you have a layer named `"shirt"` defined in an aspect that is assigned to a human who uses the `hunterF` (female hunter) rig, the game will look for a file called `hunterF_shirt.png`. 

The following are the rig names to be used for our standard Drauven characters:

* `DrauvenWarrior` (Stump model)
* `DrauvenHunter` (Haunt model)
* `DrauvenMystic` (Deeven/Skysinger model)
* `Drauven` (Stump model, used for farmers)

**As a stretch goal,** we can also tie alternate rigs to characters using the alternate theme features available in the game. Any additional models that we rig up will simply be named after the name of the original assets that were used:

* `Stump` (Stump model, exact repeat of `DrauvenWarrior`, would allow non-warriors/non-farmers to appear as a Stump)
* `Haunt` (Haunt model, exact repeat of `DrauvenHunter`, would allow non-hunters to appear as a Haunt)
* `Skysinger` (Deeven/Skysinger model, exact repeat of `DrauvenMystic`, would allow non-mystics to appear as a Deeven)
* `Dart`
* `Stormthroat`
* `Gorelord`
* `Pilot`
* `Redcloak`

### BODY PARTS (EXCLUDING HEADS)

The name for each body part will follow the following general format, omitting any sections that don't apply:
`{Rig}_{Part}{R/L}_{Pose}_{Sublayer}`

These names are **case sensitive**.

#### Rig

The name of the rig that this image applies to. See the above list of rigs for possible values.

#### Part

The body part name, which will be one of the following:
* `Torso`
* `Arm`
* `Hand`
* `Thumb`
* `Leg`
* `Tail`

**R/L**

Arms, Legs Hands and Thumbs will be followed by either a capital `R` or `L` to specify if the image is for the character's Right or Left body part, respectively. (The model is assumed to be facing to the right, the right hand is normally the character's main hand).

#### Pose (Arms and Hands only)

Arms and Hands care about the pose. The following poses are possible:

**Arms**

Arms can be posed to hold a 1-handed or 2-handed item. To aid with layering order, we have also broken the arms into upper-arm and lower-arm layers.

* `1hand_Upper`
* `1hand_Lower`
* `2hand_Upper`
* `2hand_Lower`

**Hands**
* `Open` (Not holding anything)
* `Closed` (Standard weapon/item grip)
* `2hand` (Holding 2-handed item)
* `Book` (Holding a book, grip generally more relaxed)

**Thumbs**

Thumbs are to be separated out to a separate layer so that they can go in front or behind the object being held, as appropriate, so the only poses needed would be:
* `Closed`
* `Book`

#### Sublayer

Each body part may consist of up to 3 sublayers:

* `Skin` (Usually the majority of the area, the `skin` colour will be used to tint this layer)
* `Stripe` (Stripes will have the `primary` tint applied and will be drawn overtop the base skin layer)
* `Untinted` (Any parts that should not have the tint colour applied, will be applied over the skin layer)

Black outlines will remain black when tinted, so may be part of any layer. 

### HEAD PIECES

Heads consist of a total of 4 selectable parts: Head, Horns, Feathers and Whiskers. The head itself may be broken up into multiple pieces to aid with facial expressions. Each face will have skin layer definitions that are specific for that head, so unlike the rig-specific files that _must_ follow identical naming convention, we have a bit more lattitude with faces if we need.

#### Drauven Heads

The naming convention for the files should follow the format of `replaceHead_{HeadName}_{Part}_{Expression}_{Sublayer}`

* `replaceHead` seems to be a special prefix that allows the head part to be drawn even when the normal human head is removed.

**HeadName**

The head name will the name of the Drauven model that the head originally came from, such as:

* `Stump`
* `Haunt`
* `Skysinger`
* `Pilot`
* `Stormthroat`
* `Gorelord`

**Part**

(Optional) - If breaking down the face into multiple parts for the purpose of making expressions through combinations of details, this will be the name of the part in question. These can be defined on a per-head basis, just make sure to let your coding partner know what parts will need to be defined in the layer declarations!  Suggestions include:

* `Base`
* `Eye`
* `Mouth`
* etc.

**Expression**

A description of the expression that the file should be used for. The exact mapping of images to expressions can be done on a per-head basis, so be sure to communicate with your coding partner to let them know which versions of the parts will be used with each expression. For example, you could name the images after the exact expressions used in game (`grim`, `interested`, `surprised`, etc.) or use different descriptors (such as `wide`, `normal`, `closed`, etc.) that can be assigned to multiple expressions.

**Sublayer**

Each head may include up to 3 sublayers:

* `Skin` (Usually the majority of the area, the `skin` colour will be used to tint this layer)
* `Stripe` (Stripes will have the `primary` tint applied and will be drawn overtop the base skin layer)
* `Untinted` (Any parts that should not have the tint colour applied, will be applied over the skin layer)

#### Drauven Horns, Feathers, Whiskers, Tattoos and Scars

Horns, Feathers, Whiskers and other details can be positioned separately for each of the heads that are supported. We can code a specific name for each part and head combination, so there is flexibility here to make things work as required - be sure to communicate with your coding partner to let them know exactly which layers will need to be defined and what depth they should be drawn at.

The general name convention should be something like `replaceHead_{HeadName}_{Part}_{Depth}_{Expression}_{Sublayer}`

* `replaceHead`: (Required) This prefix seems to allow parts to appear when the human head is removed
* `HeadName`:  (Required) The name of the head that the part applies to
* `Part`: (Required) The name of the part. Examples: `Whiskers1`, `Horns2`, `ScarFire`, `TattooLightning`, etc.
* `Depth`: (Optional) If needed, an indication of layering order. Examples: `Front`, `Back`
* `Expression`: (Optional) If needed, an indication of which expression(s) the layer applies to. 
* `Sublayer`: As above, an indication of which tint colour should be applied. Examples: `Skin`, `Hair`, `Streak`, `Untinted`, etc.

#### Augments & Theme Limbs

Augments, theme limbs and other existing assets will need to be saved with the same name but new rig prefix. For example, the Tree theme has pieces named `replaceArmL_tree`, `replaceArmR_tree`, etc. that exist for each of the 6 standard rigs. To make these limbs work with our Drauven, we will need copies of each of the layers using our rig names as the prefix - so the above tree theme parts would needs names such as `DrauvenWarrior_replaceArmL_tree` and `DrauvenMystic_replaceArmR_tree`, etc.