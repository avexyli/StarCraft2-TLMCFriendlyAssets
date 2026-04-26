# StarCraft 2 TLMC-Friendly Assets
This repository contains models, effects and textures for StarCraft II mapmakers primarily for the use of the Team Liquid Map Contest. This readme will explain how to use these assets and their limitations.

## Foreward

All assets contained within this repository are modifications of assets contained within the non-Campaign StarCraft II Liberty, Heart of the Swarm, Legacy of the Void, or WarCraft III dependencies, exported from the Heroes of the Storm dependency with the assistance of the mod [Resurgence of the Storm by zeroLamberg](https://github.com/zeroLamberg/RotS-Mods). All original assets are the intellectual property of Blizzard Entertainment and I do not claim ownership of these modifications. 

Under the [Blizzard's Custom Game Acceptable Use Policy](https://www.blizzard.com/en-us/legal/2749df07-2b53-4990-b75e-a7cb3610318b/custom-game-acceptable-use-policy), Section 3, these assets are not considered third party as they belong to Blizzard. These assets are and must remain free to use. These assets are intended for exclusive, non-commercial usage and may not be re-distributed under these means.

## How to Navigate These Assets

The majority of assets are organized within folders affixed with Custom or No_Custom to better separate their contents. Folders with No_Custom as their suffix contain any assets that do not rely on any new textures created by me, and will be the lightest on filesize. Examples of No-Custom assets may be pre-existing StarCraft 2 models with parts of their mesh and bones stripped away, or their materials and textures adjusted or re-mapped to other textures that exist within the non-Campaign Liberty, Swarm or Void  dependencies. Folders with the Custom suffix will always contain at least one texture I have modified or created -- or a texture that has been exported from elsewhere as noted in the Foreward; that is **required** for the model's material to render properly. Examples of Custom assets may be a CliffMaterial with a re-colored emissive, a port of a Heroes of the Storm CliffMaterial or other model, or multiple textures re-assigned to an exported model to completely adjust it's appearance beyond simple No_Custom material alterations.

## IMPORTANT: How to Use These Assets

This is a guide on how to Import and Implement both No_Custom and Custom assets from this repository, I will be referring to both as "Imported Assets" throughout this guide.

* Download the release ZIP file or copy from the master, they'll be identical. 
* Export the ZIP into your directory of choice, make it relatively to access (i.e your desktop, documents folder, somewhere not too nested), the editor does not have breadcrumbs and utilizes the old treebranch file navigation method.
* Open your Game Editor (Battle.Net Launcher > StarCraft II > Launch Editor) (Usually in Program Files\StarCraft II\Support64)
* Create a New Document (Ctrl+N) or Open one you've already made (Ctrl+O); if you're making a new one, select Melee Map, choose the Legacy of the Void dependency, select whichever Terrain Type you want and click OK. 
* At the top bar, click Modules > Import (F9)
* Right click on the space on the left and choose Import Files (Ctrl+I), navigate to where you exported the ZIP. 
* **IMPORTANT:** For Custom imported assets only, **only** import the textures included with the associated files first. Make sure all imported textures are brought in under the *Assets/Textures* hierarchy, if they are not, select them all, right click them and choose Move Files (Ctrl+M), select New Path and manually type *Assets/Textures*. 
* **If you did the above, SAVE YOUR DOCUMENT**. Then import the models, they maintain their folder paths from the git archive, which will be Assets/Cliffs for any CliffMaterial, Assets/Waters for any Water or Lava, Assets/Effects for any Particles, whilst the rest fall under Assets/Doodads. If done correctly, there should be no texture or material errors. See the FAQ for more. 
* For any No_Custom imported assets, import the selected models and ensure they follow their Assets/Doodad paths, then **save your document.**
* Click on Modules > Data (F7), and head to the appropriate section for your associated asset. You will be utilizing the small tab with the green plus to navigate through various submenus.

### Applying Terrain Cliffs

* Navigate through Edit Terrain Data > Terrain Cliffs
* Refer to the .txt file in the archive that corresponds with your imported asset, the file name for this .txt file is the Cliff Mesh that is **required** for this Material; whilst some Materials *may* fit on other meshes, it is strongly recommended for beginners to utilize this one.
* Search through the Terrain Cliffs until you find one that has a matching Cliff Mesh, then replace the (Basic) Cliff Material .m3 with your newly imported CliffMaterial. 
* Save your document, if you are overwriting a cliff that is already present on your document, you will need to close and re-open it for changes to take effect.

### Applying Terrain Textures

* Navigate through Edit Art and Sound Data > Terrain Textures
* Find any Terrain Texture you would like to replace, or create a new one (Ctrl+=)
* Change the (Basic) Texture field to your newly imported Terrain Texture that is ***not*** a _low .dds file and *not* a normal map. I recommend placing this texture into (Basic) Editor Icon as well.
* Change the (Basic) Normal *and* (Basic) Height Map (if you are using Height Blending and the Normal Map has a red Height channel) field to the corresponding Terrain Texture's normal - it will have the exact same file name with the _normal suffix. 
* Change or add a name as you please.
* Save your document.
* Navigate through Edit Terrain Data > Terrain Types
* Find the Terrain Type you are currently using, or plan to use.
* Edit (Basic) Textures - Blend + 
* If your Terrain Type has 8 Textures loaded, you will need to click on one on the right that you wish to replace, and scroll through the left side to find your new texture, before clicking Replace. If there are 7 or less textures, you may find the texture and simply press Add. Then press OK.
* If you wish to utilize Height Blending, ensure (Basic) Height Map Enabled is set to Enabled
* Save your document.
* If followed properly, the texture will appear and blend (if using Height Map Enabled) correctly. Check FAQ for more.

### Applying Models

#### A warning about Models: some models may have higher vertex counts than others, unique use of particle effects or shaders. Be mindful how you use these external models, utilize Wireframe Mode, swap Graphics modes, and check ingame performance for the comfort of our playerbase.

* Navigate through Edit Art and Sound Data > Models
* Locate the model you wish to swap.
* Open the (Basic) Art: Model to the browser:
* If your model has many variations (such as _00, _01, _02, etc.), click on any of them.
* Press Ctrl+D to enter Raw Data View, your path for (Basic) Art: Model should look like
Assets/Doodads/importedassetmodel_00.m3 (or something similar)
Place your typecursor at the end of the last digit, before the period, and delete the variation numbers and the underscore. Using my example, my path now looks like Assets/Doodads/importedassetmodel.m3 
* Press Ctrl+D again, and save your document. If you elected to import *fewer* assets than what was originally provided in the git archive, you **must** update (Basic) Art: Variation Count to reflect the new total count, starting from 00. 
* Some recommended "unused" models that are safe for swapping out for Custom imported assets are Test Model 1A, 1, 1C, 1D, 2 & 3; the various shapes such as ActorShapeCone or ActorShapeSphere, etc.



