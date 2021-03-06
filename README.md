Kuwahara filter (in a UIImage category)
========

A simple category on UIImage that implements the Kuwahara filter.
Meant to be used in iPhone/iPad projects that perform image manipulation.

## The filter ##

The Kuwahara filter was originally presented here:
* Kuwahara, M., et al., *Processing of RI-angiocardiographic images*, in Digital Processing of Biomedical Images, K. Preston and M. Onoe, Editors. 1976, Plenum Press: New York. p. 187-203.

Readily accessible information about such filter is here:
* http://en.wikipedia.org/wiki/User:DinoVgk
* http://pippin.gimp.org/image_processing/chap_area.html
* ftp://ftp.tudelft.nl/pub/DIPimage/docs/FIP2.3.pdf

## Implementation ##

This implementation of the Kuwahara filter aims to be fast, tought I've not compared it extensively with other image manipulation libraries.

* The approach is fully CPU-based (as opposed to other implementations that leverage the GPU, see e.g. https://raw.github.com/BradLarson/GPUImage and http://www.kyprianidis.com/p/gpupro/).
* The filtering code is mostly written in pure C, with a light Objective-C wrapper.
* <a href="http://en.wikipedia.org/wiki/Grand_Central_Dispatch">GCD</a> and the <a href="http://developer.apple.com/library/ios/#documentation/Accelerate/Reference/AccelerateFWRef/_index.html">Accelerate framework</a>
 are employed to speed up computations.
* Last but not least, a **dedicated incremental algorithm** is used to compute the filter.

This implementation is meant for still images, not live video frames (for this filter, real-time performace on iOS devices seem difficult to achieve by either the CPU or the GPU).

## License ##

BSD-style license. Can be used in commercial and non-commercial projects.

## Other OS implementations of this filter ##

* http://rsbweb.nih.gov/ij/plugins/kuwahara.html [Java]
* https://github.com/BradLarson/GPUImage/blob/master/framework/Source/GPUImageKuwaharaFilter.m [GLSL]
* https://github.com/dscho/fiji/blob/master/src-plugins/Kuwahara_Filter/src/main/java/Kuwahara_Filter.java [Java]
* https://github.com/novas0x2a/isis3/blob/master/src/base/apps/kuwahara/kuwahara.cpp [CPP]
* https://github.com/mahogny/Endrov/blob/master/ev/endrov/flowImageStats/EvOpKuwaharaFilter2D.java [Java]