# tiled_to_gm_properties_fix
Semi-automated bat/sh script for fixing missing inheritence in .yy file that was been exported from Tiled .

This entire thing most likely will be useless for your own needs .
I hard-asambled this script with Notepad++ macro feature . I.e. simple to creeate , but hard to rewrite for something else (though i also include "add_entry_in_to_tiled_to_gm_properties_fix_via_notepad_plus_plus.xml") .
But it can be helpfull for you as example how you can post-process .yy file that was been exoprted from Tiled and implement your own inheritence fix or something else .

I use this script to replace few default properties paths (that Tiled produced on export) with inherited ones that are in our game (D'LIRIUM) .

How this work :
For example , we have "e_name" property of the ent_activator in Tiled . On export this object will have "e_name" as it own property . But in our D'LIRIUM project ent_activaotor inherit "e_name" from parent "obj_enity" . When gamemaker will try to read such property it will delete it (or to be correctly it will set propety path to null) , since ent_activator doesnt have own "e_name" .
To fix such error , this script replaced path of the "objects/ent_activator/ent_activator.yy" with "objects/obj_entity/obj_entity.yy" .
And this procedure is repeated for every 9 properties of every 48 ent_ objects .

To execute the script on windows or linux :

1. Create new room in your GMS2 project and name it "import_from_tiled" .
2. Open folder of this new room in file manager and copy bat/sh file in to it .
3. Close GMS2 .
4. Export your map in Tiled by replacing "import_from_tiled.yy" file .
5. Download source code of "gsar" (https://github.com/abronte/gsar) , compile it (with visual studio or vs code or with "makefile") and copy compiled binary "gsar" in to the folder near "import_from_tiled.yy" .
6. Run bat/sh file .
7. Open GMS2 .
8. Open "import_from_tiled" in room editor . If you don't see any "reference missing" errors you are done .