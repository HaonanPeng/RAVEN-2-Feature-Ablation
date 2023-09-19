# Feature Ablation Study of a Learning-based Calibration for RAVEN II Surgical Robot

## Data
Training and testing data can be found at [https://drive.google.com/drive/folders/1W4U3GE-LiFojJjfVhkzVQUe9ma9OvMn6?usp=sharing](https://drive.google.com/drive/folders/1W4U3GE-LiFojJjfVhkzVQUe9ma9OvMn6?usp=sharing).

## Model training, evaluation, and ablation study 
Deep Neural Network: dnn_model_multi_attempt_scaled.ipynb
Gated Recurrent Unit: gru_model_multi_attempt_scaled.ipynb

The code can be easily run on Google Colab or Jupyter Notebook. You may need to change the data import section to fit your settings.
```
!unzip -q "/content/drive/MyDrive/RAVEN Calibration/experiments/recorded_trajs/test_no_homing_in_train.zip" -d '/content/r2_learning_calibration/data'
```

Removal ablation can be performed by removing target features in the "feature_list":
```
feature_list = [np.arange(12,13), # time stamp
                np.arange(13,29), # jpos
                np.arange(29,30), # run level
                np.arange(30,31), # sub level
                np.arange(31,32), # last_seq
                np.arange(32,34), # type
                np.arange(34,40), # pos
                np.arange(40,58), # ori
                np.arange(58,76), # ord_d
                np.arange(76,82), # pos_d
                #np.arange(82,98), # enc_val
                np.arange(98,114), # dac_val
                np.arange(114,130), # tau
                np.arange(130,133),np.arange(134,146), # mpos
                np.arange(146,162), #  mvel
                np.arange(162,178), # jvel
                np.arange(178,194), # mpos_d
                np.arange(194,210), # jpos_d
                np.arange(210,212), # grasp_d
                #np.arange(212,228), # enc_offset
                np.arange(228,240), # jac_vel
                np.arange(240,252)] # jac_f
```

Inaccurate ablation can be performed by adding target features in the "noise_list":
```
noise_type = 'stdv'
noise_list = [np.arange(13,29), # jpos
              np.arange(194,210) # jpos_d
              ]
```

Please contact Haonan Peng (penghn@uw.edu) if you have any questions.

## Robot control and data collection
The control of the RAVEN II robot and data collection was accomplished by [raven2_CRTK_Python_controller](https://github.com/uw-biorobotics/raven2_CRTK_Python_controller/tree/main).



