# tesstrain-win
Train Tesseract LSTM with make on Windows
# About tesstrain-win
The tesstrain-win comes from the  [tesseract-ocr/tesstrain](https://github.com/tesseract-ocr/tesstrain) , In order to make it run on Windows, there are some changes to the makefile and the overall file structure.
The ocrd-train(OCR-D/ocrd-train) is the Predecessor of [tesseract-ocr/tesstrain](https://github.com/tesseract-ocr/tesstrain). Reference it can help us understand the makefile of tesseract-ocr/tesstrain.
# Requirements
## tesseract
You will need a recent version (>= 4.0.0beta1) of tesseract built with the training tools and matching leptonica bindings. Build instructions and more can be found in the [Tesseract project wiki](https://github.com/tesseract-ocr/tesseract/wiki).
Build tesseract instructions on Windows can be found in the [Tesseract4.0+VS2017+win10](https://livezingy.com/compilation-tesseract4-in-vs2017-win10/).
## Python
You need a recent version of Python 3.x. For image processing the Python library Pillow is used.
##Cygwin
In order to run the makefile on Windows, you need the Cygwin. Install instructions could refer to [Install Cygwin on Win10 for makefile](https://livezingy.com/install-cygwin-on-win10-for-makefile/)
# How to Use tesstrain-win
Before training your own database, it is recommended to train [ocrd-testset.zip](https://github.com/livezingy/tesstrain-win/tree/master/data/foo-ground-truth).
If the [ocrd-testset.zip](https://github.com/livezingy/tesstrain-win/tree/master/data/foo-ground-truth) can be trained normally, it means that the current computer training environment is OK.
## How to train ocrd-testset.zip
1. Extract ocrd-testset.zip to ./data/foo-ground-truth.
2. Run the command prompt as an administrator, Go to the tesstrain-win directory, e. g.:
'cd %USERPROFILE%/tesstrain-win'
3. run make training
'make training'

## How to train your own database
1. Give your own database a name
You could give the name by change the line11 in *makefile*
'MODEL_NAME = New Name'

Or you could give the name when you run *make training*
make training MODEL_NAME=New Name

2. Prepare the base traineddata
If you train from scratch, no need to do this. If you train Fine-tune, download the base traineddata from the [tessdata_best](https://github.com/tesseract-ocr/tessdata_best),
and Place it to the ./data/tessdata.

3. Change the foo.numbers/foo.punc/foo.wordlist in data filefolder
The three files should be consistent with the base traineddata. You could download them from [langdata_lstm](https://github.com/tesseract-ocr/langdata_lstm).

3. Prepare the ground truth
Place ground truth consisting of line images and transcriptions in the folder data/MODEL_NAME-ground-truth. This list of files will be split into training and evaluation data, the ratio is defined by the RATIO_TRAIN variable.

Images must be TIFF and have the extension .tif or PNG and have the extension .png, .bin.png or .nrm.png.

Transcriptions must be single-line plain text and have the same name as the line image but with the image extension replaced by .gt.txt.

4.Run the command prompt as an administrator, Go to the tesstrain-win directory, e. g.:
'cd %USERPROFILE%/tesstrain-win'

5. run make training
'make training'

# More Information About Train Tesseract LSTM
More information about Train Tesseract LSTM could refer to [Win10 Tesseract4.1 LSTM training](https://livezingy.com/win10-tesseract4-1-lstm-training/)
