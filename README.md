# 2022-MN-map-quilt-gon-wild <!-- omit in toc -->
A fun side project for 2022 [NACIS](https://nacis.org/)

This repo was utilized to document the process of creating a static map quadrant or 'quilt square' for the NACIS 2022 Minneapolis Minnesota Mapping quilt revealed at the Annual NACIS 2022 Conference in (you guessed it) Minneapolis Minnesota.

It has become a NACIS tradition to showcase an annual Map Quilt at the meeting. A handful of cartographers each volunteer to work on a small portion of a larger map that focuses on the host city for the meeting. The only information provided is the Deliverable Prerequisites and an assigned quadrant. Mappers have no idea what any other mappers are working on for their particular quadrant. All styles are unique to each map designer/cartographer.   

NACIS member David Lambert, has spear headed this project for the last 9 years. He is the Quiltmaster who stitches all of the quilt tiles back together. This year I was lucky enough to be a participant in this fantastic tradition for the **10th Anniversary of the Carto Quilt** and this repo will serve as the home for my individual tile/quadrant. Below is a brief overview of my creative process, for more details please reference the Jupyter Notebook within this repo.  


## TOC <!-- omit in toc -->
- [Deliverable Prerequisites](#Deliverable-Prerequisites)  
- [Initial Inspiration](#Initial-Inspiration)
- [Data and Symbology](#Data-and-Symbology)
- [Assign Rules](#Assign-Rules)
- [Ramsey Final Product](#Ramsey-Final-Product)
- [NACIS 2022 Final Quilt](#NACIS-2022-Final-Quilt)

## Deliverable Prerequisites
**Projection**: NAD83_UTM_zone_15N  
 
**Size of tile**: 12  x 17"  
**Scale of map**: 1:15,000  

*300 DPI image in a format supported by Adobe Illustrator, either clipped to your extent or georeferenced, and properly sized, scaled and projected.*  

## Initial Inspiration
When looking at the quadrant assigned there were two main features that caught my eye.  

1. Bell Museum   
2. Como Park Zoo and Conservatory   

The Museum and Conservatory are built around displaying and educating Minneapolis about various wildlife both local and exotic. This animal focus prompted some thoughts from me:  
- *What if animals ruled the city again?*  
- *What would the animals use the roads for? Paths? Leaving behind tracks?*  
- *Would any animals claim a road as their own dedicated highway? Could mark it with animal patterns, stripes, spots, etc.*  
- *I couldn't leave out silhouettes of animals and vegetation. Animals need somewhere to live*   
- *If the animals had a choice in symbolizing something on the map, what would they choose? Eco-friendly items?*   

All in all, I had a cohesive concept:  
**A flip of the narrative returning Minneapolis back to a wildlife centric space.**  

So I considered **Symbology/Patterns** for this area:

**Road hierarchy For Patterns & Tracks**    
- Upper hierarchy roads would have patterns (later abandoned this idea, reference jupyter notebook for details, but it all boiled down to preferring tracks for all roads over my ability to produce animal patterns in roads). 
- Lower would have animal tracks  
    - During my internet search for how digital cartographers incorporated tracks into their maps I stumbled across Alina Gerlee's page.  
    - [Alina Gerlee Track SVG (point or line)](https://alinagerlee-pl.translate.goog/tropy-slady-qgis/?_x_tr_sl=pl&_x_tr_tl=en&_x_tr_hl=en&_x_tr_pto=sc) Alina's webpage was written in Polish so her page does need to be translated if Polish is not a familiar language for you. When translated by google she said: "*I didn't write for a long time, but at that time I prepared a style package for naturalists - animal tracks and tracks (for point and line layers). To be installed and used by the **QGIS Resource Sharing plugin**. Take it and use it!*"  

    - Alina's symbols
    <img src = ./images/alina_gerlee_symbols.png width = "600" height = "300">
    
    - Alina's page contained the steps for accessing the **QGIS Resource Sharing Plugin** which is how I accessed her SVGs she prepared. Referenced this [Youtube Video by burdGIS](https://www.youtube.com/watch?v=kAf0Bxs1Ljc&list=PLiITJ9X8KPoizHXQbwAW5elJLBKCY2yQI&index=1) for video demo of how to incorporate new opensource SVGs to QGIS symbology.
        
    - The QGIS Resource Sharing Plugin allows access to an assortment of shared SVGs and other resources. The plugin was originally developed as part of GSoC 2016 project (Google Summer of Code) by Akbar Gumbira, H??vard Tveite, and Julien Moura. The plugin allows users to search for available collections and install them. Users can also create repos to put in the collection or contribute to the resource sharing their own collection of SVGs.
    - Animal tracks and silhouettes used were selected after taking a deep dive into animals represented at the Bell Museum, animals present at Como Park Zoo & Conservatory and [Iconic Animals of MN](https://www.mprnews.org/story/2019/07/26/a-field-guide-to-minnesotas-iconic-animals) (MPR news, Daniel Ackerman).    
   
**Plantlife**
- Place vegetation throughout as buildings?
- The road tracks and animal patterns would then look like they are hiding/camouflaged among the plant life...

## Data and Symbology
- Used QGIS OSM plugin ([QuickOSM](https://plugins.qgis.org/plugins/QuickOSM/)) to pull roads, buildings, amenities. This data was used to create the basemap for the project. 
- Used [Inkscape](#https://inkscape.org/about/) to supplement animal silhouettes or tracks not found in Alina's SVGs
    - Utilized Alina's Moose (Body and Tracks), Otter (Tracks for Beaver ????), Wolf (Body & Tracks), Bear (Body & Tracks) and Lynx (Tracks).
    - I created Beaver (Body), Loon (Body & Tracks), and Lynx (Body) in Inkscape. (Initial images from [Pixabay](https://pixabay.com/) for pulling free and open use images/SVGs for baseline, then modified the base image to fit my needs)
- Decided on color palette using Coolors and selected an earthtone colors scheme that appeared different enough between all colors that all could be deciphered between for varying vision abilitites. [Ramsey Coolors Color Palettes](https://coolors.co/u/rebecca_ramsey1)  

    <img src = ./images/coolors_palette.png width = "600" height = "200">

## Assign Rules
With my animal tracks created or accessible and animal silhouttes ready to wander around my map I set ground rules for where and how to assign these symbols.

- Roads (Tracks)
    - Lynx Tracks = Motorway  
    - Loon Tracks = Primary  
    - Wolf Tracks = Secondary  
    - Moose Tracks = Tertiary  
    - Bear Tracks = Path  
    - Beaver Tracks = Service  
- Buildings
    - Used tree SVG standard with QGIS 3.16. (*C:/PROGRA~1/QGIS 3.16/apps/qgis-ltr/svg/gpsicons/tree.svg*)
    - Only symbolized buildings > 3000 meters squared (otherwise the quadrant quickly covered up basemap if all buildings were represented)
    - Called out Bell Museum and Conservatory with a darker green (#1D3527) and larger symbol. (This quadrant was inspired by them ???? after all)  
- Amenities
    - Moose = Bicycle Rental Location  
    - Beaver = Bicycle Repair Station  
    - Loon = Charging Station  
    - Lynx = Recycling areas  
    - Bear = Veterinary  
    - Wolf = Public bookcase  

    I knew from go I wanted to add animals into the picture since that is the entire theme of this quadrant. I also wanted to be intentional with regards to what the animals represented. If Minneapolis were to really *Go Wild*, I would want the animals to represent EcoFriendly Amenities they would approve of or perhaps be partial to. 

## Ramsey Final Product
With all rules in place and data reduced to a reasonable visual representation (no not every amenity or building or road was represented see Jupyter Notebook for details of reduction) a final pdf was produced. David then worked his magic to stitch it together with the other maps producing the true masterpiece.

![Ramsey completed map quilt tile](images/map_quilt_print_tile.png)
**Figure** Ramsey Quadrant of Minneapolis Minnesota.

## NACIS 2022 Final Quilt
Mad props to all those who contributed to this project and whose work is shown below including: David Lambert, Mike Foster, Nat Case, Brian Davidson, Christina Shintani, Ross Thorn, Neil Allen & Taylor Monroe, Nick Lally, Sarah Bell, and Adam Cox.
![Final NACIS Map Quilt](images/2022_NACIS_MN_Carto_Quilt_Stitched.png) **Figure** Final NACIS Map Quilt from all contributors.
