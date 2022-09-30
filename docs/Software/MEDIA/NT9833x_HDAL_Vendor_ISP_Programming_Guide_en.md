## Introduction

## Vendor_ad Function Parameter IDs and data structure definition

### Function Definition

#### vendor_ad_init

[Description]

Initialize the unit

[Syntax]

HD_RESULT vendor_ad_init(CHAR \*ad_dev_name)

[Parameter]

| Value       | Description             |
|-------------|-------------------------|
| ad_dev_name | the ad device file name |

[Return Value]

| Value      | Description                 |
|------------|-----------------------------|
| HD_OK      | Success                     |
| HD_ERR_SYS | Open ad device file failure |

#### vendor_ad_uninit

[Description]

Uninitialize the unit

[Syntax]

HD_RESULT vendor_ad_uninit(VOID)

[Parameter]

| Value | Description   |
|-------|---------------|
| VOID  | Not available |

[Return Value]

| Value     | Description |
|-----------|-------------|
| HD_OK     | Success     |
| HD_ERR_NG | Failure     |

#### vendor_ad_get

[Description]

Get parameters from ad unit

[Syntax]

HD_RESULT vendor_ad_get(VENDOR_AD_PARAM_ID id, void \*p_param);

[Parameter]

| Value   | Description           |
|---------|-----------------------|
| id      | id of parameters      |
| p_param | pointer of parameters |

[Return Value]

| Value              | Description                |
|--------------------|----------------------------|
| HD_OK              | Success                    |
| HD_ERR_NG          | Failure                    |
| HD_ERR_NOT_SUPPORT | Not support this parameter |

#### vendor_ad_set

[Description]

Not support

### Parameters IDs and data structure definition

The function vendor_ad_get provides the following parameter IDs:

-   VENDOR_AD_PARAM_TP28XX_DEVICE_INFO
    -   support get with tp28xx device info
    -   using VENDOR_AD_TP28XX_DEVICE_INFO struct
-   VENDOR_AD_PARAM_TP28XX_DEVICE_NORM
    -   support get with tp28xx device norm
    -   using VENDOR_AD_TP28XX_DEVICE_NORM struct
-   VENDOR_AD_PARAM_TP28XX_DEVICE_LOSS
    -   support get with tp28xx device loss
    -   using VENDOR_AD_TP28XX_DEVICE_LOSS struct
-   VENDOR_AD_PARAM_NVP61XX_DEVICE_INFO
    -   support get with nvp61xx device info
    -   using VENDOR_AD_NVP61XX_DEVICE_INFO struct
-   VENDOR_AD_PARAM\_ NVP61XX_DEVICE_NORM
    -   support get with nvp61xx device norm
    -   using VENDOR_AD\_ NVP61XX_DEVICE_NORM struct
-   VENDOR_AD_PARAM_NVP61XX_DEVICE_LOSS
    -   support get with nvp61xx device loss
    -   using VENDOR_AD_NVP61XX_DEVICE_LOSS struct

#### VENDOR_AD_TP28XX_DEVICE_INFO

[Description]

Get tp28xx device information

[Parameter]

| Value          | Description                                                     |
|----------------|-----------------------------------------------------------------|
| dev_num        | number of tp28xx device                                         |
| vout_mode      | chip video output port mode                                     |
| vout.xcap      | Backend X_CAP\## =\> 0:None, 1\~16:X_CAP\#0\~15                  |
| vout.vi        | Backend VI\## =\> 0:None, 1\~16: VI\#0\~15                       |
| vout.clk_dly   | Backend Video Port Clock Delay, 0 \~ 0xff                       |
| vout.clk_pdly  | Backend Video Port Clock Polarity Delay, 0 \~ 0xff              |
| vout.clk_inv   | Backend Video Port Clock Inversion, 0:none 1:invertion          |
| vout.clk_pin   | Backend Video Port Clock Pin Selection, 0:pinmux\#0 1:pinmux\#1 |
| vout.data_swap | Backend Video Port Data Swap, 0:none 1:bit swap                 |
| vin.active     | Device vin active, 0:no 1:yes                                   |
| vin.vch_id     | Device vin video channel index                                  |
| vin.vout       | Device vin video output port index                              |
| vin.chip       | Backend chip index                                              |
| vin.vcap       | Backend vcap index of this chip                                 |
| vin.vi         | Backend vi index of this vcap                                   |
| vin.ch         | Backend ch index of this vi, vin grab via this vi channel       |

#### VENDOR_AD_TP28XX_VIDEO_NORM

[Description]

Get tp28xx video norm

[Parameter]

| Value          | Description                                                     |
|----------------|-----------------------------------------------------------------|
| dev_id         | device index                                                    |
| vin_id         | device vin index                                                |
| src_width      | channel source width, video source width                        |
| src_height     | channel source height, video source height                      |
| src_fps        | channel source frame rate, must \> 0                            |
| src_prog       | channel source progressive/interlace, 0:interlace 1:progressive |
| out_width      | channel output width                                            |
| out_height     | channel output height                                           |
| out_fmt        | channel output format                                           |
| out_data_rate  | channel output data rate, for specify byte duplicate mode       |
| out_data_latch | channel output data latch mode                                  |
| out_horiz_dup  | channel output horizontal pixel duplicate mode                  |

#### VENDOR_AD_TP28XX_VIDEO_LOSS

[Description]

Get tp28xx video loss

[Parameter]

| Value   | Description            |
|---------|------------------------|
| chip    | device chip index      |
| ch      | channel index          |
| is_lost | 1: is_lost, 0:present  |

#### VENDOR_AD_NVP61XX_DEVICE_INFO

[Description]

Get nvp61xx device information

[Parameter]

| Value          | Description                                                     |
|----------------|-----------------------------------------------------------------|
| dev_num        | number of nvp61xx device                                        |
| vout_mode      | chip video output port mode                                     |
| vout.xcap      | Backend X_CAP\## =\> 0:None, 1\~16:X_CAP\#0\~15                  |
| vout.vi        | Backend VI\## =\> 0:None, 1\~16: VI\#0\~15                       |
| vout.clk_dly   | Backend Video Port Clock Delay, 0 \~ 0xff                       |
| vout.clk_pdly  | Backend Video Port Clock Polarity Delay, 0 \~ 0xff              |
| vout.clk_inv   | Backend Video Port Clock Inversion, 0:none 1:invertion          |
| vout.clk_pin   | Backend Video Port Clock Pin Selection, 0:pinmux\#0 1:pinmux\#1 |
| vout.data_swap | Backend Video Port Data Swap, 0:none 1:bit swap                 |
| vin.active     | Device vin active, 0:no 1:yes                                   |
| vin.vch_id     | Device vin video channel index                                  |
| vin.vout       | Device vin video output port index                              |
| vin.chip       | Backend chip index                                              |
| vin.vcap       | Backend vcap index of this chip                                 |
| vin.vi         | Backend vi index of this vcap                                   |
| vin.ch         | Backend ch index of this vi, vin grab via this vi channel       |

#### VENDOR_AD_NVP61XX_VIDEO_NORM

[Description]

Get nvp61xx video norm

[Parameter]

| Value          | Description                                                     |
|----------------|-----------------------------------------------------------------|
| dev_id         | device index                                                    |
| vin_id         | device vin index                                                |
| src_width      | channel source width, video source width                        |
| src_height     | channel source height, video source height                      |
| src_fps        | channel source frame rate, must \> 0                            |
| src_prog       | channel source progressive/interlace, 0:interlace 1:progressive |
| out_width      | channel output width                                            |
| out_height     | channel output height                                           |
| out_fmt        | channel output format                                           |
| out_data_rate  | channel output data rate, for specify byte duplicate mode       |
| out_data_latch | channel output data latch mode                                  |
| out_horiz_dup  | channel output horizontal pixel duplicate mode                  |

#### VENDOR_AD_NVP61XX_VIDEO_LOSS

[Description]

Get nvp61xx video loss

[Parameter]

| Value   | Description            |
|---------|------------------------|
| chip    | device chip index      |
| ch      | channel index          |
| is_lost | 1: is_lost, 0:present  |

## Vendor_video Function Parameter IDs and Data structure definition

Please refer to document NT9833x_HDAL_Vendor_Media_Programming_Guide_en.doc.

## 
