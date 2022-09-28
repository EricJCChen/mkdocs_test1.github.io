VPE IQ Tuning Guide

1 Overview
----------

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image002.jpg)

Figure 1?1 NT9833x Video Flow

VPE is an independent image processing engine in YUV domain, and it performs some pre-processing process before LCD display or encoder to improve the image quality. The related modules are as follows:

l Spatial Noise Reduction Module(SPNR, using MRNR method)

l Tempoarl Noise Reduction Module(TMNR)

l Sharpen Module(SHP)

l Scaling Module(SCA)

※ The 9833x series has removed DCE and DCTG.

※ In the following description, the area shown in blue is the same module as the 9831x series but the parameters are different. Please pay special attention)

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image003.jpg)

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image004.jpg)

Figure 1?2  VPE Image Processing Flow

2 System Control
----------------

The processing sequence of Sharpen, SPNR(using MRNR method) and TMNR is changeable, and user can change the processing sequence depends on different camera charateristic to achieve the best image quality.

### 2.1 Parameter Description

|     |     |     |     |
| --- | --- | --- | --- |
| **Parameter** | **Range** | **Def** | **Description** |
| ch_fd |     |     | Video graph use ch\_fd to represent the connected video engine of each channel. User can fine tune parameter of each video engine by setting ch\_fd. |
| pipe_mode | 0~5 | 0   | Set module processing sequence.<br><br>0 : MRNR -> TMNR -> Sharpen<br><br>1 : MRNR-> Sharpen -> TMNR<br><br>2 : Sharpen -> MRNR -> TMNR<br><br>3 : SHP->TMNR->MRNR  <br>4 :?TMNR->MRNR->SHP  <br>5 : TMNR->SHP->MRNR |

### 2.2 Setting Interface

#### 2.2.1 Proc

###### l /proc/videograph/vpe/ch_fd

**\[Description\]**

Read or write the current camera channel, and it only needs to set once, the following SHP, MRNR, TMNR parameters will work on this channel.

The following proc command will list all ch_fd of the current video engine:

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image005.png)

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[fd \] > /proc/videograph/vpe/ch_fd | **Fw Internal Pointer** |

Read : cat /proc/videograph/vpe/ch_fd

**![文字方塊: Command : echo \[fd\] > /proc/videograph/vpe/ch_fd
Current channel = <ch_fd>
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image006.png)**

###### l /proc/videograph/vpe/pipe_mode

\[Description\]

Read or write the executing sequence of SHP, MRNR and TMNR.

\[Command\]

Write :

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[pipe\_mode \] > /proc/videograph/vpe/pipe\_mode | **src\_ppo\_idx????????**<br><br>**mrnr\_ppi\_idx????**<br><br>**mrnr\_ppo\_idx???**<br><br>**tmnr\_ppi\_idx?????**<br><br>**tmnr\_ppo\_idx????**<br><br>**shp\_ppi\_idx????????**<br><br>**shp\_ppo\_idx???????**<br><br>**sca\_ppi\_idx** |

Read : cat /proc/videograph/vpe/pipe_mode

![文字方塊: Command : echo \[pipe_mode\] > /proc/videograph/vpe/pipe_mode
Current pipe_mode = \[pipe_mode\]
mode :
0 : MRNR-> TMNR-> SHP
1 : MRNR-> SHP->TMNR
2 : SHP-> MRNR -> TMNR
3 : SHP->TMNR->MRNR
4 : TMNR->MRNR->SHP
5 : TMNR->SHP->MRNR
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image007.png)

3 Spatial Noise Reduction
-------------------------

This is spatial noise reduction module(abbreviation is “SPNR”). It will divide the image into high frequency part and middle frequency part, performing noise reduction process respectively, then combine together to achieve the purpose of noise reduction and retain detail.?

### 3.1 Overview

Major processing flow is as follows :

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image008.png)

Figure 3?1 The SPNR processing flow.

Major processing flow :

1. Divide the input image into high frequency image and middle frequency image.

2. Determine and label whether the processing pixel is on the edge.

3. Perform edge smooth process on high frequency image and middle frequency image, respectively.

4. Perform flat region noise reduction process on middle frequency image.

5. Use high/middle frequency image which had performed noise reduction process to reconstruct image.

### 3.2 Parameter Description

(The blue text is the part of the parameter difference between this module and the 9831x series, please pay special attention)

Table 3?1 SPNR Parameter List

|     |     |     |     |
| --- | --- | --- | --- |
| **Parameter** | **Range** | **Def** | **Description** |
| t\_y\_edge_detection \[2\]\[8\] | 0~1023 | 161,322,483,447,<br><br>419,320,195,130,<br><br>108,215,308,272,<br><br>246,185,125,100 | Y threshold for determining whether the current processing pixel is on the edge.<br><br>It has eight thresholds mapping to pixel brightness from dark to bright, respectively.<br><br>\[0\]\[0~7\] is the threshold from dark to bright for high frequency image.<br><br>\[1\]\[0~7\] is the threshold from dark to bright for middle frequency image. |
| t\_cb\_edge_detection | 0~1023 | 0,249 | Cb threshold for determining whether the current processing pixel is on the edge. Only works in middle frequency image. |
| t\_cr\_edge_detection \[2\] | 0~1023 | 0,249 | Cr threshold for determining whether the current processing pixel is on the edge. Only works in middle frequency image. |
| t\_y\_edge_smoothing\[2\]\[8\] | 0~255 | 66,132,161,149,<br><br>140,107,80,53,<br><br>44,88,103,91,<br><br>82,62,51,41 | Y threshold for determining whether it will perform smooth process.<br><br>It has eight thresholds mapping to pixel brightness from dark to bright, respectively.<br><br>\[0\]\[0~7\] is the threshold from dark to bright for high frequency image.<br><br>\[1\]\[0~7\] is the threshold from dark to bright for middle frequency image. |
| t\_cb\_edge_smoothing \[2\] | 0~255 | 0,153 | Cb threshold for determining whether it will perform smooth process. Only works in middle frequency image. |
| t\_cr\_edge_smoothing \[2\] | 0~255 | 0,153 | Cr threshold for determining whether it will perform smooth process. Only works in middle frequency image. |
| nr\_strength\_y\[2\] | 0~15 | {0, 0} | The denoise strength of spatial domain on Y channel.<br><br>\[0\] is denoise strength for high frequency image.<br><br>\[1\] is denoise strength for middle frequency image. |
| nr\_strength\_c | 0~15 | {0, 10} | The denoise strength of spatial domain on Cb/Cr channel. Only works in middle frequency image. |

**Advance description**:

l edge_smoothing?: When SPNR performs smooth process, it will calculate weighting sum of neighbor pixels along the edge direction, if the difference between the neighbor pixel and center pixel is larger than threshold, this neighbor pixel will not be used in the smooth process. The smooth process of Y/Cb/Cr are the same.

### 3.3 Setting Interface

#### 3.3.1 Proc

###### l /proc/videograph/vpe/mrnr/dump_info

**\[Description\]**

Read all SPNR(using MRNR method) parameters of the current camera channel.

**\[Command\]**

**Write : Not support.**

**Read : cat /proc/videograph/vpe/mrnr/dump_info**

**Output:** **![文字方塊: channel <ch_no> = enable/disable
t_y_edge_detection\[0\]\[8\] = t_y_edge_detection\[0\]\[0\] ….\[0\]\[7\]
t_y_edge_detection\[1\]\[8\] = t_y_edge_detection\[1\]\[0\] ….\[1\]\[7\]
t_cb_edge_detection = t_cb_edge_detection
t_cr_edge_detection = t_cr_edge_detection
t_y_edge_smoothing\[0\]\[8\] = t_y_edge_smoothing\[0\]\[0\]……\[0\]\[7\]
t_y_edge_smoothing\[1\]\[8\] = t_y_edge_smoothing\[1\]\[0\]……\[1\]\[7\]
t_cb_edge_smoothing = t_cb_edge_smoothing
t_cr_edge_smoothing = t_cr_edge_smoothing
nr_strength_y\[2\] = nr_strength_y\[0\], nr_strength_y\[0\]
nr_strength_c = nr_strength_c
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image009.png)**

###### l /proc/videograph/vpe/mrnr/mrnr_en

**\[Description\]**

Read or write the MRNR enable status of the current camera channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| **echo \[mrnr\_en (0~1)\] > /proc/videograph/vpe/mrnr/mrnr\_en** | **mrnr_en** |

**Read : cat /proc/videograph/vpe/mrnr/mrnr_en**

**Output:** **![文字方塊: Command : echo \[ch_en (0~1)\] > /proc/videograph/vpe/mrnr/mrnr_en](NT9833x_VPE_IQ_Tuning_Guide_en.files/image010.png)**

###### l /proc/videograph/vpe/mrnr/t\_xx\_edge_det

**\[Description\]**

Read or write edge_detection parameters.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[t\_y\_edge\_det\[0\]\[0\] …..\[0\]\[7\]\] > /proc/videograph/vpe/mrnr/ t\_y\_edge\_det_1 | **t\_y\_edge_detection\[0~7\]** |
| echo \[t\_y\_edge\_det\[1\]\[0\] …..\[1\]\[7\]\] > /proc/videograph/vpe/mrnr/ t\_y\_edge\_det_2 | **t\_y\_edge_detection\[8~15\]** |
| echo \[t\_cb\_edge\_det\] > /proc/videograph/vpe/mrnr/ t\_cb\_edge\_det | **t\_cb\_edge_detection\[0~1\]** |
| echo \[t\_cr\_edge\_det\] > /proc/videograph/vpe/mrnr/ t\_cr\_edge\_det | **t\_cr\_edge_detection\[0~1\]** |

**Read :**

**cat /proc/videograph/vpe/mrnr/**t\_y\_edge\_det\_1

**cat /proc/videograph/vpe/mrnr/**t\_y\_edge\_det\_2

**cat /proc/videograph/vpe/mrnr/**t\_cb\_edge\_det\_1

**cat /proc/videograph/vpe/mrnr/**t\_cr\_edge\_det\_1

**Output :**

**![文字方塊: Command :
echo \[t_y_edge_det\[0\]\[0\] …….. \[0\]\[7\] > /proc/videograph/vpe/mrnr/ t_y_edge_det_1
echo \[t_y_edge_det\[1\]\[0\] …….. \[0\]\[7\] > /proc/videograph/vpe/mrnr/ t_y_edge_det_2
echo \[t_cb_edge_det > /proc/videograph/vpe/mrnr/ t_cb_edge_det
echo \[t_cr_edge_det > /proc/videograph/vpe/mrnr/ t_cr_edge_det
===============================================================
t_y_edge_det1 = t_y_edge_detection \[0\] \[0\] …………….\[0\]\[7\]
t_y_edge_det2 = t_y_edge_detection \[1\] \[0\]…………….. \[0\]\[7\]
t_cb_edge_det = t_cb_edge_detection
t_cr_edge_det = t_cb_edge_detection 
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image011.png)**

###### l /proc/videograph/vpe/mrnr/t\_xx\_edge_smooth

**\[Description\]**

Read or write edge_smoothing parameters.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[t\_y\_edge\_smooth\[0\]\[0\]\] ……..\[t\_y\_edge\_smooth \[0\]\[7\]\] > /proc/videograph/vpe/mrnr/ t\_y\_edge\_smooth\_1 | **t\_y\_edge_ smoothing\[0~7\]** |
| echo \[t\_y\_edge\_smooth\[1\]\[0\] …….. \[t\_y\_edge\_smooth\[1\] \[7\]\] > /proc/videograph/vpe/mrnr/t\_y\_edge\_smooth\_2 | **t\_y\_edge_ smoothing\[8~16\]** |
| echo \[t\_cb\_edge\_smooth\] > /proc/videograph/vpe/mrnr/ t\_cb\_edge\_smooth | **t\_cb\_edge_smoothing\[0~1\]** |
| echo \[t\_cr\_edge\_smooth\] > /proc/videograph/vpe/mrnr/ t\_cr\_edge\_smooth | **t\_cr\_edge_ smoothing\[0~1\]** |

**Read :**

cat /proc/videograph/vpe/mrnr/t\_y\_edge\_smooth\_1

cat /proc/videograph/vpe/mrnr/t\_y\_edge\_smooth\_2

cat /proc/videograph/vpe/mrnr/t\_cb\_edge_smooth

cat /proc/videograph/vpe/mrnr/t\_cr\_edge_smooth

**Output :**

**![文字方塊: Command :
echo \[t_y_edge_smooth\[0\]\] …….. \[t_y_edge_smooth \[7\]\] > /proc/videograph/vpe/mrnr/t_y_edge_smooth_1
…
===============================================================

t_y_edge_smooth1 = t_y_edge_smoothing\[0\]\[0\] ……………. \[0\]\[7\]
t_y_edge_smooth1 = t_y_edge_smoothing \[1\]\[0\]…………….. \[0\]\[7\]
t_cb_edge_smooth = t_cb_edge_smoothing
t_cr_edge_smooth = t_cr_edge_smoothing
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image012.png)**

###### l /proc/videograph/vpe/mrnr/nr_strength

**\[Description\]**

Read or write nr_strength parameters on Y/C channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[strength\_y\[0\]\] \[strength\_y \[1\]\] \[strength\_c\] > /proc/videograph/vpe/mrnr/nr\_strength | **nr\_strength\_y\[0~1\], nr\_strength\_c** |

**Read : cat /proc/videograph/vpe/mrnr/ nr_strength**

**Output :**

**![文字方塊: Command :
echo \[strength_y\[0\]\] \[strength_y \[1\]\] \[strength_c\]\] > /proc/videograph/vpe/mrnr/nr_strength ===============================================================
nr_strength_y = nr_strength_y\[0\], strength_y \[1\]
nr_strength_c= nr_strength_c
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image013.png)**

#### 3.3.2 Vendor API

**\[Description\]**

Get and set the 2DNR parameters corresponding to current path_id.

**\[Command\]**

??????? **Get****：**

HD\_RESULT vendor\_video\_get(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_DN\_2D, VENDOR\_VIDEO\_PARAM\_MRNR *p_param);

**??????? Set****：**

HD\_RESULT vendor\_video\_set(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_DN\_2D, VENDOR\_VIDEO\_PARAM\_MRNR *p_param);

**\[Definition\]**

**![文字方塊: typedef struct _VENDOR_VIDEO_MRNR {
	UINT32 mrnr_en;  					///< MRNR ON/OFF
	UINT32 t_y_edge_detection\[2\]\[8\]; 	///< Edge pixel detection threshold of Y{layer1~layer2}, 0~1023
	UINT32 t_cb_edge_detection; 		///< Edge pixel detection threshold of Cb{layer2}, 0~1023
	UINT32 t_cr_edge_detection; 		///< Edge pixel detection threshold of Cr{layer2}, 0~1023
	UINT32 t_y_edge_smoothing\[2\]\[8\]; 	///< Edge pixel smoothing threshold of Y: {layer1~layer2}, 0~255
	UINT32 t_cb_edge_smoothing; 		///< Edge pixel smoothing threshold of Cb: {layer2}, 0~255
	UINT32 t_cr_edge_smoothing;			///< Edge pixel smoothing threshold of Cr: {layer2}, 0~255
	UINT32 nr_strength_y\[2\]; 			///< Strength of noise reduction of Y: {layer1~layer2}, 0~15
	UINT32 nr_strength_c; 				///< Strength of noise reduction of CbCr: {layer2}, 0~15
} VENDOR_VIDEO_PARAM_MRNR;
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image014.png)**

4 Temporal Noise Reduction (TMNR)
---------------------------------

This is temporal noise reduction module(abbreviation is “TMNR”). The major function is to eliminate temporal noise in the image.

### 4.1 Overview

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image015.png)

The concept of TMNR algorithm is to determine whether the pixel status is static(MotionLevel=0) or motion(MotionLevel=2) by Motion Detect module. The static region perform 3DNR to reduce the temporal noise, and the motion region will not perform 3DNR to prevent from having ghost, instead, it will perform 2DNR to reduce noise. The transition region between static region and motion region will combine the result of 2DNR and 3DNR by weighting.

### 4.2 Parameter description

(The blue text is the part of the parameter difference between this module and the 9831x series, please pay special attention)

Table 4?1  TMNR Parameter List

|     |     |     |     |
| --- | --- | --- | --- |
| **Parameter** | **Range** | **Default** | **Description** |
| **_tmnr_en_** | 0~1 | 1   | TMNR ON/OFF |
| **_luma\_dn\_en_** | 0~1 | 1   | Y channel TMNR ON/OFF |
| **_chroma\_dn\_en_** | 0~1 | 1   | Cb/Cr channel TMNR ON/OFF |
| **_tmnr\_fcs\_en_** | 0~1 | 0   | Temporal de-false color function ON/OFF<br><br>It only works when “chroma\_dn\_en” is set to 1.<br><br>Please refer to advance description. |
| **_nr\_str\_y_3d_** | 0~32 | 8   | Y channel temporal NR strength |
| **_nr\_str\_y_2d_** | 0~32 | 16  | Y channel spatial NR strength of motion object |
| **_nr\_str \_c_3d_** | 0~32 | 16  | Cb/Cr channel temporal NR strength |
| **_nr\_str \_c_2d_** | 0~32 | 16  | Cb/Cr channel spatial NR strength of motion object |
| **_blur\_str\_y_** | 0~2 | 1   | Y image blurred strength<br><br>0: No blur<br><br>1: low-strength blur<br><br>2: high-strength blur<br><br>※It is recommend to set enable, if the executing sequence of 3DNR is after Sharpness; otherwise, it is recommend to set disable. For DVR/NVR application, due to in most case the front-end camera had perfomed sharpen process, it is recommend to set 1. |
| **_center\_wzero\_y\_2d\_en_** | 0~1 | 1   | Set to enable represents when performing the 2DNR, the weighting of center point is 0. It will increase NR strength, but might lose detail. Due to 2DNR only works on motion region, the detail loss is not obvious, it is recommend to fix enable. |
| **_center\_wzero\_y\_3d\_en_** | 0~1 | 1   | Set to enable represents when performing 3DNR, the weighting of center point is 0. It is recommend to fix enable. |
| **_small\_vibrat\_supp\_y\_en_** | 0~1 | 0   | Y channel small vibration suppresiioon ON/OFF. This function will enhance suppression on small vibration noise to make the image more stable. However, it also causes slower ghost removal. It is recommend to enable at normal luminance, and disable at dark luminance. |
| **_avoid\_residue\_th_y_** | 1~4 | 2   | Upper threshold for Y channel small noise putting back.<br><br>If **err_compen****_sate_** = 0, bigger this value will cause smaller temporal noise. On the other hand, if err_compensate = 1, bigger this value will cause bigger temporal noise. |
| **_avoid\_residue\_th_c_** | 1~4 | 1   | Upper threshold for Vb/Cr channel small noise putting back.<br><br>If **err_compensate** = 0, bigger this value will cause smaller temporal noise. On the other hand, if err_compensate = 1, bigger this value will cause bigger temporal noise. |
| **_display\_motion\_map_en_** | 0~1 | 0   | Debug mode. Show motion detection result on the image to assist to judge the correctness of motion detect parameters.<br><br>Please refer to advance description. |
| **_motion\_map\_channel_** | 0~4 | 0   | Select debug signal channel.<br><br>0: Y channel<br><br>1: Cb channel<br><br>2: Cr channel<br><br>3: temporal de-false color Cb channel<br><br>4: temporal de-false color Cr channel |
| **_y_base\[8\]_** | 0~16320 | {146,147,107,110,102,104,104,104} | y\_base\[0\]-\[7\] are NoiseSAD mapping to pixel brightness from dark to bright. When performing 2DNR, the internal algorithm will automatically fine tune strength based on y\_base. The larger the y\_base, the stronger strength of 2DNR of motion object. It is recommend to increase y\_base as sensor gain increases. |
| **_motion\_level\_th\_y\_k1_** | 0~32 | 8   | Threshold (motion\_level\_th\_y\_k1*Y\_NOISE) for determining transition region on Y channel. Y\_NOISE please refer to advance description. |
| **_motion\_level\_th\_y\_k2_** | 0~32 | 8   | Threshold (motion\_level\_th\_y\_k2*Y_NOISE) for determining motion region on Y channel.<br><br>K2 must larger or equal to K1. |
| **_y_coefa\[8\]_** | 0~48 | {0,0,0,0,0,0,0,0} | The slope of NoiseSAD from flat region to detail region on Y channel. y_coefa\[0\]-\[7\] mapping to pixel brightness from dark to bright. |
| **_y_coefb\[8\]_** | 0~16320 | {27,27,20,12,7,10,10,10} | NoiseSAD of flat region on Y channel. y_coefb\[0\]-\[7\] mapping to pixel brightness from dark to bright. |
| **_y_std\[8\]_** | 0~16320 | {20,70,70,70,70,50,28,18} | The standard deviation of NoiseSAD on Y channel. y_std\[0\]-\[7\] mapping to pixel brightness from dark to bright. |
| **_motion\_level\_th\_c\_k1_** | 0~32 | 8   | Threshold for determining transition region on Cb/Cr channel. |
| **_motion\_level\_th\_c\_k2_** | 0~32 | 8   | Threshold for determining motion region on Cb/Cr channel, K2 must larger or equal to K1. |
| **_cb_mean\[8\]_** | 0~6375 | {33,33,34,32,29,28,28,28} | The NoiseSAD mean value on Cb channel. cb_mean\[0\]-\[7\] mapping to pixel brightness from dark to bright. |
| **_cb_std\[8\]_** | 0~6375 | {10,9,10,10,9,9,9,9} | The standard deviation of NoiseSAD on Cb channel. cb_std\[0\]-\[7\] mapping to pixel brightness from dark to bright. |
| **_cr_mean\[8\]_** | 0~6375 | {23,23,25,23,20,20,21,21} | The NoiseSAD mean value on Cr channel. cr_mean\[0\]-\[7\] mapping to pixel brightness from dark to bright. |
| **_cr_std\[8\]_** | 0~6375 | {7,7,8,7,7,77,7} | The standard deviation of NoiseSAD on Cr channel. cr_std\[0\]-\[7\] mapping to pixel brightness from dark to bright. |
| **_lut\_y\_3d\_1\_Th\[4\]_** | 0~127 | {11,33,55,77} | Lut of Y channel 3D_1 filter<br><br>Please refer to advance description. |
| **_lut\_y \_3d\_2\_Th\[4\]_** | 0~127 | {40,14,7,3} | Lut of Y channel 3D_2 filter<br><br>Please refer to advance description. |
| **_lut\_y\_2d_Th\[4\]_** | 0~127 | {11,33,55,77} | Lut of Y channel 2D filter<br><br>Please refer to advance description. |
| **_lut\_c\_3d_Th\[4\]_** | 0~127 | {37,19,11,7} | Lut of Cb/Cr channel 3D filter<br><br>Please refer to advance description. |
| **_lut\_c\_2d_Th\[4\]_** | 0~127 | {11,33,55,77} | Lut of Cb/Cr channel 2D filter<br><br>Please refer to advance description. |
| **_tmnr\_fcs\_str_** | 0~15 | 4   | The strength of temporal de-false color function. |
| **_tmnr\_fcs\_th_** | 0~255 | 32  | Threshold for the difference between the previous frame and the current frame to determine whether it is false color. |
| **_dithering_en_** | 0~1 | 1   | Dithering enable. This function can be used to eliminate slight power noise or flicker phenomenon. |
| **_dithering\_bit\_y_** | 0~3 | 2   | Y channel random bit number. The higher the value, the stronger the ability to eliminate the power noiser and filcker phenomenon, but the picture may appear larger fine noise. |
| **_dithering\_bit\_u_** | 0~3 | 1   | U channel random bit number. The higher the value, the stronger the ability to eliminate the power noiser and filcker phenomenon, but the picture may appear larger fine noise. |
| **_dithering\_bit\_v_** | 0~3 | 1   | V channel random bit number. The higher the value, the stronger the ability to eliminate the power noiser and filcker phenomenon, but the picture may appear larger fine noise. |
| **_err_compensate_** | 0~1 | 1   | YC Compression error compensation.<br><br>0: Antiflicker mode. (Larger anti-flicker effect)<br><br>1: Compensation mode. (Data Compression Error Compensation) |

**Advance Description:**

l **_tmnr\_fcs\_en:_**  Temporal de-false color ON/OFF. This function will eliminate color-flash phenomenon in high frequency region.

|     |     |
| --- | --- |
| **FCS off** | **FCS on** |
| ![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image016.jpg) | ![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image017.jpg) |

**_![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image018.png)_**

l **_display\_motion\_map_en:_**。

Motion region will label with red color, static region will label with black color, and transition region will label with white color.

|     |     |
| --- | --- |
| Original image | Motion Map |
| ![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image019.jpg) | ![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image020.jpg) |

l **_Y_NOISE_****:**  Block SAD is the summation of pixel difference between the previous frame and current frame at the same location. If the Block SAD is larger than K2*NoiseSAD\_STD(NoiseSAD\_STD is the input parameter), it determines as motion region. If the Block SAD is smaller than K1*NoiseSAD_STD, it determines as static region. If the Block SAD is larger than K1\*NoiseSAD\_STD and smaller than K2\*NoiseSAD\_STD, it determines as transition region.

As follows :

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image021.png)

l Cb\_NOISE, Cr\_NOISE:

Different from Y channel, the NoiseSAD of Cb/Cr channel has no relationship with detail. Therefore, it has no slope parameter.

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image022.png)

l **_lut\_Y\_3d\_1\_Th:_**  Weighting Lut for stage 1 3DNR on Y channel, the x-axis is delta difference of neighbor pixel, the y-axis is weighting. As the following figure, the larger the difference, the smaller the weighting. The smaller the difference, the larger the weighting. Then, based on each weighting to perform weighting sum.

**_![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image023.png)_**

l **_lut\_Y\_3d\_2\_Th:_**  Weighting Lut for Stage 2 3DNR on Y channel, the x-axis is difference of the reference point between the previous frame and current frame, the y-axis is weighting. As the following figure, those with smaller difference might be static region, and set smaller weighting, the output will close to the reference frame. On the contrast, those with larger difference might be motion region, and set larger weighting, the output will close to the current frame.

**_![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image024.png)_**

l **_lut\_Y\_2d_Th:_**  Weighting Lut of neighbor pixel for 2DNR on Y channel, the x-axis is difference, the y-axis is weighting. As the following figure, the larger the difference, the smaller the weighting. The smaller the difference, the larger the weighting. Then, based on each weighting to perform weighting sum.

**_![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image025.png)_**

l **_lut\_c\_3d_Th:_** Suppression Level Lut for 3DNR on Cb/Cr channel, the x-axis is the difference of the reference point between the previous frame and current frame, the y-axis is the suppression level. The concept is the same with “**_LUT\_Y\_3d\_2\_Th_**”.

l **_lut\_c\_2d_Th:_**  Weighting Lut of neighbor pixel for 2DNR on Cb/Cr channel, the x-axis is difference, the y-axis is weighting. The concept is the same with “**_lut\_Y\_2d_Th_**”.

### 4.3 Setting Interface

#### 4.3.1 Proc

###### l /proc/videograph/vpe/tmnr/dump_info

**\[Description\]**

Read all parameters of the current camera channel.

**\[Command\]**

**Write : Not support.**

**Read :**

cat /proc/videograph/vpe/tmnr/dump_info

**Output :**

**![文字方塊: luma_dn_en = luma_dn_en
chroma_dn_en = chroma_dn_en
tmnr_fcs_en = tmnr_fcs_en
nt_str_y_3d = nt_str_y_3d
nr_str_y_2d = nr_str_y_2d
nr_str_c_3d = nr_str_c_3d
nr_str_c_2d = nr_str_c_2d
blur_str_y = blur_str_y
center_wzero_y_2d_en = center_wzero_y_2d_en
center_wzero_y_3d_en = center_wzero_y_3d_en
small_vibrat_supp_y_en = small_vibrat_supp_y_en
avoid_residue_th_y = avoid_residue_th_y
avoid_residue_th_c = avoid_residue_th_c
y_base\[8\] = y_base\[0\] ….. y_base\[7\]
motion_level_th_y = motion_leve_tTh_y_k1, motion_level_th_y_k2
motion_level_th_c = motion_level_th_c_k1, motion_level_th_c_k2
y_coefa\[8\] = y_coefa\[0\] …y_coefa\[7\]
y_coefb\[8\] = y_coefb\[0\] …y_coefb\[7\]
y_std\[8\] = y_std\[0\] …y_std\[7\]
cb_mean\[8\] = cb_mean\[0\] …. cb_mean\[7\]
cb_std\[8\] = cb_std\[0\]……..cb_std\[7\]
cr_mean\[8\] = cr_mean\[0\] …. cr_mean\[7\]
cr_std\[8\] = cr_std\[0\]……..cr_std\[7\]
lut_y_3d_1_th\[4\] = lut_y_3d_1_th\[0\]  ….. lut_y_3d_1_th\[3\]
lut_y_3d_2_th\[4\] = lut_y_3d_2_th\[0\]  ….. lut_y_3d_2_th\[3\]
lut_y_2d_th\[4\] = lut_y_2d_th\[0\]……lut_y_2d_th\[3\]
lut_c_3d_th\[4\] = lut_c_3d_th\[0\]……. lut_c_3d_th\[3\]
lut_c_2d_th\[4\] = lut_c_2d_th\[0\]…….. lut_c_2d_th\[3\]
tmnr_fcs_str = tmnr_fcs_str
tmnr_fcs_th = tmnr_fcs_th
dithering_en = dithering_en
dithering_bit_y = dithering_bit_y
dithering_bit_u = dithering_bit_u
dithering_bit_v = dithering_bit_v
err_compensate = err_compensate
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image026.png)**

###### l /proc/videograph/vpe/tmnr/ch\_en\_status

**\[Description\]**

Read or write the enable status of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[luma\_en\] \[chroma\_en\] \[fcs\_en\] > /proc/videograph/vpe/tmnr/ch\_en_status | **luma\_dn\_en**<br><br>**chroma\_dn\_en**<br><br>**tmnr\_fcs\_en** |

**Read :**

**cat /proc/videograph/vpe/tmnr/ch\_en\_status**

**Output :**

**![文字方塊: Command : 
echo \[luma_en\] \[chroma_en\] \[fcs_en\] > /proc/videograph/vpe/tmnr/ch_en_status ===============================================================

luma_en = luma_dn_en
chroma_en = chroma_dn_en
fcs_en = tmnr_fcs_en
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image027.png)**

###### l /proc/videograph/vpe/tmnr/nr_strength

**\[Description\]**

Read or write the TMNR strength of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[y\_3d\_str\] \[y\_2d\_str\] \[c\_3d\_str\] \[c\_2d\_str\] > /proc/videograph/vpe/tmnr/nr_strength | **nr\_str\_y\_3d, nr\_str\_y\_2d**<br><br>**nr\_str\_c\_3d, nr\_str\_c\_2d** |

**Read :**

**cat /proc/videograph/vpe/tmnr/nr_strength**

**Output :**

**![文字方塊: Command : 
echo \[y_3d_str\] \[y_2d_str\] \[c_3d_str\] \[c_2d_str\] > /proc/videograph/vpe/tmnr//proc/videograph/vpe/tmnr/nr_strength ===============================================================

nr_str_y_3d = nr_str_y_3d
nr_str_y_2d = nr_str_y_2d
nr_str_c_3d = nr_str_c_3d
nr_str_c_2d = nr_str_c_2d
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image028.png)**

###### l /proc/videograph/vpe/tmnr/y_base

**\[Description\]**

Read or write the base noise level of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[y\_base0\] \[y\_base1\]………\[y\_base7\] > /proc/videograph/vpe/tmnr/y\_base | **y_base\[0\]~\[7\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/y_base**

**Output :**

**![文字方塊: Command : 
echo \[y_base0\] \[y_base1\]………\[y_base7\] > /proc/videograph/vpe/tmnr/y_base ===============================================================

TMNR Noise Y_base = y_base\[0\]…………y_base\[7\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image029.png)**

###### l /proc/videograph/vpe/tmnr/motion\_level\_th

**\[Description\]**

Read or write the noise model parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[y\_k1\] \[y\_k2\] \[c\_k1\] \[c\_k2\] > /proc/videograph/vpe/tmnr/motion\_level\_th | **motion\_level\_th\_y\_k1**<br><br>**motion\_level\_th\_y\_k2**<br><br>**motion\_level\_th\_c\_k1**<br><br>**motion\_level\_th\_c\_k2** |

**Read :**

**cat /proc/videograph/vpe/tmnr/motion\_level\_th**

**Output :**

**![文字方塊: Command : 
echo \[y_k1\] \[y_k2\] \[c_k1\] \[c_k2\] > /proc/videograph/vpe/tmnr/motion_level_th ===============================================================

TMNR motion level th = motion_level_th_y_k1, motion_level_th_y_k2, motion_level_th_c_k1, motion_level_th_c_k2,
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image030.png)**

###### l /proc/videograph/vpe/tmnr/y_coeffa

**\[Description\]**

Read or write the noise model parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[y\_coeffa0\] \[y\_coeffa1\]………\[y\_coeffa7\] > /proc/videograph/vpe/tmnr/y\_coeffa | **y_coeffa\[0\]~\[7\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/y_coeffa**

**Output :**

**![文字方塊: Command : 
echo \[y_coeffa0\] \[y_coeffa1\]………\[y_coeffa7\] > /proc/videograph/vpe/tmnr/y_coeffa ===============================================================

TMNR Noise model y_coeffa = y_coeffa\[0\]…………y_coeffa\[7\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image031.png)**

###### l /proc/videograph/vpe/tmnr/y_coeffb

**\[Description\]**

Read or write the noise model parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[y\_coeffb0\] \[y\_coeffb1\]………\[y\_coeffb7\] > /proc/videograph/vpe/tmnr/y\_coeffb | **y_coeffb\[0\]~\[7\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/y_coeffb**

**Output :**

**![文字方塊: Command : 
echo \[y_coeffb0\] \[y_coeffb1\]………\[y_coeffb7\] > /proc/videograph/vpe/tmnr/y_coeffb ===============================================================

TMNR Noise model y_coeffb = y_coeffb\[0\]…………y_coeffb\[7\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image032.png)**

###### l /proc/videograph/vpe/tmnr/y_std

**\[Description\]**

Read or write the noise model parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[y\_std0\] \[y\_std1\]………\[y\_std7\] > /proc/videograph/vpe/tmnr/y\_std | **y_std\[0\]~\[7\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/y_std**

**Output :**

**![文字方塊: Command : 
echo \[y_std0\] \[y_std1\]………\[y_std7\] > /proc/videograph/vpe/tmnr/y_std ===============================================================

TMNR Noise model y_std = y_std\[0\]…………y_std\[7\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image033.png)**

###### l /proc/videograph/vpe/tmnr/cb_mean

**\[Description\]**

Read or write the noise model parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[cb\_mean0\] \[cb\_mean1\]………\[cb\_mean 7\] > /proc/videograph/vpe/tmnr/cb\_mean | **cb_mean\[0\]~\[7\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/cb_mean**

**Output :**

**![文字方塊: Command : 
echo \[cb_mean0\] \[cb_mean1\]………\[cb_mean 7\] > /proc/videograph/vpe/tmnr/cb_mean ===============================================================

TMNR Noise model cb_mean = cb_mean\[0\]…………cb_mean\[7\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image034.png)**

###### l /proc/videograph/vpe/tmnr/cb_std

**\[Description\]**

Read or write the noise model parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[cb\_std0\] \[cb\_std1\]………\[cb\_std7\] > /proc/videograph/vpe/tmnr/cb\_std | **cb_std\[0\]~\[7\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/cb_std**

**Output :**

**![文字方塊: Command : 
echo \[cb_std0\] \[cb_std1\]………\[cb_std7\] > /proc/videograph/vpe/tmnr/cb_std ===============================================================
TMNR Noise model cb_std = cb_std\[0\]…………cb_std\[7\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image035.png)**

###### l /proc/videograph/vpe/tmnr/cr_mean

**\[Description\]**

Read or write the noise model parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[cr\_mean0\] \[cr\_mean1\]………\[cr\_std7\] > /proc/videograph/vpe/tmnr/cr\_mean | **cr_std\[0\]~\[7\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/cr_mean**

**Output :**

**![文字方塊: Command : 
echo \[cr_mean0\] \[cr_mean1\]………\[cr_std7\] > /proc/videograph/vpe/tmnr/cr_mean ===============================================================

TMNR Noise model cr_mean = cr_mean\[0\]…………cr_mean\[7\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image036.png)**

###### l /proc/videograph/vpe/tmnr/cr_std

**\[Description\]**

Read or write the noise model parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[cr\_std0\] \[cr\_std1\]………\[cr\_std7\] \] > /proc/videograph/vpe/tmnr/cr\_std | **cr_std\[0\]~\[7\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/cr_std**

**Output :**

**![文字方塊: Command : 
echo \[cr_std0\] \[cr_std1\]………\[cr_std7\] > /proc/videograph/vpe/tmnr/cr_std ===============================================================

TMNR Noise model cr_std = cr_std\[0\]…………cr_std\[7\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image037.png)**

###### l /proc/videograph/vpe/tmnr/lut\_y\_3d\_1\_th

**\[Description\]**

Read or write the 3D noise reduction parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut\_y\_3d\_1\_th | **lut\_y\_3d\_1\_th\[0\]~\[3\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/lut\_y\_3d\_1\_th**

**Output :**

**![文字方塊: Command : 
echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut_y_3d_1_th ===============================================================
TMNR lut_y_3d_1_th = lut_y_3d_1_th\[0\]…th\[3\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image038.png)**

###### l /proc/videograph/vpe/tmnr/lut\_y\_3d\_2\_th

**\[Description\]**

Read or write the 3D noise reduction parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut\_y\_3d\_2\_th | **lut\_y\_3d\_2\_th\[0\]~\[3\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/lut\_y\_3d\_2\_th**

**Output :**

**![文字方塊: Command : 
echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut_y_3d_2_th ===============================================================
TMNR lut_y_3d_2_th = lut_y_3d_2_th\[0\]…th\[3\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image039.png)**

###### l /proc/videograph/vpe/tmnr/lut\_y\_2d_th

**\[Description\]**

Read or write the 2D noise reduction parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut\_y\_2d_th | **lut\_y\_2d_th\[0\]~\[3\]** |

**Read :**

cat /proc/videograph/vpe/tmnr/lut\_y\_2d_th

**Output :**

**![文字方塊: Command : 
echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut_y_2d_th ===============================================================

TMNR lut_y_2d_th = lut_y_2d_th\[0\]…th\[3\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image040.png)**

###### l /proc/videograph/vpe/tmnr/lut\_c\_3d_th

**\[Description\]**

Read or write the 3D noise reduction parameters of 3DNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut\_c\_3d_th | **lut\_c\_3d_th\[0\]~\[3\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/lut\_c\_3d_th**

**Output :**

**![文字方塊: Command : 
echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut_c_3d_th ===============================================================

TMNR lut_c_3d_th = lut_c_3d_th\[0\]…th\[3\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image041.png)**

###### l /proc/videograph/vpe/tmnr/lut\_c\_2d_th

**\[Description\]**

Read or write the 2D noise reduction parameters of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut\_c\_2d_th | **lut\_c\_2d_th\[0\]~\[3\]** |

**Read :**

**cat /proc/videograph/vpe/tmnr/lut\_c\_2d_th**

**Output :**

**![文字方塊: Command : 
echo \[th0\] \[th1\] \[th2\] \[th3\] > /proc/videograph/vpe/tmnr/lut_c_2d_th ===============================================================

TMNR lut_c_3d_th = lut_c_2d_th\[0\]…th\[3\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image042.png)**

###### l /proc/videograph/vpe/tmnr/fcs_str

**\[Description\]**

Read or write the false color suppression strength of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[fcs\_str (0~15) \] > /proc/videograph/vpe/tmnr/fcs\_str | **tmnr\_fcs\_str** |

**Read :**

cat /proc/videograph/vpe/tmnr/fcs_str

**Output :**

**![文字方塊: Command : 
echo \[fcs_str (0~15) \] > /proc/videograph/vpe/tmnr/fcs_str ===============================================================

TMNR FCS strength = tmnr_fcs_str
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image043.png)**

###### l /proc/videograph/vpe/tmnr/fcs_th

**\[Description\]**

Read or write the threshold for determining whether it is false color of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[fcs\_th (0~255) \] > /proc/videograph/vpe/tmnr/fcs\_th | **tmnr\_fcs\_th** |

**Read :**

cat /proc/videograph/vpe/tmnr/fcs_th

**Output :**

**![文字方塊: Command : 
echo \[fcs_th (0~255) \] > /proc/videograph/vpe/tmnr/fcs_th ===============================================================

TMNR FCS th = tmnr_fcs_th
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image044.png)**

###### l /proc/videograph/vpe/tmnr/motion_map

**\[Description\]**

Read or write the motion map of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[map\_en (0~1)\] > \[map\_idx\] > /proc/videograph/vpe/tmnr/motion_map<br><br>map_en:<br><br>0: display\_motion\_map_en = 0<br><br>1: display\_motion\_map_en = 1<br><br>map_idx :<br><br>?0: motion\_map\_channel=Y<br><br>?1: motion\_map\_channel=Cb<br><br>2: motion\_map\_channel=Cr<br><br>3: motion\_map\_channel=FCS_Cb<br><br>4: motion\_map\_channel=FCS_Cr | **display\_motion\_map_en,**<br><br>**motion\_map\_channel** |

**Read :**

cat /proc/videograph/vpe/tmnr/motion_map

**Output :**

**![文字方塊: Command : 
echo \[map_en (0~1)\] \[map_idx (0~4)\] > /proc/videograph/vpe/tmnr/motion_map
===============================================================

TMNR motion_map : 
map_en = display_motion_map_en 
map_channel = motion_map_channel
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image045.png)**

###### l /proc/videograph/vpe/tmnr/diff\_blur\_str

**\[Description\]**

Read or write the Diff. image blur strength of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[str (0~2)\] > /proc/videograph/vpe/tmnr/diff\_blur\_str<br><br>str: blur strength 0 ~2 | **blur\_str\_y** |

**Read :**

cat /proc/videograph/vpe/tmnr/diff\_blur\_str

**Output :**

**![文字方塊: Command : 
echo \[str (0~2)\] > /proc/videograph/vpe/tmnr/diff_blur_str
===============================================================

diff_blur_str = blur_str_y
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image046.png)**

###### l /proc/videograph/vpe/tmnr/avoid\_residue\_th

**\[Description\]**

Read or write the Diff. image blur strength of TMNR of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[avoid\_residue\_th\_y (1~4)\] \[avoid\_residue\_th\_c (1~4)\] > /proc/videograph/vpe/tmnr/avoid\_residue\_th | **avoid\_residue\_th\_y, avoid\_residue\_th\_c** |

**Read :**

cat /proc/videograph/vpe/tmnr/avoid\_residue\_th

**Output :**

**![文字方塊: Command : 
echo \[avoid_residue_th_y (1~4)\] \[avoid_residue_th_c (1~4)\] > /proc/videograph/vpe/ avoid_residue_th
===============================================================
avoid_residue_th_y= avoid_residue_th_y,  avoid_residue_th_c= avoid_residue_th_c
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image047.png)**

###### l /proc/videograph/vpe/tmnr/dithering

**\[Description\]**

 Read or write the dithering relative parameters of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[dithering\_en (0~1)\] \[dithering\_bit\_y (0~7)\] \[dithering\_bit\_u (0~7)\] \[dithering\_bit_v (0~7)\] > /proc/videograph/vpe/tmnr/dithering | **dithering_en**<br><br>**dithering\_bit\_y**<br><br>**dithering\_bit\_u**<br><br>**dithering\_bit\_v** |

**Read :**

cat /proc/videograph/vpe/tmnr/ dithering

**Output :**

**![文字方塊: Command : 
echo \[dithering_en (0~1)\] \[dithering_bit_y (0~7)\] \[dithering_bit_u (0~7)\] \[dithering_bit_v (0~7)\] > /proc/videograph/vpe/tmnr/dithering
===============================================================
dithering_en = dithering_en, dithering_bit_y = dithering_bit_y, dithering_bit_u = dithering_bit_u, dithering_bit_v = dithering_bit_v
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image048.png)**

###### l /proc/videograph/vpe/tmnr/err_compensate

**\[Description\]**

Read or write the err_compensate parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[err_compensate (0~1)\] > /proc/videograph/vpe/tmnr/err_compensate | **err_compensate** |

**Read :**

cat /proc/videograph/vpe/tmnr/err_compensate

**Output :**

**![文字方塊: Command : 
echo \[err_compensate (0~1)\] > /proc/videograph/vpe/tmnr/err_compensate
===============================================================
err_compensate = err_compensate
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image049.png)**

#### 4.3.2 Vendor API

**\[Description\]**

Get and set the TMNR parameters corresponding to current path_id.

**\[Command\]**

??????? **Get****：**

HD\_RESULT vendor\_video\_get(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_TMNR\_CTRL, VENDOR\_VIDEO\_PARAM\_TMNR\_EXT *p\_param);

??????? **Set****：**

HD\_RESULT vendor\_video\_set(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_DN\_2D, VENDOR\_VIDEO\_PARAM\_TMNR\_EXT *p\_param);

**\[Definition\]**

**![文字方塊: typedef struct _VENDOR_VIDEO_PARAM_TMNR_EXT {
	UINT32 tmnr_en;  		///< 3DNR ON/OFF
	UINT32 luma_dn_en;  	///< Y channel 3DNR ON/OFF
	UINT32 chroma_dn_en;  	///< CbCr channel 3DNR ON/OFF
	UINT32 nr_str_y_3d; 	///< Y channel temporal NR strength, 0~32
	UINT32 nr_str_y_2d; 	///< Y channel spatial NR strength, 0~32
	UINT32 nr_str_c_3d; 	///< CbCr channel temporal NR strength, 0~32
	UINT32 nr_str_c_2d; 	///< CbCr channel spatial NR strength, 0~32
	UINT32 blur_str_y; 		///< Difference Y image blurred strength (0: No blur, 1: low-strength blur, 2: high-strength blur)
	UINT32 center_wzero_y_2d_en; 	///< Apply zero to center weight of Y spatial Bilateral filter
	UINT32 center_wzero_y_3d_en; 	///< Apply zero to center weight of Y temporal Bilateral filter
	UINT32 small_vibrat_supp_y_en; 	///< Y channel small vibration suppression ON/OF
	UINT32 avoid_residue_th_y; 		///< 1~4
	UINT32 avoid_residue_th_c; 		///< 1~4
	UINT32 display_motion_map_en; 	///< Display motion level map ON/OFF
	UINT32 motion_map_channel; 		///< Channel selection for motion level map display (0:Y, 1:Cb, 2:Cr)
	UINT32 motion_level_th_y_k1; 	///< Y channel match level threshold 1 adjustment, 0~32
	UINT32 motion_level_th_y_k2; 	///< Y channel match level threshold 2 adjustment, 0~32 AND K2 > K1
	UINT32 motion_level_th_c_k1; 	///< CbCr channel match level threshold 1 adjustment, 0~32
	UINT32 motion_level_th_c_k2; 	///< CbCr channel match level threshold 2 adjustment, 0~32 AND K2 > K1
	UINT32 lut_y_3d_1_th\[4\]; 		///< LUT of Y channel 3d_1 filter, 0~127
	UINT32 lut_y_3d_2_th\[4\]; 		///< LUT of CbCr channel 3d filter, 0~127
	UINT32 lut_y_2d_th\[4\]; 			///< LUT of Y channel 2d filter, 0~127
	UINT32 lut_c_3d_th\[4\]; 			///< LUT of CbCr channel 3d filter, 0~127
	UINT32 lut_c_2d_th\[4\]; 			///< LUT of CbCr channel 2d filter, 0~127
	UINT32 y_base\[8\]; 				///< Y channel noise model parameter: base noise level, 0 ~16320
	UINT32 y_coefa\[8\]; 				///< Y channel noise model parameter: slope of line, 0~48, Regard 16 as slope 1.0
	UINT32 y_coefb\[8\]; 				///< Y channel noise model parameter: intercept of line, 0 ~16320
	UINT32 y_std\[8\]; 				///< Y channel noise model parameter: noise standard deviation, 0 ~16320
	UINT32 cb_mean\[8\]; 				///< Cb channel noise model parameter: noise mean, 0 ~6375
	UINT32 cb_std\[8\]; 				///< Cb channel nosie model parameter: noise standard deviation, 0 ~6375
	UINT32 cr_mean\[8\]; 				///< Cr channel noise model parameter: noise mean, 0 ~6375
	UINT32 cr_std\[8\]; 				///< Cr channel nosie model parameter: noise standard deviation, 0 ~6375
	UINT32 tmnr_fcs_en;  	        ///< TMNR False Color Supression enable, **chroma_dn_en shoulde be 1
	UINT32 tmnr_fcs_str;   			///< TMNR_False Color Supression strength
	UINT32 tmnr_fcs_th;         	///< TMNR False Color Supression threshold
	//new in nt98321
	UINT8 dithering_en;   			///< source dithering switch. 0~1. default  0
	UINT8 dithering_bit_y;			///< Y-channel dithering range. 0~3. default 2
	UINT8 dithering_bit_u;			///< U-channel dithering range. 0~3. default 1
	UINT8 dithering_bit_v;			///< V-channel dithering range. 0~3. default 1
	UINT8 err_compensate;			///< err compensation method option. 0~1. default 1
} VENDOR_VIDEO_PARAM_TMNR_EXT;
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image050.png)**

5 Sharpen (SHP)
---------------

This is texture enhancement module.

### 5.1 Overview

This algorithm adopts inverse gamma information and after gamma information to perform texture enhancement, respectively, to improve the enhancement strength not smooth problem of the bright/dark region. Besides, it adopts 3x3 and 5x5 filter to enhance thin edge and thick edge, repectively, to take care of the detail and contrast of image. Calculating “Edge Weight” to determine this is detail region or flat region(thinner edge) and automatically adjusting weighting of detail enhancement result and flat region enhancement result to take care of texture enhancement and avoid noise enhancement. The “Halo clip” is used to control the overshootong phenomenon caused by edge enhancement.

The major flow please refer to the following figure:

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image051.png)

Parameter Description

Table 5?1 SHP Parameter List

|     |     |     |     |
| --- | --- | --- | --- |
| **Parameter** | **Range** | **Def** | **Description** |
| **_sharpen_en_** | 0~1 | 0   | Edge enhance ON/OFF |
| **_edge\_weight\_src_sel_** | 0~1 | 0   | Select the image source to calculate “Edge Weight ”.<br><br>0: after gamma, 1: inverse gamma.<br><br>Please refer to description. |
| **_edge\_weight\_th_** | 0~255 | 2   | Threshold for calculating “Edge Weight”, those smaller than threshold will be considered as flat region, and the output all adopt flat region enhancement result. |
| **_edge\_weight\_gain_** | 0~255 | 175 | Adjust the weighting of detail enhancement result and flat region(thin edge) enhancement result. Based on the setting of “noise\_level+noise\_curve” to adjust EdgeWeight for different pixel brightness. The larger the Edge Weight, the larger weighting of detail enhancement result, repersenting the edge enhance is more stronger(more noise). In the contrast, the smaller the edge weight, the larger weighting of flat region enhancement result, representing the edge enhancement is less stronger. |
| **_noise_level_** | 0~255 | 25  | Please refer to advance description. |
| **_noise_curve\[17\]_** | 0~255 | {50, 50, 50, 48, 47, 44, 39, 38, 37, 36, 35, 35, 35, 35, 35, 35, 35} | Please refer to advance description. |
| **_blend\_inv\_gamma_** | 0~128 | 64  | The blending weight of inverse gamma edge enhancement result and after gamma edge enhancement result. This parameter is equal to adjust the ratio of edge enhancement between bright region and dark region, let the edge enhancement level of bright region and dark region is more even. The larger the value, the stronger strength of bright region enhancement, but the weaker strength of dark region enhancement. |
| **_edge\_sharp\_str1_** | 0~255 | 25  | Adjust the strength of thin edge enhancement |
| **_edge\_sharp\_str2_** | 0~255 | 10  | Adjust the strength of thick edge enhancement |
| **_flat\_sharp\_str_** | 0~255 | 0   | Adjust the strength of flat region(thin detail) enhancement. |
| **_coring_th_** | 0~255 | 0   | Threshold for determing whether to perform enhancement. For those edge value smaller than threshold, they will not perform edge enhancement to avoid enhancing noise. |
| **_bright\_halo\_clip_** | 0~128 | 32  | Remove bright halo edge caused by edge enhancement. The smaller the “bright\_halo\_clip”, the less bright halo edge, but the sharpness might be decreased. |
| **_dark\_halo\_clip_** | 0~128 | 96  | Remove dark halo edge caused by edge enhancement. The smaller the “dark\_halo\_clip”, the less dark halo edge, but the sharpness might be decreased. |

**Advance description**

l **_noise\_level, noise\_curve\[17\]:_**

noise\_level = noise\_level + NoiseofPixel, wherein the NoiseofPixel is the y-axis of noise_curve.

The noise\_curve may depend on the pixel brightness to set the noise size, respectively. Normally, human eyes are less sensitive to the noise in high bright region; thus, it can set small value to increase the edge enhancement strength to enhance detail. It is recommend to use the following default value. If user want to adjust the noise size at all Y range(0-255), it just needs to adjust noise\_level.

Noise

?

  

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image052.png)

Default value:

**_edge\_weight\_src_sel_** =0

noise_curve\[17\] ={50,50,50,48,47,44,39,38,37,36,35,35,35,35,35,35,35}

e More strengthen on detail in bright region to avoid enhancing noise.

**_edge\_weight\_src_sel_** =1

noise_curve\[17\] = {0, 38, 46, 51, 54, 57, 59, 61, 62, 62, 62, 62, 62, 62, 62, 62, 62}

e More strengthen on detail in dark region to enhance thin detail, but the noise in dark region will be enhanced, either.

### 5.2 Setting Interface

#### 5.2.1 Proc

###### l /proc/videograph/vpe/sharpen/dump_info

**\[Description\]**

Read all Sharpen parameters of the current camera channel.

**\[Command\]**

**Write : Not support.**

Read : cat /proc/videograph/vpe/sharpen/dump_info

**![文字方塊: Current channel = <ch_no>
edge_weight_src_sel = edge_weight_src_sel
edge_weight_th = edge_weight_th
edge_weight_gain = edge_weight_gain
noise_level = noise_level
noise_curve\[17\] = noise_curve\[0\] ………. noise_curve\[16\]
blend_inv_gamma = blend_inv_gamma
edge_sharp_str1 = edge_sharp_str1
edge_sharp_str2 = edge_sharp_str2
flat_sharp_str = flat_sharp_str
coring_th = coring_th
bright_halo_clip = bright_halo_clip
dark_halo_clip = dark_halo_clip
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/sharp_en

**\[Description\]**

Read or write the enable status of the cuurent channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[ sharp\_en (0~1) \] > /proc/videograph/vpe/sharpen/sharp\_en | **sharpen_en** |

**Read :**

**cat /proc/videograph/vpe/sharpen/shp_en**

**Output :**

**![文字方塊: Command : 
echo \[ sharp_en (0~1) \] > /proc/videograph/vpe/sharpen/sharp_en ===============================================================

sharpen_en = sharpen_en
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/edge\_weight\_src_sel

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[src\_sel (0 ~ 1) \] > /proc/videograph/vpe/sharpen/edge\_weight\_src\_sel | **edge\_weight\_src_sel** |

**Read :**

cat /proc/videograph/vpe/sharpen/edge\_weight\_src_sel

**Output :**

**![文字方塊: Command : 
echo \[src_sel (0 ~ 1)\] > /proc/videograph/vpe/sharpen/edge_weight_src_sel ===============================================================

edge_weight_src_sel = edge_weight_src_sel
0: after gamma 1: before gamma
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/edge\_weigt\_gain

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[gain (0~255) \] > /proc/videograph/vpe/sharpen/edge\_weight\_gain | **_edge\_weight\_gain_** |

**Read :**

cat /proc/videograph/vpe/sharpen/edge\_weight\_gain

**Output :**

**![文字方塊: Command : 
echo \[gain (0~255)\] > /proc/videograph/vpe/sharpen/edge_weight_gain ===============================================================

edge_weight_gain = edge_weight_gain
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/edge\_weight\_th

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[th (0~255) \] > /proc/videograph/vpe/sharpen/edge\_weight\_th | **_edge\_weight\_th_** |

**Read :**

cat /proc/videograph/vpe/sharpen/edge\_weight\_th

**Output :**

**![文字方塊: Command : 
echo \[th (0~255)\] > /proc/videograph/vpe/sharpen/edge_weight_th ===============================================================

edge_weight_th = edge_weight_th
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/blend\_inv\_gamma

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[th (0~128) \] > /proc/videograph/vpe/sharpen/blend\_inv\_gamma | **_blend\_inv\_gamma_** |

**Read :**

cat /proc/videograph/vpe/sharpen/blend\_inv\_gamma

**Output :**

**![文字方塊: Command : 
echo \[th (0~128) > /proc/videograph/vpe/sharpen/blend_inv_gamma ===============================================================

blend_inv_gamma = blend_inv_gamma
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/edge\_sharp\_str

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[str1 (0~255)\] \[str2 (0~255)\] > /proc/videograph/vpe/sharpen/edge\_sharp\_str | **_edge\_sharp\_str1_**<br><br>**_edge\_sharp\_str2_** |

**Read :**

cat /proc/videograph/vpe/sharpen/edge\_sharp\_str

**Output :**

**![文字方塊: Command : 
echo \[str1 (0~255)\] \[str2 (0~255)\] > /proc/videograph/vpe/sharpen/edge_sharp_str ===============================================================
sharp_str1 = edge_sharp_str1
sharp_str2 = edge_sharp_str2
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/flat\_sharp\_str

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[str (0~255)\] > /proc/videograph/vpe/sharpen/flat\_sharp\_str | **_flat\_sharp\_str_** |

**Read :**

cat /proc/videograph/vpe/sharpen/flat\_sharp\_str

**Output :**

**![文字方塊: Command : 
echo \[str (0~255)\] > /proc/videograph/vpe/sharpen/flat_sharp_str ===============================================================

flat_sharp_str = flat_sharp_str
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/coring_th

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[coring\_th (0~255)\] > /proc/videograph/vpe/sharpen/coring\_th | **_coring_th_** |

**Read :**

cat /proc/videograph/vpe/sharpen/coring_th

**Output :**

**![文字方塊: Command : 
echo \[coring_th (0~255)\] > /proc/videograph/vpe/sharpen/coring_th ===============================================================

coring_th = coring_th
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/halo_clip

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[bright\_clip (0~128)\] \[dark\_clip(0~128)\] > /proc/videograph/vpe/sharpen/halo_clip | **_bright\_halo\_clip_**<br><br>**_drak\_halo\_clip_** |

**Read :**

cat /proc/videograph/vpe/sharpen/halo_clip

**Output :**

**![文字方塊: Command : 
echo \[bright_clip (0~128)\] \[dark_clip(0~128)\] > /proc/videograph/vpe/sharpen/halo_clip ===============================================================

Bright_halo_clip = bright_halo_clip
Dark_halo_clip = dark_halo_clip
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/sharpen/noise_curve

**\[Description\]**

Read or write the sharpen parameter of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[noise\_curve\[0\] (0~255)\]…. \[noise\_curve \[16\] (0~255)\] > /proc/videograph/vpe/sharpen/noise_curve | **_noise_curve\[17\]_** |

**Read :**

cat /proc/videograph/vpe/sharpen/noise_curve

**Output :**

**![文字方塊: Command : 
echo \[noise_curve\[0\] (0~255)\]…. \[noise_curve \[16\] (0~255)\] > /proc/videograph/vpe/sharpen/noise_curve ===============================================================

noise_curve = noise_curve\[0\] ……….noise_curve\[16\]
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

#### 5.2.2 Vendor API

**\[Description\]**

Get and set the sharpen parameters corresponding to current path_id.

**\[Command\]**

??????? **Get****：**

HD\_RESULT vendor\_video\_get(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_SHARP, VENDOR\_VIDEO\_PARAM_SHARP  *p_param);

??????? **Set****：**

HD\_RESULT vendor\_video\_set(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_SHARP, VENDOR\_VIDEO\_PARAM_SHARP *p_param);

**\[****定義****\]**

**![文字方塊: typedef struct _VENDOR_VIDEO_PARAM_SHARP {
	UINT32 sharp_en;  			///< Sharpness ON/OFF
	UINT32 edge_weight_src_sel; ///< Select source of edge weight calculation, 0~1
	UINT32 edge_weight_th; 		///< Edge weight coring threshold, 0~255
	UINT32 edge_weight_gain; 	///< Edge weight gain, 0~255
	UINT32 noise_level; 		///< Noise Level, 0~255
	UINT32 noise_curve\[17\]; 	///< 17 control points of noise modulation curve, 0~255
	UINT32 blend_inv_gamma; 	///< Blending ratio of HPF results, 0~128
	UINT32 edge_sharp_str1; 	///< Sharpen strength1 of edge region, 0~255
	UINT32 edge_sharp_str2; 	///< Sharpen strength2 of edge region, 0~255
	UINT32 flat_sharp_str; 		///< Sharpen strength of flat region,0~255
	UINT32 coring_th; 			///< Coring threshold, 0~255
	UINT32 bright_halo_clip; 	///< Bright halo clip ratio, 0~255
	UINT32 dark_halo_clip; 		///< Dark halo clip ratio, 0~255
} VENDOR_VIDEO_PARAM_SHARP;
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image054.png)**

6 Edge Smoothing (ES)
---------------------

This module is edge smoothing. The main function is to eliminate aliasing in the picture to improve the smoothness of the picture.

### 6.1 Overview

The characteristics of this algorithm are to effectively smooth the edges of the input image, correct the jaggedness in the edge area of the input image, and avoid the Sharpen module to enhance the degree of jaggedness in the image edge again. The algorithm divides the input image into edge area and detail area, calculates the direction of the edge on the edge area, and then performs LPF convolution adaptively along the edge direction to smooth the edge of the image. The Edge Mask can be adjusted to avoid high-frequency areas being blurred due to smoothing.

Please refer to the following figure for the main process:

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image055.png)

### 6.2 Parameter Description

Table 6?1 ES Parameter List

|     |     |     |     |
| --- | --- | --- | --- |
| **Parameter** | **Range** | **Def** | **Description** |
| **_edge\_smooth\_en_** | 0~1 | 0   | Edge smooth enable |
| **_edge\_smooth\_y\_edeng\_th_lo_** | 0~255 | 10  | Adjust the strength threshold of detail areas in the picture<br><br>Please refer to the advanced instructions |
| **_edge\_smooth\_y\_edeng\_th_hi_** | 0~255 | 70  | Adjust the strength threshold of the edge area in the picture<br><br>Please refer to the advanced instructions |
| **_edge\_smooth\_y\_ew\_lo_** | 0~255 | 2   | Adjust the smoothing strength weight of detail areas in the picture<br><br>Please refer to the advanced instructions |
| **_edge\_smooth\_y\_ew\_hi_** | 0~255 | 32  | Adjust the suppression threshold for the smoothing of high-frequency areas in the picture. The larger the value, the easier it is to determine and smooth the high-frequency area. Therefore, the larger the value, the smoother the high-frequency area, and the smaller the value, the clearer the high-frequency area |
| **_edge\_smooth\_y\_edi\_th_** | 0~63 | 31  | Suppresses the strength of smoothing in the high-frequency region. The larger the value, the stronger the smoothing in the high-frequency region. |
| **_edge\_smooth\_y\_ds\_str_** | 0~7 | 5   | Adjust the strength of the smoothing filter in the picture. The larger the value, the stronger the smoothing degree. |

**Advance description:**

l **_edge\_smooth\_y\_edeng\_th_lo_****_,_** **_edge\_smooth\_y\_edeng\_th\_hi, edge\_smooth\_y\_ew\_lo, edge\_smooth\_y\_ew_hi_****_:_** The strength of edge smooth is controlled by the edge energy intensity of the input image, where edge\_smooth\_y\_edeng\_th\_hi and edge\_smooth\_y\_edeng\_th\_lo are the ranges that set the edge area and the detail area, and edge\_smooth\_y\_ew\_hi and edge\_smooth\_y\_ew\_lo set the smoothness strength of the edge area and detail area. The larger the number, the stronger of the smoothness.

The relationship between the edge area and the detail area is a continuous linear change, and the corresponding relationship is shown in the following figure:

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image056.png)

### 6.3 Setting Interface

#### 6.3.1 Proc

###### l /proc/videograph/vpe/es/param

**\[Description\]**

Read all edge smoothing parameters of the current camera channel.

**\[Command\]**

**Write : Not support.**

Read : cat /proc/videograph/vpe/es/param

**![文字方塊: fd(0x00000000)
edge_smooth_en              = edge_smooth_en           
edge_smooth_out_sel         = edge_smooth_out_sel      
edge_smooth_y_edeng_th_lo   = edge_smooth_y_edeng_th_lo
edge_smooth_y_edeng_th_hi   = edge_smooth_y_edeng_th_hi
edge_smooth_y_ew_lo         = edge_smooth_y_ew_lo      
edge_smooth_y_ew_hi         = edge_smooth_y_ew_hi      
edge_smooth_y_edi_th        = edge_smooth_y_edi_th     
edge_smooth_y_ds_str         = edge_smooth_y_ds_str
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png)**

###### l /proc/videograph/vpe/es/edge\_smooth\_en

**\[Description\]**

Set the edge smooth switch of the current camera channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[edge\_smooth\_en (0~1)\] > /proc/videograph/vpe/es/edge\_smooth\_en | **edge\_smooth\_en** |

###### l /proc/videograph/vpe/es/edge\_smooth\_out_sel

**\[Description\]**

Set the edge smooth debugging switch of the current camera channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[edge\_smooth\_out\_sel (0~1)\] > /proc/videograph/vpe/es/edge\_smooth\_out\_sel | **edge\_smooth\_out_sel** |

**Read :**

cat /proc/videograph/vpe/es/edge\_smooth\_out_sel

**Output :**

**![文字方塊: Command : 
echo \[edge_smooth_out_sel (0~1)\] > /proc/videograph/vpe/es/edge_smooth_out_sel
===============================================================
edge_smooth_out_sel  = edge_smooth_out_sel
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png)**

###### l /proc/videograph/vpe/es/edge\_smooth\_th

**\[Description\]**

Set the edge smooth related threshold of the current camera channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[y\_edeng\_th\_lo (0~255)\] \[y\_edeng\_th\_hi (0~255)\] \[y\_ew\_lo (0~255)\] \[y\_ew\_hi (0~255)\] > /proc/videograph/vpe/es/edge\_smooth\_th | **edge\_smooth\_y\_edeng\_th_l**<br><br>**edge\_smooth\_y\_edeng\_th_hi**<br><br>**edge\_smooth\_y\_ew\_lo**<br><br>**edge\_smooth\_y\_ew\_hi** |

**Read :**

cat /proc/videograph/vpe/es/edge\_smooth\_th

**Output :**

**![文字方塊: Command : 
echo \[y_edeng_th_lo (0~255)\] \[y_edeng_th_hi (0~255)\] \[y_ew_lo (0~255)\] \[y_ew_hi (0~255)\] > /proc/videograph/vpe/es/edge_smooth_th ===============================================================
y_edeng_th_l = edge_smooth_y_edeng_th_l
y_edeng_th_hi = edge_smooth_y_edeng_th_hi
y_ew_lo = edge_smooth_y_ew_lo
y_ew_hi = edge_smooth_y_ew_hi
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png)**

###### l /proc/videograph/vpe/es/edge\_smooth\_y\_edi\_th

**\[Description\]**

Set the edge smooth mask related parameters of the current camera channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[edge\_smooth\_y\_edi\_th (0~63)\] > /proc/videograph/vpe/es/edge\_smooth\_y\_edi\_th | **edge\_smooth\_y\_edi\_th** |

**Read :**

cat /proc/videograph/vpe/es/edge\_smooth\_y\_edi\_th

**Output :**

**![文字方塊: Command : 
echo \[edge_smooth_y_edi_th (0~63)\] > /proc/videograph/vpe/es/edge_smooth_ds_str
===============================================================
edge_smooth_y_edi_th = edge_smooth_y_edi_th
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png)**

###### l /proc/videograph/vpe/es/edge\_smooth\_y\_ds\_str

**\[Description\]**

Sets the filter strength of the edge smooth of the current camera channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[edge\_smooth\_y\_ds\_str (0~7)\] > /proc/videograph/vpe/es/edge\_smooth\_y\_ds\_str | **edge\_smooth\_y\_ds\_str** |

**Read :**

cat /proc/videograph/vpe/es/edge\_smooth\_y\_ds\_str

**Output :**

**![文字方塊: Command : 
echo \[edge_smooth_y_ds_str (0~7)\] > /proc/videograph/vpe/es/edge_smooth_y_ds_str
===============================================================
edge_smooth_y_ds_str = edge_smooth_y_ds_str
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

#### 6.3.2 Vendor API

**\[Description\]**

Get and set the edge smooth parameters corresponding to current path_id.

**\[Command\]**

 **Get****：**

HD\_RESULT vendor\_video\_get(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_EDGE_SMOOTH, VENDOR\_VIDEO\_PARAM_SHARP  *p_param);

??????? **Set****：**

HD\_RESULT vendor\_video\_set(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_EDGE_SMOOTH, VENDOR\_VIDEO\_PARAM_SHARP *p_param);

**\[Definition\]**

**![文字方塊: typedef struct _VENDOR_VIDEO_PARAM_EDGE_SMOOTH {
	UINT8 edge_smooth_en; 			// Edge smooth enable, ON/OFF
	UINT8 edge_smooth_y_edeng_th_lo;	// luma layer edge energy low threshold, 0~255
	UINT8 edge_smooth_y_edeng_th_hi;	// luma layer edge energy high threshold, 0~255
	UINT8 edge_smooth_y_ew_lo;		// luma layer edge weighting curve low value, 0~32
	UINT8 edge_smooth_y_ew_hi;		// luma layer edge weighting curve high value, 0~32
	UINT8 edge_smooth_y_edi_th;		// luma layer edge mask threshold, 0~63
	UINT8 edge_smooth_y_ds_str;       // luma layer edge directed smoothing filter strength, 0 ~ 7
} VENDOR_VIDEO_PARAM_EDGE_SMOOTH;
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image054.png)**

7 Scaling (SCA)
---------------

Inupt/Output low pass filter process with different resolution. The recommend maximum scaling down ratio is 8, and the recommend maximum scaling up ratio is 8.

### 7.1 Overview

This is image scaling module, the major concept is interpolation and smooth process.

### 7.2 Parameter Description

Table 7?1 SCA Parameter List

|     |     |     |     |
| --- | --- | --- | --- |
| **Parameter** | **Range** | **Def** | **Description** |
| **_sca\_y\_luma\_algo\_en_** | 0~3 | 0   | Algorithm select for vertical luma scaler.<br><br>0: judge by HW algorithm<br><br>1: select the nearest point on the left side<br><br>2: select the left side point and perform low pass filter process<br><br>3: the same as option 0<br><br>It is recommend to set 0. |
| **_sca\_x\_luma\_algo\_en_** | 0~3 | 0   | Algorithm select for horizontal luma scaler.<br><br>0: judge by HW algorithm<br><br>1: select the nearest point on the left side<br><br>2: select the left side point and perform low pass filter process<br><br>3: the same as option 0<br><br>It is recommend to set 0. |
| **_sca\_y\_chroma\_algo\_en_** | 0~3 | 0   | Algorithm select for vertical chroma scaler.<br><br>0: judge by HW algorithm<br><br>1: select the nearest point on the left side<br><br>2: bilinear interpolation<br><br>3: average<br><br>It is recommend to set 0. |
| **_sca\_x\_chroma\_algo\_en_** | 0~3 | 0   | Algorithm select for horizontal chroma scaler.<br><br>0: judge by HW algorithm<br><br>1: select the nearest point on the left side<br><br>2: bilinear interpolation<br><br>3: average<br><br>It is recommend to set 0. |
| **_sca\_map\_sel_** | 0~1 | 0   | Select scaler source mapping format.<br><br>0: without 0.5 pixel distance shift(start from the 0th pixel of image image)<br><br>1: with 0.5 pixel distance shift(start from the 0.5th pixel of image image)<br><br>If set to 1, when the size of input image and output image is the same or the size is multiple of 2, the scaling performance of output image will similar to perform low pass filter.<br><br>It is recommend to set 0. |
| **_sca\_ceffH\_0~3_** | -128~127 | \[0, 0, 0, 64\] | LPF coefficient in horizontal direction.<br><br>Please refer to advance description.<br><br>※The software limit range is between -128~127, to reduce memory usage. |
| **_sca\_ceffv\_0~3_** | -128~127 | \[0, 0, 0, 64\] | LPF coefficient in vertical direction.<br><br>Please refer to advance description.<br><br>※The software limit range is between -128~127, to reduce memory usage. |
| **_des_drt_** | 0, 2,3 | 0   | YUV domain transform<br><br>0: bypass<br><br>2: PC level to TV level (Y: 16~235 / C:16~240)<br><br>3: TV level to PC level? (Y: 0~235 C:0~255)<br><br>255: decide by job parameter of AP rather than driver  <br>(default value is 255, other settings are used for debug) |

**Advance description:**

l **_sca\_ceffH\_0~3, sca\_ceffV\_0~3:_** LPF coefficients in horizontal direction and vertical direction. User can adjust LPF coefficients to fine tune sawtooth phenomenon in oblique line caused by scaling.

?Table 7?2 Scaler Low pass filter default parameter list

|     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **Scaling Ratio (R)** | **HCoef0** | **HCoef1** | **HCoef2** | **HCoef3** | **VCoef0** | **VCoef1** | **VCoef2** | **VCoef3** |
| **≧** **1x** | 0   | 0   | 0   | 64  | 0   | 0   | 0   | 64  |
| **1 < R** **≦** **1.25x** | 0   | 0   | 3   | 58  | 0   | 0   | 3   | 58  |
| **1.25 < R** **≦** **1.5x** | 0   | 0   | 7   | 50  | 0   | 0   | 7   | 50  |
| **1.5 < R** **≦** **1.75x** | 0   | 0   | 11  | 42  | 0   | 0   | 11  | 42  |
| **1.75 < R** **≦** **2x** | 0   | 1   | 13  | 36  | 0   | 1   | 13  | 36  |
| **2 < R** **≦** **2.25x** | 0   | 1   | 15  | 32  | 0   | 1   | 15  | 32  |
| **2.25 < R** **≦** **2.5x** | 0   | 2   | 15  | 30  | 0   | 2   | 15  | 30  |
| **2.5 < R** **≦** **2.75x** | 0   | 3   | 15  | 28  | 0   | 3   | 15  | 28  |
| **2.75 < R** **≦** **3x** | 0   | 4   | 15  | 26  | 0   | 4   | 15  | 26  |
| **3 < R** **≦** **3.25x** | 1   | 4   | 15  | 24  | 1   | 4   | 15  | 24  |
| **3.25 < R** **≦** **3.5x** | 1   | 5   | 15  | 22  | 1   | 5   | 15  | 22  |
| **3.5 < R** **≦** **3.75x** | 2   | 7   | 14  | 18  | 2   | 7   | 14  | 18  |
| **3.75 < R** **≦** **4x** | 3   | 8   | 13  | 16  | 3   | 8   | 13  | 16  |
| **4 < R** **≦** **5x** | 4   | 8   | 13  | 14  | 4   | 8   | 13  | 14  |
| **5 < R** **≦** **6x** | 4   | 9   | 12  | 14  | 4   | 9   | 12  | 14  |
| **6x < R** **≦** **7x** | 6   | 9   | 11  | 12  | 6   | 9   | 11  | 12  |
| **7x < R** | 6   | 9   | 11  | 12  | 6   | 9   | 11  | 12  |

### 7.3 Setting Interface

#### 7.3.1 Proc

###### l /proc/videograph/vpe/sca/param

**\[Description\]**

Read all SCA parameters of the cuurent scaling ratio

**\[Command\]**

**Write : Not support.**

Read : cat /proc/videograph/vpe/sca/param

**![文字方塊: fd(0x00000000)
sca_y_luma_algo_en = 0
sca_x_luma_algo_en = 0
sca_y_chroma_algo_en = 0
sca_x_chroma_algo_en = 0
sca_map_sel = 0
sca_1x_param = {
0, 0, 0, 64,
0, 0, 0, 64
}

sca_1.25x_param = {
0, 0, 0, 64,
0, 0, 0, 64
}
…
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png)**

###### l /proc/videograph/vpe/sca/ctrl_param

**\[Description\]**

Set SCA controlling parameter for specific ratio.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[sca\_luma\_algo (0~3)\] \[sca\_chroma\_algo (0~3)\] \[sca\_map\_sel (0~1)\] > /proc/videograph/vpe/sca/ctrl_param | index: Target ratio<br><br>The command “sca\_luma\_algo” set parameters “sca\_y\_luma\_algo\_en” and “sca\_x\_luma\_algo\_en” at the same time.<br><br>The command “sca\_chroma\_algo” set parameters<br><br>“sca\_y\_chroma\_algo\_en” and<br><br>“sca\_x\_chroma\_algo\_en” at the same time.<br><br>The command “sca\_map\_sel” set  “sca\_map\_sel” parameter. |

Read : Not support

###### l /proc/videograph/vpe/sca/lpf_param

**\[Description\]**

Set SCA low pass filter parameter for specific ratio.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[index (0~16)\] \[coeffH\[0\]\] \[coeffH\[1\]\] \[coeffH\[2\]\] \]coeffH\[3\]\] \[coeffV\[0\]\] \[coeffV\[1\]\] \[coeffV\[2\]\] \[coeffV\[3\]\] (-128 ~ 127) >? /proc/videograph/vpe/sca/lpf_param | index: Target ratio<br><br>coeffH : sca_ceffH\[4\]<br><br>coeffV: sca_ceffV\[4\]<br><br>※The software limit range is between -128~127, to reduce memory usage. |

Read : Not support

###### l /proc/videograph/vpe/sca/yuv_range

**\[Description\]**

Read or write YUV range of SCA at each one of the channel.

**※****Parameter can be set by put job of AP depends on channel requests, it is not recommend to be set by this proc command or ioctl to avoid conflicts. This command is used for debugging.**

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[fd range\] > /proc/videograph/vpe/sca /yuv_range<br><br>yuv_range: 0, 2, 3, 255 (disable)<br><br>※disable represent AP directly control parameters | **des_drt** |

**Read :**

cat /proc/videograph/vpe/sca/yuv_range

**Output :**

**![文字方塊: Command : 
echo < fd range >(0:bypass, 2:TV, 3:PC, 255:diable)
===============================================================

fd(0x40000000) yuv range = 0
fd(0x40000001) yuv range = 0
fd(0x40000002) yuv range = 0
fd(0x40000003) yuv range = 0
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

#### 7.3.2 Vendor API

**\[Description\]**

Get and set the scaling parameters corresponding to current path_id.

**\[Command\]**

??????? **Get****：**

HD\_RESULT vendor\_video\_get(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_SCA, VENDOR\_VIDEO\_PARAM\_SCA\_SET  *p_param);

??????? **Set****：**

HD\_RESULT vendor\_video\_set(HD\_PATH\_ID path\_id, VENDOR\_VIDEO\_SCA, VENDOR\_VIDEO\_PARAM\_SCA\_SET *p_param);

**\[Definition\]**

**![文字方塊: typedef struct _VENDOR_VIDEO_PARMA_SCA_CTRL {
	INT32 sca_ceffH\[4\]; 				///< LPF coefficient in horizontal direction
	INT32 sca_ceffV\[4\]; 				///< LPF coefficient in vertical direction
} VENDOR_VIDEO_PARMA_SCA_CTRL;

typedef struct _VENDOR_VIDEO_PARAM_SCA_SET {
	UINT8 sca_y_luma_algo_en; 			///< Algorithm select for vertical luma scaler
	UINT8 sca_x_luma_algo_en; 			///< Algorithm select for horizontal luma scaler
	UINT8 sca_y_chroma_algo_en; 		///< Algorithm select for vertical chroma scaler
	UINT8 sca_x_chroma_algo_en; 		///< Algorithm select for horizontal chroma scaler
	UINT8 sca_map_sel; 					///< Scaler source mapping format select
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_1000x_param;  ///< scaling parameter for scaling ratio 1.00x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_1250x_param;  ///< scaling parameter for scaling ratio 1.25x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_1500x_param;  ///< scaling parameter for scaling ratio 1.50x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_1750x_param;  ///< scaling parameter for scaling ratio 1.75x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_2000x_param;  ///< scaling parameter for scaling ratio 2.00x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_2250x_param;  ///< scaling parameter for scaling ratio 2.25x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_2500x_param;  ///< scaling parameter for scaling ratio 2.50x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_2750x_param;  ///< scaling parameter for scaling ratio 2.75x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_3000x_param;  ///< scaling parameter for scaling ratio 3.00x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_3250x_param;  ///< scaling parameter for scaling ratio 3.25x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_3500x_param;  ///< scaling parameter for scaling ratio 3.50x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_3750x_param;  ///< scaling parameter for scaling ratio 3.75x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_4000x_param;  ///< scaling parameter for scaling ratio 4.00x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_5000x_param;  ///< scaling parameter for scaling ratio 5.00x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_6000x_param;  ///< scaling parameter for scaling ratio 6.00x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_7000x_param;  ///< scaling parameter for scaling ratio 7.00x
	VENDOR_VIDEO_PARMA_SCA_CTRL sca_8000x_param;  ///< scaling parameter for scaling ratio 8.00x
} VENDOR_VIDEO_PARAM_SCA_SET;
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image058.png)**

8 Distortion Correction Engine (DCE)
------------------------------------

### 8.1 Overview

This is lens distortion calibration module, it can perform calibration on wide-angle lens and fish-eye lens.

### 8.2 DCE Parameter Description

Table 8?1 DCE Parameter List

|     |     |     |     |
| --- | --- | --- | --- |
| **Parameter** | **Range** | **Def** | **Description** |
| **_dce_mode_** | 0~1 | 0   | Select distortion function<br><br>0: GDC lens calibration<br><br>1: 2DLUT self-define XY coordinate distortion |
| **_lut2d_sz_** | 0~5 | 0   | Size selection of 2D look-up table. The larger the size, the more precision to describe distortion.<br><br>0: 9x9<br><br>3: 65x65<br><br>4: 129x129<br><br>5: 257x257 |
| **_lsb_rand_** | 0~1 | 0   | LSB 2 bit random generation for internal 10 bit->8 bit image.<br><br>0: fixed fill 0<br><br>1: random generate 0~3 |
| **_fovbound_** | 0~1 | 0   | FOV boundary process method selection.<br><br>When the distortion result can not fill the total output image, select different way to proceed the exceed range.<br><br>0: Replace out of boundary pixels with duplicate nearest pixel<br><br>1: Replace out of boundary pixels with bound pixels |
| **_boundy_** | 0~1023 | 0   | Bound value for Y component(u8.2) |
| **_boundu_** | 0~1023 | 0   | Bound value for U component(u8.2) |
| **_boundv_** | 0~1023 | 0   | Bound value for V component(u8.2) |
| **_cent\_x\_s_** | 213-1 | 0   | Define lens center of x-axis.<br><br>It is recommend to set width/2. |
| **_cent\_y\_s_** | 213-1 | 0   | Define lens center of y-axis.<br><br>It is recommend to set height/2. |
| **_xdist_** | 0~4095 | 0   | X input distance factor, for oval shape modeling.<br><br>It is recommend to set 4095, which is suitable for most situation. |
| **_ydist_** | 0~4095 | 0   | Y input distance factor, for oval shape modeling.<br><br>It is recommend to set 4095, which is suitable for most situation. |
| **_geo_lut_** | 0~65535 | 0   | The GEO deformation gain table, a total of 65 points, indicates the magnification of each pixel in the image at a different distance from the deformation center (magnification = 65535 * input radius / output radius), the gainbase is 65535, please refer to Note 2 for the gain table example.<br><br>Value range：\[0, 65535\]。 |
| **_normfact_** | 0~255 | 128 | Radius normalization factor.<br><br>Normfact = 1 << (normbit + 7) / R2 |
| **_normbit_** | 0~31 | 31  | Radius normalization shift bit.<br><br>R2 = (width/2)2+(height/2)2<br><br>The total bit number of R2 is normbit.<br><br>Example: 9602+5402 = 1213200 (21 bits) |
| **_fovgain_** | 0~4095 | 0   | Adjust the scaling ratio of the final distortion coordinate to preserve FOV.<br><br>Scale down factor for FOV preservation.<br><br>Due to it will effect the calibration performance, it is recommend to set 1024. |
| **_hfact_** | 0 ~ 224 -1 | 0   | Horizontal scaling factor for 2DLut scaling up(u0.24).<br><br>((2DLUT horizontal pixel number – 1) << 24) / (width – 1) |
| **_vfact_** | 0 ~ 224 -1 | 0   | Vertical scaling factor for 2DLut scaling up(u0.24).<br><br>((2DLUT vertical pixel number – 1) << 24) / (height – 1) |
| **_xofs_i_** | 0~127 | 0   | 2DLut x offset, integer part.<br><br>It is recommend to set 0, if user need to adjust the DCE performance, user need to change the 2DLUT value. |
| **_xofs_f_** | 0~224-1 | 0   | 2DLut x offset, fraction part.<br><br>It is recommend to set 0, if user need to adjust the DCE performance, user need to change the 2DLUT value. |
| **_yofs_i_** | 0~127 | 0   | 2DLut y offset, integer part.<br><br>It is recommend to set 0, if user need to adjust the DCE performance, user need to change the 2DLUT value. |
| **_yofs_f_** | 0~224-1 | 0   | 2DLut y offset, fraction part.<br><br>It is recommend to set 0, if user need to adjust the DCE performance, user need to change the 2DLUT value. |

**\[Note 1\]**

Adjust geo\_fov\_gain, the left side is 1024, the right side is 1320, you can observe the increase in the field of view on the right side.

![new_fovgain1024](NT9833x_VPE_IQ_Tuning_Guide_en.files/image059.jpg)?![new_fovgain1320](NT9833x_VPE_IQ_Tuning_Guide_en.files/image060.jpg)

**\[Note 2\]**

The example of the GEO deformation gain table, from left to right, corresponds to the deformation amount from the center of the image to the edge. This parameter group indicates that the larger the deformation amount toward the edge is. This example is a barrel deformation correction.

R is the distance from the center of the image to each point. This distance can be understood as the radius of the circle.

Ri represents the radius of each point of the input (before correction) image.

Ro represents the radius of each point of the output (corrected) image.

RoMax represents the longest distance from the center of the output image to the four corners. If the center of the image falls at 1/2 of the width and height, the four corners are all equal, and they are the longest distances. ![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image061.png)![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image062.png)![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image063.png)

### 8.3 Setting Interface

#### 8.3.1 Proc

###### l /proc/videograph/vpe/dce/dump_info

**\[Description\]**

Read all DCE parameters at the current camera channel.

**\[Command\]**

**Write : Not support.**

Read : cat /proc/videograph/vpe/dce/dump_info

**![文字方塊: dce_en = 0
dce_mode = 1
lut2d_sz = 3
lut2d_vaddr = 0x0000000000000000
lut2d_paddr = 0x0
lsb_rand = 0
fovbound = 1
boundy = 512
boundu = 512
boundv = 512
cent_x_s = 720
cent_y_s = 720
xdist = 4095
ydist = 4095
normfact = 0
normbit = 0
fovgain = 1024
hfact = 745654
vfact = 745654
xofs_i = 0
xofs_f = 0
yofs_i = 0
yofs_f = 0
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 
geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0 geo_lut\[i\]=0

](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

###### l /proc/videograph/vpe/dce/ch_en

**\[Description\]**

Read or write the enable status of the current channel.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[ dc\_en 0~1 \] > /proc/videograph/vpe/dce/ch\_en | **dc_en** |

**Read :**

**cat /proc/videograph/vpe/dce/ch_en**

**Output :**

**![文字方塊: dc_en = 0](NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png)**

#### 8.3.2 Vendor API

**\[Description\]**

Get and set the dce parameters corresponding to current path_id.

**\[Command\]**

??????? Get：

HD\_RESULT vendor\_video\_get(HD\_PATH\_ID path\_id, VENDOR\_VIDEOPROC\_DEWARP\_INFO, VENDOR\_DEWARP\_INFO *p\_param);

??????? Set：

HD\_RESULT c(HD\_PATH\_ID path\_id, VENDOR_ VENDOR\_VIDEOPROC\_DEWARP\_INFO, VENDOR\_DEWARP\_INFO *p\_param);

**\[Define\]**

**![文字方塊: typedef struct _VENDOR_DEWARP_CTRL {
	BOOL dc_enable;
	BOOL dctg_enable;
} VENDOR_DEWARP_CTRL;

typedef enum _VENDOR_DEWARP_MODE {
	VENDOR_DEWARP_DEWARP_MODE_GDC	= 0,
	VENDOR_DEWARP_DEWARP_MODE_2DLUT	= 1,
	ENUM_DUMMY4WORD(VENDOR_DEWARP_DEWARP_MODE)
} VENDOR_DEWARP_MODE;

typedef struct _VENDOR_DEWARP_DGC_PARM {
	INT32 cent_x_s;		///< Lens center of x axis (signed)
	INT32 cent_y_s;    	///< Lens center of y axis (signed)
	UINT32 lens_r;		///< Radius of Lens
	UINT32 xdist;  		///< X input distance factor, for oval shape modeling
	UINT32 ydist;  		///< Y input distance factor, for oval shape modeling
	UINT8 normfact;  	///< Radius normalization factor (u1.7)
	UINT8 normbit;  	     ///< Radius normalization shift bit
	UINT16 geo_lut\[VENDOR_GEO_LUT_X\]; ///< GDC look-up table
} VENDOR_DEWARP_DGC_PARM;

typedef struct _VENDOR_DEWARP_2DLUT_PARM {
	UINT8 lut2d_sz;		///< Size selection of 2D look-up table, 0:9x9, 3:65x65
	UINT32 hfact;  		///< Horizontal scaling factor for 2DLut scaling up (u0.24)
	UINT32 vfact;  		///< Vertical scaling factor for 2DLut scaling up (u0.24)
	UINT8 xofs_i;  		///< 2DLUT x offset, integer part
	UINT32 xofs_f;     	///< 2DLUT x offset, fraction part
	UINT8 yofs_i;  		///< 2DLUT y offset, integer part
	UINT32 yofs_f;    	///< 2DLUT xy offset, fraction part
} VENDOR_DEWARP_2DLUT_PARM;

typedef struct _VENDOR_DEWARP_FOV_PARM {
	UINT8 fovbound;  	///< FOV boundary process method selection
	UINT16 boundy;   	///< Bound value for Y component (u8.2)
	UINT16 boundu;   	///< Bound value for U component (u8.2)
	UINT16 boundv;   	///< Bound value for V component (u8.2)
	UINT16 fovgain;   	///< Scale down factor for FOV preservation (u2.10)
} VENDOR_DEWARP_FOV_PARM;


](NT9833x_VPE_IQ_Tuning_Guide_en.files/image064.png)**

**![文字方塊: typedef struct _VENDOR_DEWARP_INFO {
	VENDOR_DEWARP_MODE mode;
	VENDOR_DEWARP_DGC_PARM dgc;
	VENDOR_DEWARP_2DLUT_PARM lut2d;
	VENDOR_DEWARP_FOV_PARM fov;
} VENDOR_DEWARP_INFO;

typedef struct _VENDOR_DEWARP_2DLUT_TABLE {
	UINT32 tbl\[VENDOR_GEO_LUT\];
} VENDOR_DEWARP_2DLUT_TABLE;

](NT9833x_VPE_IQ_Tuning_Guide_en.files/image058.png)**

9 DC Table Generator(DCTG)
--------------------------

### 9.1 Overview

For perspective projection application, in order to increase the convenience of usage, DCTG module let user to set the desired angle and size with an instinct way to generate DCTG parameters automatically. Whenever this function is enabled, manual set DCE 2D-LUT function will be invalid.

**\[Note\]**

??When using DCTG function, user needs to set two parameters enable, one is dc\_enable, the other is dctg\_en.

Please refer to the following description:

The “theta” is the top/bottom angle.

The “phi” is the rotate angle.

The “rot_y” is the rotate offset of (x, z) plane towards Y-axis.

The “rot_z” is the rotate offset of (x, y) plane towards Z-axis.

Generate LUT:

Define the rotate angle of FOV by phi\_st/phi\_ed, and then rotate to FOV location by rot_y.

Define the top/bottom angle of FOV by theta\_st/theta\_ed, and then rotate to FOV location by rot_z.

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image065.jpg)![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image066.jpg)

### 9.2 Parameter Description

Table 9?1 DCTG parameter list

|     |     |     |     |
| --- | --- | --- | --- |
| **Parameter** | **Range** | **Def** | **Description** |
| **_dctg_en_** | 0-1 | 0   | DCTG ON/OFF |
| **_mount_type_** | 0~1 | 0   | Camera mount type.<br><br>0: Ceiling mount<br><br>1: Floor mount |
| **_lut2d_sz_** | 0, 3 | 3   | Select size of 2D look-up table, this parameter must the same with DCE parameter.<br><br>0: 9x9<br><br>3: 65x65 |
| **_lens_r_** | 0~215-1 | 0   | Valid radius of fish-eye lens, the unit is pixel.<br><br>Please refer to advance description. |
| **_lens\_x\_st_** | 0~214-1 | 0   | The start x position of fish-eye lens at the source image, the unit is pixel. |
| **_lens\_y\_st_** | 0~214-1 | 0   | The start y position of fish-eye lens at the source image, the unit is pixel. |
| **_theta_st_** | -180 ~ 180<br><br>(-\*pi ~ \*pi) | 0   | FOV theta start radian. |
| **_theta_ed_** | -180 ~ 180<br><br>(-\*pi ~ \*pi) | 0   | FOV theta end radian.<br><br>theta\_end > theta\_st: normal image<br><br>theta\_end < theta\_st: flip image |
| **_phi_st_** | -360 ~ 360  <br>(-2\*pi ~ 2\*pi) | 0   | OV phi start radian. |
| **_phi_ed_** | -360 ~ 360  <br>(-2\*pi ~ 2\*pi) | 0   | FOV phi end radian.<br><br>(-2\*pi ~ 2\*pi)<br><br>phi\_end > theta\_st: normal image<br><br>phi\_end < theta\_st: flip image |
| **_rot_z_** | -360 ~ 360  <br>(-2\*pi ~ 2\*pi) | 0   | Z-axis rotate radian |
| **_rot_y_** | -360 ~ 360  <br>(-2\*pi ~ 2\*pi) | 0   | Y-zxis rotate radian. |

**Advance description:**

l **_lens_r:_** The valid radius of fish-eye device.

l **_lens\_x\_st :_** The start x position of fish-eye lens at the source image, the unit is pixel.

l **_lens\_y\_st :_**  The start y position of fish-eye lens at the source image, the unit is pixel.

![](NT9833x_VPE_IQ_Tuning_Guide_en.files/image067.png)

### 9.3 Setting Interface

#### 9.3.1 Proc

###### l /proc/videograph/vpe/dctg/dump_info

**\[Description\]**

Read all dctg parameters of the current channel.

**\[Command\]**

**Write : Not support.**

Read : cat /proc/videograph/vpe/dctg/dump_info

**![文字方塊: fd(0x00000000)
dctg_en = 0
mount_type = 1
lut2d_sz = 3
lens_r = 540
lens_x_st = 0(0)
lens_y_st = 0(0)
theta_st = 45(51471)
theda_ed = 90(102943)
phi_st = -40(-45753)
phi_ed = 40(45752)
rot_z = 0
rot_y = 0
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image068.png)**

###### l /proc/videograph/vpe/dctg/ch_en

**\[Description\]**

??????? Set dctg enable.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[dctg\_en\] > /proc/videograph/vpe/dctg/ch\_en | dctg_en: dctg enable |

**Read :**

cat /proc/videograph/vpe/dctg/ch_en

**Output :**

**![文字方塊: dctg_en = 1](NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png)**

###### l /proc/videograph/vpe/dctg/phi

**\[Description\]**

Set FOV phi start radian

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[st\] \[ed\] > /proc/videograph/vpe/dctg/phi | st: FOV phi start radian<br><br>ed : FOV phi end radian<br><br>※angle range: -360 ~ 360 |

**Read :**

cat /proc/videograph/vpe/dctg/phi

**Output :**

**![文字方塊: echo <st> <ed> (range -360~360)
phi_st degree= -40
phi_ed degree = 40
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png)**

###### l /proc/videograph/vpe/dctg/rot

**\[Description\]**

Set Z-axis and Y-zxis rotate radian.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **Target Parameter** |
| echo \[z\] \[y\] > /prc/videograph/vpe/dctg/rot | z: Z-axis rotate radian.<br><br>y: Y-zxis rotate radian<br><br>※angle range: -360 ~ 360 |

**Read :**

cat /proc/videograph/vpe/dctg/rot

**Output :**

![文字方塊: echo <z> <y> (range -360~360)
rot_z degree = 0
rot_y degree = 0
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png)

###### l /proc/videograph/vpe/dctg/theta

**\[Description\]**

Set FOV theta start radian.

**\[Command\]**

**Write :**

|     |     |
| --- | --- |
| **proc command** | **目標參數** |
| echo \[st\] \[ed\] > /prc/videograph/vpe/dctg/theta | st: FOV theta start radian.<br><br>ed : FOV theta end radian<br><br>※angle range: -180 ~ 180 |

**Read :**

cat /proc/videograph/vpe/dctg/theta

**Output :**

**![文字方塊: echo <st> <ed> (range -180~180)
theta_st degree = 45
theda_ed degree = 90
](NT9833x_VPE_IQ_Tuning_Guide_en.files/image069.png)**

#### 9.3.2 Vendor API

**\[Description\]**

Get and set the dctg parameters corresponding to current path_id.

**\[Command\]**

??????? Get：

HD\_RESULT vendor\_videoproc\_get(HD\_PATH\_ID path\_id, VENDOR\_VIDEOPROC\_DEWARP\_DCTG\_INFO, VENDOR\_DEWARP\_DCTG_INFO *p_param);

??????? Set：

HD\_RESULT vendor\_videoproc\_set(HD\_PATH\_ID path\_id, VENDOR\_VIDEOPROC\_DEWARP\_DCTG\_INFO, VENDOR\_DEWARP\_DCTG_INFO *p_param);

**\[Define\]**

**![文字方塊: typedef struct _VENDOR_DEWARP_CTRL {
	BOOL dc_enable;
	BOOL dctg_enable;
} VENDOR_DEWARP_CTRL;

typedef struct _VENDOR_DEWARP_DCTG_INFO {
        VENDOR_DEWARP_DCTG_MODE mode;
        VENDOR_DEWARP_DCTG_LENS_PARM lens;
        VENDOR_DEWARP_DCTG_FOV_PARM fov;
} VENDOR_DEWARP_DCTG_INFO;

typedef enum _VENDOR_DEWARP_DCTG_MODE {
	VENDOR_DEWARP_DCTG_MODE_90	= 0,
	VENDOR_DEWARP_DCTG_MODE_360	= 1,
	ENUM_DUMMY4WORD(VENDOR_DEWARP_DCTG_MODE)
} VENDOR_DEWARP_DCTG_MODE;

typedef struct _VENDOR_DEWARP_DCTG_LENS_PARM {
        UINT8 mount_type;         ///< Camera mount type. 0:Ceiling mount, 1:Floor mount
        UINT8 lut2d_sz;         ///< Size selection of 2D look-up table, 0:9x9, 3:65x65, should the same with DCE setting.
        UINT32 lens_r;          ///< Radius of Lens
        UINT32 lens_x_st;     ///< Lens start x position at a source image
        UINT32 lens_y_st;     ///< Lens start y position at a source image
} VENDOR_DEWARP_DCTG_LENS_PARM;

typedef struct _VENDOR_DEWARP_DCTG_FOV_PARM {
        INT32 theta_st;           ///< FOV theta start radian (s4.16) Range: -*pi ~ *pi
        INT32 theta_ed;          ///< FOV theta end radian (s4.16) Range: -*pi ~ *pi
        INT32 phi_st;                  ///< FOV phi start radian (s4.16) Range: -2*pi ~ 2*pi
        INT32 phi_ed;                ///< FOV phi end radian (s4.16) Range: -2*pi ~ 2*pi
        INT32 rot_z;               ///< Z-axis rotate radian (s4.16) Range: -2*pi ~ 2*pi
        INT32 rot_y;                   ///< Y-axis rotate radian (s4.16) Range: -2*pi ~ 2*pi
} VENDOR_DEWARP_DCTG_FOV_PARM;

](NT9833x_VPE_IQ_Tuning_Guide_en.files/image070.png)**

10 Revise History
-----------------

|     |     |     |     |
| --- | --- | --- | --- |
| **Version** | **Date** | **Advisor** | **Description** |
| 0.1.00 | 2021/01/20 | Allen Hsu | First version. |
| 0.2.00 | 2021/3/26 | Allen Hsu | Add description of Vendor command. |
| 0.3.00 | 2022/4/11 | Mina Wang | Add description for dce and dctg |