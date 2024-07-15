## To run these models (PhaseNet and EQTransformer) on data with different sampling rate (e.g., 2000 Hz in this study)

### In PhaseNet:

1. In the data_reader.py from this repository, you can change the "sampling_rate = 2000" line to the sampling rate of your choice. I've used 2000 Hz here for my data.
2. In your 'phasenet' model folder, there should be another data_reader.py - replace it with the one you edited. That should read 2000 Hz data easily.

### In EQTransformer:

1. In the mseed_predictor_colab_3.py from this repository, you need to change how the time shift for the sliding window is defined. For our 2000 Hz data, the 6000 sample window will be "tim_shift = (3-(args['overlap']*3))" which is in this file (mseed_predictor_colab_3.py). If your sampling rate is different, divide the 6000 sample window by your sampling rate (x = 6000/sampling_rate), then edit the variable "tim_shift = (x-(args['overlap']*x))". E.g., if your data has a 250 Hz sampling frequency, your tim_shift = (24-(args['overlap']*x)).
2. Replace the 'mseed_predictor.py" with the edited mseed_predictor_colab_3.py file in the EQTransformer/core/ folder of the model and rename the "mseed_predictor_colab_3.py" file to "mseed_predictor.py"
