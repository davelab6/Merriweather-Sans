Open all the UFOs in Glyphs v2.3b

File, Export to your Desktop, choose to remove overlaps, autohint, and do not save as TrueType

Make a directory for the release

    mkdir 2016-02-30
    cd 2016-02-30

and copy the built files in

    mkdir OTF;
    mv ~/Desktop/MerriweatherSans-*.otf OTF/;

File, Export to your Desktop, choose to remove overlaps, do not autohint, and save as TrueType

Then hint the fonts with ttfautohint v1.4.1

    mkdir TTF;
    cd TTF;
    mkdir UNHINTED;
    mv ~/Desktop/MerriweatherSans-*.ttf UNHINTED/;
    for i in `ls -1 UNHINTED/*ttf`; do \
      echo $i; ttfautohint -l 6 -r 50 \
      -G 0 -x 11 -H 220 -D latn -f none \
      -w "" -X "" -I \
      $i $i-ta;
    done;
    mv UNHINTED/*-ta . ; 
    rename s/ttf-ta/ttf/g *;

Then fixup the TTX files by hand, correcting the NAME table

    cd ../..;
    ttx -s 2016-02-30/*/*tf;
    mate */*x 

Then recompile

    ttx 2016-02-30/OTF/MerriweatherSans-ExtraBold.ttx
    ttx 2016-02-30/OTF/MerriweatherSans-ExtraBoldItalic.ttx;
    ttx 2016-02-30/OTF/MerriweatherSans-Bold.ttx;
    ttx 2016-02-30/OTF/MerriweatherSans-BoldItalic.ttx;
    ttx 2016-02-30/OTF/MerriweatherSans-Italic.ttx;
    ttx 2016-02-30/OTF/MerriweatherSans-Light.ttx;
    ttx 2016-02-30/OTF/MerriweatherSans-LightItalic.ttx;
    ttx 2016-02-30/OTF/MerriweatherSans-Regular.ttx;
    ttx 2016-02-30/TTF/MerriweatherSans-ExtraBold.ttx;
    ttx 2016-02-30/TTF/MerriweatherSans-ExtraBoldItalic.ttx;
    ttx 2016-02-30/TTF/MerriweatherSans-Bold.ttx;
    ttx 2016-02-30/TTF/MerriweatherSans-BoldItalic.ttx;
    ttx 2016-02-30/TTF/MerriweatherSans-Italic.ttx;
    ttx 2016-02-30/TTF/MerriweatherSans-Light.ttx;
    ttx 2016-02-30/TTF/MerriweatherSans-LightItalic.ttx;
    ttx 2016-02-30/TTF/MerriweatherSans-Regular.ttx;
