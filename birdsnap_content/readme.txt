Birdsnap Dataset v 1.1.

Welcome to the Birdsnap dataset, consisting of 49,829 images of 500 species of
North American birds, collected from Flickr, and corresponding species,
bounding box, and part labels.

The dataset was introduced in the paper "Birdsnap: Large-scale Fine-grained
Visual Categorization of Birds," by T. Berg, J. Liu, S. W. Lee,
M. L. Alexander, D. W. Jacobs, and P. N. Belhumeur (CVPR 2014).

The dataset distribution consists of the following files:

1. species.txt
This file lists the species in the dataset.  The first line is a header.  Each
subsequent line represents a species.  Lines are tab-delimited, and the fields
are:
- id: An integer id for the species.  These ids run from 1 to 500 for the 500
  species.
- common: The common English name of the species, for example "Blue Jay."
- scientific: The scientific (Latin) name of the species, for example
  "Cyanocitta cristata."
- dir: The name of the a directory in which to store the images of this
  species.  This is just the common name with spaces and other
  dangerous-in-file-path characters replaced or removed.

2. images.txt
This file lists the images in the dataset, with the coresponding bounding
boxes, part locations, and species labels.  Like species.txt, it is
tab-delimited with the first line giving field names.  The fields are:
- url: The URL from which the image was downloaded.
- md5: An MD5 sum of the image file constants.
- path: The local path of the image.
- species_id: The id of the species of the labeled bird in the image.
- bb_x1, bb_y1, bb_x2, bb_y2: The coordinates of the top-left (bb_x1, bb_y1)
  and bottom-right (bb_x2, bb_y2) corners of the bounding box of the labeled
  bird.
- ${part}_x, ${part}_y: The coordinates of part ${part}.  Parts are back, beak,
  belly, breast, crown, forehead, left_cheek, left_eye, left_leg, left_wing,
  nape, right_cheek, right_eye, right_leg, right_wing, tail, throat.

3. test_images.txt
This file lists the 2443 test images used in the species identification
experiments in the paper.  It has a header line, then the "path" (from
images.txt) of each test image, one per line.

4. get_birdsnap.py
This python script will read the data files from the dataset and attempt to
download the original images from Flickr.  To get the images, run
    python get_birdsnap.py
from the command line.  Or run
    python get_birdsnap.py -h
to see a few options.  In addition to downloading the images, the script will
write a detailed log, and will create files success.txt and fail.txt listing
the images that were and were not successfully downloaded.  Running the script
additional times will only attempt to download the images that you don't
already have (so you can kill the script and restart it later if necessary).

5. readme.txt
This file.

Version History:
2015-01-25 Release 1.0
2015-03-30 Release 1.1, adding file test_images.txt
