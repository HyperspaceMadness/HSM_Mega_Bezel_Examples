

**Multigame background example**

---

This example shows how you can use one preset to load the right background images for many different games automatically. It is set up to automatically have the game image/crt  image scaled and placed properly inside the hole cut into these background images.

---
---

Credit for all the very great arcade background images in this example go to Orions Angel.

Thanks for your wonderful work Orions Angel!

---
---
**How to Try the Example**

The folder arcade_game_images has images for testing this example set. 

If you load one of these images in Retroarch and then load the Multigame.slangp the matching background or slangp will be loaded if it's there, if there is no matching background you will get the default background. The images starting with _no_bg_exists do not have matching backgrounds, so if you open these you will get the default bezel image.



-------------------
**Per Game Adjustments**

If you want to make some additional adjustments for a particular game, here is the procedure:

* Load your game/image with the name of the game
* Load the Multigame.slangp
* Make Parameter adjustments
* Go to the Save page
* Make sure Simple Presets is turned ON
* Save a game preset
* Go to the Retroarch/config folder for the core you were running
* Take the file that it saved, e.g. galaga.slangp
* Move this file to the folder with the background images
* Change the extension of the file to .params
* Open the file in a text editor, I recommend VS Code
Change the path of the reference line to: "_base.params"

Reload Multigame.slangp, it should now load up with your adjustments

-------
**Explanation of how the wildcards work in this example**

* `Multigame.slangp` has a reference to a base preset which gives the look of the crt game * image
* `Multigame.slangp` also has a reference to `$CORE-ASPECT-ORIENT$/_connector.params` this will cause it to choose the _connector.params for the correct aspect ratio of the core image, e.g. horizontal or vertical
* `_connector.params` has a reference to `$GAME$.params`
* When the preset loads if a preset named by the game name is not found then `$GAME$.* params` will be used
* The `$GAME$.params` file has a reference to `_base.params` which has all the basic * parameters and texture paths
* The texture paths inside `_base.params` are all set to `$GAME$.png` if an image named the same as your game exists that will be used, if not the `$GAME$.png` image will be used instead