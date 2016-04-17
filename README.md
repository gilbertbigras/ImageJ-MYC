
IHC MYC
==========
This software refers to this article published in Applied Immunohistochemistry & Molecular Morphology.

Prerequisites and software installation
This software requires installation of imageJ, an open source software written in Java, available for Linux, Mac OS X and Windows. ImageJ is available [here](https://imagej.nih.gov/ij/). Basic understanding of ImageJ will facilitate installation.
Current software (MYC_IHC.txt) is a "toolset" written in macro language and requires to be installed in the following directory:
```
→ ImageJ → macros → toolsets.
```

Two additional "plugins" are required:
* Color Deconvolution plugin written by Gabriel Landini is available [here] (http://www.mecourse.com/landinig/software/cdeconv/cdeconv.html) with documentation.
* Euclidean minimum spanning tree plugin written by Gilbert Bigras available [here] (http://imagejdocu.tudor.lu/doku.php?id=plugin:morphology:euclidean_minimum_spanning_tree:start).

Colour deconvolution and Euclidean minimum spanning tree plugin names are respectively: "Colour_Deconvolution.class" and "e_mst.jar". Both files (plugins) have to be installed in the following directory
```
→ ImageJ → plugins
```
Prerequisites for IHC analysis
==========
Since the purpose of this analysis is to be a predictor of MYC dysregulation, It is expected that pre-analytical and analytical variables are optimized and controlled as other [class II Biomarkers] (http://www.ncbi.nlm.nih.gov/pubmed/26286753)

Operator is expected to grab an area of viable tumour with the most intense IHC staining

Operator is expected to grab a picture with a priori correction of background illumination as explained [here] (http://imagejdocu.tudor.lu/doku.php?id=howto:working:how_to_correct_background_illumination_in_brightfield_microscopy) by Gabriel Landini.

This involves multiple steps a) Image acquisition of a white field without oversaturation and white balance of RGB channels b) Image acquisition of a black field c) Image acquisition of the tissue specimen and d) the correction itself.
Software utilization
---------------


Icons | Description
------------ | -------------
![](/image/selector.png) | Click the icon  and select MYC_IHC,dkow3pdk kdop dko kdwo kdow dko kdow kdo kdow you should see the following icons
Content in the first column | Content in the second column



The output:

![hello](ImageJ_034.png) 

Feedback
-----------------

Please send me your feedback

