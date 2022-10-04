## 1 Introduction

### 1.1 Overview

The motion detection supports applications including global motion detection, sub-region motion detection, motion object detection and tamper detection.

 **Global motion detection**

By using a fixed camera, global motion detection issues alarm if the area of moving objects is larger than the user-defined threshold.

![D:\\work6\\636\\fhtml\\NT9833X_MD_User_Guide_en.files\\image002.gif](nvt_media/402573d7ddb5ab9cf67ff173bdc2a307.gif)

Figure 1 Global motion detection

 **Sub-region motion detection**

By using a fixed camera, this function issues a sub-region motion alarm if the area of moving objects in the user-defined regions is larger than the user-defined threshold.

![D:\\work6\\636\\fhtml\\NT9833X_MD_User_Guide_en.files\\image003.gif](nvt_media/ef4723d2898d0367530a02f60494145f.gif)

Figure 2 Sub-region motion alarm

 **Motion objects detection**

By using a fixed camera, it detects moving objects if their areas are larger than a user-defined threshold. It also reports the sizes and coordinates of detected moving objects.

![D:\\work6\\636\\fhtml\\NT9833X_MD_User_Guide_en.files\\image004.gif](nvt_media/c0de02ad3d8dfd3dee63b084184e71d1.gif)

Figure 3 Motion objects detection

 **Tamper detection**

By using a fixed camera, it issues a tamper alarm if the occlusion area is larger than a user-defined area threshold.

![D:\\work6\\636\\fhtml\\NT9833X_MD_User_Guide_en.files\\image005.jpg](nvt_media/47668080c467f11b81bcb464d9856212.jpg)

Figure 4: Tamper Detection

### 1.2 Motion detection steps

The steps of motion detection functions are

Step. 1: Generating a initial background model by using the first few frames.

Step. 2: Micro block (MB) map is used in motion detection. The size of each MB can be 32x32 or 16x16. The algorithm determines a MB as a motion block if the variance of blocks is higher than a predefined threshold.

Step. 3: Updating the background model by using current frame information.

![D:\\work6\\636\\fhtml\\NT9833X_MD_User_Guide_en.files\\image006.gif](nvt_media/b6a03746a9f2e830424ef691db40c762.gif)

Figure 5. The flowchart of MD algoritm

### 1.3 Process Flow

![D:\\work6\\636\\fhtml\\NT9833X_MD_User_Guide_en.files\\image007.gif](nvt_media/c5a40d37e3ed5a4a5b8652d4912f00d2.gif)

Figure 6. The process flow of MD

### 1.4 Parameters

MD has two major parameter types, as listed below

 The parameters of vendor MD are used to control MD hardware.

 The parameters of libmd are used to control MD software application.

 Please notice that the parameters of vendor MD should be set before setting the parameters of libmd.

**  
**

#### 1.4.1 Parameters of vendor MD

 VENDOR_MD_CTRL: trigger setting of MD hardware

| Parameter      | Range | Comment            | Value            |
|----------------|-------|--------------------|------------------|
| engine_enabled |  0, 1 | HW trigger setting | 0: close 1: open |

 VENDOR_MD_MDT_INFO: size information of MD hardware

| Parameter     | Range    | Comment                                       | Value                                                                                                         |
|---------------|----------|-----------------------------------------------|---------------------------------------------------------------------------------------------------------------|
| phy_width     | 32\~3840 | Sensor resolution (width)                     | --                                                                                                            |
| phy_height    | 16\~2160 | Sensor resolution (height)                    | --                                                                                                            |
| phy_mb_x_size | 16, 32   | The x-size of micro-block (MB) for HW         | Set 32 when the phy_height is bigger than 1088.  Set 16 when the phy_height is smaller than or equal to 1088. |
| phy_mb_y_size | 16, 32   | The y-size of MB for HW                       | Same value of phy_mb_x_size.                                                                                  |
| phy_mb_x_num  |          | The number of MB in the MB-map at x-direction | phy_width/ phy_mb_x_size                                                                                      |
| phy_mb_y_num  |          | The number of MB in the MB-map at y-direction | phy_height/ phy_mb_y_size                                                                                     |

 VENDOR_MD_MDT_PARAM_IDX: index of MD background model parameters

| id                                       | Comment                                                         |
|------------------------------------------|-----------------------------------------------------------------|
| VENDOR_MD_MDT_PARAM_RST                  | Background model reset                                          |
| VENDOR_MD_MDT_PARAM_TYPE                 | The method to construct background model                        |
| VENDOR_MD_MDT_PARAM_TIME_PERIOD          | update time of background model  (only for MD2)                 |
| VENDOR_MD_MDT_PARAM_TBG                  | Weight threshold of background model                            |
| VENDOR_MD_MDT_PARAM_LVL_ALPHA            | Learning rate for the fitting background model                  |
| VENDOR_MD_MDT_PARAM_LVL_ONE_MIN_ALPHA    | Learning rate for the nun-fitting background model              |
| VENDOR_MD_MDT_PARAM_LVL_INIT_WEIGHT      | Initial weight of background model                              |
| VENDOR_MD_MDT_PARAM_LVL_MODEL_UPDATE     | Update constraint of background model                           |
| VENDOR_MD_MDT_PARAM_LVL_TB               | Threshold of foreground detection                               |
| VENDOR_MD_MDT_PARAM_LVL_SIGMA            | Variance threshold of background model                          |
| VENDOR_MD_MDT_PARAM_LVL_TG               | Threshold of background model update                            |
| VENDOR_MD_MDT_PARAM_LVL_PRUNE            | Threshold to decrease weight for nun-fitting background model   |
| VENDOR_MD_MDT_PARAM_LVL_LUMA_DIFF_THRES  | Luminance variance threshold at refine stage (only for MD1)     |
| VENDOR_MD_MDT_PARAM_LVL_TEXT_DIFF_THRES  | Texture variance threshold at refine stage  (only for MD1)      |
| VENDOR_MD_MDT_PARAM_LVL_TEXT_THRES       | Texture strength threshold at refine stage  (only for MD1)      |
| VENDOR_MD_MDT_PARAM_LVL_TEXT_RATIO_THRES | Texture coverage ratio threshold at refine stage (only for MD1) |
| VENDOR_MD_MDT_PARAM_LVL_GM_MD2_THRES     | Background threshold  (only for MD2)                            |

 VENDOR_MD_MDT_PARAM: parameters of MD background model

| Parameter | Comment                    |
|-----------|----------------------------|
| out_id    | Path id                    |
| level     | Choose the selective model |
| id        | VENDOR_MD_MDT_PARAM_IDX    |
| value     | Parameter value            |

 Value range of the VENDOR_MD_MDT_PARAM

| VENDOR_MD_MDT_PARAM_IDX                  | Range     | Comment                                                                                                                                                                                         | Value                                                      |
|------------------------------------------|-----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------|
| VENDOR_MD_MDT_PARAM_RST                  | 0, 1      | Reset MD background model                                                                                                                                                                       | 0: no reset 1: reset                                       |
| VENDOR_MD_MDT_PARAM_TYPE                 |  0, 1     | MD method type                                                                                                                                                                                  | 0: MD1 (HW) (learning-based) 1: MD2 (HW) difference-based) |
| VENDOR_MD_MDT_PARAM_TIME_PERIOD          | -         | Background update frame threshold (only for MD2)                                                                                                                                                | 10                                                         |
| VENDOR_MD_MDT_PARAM_TBG                  | 1\~32767  | Background model weight threshold **Suggest not to modify the value.**                                                                                                                          | 29490                                                      |
| VENDOR_MD_MDT_PARAM_LVL_ALPHA            |  1\~32767 | Background learning rate threshold when input fits model. Please set higher value when AE change obviously to avoid false alarm.                                                                | 32                                                         |
| VENDOR_MD_MDT_PARAM_LVL_ONE_MIN_ALPHA    |  1\~32767 | Background learning rate threshold when input doesn’t fit model.                                                                                                                                | 32736                                                      |
| VENDOR_MD_MDT_PARAM_LVL_INIT_WEIGHT      |  1\~32767 | Background model initial weight                                                                                                                                                                 | 32                                                         |
| VENDOR_MD_MDT_PARAM_LVL_MODEL_UPDATE     |  0, 1     | Background model constraint update  **Suggest not to modify the value.**                                                                                                                        | 0                                                          |
| VENDOR_MD_MDT_PARAM_LVL_TB               |  1\~31    | Background model fitting threshold. The MD is more sensitive when the value is lower.                                                                                                           | 25                                                         |
| VENDOR_MD_MDT_PARAM_LVL_SIGMA            |  1\~31    | Background model variance threshold. Set larger value to avoid false alarm when background luminance changes large. Please set the value lower when the MD result of detected object is broken. | 25                                                         |
| VENDOR_MD_MDT_PARAM_LVL_TG               |  1\~31    | Background model count threshold.  **Suggest not to modify the value.**                                                                                                                         | 9                                                          |
| VENDOR_MD_MDT_PARAM_LVL_PRUNE            |  1\~32767 | Weight decrease threshold for un-fitting model                                                                                                                                                  | 51                                                         |
| VENDOR_MD_MDT_PARAM_LVL_LUMA_DIFF_THRES  |  0\~255   | Luminance variance threshold at refine stage (only for MD1)                                                                                                                                     | 0                                                          |
| VENDOR_MD_MDT_PARAM_LVL_TEXT_DIFF_THRES  |  0\~255   | Texture variance threshold at refine stage (only for MD1)                                                                                                                                       | 0                                                          |
| VENDOR_MD_MDT_PARAM_LVL_TEXT_THRES       |  0\~255   | Texture strength threshold at refine stage (only for MD1)                                                                                                                                       | 0                                                          |
| VENDOR_MD_MDT_PARAM_LVL_TEXT_RATIO_THRES |  0\~127   | Texture coverage ratio threshold at refine stage (only for MD1)                                                                                                                                 | 127                                                        |
| VENDOR_MD_MDT_PARAM_LVL_GM_MD2_THRES     |  0\~255   | Background threshold (only for MD2)                                                                                                                                                             | 10                                                         |

 VENDOR_MD_MDT_MB_LEVEL: region setting of the background model

| Parameter | Range          | Comment                                                                         |
|-----------|----------------|---------------------------------------------------------------------------------|
| x         |  0\~max_width  | x position of the left upper corner of the region (physical plane, Unit: pixel) |
| y         |  0\~max_height | y position of the left upper corner of the region (physical plane, Unit: pixel) |
| width     |  1\~max_width  | width of the left upper corner of the region (physical plane, Unit: pixel)      |
| height    |  1\~max_height | height of the left upper corner of the region (physical plane, Unit: pixel)     |
| level     |  0\~3          | The selective background model of the region                                    |

 VENDOR_MD_TDT_PARAM_IDX: index of the tamper detection parameters

| id                                 | Comment                                      |
|------------------------------------|----------------------------------------------|
| VENDOR_MD_TDT_PARAM_TYPE           | Tamper detection method type                 |
| VENDOR_MD_TDT_PARAM_EDGE_TEX_THRES | Texture strength threshold                   |
| VENDOR_MD_TDT_PARAM_EDGE_WIN_THRES | Coverage of low texture strength threshold   |
| VENDOR_MD_TDT_PARAM_AVG_TEX_THRES  | Luminance strength threshold                 |
| VENDOR_MD_TDT_PARAM_AVG_WIN_THRES  | Coverage of low luminance strength threshold |

 VENDOR_MD_MDT_PARAM: tamper detection parameters

| Parameter | Comment                 |
|-----------|-------------------------|
| out_id    | Path id                 |
| id        | VENDOR_MD_TDT_PARAM_IDX |
| value     | Parameter value         |

 Value range of the tamper detection parameters

| VENDOR_MD_TDT_PARAM_IDX            | Range  | Comment                                      | Default                          |
|------------------------------------|--------|----------------------------------------------|----------------------------------|
| VENDOR_MD_TDT_PARAM_TYPE           | 0, 1   | Tamper detection method                      | 0: edge-based 1: intensity based |
| VENDOR_MD_TDT_PARAM_EDGE_TEX_THRES | 0\~255 | Texture strength threshold                   | 25                               |
| VENDOR_MD_TDT_PARAM_EDGE_WIN_THRES | 0\~127 | Coverage of low texture strength threshold   | 100                              |
| VENDOR_MD_TDT_PARAM_AVG_TEX_THRES  | 0\~255 | Luminance strength threshold                 | 65                               |
| VENDOR_MD_TDT_PARAM_AVG_WIN_THRES  | 0\~127 | Coverage of low luminance strength threshold | 100                              |

 VENDOR_BUFFER : buffer information structure

| Parameter | Comment          |
|-----------|------------------|
| paddr     | Physical address |
| size      | Buffer size      |
| ddr_id    | DDR_IDX          |

 VENDOR_MD_BUFFER: buffer information of MD hardware

| Parameter    | Comment                                          |
|--------------|--------------------------------------------------|
| mb_x_num_max | Maximum width of the MB number(Unit: MB number)  |
| mb_y_num_max | Maximum height of the MB number(Unit: MB number) |
| sta          | MD HW statistics value buffer                    |
| event        | MD HWmotion bitmap buffer                        |
| level        | MD HW selective background model buffer          |

 VENDOR_MD_PARAM_ID: index of vendor_md function

| id                               | Comment                                                                                                                                                                                                                                                            |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| VENDOR_MD_CTRL_PARAM             | MD HW control structure                                                                                                                                                                                                                                            |
| VENDOR_MD_MOTION_DETECT_INFO     | MD HW process size unit structure                                                                                                                                                                                                                                  |
| VENDOR_MD_MOTION_DETECT_PARAM    | MD HW background model parameter structure                                                                                                                                                                                                                         |
| VENDOR_MD_MOTION_DETECT_MB_LEVEL | MD HW background model selective model structure                                                                                                                                                                                                                   |
| VENDOR_MD_MOTION_DETECT_BUFFER   | MD HW buffer structure                                                                                                                                                                                                                                             |
| VENDOR_MD_TAMPER_DETECT_PARAM    | MD HW tamper parameter structure                                                                                                                                                                                                                                   |
| VENDOR_MD_RESULT_INFO            | MD HW result structure                                                                                                                                                                                                                                             |
| VENDOR_MD_REASSIGN_BUFFERS       | MD reassign buffer API. When max MB num is larger than (1920/16, 1080/16) or want to shrink MD buffer size. Note: hdal default pool buffer size for MD is (120,67) and 8 channel. If you use reassign buffer, you should change the hdal default pool buffer size. |

#### 1.4.2 Parameters of libmd

 LIB_MD_AP_ENABLE: trigger setting of MD application:

| Parameter                    | Range | Comment                         |
|------------------------------|-------|---------------------------------|
| globel_md_alarm_detect_en    | 0, 1  | Global motion alarm enable      |
| subregion_md_alarm_detect_en | 0, 1  | Sub-region motion alarm enable  |
| md_obj_detect_en             | 0, 1  | Objects detection enable        |
| md_postprocess_en            | 0, 1  | Motionbitmap postprocess enable |

 LIB_MD_EVT_INFO: results of motion detection

| Parameter | Comment                       |
|-----------|-------------------------------|
| p_evt_map | MD HW event bimap buffer      |
| evt_sz    | MD HW event bimap buffer size |
| timestamp | MD event timestamp            |

 LIB_MD_MDT_INFO: size setting information of libmd

| Parameter     | Range   | Comment                               | Default                                           |
|---------------|---------|---------------------------------------|---------------------------------------------------|
| md_enabled    | 0, 1    | Libmd enable                          | vendor_md engine_enabled should be enable firstly |
| vp_width      | 1\~3840 | User plane width                      | suggest to set as sensor setting                  |
| vp_height     | 1\~2160 | User plane height                     | suggest to set as sensor setting                  |
| vp_mb_x_size  | 16, 32  | Width of MB size in the user plane    | suggest to set the same value of phy_mb_x_size    |
| vp_mb_y_size  | 16, 32  | Height of MB size in the user plane   | suggest to set the same value of phy_mb_y_size    |
| vp_mb_x_num   |  -      | Width of MB number in the user plane  | vp_width / vp_mb_x_size                           |
| vp_mb_y_num   |  -      | Height of MB number in the user plane | vp_height / vp_mb_y_size                          |
| phy_mb_x_size | 16, 32  | HW width of MB size                   | set the same as vendor_md                         |
| phy_mb_y_size | 16, 32  | HW height of MB size                  | set the same as vendor_md                         |
| phy_mb_x_num  |         | Sensor_width/ phy_mb_x_size           | set the same as vendor_md                         |
| phy_mb_y_num  |         | Sensor_height/ phy_mb_y_size          | set the same as vendor_md                         |

 LIB_MD_AP_POSTPROCESS: post-process type of libmd event

| Parameter            | Range | Comment                  | Default                                                                                                                                                                      |
|----------------------|-------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| evt_postprocess_type | 0\~7  | Motion event postprocess | 0: no 1: one erosion + two dilation 2: two dilation + one erosion 3: two dilation 4: one dilation 5: one erosion 6: one dilation + one erosion 7: one erosion + one dilation |

 LIB_MD_AP_GLOBAL_MOTION_ALARM: parameters of global motion alarm detection

| Parameter       | Range                     | Comment                                                                                                                                                                              |
|-----------------|---------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| motion_alarm_th | 0\~100                    | Global motion detection alarm area coverage ratio threshold (%). MD is more sensitive when the value is lower.                                                                       |
| ref_cell_en     | 0, 1                      | The detection result will reference p_cell_map or not. When the value is 1, the global motion alarm/ sub-region motion alarm/ object detection result will reference the p_cell_map. |
| p_cell_map      | 0, 1                      | The detection result will reference the buffer when the ref_cell_en=1.                                                                                                               |
| cell_map_sz     | vp_mb_x_num\* vp_mb_y_num | The buffer size of the p_cell_map                                                                                                                                                    |

 LIB_MD_AP_SUBREGION: parameters of specified sub-region structure

| Parameter | Range         | Comment                                                                                                            |
|-----------|---------------|--------------------------------------------------------------------------------------------------------------------|
| enabled   | 0, 1          | Sub-region motion detection alarm enable                                                                           |
| x_start   | 0\~mb_w_num-1 | x position of the left upper corner of the region (virtual plane，Unit: macro block)                               |
| y_start   | 0\~mb_h_num-1 | y position of the left upper corner of the region (virtual plane，Unit: macro block)                               |
| x_end     | 0\~mb_w_num-1 | x position of the right under corner of the region (virtual plane，Unit: macro block)                              |
| y_end     | 0\~mb_h_num-1 | y position of the right under corner of the region (virtual plane，Unit: macro block)                              |
| alarm_th  | 0\~100        | Sub-region motion detection alarm area coverage ratio threshold (%). MD is more sensitive when the value is lower. |

 LIB_MD_AP_SUBREGION_MOTION_ALARM: parameters of sub-region motion alarm detection

| Parameter      | Range | Comment                        |
|----------------|-------|--------------------------------|
| sub_region_num |  0\~4 | Specified sub-region number    |
| sub_region     |  -    | Specified sub-region structure |

 LIB_MD_AP_OBJ: size setting of minmum motion object

| Parameter   | Range | Comment                                                    |
|-------------|-------|------------------------------------------------------------|
| object_size |  -    | Minimum size of detected moing objects (Unit: macro block) |

 LIB_MD_AP_OBJ_INFO: information of motion objects

| Parameter | Range        | Comment                                                                                      |
|-----------|--------------|----------------------------------------------------------------------------------------------|
| start_x   | 0\~ vp_width | x position of the left upper corner of the motion object (virtual plane，Unit:pixel)         |
| start_y   | 0\~vp_height | y position of the left upper corner of the motion object (virtual plane，Unit:pixel)         |
| end_x     | 0\~ vp_width | x position of the right under corner of the motion object (virtual plane，Unit: macro block) |
| end_y     | 0\~vp_height | y position of the right under corner of the motion object (virtual plane，Unit: macro block) |
| label     | 0\~128       | Motion obect index                                                                           |

 LIB_MD_MDT_RESULT_INFO: results information of the libmd

| Parameter               | Range                         | Comment                                      | Value                |
|-------------------------|-------------------------------|----------------------------------------------|----------------------|
| global_motion_alarm     |  0, 1                         | Global motion detection alarm                | 0: no alarm 1: alarm |
| global_motion_alarm_num | 0\~ vp_mb_x_num\* vp_mb_y_num | Motion MB number                             |                      |
| sub_motion_alarm        |  0, 1                         | Sub-region motion detection alarm            | 0: no alarm 1: alarm |
| obj_num                 |  0\~128                       | Motion object number                         |                      |
| obj                     |  -                            | Motion object structure                      |                      |
| vp_evt_info             |  -                            | Motion detection event map in the user plane |                      |

 LIB_MD_PARAM_ID: index of libmd function

| Parameter                                | Comment                                                                                                                                                                             |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| LIB_MD_MOTION_DETECT_INFO                | Libmd set virtual/physical plane evt bitmap addr. Physical plane should be set the same as vendor_md. Physical evt bitmap address is vendor_md output result motion bitmap address. |
| evt bitmap addr為vendor_md output result | Libmd all detection application enable port                                                                                                                                         |
| LIB_MD_AP_ENABLE_PARAM                   | Libmd postprocess enable                                                                                                                                                            |
| LIB_MD_AP_POSTPROCESS_PARAM              | Libmd global motion detection enable                                                                                                                                                |
| LIB_MD_AP_GLOBAL_MOTION_ALARM_PARAM      | Libmd sub-region motion detection enable                                                                                                                                            |
| LIB_MD_AP_SUBREGION_MOTION_ALARM_PARAM   | Libmd motion object detection enable                                                                                                                                                |
| LIB_MD_AP_OBJ_PARAM                      | Libmd result information                                                                                                                                                            |

**Note:** The MD model can lean the stable change of scene, such as river or twinkle light. If the user want to detect this kind of events, the parameters can be set as following:

 Model parameters

 tg=3

 tb=19

 alpha = 1024

 Refine process

 lum_diff_th=75

 tex_diff_th=50

 tex_ratio_th=50

**  
**

### 1.5 Initilization of MD

 Vendor MD

The buffer of vender MD and HW internal parametesrs should be set by the API as following:

**HD_RESULT md_init(void);**

 Libmd

The buffer of libmd and software parametesrs should be set by the API as following:

**HD_RESULT motion_set_ap_param(UINT32 path_id);**

**HD_RESULT lib_md_init(HD_PATH_ID path_id);** // libmd buffer setting shoule be set after HW MD size setting which set through motion_set_ap_param.

### 1.6 Parameters Setting of MD

 Vendor MD

Vendor MD parameters should be set by the following API.

**ret = vendor_md_set(video_cap[ch], VENDOR_MD_CTRL_PARAM, \&md_cfg);**

The content of **VENDOR_MD_PARAM_ID** is list in the section1.4.1.

 Libmd

The parameters of libmd should be set by the following API.

**ret = lib_md_set(path_id, LIB_MD_AP_ENABLE_PARAM, \&mdt_lib_param[idx].mdt_enable);**

The content of **LIB_MD_PARAM_ID** is list in the section1.4.2.

### 1.7 Execution of MD

#### 1.7.1 vendor MD

Vendor MD application should be set by the following API.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// buffer and parameters intial setting
HD_RESULT md_init(void); 
// create md_thread
static void *md_thread(void *arg);
//set and get vendor md API
ret = vendor_md_get(path_id, VENDOR_MD_MOTION_DETECT_INFO, &mdt_info);
ret = vendor_md_set(path_id, VENDOR_MD_RESULT_INFO, &result_info);
ret = vendor_md_get(path_id, VENDOR_MD_RESULT_INFO, &result_info); 
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

#### 1.7.2 libmd

libmd application should be set by the following API.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
// buffer and parameters intial setting
HD_RESULT motion_set_ap_param(UINT32 path_id);
HD_RESULT lib_md_init(HD_PATH_ID path_id); 
// create md_thread
static void *md_thread(void *arg);
//set and get libmd API
ret = vendor_md_get(path_id, VENDOR_MD_RESULT_INFO, &result_info); //libmd process should use vendor_md result as input
vendor_md_get(path_id, VENDOR_MD_RESULT_INFO, &result_info)
ret = lib_md_set(path_id, LIB_MD_MOTION_DETECT_INFO, &lib_md_info);
ret = lib_md_get(path_id, LIB_MD_RESULT_INFO, &lib_md_rst);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### 1.8 Requirement of MD

 MD funtions only be applied by CPU and HW.

### 1.9 Limitation of MD

 MD shoud be used in the fixed-camera. If camera has been moved, MD function might output a false alarm event.

 MD function might output a false alarm event because of the zoom in/out of camera or the adjustment of auto white balance.

 The size of moving object should be larger than 1 micro-block (MB)

### 1.10 Test Flow of MD

 Check MD use in the fixed-camera scene

 Check MD event bitmap to check MD flow

 MD should be used after 3 frames to create initial background.

## 2 Output

### 2.1 Get Output Results of MD

 vendor MD

Vendor MD result should be set/got by the following API.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
ret = vendor_md_set(path_id, VENDOR_MD_RESULT_INFO, &result_info);
ret = vendor_md_get(path_id, VENDOR_MD_RESULT_INFO, &result_info);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The structure of MD hardware result lists as following.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
typedef struct _VENDOR_MD_MDT_RESULT_INFO {
     UINT8       *p_evt_map;                           ///< motion detection bitmap, size is evt_sz
     UINT32      evt_sz;                         ///< phy_mb_x_num*phy_mb_y_num MB
     UINT8       tp_result;                             ///< tamper alarm 
     UINT32      timestamp;
} VENDOR_MD_MDT_RESULT_INFO;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

 libmd

libmd result should be set/got by the following API.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
vendor_md_get(path_id, VENDOR_MD_RESULT_INFO, &result_info)
ret = lib_md_set(path_id, LIB_MD_MOTION_DETECT_INFO, &lib_md_info);
ret = lib_md_get(path_id, LIB_MD_RESULT_INFO, &lib_md_rst);
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

libmd result structure lists as following.

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
typedef struct _LIB_MD_MDT_RESULT_INFO {
     UINT8         global_motion_alarm;                         ///< global motion alarm   
     UINT32        global_motion_alarm_num;                     ///< global motion alarm num
     UINT32        sub_motion_alarm[LIB_MD_MAX_SUB_REGION_NUM]; ///< sub-region motion alarm
     UINT32        obj_num;                                    ///< detect object number (max=128)
     LIB_MD_AP_OBJ_INFO  obj[LIB_MD_MAX_OBJ_NUM];               ///< detect object info
     LIB_MD_EVT_INFO vp_evt_info;
} LIB_MD_MDT_RESULT_INFO;
 
typedef struct _LIB_MD_EVT_INFO {
     UINT8        *p_evt_map;                    ///< motion detection bitmap, size is evt_sz
     UINT32       evt_sz;                        ///< mb_x_num*mb_y_num MB
     UINT32       timestamp;
} LIB_MD_EVT_INFO;
 
typedef struct _LIB_MD_AP_OBJ_INFO {
     UINT32        start_x;                  ///< obj rectangle left upper x position (virtual pixel)  
     UINT32        start_y;                  ///< obj rectangle left upper y position (virtual pixel)  
     UINT32        end_x;                    ///< obj rectangle right down x position (virtual pixel)  
     UINT32        end_y;                    ///< obj rectangle right down y position (virtual pixel)  
     UINT32        label;                    ///< obj label
} LIB_MD_AP_OBJ_INFO;
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

### 2.2 Print Output Results of MD

 Output Result of Global Motion Detection

UART will print the results as following when motion area in the whole scene is larger than user-defined threshold.

**\> global motion alarm on ch(specified channel).**

 Output Result of Sub-region Motion Detection

UART will print the results as following when the motion area in one or more sub-regions is larger than user-defined threshold.

**\> sub_region[specified region index] motion alarm on ch(specified channel).**

 Output Result of Motion Object Detection

UART will print the results as following when motion objects area are larger than minimum object user-defined threshold.

**\> obj num:Motion object number and obj[object index]: start_xy=[left upper corner position of motion object], end_xy = [right under corner position of motion object], label = object label.**

 Output Result of Tamper Detection

UART will print the results as following when occlusion area is larger than user-defined threshold.

**\> tamper_result:1 on ch(specified channel).**

### 2.3 Limitation MD Hardware

 Maximum sensor resolution is 3840x2160.

 Maximum MB number of MD hardware are (mb_x_num, mb_y_num) = (256, 128) and minimum MB number of MD hardware are (mb_x_num, mb_y_num) = (2, 1).

 In the Vcap flow, MD doesn’t support the scale function.

### 2.4 Requirement of MD System

 The efficiency of MD function is associated with system loading. The ouput result of MD may be delayed when system is overloading.

### 2.5 Tuning of MD Parameters

 In the scene with the shortly changing of light, such as AE adjustment or turn-on and turn-off the light, please set the value of *alpha* higher. The side effect is that moving slowly object might be detected as background.

 Please set **tb** to be higher for shadow. The side effect is that the detected forground of moving obeject might be broken. In this case, please also set “sigma” to be lower to fix the broken forground issue.

 The distance between moving object and camera should be farer than 30 cm. If the moving objects is too close to the camera, there might cause the false alarm of shadow.

 Please set lower **tb** when foreground luminance is similar background. However, the side effect is that the false alarm of shadow may be increase.

 Please see section 1.5 when you need to detect stable motion case.

 The MD function doesn’t support night view with IR-cut. In this case, there might be similar between background and foreground.

 There is no motion event when MD is creating intial background model. Also, MD will need longer time to create initial backgroung model if there are some moving objects in the initial scene.

 The size of moving object should be larger than 1 MB.

## 3 Q&A

(1) How to check vendor MD version?

Ans:

echo md \> /proc/hdal/flow

Execute AP

cat /proc/hdal/flow

(2) How to set the md sensitive?

Ans:

I. Use vendor_md_set API (the details describe in the 1.6 section and the section 1.4.1.

II. Tuning Guide document provide the tuning parameter suggestion. If any more question, please provide the video and parameters.

(3) How to solve sensor resolution change error?

Ans:

If you want to chage sensor reolution, please vendor_md_unint & vendor_md_int at fisrt and you might see liveview_with_md_ctrl.c or liveview_with_md_resolution.c

(4) How to check sensor interlace case?

Ans:

MD is field input. If input is interlace, please set the half of the sensor input height. You can see interlace case through command as following cat /proc/vcap316/vcap0/vg_info.

(5) Check AD mode (960H and 720) case

Ans:

I. Check AD output is full frame.

II. MD input size is the same as the AD output size. phy_width andphy_height should be calculate by AD output (might not be the size of sensor). The size setting check by /proc/vcap316/vcap0/vg_info and vcap md (detal describe in question 6 ).

(6) If any setting question of the vendor_md flow, please provide the log of vendor_md flow by the following command.

Ans:

echo md \> /proc/hdal/flow

Execute AP

cat /proc/hdal/flow

(7) How to check vcap md setting

Ans:

echo vcap_ch \> /proc/vcap316/vcap0/vcap0.CHIP/md/event

(vcap_ch and CHIP according to vg_info)

cat /proc/vcap316/vcap0/vcap0. CHIP /md/region

cat /proc/vcap316/vcap0/vcap0. CHIP /md/param

(8) How to solve the mb num \>(120,67)?

Ans:

I. modify hdal excel buffer size setting

II. open reassign_buffer

(9) How to use the level setting ?

Ans:

Each MB can be setted different level. Each level is mapping the set of background model. In nomal scene, all scene use the same level. In the scene which include both indoor and outdoor, you can set two level of the scene.

(10) Where is the tamper sample code?

Ans:

tamper sample code is liveview_with_md.c.

## 4 Revision History

| Revision | Date       | Author | Changes                                                       |
|----------|------------|--------|---------------------------------------------------------------|
| 0.1      | 2021/06/30 | Sophia | First formal version                                          |
| 0.2      | 2021/07/02 | Sophia | Update document format and description                        |
| 0.3      | 2022/06/24 | Hunter | Modify the description of mb size and some wrong information. |
