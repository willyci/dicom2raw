dicom2raw
=========
Converting DICOM files to RAW file( s )
	

Usage
--------
	dicom2raw 00.dcm 01.dcm ....
	
	More programs are available (e.g. convert DICOM files to RAW image (3d)).
License
--------
	3-clause BSD License (See COPYRIGHT.txt)

Note 
--------
	This software was developed at Suzuki Laboratory at RCAST, Univ. Tokyo for the research purpose in 2007. 




--------

http://paulbourke.net/dataformats/pvm/



PVM File Format Specification
Format designed by Stefan Roettger
Description by Paul Bourke


PVM format contains information about the grid size, bit depth, and the cell spacing of a volumetric dataset. It can also contain a number of descriptive text fields. This information and the raw data is normally used by the PVM tools distributed with software by Stefan Roettger.

There are a variety of flavours that come under the umbrella of "pvm". They each have a "magic" header identifier, the first N bytes of the file ("PVM\n", "PVM2\n", "PVM3\n", "DDS v3d\n", "DDS v3e\n") and each is described below depending on that file identifier.

PVM
The header is 3 ascii text lines consisting of "PVM" on the first line, the width, height, and depth on the second line, and the number of components (bytes) per voxel on the third line. Since this is ascii the nature of the file can be readily determined with the UNIX command "head -3 thefile.pvm". The data then follows as binary data.

Notes:
The number of bytes in the binary data will be width*height*depth*components.

The three lines of ascii header as a single string will be null '\0' terminated, so one extra byte after the last '\n'.

The voxels are assumed to be cubic.

PVM2

This is the same as PVM except there is an extra ascii line between the dimensions and the number of components. This line has three numbers indicating the relative size of the voxels, that is, providing support for non-square voxels.

PMV3
This is the same as PVM2 except that after the 4th line of the PVM2 header and before the raw data there are 4 null terminated strings. These can of course be used for anything but they are notionally intended for "description", "courtesy", "parameters", and "comment". The maximum allowed length for each of these is 256 bytes.
