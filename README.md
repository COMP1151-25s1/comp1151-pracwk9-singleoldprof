# Week 9 -- Tilemaps --

Topic: Tilemaps

Learning outcomes:

* Using the "Tiled" editor to create a scene from a tileset
* Using the UI system to display information.
* Using pivots & anchors to position UI a screen independent way.

## Foreword

We are finally moving on from the Space shooter series of pracs, and on to a new game. The vibe of this game is entirely up to you, but in the next series of pracs we will focus on the more aesthetic parts of games development:

* Sound & Music
* Camera functionality
* Advanced 2D Physics
* Basic UI
* Tilemaps

Today we will be looking at both **Tilesheets** & **Tilemaps**, and the basic of how to implement UI features. A rule of thumb to remember the two is that the sheet is a source of the tiles, and the map is the layout (i.e. something you've designed/a level map)

You may be wondering where the prac content is, since this repository seems quite empty. For the next few weeks, you will be working in a personal repository, and instead the weekly repository will only contain further instructions.

Early on we wanted you to be required to remember how to import/export packages, how to regenerate nodes, and how to set up your layer collision matrix, but at this point we're confident you all remember this. If you forget these steps in future, please check out past practicals.


|   |                                                                                                                                                                                                                                                                                                                         |   |
| --- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --- |
|   | This prac will be going back over a lot of content discussed in the Colliders prac (wk6). If you have trouble remembering how to do certain things regarding that (like setting up triggers from scratch), it may be ideal to keep referring back to that prac - the prac will assume you remember most of these things. |   |
|   |                                                                                                                                                                                                                                                                                                                         |   |

## Links

Today we will be using various resources. Their links will be provided in the prac when needed, but here is a list of them and their use:

* [Tiled](https://www.mapeditor.org/) - Our Tilemap Editor
* [Kenny.NL](https://kenney.nl/assets/tag:pixelhttps://kenney.nl/assets/category:2D?sort=updat) - The website where we will be downloading a tilemap - You *could* find an alternative, but for these pracs please use this website
  * It is recommended to use a Tilemap from the "[Tiny](https://kenney.nl/assets/series:Tiny)" series
* [Super Tiled2Unity (v2.3.1)](https://seanba.itch.io/supertiled2unity/devlog/937160/super-tiled2unity-231) - A Package that allows us to read **Tiled** files
* [COMP1151 TilemapGame Repository](https://classroom.github.com/a/cd80dyay) - The Github Classroom link that contains your new tilemap game repository. This will be used for the rest of semester.

## Getting Started with Tiled

To start off today's prac, we will actually not be using Unity. Instead we will be looking at an additional, helpful piece of software where we will be making our Tilemaps, called **Tiled**

Lab Users -- Tiled should already be installed on the PC, so you can skip this step

Otherwise, you can download Tiled from their [itch.io page here](https://thorbjorn.itch.io/tiled), or you can simply [check out their main web page](https://www.mapeditor.org/) and navigate through the links.

Please make sure you download the correct version for your device -- Note that Windows users should **not** need the 32-bit version


|   |                                                                                                                                                                         ⚠️Why is it asking me to pay?⚠️                                                                                                                                                                         |   |
| --- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --- |
|   | On itch.io, when downloading software you will be asked if you want to donate to the authors. This is not required to get the software, nor is it required to do the practical. When pressing the`Download Now` button on the respective pages, simply click the `No thanks, just take me to the downloads` link above the donation page, and select your desired version from there |   |
|   |                                                                                                                                                                                                                                                                                                                                                                                     |   |


|   |                                                                                                                                                                                                          What if I can't use Tiled?                                                                                                                                                                                                          |   |
| --- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --- |
|   | If you cannot use Tiled, Unity*does* feature an inbuilt tilemap editor, but it leaves a lot to be desired. [More can be found about the Unity Tilemap Editor here](https://learn.unity.com/tutorial/introduction-to-tilemaps). For this prac, it is assumed you have access to a Lab PC, which already has Tiled installed. For other projects though, if you cannot use Tiled, you may want to instead use the Unity inbuilt tilemap editor |   |
|   |                                                                                                                                                                                                                                                                                                                                                                                                                                             |   |

## What is Tiled

Tiled, simply put, is a standalone editor that supports the editing of tile maps. It supports editing in various projections (orthogonal, isometric, hexagonal), and also supports building levels with the other various tools it has on offer.

With a special Unity Package, we can also set up our colliders & triggers in Tiled itself, as well as. Past that though, we won't be going in to further depth. You are encouraged to play with Tiled in your own time though.

Various games have been made with tiled, such as [Shovel Knight](https://www.yachtclubgames.com/games/shovel-knight-treasure-trove) and [Axiom Verge](https://www.axiomverge.com/)


|   |                                                                                                                                                                                                                    Regarding Tiled Instructions                                                                                                                                                                                                                    |   |
| --- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --- |
|   | **Tiled** has a lot of features that we could go into, but unfortunately anything not mentioned in today's prac is simply outside of the scope of this unit (like other types of tilesets). If you are interested in learning more about Tiled, it is recommended that you do your own research by looking into the [Tiled documentation](https://doc.mapeditor.org/en/stable/manual/introduction), as well as looking into the various tutorials available online. |   |
|   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |   |

## Getting your practical repository

Before going further, it is advised to get a copy of your practical repository. That way, you will be able to sync your Tiled files with your GitHub repository, and easily be able to check changes made in your Tilemap.

[Github Classroom - COMP1151Prac_TilemapGame](https://classroom.github.com/a/cd80dyay)

Once this is downloaded, you do not need to open Unity just yet. We will go over how to set up your Tiled project folders so that you can directly edit your tilesheet in your project.

## Downloading Your Tilesheet

To get started with Tiled, we will first need a **Tilesheet**. For us, this will essentially act as a sort of palette to paint our map with

You may remember tilesheets from our earlier pracs, where we made a floating platform as a prefab. This is different to that, the tiles themselves act fairly differently to prefabs, and are not treated as one. This also means that the majority of the setup itself will be done in Tiled.

Download a pixel **Tilemap** from [Kenny.nl](https://kenney.nl/assets/tag:pixel) - we recommend one of the [Tiny](https://kenney.nl/assets/series:Tiny) tilesheets (specifically [TinyDungeon](https://kenney.nl/assets/tiny-dungeon) - this is the one that will be used in prac screenshots). However, the choice is entirely yours, there are a few other cool ones like "Monochrome Pirates" for example.

Note: Please ensure they are 2D tiles (the links have already been pre-filtered).

Once you have downloaded this, save and unzip it.

Ideally you should save this tilesheet directly in to your Unity Project folder:

* Navigate to your Unity Project folder (from the GitHub Classroom link above)
* Make a new folder within `Assets` called `Tiled`
* Make another folder called `TilemapGame`

If you would prefer to make your folders in a different location (such as Documents), the choice is up to you. However, making the Tiled folders within your Unity project will make your process far simpler and quicker, and will also help you back up your work (since it will exist in your repository).

## Tiled 101

Open **Tiled**. You will be faced with a fairly empty menu, with a couple of buttons, and a top menu button bar.

<img src="PracResources\images\01_TiledMain.png">

For now, do the following:

* Select `New Project`
* Navigate to where you are working on your Tilemap. If you made the folder within your Unity Project, navigate to that folder
* Call the file something simple, like `gameTilemap`, then press save

### Opening your Tilesheet - .tsx files

After creating a **Tiled** "session", you will then be prompted to select your tilesheet.

1. Select `New Tileset`
2. Call this whatever you want - a sensible name would be the same name as the image/tileset (e.g. `TinyDungeon_Tilesheet`)
3. Click the `Browse` button beside the **Source** field, and navigate to your downloaded tilesheet (the .png file in the .zip folder you downloaded).
   * Ensure that what you're selecting is a tilesheet, and not simply a single sprite. The tilesheet will be a picture containing all of the possible sprites you can use to make a tilemap. Most of the Kenny.NL packages will have the tilesheets located at `[PackageName] > Tilesheets > tilemap.png`
4. At this point you will need to set the tile height and width - On the page you downloaded your Kenny.NL asset, it will be listed on the side (Example below)
   * If you are using a Kenny.NL tilesheet, this information is contained in the root of the download, in a text file called `Tilesheet.txt`

<img src="PracResources\images\02_KennyTileSize.png">

* Once you have selected the Create button, you will then be prompted to create a `.tsx` file, basically a file containing the tilesheet & its associated metadata. Save this inside your `COMP1151_TilemapGame` folder, and give it a meaningful name, like `Tilesheet`.

|   |                                                                                                                                                                                                      Regarding Tiled Instructions                                                                                                                                                                                                      |   |
| --- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------: | --- |
|   | **Tiled **has a lot of features that we could go into, but unfortunately anything past getting a tilesheet and making a tilemap is out of the scope of this prac & the unit. If you are interested in learning more, it is recommended that you do your own research by looking into the[Tiled documentation](https://doc.mapeditor.org/en/stable/manual/introduction), as well as looking into the various tutorials available online. |   |
|   |                                                                                                                                                                                                                                                                                                                                                                                                                                         |   |

## Creating/Editing your Tilemap - .tmx files

Once you have created your tilesheet, you will then need to create a tilemap so you can paint your level (using the tilesheet as a palette).

Select `File > New > New Map ` in the top menu bar. Set the following:

* `Map Size` - `✅Infinite`
* `Tile Size` - (the same as your tilesheet. Again, check the web page where you downloaded your tilesheet)

Then, press the `OK` button. You will then see something like this:

<img src="PracResources\images\03_TilemapEditor.png">

Have a quick play around with the editor. To draw your tiles:

1. Select a tile to paint onto your level using the `Tilesets` window on the side.

* You can zoom in and out of this window by holding `Ctrl` and scrolling with the mouse wheel
* You can also zoom in and out of your tilesheet this way

2. Simply hold left click over a grid space to paint your selected tile

A the top, there is also a toolbar you can use to edit tiles.

<img src="PracResources\images\04_TilemapToolbar.png">

Most of these you will not need, but here are the main ones:

* `E` "**Eraser**" - deletes tiles
* `R` "**Rectangular Select**" - which allows you to select a group of tiles
* `X` to flip tiles Horizontally before placing
* `Y` to flip tiles Vertically before placing
* `Shift+Z` to rotate tiles left before placing
* `Z` to rotate tiles right before placing

These are just the basics, you are more than welcome to dig deeper into the many different tools on offer. Spend some time making a nice looking level. Don't spend more than 15 minutes here, you will be coming back to make changes to your level throughout.

### Tiled Tricks - Layers

It is worth noting that you can create "Layers" in Tiled - these act similarly to programs like Photoshop, where you can separate objects into different layers, and overlay them from one another. You can also imagine that from a level design point of view, it might make sense to have interactables and objects in a separate layer from your Environment tiles.

To add a new layer, simply right-click in the Layers window (while editing a tilemap), and select `New > Tile Layer`.

<img src="PracResources\images\05_TiledNewLayer.png">

Renaming layers works similarly to Unity - simply double click the name of a layer and a input field will appear, where you can change the name. Note that these layer names will be brought over to Unity when you get to that stage, so it would be ideal to give them sensible names (like `Environment` or `Foreground`)

<img src="PracResources\images\06_TiledRenameLayer.png">

You can also temporarily "hide" a layer clicking the eye button, next to the name of a layer.

## Saving and Exporting to Unity

Once you have a neat looking level (or a draft of a level), save your tilemap using `Ctrl + S` (or using `File > Save`).

After you have saved it, we will need to import it into Unity. Open up today's Unity Project, and while that opens start following the next section.

### "Super Tiled2Unity"

Natively, Unity does not support the file types that **Tiled** creates. However, there is a community Unity Package called "**Super Tiled2Unity**" which does what you can imagine. We will be using this to import our Tiled files in to Unity.

If you saved your **Tiled** files in your Unity project, you can simply install this and it will update as changes are made. If you have saved your **Tiled** files in another directory (e.g. Documents), you will continuously need to copy/paste them in to Unity when you have made changes.

To install Super Tiled2Unity:

1. Download Super Tiled2Unity - **version 2.3.1**. You can install them from one of two places
   * The [itch.io page](https://seanba.itch.io/supertiled2unity)  (Recommended)
   * [Github](https://github.com/Seanba/SuperTiled2Unity/tree/master/deploy) (Not Recommended)
2. Once the .zip folder has been downloaded, unzip the folder. Leaving the unzipped folder in your Downloads folder is fine
3. In Unity, we'll need to import the package using the **Package Manager**. Navigate to the Package Manager (`Window > Package Manager`), then press the `+` button at the top of the window, and select `Install Package from disk`

<img src="PracResources\images\07_PackageManagerPlus.png">

1. In the popup window, navigate to the unzipped package we just downloaded, and select the `package.json` file within to add it to Unity

<img src="PracResources\images\08_SelectPackageJSON.png">

After this, the package should be added. Close the popup window, and navigate to where your Tiled files are located. Your `.tsx` and `.tmx` should look like this if you were successful:

<img src="PracResources\images\09_TMXandTSX_Unity.png">


|   | Further Reading                                                                                                   |   |
| --- | ------------------------------------------------------------------------------------------------------------------- | --- |
|   | Further Documentation on Super Tiled2Unity can be found[here](https://supertiled2unity.readthedocs.io/en/latest/) |   |
|   |                                                                                                                   |   |

## Importing your Tilemap into Unity

Open your `Game` Scene, and simply drag & drop the .tmx file from your **Project** window, into your **Hierarchy**. And just like that, your tilemap should be in Unity.

However, it is worth noting that the default pixels per unit is probably too large. Select both the .tmx and .tsx files in your **Project** window, and change their `Pixels per Unit` in the Inspector (this is the same as your tile width/height in Tiled), then `Apply` the change. Do this for each file

There are some glaring issues with our scene, but lets put in a Player and start moving around first.

## Setting up the Player

We have given you a lightweight player script graph already. You are free to use this and change it as you see fit. This can be found in the `Scripts` folder. We have also already set up the `InputActions` asset file in this repository


|   | Gamepad Usage                                                                                                                                                                                                    |   |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --- |
|   | The**InputActions** has been set up with a basic implementation of gamepad support. If you would like to test your game using a controller, feel free to do so (ask your TA about controller access in the labs) |   |
|   |                                                                                                                                                                                                                  |   |

To implement the player in your scene, you will need to change the following on the already existing Player object:

* Attach the Main Camera as a child of the Player
* Add a sprite to the player - Add a `Sprite Renderer` component, and select one of the player sprites from your tilesheet
  * If your tilesheet doesn't have one, simply use the `UISprite` image or make the Player from scratch with a 2D primitive shape (right-click in the **Hierarchy** and select `2D Objects > Sprite >...` )
* Add a `Rigidbody 2D` to your player
  * Ensure it's type is `Dynamic`
  * Set `Gravity Scale` to `0`
  * Tick the `Constraints > Freeze Rotation > ✅Z` checkbox
* Add a `Collider2D` to your player. Depending on your sprite, a sphere, box or polygon collider would be the most appropriate.

You will notice that the world isn't at all what we'd like at the moment. Our level has gaps/seams which look quite ugly, and our tiles have no collision. Let's address these now

### Adjustments to your Tilemap - Removing Seams

Due to how our Tilemap files are read, Unity has a hard time determining the shape of our grid when we move around, causing seams to appear.

The issue is quite convoluted, but has thankfully been addressed in the new version of "**Super Tiled2Unity**". To fix this issue you will need to do the following:

1. In your `Tiled > TilemapGame` folder, make a "Sprite Atlas" -- Navigate to your **Project** window and Right Click - `Create > 2D Sprite Atlas` . Essentially this is a Unity friendly version of your Tilesheet file Tiled uses, more can be found about Unity's Sprite Atlas [here](https://docs.unity3d.com/ScriptReference/U2D.SpriteAtlas.html).
2. Select your **Tilesheet**/.tsx file, click the `>` arrow to open up the contents of the file, and select all of the .png images.
3. Drag and drop the images on top of the `Objects for Packing` text in the Inspector window -- **specifically drag it on top of the text, next to the down arrow** (Do not add them manually, as it is quite tedious).
   * You may need to *lock* your **Inspector** window to do this easily, as selecting then dragging into the Inspector can be quite finicky. Your TA can show you how to do this, but essentially click the padlock icon to the top-right of the **Inspector** window tab

From here, the seams will be fixed, but your level will likely suddenly become blurry. To resolve this, in your Sprite Atlas change the following:

* Make sure `☐ Tight packing` is not ticked
* Set `Max Texture Size` to `128` (do not make it higher than 512)
* Ensure `Format` is set to `Automatic`
* Set `Compression` to `None`
* Change `Sprite Filtering Mode` to `Point` (this is usually the main cause of blurry sprites)

You will be prompted to save your Sprite Atlas when clicking away, press `Save`. Play your game and test if the seams still appear

### Adjustments to your Tilemap - Tilemap Colliders

You may be worried that we will need to go through and add colliders manually in the scene, but thankfully that is not needed. Instead, we can do that directly in **Tiled** itself.

Go back to Tiled, and select your Tilesheet file (the tab with `.tsx` at the end). Once you've done that, open up the `Tile Collision Editor` by navigating to the top menu bar, and selecting `Tileset > Tile Collision Editor`.

Select a tile you want to use as a wall, ideally a completely solid wall. Once selected, in your **Tile Collision Editor** window press the `Detect Bounding Box` button, and it will guess what the collider should be

<img src="PracResources\images\10_DetectBoundingBox.png">

From here, you can use the handles on the outside of the sprite to reshape your tile collider. Do this for all tiles you wish to change, then save your tilesheet.

You will notice that in your tilemap editor, you should now see a *slight* outline of your colliders.

Make any further edits you wish to your tilemap, and go back to Unity.

Before playing your game, Add a`Tilemap Collider 2D` to any tilemap layers that you want to have collision - you can tell which children they will be as they will have a `Tilemap` component:

<img src="PracResources\images\xx_TilemapCol.png">

Play your game and you should now not be able to walk through your wall tiles

Note: While developing, you may want to reshape some colliders (e.g. like the player sprite, as it may be a bit too wide of a collider). It would be quite helpful if we could easily see our colliders when doing this.

Selecting the Tilemap Layer in the Unity **Hierarchy** is a reasonable way to go about getting this information. However, probably the best way to get a visual of the colliders of your tilemap in Unity is definitely briefly changing your view mode to `Wireframe Draw mode`, and selecting the object you wish to check colliders for.

<img src="PracResources\images\11_WireframeDrawMode.png">
<img src="PracResources\images\12_ColliderWireframe.png">

### Adjustments to your Tilemap - Order in Layer

You may find the player disappearing behind certain objects. In the Player `Sprite Renderer`, and each tilemap layers `Tilemap Renderer`, check that the `Order in Layer` ordering is correct.

This was covered in the first few pracs, so this won't be covered in detail. Just remembered that the highest number appears at the top. If you want your player to stand over your foreground, make sure its `Order in Layer` is higher than the other layers.

### Adding hazards for the player

Once you're at a level where you're satisfied with your level, let's start adding a bit more gameplay & add some hazardous tiles.

In Unity, quickly make two new layers, one called `Hazard`, and one called `Player` (We will not need the player layer for now). It would also make sense to set up your **Layer Collision Matrix** - for now you can just make sure that Players can collide with Default and Hazards

In **Tiled**, navigate to your Tilesheet and select an unused tile, ideally one that we can put on a foreground layer, or one that specifically looks dangerous. The TinyDungeon tilesheet features some icon tiles, which are quite simple in their appearance, and will be used for this activity.

<img src="PracResources\images\13_TinydungeonHazardTile.png">

Add a collider to your chosen hazard tile like previously. Once you've done that, look over to the **Properties** window in Tiled. If you have accidentally closed that window, you can open it back up by navigating to the top menu bar, and selecting `Tileset > Tileset Properties`.

Right-click the `Custom Properties` header at the bottom, and select `+ Add Property`. You will see this popup window:

<img src="PracResources\images\14_AddPropertyTiled.png">

Whichever tile you have chosen, we will be putting it on its own layer and marking it as a trigger - Tiled will automatically do this for us when we save our tilesheet.

In the popup window, type `unity:layer`. Check the spelling, then press `OK`. You will then be prompted to type a value in to the newly created field in the **Custom Properties** window. Type `Hazard` in to this field.-

It should look like this if completed correctly

<img src="PracResources\images\15_unityIsHazard.png">

Repeat that process, but this time make the name `unity:IsTrigger`, and the value `true`

<img src="PracResources\images\16_unitylayer.png">

Save your tilesheet, then place that new tile in your tilemap (on any layer you prefer) then navigate back to Unity.

If you were to select the layer on your tilemap, and then expand the parent object completely (Hold `Alt` while clicking the `>` arrow on the layer name), you should notice that there is a new object called `Collision_Hazard`. Selecting the object should also highlight the collision tiles placed in your Scene.

<img src="PracResources\images\xx_TriggerTileHighlight.png">

To test this, add some functionality to your Player Script to check if it is colliding with the "Hazard" layer. You should have a good idea on how to do this already.


|   | Regenerate nodes                                                                                                                                                                                               |   |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --- |
|   | Since this is a fresh repository with custom nodes being placed in, make sure you regenerate your nodes if you you cannot find certain nodes --`Edit > Project Settings > Visual Scripting > Regenerate nodes` |   |
|   |                                                                                                                                                                                                                |   |

Once you've finished developing that, test and see if it works. If it does not, check the following:

* All of the colliders are `2D`
* Your `Layer Collision Matrix` is correctly set up
* You are using the `OnTriggerEnter2D` node, not the 3D version

Once you've got that working, copy and paste the logic, but instead link it up to an `OnTriggerStay2D` event node.

You should end up with something like this when you're done:

<img src="PracResources\images\17_TriggerLogicHealth.png">

Test this, and see if you are also getting events for `OnTriggerStay2D`.

You will likely find that during testing the hazard, the debug logs will sometimes stop when the player is not moving is happening.

This is because the Rigidbody will sometimes "go to sleep" to help with performance. However, in our case we might want to the player to keep taking damage (for example, if they are standing in lava). We'll go over the intricacies of the Rigidbody in a future prac, but for now navigate to the Rigidbody2D you placed on the Player, and set `Sleeping Mode` to `Never Sleep`

## User Interface - Health

We're now going to add some health to the player, and track it using some text. There are obviously other ways to do this (like a health bar), but concious of time, this has been moved to next week.

To get started with this:

* In your **Hierarchy** right click & Select `UI > Text-TextMeshPro`
* A popup window will appear, asking you to install "**Text Mesh Pro**". Select `Import TMP Essentials`, and once it is done, close the popup window

You will now have a text object on the screen of your game, keep in mind that this does not exist within the play space.

Note that when modifying text, the "box" it appears in represents your entire screen. You will likely need to zoom quite far out to be able to see everything. Alternatively, double-click on the UI asset you are editing (or the Canvas itself) to quickly snap to the object

### Health as Text

To make our health system work with our hazard system, we'll only need to add the following variables to our player.

Add these variables:

* `healthValue` (Type: `Integer`) - make this a number larger than 10 since we are losing health every frame/in OnTriggerStay. I picked 99
* `healthText` (Type: `TM Pro > Text Mesh Pro UGUI`) - this will contain the reference for our text field

The logic is quite straightforward, and will not be anything challenging:

1. Use our already existing functions for `OnTriggerEnter/Stay`, but simply delete the Debug Logs
2. Once those are deleted, hook the output triggers for both of these to a new `SetVariable` node, where `healthValue` is being set
3. Get the current `healthValue` node, and subtract 1. The output of this subtract node should be setting our previously created `Set Variable`-`healthValue` node.

Once you've done that, to update the text:

1. Drag the output flow to a `Text Mesh Pro UGUI: Set Text` Node

This node looks like this:

<img src="PracResources\images\18_SetTextNode.png">

It can be quite tricky to find as there are lots of options within TextMeshPro. Simply put though, you attach your text reference (variable), and set the string you wish to update. This is a bit tricky for us though, since the type we're wanting to input is not a string...:

2. Create a `GetVariable` for our healthValue need, and feed it into  a `Integer To String ()` node - this node is quite straightforward, and simply converts our number to text.

You may also want to go ahead and create an `OnStart` event node that runs `SetText` at the start, otherwise it will be left as default text

Once you're done, you should have something like this:

<img src="PracResources\images\19_HazardFunction.png">

Save and Play, and check that this works.

### Anchors and Pivots

If you try to resize your **Game** window, you will notice that the text goes off of the screen. This is where **Anchoring** and **UI Scale** come in.

To fix this:

* On the **Canvas** object that was created before, find the `Canvas Scaler` component, and set it's `UI Scale Mode` to `Scale With Screen Size`
  * Underneath this, give it an appropriate `Reference Resolution`. Typically you should give one suitable for the aspect ratio you are playing in (e.g. 16:9 screens can simply use x`1920`y`1080`)
  * While you're here, change `Reference pixels per unit` to whatever your tilesets are using

<img src="PracResources\images\20_CanvasTweaks.png">

* On your Health **Text** object, navigate to the **Rect Transform** component, and select the Anchor Presets, and select an appropriate pivot point. Doing this will ensure it stays in that corner of the screen (relative to where you've placed it)

<img src="PracResources\images\21_HealthTextTweaks.png">

Try resizing your screen now, and you should see the difference

Please complete one challenge for today

## Recommended Challenge - Expand your level

Spend some time making your level more diverse and expansive. You may wish to add new tilesheets to your Tiled project to help you

## Recommended Challenge - Sprite changes according to faced direction

Add some logic in to your `Player` script, that determines whether they should be facing left or right.

For this challenge, it is recommended to change the `Flip` tickboxes in the **Player** `Sprite Renderer`. You will also likely want to be tracking this with a boolean variable on the player

## Moderate Challenge - Add an Invulnerability Window/Timer after Taking Damage from a Hazard

Create a performance efficient timer that gives players a limited time invulnerability for taking damage, for a certain amount of time. Please consider the following:

* We would want variables on the player to be able to tweak this (e.g. `invulnTime`, `invulnDurationCurrent`)
* The health UI should correctly reflect the players current health, and should not tick down outside of their invulnerability window
* The timer *must not* tick down every frame - this timer should not exist in "Update"

## Completed Tasks

To verify that you've completed all of the content in this prac, check you have done the following:

* Downloaded a tilesheet from Kenney.NL (e.g. Tiny Town / Tiny Dungeon)
* Made a basic tilemap in Tiled.
* Imported your tilemap in to Unity using [SuperTiled2Unity](https://seanba.itch.io/supertiled2unity)
* Added a TilemapCollider to your Tiled Tilemaps
* Made the camera a child of the player avatar
* Added hazards as trigger colliders which cause damage
* Added a UI to track damage [Raw number & Slider]
* Used anchors & pivots to position UI elements
* Tested different screen aspect ratios

### Show your demonstrator

To show your understanding of this weeks content to your prac demonstrator, you may wish to show:

* Your tilemap editing skills in Tiled
* Your Game scene in Unity, featuring the imported tilemap
* The various hazards in your scene
* Your UI, with anchors and pivots (that does not lose key information when changing aspect ratios)
