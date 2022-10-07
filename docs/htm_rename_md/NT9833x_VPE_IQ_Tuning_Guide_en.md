


<body lang=ZH-TW link=blue vlink=purple style='text-justify-trim:punctuation'>


<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570734"><span
lang=X-NONE>1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Overview</span></a></h1>

<p class=MsoNormal><span lang=X-NONE><img width=620 height=384
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image003.jpg"></span></p>

<p class=MsoCaption align=center style='text-align:center'><a
name="_Toc62034812"><span lang=EN-US>Figure </span></a><span
lang=EN-US>1</span><span lang=EN-US>&#8209;</span><span
lang=EN-US>1</span><span lang=EN-US> NT9833x Video Flow</span></p>

<p class=MsoNormal><span lang=X-NONE>VPE is an independent image processing
engine in YUV domain, and it performs some pre-processing process before LCD
display or encoder to improve the image quality. The related modules are as
follows: </span></p>

<p class=MsoNormal style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=X-NONE style='font-family:Wingdings'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;
</span></span><span lang=X-NONE>Spatial Noise Reduction Module(SPNR, using MRNR
method)</span></p>

<p class=MsoNormal style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=X-NONE style='font-family:Wingdings'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;
</span></span><span lang=X-NONE>Tempoarl Noise Reduction Module(TMNR)</span></p>

<p class=MsoNormal style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=X-NONE style='font-family:Wingdings'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;
</span></span><span lang=X-NONE>Sharpen Module(SHP)</span></p>

<p class=MsoNormal style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=X-NONE style='font-family:Wingdings'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;
</span></span><span lang=X-NONE>Scaling Module(SCA)</span></p>

<p class=MsoNormal><span style='font-family:"新細明體",serif;color:#0000CC'>※ </span><span
lang=X-NONE style='color:#0000CC'>The 9833x series has removed DCE and DCTG. </span></p>

<p class=MsoNormal><span style='font-family:"新細明體",serif;color:#0000CC'>※ </span><span
lang=X-NONE style='color:#0000CC'>In the following description, the area shown
in blue is the same module as the 9831x series but the parameters are
different. Please pay special attention)</span></p>

<p class=MsoNormal><span lang=EN-US><img width=642 height=435 id="圖片 2"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image004.jpg" alt="VPE_0"></span></p>

<p class=MsoNormal align=center style='text-align:center'><span lang=X-NONE><img
width=516 height=379 id="圖片 3"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image005.jpg" alt="VPE_1"></span></p>

<p class=MsoCaption align=center style='text-align:center'><a
name="_Toc62034813"><span lang=EN-US>Figure </span></a><span
lang=EN-US>1</span><span lang=EN-US>&#8209;</span><span
lang=EN-US>2</span><span lang=EN-US> </span><span lang=X-NONE>VPE Image
Processing Flow</span></p>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570735"><span
lang=X-NONE>2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>System Control</span></a></h1>

<p class=MsoNormal><span lang=X-NONE>The processing sequence of Sharpen, SPNR(using
MRNR method) and TMNR is changeable, and user can change the processing
sequence depends on different camera charateristic to achieve the best image
quality.</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570736"><span
lang=EN-US>2.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Parameter Description</span></a></h2>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=652
 style='width:489.05pt;margin-left:5.4pt;border-collapse:collapse'>
 <tr>
  <td width=180 valign=top style='width:134.7pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:72.05pt;text-indent:-72.05pt'><b><span
  lang=EN-US style='font-size:11.0pt'>Parameter</span></b></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:11.0pt'>Range</span></b></p>
  </td>
  <td width=106 valign=top style='width:79.65pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:11.0pt'>Def</span></b></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:11.0pt'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>ch_fd</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Video
  graph use ch_fd to represent the connected video engine of each channel. User
  can fine tune parameter of each video engine by setting ch_fd.</span></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=FR style='font-size:11.0pt;font-family:"Calibri",sans-serif'>pipe_mode</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~5</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:3.0pt;margin-right:0cm;margin-bottom:
  3.0pt;margin-left:0cm'><span lang=EN-US style='font-size:11.0pt;font-family:
  "Calibri",sans-serif'>Set module processing sequence.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0
  : MRNR -&gt; TMNR -&gt; Sharpen</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>1
  : MRNR-&gt; Sharpen -&gt; TMNR</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>2
  : Sharpen -&gt; MRNR -&gt; TMNR</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>3
  : SHP-&gt;TMNR-&gt;MRNR<br>
  4 :&nbsp;TMNR-&gt;MRNR-&gt;SHP<br>
  5 : TMNR-&gt;SHP-&gt;MRNR</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570737"><span
lang=EN-US>2.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Setting Interface</span></a></h2>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570738"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>2.2.1<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Proc</span></a></h3>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
28.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>
</span></span><span lang=X-NONE>/proc/videograph/vpe/ch_fd</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the current camera channel, and it only
needs to set once, the following SHP, MRNR, TMNR parameters will work on this
channel.</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>The following proc command will list all ch_fd of the
current video engine:</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:12.0pt'><span
lang=EN-US><img width=390 height=219 id="圖片 4"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image006.png" alt=652></span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write :</span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt'>echo [fd ] &gt; /proc/videograph/vpe/ch_fd</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Fw Internal
  Pointer</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>Read : cat /proc/videograph/vpe/ch_fd</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=60
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image007.png"
alt="Command : echo [fd] &gt; /proc/videograph/vpe/ch_fd&#13;&#10;Current channel = &lt;ch_fd&gt;&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
28.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>
</span></span><span lang=X-NONE>/proc/videograph/vpe/pipe_mode</span></h5>

<p class=MsoListBulletCxSpFirst style='margin-top:0cm;margin-right:12.0pt;
margin-bottom:0cm;margin-left:48.0pt;margin-bottom:.0001pt;text-indent:-24.0pt'><span
lang=EN-US>[Description]</span></p>

<p class=MsoListBulletCxSpMiddle style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=EN-US>Read or write the execsuting sequence of SHP, MRNR and TMNR. </span></p>

<p class=MsoListBulletCxSpMiddle style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=EN-US>[Command]</span></p>

<p class=MsoListBulletCxSpLast style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=EN-US>Write :</span></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt'>echo [pipe_mode ] &gt; /proc/videograph/vpe/pipe_mode</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>src_ppo_idx&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>mrnr_ppi_idx&nbsp;&nbsp;&nbsp;&nbsp; </span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>mrnr_ppo_idx&nbsp;&nbsp;&nbsp; </span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>tmnr_ppi_idx&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>tmnr_ppo_idx&nbsp;&nbsp;&nbsp;&nbsp; </span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>shp_ppi_idx&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>shp_ppo_idx&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>sca_ppi_idx</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoListBullet style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoListBulletCxSpFirst style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=EN-US>Read : cat /proc/videograph/vpe/pipe_mode</span></p>

<p class=MsoListBulletCxSpLast style='margin-left:48.0pt;text-indent:-24.0pt'><span
lang=EN-US><img width=618 height=228
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image008.png"
alt="Command : echo [pipe_mode] &gt; /proc/videograph/vpe/pipe_mode&#13;&#10;Current pipe_mode = [pipe_mode]&#13;&#10;mode :&#13;&#10;0 : MRNR-&gt; TMNR-&gt; SHP&#13;&#10;1 : MRNR-&gt; SHP-&gt;TMNR&#13;&#10;2 : SHP-&gt; MRNR -&gt; TMNR&#13;&#10;3 : SHP-&gt;TMNR-&gt;MRNR&#13;&#10;4 : TMNR-&gt;MRNR-&gt;SHP&#13;&#10;5 : TMNR-&gt;SHP-&gt;MRNR&#13;&#10;"></span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<b><span lang=X-NONE style='font-size:20.0pt;line-height:300%;font-family:"Arial",sans-serif'><br
clear=all style='page-break-before:always'>
</span></b>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc526350607"></a><a
name="_Toc526405682"></a><a name="_Toc526407372"></a><a name="_Toc526409060"></a><a
name="_Toc526412783"></a><a name="_Toc526414230"></a><a name="_Toc526350608"></a><a
name="_Toc526405683"></a><a name="_Toc526407373"></a><a name="_Toc526409061"></a><a
name="_Toc526412784"></a><a name="_Toc526414231"></a><a name="_Toc526350610"></a><a
name="_Toc526405685"></a><a name="_Toc526407375"></a><a name="_Toc526409063"></a><a
name="_Toc526412786"></a><a name="_Toc526414233"></a><a name="_Toc526350612"></a><a
name="_Toc526405687"></a><a name="_Toc526407377"></a><a name="_Toc526409065"></a><a
name="_Toc526412788"></a><a name="_Toc526414235"></a><a name="_Toc526350630"></a><a
name="_Toc526405705"></a><a name="_Toc526407395"></a><a name="_Toc526409083"></a><a
name="_Toc526412806"></a><a name="_Toc526414253"></a><a name="_Toc526350650"></a><a
name="_Toc526405725"></a><a name="_Toc526407415"></a><a name="_Toc526409103"></a><a
name="_Toc526412826"></a><a name="_Toc526414273"></a><a name="_Toc526350651"></a><a
name="_Toc526405726"></a><a name="_Toc526407416"></a><a name="_Toc526409104"></a><a
name="_Toc526412827"></a><a name="_Toc526414274"></a><a name="_Toc526350653"></a><a
name="_Toc526405728"></a><a name="_Toc526407418"></a><a name="_Toc526409106"></a><a
name="_Toc526412829"></a><a name="_Toc526414276"></a><a name="_Toc526350655"></a><a
name="_Toc526405730"></a><a name="_Toc526407420"></a><a name="_Toc526409108"></a><a
name="_Toc526412831"></a><a name="_Toc526414278"></a><a name="_Toc526350673"></a><a
name="_Toc526405748"></a><a name="_Toc526407438"></a><a name="_Toc526409126"></a><a
name="_Toc526412849"></a><a name="_Toc526414296"></a><a name="_Toc526350693"></a><a
name="_Toc526405768"></a><a name="_Toc526407458"></a><a name="_Toc526409146"></a><a
name="_Toc526412869"></a><a name="_Toc526414316"></a><a name="_Toc526350694"></a><a
name="_Toc526405769"></a><a name="_Toc526407459"></a><a name="_Toc526409147"></a><a
name="_Toc526412870"></a><a name="_Toc526414317"></a><a name="_Toc526350696"></a><a
name="_Toc526405771"></a><a name="_Toc526407461"></a><a name="_Toc526409149"></a><a
name="_Toc526412872"></a><a name="_Toc526414319"></a><a name="_Toc526350697"></a><a
name="_Toc526405772"></a><a name="_Toc526407462"></a><a name="_Toc526409150"></a><a
name="_Toc526412873"></a><a name="_Toc526414320"></a><a name="_Toc526350706"></a><a
name="_Toc526405781"></a><a name="_Toc526407471"></a><a name="_Toc526409159"></a><a
name="_Toc526412882"></a><a name="_Toc526414329"></a><a name="_Toc526350707"></a><a
name="_Toc526405782"></a><a name="_Toc526407472"></a><a name="_Toc526409160"></a><a
name="_Toc526412883"></a><a name="_Toc526414330"></a><a name="_Toc526350708"></a><a
name="_Toc526405783"></a><a name="_Toc526407473"></a><a name="_Toc526409161"></a><a
name="_Toc526412884"></a><a name="_Toc526414331"></a><a name="_Toc100570739"><span
lang=X-NONE>3<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Spatial Noise Reduction</span></a><span
lang=X-NONE> </span></h1>

<p class=Body0><span lang=X-NONE style='font-size:12.0pt;line-height:150%;
font-family:"Times New Roman",serif'>This is spatial noise reduction module(abbreviation
is “SPNR”). It will divide the image into high frequency part and middle
frequency part, performing noise reduction process respectively, then combine
together to achieve the purpose of noise reduction and retain detail.&nbsp; </span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570740"><span
lang=EN-US>3.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Overview</span></a></h2>

<p class=MsoNormal><span lang=X-NONE>Major processing flow is as follows :</span></p>

<p class=MsoNormal><span lang=EN-US><img width=645 height=227 id="圖片 7"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image009.png"></span></p>

<p class=MsoCaption align=center style='text-align:center'><span lang=EN-US>Figure
3&#8209;1 The SPNR processing flow.</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>Major processing flow :</span></p>

<p class=MsoNormal style='margin-left:18.0pt;text-indent:-18.0pt'><span
lang=X-NONE>1.<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=EN-US>Divide the input image into high frequency image
and middle frequency image.</span></p>

<p class=MsoNormal style='margin-left:18.0pt;text-indent:-18.0pt'><span
lang=X-NONE>2.<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Determine and label whether the processing
pixel is on the edge.</span></p>

<p class=MsoNormal style='margin-left:18.0pt;text-indent:-18.0pt'><span
lang=X-NONE>3.<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Perform edge smooth process on high frequency
image and middle frequency image, respectively.</span></p>

<p class=MsoNormal style='margin-left:18.0pt;text-indent:-18.0pt'><span
lang=X-NONE>4.<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Perform flat region noise reduction process on
middle frequency image.</span></p>

<p class=MsoNormal style='margin-left:18.0pt;text-indent:-18.0pt'><span
lang=X-NONE>5.<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Use high/middle frequency image which had
performed noise reduction process to reconstruct image.</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570741"><span
lang=EN-US>3.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Parameter Description</span></a></h2>

<p class=MsoNormal><span lang=X-NONE style='color:#0000CC'>(The blue text is
the part of the parameter difference between this module and the 9831x series,
please pay special attention)</span></p>

<p class=MsoCaption><a name="_Toc100570781"><span lang=EN-US>Table </span></a><span lang=EN-US>3</span><span lang=EN-US>&#8209;</span><span
lang=EN-US>1</span><span lang=EN-US> SPNR Parameter List</span></p>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=652
 style='width:489.05pt;margin-left:5.4pt;border-collapse:collapse'>
 <tr>
  <td width=180 valign=top style='width:134.7pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:72.05pt;text-indent:-72.05pt'><b><span
  lang=EN-US style='font-size:11.0pt'>Parameter</span></b></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:11.0pt'>Range</span></b></p>
  </td>
  <td width=106 valign=top style='width:79.65pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:11.0pt'>Def</span></b></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:11.0pt'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=FR style='font-size:11.0pt;font-family:"Calibri",sans-serif'>t_y_edge_detection
  [2][8]</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~1023</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>161,322,483,447,</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>419,320,195,130,</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>108,215,308,272,</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>246,185,125,100</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Y
  threshold for determining whether the current processing pixel is on the
  edge. </span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>It
  has eight thresholds mapping to pixel brightness from dark to bright,
  respectively.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[0][0~7]
  is the threshold from dark to bright for high frequency image.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[1][0~7]
  is the threshold from dark to bright for middle frequency image.</span></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=FR style='font-size:11.0pt;font-family:"Calibri",sans-serif'>t_cb_edge_detection</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~1023</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>0,249</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Cb
  threshold for determining whether the current processing pixel is on the
  edge. Only works in middle frequency image.</span></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=FR style='font-size:11.0pt;font-family:"Calibri",sans-serif'>t_cr_edge_detection
  [2]</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~1023</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>0,249</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Cr
  threshold for determining whether the current processing pixel is on the
  edge. Only works in middle frequency image.</span></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=FR style='font-size:11.0pt;font-family:"Calibri",sans-serif'>t_y_edge_smoothing[2][8]</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~255</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>66,132,161,149,</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>140,107,80,53,</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>44,88,103,91,</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>82,62,51,41</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='margin-top:4.5pt;margin-right:0cm;margin-bottom:
  4.5pt;margin-left:0cm;layout-grid-mode:char'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Y threshold for
  determining whether it will perform smooth process.</span><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'> </span></p>
  <p class=MsoNormal style='margin-top:4.5pt;margin-right:0cm;margin-bottom:
  4.5pt;margin-left:0cm;layout-grid-mode:char'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>It has eight
  thresholds mapping to pixel brightness from dark to bright, respectively.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[0][0~7]
  is the threshold from dark to bright for high frequency image.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[1][0~7]
  is the threshold from dark to bright for middle frequency image.</span></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=FR style='font-size:11.0pt;font-family:"Calibri",sans-serif'>t_cb_edge_smoothing
  [2]</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~255</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0,153</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Cb
  threshold for determining whether it will perform smooth process. </span><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Only
  works in middle frequency image.</span></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=FR style='font-size:11.0pt;font-family:"Calibri",sans-serif'>t_cr_edge_smoothing
  [2]</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~255</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0,153</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Cr
  threshold for determining whether it will perform smooth process. </span><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Only
  works in middle frequency image.</span></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>nr_strength_y[2]</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~15</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>{0,
  0}</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  denoise strength of spatial domain on Y channel.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[0]
  is denoise strength for high frequency image.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[1]
  is denoise strength for middle frequency image.</span></p>
  </td>
 </tr>
 <tr>
  <td width=180 style='width:134.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>nr_strength_c</span></p>
  </td>
  <td width=85 style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~15</span></p>
  </td>
  <td width=106 style='width:79.65pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>{0,
  10}</span></p>
  </td>
  <td width=281 valign=top style='width:210.95pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  denoise strength of spatial domain on Cb/Cr channel. </span><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Only works in middle
  frequency image.</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<p class=MsoNormal><a name="_Toc526350712"></a><a name="_Toc526405787"></a><a
name="_Toc526407477"></a><a name="_Toc526409165"></a><a name="_Toc526350713"></a><a
name="_Toc526405788"></a><a name="_Toc526407478"></a><a name="_Toc526409166"></a><a
name="_Toc526350715"></a><a name="_Toc526405790"></a><a name="_Toc526407480"></a><a
name="_Toc526409168"></a><a name="_Toc526350717"></a><a name="_Toc526405792"></a><a
name="_Toc526407482"></a><a name="_Toc526409170"></a><a name="_Toc526350719"></a><a
name="_Toc526405794"></a><a name="_Toc526407484"></a><a name="_Toc526409172"></a><a
name="_Toc526350737"></a><a name="_Toc526405812"></a><a name="_Toc526407502"></a><a
name="_Toc526409190"></a><a name="_Toc526350754"></a><a name="_Toc526405829"></a><a
name="_Toc526407519"></a><a name="_Toc526409207"></a><a name="_Toc526350755"></a><a
name="_Toc526405830"></a><a name="_Toc526407520"></a><a name="_Toc526409208"></a><a
name="_Toc526350757"></a><a name="_Toc526405832"></a><a name="_Toc526407522"></a><a
name="_Toc526409210"></a><a name="_Toc526350759"></a><a name="_Toc526405834"></a><a
name="_Toc526407524"></a><a name="_Toc526409212"></a><a name="_Toc526350777"></a><a
name="_Toc526405852"></a><a name="_Toc526407542"></a><a name="_Toc526409230"></a><a
name="_Toc526350794"></a><a name="_Toc526405869"></a><a name="_Toc526407559"></a><a
name="_Toc526409247"></a><a name="_Toc526350797"></a><a name="_Toc526405872"></a><a
name="_Toc526407562"></a><a name="_Toc526409250"></a><a name="_Toc526350799"></a><a
name="_Toc526405874"></a><a name="_Toc526407564"></a><a name="_Toc526409252"></a><a
name="_Toc526350817"></a><a name="_Toc526405892"></a><a name="_Toc526407582"></a><a
name="_Toc526409270"></a><a name="_Toc526350834"></a><a name="_Toc526405909"></a><a
name="_Toc526407599"></a><a name="_Toc526409287"></a><a name="_Toc526350837"></a><a
name="_Toc526405912"></a><a name="_Toc526407602"></a><a name="_Toc526409290"></a><a
name="_Toc526350839"></a><a name="_Toc526405914"></a><a name="_Toc526407604"></a><a
name="_Toc526409292"></a><a name="_Toc526350857"></a><a name="_Toc526405932"></a><a
name="_Toc526407622"></a><a name="_Toc526409310"></a><a name="_Toc526350874"></a><a
name="_Toc526405949"></a><a name="_Toc526407639"></a><a name="_Toc526409327"></a><a
name="_Toc526350875"></a><a name="_Toc526405950"></a><a name="_Toc526407640"></a><a
name="_Toc526409328"></a><a name="_Toc526350876"></a><a name="_Toc526405951"></a><a
name="_Toc526407641"></a><a name="_Toc526409329"></a><a name="_Toc526350878"></a><a
name="_Toc526405953"></a><a name="_Toc526407643"></a><a name="_Toc526409331"></a><a
name="_Toc526350887"></a><a name="_Toc526405962"></a><a name="_Toc526407652"></a><a
name="_Toc526409340"></a><a name="_Toc526350888"></a><a name="_Toc526405963"></a><a
name="_Toc526407653"></a><a name="_Toc526409341"></a><a name="_Toc526350889"></a><a
name="_Toc526405964"></a><a name="_Toc526407654"></a><a name="_Toc526409342"></a><a
name="_Toc526350890"></a><a name="_Toc526405965"></a><a name="_Toc526407655"></a><a
name="_Toc526409343"></a><a name="_Toc526350892"></a><a name="_Toc526405967"></a><a
name="_Toc526407657"></a><a name="_Toc526409345"></a><a name="_Toc526350894"></a><a
name="_Toc526405969"></a><a name="_Toc526407659"></a><a name="_Toc526409347"></a><a
name="_Toc526350896"></a><a name="_Toc526405971"></a><a name="_Toc526407661"></a><a
name="_Toc526409349"></a><a name="_Toc526350897"></a><a name="_Toc526405972"></a><a
name="_Toc526407662"></a><a name="_Toc526409350"></a><a name="_Toc526350898"></a><a
name="_Toc526405973"></a><a name="_Toc526407663"></a><a name="_Toc526409351"></a><a
name="_Toc526350900"></a><a name="_Toc526405975"></a><a name="_Toc526407665"></a><a
name="_Toc526409353"></a><a name="_Toc526350918"></a><a name="_Toc526405993"></a><a
name="_Toc526407683"></a><a name="_Toc526409371"></a><a name="_Toc526350919"></a><a
name="_Toc526405994"></a><a name="_Toc526407684"></a><a name="_Toc526409372"></a><a
name="_Toc526350921"></a><a name="_Toc526405996"></a><a name="_Toc526407686"></a><a
name="_Toc526409374"></a><a name="_Toc526350922"></a><a name="_Toc526405997"></a><a
name="_Toc526407687"></a><a name="_Toc526409375"></a><a name="_Toc526350923"></a><a
name="_Toc526405998"></a><a name="_Toc526407688"></a><a name="_Toc526409376"></a><a
name="_Toc526350924"></a><a name="_Toc526405999"></a><a name="_Toc526407689"></a><a
name="_Toc526409377"></a><a name="_Toc526350925"></a><a name="_Toc526406000"></a><a
name="_Toc526407690"></a><a name="_Toc526409378"></a><a name="_Toc526350926"></a><a
name="_Toc526406001"></a><a name="_Toc526407691"></a><a name="_Toc526409379"></a><a
name="_Toc526350927"></a><a name="_Toc526406002"></a><a name="_Toc526407692"></a><a
name="_Toc526409380"></a><a name="_Toc526350929"></a><a name="_Toc526406004"></a><a
name="_Toc526407694"></a><a name="_Toc526409382"></a><a name="_Toc526350947"></a><a
name="_Toc526406022"></a><a name="_Toc526407712"></a><a name="_Toc526409400"></a><a
name="_Toc526350948"></a><a name="_Toc526406023"></a><a name="_Toc526407713"></a><a
name="_Toc526409401"></a><a name="_Toc526350950"></a><a name="_Toc526406025"></a><a
name="_Toc526407715"></a><a name="_Toc526409403"></a><a name="_Toc526350951"></a><a
name="_Toc526406026"></a><a name="_Toc526407716"></a><a name="_Toc526409404"></a><a
name="_Toc526350952"></a><a name="_Toc526406027"></a><a name="_Toc526407717"></a><a
name="_Toc526409405"></a><a name="_Toc526350953"></a><a name="_Toc526406028"></a><a
name="_Toc526407718"></a><a name="_Toc526409406"></a><a name="_Toc526350954"></a><a
name="_Toc526406029"></a><a name="_Toc526407719"></a><a name="_Toc526409407"></a><a
name="_Toc526350955"></a><a name="_Toc526406030"></a><a name="_Toc526407720"></a><a
name="_Toc526409408"></a><a name="_Toc526350957"></a><a name="_Toc526406032"></a><a
name="_Toc526407722"></a><a name="_Toc526409410"></a><b><span lang=EN-US
style='font-size:11.0pt'>Advance description</span></b><span lang=EN-US
style='font-size:11.0pt'>: </span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:10.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><span lang=FR
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>edge_smoothing&nbsp;:
When SPNR performs smooth process, it will calculate weighting sum of neighbor
pixels along the edge direction, if the difference between the neighbor pixel
and center pixel is larger than threshold, this neighbor pixel will not be used
in the smooth process. The smooth process of Y/Cb/Cr are the same.</span><span
lang=FR style='font-size:10.0pt'> </span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570742"><span
lang=EN-US>3.3<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Setting Interface</span></a><span lang=X-NONE> </span></h2>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570743"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>3.3.1<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Proc</span></a></h3>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/mrnr/dump_info</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read all SPNR(using MRNR method) parameters of the
current camera channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : Not support.</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : cat /proc/videograph/vpe/mrnr/dump_info</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Output: <img width=618 height=276
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image010.png"
alt="channel &lt;ch_no&gt; = enable/disable&#13;&#10;t_y_edge_detection[0][8] = t_y_edge_detection[0][0] ….[0][7]&#13;&#10;t_y_edge_detection[1][8] = t_y_edge_detection[1][0] ….[1][7]&#13;&#10;t_cb_edge_detection = t_cb_edge_detection&#13;&#10;t_cr_edge_detection = t_cr_edge_detection&#13;&#10;t_y_edge_smoothing[0][8] = t_y_edge_smoothing[0][0]……[0][7]&#13;&#10;t_y_edge_smoothing[1][8] = t_y_edge_smoothing[1][0]……[1][7]&#13;&#10;t_cb_edge_smoothing = t_cb_edge_smoothing&#13;&#10;t_cr_edge_smoothing = t_cr_edge_smoothing&#13;&#10;nr_strength_y[2] = nr_strength_y[0], nr_strength_y[0]&#13;&#10;nr_strength_c = nr_strength_c&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/mrnr/</span><span
lang=X-NONE>mrnr</span><span lang=X-NONE>_en</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the MRNR enable status of the current
camera channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write :</span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>echo [mrnr_en
  (0~1)] &gt; /proc/videograph/vpe/mrnr/mrnr_en</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>mrnr_en</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : cat /proc/videograph/vpe/mrnr/mrnr_en</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Output: <img width=618 height=36
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image011.png"
alt="Command : echo [ch_en (0~1)] &gt; /proc/videograph/vpe/mrnr/mrnr_en"></span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/mrnr/t_xx_edge_det</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write edge_detection parameters.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border-top:none;border-left:
  solid navy 1.0pt;border-bottom:none;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [t_y_edge_det[0][0]
  …..[0][7]] &gt; /proc/videograph/vpe/mrnr/ t_y_edge_det_1</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border:none;border-right:solid navy 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>t_y_edge_detection[0~7]</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border-top:none;border-left:
  solid navy 1.0pt;border-bottom:none;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [t_y_edge_det[1][0]
  …..[1][7]] &gt; /proc/videograph/vpe/mrnr/ t_y_edge_det_2</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border:none;border-right:solid navy 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>t_y_edge_detection[8~15]</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border-top:none;border-left:
  solid navy 1.0pt;border-bottom:none;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [t_cb_edge_det]
  &gt; /proc/videograph/vpe/mrnr/ t_cb_edge_det</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border:none;border-right:solid navy 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>t_cb_edge_detection[0~1]</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [t_cr_edge_det]
  &gt; /proc/videograph/vpe/mrnr/ t_cr_edge_det</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>t_cr_edge_detection[0~1]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/mrnr/</span></b><span
lang=X-NONE style='font-size:10.0pt'>t_y_edge_det_1</span></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/mrnr/</span></b><span
lang=X-NONE style='font-size:10.0pt'>t_y_edge_det_2</span></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/mrnr/</span></b><span
lang=X-NONE style='font-size:10.0pt'>t_cb_edge_det_1</span></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/mrnr/</span></b><span
lang=X-NONE style='font-size:10.0pt'>t_cr_edge_det_1</span></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>&nbsp;</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=252
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image012.png"
alt="Command :&#13;&#10;echo [t_y_edge_det[0][0] …….. [0][7] &gt; /proc/videograph/vpe/mrnr/ t_y_edge_det_1&#13;&#10;echo [t_y_edge_det[1][0] …….. [0][7] &gt; /proc/videograph/vpe/mrnr/ t_y_edge_det_2&#13;&#10;echo [t_cb_edge_det &gt; /proc/videograph/vpe/mrnr/ t_cb_edge_det&#13;&#10;echo [t_cr_edge_det &gt; /proc/videograph/vpe/mrnr/ t_cr_edge_det&#13;&#10;===============================================================&#13;&#10;t_y_edge_det1 = t_y_edge_detection [0] [0] …………….[0][7]&#13;&#10;t_y_edge_det2 = t_y_edge_detection [1] [0]…………….. [0][7]&#13;&#10;t_cb_edge_det = t_cb_edge_detection&#13;&#10;t_cr_edge_det = t_cb_edge_detection &#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-autospace:none'><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/mrnr/t_xx_edge_smooth</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write edge_smoothing parameters.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border-top:none;border-left:
  solid navy 1.0pt;border-bottom:none;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [t_y_edge_smooth[0][0]]
  ……..[t_y_edge_smooth [0][7]] &gt; /proc/videograph/vpe/mrnr/
  t_y_edge_smooth_1</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border:none;border-right:solid navy 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>t_y_edge_
  smoothing[0~7]</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border-top:none;border-left:
  solid navy 1.0pt;border-bottom:none;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [t_y_edge_smooth[1][0]
  …….. [t_y_edge_smooth[1] [7]] &gt; /proc/videograph/vpe/mrnr/t_y_edge_smooth_2</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border:none;border-right:solid navy 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>t_y_edge_
  smoothing[8~16]</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border-top:none;border-left:
  solid navy 1.0pt;border-bottom:none;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [t_cb_edge_smooth]
  &gt; /proc/videograph/vpe/mrnr/ t_cb_edge_smooth</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border:none;border-right:solid navy 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>t_cb_edge_smoothing[0~1]</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [t_cr_edge_smooth]
  &gt; /proc/videograph/vpe/mrnr/ t_cr_edge_smooth</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>t_cr_edge_
  smoothing[0~1]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/mrnr/t_y_edge_smooth_1</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/mrnr/t_y_edge_smooth_2</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/mrnr/t_cb_edge_smooth</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/mrnr/t_cr_edge_smooth</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=228
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image013.png"
alt="Command :&#13;&#10;echo [t_y_edge_smooth[0]] …….. [t_y_edge_smooth [7]] &gt; /proc/videograph/vpe/mrnr/t_y_edge_smooth_1&#13;&#10;…&#13;&#10;===============================================================&#13;&#10;&#13;&#10;t_y_edge_smooth1 = t_y_edge_smoothing[0][0] ……………. [0][7]&#13;&#10;t_y_edge_smooth1 = t_y_edge_smoothing [1][0]…………….. [0][7]&#13;&#10;t_cb_edge_smooth = t_cb_edge_smoothing&#13;&#10;t_cr_edge_smooth = t_cr_edge_smoothing&#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-autospace:none'><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/mrnr/nr_strength</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write nr_strength parameters on Y/C channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [strength_y[0]]
  [strength_y [1]] [strength_c] &gt; /proc/videograph/vpe/mrnr/nr_strength</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>nr_strength_y[0~1],
  nr_strength_c</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : cat /proc/videograph/vpe/mrnr/ nr_strength</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image014.png"
alt="Command :&#13;&#10;echo [strength_y[0]] [strength_y [1]] [strength_c]] &gt; /proc/videograph/vpe/mrnr/nr_strength ===============================================================&#13;&#10;nr_strength_y = nr_strength_y[0], strength_y [1]&#13;&#10;nr_strength_c= nr_strength_c&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>&nbsp;</span></p>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570744"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>3.3.2<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Vendor API</span></a></h3>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Get and set the 2DNR
parameters corresponding to current path_id.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>Get</b></span><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_get(HD_PATH_ID path_id,
VENDOR_VIDEO_DN_2D, VENDOR_VIDEO_PARAM_MRNR *p_param);</span></p>

<p class=MsoNormal><b><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set</span></b><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_set(HD_PATH_ID path_id, VENDOR_VIDEO_DN_2D,
VENDOR_VIDEO_PARAM_MRNR *p_param);</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Definition]</span></b></p>

<p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt;font-family:
"Calibri",sans-serif'><img width=618 height=276
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image015.png"
alt="typedef struct _VENDOR_VIDEO_MRNR {&#13;&#10;	UINT32 mrnr_en;  					///&lt; MRNR ON/OFF&#13;&#10;	UINT32 t_y_edge_detection[2][8]; 	///&lt; Edge pixel detection threshold of Y{layer1~layer2}, 0~1023&#13;&#10;	UINT32 t_cb_edge_detection; 		///&lt; Edge pixel detection threshold of Cb{layer2}, 0~1023&#13;&#10;	UINT32 t_cr_edge_detection; 		///&lt; Edge pixel detection threshold of Cr{layer2}, 0~1023&#13;&#10;	UINT32 t_y_edge_smoothing[2][8]; 	///&lt; Edge pixel smoothing threshold of Y: {layer1~layer2}, 0~255&#13;&#10;	UINT32 t_cb_edge_smoothing; 		///&lt; Edge pixel smoothing threshold of Cb: {layer2}, 0~255&#13;&#10;	UINT32 t_cr_edge_smoothing;			///&lt; Edge pixel smoothing threshold of Cr: {layer2}, 0~255&#13;&#10;	UINT32 nr_strength_y[2]; 			///&lt; Strength of noise reduction of Y: {layer1~layer2}, 0~15&#13;&#10;	UINT32 nr_strength_c; 				///&lt; Strength of noise reduction of CbCr: {layer2}, 0~15&#13;&#10;} VENDOR_VIDEO_PARAM_MRNR;&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<b><span lang=X-NONE style='font-size:20.0pt;line-height:300%;font-family:"Arial",sans-serif'><br
clear=all style='page-break-before:always'>
</span></b>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc526350966"></a><a
name="_Toc526406041"></a><a name="_Toc526407731"></a><a name="_Toc526409419"></a><a
name="_Toc526412888"></a><a name="_Toc526414335"></a><a name="_Toc526350967"></a><a
name="_Toc526406042"></a><a name="_Toc526407732"></a><a name="_Toc526409420"></a><a
name="_Toc526412889"></a><a name="_Toc526414336"></a><a name="_Toc526350968"></a><a
name="_Toc526406043"></a><a name="_Toc526407733"></a><a name="_Toc526409421"></a><a
name="_Toc526412890"></a><a name="_Toc526414337"></a><a name="_Toc526350969"></a><a
name="_Toc526406044"></a><a name="_Toc526407734"></a><a name="_Toc526409422"></a><a
name="_Toc526412891"></a><a name="_Toc526414338"></a><a name="_Toc100570745"><span
lang=X-NONE>4<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Temporal Noise Reduction (TMNR)</span></a><span
lang=X-NONE> </span></h1>

<p class=Body0 style='text-align:justify;text-justify:inter-ideograph'><span
lang=X-NONE style='font-size:12.0pt;line-height:150%;font-family:"Times New Roman",serif'>This
is temporal noise reduction module(abbreviation is “TMNR”). The major function
is to eliminate temporal noise in the image.</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570746"><span
lang=EN-US>4.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Overview</span></a></h2>

<p class=MsoNormal><span lang=EN-US style='font-family:"Arial",sans-serif'><img
width=643 height=303 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image016.png"></span></p>

<p class=MsoNormal style='margin-left:18.0pt'><span lang=EN-US
style='font-family:"Calibri",sans-serif'>The concept of TMNR algorithm is to
determine whether the pixel status is static(MotionLevel=0) or motion(MotionLevel=2)
by Motion Detect module. The static region perform 3DNR to reduce the temporal
noise, and the motion region will not perform 3DNR to prevent from having
ghost, instead, it will perform 2DNR to reduce noise. The transition region between
static region and motion region will combine the result of 2DNR and 3DNR by
weighting. </span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570747"></a><a
name="_Ref522722543"></a><a name="_Ref522722539"></a><a name="_Parameter"></a><span
lang=EN-US>4.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Parameter description</span></h2>

<p class=MsoNormal><span lang=X-NONE style='color:#0000CC'>(The blue text is
the part of the parameter difference between this module and the 9831x series,
please pay special attention)</span></p>

<p class=MsoCaption><a name="_Toc100570782"><span lang=EN-US>Table </span></a><span lang=EN-US>4</span><span lang=EN-US>&#8209;</span><span
lang=EN-US>1</span><span lang=EN-US> </span><span lang=X-NONE>TMNR Parameter
List</span></p>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=650
 style='width:487.35pt;border-collapse:collapse'>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:72.05pt;text-align:
  center;text-indent:-72.05pt'><b><span lang=EN-US style='font-size:11.0pt'>Parameter</span></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><b><span lang=EN-US style='font-size:11.0pt'>Range</span></b></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><b><span lang=EN-US style='font-size:11.0pt'>Default</span></b></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><b><span lang=EN-US style='font-size:11.0pt;font-family:"新細明體",serif'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>tmnr_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>TMNR
  ON/OFF</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>luma_dn_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Y
  channel TMNR ON/OFF</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>chroma_dn_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Cb/Cr
  channel TMNR ON/OFF</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>tmnr_fcs_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Temporal
  de-false color function ON/OFF</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>It
  only works when “chroma_dn_en” is set to 1.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>nr_str_y_3d</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~32</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>8</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Y
  channel temporal NR strength</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>nr_str_y_2d</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~32</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>16</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Y
  channel spatial NR strength of motion object</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>nr_str _c_3d</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~32</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>16</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Cb/Cr
  channel temporal NR strength</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>nr_str _c_2d</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~32</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>16</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Cb/Cr
  channel spatial NR strength of motion object</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>blur_str_y</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~2</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Y
  image blurred strength</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0:
  No blur</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>1:
  low-strength blur</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>2:
  high-strength blur</span></p>
  <p class=MsoNormal><span style='font-size:11.0pt;font-family:"新細明體",serif'>※</span><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>It is
  recommend to set enable, if the executing sequence of 3DNR is after Sharpness;
  otherwise, it is recommend to set disable. For DVR/NVR application, due to in
  most case the front-end camera had perfomed sharpen process, it is recommend
  to set 1. </span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>center_wzero_y_2d_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Set
  to enable represents when performing the 2DNR, the weighting of center point
  is 0. It will increase NR strength, but might lose detail. Due to 2DNR only
  works on motion region, the detail loss is not obvious, it is recommend to
  fix enable.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>center_wzero_y_3d_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Set
  to enable represents when performing 3DNR, the weighting of center point is
  0. It is recommend to fix enable. </span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>small_vibrat_supp_y_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Y
  channel small vibration suppresiioon ON/OFF. This function will enhance
  suppression on small vibration noise to make the image more stable. However,
  it also causes slower ghost removal. It is recommend to enable at normal
  luminance, and disable at dark luminance.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>avoid_residue_th_y</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1~4</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>2</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Upper
  threshold for Y channel small noise putting back.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif;
  color:#0000CC'>If <b>err_compen</b></span><b><i><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif;color:#0000CC'>sate</span></i></b><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif;
  color:#0000CC'> = 0, bigger this value will cause smaller temporal noise. On
  the other hand, if err_compensate = 1, bigger this value will cause bigger
  temporal noise.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>avoid_residue_th_c</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1~4</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif;
  color:#0000CC'>Upper threshold for Vb/Cr channel small noise putting back.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif;
  color:#0000CC'>If <b>err_compensate</b> = 0, bigger this value will cause
  smaller temporal noise. On the other hand, if err_compensate = 1, bigger this
  value will cause bigger temporal noise.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>display_motion_map_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Debug
  mode. Show motion detection result on the image to assist to judge the
  correctness of motion detect parameters.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>motion_map_channel</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~4</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Select
  debug signal channel.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0:
  Y channel</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>1:
  Cb channel</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>2:
  Cr channel</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>3:
  temporal de-false color Cb channel</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>4:
  temporal de-false color Cr channel</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=EN-US style='font-size:11.0pt;font-family:
  "Calibri",sans-serif'>y_base[8]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~16320</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{146,147,107,110,102,104,104,104}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>y_base[0]-[7]
  are NoiseSAD mapping to pixel brightness from dark to bright. When performing
  2DNR, the internal algorithm will automatically fine tune strength based on y_base.
  The larger the y_base, the stronger strength of 2DNR of motion object. It is
  recommend to increase y_base as sensor gain increases.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>motion_level_th_y_k1</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~32</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>8</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Threshold
  (motion_level_th_y_k1*Y_NOISE) for determining transition region on Y
  channel. Y_NOISE please refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>motion_level_th_y_k2</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~32</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>8</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Threshold
  (motion_level_th_y_k2*Y_NOISE) for determining motion region on Y channel. </span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>K2
  must larger or equal to K1.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>y_coefa[8]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~48</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{0,0,0,0,0,0,0,0}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  slope of NoiseSAD from flat region to detail region on Y channel. y_coefa[0]-[7]
  mapping to pixel brightness from dark to bright.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>y_coefb[8]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~16320</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{27,27,20,12,7,10,10,10}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>NoiseSAD
  of flat region on Y channel. y_coefb[0]-[7] mapping to pixel brightness from
  dark to bright.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>y_std[8]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~16320</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{20,70,70,70,70,50,28,18}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  standard deviation of NoiseSAD on Y channel. y_std[0]-[7] mapping to pixel
  brightness from dark to bright.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>motion_level_th_c_k1</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~32</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>8</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Threshold
  for determining transition region on Cb/Cr channel.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>motion_level_th_c_k2</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~32</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>8</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Threshold
  for determining motion region on Cb/Cr channel, K2 must larger or equal to
  K1.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>cb_mean[8]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~6375</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{33,33,34,32,29,28,28,28}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  NoiseSAD mean value on Cb channel. cb_mean[0]-[7] mapping to pixel brightness
  from dark to bright.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>cb_std[8]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~6375</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{10,9,10,10,9,9,9,9}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  standard deviation of NoiseSAD on Cb channel. cb_std[0]-[7] mapping to pixel
  brightness from dark to bright.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>cr_mean[8]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~6375</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{23,23,25,23,20,20,21,21}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  NoiseSAD mean value on Cr channel. cr_mean[0]-[7] mapping to pixel brightness
  from dark to bright.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>cr_std[8]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~6375</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{7,7,8,7,7,77,7}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  standard deviation of NoiseSAD on Cr channel. cr_std[0]-[7] mapping to pixel
  brightness from dark to bright. </span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>lut_y_3d_1_Th[4]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~127</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{11,33,55,77}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Lut
  of Y channel 3D_1 filter</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>lut_y _3d_2_Th[4]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~127</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{40,14,7,3}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Lut
  of Y channel 3D_2 filter</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>lut_y_2d_Th[4]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~127</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{11,33,55,77}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Lut
  of Y channel 2D filter</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>lut_c_3d_Th[4]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~127</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{37,19,11,7}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Lut
  of Cb/Cr channel 3D filter</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>lut_c_2d_Th[4]</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~127</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>{11,33,55,77}</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Lut
  of Cb/Cr channel 2D filter</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>tmnr_fcs_str</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~15</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>4</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  strength of temporal de-false color function.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif'>tmnr_fcs_th</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>0~255</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif'>32</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Threshold
  for the difference between the previous frame and the current frame to
  determine whether it is false color.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif;color:#0000CC'>dithering_en</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><a name="OLE_LINK4"></a><a name="OLE_LINK3"><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif;
  color:#0000CC'>Dithering enable</span></a><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif;color:#0000CC'>. This function can be
  used to eliminate slight power noise or flicker phenomenon. </span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif;color:#0000CC'>dithering_bit_y</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>0~3</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>2</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><a name="OLE_LINK6"></a><a name="OLE_LINK5"><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif;
  color:#0000CC'>Y channel random bit number</span></a><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif;color:#0000CC'>. The
  higher the value, the stronger the ability to eliminate the power noiser and
  filcker phenomenon, but the picture may appear larger fine noise.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif;color:#0000CC'>dithering_bit_u</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>0~3</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif;
  color:#0000CC'>U channel random bit number. The higher the value, the
  stronger the ability to eliminate the power noiser and filcker phenomenon,
  but the picture may appear larger fine noise.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif;color:#0000CC'>dithering_bit_v</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>0~3</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif;
  color:#0000CC'>V channel random bit number. The higher the value, the
  stronger the ability to eliminate the power noiser and filcker phenomenon,
  but the picture may appear larger fine noise.</span></p>
  </td>
 </tr>
 <tr>
  <td width=187 valign=top style='width:140.1pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><b><i><span lang=EN-US style='font-size:
  11.0pt;font-family:"Calibri",sans-serif;color:#0000CC'>err_compensate</span></i></b></p>
  </td>
  <td width=76 valign=top style='width:2.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>0~1</span></p>
  </td>
  <td width=85 valign=top style='width:63.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal style='line-height:15.0pt;layout-grid-mode:char;
  text-autospace:ideograph-numeric'><span lang=EN-US style='font-size:11.0pt;
  font-family:"Calibri",sans-serif;color:#0000CC'>1</span></p>
  </td>
  <td width=302 valign=top style='width:8.0cm;border:none;border-bottom:solid #1D1DFF 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='color:#0000CC'>YC Compression
  error compensation. </span></p>
  <p class=MsoNormal><span lang=EN-US style='color:#0000CC'>0: Antiflicker
  mode. (Larger anti-flicker effect)</span></p>
  <p class=MsoNormal><span lang=EN-US style='color:#0000CC'>1: Compensation
  mode. (Data Compression Error Compensation)</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US style='font-size:11.0pt;font-family:
"Calibri",sans-serif'>Advance Description:</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt;text-indent:-24.1pt;line-height:
16.0pt'><span lang=EN-US style='font-family:Wingdings'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;
</span></span><b><i><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>tmnr_fcs_en:</span></i></b><b><i><span
lang=EN-US style='font-size:11.0pt'> </span></i></b><span lang=EN-US
style='font-size:11.0pt'>Temporal de-false color ON/OFF. This function will
eliminate color-flash phenomenon in high frequency region</span><span
lang=EN-US style='font-size:10.0pt'>.</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=EN-US>&nbsp;</span></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0
 style='margin-left:24.0pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=323 valign=top style='width:242.35pt;border:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><b><span
  lang=EN-US>FCS off</span></b></p>
  </td>
  <td width=323 valign=top style='width:242.35pt;border:solid windowtext 1.0pt;
  border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><b><span
  lang=EN-US>FCS on</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=323 valign=top style='width:242.35pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US><img width=238 height=138 id="圖片 15"
  src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image017.jpg"></span></p>
  </td>
  <td width=323 valign=top style='width:242.35pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US><img width=227 height=128 id="圖片 16"
  src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image018.jpg"></span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt'><b><i><span lang=EN-US><img
width=103 height=71 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image019.png"></span></i></b></p>

<p class=MsoNormal style='margin-left:24.1pt;text-indent:-24.1pt;line-height:
18.0pt'><span lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>display_motion_map_en:</span></i></b><span
style='font-size:11.0pt;font-family:"新細明體",serif'>。</span></p>

<p class=MsoNormal style='line-height:18.0pt'><span lang=EN-US
style='font-size:11.0pt'>Motion region will label with red color, static region
will label with black color, and transition region will label with white color</span><span
lang=EN-US style='font-size:10.0pt'>.</span></p>

<p class=MsoNormal><span lang=EN-US style='font-size:10.0pt'>&nbsp;</span></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0
 style='border-collapse:collapse;border:none'>
 <tr>
  <td width=253 valign=top style='width:189.7pt;border:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>Original image</span></p>
  </td>
  <td width=255 valign=top style='width:191.35pt;border:solid windowtext 1.0pt;
  border-left:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US>Motion Map</span></p>
  </td>
 </tr>
 <tr>
  <td width=253 valign=top style='width:189.7pt;border:solid windowtext 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US><img width=219 height=184
  src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image020.jpg"></span></p>
  </td>
  <td width=255 valign=top style='width:191.35pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US><img width=223 height=179 id="圖片 1"
  src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image021.jpg"></span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;line-height:16.0pt'><span
lang=EN-US style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt;line-height:
18.0pt'><span lang=X-NONE style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:11.0pt'>Y_NOISE</span></i></b><b><span lang=X-NONE
style='font-size:11.0pt'>:</span></b><span lang=X-NONE style='font-size:11.0pt'>
</span><span lang=EN-US style='font-size:11.0pt'>Block SAD is the summation of
pixel difference between the previous frame and current frame at the same
location. If the </span><span lang=X-NONE style='font-size:11.0pt'>Block SAD</span><span
lang=EN-US style='font-size:11.0pt'> is larger than </span><span lang=X-NONE
style='font-size:11.0pt'>K2*NoiseSAD_STD(NoiseSAD_STD is the input parameter),
it determines as motion region. </span><span lang=EN-US style='font-size:11.0pt'>If
the </span><span lang=X-NONE style='font-size:11.0pt'>Block SAD</span><span
lang=EN-US style='font-size:11.0pt'> is smaller than </span><span lang=X-NONE
style='font-size:11.0pt'>K1*NoiseSAD_STD, it determines as static region. </span><span
lang=EN-US style='font-size:11.0pt'>If the </span><span lang=X-NONE
style='font-size:11.0pt'>Block SAD</span><span lang=EN-US style='font-size:
11.0pt'> is larger than </span><span lang=X-NONE style='font-size:11.0pt'>K1*NoiseSAD_STD
and smaller than K2*NoiseSAD_STD, it determines as transition region.</span></p>

<p class=MsoNormal style='line-height:18.0pt'><span lang=X-NONE
style='font-size:11.0pt'>As follows :</span></p>

<p class=MsoNormal align=center style='text-align:center'><span lang=X-NONE><img
width=364 height=193 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image022.png"></span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt;line-height:
18.0pt'><span lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><span
lang=EN-US style='font-size:11.0pt'>Cb_NOISE, Cr_NOISE:</span></p>

<p class=MsoNormal style='margin-left:24.0pt;line-height:18.0pt'><span
lang=EN-US style='font-size:11.0pt'>Different from Y channel, the NoiseSAD of
Cb/Cr channel has no relationship with detail. Therefore, it has no slope
parameter. </span></p>

<p class=MsoNormal align=center style='text-align:center'><span lang=EN-US><img
width=364 height=193 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image023.png"></span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>lut_Y_3d_1_Th:</span></i></b><b><i><span
lang=EN-US style='font-size:10.0pt'> </span></i></b><span lang=EN-US
style='font-size:10.0pt'>Weighting Lut for stage 1 3DNR on Y channel, the
x-axis is delta difference of neighbor pixel, the y-axis is weighting. As the
following figure, the larger the difference, the smaller the weighting. The
smaller the difference, the larger the weighting. Then, based on each weighting
to perform weighting sum.</span></p>

<p class=MsoNormal align=center style='margin-left:24.0pt;text-align:center'><span
lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal align=center style='margin-left:24.0pt;text-align:center'><b><i><span
lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'><img
width=309 height=190 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image024.png"></span></i></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><b><i><span lang=EN-US
style='font-size:10.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></i></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>lut_Y_3d_2_Th:</span></i></b><b><i><span
lang=EN-US style='font-size:10.0pt'> </span></i></b><span lang=EN-US
style='font-size:10.0pt'>Weighting Lut for Stage 2 3DNR on Y channel, the
x-axis is difference of the reference point between the previous frame and
current frame, the y-axis is weighting. As the following figure, those with
smaller difference might be static region, and set smaller weighting, the
output will close to the reference frame. On the contrast, those with larger
difference might be motion region, and set larger weighting, the output will
close to the current frame.</span></p>

<p class=MsoNormal align=center style='margin-left:24.0pt;text-align:center'><b><i><span
lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'><img
width=309 height=190 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image025.png"></span></i></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>lut_Y_2d_Th:</span></i></b><b><i><span
lang=EN-US style='font-size:10.0pt'> </span></i></b><span lang=EN-US
style='font-size:10.0pt'>Weighting Lut of neighbor pixel for 2DNR on Y channel,
the x-axis is difference, the y-axis is weighting. As the following figure, the
larger the difference, the smaller the weighting. The smaller the difference,
the larger the weighting. Then, based on each weighting to perform weighting
sum.</span></p>

<p class=MsoNormal align=center style='margin-left:24.0pt;text-align:center'><b><i><span
lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'><img
width=309 height=190 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image026.png"></span></i></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>lut_c_3d_Th:
</span></i></b><span lang=EN-US style='font-size:10.0pt'>Suppression Level Lut
for 3DNR on Cb/Cr channel, the x-axis is the difference of the reference point
between the previous frame and current frame, the y-axis is the suppression
level. The concept is the same with “</span><b><i><span lang=EN-US
style='font-size:10.0pt;font-family:"Calibri",sans-serif'>LUT_Y_3d_2_Th</span></i></b><span
lang=EN-US style='font-size:10.0pt'>”.</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:10.0pt;font-family:"Calibri",sans-serif'>lut_c_2d_Th:</span></i></b><b><i><span
lang=EN-US style='font-size:10.0pt'> </span></i></b><span lang=EN-US
style='font-size:10.0pt'>Weighting Lut of neighbor pixel for 2DNR on Cb/Cr
channel, the x-axis is difference, the y-axis is weighting. The concept is the
same with “<b><i>lut_Y_2d_Th</i></b>”.</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=EN-US style='font-size:11.0pt'>&nbsp;</span></b></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570748"><span
lang=EN-US>4.3<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Setting Interface</span></a></h2>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570749"><span
lang=X-NONE>4.3.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Proc</span></a></h3>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/dump_info</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read all parameters of the current camera channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : Not support.</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/dump_info</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=572
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image027.png"
alt="luma_dn_en = luma_dn_en&#13;&#10;chroma_dn_en = chroma_dn_en&#13;&#10;tmnr_fcs_en = tmnr_fcs_en&#13;&#10;nt_str_y_3d = nt_str_y_3d&#13;&#10;nr_str_y_2d = nr_str_y_2d&#13;&#10;nr_str_c_3d = nr_str_c_3d&#13;&#10;nr_str_c_2d = nr_str_c_2d&#13;&#10;blur_str_y = blur_str_y&#13;&#10;center_wzero_y_2d_en = center_wzero_y_2d_en&#13;&#10;center_wzero_y_3d_en = center_wzero_y_3d_en&#13;&#10;small_vibrat_supp_y_en = small_vibrat_supp_y_en&#13;&#10;avoid_residue_th_y = avoid_residue_th_y&#13;&#10;avoid_residue_th_c = avoid_residue_th_c&#13;&#10;y_base[8] = y_base[0] ….. y_base[7]&#13;&#10;motion_level_th_y = motion_leve_tTh_y_k1, motion_level_th_y_k2&#13;&#10;motion_level_th_c = motion_level_th_c_k1, motion_level_th_c_k2&#13;&#10;y_coefa[8] = y_coefa[0] …y_coefa[7]&#13;&#10;y_coefb[8] = y_coefb[0] …y_coefb[7]&#13;&#10;y_std[8] = y_std[0] …y_std[7]&#13;&#10;cb_mean[8] = cb_mean[0] …. cb_mean[7]&#13;&#10;cb_std[8] = cb_std[0]……..cb_std[7]&#13;&#10;cr_mean[8] = cr_mean[0] …. cr_mean[7]&#13;&#10;cr_std[8] = cr_std[0]……..cr_std[7]&#13;&#10;lut_y_3d_1_th[4] = lut_y_3d_1_th[0]  ….. lut_y_3d_1_th[3]&#13;&#10;lut_y_3d_2_th[4] = lut_y_3d_2_th[0]  ….. lut_y_3d_2_th[3]&#13;&#10;lut_y_2d_th[4] = lut_y_2d_th[0]……lut_y_2d_th[3]&#13;&#10;lut_c_3d_th[4] = lut_c_3d_th[0]……. lut_c_3d_th[3]&#13;&#10;lut_c_2d_th[4] = lut_c_2d_th[0]…….. lut_c_2d_th[3]&#13;&#10;tmnr_fcs_str = tmnr_fcs_str&#13;&#10;tmnr_fcs_th = tmnr_fcs_th&#13;&#10;dithering_en = dithering_en&#13;&#10;dithering_bit_y = dithering_bit_y&#13;&#10;dithering_bit_u = dithering_bit_u&#13;&#10;dithering_bit_v = dithering_bit_v&#13;&#10;err_compensate = err_compensate&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/ch_en_status</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the enable status of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [luma_en] [chroma_en]
  [fcs_en] &gt; /proc/videograph/vpe/tmnr/ch_en_status</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>luma_dn_en</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>chroma_dn_en</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>tmnr_fcs_en</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/ch_en_status</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=180
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image028.png"
alt="Command : &#13;&#10;echo [luma_en] [chroma_en] [fcs_en] &gt; /proc/videograph/vpe/tmnr/ch_en_status ===============================================================&#13;&#10;&#13;&#10;luma_en = luma_dn_en&#13;&#10;chroma_en = chroma_dn_en&#13;&#10;fcs_en = tmnr_fcs_en&#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/nr_strength</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the TMNR strength of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [y_3d_str]
  [y_2d_str] [c_3d_str] [c_2d_str] &gt; /proc/videograph/vpe/tmnr/nr_strength</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>nr_str_y_3d,
  nr_str_y_2d</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>nr_str_c_3d,
  nr_str_c_2d</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/nr_strength</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=228
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image029.png"
alt="Command : &#13;&#10;echo [y_3d_str] [y_2d_str] [c_3d_str] [c_2d_str] &gt; /proc/videograph/vpe/tmnr//proc/videograph/vpe/tmnr/nr_strength ===============================================================&#13;&#10;&#13;&#10;nr_str_y_3d = nr_str_y_3d&#13;&#10;nr_str_y_2d = nr_str_y_2d&#13;&#10;nr_str_c_3d = nr_str_c_3d&#13;&#10;nr_str_c_2d = nr_str_c_2d&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/y_base</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the base noise level of TMNR of the
current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [y_base0] [y_base1]………[y_base7]
  &gt; /proc/videograph/vpe/tmnr/y_base</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>y_base[0]~[7]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/y_base</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image030.png"
alt="Command : &#13;&#10;echo [y_base0] [y_base1]………[y_base7] &gt; /proc/videograph/vpe/tmnr/y_base ===============================================================&#13;&#10;&#13;&#10;TMNR Noise Y_base = y_base[0]…………y_base[7]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/motion_level_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the noise model parameters of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [y_k1] [y_k2]
  [c_k1] [c_k2] &gt; /proc/videograph/vpe/tmnr/motion_level_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>motion_level_th_y_k1</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>motion_level_th_y_k2</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>motion_level_th_c_k1</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>motion_level_th_c_k2</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/motion_level_th</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=156
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image031.png"
alt="Command : &#13;&#10;echo [y_k1] [y_k2] [c_k1] [c_k2] &gt; /proc/videograph/vpe/tmnr/motion_level_th ===============================================================&#13;&#10;&#13;&#10;TMNR motion level th = motion_level_th_y_k1, motion_level_th_y_k2, motion_level_th_c_k1, motion_level_th_c_k2,&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/y_coeffa</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the noise model parameters of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [y_coeffa0]
  [y_coeffa1]………[y_coeffa7] &gt; /proc/videograph/vpe/tmnr/y_coeffa</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>y_coeffa[0]~[7]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/y_coeffa</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image032.png"
alt="Command : &#13;&#10;echo [y_coeffa0] [y_coeffa1]………[y_coeffa7] &gt; /proc/videograph/vpe/tmnr/y_coeffa ===============================================================&#13;&#10;&#13;&#10;TMNR Noise model y_coeffa = y_coeffa[0]…………y_coeffa[7]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/y_coeffb</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the noise model parameters of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [y_coeffb0]
  [y_coeffb1]………[y_coeffb7] &gt; /proc/videograph/vpe/tmnr/y_coeffb</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>y_coeffb[0]~[7]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/y_coeffb</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image033.png"
alt="Command : &#13;&#10;echo [y_coeffb0] [y_coeffb1]………[y_coeffb7] &gt; /proc/videograph/vpe/tmnr/y_coeffb ===============================================================&#13;&#10;&#13;&#10;TMNR Noise model y_coeffb = y_coeffb[0]…………y_coeffb[7]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/y_std</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the noise model parameters of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [y_std0] [y_std1]………[y_std7]
  &gt; /proc/videograph/vpe/tmnr/y_std</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>y_std[0]~[7]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/y_std</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image034.png"
alt="Command : &#13;&#10;echo [y_std0] [y_std1]………[y_std7] &gt; /proc/videograph/vpe/tmnr/y_std ===============================================================&#13;&#10;&#13;&#10;TMNR Noise model y_std = y_std[0]…………y_std[7]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/cb_mean</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the noise model parameters of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [cb_mean0]
  [cb_mean1]………[cb_mean 7] &gt; /proc/videograph/vpe/tmnr/cb_mean</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>cb_mean[0]~[7]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/cb_mean</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image035.png"
alt="Command : &#13;&#10;echo [cb_mean0] [cb_mean1]………[cb_mean 7] &gt; /proc/videograph/vpe/tmnr/cb_mean ===============================================================&#13;&#10;&#13;&#10;TMNR Noise model cb_mean = cb_mean[0]…………cb_mean[7]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/cb_std</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the noise model parameters of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [cb_std0] [cb_std1]………[cb_std7]
  &gt; /proc/videograph/vpe/tmnr/cb_std</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>cb_std[0]~[7]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/cb_std</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=108
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image036.png"
alt="Command : &#13;&#10;echo [cb_std0] [cb_std1]………[cb_std7] &gt; /proc/videograph/vpe/tmnr/cb_std ===============================================================&#13;&#10;TMNR Noise model cb_std = cb_std[0]…………cb_std[7]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/cr_</span><span
lang=X-NONE>mean</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the noise model parameters of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [cr_mean0]
  [cr_mean1]………[cr_std7] &gt; /proc/videograph/vpe/tmnr/cr_mean</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>cr_std[0]~[7]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/cr_mean</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image037.png"
alt="Command : &#13;&#10;echo [cr_mean0] [cr_mean1]………[cr_std7] &gt; /proc/videograph/vpe/tmnr/cr_mean ===============================================================&#13;&#10;&#13;&#10;TMNR Noise model cr_mean = cr_mean[0]…………cr_mean[7]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/cr_std</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the noise model parameters of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [cr_std0] [cr_std1]………[cr_std7]
  ] &gt; /proc/videograph/vpe/tmnr/cr_std</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>cr_std[0]~[7]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/cr_std</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image038.png"
alt="Command : &#13;&#10;echo [cr_std0] [cr_std1]………[cr_std7] &gt; /proc/videograph/vpe/tmnr/cr_std ===============================================================&#13;&#10;&#13;&#10;TMNR Noise model cr_std = cr_std[0]…………cr_std[7]&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/lut_y_3d_1_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the 3D noise reduction parameters of
TMNR of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [th0] [th1]
  [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_y_3d_1_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>lut_y_3d_1_th[0]~[3]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/lut_y_3d_1_th</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=108
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image039.png"
alt="Command : &#13;&#10;echo [th0] [th1] [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_y_3d_1_th ===============================================================&#13;&#10;TMNR lut_y_3d_1_th = lut_y_3d_1_th[0]…th[3]&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/lut_y_3d_2_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the 3D noise reduction parameters of
TMNR of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [th0] [th1]
  [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_y_3d_2_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>lut_y_3d_2_th[0]~[3]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/lut_y_3d_2_th</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'><img width=618 height=108
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image040.png"
alt="Command : &#13;&#10;echo [th0] [th1] [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_y_3d_2_th ===============================================================&#13;&#10;TMNR lut_y_3d_2_th = lut_y_3d_2_th[0]…th[3]&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/lut_y_2d_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the 2D noise reduction parameters of
TMNR of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [th0] [th1]
  [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_y_2d_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>lut_y_2d_th[0]~[3]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/lut_y_2d_th</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image041.png"
alt="Command : &#13;&#10;echo [th0] [th1] [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_y_2d_th ===============================================================&#13;&#10;&#13;&#10;TMNR lut_y_2d_th = lut_y_2d_th[0]…th[3]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/lut_c_3d_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the 3D noise reduction parameters of
3DNR of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [th0] [th1]
  [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_c_3d_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>lut_c_3d_th[0]~[3]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/lut_c_3d_th</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image042.png"
alt="Command : &#13;&#10;echo [th0] [th1] [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_c_3d_th ===============================================================&#13;&#10;&#13;&#10;TMNR lut_c_3d_th = lut_c_3d_th[0]…th[3]&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/lut_c_2d_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the 2D noise reduction parameters of
TMNR of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [th0] [th1]
  [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_c_2d_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>lut_c_2d_th[0]~[3]</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/lut_c_2d_th</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image043.png"
alt="Command : &#13;&#10;echo [th0] [th1] [th2] [th3] &gt; /proc/videograph/vpe/tmnr/lut_c_2d_th ===============================================================&#13;&#10;&#13;&#10;TMNR lut_c_3d_th = lut_c_2d_th[0]…th[3]&#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/fcs_str</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the false color suppression strength of
TMNR of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [fcs_str (0~15)
  ] &gt; /proc/videograph/vpe/tmnr/fcs_str</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>tmnr_fcs_str</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/fcs_str</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image044.png"
alt="Command : &#13;&#10;echo [fcs_str (0~15) ] &gt; /proc/videograph/vpe/tmnr/fcs_str ===============================================================&#13;&#10;&#13;&#10;TMNR FCS strength = tmnr_fcs_str&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/fcs_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the threshold for determining whether it
is false color of TMNR of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [fcs_th (0~255)
  ] &gt; /proc/videograph/vpe/tmnr/fcs_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>tmnr_fcs_th</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/fcs_th</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image045.png"
alt="Command : &#13;&#10;echo [fcs_th (0~255) ] &gt; /proc/videograph/vpe/tmnr/fcs_th ===============================================================&#13;&#10;&#13;&#10;TMNR FCS th = tmnr_fcs_th&#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/motion_map</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the motion map of TMNR of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [map_en (0~1)]
  &gt; [map_idx] &gt; /proc/videograph/vpe/tmnr/motion_map</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>map_en:</span></p>
  <p class=MsoNormal style='text-indent:10.0pt'><span lang=X-NONE
  style='font-size:10.0pt'>0: display_motion_map_en = 0</span></p>
  <p class=MsoNormal style='text-indent:10.0pt'><span lang=X-NONE
  style='font-size:10.0pt'>1: display_motion_map_en = 1</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>map_idx :</span></p>
  <p class=MsoNormal style='text-indent:5.0pt'><span lang=X-NONE
  style='font-size:10.0pt'>&nbsp;0: motion_map_channel=Y</span></p>
  <p class=MsoNormal style='text-indent:5.0pt'><span lang=X-NONE
  style='font-size:10.0pt'>&nbsp;1: motion_map_channel=Cb </span></p>
  <p class=MsoNormal style='text-indent:10.0pt'><span lang=X-NONE
  style='font-size:10.0pt'>2: motion_map_channel=Cr</span></p>
  <p class=MsoNormal style='text-indent:10.0pt'><span lang=X-NONE
  style='font-size:10.0pt'>3: motion_map_channel=FCS_Cb</span></p>
  <p class=MsoNormal style='text-indent:10.0pt'><span lang=X-NONE
  style='font-size:10.0pt'>4: motion_map_channel=FCS_Cr</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>display_motion_map_en,</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>motion_map_channel</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/motion_map</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=180
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image046.png"
alt="Command : &#13;&#10;echo [map_en (0~1)] [map_idx (0~4)] &gt; /proc/videograph/vpe/tmnr/motion_map&#13;&#10;===============================================================&#13;&#10;&#13;&#10;TMNR motion_map : &#13;&#10;map_en = display_motion_map_en &#13;&#10;map_channel = motion_map_channel&#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/diff_blur_str</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the Diff. image blur strength of TMNR of
the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [str (0~2)]
  &gt; /proc/videograph/vpe/tmnr/diff_blur_str</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>str: blur
  strength 0 ~2</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>blur_str_y</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/</span><span
lang=X-NONE style='font-size:10.0pt'>diff_blur_str</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image047.png"
alt="Command : &#13;&#10;echo [str (0~2)] &gt; /proc/videograph/vpe/tmnr/diff_blur_str&#13;&#10;===============================================================&#13;&#10;&#13;&#10;diff_blur_str = blur_str_y&#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/</span><span
lang=X-NONE>avoid_residue_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><a name="OLE_LINK12"></a><a
name="OLE_LINK11"><span lang=X-NONE style='font-size:11.0pt'>Read or write the Diff.
image blur strength of TMNR of the current channel.</span></a></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><a name="OLE_LINK16"></a><a name="OLE_LINK15"><b><span
  lang=X-NONE style='font-size:10.0pt'>Target Parameter</span></b></a></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [avoid_residue_th_y
  (1~4)] [avoid_residue_th_c (1~4)] &gt; /proc/videograph/vpe/tmnr/avoid_residue_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>avoid_residue_th_y,
  avoid_residue_th_c</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/</span><span
lang=X-NONE style='font-size:10.0pt'>avoid_residue_th</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=108
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image048.png"
alt="Command : &#13;&#10;echo [avoid_residue_th_y (1~4)] [avoid_residue_th_c (1~4)] &gt; /proc/videograph/vpe/ avoid_residue_th&#13;&#10;===============================================================&#13;&#10;avoid_residue_th_y= avoid_residue_th_y,  avoid_residue_th_c= avoid_residue_th_c&#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/</span><span
lang=X-NONE>dithering</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><a
name="OLE_LINK14"></a><a name="OLE_LINK13"><span lang=X-NONE style='font-size:
11.0pt'>Read or write the dithering relative parameters of the current channel.</span></a></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [dithering_en
  (0~1)] [dithering_bit_y (0~7)] [dithering_bit_u (0~7)] [dithering_bit_v (0~7)]
  &gt; /proc/videograph/vpe/tmnr/dithering</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>dithering_en</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>dithering_bit_y</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>dithering_bit_u</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>dithering_bit_v</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/</span><span
lang=X-NONE style='font-size:10.0pt'> dithering</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=156
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image049.png"
alt="Command : &#13;&#10;echo [dithering_en (0~1)] [dithering_bit_y (0~7)] [dithering_bit_u (0~7)] [dithering_bit_v (0~7)] &gt; /proc/videograph/vpe/tmnr/dithering&#13;&#10;===============================================================&#13;&#10;dithering_en = dithering_en, dithering_bit_y = dithering_bit_y, dithering_bit_u = dithering_bit_u, dithering_bit_v = dithering_bit_v&#13;&#10;"></span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/tmnr/</span><span
lang=X-NONE>err_compensate</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the err_compensate parameter of the
current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [</span><span
  lang=X-NONE style='font-size:11.0pt'>err_compensate</span><span lang=X-NONE
  style='font-size:10.0pt'> (0~1)] &gt; /proc/videograph/vpe/tmnr/</span><span
  lang=X-NONE style='font-size:11.0pt'>err_compensate</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>err_compensate</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/tmnr/err_compensate</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=108
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image050.png"
alt="Command : &#13;&#10;echo [err_compensate (0~1)] &gt; /proc/videograph/vpe/tmnr/err_compensate&#13;&#10;===============================================================&#13;&#10;err_compensate = err_compensate&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>&nbsp;</span></p>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570750"><span
lang=X-NONE>4.3.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Vendor API</span></a></h3>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Get and set the TMNR
parameters corresponding to current path_id.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>Get</b></span><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_get(HD_PATH_ID path_id, VENDOR_VIDEO_TMNR_CTRL,
VENDOR_VIDEO_PARAM_TMNR_EXT *p_param);</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>Set</b></span><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_set(HD_PATH_ID path_id, VENDOR_VIDEO_DN_2D,
VENDOR_VIDEO_PARAM_TMNR_EXT *p_param);</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Definition]</span></b></p>

<p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt;font-family:
"Calibri",sans-serif'><img width=683 height=815
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image051.png"
alt="typedef struct _VENDOR_VIDEO_PARAM_TMNR_EXT {&#13;&#10;	UINT32 tmnr_en;  		///&lt; 3DNR ON/OFF&#13;&#10;	UINT32 luma_dn_en;  	///&lt; Y channel 3DNR ON/OFF&#13;&#10;	UINT32 chroma_dn_en;  	///&lt; CbCr channel 3DNR ON/OFF&#13;&#10;	UINT32 nr_str_y_3d; 	///&lt; Y channel temporal NR strength, 0~32&#13;&#10;	UINT32 nr_str_y_2d; 	///&lt; Y channel spatial NR strength, 0~32&#13;&#10;	UINT32 nr_str_c_3d; 	///&lt; CbCr channel temporal NR strength, 0~32&#13;&#10;	UINT32 nr_str_c_2d; 	///&lt; CbCr channel spatial NR strength, 0~32&#13;&#10;	UINT32 blur_str_y; 		///&lt; Difference Y image blurred strength (0: No blur, 1: low-strength blur, 2: high-strength blur)&#13;&#10;	UINT32 center_wzero_y_2d_en; 	///&lt; Apply zero to center weight of Y spatial Bilateral filter&#13;&#10;	UINT32 center_wzero_y_3d_en; 	///&lt; Apply zero to center weight of Y temporal Bilateral filter&#13;&#10;	UINT32 small_vibrat_supp_y_en; 	///&lt; Y channel small vibration suppression ON/OF&#13;&#10;	UINT32 avoid_residue_th_y; 		///&lt; 1~4&#13;&#10;	UINT32 avoid_residue_th_c; 		///&lt; 1~4&#13;&#10;	UINT32 display_motion_map_en; 	///&lt; Display motion level map ON/OFF&#13;&#10;	UINT32 motion_map_channel; 		///&lt; Channel selection for motion level map display (0:Y, 1:Cb, 2:Cr)&#13;&#10;	UINT32 motion_level_th_y_k1; 	///&lt; Y channel match level threshold 1 adjustment, 0~32&#13;&#10;	UINT32 motion_level_th_y_k2; 	///&lt; Y channel match level threshold 2 adjustment, 0~32 AND K2 &gt; K1&#13;&#10;	UINT32 motion_level_th_c_k1; 	///&lt; CbCr channel match level threshold 1 adjustment, 0~32&#13;&#10;	UINT32 motion_level_th_c_k2; 	///&lt; CbCr channel match level threshold 2 adjustment, 0~32 AND K2 &gt; K1&#13;&#10;	UINT32 lut_y_3d_1_th[4]; 		///&lt; LUT of Y channel 3d_1 filter, 0~127&#13;&#10;	UINT32 lut_y_3d_2_th[4]; 		///&lt; LUT of CbCr channel 3d filter, 0~127&#13;&#10;	UINT32 lut_y_2d_th[4]; 			///&lt; LUT of Y channel 2d filter, 0~127&#13;&#10;	UINT32 lut_c_3d_th[4]; 			///&lt; LUT of CbCr channel 3d filter, 0~127&#13;&#10;	UINT32 lut_c_2d_th[4]; 			///&lt; LUT of CbCr channel 2d filter, 0~127&#13;&#10;	UINT32 y_base[8]; 				///&lt; Y channel noise model parameter: base noise level, 0 ~16320&#13;&#10;	UINT32 y_coefa[8]; 				///&lt; Y channel noise model parameter: slope of line, 0~48, Regard 16 as slope 1.0&#13;&#10;	UINT32 y_coefb[8]; 				///&lt; Y channel noise model parameter: intercept of line, 0 ~16320&#13;&#10;	UINT32 y_std[8]; 				///&lt; Y channel noise model parameter: noise standard deviation, 0 ~16320&#13;&#10;	UINT32 cb_mean[8]; 				///&lt; Cb channel noise model parameter: noise mean, 0 ~6375&#13;&#10;	UINT32 cb_std[8]; 				///&lt; Cb channel nosie model parameter: noise standard deviation, 0 ~6375&#13;&#10;	UINT32 cr_mean[8]; 				///&lt; Cr channel noise model parameter: noise mean, 0 ~6375&#13;&#10;	UINT32 cr_std[8]; 				///&lt; Cr channel nosie model parameter: noise standard deviation, 0 ~6375&#13;&#10;	UINT32 tmnr_fcs_en;  	        ///&lt; TMNR False Color Supression enable, **chroma_dn_en shoulde be 1&#13;&#10;	UINT32 tmnr_fcs_str;   			///&lt; TMNR_False Color Supression strength&#13;&#10;	UINT32 tmnr_fcs_th;         	///&lt; TMNR False Color Supression threshold&#13;&#10;	//new in nt98321&#13;&#10;	UINT8 dithering_en;   			///&lt; source dithering switch. 0~1. default  0&#13;&#10;	UINT8 dithering_bit_y;			///&lt; Y-channel dithering range. 0~3. default 2&#13;&#10;	UINT8 dithering_bit_u;			///&lt; U-channel dithering range. 0~3. default 1&#13;&#10;	UINT8 dithering_bit_v;			///&lt; V-channel dithering range. 0~3. default 1&#13;&#10;	UINT8 err_compensate;			///&lt; err compensation method option. 0~1. default 1&#13;&#10;} VENDOR_VIDEO_PARAM_TMNR_EXT;&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>&nbsp;</span></p>

<b><span lang=X-NONE style='font-size:20.0pt;line-height:300%;font-family:"Arial",sans-serif'><br
clear=all style='page-break-before:always'>
</span></b>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570751"><span
lang=X-NONE>5<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Sharpen (SHP)</span></a></h1>

<p class=MsoNormal><span lang=EN-US>This is texture enhancement module.</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570752"><span
lang=EN-US>5.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Overview</span></a></h2>

<p class=MsoNormal><span lang=EN-US>This a</span><span lang=X-NONE>lgorithm
adopts inverse gamma information and after gamma information to perform texture
enhancement, respectively, to improve the enhancement strength not smooth
problem of the bright/dark region. Besides, it adopts 3x3 and 5x5 filter to
enhance thin edge and thick edge, repectively, to take care of the detail and
contrast of image. Calculating “Edge Weight” to determine this is detail region
or flat region(thinner edge) and automatically adjusting weighting of detail
enhancement result and flat region enhancement result to take care of texture
enhancement and avoid noise enhancement. The “Halo clip” is used to control the
overshootong phenomenon caused by edge enhancement.</span></p>

<p class=MsoNormal><span lang=EN-US>The major flow please refer to the following
figure:</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US><img width=629 height=259 id="圖片 226"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image052.png"></span></p>

<p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US>Parameter
Description</span></p>

<p class=MsoCaption><a name="_Toc100570783"><span lang=EN-US>Table </span></a><span lang=EN-US>5</span><span lang=EN-US>&#8209;</span><span
lang=EN-US>1</span><span lang=EN-US> SHP Parameter List</span></p>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=652
 style='width:489.05pt;margin-left:5.4pt;border-collapse:collapse'>
 <tr>
  <td width=142 valign=top style='width:106.4pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:72.05pt;text-align:center;
  text-indent:-72.05pt'><b><span lang=EN-US style='font-size:11.0pt'>Parameter</span></b></p>
  </td>
  <td width=96 valign=top style='width:71.95pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Range</span></b></p>
  </td>
  <td width=113 valign=top style='width:85.0pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Def</span></b></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"新細明體",serif'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>sharpen_en</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Edge enhance ON/OFF</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_weight_src_sel</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Select the image source to calculate “Edge Weight ”.
  </span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0: after gamma, 1: inverse gamma.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_weight_th</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>2</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Threshold for calculating “Edge Weight”, those
  smaller than threshold will be considered as flat region, and the output all adopt
  flat region enhancement result.</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_weight_gain</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>175</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Adjust the weighting of detail enhancement result
  and flat region(thin edge) enhancement result. Based on the setting of “noise_level+noise_curve”
  to adjust EdgeWeight for different pixel brightness. The larger the Edge
  Weight, the larger weighting of detail enhancement result, repersenting the edge
  enhance is more stronger(more noise). In the contrast, the smaller the edge
  weight, the larger weighting of flat region enhancement result, representing
  the edge enhancement is less stronger.</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>noise_level</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>25</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Please refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>noise_curve[17]</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>{50, 50, 50, 48, 47, 44, 39, 38, 37, 36,
  35, 35, 35, 35, 35, 35, 35}</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Please refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>blend_inv_gamma</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~128</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>64</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>The blending weight of inverse gamma edge
  enhancement result and after gamma edge enhancement result. This parameter is
  equal to adjust the ratio of edge enhancement between bright region and dark
  region, let the edge enhancement level of bright region and dark region is
  more even. The larger the value, the stronger strength of bright region
  enhancement, but the weaker strength of dark region enhancement. </span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_sharp_str1</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>25</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Adjust the strength of thin edge enhancement</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_sharp_str2</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>10</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Adjust the strength of thick edge enhancement</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>flat_sharp_str</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Adjust the strength of flat region(thin detail)
  enhancement.</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>coring_th</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Threshold for determing whether to perform
  enhancement. For those edge value smaller than threshold, they will not
  perform edge enhancement to avoid enhancing noise.</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>bright_halo_clip</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~128</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>32</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Remove
  bright halo edge caused by edge enhancement. The smaller the “bright_halo_clip”,
  the less bright halo edge, but the sharpness might be decreased.</span></p>
  </td>
 </tr>
 <tr>
  <td width=142 style='width:106.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>dark_halo_clip</span></i></b></p>
  </td>
  <td width=96 style='width:71.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~128</span></p>
  </td>
  <td width=113 style='width:85.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>96</span></p>
  </td>
  <td width=301 valign=top style='width:225.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Remove dark halo edge caused by edge enhancement.
  The smaller the “dark_halo_clip”, the less dark halo edge, but the sharpness
  might be decreased.</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>Advance description</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>noise_level,
noise_curve[17]:</span></i></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=EN-US
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>noise_level = noise_level
+ NoiseofPixel, wherein the NoiseofPixel is the y-axis of </span><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>noise_curve</span><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>.</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=EN-US
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The noise_curve may
depend on the pixel brightness to set the noise size, respectively. Normally,
human eyes are less sensitive to the noise in high bright region; thus, it can
set small value to increase the edge enhancement strength to enhance detail. It
is recommend to use the following default value. If user want to adjust the
noise size at all Y range(0-255), it just needs to adjust noise_level.</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span style='position:relative;
z-index:251619328'><span style='left:0px;position:absolute;left:91px;
top:-2363px;width:75px;height:1px'><img width=75 height=1
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image053.png" alt=Noise></span></span><span
lang=EN-US>&nbsp;</span></p>

<br clear=ALL>

<p class=MsoNormal><span lang=EN-US><img width=654 height=190
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image054.png"></span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=EN-US>Default value:</span></p>

<p class=MsoNormal style='text-indent:24.0pt'><b><i><span lang=EN-US
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>edge_weight_src_sel</span></i></b><span
lang=EN-US style='font-size:11.0pt'> =0</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=EN-US
style='font-size:11.0pt'>noise_curve[17] ={50,50,50,48,47,44,39,38,37,36,35,35,35,35,35,35,35}</span></p>

<p class=MsoNormal style='margin-left:42.0pt;text-indent:-18.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>&eth;<span
style='font:7.0pt "Times New Roman"'>&nbsp; </span></span><span lang=EN-US
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>More strengthen on
detail in bright region to avoid enhancing noise.</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><b><i><span lang=EN-US
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>edge_weight_src_sel</span></i></b><span
lang=EN-US style='font-size:11.0pt'> =1</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=EN-US
style='font-size:11.0pt'>noise_curve[17] = {0, 38, 46, 51, 54, 57, 59, 61, 62,
62, 62, 62, 62, 62, 62, 62, 62}</span></p>

<p class=MsoNormal style='margin-left:42.0pt;text-indent:-18.0pt'><span
lang=EN-US style='font-size:10.0pt;font-family:Wingdings'>&eth;<span
style='font:7.0pt "Times New Roman"'>&nbsp; </span></span><span lang=EN-US
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>More strengthen on
detail in dark region to enhance thin detail, but the noise in dark region will
be enhanced, either.</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570753"><span
lang=EN-US>5.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Setting Interface</span></a></h2>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570754"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>5.2.1<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Proc</span></a></h3>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/dump_info</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read all Sharpen parameters of the current camera
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : Not support.</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>Read : cat /proc/videograph/vpe/sharpen/dump_info</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=324
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image055.png"
alt="Current channel = &lt;ch_no&gt;&#13;&#10;edge_weight_src_sel = edge_weight_src_sel&#13;&#10;edge_weight_th = edge_weight_th&#13;&#10;edge_weight_gain = edge_weight_gain&#13;&#10;noise_level = noise_level&#13;&#10;noise_curve[17] = noise_curve[0] ………. noise_curve[16]&#13;&#10;blend_inv_gamma = blend_inv_gamma&#13;&#10;edge_sharp_str1 = edge_sharp_str1&#13;&#10;edge_sharp_str2 = edge_sharp_str2&#13;&#10;flat_sharp_str = flat_sharp_str&#13;&#10;coring_th = coring_th&#13;&#10;bright_halo_clip = bright_halo_clip&#13;&#10;dark_halo_clip = dark_halo_clip&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/</span><span
lang=X-NONE>sharp</span><span lang=X-NONE>_en</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the enable status of the cuurent
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [ sharp_en
  (0~1) ] &gt; /proc/videograph/vpe/sharpen/sharp_en</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>sharpen_en</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/shp_en</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image056.png"
alt="Command : &#13;&#10;echo [ sharp_en (0~1) ] &gt; /proc/videograph/vpe/sharpen/sharp_en ===============================================================&#13;&#10;&#13;&#10;sharpen_en = sharpen_en&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/edge_weight_src_sel</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [src_sel (0
  ~ 1) ] &gt; /proc/videograph/vpe/sharpen/edge_weight_src_sel</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>edge_weight_src_sel</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>edge_weight_src_sel</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=156
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image057.png"
alt="Command : &#13;&#10;echo [src_sel (0 ~ 1)] &gt; /proc/videograph/vpe/sharpen/edge_weight_src_sel ===============================================================&#13;&#10;&#13;&#10;edge_weight_src_sel = edge_weight_src_sel&#13;&#10;0: after gamma 1: before gamma&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/edge_weigt_gain</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [gain
  (0~255) ] &gt; /proc/videograph/vpe/sharpen/edge_weight_gain</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>edge_weight_gain</span></i></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>edge_weight_gain</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image058.png"
alt="Command : &#13;&#10;echo [gain (0~255)] &gt; /proc/videograph/vpe/sharpen/edge_weight_gain ===============================================================&#13;&#10;&#13;&#10;edge_weight_gain = edge_weight_gain&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/edge_weight_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [th
  (0~255) ] &gt; /proc/videograph/vpe/sharpen/edge_weight_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>edge_weight_th</span></i></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>edge_weight_th</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image059.png"
alt="Command : &#13;&#10;echo [th (0~255)] &gt; /proc/videograph/vpe/sharpen/edge_weight_th ===============================================================&#13;&#10;&#13;&#10;edge_weight_th = edge_weight_th&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/blend_inv_gamma</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [th
  (0~128) ] &gt; /proc/videograph/vpe/sharpen/blend_inv_gamma</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>blend_inv_gamma</span></i></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>blend_inv_gamma</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image060.png"
alt="Command : &#13;&#10;echo [th (0~128) &gt; /proc/videograph/vpe/sharpen/blend_inv_gamma ===============================================================&#13;&#10;&#13;&#10;blend_inv_gamma = blend_inv_gamma&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/edge_sharp_str</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [str1
  (0~255)] [str2 (0~255)] &gt; /proc/videograph/vpe/sharpen/edge_sharp_str</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>edge_sharp_str1</span></i></b></p>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>edge_sharp_str2</span></i></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>edge_sharp_str</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image061.png"
alt="Command : &#13;&#10;echo [str1 (0~255)] [str2 (0~255)] &gt; /proc/videograph/vpe/sharpen/edge_sharp_str ===============================================================&#13;&#10;sharp_str1 = edge_sharp_str1&#13;&#10;sharp_str2 = edge_sharp_str2&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/flat_sharp_str</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [str
  (0~255)] &gt; /proc/videograph/vpe/sharpen/flat_sharp_str</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>flat_sharp_str</span></i></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>flat_sharp_str</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image062.png"
alt="Command : &#13;&#10;echo [str (0~255)] &gt; /proc/videograph/vpe/sharpen/flat_sharp_str ===============================================================&#13;&#10;&#13;&#10;flat_sharp_str = flat_sharp_str&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/coring_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [coring_th
  (0~255)] &gt; /proc/videograph/vpe/sharpen/coring_th</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>coring_th</span></i></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>coring_th</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image063.png"
alt="Command : &#13;&#10;echo [coring_th (0~255)] &gt; /proc/videograph/vpe/sharpen/coring_th ===============================================================&#13;&#10;&#13;&#10;coring_th = coring_th&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/halo_clip</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [bright_clip
  (0~128)] [dark_clip(0~128)] &gt; /proc/videograph/vpe/sharpen/halo_clip</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>bright_halo_clip</span></i></b></p>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>drak_halo_clip</span></i></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>halo_clip</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=156
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image064.png"
alt="Command : &#13;&#10;echo [bright_clip (0~128)] [dark_clip(0~128)] &gt; /proc/videograph/vpe/sharpen/halo_clip ===============================================================&#13;&#10;&#13;&#10;Bright_halo_clip = bright_halo_clip&#13;&#10;Dark_halo_clip = dark_halo_clip&#13;&#10;"></span></b></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sharpen/noise_curve</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the sharpen parameter of the current
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write :</span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [noise_curve[0]
  (0~255)]…. [noise_curve [16] (0~255)] &gt; /proc/videograph/vpe/sharpen/noise_curve</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><i><span lang=X-NONE style='font-size:10.0pt'>noise_curve[17]</span></i></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sharpen/</span><span
lang=X-NONE style='font-size:10.0pt'>noise_curve</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=132
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image065.png"
alt="Command : &#13;&#10;echo [noise_curve[0] (0~255)]…. [noise_curve [16] (0~255)] &gt; /proc/videograph/vpe/sharpen/noise_curve ===============================================================&#13;&#10;&#13;&#10;noise_curve = noise_curve[0] ……….noise_curve[16]&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=EN-US style='font-size:10.0pt'>&nbsp;</span></p>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570755"><span
lang=X-NONE>5.2.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Vendor API</span></a></h3>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Get and set the
sharpen parameters corresponding to current path_id.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>Get</b></span><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_get(HD_PATH_ID path_id, VENDOR_VIDEO_SHARP,
</span><span lang=X-NONE style='font-size:11.0pt'>VENDOR_VIDEO_PARAM_SHARP</span><span
lang=X-NONE style='font-size:14.0pt'> </span><span lang=X-NONE
style='font-size:11.0pt'>*p_param);</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>Set</b></span><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_set(HD_PATH_ID path_id, VENDOR_VIDEO_SHARP,
</span><span lang=X-NONE style='font-size:11.0pt'>VENDOR_VIDEO_PARAM_SHARP</span><span
lang=X-NONE style='font-size:11.0pt'> *p_param);</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[</span></b><b><span
style='font-size:11.0pt;font-family:"新細明體",serif'>定義</span></b><b><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>]</span></b></p>

<p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt;font-family:
"Calibri",sans-serif'><img width=641 height=292
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image066.png"
alt="typedef struct _VENDOR_VIDEO_PARAM_SHARP {&#13;&#10;	UINT32 sharp_en;  			///&lt; Sharpness ON/OFF&#13;&#10;	UINT32 edge_weight_src_sel; ///&lt; Select source of edge weight calculation, 0~1&#13;&#10;	UINT32 edge_weight_th; 		///&lt; Edge weight coring threshold, 0~255&#13;&#10;	UINT32 edge_weight_gain; 	///&lt; Edge weight gain, 0~255&#13;&#10;	UINT32 noise_level; 		///&lt; Noise Level, 0~255&#13;&#10;	UINT32 noise_curve[17]; 	///&lt; 17 control points of noise modulation curve, 0~255&#13;&#10;	UINT32 blend_inv_gamma; 	///&lt; Blending ratio of HPF results, 0~128&#13;&#10;	UINT32 edge_sharp_str1; 	///&lt; Sharpen strength1 of edge region, 0~255&#13;&#10;	UINT32 edge_sharp_str2; 	///&lt; Sharpen strength2 of edge region, 0~255&#13;&#10;	UINT32 flat_sharp_str; 		///&lt; Sharpen strength of flat region,0~255&#13;&#10;	UINT32 coring_th; 			///&lt; Coring threshold, 0~255&#13;&#10;	UINT32 bright_halo_clip; 	///&lt; Bright halo clip ratio, 0~255&#13;&#10;	UINT32 dark_halo_clip; 		///&lt; Dark halo clip ratio, 0~255&#13;&#10;} VENDOR_VIDEO_PARAM_SHARP;&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570756"></a><a
name="_Toc530562922"></a><a name="_Toc526350977"></a><a name="_Toc526406052"></a><a
name="_Toc526407742"></a><a name="_Toc526409430"></a><a name="_Toc526412899"></a><a
name="_Toc526414346"></a><a name="_Toc526350978"></a><a name="_Toc526406053"></a><a
name="_Toc526407743"></a><a name="_Toc526409431"></a><a name="_Toc526412900"></a><a
name="_Toc526414347"></a><a name="_Toc526350980"></a><a name="_Toc526406055"></a><a
name="_Toc526407745"></a><a name="_Toc526409433"></a><a name="_Toc526412902"></a><a
name="_Toc526414349"></a><a name="_Toc526350982"></a><a name="_Toc526406057"></a><a
name="_Toc526407747"></a><a name="_Toc526409435"></a><a name="_Toc526412904"></a><a
name="_Toc526414351"></a><a name="_Toc526351000"></a><a name="_Toc526406075"></a><a
name="_Toc526407765"></a><a name="_Toc526409453"></a><a name="_Toc526412922"></a><a
name="_Toc526414369"></a><a name="_Toc526351017"></a><a name="_Toc526406092"></a><a
name="_Toc526407782"></a><a name="_Toc526409470"></a><a name="_Toc526412939"></a><a
name="_Toc526414386"></a><a name="_Toc526351018"></a><a name="_Toc526406093"></a><a
name="_Toc526407783"></a><a name="_Toc526409471"></a><a name="_Toc526412940"></a><a
name="_Toc526414387"></a><a name="_Toc526351020"></a><a name="_Toc526406095"></a><a
name="_Toc526407785"></a><a name="_Toc526409473"></a><a name="_Toc526412942"></a><a
name="_Toc526414389"></a><a name="_Toc526351022"></a><a name="_Toc526406097"></a><a
name="_Toc526407787"></a><a name="_Toc526409475"></a><a name="_Toc526412944"></a><a
name="_Toc526414391"></a><a name="_Toc526351040"></a><a name="_Toc526406115"></a><a
name="_Toc526407805"></a><a name="_Toc526409493"></a><a name="_Toc526412962"></a><a
name="_Toc526414409"></a><a name="_Toc526351057"></a><a name="_Toc526406132"></a><a
name="_Toc526407822"></a><a name="_Toc526409510"></a><a name="_Toc526412979"></a><a
name="_Toc526414426"></a><a name="_Toc526351058"></a><a name="_Toc526406133"></a><a
name="_Toc526407823"></a><a name="_Toc526409511"></a><a name="_Toc526412980"></a><a
name="_Toc526414427"></a><a name="_Toc526351060"></a><a name="_Toc526406135"></a><a
name="_Toc526407825"></a><a name="_Toc526409513"></a><a name="_Toc526412982"></a><a
name="_Toc526414429"></a><a name="_Toc526351062"></a><a name="_Toc526406137"></a><a
name="_Toc526407827"></a><a name="_Toc526409515"></a><a name="_Toc526412984"></a><a
name="_Toc526414431"></a><a name="_Toc526351080"></a><a name="_Toc526406155"></a><a
name="_Toc526407845"></a><a name="_Toc526409533"></a><a name="_Toc526413002"></a><a
name="_Toc526414449"></a><a name="_Toc526351097"></a><a name="_Toc526406172"></a><a
name="_Toc526407862"></a><a name="_Toc526409550"></a><a name="_Toc526413019"></a><a
name="_Toc526414466"></a><a name="_Toc526351098"></a><a name="_Toc526406173"></a><a
name="_Toc526407863"></a><a name="_Toc526409551"></a><a name="_Toc526413020"></a><a
name="_Toc526414467"></a><a name="_Toc526351100"></a><a name="_Toc526406175"></a><a
name="_Toc526407865"></a><a name="_Toc526409553"></a><a name="_Toc526413022"></a><a
name="_Toc526414469"></a><a name="_Toc526351102"></a><a name="_Toc526406177"></a><a
name="_Toc526407867"></a><a name="_Toc526409555"></a><a name="_Toc526413024"></a><a
name="_Toc526414471"></a><a name="_Toc526351120"></a><a name="_Toc526406195"></a><a
name="_Toc526407885"></a><a name="_Toc526409573"></a><a name="_Toc526413042"></a><a
name="_Toc526414489"></a><a name="_Toc526351137"></a><a name="_Toc526406212"></a><a
name="_Toc526407902"></a><a name="_Toc526409590"></a><a name="_Toc526413059"></a><a
name="_Toc526414506"></a><a name="_Toc526351140"></a><a name="_Toc526406215"></a><a
name="_Toc526407905"></a><a name="_Toc526409593"></a><a name="_Toc526413062"></a><a
name="_Toc526414509"></a><a name="_Toc526351142"></a><a name="_Toc526406217"></a><a
name="_Toc526407907"></a><a name="_Toc526409595"></a><a name="_Toc526413064"></a><a
name="_Toc526414511"></a><a name="_Toc526351160"></a><a name="_Toc526406235"></a><a
name="_Toc526407925"></a><a name="_Toc526409613"></a><a name="_Toc526413082"></a><a
name="_Toc526414529"></a><a name="_Toc526351177"></a><a name="_Toc526406252"></a><a
name="_Toc526407942"></a><a name="_Toc526409630"></a><a name="_Toc526413099"></a><a
name="_Toc526414546"></a><a name="_Toc526351179"></a><a name="_Toc526406254"></a><a
name="_Toc526407944"></a><a name="_Toc526409632"></a><a name="_Toc526413101"></a><a
name="_Toc526414548"></a><a name="_Toc526351180"></a><a name="_Toc526406255"></a><a
name="_Toc526407945"></a><a name="_Toc526409633"></a><a name="_Toc526413102"></a><a
name="_Toc526414549"></a><a name="_Toc526351182"></a><a name="_Toc526406257"></a><a
name="_Toc526407947"></a><a name="_Toc526409635"></a><a name="_Toc526413104"></a><a
name="_Toc526414551"></a><a name="_Toc526351200"></a><a name="_Toc526406275"></a><a
name="_Toc526407965"></a><a name="_Toc526409653"></a><a name="_Toc526413122"></a><a
name="_Toc526414569"></a><a name="_Toc526351217"></a><a name="_Toc526406292"></a><a
name="_Toc526407982"></a><a name="_Toc526409670"></a><a name="_Toc526413139"></a><a
name="_Toc526414586"></a><a name="_Toc526351219"></a><a name="_Toc526406294"></a><a
name="_Toc526407984"></a><a name="_Toc526409672"></a><a name="_Toc526413141"></a><a
name="_Toc526414588"></a><a name="_Toc526351220"></a><a name="_Toc526406295"></a><a
name="_Toc526407985"></a><a name="_Toc526409673"></a><a name="_Toc526413142"></a><a
name="_Toc526414589"></a><a name="_Toc526351222"></a><a name="_Toc526406297"></a><a
name="_Toc526407987"></a><a name="_Toc526409675"></a><a name="_Toc526413144"></a><a
name="_Toc526414591"></a><a name="_Toc526351223"></a><a name="_Toc526406298"></a><a
name="_Toc526407988"></a><a name="_Toc526409676"></a><a name="_Toc526413145"></a><a
name="_Toc526414592"></a><a name="_Toc526351224"></a><a name="_Toc526406299"></a><a
name="_Toc526407989"></a><a name="_Toc526409677"></a><a name="_Toc526413146"></a><a
name="_Toc526414593"></a><a name="_Toc526351225"></a><a name="_Toc526406300"></a><a
name="_Toc526407990"></a><a name="_Toc526409678"></a><a name="_Toc526413147"></a><a
name="_Toc526414594"></a><a name="_Toc526351226"></a><a name="_Toc526406301"></a><a
name="_Toc526407991"></a><a name="_Toc526409679"></a><a name="_Toc526413148"></a><a
name="_Toc526414595"></a><a name="_Toc526351228"></a><a name="_Toc526406303"></a><a
name="_Toc526407993"></a><a name="_Toc526409681"></a><a name="_Toc526413150"></a><a
name="_Toc526414597"></a><a name="_Toc526351237"></a><a name="_Toc526406312"></a><a
name="_Toc526408002"></a><a name="_Toc526409690"></a><a name="_Toc526413159"></a><a
name="_Toc526414606"></a><a name="_Toc526351238"></a><a name="_Toc526406313"></a><a
name="_Toc526408003"></a><a name="_Toc526409691"></a><a name="_Toc526413160"></a><a
name="_Toc526414607"></a><a name="_Toc526351239"></a><a name="_Toc526406314"></a><a
name="_Toc526408004"></a><a name="_Toc526409692"></a><a name="_Toc526413161"></a><a
name="_Toc526414608"></a><a name="_Toc526351240"></a><a name="_Toc526406315"></a><a
name="_Toc526408005"></a><a name="_Toc526409693"></a><a name="_Toc526413162"></a><a
name="_Toc526414609"></a><a name="_Toc526351241"></a><a name="_Toc526406316"></a><a
name="_Toc526408006"></a><a name="_Toc526409694"></a><a name="_Toc526413163"></a><a
name="_Toc526414610"></a><a name="_Toc526351243"></a><a name="_Toc526406318"></a><a
name="_Toc526408008"></a><a name="_Toc526409696"></a><a name="_Toc526413165"></a><a
name="_Toc526414612"></a><a name="_Toc526351252"></a><a name="_Toc526406327"></a><a
name="_Toc526408017"></a><a name="_Toc526409705"></a><a name="_Toc526413174"></a><a
name="_Toc526414621"></a><a name="_Toc526351253"></a><a name="_Toc526406328"></a><a
name="_Toc526408018"></a><a name="_Toc526409706"></a><a name="_Toc526413175"></a><a
name="_Toc526414622"></a><a name="_Toc526351254"></a><a name="_Toc526406329"></a><a
name="_Toc526408019"></a><a name="_Toc526409707"></a><a name="_Toc526413176"></a><a
name="_Toc526414623"></a><a name="_Toc526351255"></a><a name="_Toc526406330"></a><a
name="_Toc526408020"></a><a name="_Toc526409708"></a><a name="_Toc526413177"></a><a
name="_Toc526414624"></a><a name="_Toc526351256"></a><a name="_Toc526406331"></a><a
name="_Toc526408021"></a><a name="_Toc526409709"></a><a name="_Toc526413178"></a><a
name="_Toc526414625"></a><a name="_Toc526351257"></a><a name="_Toc526406332"></a><a
name="_Toc526408022"></a><a name="_Toc526409710"></a><a name="_Toc526413179"></a><a
name="_Toc526414626"></a><a name="_Toc526351259"></a><a name="_Toc526406334"></a><a
name="_Toc526408024"></a><a name="_Toc526409712"></a><a name="_Toc526413181"></a><a
name="_Toc526414628"></a><a name="_Toc526351268"></a><a name="_Toc526406343"></a><a
name="_Toc526408033"></a><a name="_Toc526409721"></a><a name="_Toc526413190"></a><a
name="_Toc526414637"></a><a name="_Toc526351269"></a><a name="_Toc526406344"></a><a
name="_Toc526408034"></a><a name="_Toc526409722"></a><a name="_Toc526413191"></a><a
name="_Toc526414638"></a><a name="_Toc526351270"></a><a name="_Toc526406345"></a><a
name="_Toc526408035"></a><a name="_Toc526409723"></a><a name="_Toc526413192"></a><a
name="_Toc526414639"></a><a name="_Toc526351271"></a><a name="_Toc526406346"></a><a
name="_Toc526408036"></a><a name="_Toc526409724"></a><a name="_Toc526413193"></a><a
name="_Toc526414640"></a><a name="_Toc526351272"></a><a name="_Toc526406347"></a><a
name="_Toc526408037"></a><a name="_Toc526409725"></a><a name="_Toc526413194"></a><a
name="_Toc526414641"></a><a name="_Toc526351273"></a><a name="_Toc526406348"></a><a
name="_Toc526408038"></a><a name="_Toc526409726"></a><a name="_Toc526413195"></a><a
name="_Toc526414642"></a><a name="_Toc526351275"></a><a name="_Toc526406350"></a><a
name="_Toc526408040"></a><a name="_Toc526409728"></a><a name="_Toc526413197"></a><a
name="_Toc526414644"></a><a name="_Toc526351284"></a><a name="_Toc526406359"></a><a
name="_Toc526408049"></a><a name="_Toc526409737"></a><a name="_Toc526413206"></a><a
name="_Toc526414653"></a><a name="_Toc526351285"></a><a name="_Toc526406360"></a><a
name="_Toc526408050"></a><a name="_Toc526409738"></a><a name="_Toc526413207"></a><a
name="_Toc526414654"></a><a name="_Toc526351286"></a><a name="_Toc526406361"></a><a
name="_Toc526408051"></a><a name="_Toc526409739"></a><a name="_Toc526413208"></a><a
name="_Toc526414655"></a><a name="_Toc526351287"></a><a name="_Toc526406362"></a><a
name="_Toc526408052"></a><a name="_Toc526409740"></a><a name="_Toc526413209"></a><a
name="_Toc526414656"></a><a name="_Toc526351288"></a><a name="_Toc526406363"></a><a
name="_Toc526408053"></a><a name="_Toc526409741"></a><a name="_Toc526413210"></a><a
name="_Toc526414657"></a><a name="_Toc526351290"></a><a name="_Toc526406365"></a><a
name="_Toc526408055"></a><a name="_Toc526409743"></a><a name="_Toc526413212"></a><a
name="_Toc526414659"></a><a name="_Toc526351299"></a><a name="_Toc526406374"></a><a
name="_Toc526408064"></a><a name="_Toc526409752"></a><a name="_Toc526413221"></a><a
name="_Toc526414668"></a><a name="_Toc526351300"></a><a name="_Toc526406375"></a><a
name="_Toc526408065"></a><a name="_Toc526409753"></a><a name="_Toc526413222"></a><a
name="_Toc526414669"></a><a name="_Toc526351301"></a><a name="_Toc526406376"></a><a
name="_Toc526408066"></a><a name="_Toc526409754"></a><a name="_Toc526413223"></a><a
name="_Toc526414670"></a><a name="_Toc526351302"></a><a name="_Toc526406377"></a><a
name="_Toc526408067"></a><a name="_Toc526409755"></a><a name="_Toc526413224"></a><a
name="_Toc526414671"></a><a name="_Toc526351303"></a><a name="_Toc526406378"></a><a
name="_Toc526408068"></a><a name="_Toc526409756"></a><a name="_Toc526413225"></a><a
name="_Toc526414672"></a><a name="_Toc526351305"></a><a name="_Toc526406380"></a><a
name="_Toc526408070"></a><a name="_Toc526409758"></a><a name="_Toc526413227"></a><a
name="_Toc526414674"></a><a name="_Toc526351314"></a><a name="_Toc526406389"></a><a
name="_Toc526408079"></a><a name="_Toc526409767"></a><a name="_Toc526413236"></a><a
name="_Toc526414683"></a><a name="_Toc526351315"></a><a name="_Toc526406390"></a><a
name="_Toc526408080"></a><a name="_Toc526409768"></a><a name="_Toc526413237"></a><a
name="_Toc526414684"></a><a name="_Toc526351316"></a><a name="_Toc526406391"></a><a
name="_Toc526408081"></a><a name="_Toc526409769"></a><a name="_Toc526413238"></a><a
name="_Toc526414685"></a><a name="_Toc526351317"></a><a name="_Toc526406392"></a><a
name="_Toc526408082"></a><a name="_Toc526409770"></a><a name="_Toc526413239"></a><a
name="_Toc526414686"></a><a name="_Toc526351318"></a><a name="_Toc526406393"></a><a
name="_Toc526408083"></a><a name="_Toc526409771"></a><a name="_Toc526413240"></a><a
name="_Toc526414687"></a><a name="_Toc526351320"></a><a name="_Toc526406395"></a><a
name="_Toc526408085"></a><a name="_Toc526409773"></a><a name="_Toc526413242"></a><a
name="_Toc526414689"></a><a name="_Toc526351329"></a><a name="_Toc526406404"></a><a
name="_Toc526408094"></a><a name="_Toc526409782"></a><a name="_Toc526413251"></a><a
name="_Toc526414698"></a><a name="_Toc526351330"></a><a name="_Toc526406405"></a><a
name="_Toc526408095"></a><a name="_Toc526409783"></a><a name="_Toc526413252"></a><a
name="_Toc526414699"></a><a name="_Toc526351331"></a><a name="_Toc526406406"></a><a
name="_Toc526408096"></a><a name="_Toc526409784"></a><a name="_Toc526413253"></a><a
name="_Toc526414700"></a><a name="_Toc526351332"></a><a name="_Toc526406407"></a><a
name="_Toc526408097"></a><a name="_Toc526409785"></a><a name="_Toc526413254"></a><a
name="_Toc526414701"></a><a name="_Toc526351333"></a><a name="_Toc526406408"></a><a
name="_Toc526408098"></a><a name="_Toc526409786"></a><a name="_Toc526413255"></a><a
name="_Toc526414702"></a><a name="_Toc526351335"></a><a name="_Toc526406410"></a><a
name="_Toc526408100"></a><a name="_Toc526409788"></a><a name="_Toc526413257"></a><a
name="_Toc526414704"></a><a name="_Toc526351345"></a><a name="_Toc526406420"></a><a
name="_Toc526408110"></a><a name="_Toc526409798"></a><a name="_Toc526413267"></a><a
name="_Toc526414714"></a><a name="_Toc526351346"></a><a name="_Toc526406421"></a><a
name="_Toc526408111"></a><a name="_Toc526409799"></a><a name="_Toc526413268"></a><a
name="_Toc526414715"></a><a name="_Toc526351347"></a><a name="_Toc526406422"></a><a
name="_Toc526408112"></a><a name="_Toc526409800"></a><a name="_Toc526413269"></a><a
name="_Toc526414716"></a><a name="_Toc526351348"></a><a name="_Toc526406423"></a><a
name="_Toc526408113"></a><a name="_Toc526409801"></a><a name="_Toc526413270"></a><a
name="_Toc526414717"></a><a name="_Toc526351349"></a><a name="_Toc526406424"></a><a
name="_Toc526408114"></a><a name="_Toc526409802"></a><a name="_Toc526413271"></a><a
name="_Toc526414718"></a><a name="_Toc526351351"></a><a name="_Toc526406426"></a><a
name="_Toc526408116"></a><a name="_Toc526409804"></a><a name="_Toc526413273"></a><a
name="_Toc526414720"></a><a name="_Toc526351360"></a><a name="_Toc526406435"></a><a
name="_Toc526408125"></a><a name="_Toc526409813"></a><a name="_Toc526413282"></a><a
name="_Toc526414729"></a><a name="_Toc526351361"></a><a name="_Toc526406436"></a><a
name="_Toc526408126"></a><a name="_Toc526409814"></a><a name="_Toc526413283"></a><a
name="_Toc526414730"></a><a name="_Toc526351362"></a><a name="_Toc526406437"></a><a
name="_Toc526408127"></a><a name="_Toc526409815"></a><a name="_Toc526413284"></a><a
name="_Toc526414731"></a><a name="_Toc526351363"></a><a name="_Toc526406438"></a><a
name="_Toc526408128"></a><a name="_Toc526409816"></a><a name="_Toc526413285"></a><a
name="_Toc526414732"></a><a name="_Toc526351364"></a><a name="_Toc526406439"></a><a
name="_Toc526408129"></a><a name="_Toc526409817"></a><a name="_Toc526413286"></a><a
name="_Toc526414733"></a><a name="_Toc526351366"></a><a name="_Toc526406441"></a><a
name="_Toc526408131"></a><a name="_Toc526409819"></a><a name="_Toc526413288"></a><a
name="_Toc526414735"></a><a name="_Toc526351375"></a><a name="_Toc526406450"></a><a
name="_Toc526408140"></a><a name="_Toc526409828"></a><a name="_Toc526413297"></a><a
name="_Toc526414744"></a><a name="_Toc526351376"></a><a name="_Toc526406451"></a><a
name="_Toc526408141"></a><a name="_Toc526409829"></a><a name="_Toc526413298"></a><a
name="_Toc526414745"></a><a name="_Toc526351377"></a><a name="_Toc526406452"></a><a
name="_Toc526408142"></a><a name="_Toc526409830"></a><a name="_Toc526413299"></a><a
name="_Toc526414746"></a><a name="_Toc526351378"></a><a name="_Toc526406453"></a><a
name="_Toc526408143"></a><a name="_Toc526409831"></a><a name="_Toc526413300"></a><a
name="_Toc526414747"></a><a name="_Toc526351379"></a><a name="_Toc526406454"></a><a
name="_Toc526408144"></a><a name="_Toc526409832"></a><a name="_Toc526413301"></a><a
name="_Toc526414748"></a><a name="_Toc526351381"></a><a name="_Toc526406456"></a><a
name="_Toc526408146"></a><a name="_Toc526409834"></a><a name="_Toc526413303"></a><a
name="_Toc526414750"></a><a name="_Toc526351391"></a><a name="_Toc526406466"></a><a
name="_Toc526408156"></a><a name="_Toc526409844"></a><a name="_Toc526413313"></a><a
name="_Toc526414760"></a><a name="_Toc526351392"></a><a name="_Toc526406467"></a><a
name="_Toc526408157"></a><a name="_Toc526409845"></a><a name="_Toc526413314"></a><a
name="_Toc526414761"></a><a name="_Toc526351393"></a><a name="_Toc526406468"></a><a
name="_Toc526408158"></a><a name="_Toc526409846"></a><a name="_Toc526413315"></a><a
name="_Toc526414762"></a><a name="_Toc526351394"></a><a name="_Toc526406469"></a><a
name="_Toc526408159"></a><a name="_Toc526409847"></a><a name="_Toc526413316"></a><a
name="_Toc526414763"></a><a name="_Toc526351395"></a><a name="_Toc526406470"></a><a
name="_Toc526408160"></a><a name="_Toc526409848"></a><a name="_Toc526413317"></a><a
name="_Toc526414764"></a><a name="_Toc526351397"></a><a name="_Toc526406472"></a><a
name="_Toc526408162"></a><a name="_Toc526409850"></a><a name="_Toc526413319"></a><a
name="_Toc526414766"></a><a name="_Toc526351399"></a><a name="_Toc526406474"></a><a
name="_Toc526408164"></a><a name="_Toc526409852"></a><a name="_Toc526413321"></a><a
name="_Toc526414768"></a><a name="_Toc526351406"></a><a name="_Toc526406481"></a><a
name="_Toc526408171"></a><a name="_Toc526409859"></a><a name="_Toc526413328"></a><a
name="_Toc526414775"></a><a name="_Toc526351407"></a><a name="_Toc526406482"></a><a
name="_Toc526408172"></a><a name="_Toc526409860"></a><a name="_Toc526413329"></a><a
name="_Toc526414776"></a><a name="_Toc526351408"></a><a name="_Toc526406483"></a><a
name="_Toc526408173"></a><a name="_Toc526409861"></a><a name="_Toc526413330"></a><a
name="_Toc526414777"></a><a name="_Toc526351409"></a><a name="_Toc526406484"></a><a
name="_Toc526408174"></a><a name="_Toc526409862"></a><a name="_Toc526413331"></a><a
name="_Toc526414778"></a><span lang=X-NONE style='color:#0000CC'>6<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE style='color:#0000CC'>Edge Smoothing (ES)</span></h1>

<p class=Body0 style='text-align:justify;text-justify:inter-ideograph'><a
name="OLE_LINK20"></a><a name="OLE_LINK19"><span lang=EN-US style='font-size:
12.0pt;line-height:150%;font-family:"Calibri",sans-serif'>This module is edge
smoothing. The main function is to eliminate aliasing in the picture to improve
the smoothness of the picture.</span></a></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570757"><span
lang=EN-US>6.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Overview</span></a></h2>

<p class=MsoNormal><a name="OLE_LINK22"></a><a name="OLE_LINK21"><span
lang=EN-US>The characteristics of this algorithm are to effectively smooth the
edges of the input image, correct the jaggedness in the edge area of the input
image, and avoid the Sharpen module to enhance the degree of jaggedness in the
image edge again. The algorithm divides the input image into edge area and
detail area, calculates the direction of the edge on the edge area, and then
performs LPF convolution adaptively along the edge direction to smooth the edge
of the image. The Edge Mask can be adjusted to avoid high-frequency areas being
blurred due to smoothing.</span></a></p>

<p class=MsoNormal><span lang=EN-US>Please refer to the following figure for
the main process:</span></p>

<p class=MsoNormal align=center style='text-align:center'><span lang=EN-US><img
width=486 height=123 id="圖片 402"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image067.png"></span></p>

<p class=MsoNormal align=center style='text-align:center'><span lang=EN-US>&nbsp;</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570758"><span
lang=EN-US>6.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Parameter Description</span></a></h2>

<p class=MsoCaption><span lang=EN-US>Table 6&#8209;1 ES Parameter List</span></p>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=652
 style='width:489.05pt;margin-left:5.4pt;border-collapse:collapse'>
 <tr>
  <td width=195 valign=top style='width:146.6pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:72.05pt;text-align:center;
  text-indent:-72.05pt'><b><span lang=EN-US style='font-size:11.0pt'>Parameter</span></b></p>
  </td>
  <td width=89 valign=top style='width:66.4pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Range</span></b></p>
  </td>
  <td width=100 valign=top style='width:75.0pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Def</span></b></p>
  </td>
  <td width=268 valign=top style='width:201.05pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"新細明體",serif'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=195 style='width:146.6pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_smooth_en</span></i></b></p>
  </td>
  <td width=89 style='width:66.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=100 style='width:75.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=268 valign=top style='width:201.05pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;font-family:"新細明體",serif'>Edge smooth enable</span></p>
  </td>
 </tr>
 <tr>
  <td width=195 style='width:146.6pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_smooth_y_edeng_th_lo</span></i></b></p>
  </td>
  <td width=89 style='width:66.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~255</span></p>
  </td>
  <td width=100 style='width:75.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>10</span></p>
  </td>
  <td width=268 valign=top style='width:201.05pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;font-family:"新細明體",serif'>Adjust the strength
  threshold of detail areas in the picture</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;font-family:"新細明體",serif'>Please refer to the
  advanced instructions</span></p>
  </td>
 </tr>
 <tr>
  <td width=195 style='width:146.6pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_smooth_y_edeng_th_hi</span></i></b></p>
  </td>
  <td width=89 style='width:66.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~255</span></p>
  </td>
  <td width=100 style='width:75.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>70</span></p>
  </td>
  <td width=268 valign=top style='width:201.05pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;font-family:"新細明體",serif'>Adjust the strength
  threshold of the edge area in the picture</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"新細明體",serif'>Please
  refer to the advanced instructions</span></p>
  </td>
 </tr>
 <tr>
  <td width=195 style='width:146.6pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_smooth_y_ew_lo</span></i></b></p>
  </td>
  <td width=89 style='width:66.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~255</span></p>
  </td>
  <td width=100 style='width:75.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>2</span></p>
  </td>
  <td width=268 valign=top style='width:201.05pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;font-family:"新細明體",serif'>Adjust the smoothing strength
  weight of detail areas in the picture</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;font-family:"新細明體",serif'>Please refer to the
  advanced instructions</span></p>
  </td>
 </tr>
 <tr>
  <td width=195 style='width:146.6pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_smooth_y_ew_hi</span></i></b></p>
  </td>
  <td width=89 style='width:66.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~255</span></p>
  </td>
  <td width=100 style='width:75.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>32</span></p>
  </td>
  <td width=268 valign=top style='width:201.05pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"新細明體",serif'>Adjust
  the suppression threshold for the smoothing of high-frequency areas in the
  picture. The larger the value, the easier it is to determine and smooth the high-frequency
  area. Therefore, the larger the value, the smoother the high-frequency area,
  and the smaller the value, the clearer the high-frequency area</span></p>
  </td>
 </tr>
 <tr>
  <td width=195 style='width:146.6pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_smooth_y_edi_th</span></i></b></p>
  </td>
  <td width=89 style='width:66.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~63</span></p>
  </td>
  <td width=100 style='width:75.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>31</span></p>
  </td>
  <td width=268 valign=top style='width:201.05pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;font-family:"新細明體",serif'>Suppresses the strength of
  smoothing in the high-frequency region. The larger the value, the stronger
  the smoothing in the high-frequency region.</span></p>
  </td>
 </tr>
 <tr>
  <td width=195 style='width:146.6pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>edge_smooth_y_ds_str</span></i></b></p>
  </td>
  <td width=89 style='width:66.4pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~7</span></p>
  </td>
  <td width=100 style='width:75.0pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>5</span></p>
  </td>
  <td width=268 valign=top style='width:201.05pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;font-family:"新細明體",serif'>Adjust the strength of the
  smoothing filter in the picture. The larger the value, the stronger the
  smoothing degree.</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>Advance description:</span></b></p>

<p class=MsoListParagraph style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:10.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:11.0pt'>edge_smooth_y_edeng_th_lo</span></i></b><b><i><span
lang=EN-US style='font-size:11.0pt'>, </span></i></b><b><i><span lang=EN-US
style='font-size:11.0pt'>edge_smooth_y_edeng_th_hi, edge_smooth_y_ew_lo,
edge_smooth_y_ew_hi</span></i></b><b><i><span lang=EN-US style='font-size:11.0pt'>:
</span></i></b><span lang=EN-US style='font-size:11.0pt;font-family:"Arial",sans-serif'>The
strength of edge smooth is controlled by the edge energy intensity of the input
image, where edge_smooth_y_edeng_th_hi and edge_smooth_y_edeng_th_lo are the
ranges that set the edge area and the detail area, and edge_smooth_y_ew_hi and
edge_smooth_y_ew_lo set the smoothness strength of the edge area and detail
area. The larger the number, the stronger of the smoothness. </span></p>

<p class=MsoListParagraph style='margin-left:24.0pt'><span lang=EN-US
style='font-size:11.0pt;font-family:"Arial",sans-serif'>The relationship
between the edge area and the detail area is a continuous linear change, and
the corresponding relationship is shown in the following figure:</span></p>

<p class=MsoCaption align=center style='text-align:center'><span lang=EN-US
style='font-family:"Arial",sans-serif'><img width=499 height=256 id="圖片 403"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image068.png"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570759"><span
lang=EN-US>6.3<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Setting Interface</span></a></h2>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570760"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>6.3.1<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Proc</span></a></h3>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/</span><span lang=X-NONE>es</span><span
lang=X-NONE>/param</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read all edge smoothing parameters of the current camera
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : Not support.</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>Read : cat /proc/videograph/vpe/es/param</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=223
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image069.png"
alt="fd(0x00000000)&#13;&#10;edge_smooth_en              = edge_smooth_en           &#13;&#10;edge_smooth_out_sel         = edge_smooth_out_sel      &#13;&#10;edge_smooth_y_edeng_th_lo   = edge_smooth_y_edeng_th_lo&#13;&#10;edge_smooth_y_edeng_th_hi   = edge_smooth_y_edeng_th_hi&#13;&#10;edge_smooth_y_ew_lo         = edge_smooth_y_ew_lo      &#13;&#10;edge_smooth_y_ew_hi         = edge_smooth_y_ew_hi      &#13;&#10;edge_smooth_y_edi_th        = edge_smooth_y_edi_th     &#13;&#10;edge_smooth_y_ds_str         = edge_smooth_y_ds_str&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/</span><span lang=X-NONE>es</span><span
lang=X-NONE>/</span><span lang=X-NONE>edge_smooth_en</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Set the edge smooth switch of the current camera channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:42.85pt'>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt'>echo [edge_smooth_en (0~1)] &gt;
  /proc/videograph/vpe/es/edge_smooth_en</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>edge_smooth_en</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/</span><span lang=X-NONE>es</span><span
lang=X-NONE>/</span><span lang=X-NONE>edge_smooth_out_sel</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Set the edge smooth debugging switch of the current camera
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:42.85pt'>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt'>echo [edge_smooth_out_sel (0~1)] &gt;
  /proc/videograph/vpe/es/edge_smooth_out_sel</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>edge_smooth_out_sel</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/es/edge_smooth_out_sel</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=108
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image070.png"
alt="Command : &#13;&#10;echo [edge_smooth_out_sel (0~1)] &gt; /proc/videograph/vpe/es/edge_smooth_out_sel&#13;&#10;===============================================================&#13;&#10;edge_smooth_out_sel  = edge_smooth_out_sel&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/</span><span lang=X-NONE>es</span><span
lang=X-NONE>/</span><span lang=X-NONE>edge_smooth_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Set the edge smooth related threshold of the current camera
channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:42.85pt'>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt'>echo [y_edeng_th_lo (0~255)] [y_edeng_th_hi (0~255)]
  [y_ew_lo (0~255)] [y_ew_hi (0~255)] &gt;
  /proc/videograph/vpe/es/edge_smooth_th</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>edge_smooth_y_edeng_th_l</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>edge_smooth_y_edeng_th_hi</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>edge_smooth_y_ew_lo</span></b></p>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>edge_smooth_y_ew_hi</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/es/edge_smooth_th</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=204
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image071.png"
alt="Command : &#13;&#10;echo [y_edeng_th_lo (0~255)] [y_edeng_th_hi (0~255)] [y_ew_lo (0~255)] [y_ew_hi (0~255)] &gt; /proc/videograph/vpe/es/edge_smooth_th ===============================================================&#13;&#10;y_edeng_th_l = edge_smooth_y_edeng_th_l&#13;&#10;y_edeng_th_hi = edge_smooth_y_edeng_th_hi&#13;&#10;y_ew_lo = edge_smooth_y_ew_lo&#13;&#10;y_ew_hi = edge_smooth_y_ew_hi&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/</span><span lang=X-NONE>es</span><span
lang=X-NONE>/</span><span lang=X-NONE>edge_smooth_y_edi_th</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><span lang=X-NONE style='font-size:
11.0pt'>Set the edge smooth mask related parameters of the current camera channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:42.85pt'>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt'>echo [edge_smooth_y_edi_th (0~63)] &gt;
  /proc/videograph/vpe/es/edge_smooth_y_edi_th</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>edge_smooth_y_edi_th</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/es/edge_smooth_y_edi_th</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=108
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image072.png"
alt="Command : &#13;&#10;echo [edge_smooth_y_edi_th (0~63)] &gt; /proc/videograph/vpe/es/edge_smooth_ds_str&#13;&#10;===============================================================&#13;&#10;edge_smooth_y_edi_th = edge_smooth_y_edi_th&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/</span><span lang=X-NONE>es</span><span
lang=X-NONE>/</span><span lang=X-NONE>edge_smooth_y_ds_str</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Sets the filter strength of the edge smooth of the
current camera channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:42.85pt'>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt'>echo [edge_smooth_y_ds_str (0~7)] &gt;
  /proc/videograph/vpe/es/edge_smooth_y_ds_str</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt;height:42.85pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt'>edge_smooth_y_ds_str</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/es/edge_smooth_y_ds_str</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=108
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image073.png"
alt="Command : &#13;&#10;echo [edge_smooth_y_ds_str (0~7)] &gt; /proc/videograph/vpe/es/edge_smooth_y_ds_str&#13;&#10;===============================================================&#13;&#10;edge_smooth_y_ds_str = edge_smooth_y_ds_str&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE>&nbsp;</span></p>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570761"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>6.3.2<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Vendor API</span></a></h3>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Get and set the edge
smooth parameters corresponding to current path_id.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span><b><span
lang=X-NONE style='font-size:11.0pt'>Get</span></b><b><span style='font-size:
11.0pt;font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_get(HD_PATH_ID path_id, VENDOR_VIDEO_EDGE_SMOOTH,
</span><span lang=X-NONE style='font-size:11.0pt'>VENDOR_VIDEO_PARAM_SHARP</span><span
lang=X-NONE style='font-size:14.0pt'> </span><span lang=X-NONE
style='font-size:11.0pt'>*p_param);</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>Set</b></span><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_set(HD_PATH_ID path_id, VENDOR_VIDEO_EDGE_SMOOTH,
</span><span lang=X-NONE style='font-size:11.0pt'>VENDOR_VIDEO_PARAM_SHARP</span><span
lang=X-NONE style='font-size:11.0pt'> *p_param);</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Definition]</span></b></p>

<p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt;font-family:
"Calibri",sans-serif'><img width=641 height=180
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image074.png"
alt="typedef struct _VENDOR_VIDEO_PARAM_EDGE_SMOOTH {&#13;&#10;	UINT8 edge_smooth_en; 			// Edge smooth enable, ON/OFF&#13;&#10;	UINT8 edge_smooth_y_edeng_th_lo;	// luma layer edge energy low threshold, 0~255&#13;&#10;	UINT8 edge_smooth_y_edeng_th_hi;	// luma layer edge energy high threshold, 0~255&#13;&#10;	UINT8 edge_smooth_y_ew_lo;		// luma layer edge weighting curve low value, 0~32&#13;&#10;	UINT8 edge_smooth_y_ew_hi;		// luma layer edge weighting curve high value, 0~32&#13;&#10;	UINT8 edge_smooth_y_edi_th;		// luma layer edge mask threshold, 0~63&#13;&#10;	UINT8 edge_smooth_y_ds_str;       // luma layer edge directed smoothing filter strength, 0 ~ 7&#13;&#10;} VENDOR_VIDEO_PARAM_EDGE_SMOOTH;&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<b><span lang=X-NONE style='font-size:20.0pt;line-height:300%;font-family:"Arial",sans-serif'><br
clear=all style='page-break-before:always'>
</span></b>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc393462387"></a><a
name="_Toc100570762"><span lang=X-NONE>7<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Scaling (SCA)</span></a></h1>

<p class=MsoNormal><span lang=EN-US>Inupt/Output low pass filter process with
different resolution. The recommend maximum scaling down ratio is 8, and the
recommend maximum scaling up ratio is 8. </span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570763"><span
lang=EN-US>7.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Overview</span></a></h2>

<p class=MsoNormal><span lang=EN-US>This is image scaling module, the major
concept is interpolation and smooth process.</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570764"><span
lang=EN-US>7.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Parameter Description</span></a></h2>

<p class=MsoCaption><a name="_Toc100570784"><span lang=EN-US>Table 7&#8209;</span></a><span
lang=EN-US>1</span><span lang=EN-US> SCA Parameter List</span></p>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=652
 style='width:489.05pt;margin-left:5.4pt;border-collapse:collapse'>
 <tr>
  <td width=158 valign=top style='width:118.5pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:72.05pt;text-align:center;
  text-indent:-72.05pt'><b><span lang=EN-US style='font-size:11.0pt'>Parameter</span></b></p>
  </td>
  <td width=93 valign=top style='width:69.95pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Range</span></b></p>
  </td>
  <td width=108 valign=top style='width:81.25pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Def</span></b></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"新細明體",serif'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=158 style='width:118.5pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>sca_y_luma_algo_en</span></i></b></p>
  </td>
  <td width=93 style='width:69.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~3</span></p>
  </td>
  <td width=108 style='width:81.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Algorithm select for vertical luma scaler.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0: judge by HW algorithm</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>1: select the nearest point on the left side</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>2: select the left side point and perform low pass
  filter process</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>3:
  the same as option 0</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>It
  is recommend to set 0.</span></p>
  </td>
 </tr>
 <tr>
  <td width=158 style='width:118.5pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>sca_x_luma_algo_en</span></i></b></p>
  </td>
  <td width=93 style='width:69.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~3</span></p>
  </td>
  <td width=108 style='width:81.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Algorithm select for horizontal luma scaler.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0: judge by HW algorithm</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>1: select the nearest point on the left side</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>2: select the left side point and perform low pass
  filter process</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>3:
  the same as option 0</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set 0.</span></p>
  </td>
 </tr>
 <tr>
  <td width=158 style='width:118.5pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>sca_y_chroma_algo_en</span></i></b></p>
  </td>
  <td width=93 style='width:69.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~3</span></p>
  </td>
  <td width=108 style='width:81.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Algorithm select for vertical chroma scaler.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0: judge by HW algorithm</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>1: select the nearest point on the left side</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>2: bilinear interpolation</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>3:
  average</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set 0.</span></p>
  </td>
 </tr>
 <tr>
  <td width=158 style='width:118.5pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>sca_x_chroma_algo_en</span></i></b></p>
  </td>
  <td width=93 style='width:69.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~3</span></p>
  </td>
  <td width=108 style='width:81.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Algorithm select for horizontal chroma scaler.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0: judge by HW algorithm</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>1: select the nearest point on the left side</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>2: bilinear interpolation</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>3:
  average</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set 0.</span></p>
  </td>
 </tr>
 <tr>
  <td width=158 style='width:118.5pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>sca_map_sel</span></i></b></p>
  </td>
  <td width=93 style='width:69.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=108 style='width:81.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Select scaler source mapping format. </span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0:
  without 0.5 pixel distance shift(start from the 0th pixel of image image)</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>1:
  with 0.5 pixel distance shift(start from the 0.5th pixel of image image)</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>If set to 1, when the size of input image and output
  image is the same or the size is multiple of 2, the scaling performance of
  output image will similar to perform low pass filter.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>It
  is recommend to set 0.</span></p>
  </td>
 </tr>
 <tr>
  <td width=158 style='width:118.5pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>sca_ceffH_0~3</span></i></b></p>
  </td>
  <td width=93 style='width:69.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>-128~127</span></p>
  </td>
  <td width=108 style='width:81.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>[0, 0, 0, 64]</span></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>LPF coefficient in horizontal direction.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span style='font-size:
  11.0pt;font-family:"新細明體",serif'>※</span><span lang=EN-US style='font-size:
  11.0pt'>The software limit range is between -128~127, to reduce memory usage.</span></p>
  </td>
 </tr>
 <tr>
  <td width=158 style='width:118.5pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>sca_ceffv_0~3</span></i></b></p>
  </td>
  <td width=93 style='width:69.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>-128~127</span></p>
  </td>
  <td width=108 style='width:81.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>[0, 0, 0, 64]</span></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>LPF coefficient in vertical direction.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Please
  refer to advance description.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span style='font-size:
  11.0pt;font-family:"新細明體",serif'>※</span><span lang=EN-US style='font-size:
  11.0pt'>The software limit range is between -128~127, to reduce memory usage.</span></p>
  </td>
 </tr>
 <tr>
  <td width=158 style='width:118.5pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>des_drt</span></i></b></p>
  </td>
  <td width=93 style='width:69.95pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0, 2,3</span></p>
  </td>
  <td width=108 style='width:81.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=292 valign=top style='width:219.35pt;border:none;border-bottom:
  solid #1D1DFF 1.0pt;background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>YUV domain transform</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0:
  bypass</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>2:
  PC level to TV level (Y: 16~235 / C:16~240)</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>3:
  TV level to PC level&nbsp; (Y: 0~235 C:0~255)</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>255:
  decide by job parameter of AP rather than driver<br>
  (default value is 255, other settings are used for debug)</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>Advance description:</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:10.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>sca_ceffH_0~3,
sca_ceffV_0~3: </span></i></b><span lang=EN-US style='font-size:10.0pt'>LPF
coefficients in horizontal direction and vertical direction. User can adjust
LPF coefficients to fine tune sawtooth phenomenon in oblique line caused by
scaling. </span></p>

<p class=MsoCaption><span lang=EN-US style='font-family:"Arial",sans-serif'>&nbsp;<a
name="_Toc100570785">Table 7&#8209;</a></span><span
lang=EN-US style='font-family:"Arial",sans-serif'>2</span><span lang=EN-US
style='font-family:"Arial",sans-serif'> Scaler Low pass filter default
parameter list</span></p>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=520
 style='width:389.8pt;margin-left:21.35pt;border-collapse:collapse'>
 <tr>
  <td width=139 valign=top style='width:104.55pt;border-top:solid #1D1DFF 1.5pt;
  border-left:solid windowtext 1.0pt;border-bottom:solid #1D1DFF 1.5pt;
  border-right:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:72.05pt;text-align:center;
  text-indent:-72.05pt'><b><span lang=EN-US style='font-size:9.0pt;font-family:
  "Arial Narrow",sans-serif'>Scaling Ratio (R)</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:solid #1D1DFF 1.5pt;
  border-left:solid windowtext 1.0pt;border-bottom:solid #1D1DFF 1.5pt;
  border-right:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial Narrow",sans-serif'>HCoef0</span></b></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial Narrow",sans-serif'>HCoef1</span></b></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial Narrow",sans-serif'>HCoef2</span></b></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:solid windowtext 1.0pt;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial Narrow",sans-serif'>HCoef3</span></b></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial Narrow",sans-serif'>VCoef0</span></b></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial Narrow",sans-serif'>VCoef1</span></b></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial Narrow",sans-serif'>VCoef2</span></b></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:solid windowtext 1.0pt;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial Narrow",sans-serif'>VCoef3</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span style='font-size:
  8.0pt;font-family:"新細明體",serif'>≧</span></b><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'> 1x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>64</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>64</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>1 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 1.25x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>3</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>58</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>3</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>58</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>1.25 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 1.5x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>7</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>50</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>7</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>50</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>1.5 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 1.75x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>11</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>42</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>11</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>42</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>1.75 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 2x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>1</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>13</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>36</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>1</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>13</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>36</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>2 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 2.25x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>1</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>32</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>1</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>32</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>2.25 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 2.5x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>2</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>30</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>2</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>30</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>2.5 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 2.75x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>3</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>28</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>3</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>28</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>2.75 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 3x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>4</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>26</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>0</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>4</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>26</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>3 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 3.25x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>1</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>4</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>24</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>1</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>4</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>24</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>3.25 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 3.5x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>1</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>5</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>22</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>1</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>5</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>15</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>22</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>3.5 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 3.75x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>2</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>7</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>14</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>18</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>2</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>7</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>14</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>18</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>3.75 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 4x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>3</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>8</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>13</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>16</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>3</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>8</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>13</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>16</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>4 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 5x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>4</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>8</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>13</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>14</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>4</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>8</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>13</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>14</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>5 &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 6x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>4</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>9</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>12</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>14</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>4</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>9</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>12</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>14</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>6x &lt; R </span></b><b><span
  style='font-size:8.0pt;font-family:"新細明體",serif'>≦</span></b><b><span
  lang=EN-US style='font-size:8.0pt;font-family:"Arial",sans-serif'> 7x</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>6</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>9</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>11</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>12</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>6</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>9</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>11</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>12</span></p>
  </td>
 </tr>
 <tr>
  <td width=139 style='width:104.55pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:#DBE5F1;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><span lang=EN-US
  style='font-size:8.0pt;font-family:"Arial",sans-serif'>7x &lt; R</span></b></p>
  </td>
  <td width=56 valign=top style='width:42.1pt;border-top:none;border-left:solid windowtext 1.0pt;
  border-bottom:solid #1D1DFF 1.0pt;border-right:none;background:white;
  padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>6</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>9</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>11</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border-top:none;border-left:none;
  border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>12</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>6</span></p>
  </td>
  <td width=46 valign=top style='width:34.7pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>9</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>11</span></p>
  </td>
  <td width=46 valign=top style='width:34.75pt;border-top:none;border-left:
  none;border-bottom:solid #1D1DFF 1.0pt;border-right:solid windowtext 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=right style='margin-left:0cm;text-align:right'><span
  lang=EN-US style='font-size:9.0pt;font-family:"Arial",sans-serif'>12</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570765"><span
lang=EN-US>7.3<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Setting Interface</span></a></h2>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570766"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>7.3.1<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Proc</span></a></h3>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sca/param</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read all SCA parameters of the cuurent scaling ratio</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : Not support.</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>Read : cat /proc/videograph/vpe/sca/param</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=323
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image075.png"
alt="fd(0x00000000)&#13;&#10;sca_y_luma_algo_en = 0&#13;&#10;sca_x_luma_algo_en = 0&#13;&#10;sca_y_chroma_algo_en = 0&#13;&#10;sca_x_chroma_algo_en = 0&#13;&#10;sca_map_sel = 0&#13;&#10;sca_1x_param = {&#13;&#10;0, 0, 0, 64,&#13;&#10;0, 0, 0, 64&#13;&#10;}&#13;&#10;&#13;&#10;sca_1.25x_param = {&#13;&#10;0, 0, 0, 64,&#13;&#10;0, 0, 0, 64&#13;&#10;}&#13;&#10;…&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sca/ctrl_param</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Set SCA controlling parameter for specific ratio.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=406 valign=top style='width:304.75pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=219 valign=top style='width:163.95pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:47.55pt'>
  <td width=406 valign=top style='width:304.75pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:47.55pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt'>echo [sca_luma_algo (0~3)] [sca_chroma_algo (0~3)] [sca_map_sel
  (0~1)] &gt; /proc/videograph/vpe/sca/ctrl_param</span></p>
  </td>
  <td width=219 valign=top style='width:163.95pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt;height:47.55pt'>
  <p class=MsoNormal><span lang=X-NONE>index: Target ratio</span></p>
  <p class=MsoNormal><span lang=X-NONE>The command “sca_luma_algo” set
  parameters “sca_y_luma_algo_en” and “sca_x_luma_algo_en” at the same time.</span></p>
  <p class=MsoNormal><span lang=X-NONE>The command “sca_chroma_algo” set
  parameters</span></p>
  <p class=MsoNormal><span lang=X-NONE>“sca_y_chroma_algo_en” and</span></p>
  <p class=MsoNormal><span lang=X-NONE>“sca_x_chroma_algo_en” at the same time.</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt'>The command “sca_map_sel”
  set<span style='color:red'> </span>“sca_map_sel” parameter.</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>Read : Not support</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sca/lpf_param</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Set SCA low pass filter parameter for specific ratio.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:20.0pt'>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:20.0pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt'>echo [index (0~16)]
  [coeffH[0]] [coeffH[1]] [coeffH[2]] ]coeffH[3]] [coeffV[0]] [coeffV[1]] [coeffV[2]]
  [coeffV[3]] (-128 ~ 127) &gt;&nbsp; /proc/videograph/vpe/sca/lpf_param</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid navy 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt;height:20.0pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt'>index: Target
  ratio</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt'>coeffH : sca_ceffH[4]</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt'>coeffV:
  sca_ceffV[4]</span></p>
  <p class=MsoNormal><span style='font-size:11.0pt;font-family:"新細明體",serif'>※</span><span
  lang=X-NONE style='font-size:11.0pt'>The software limit range is between
  -128~127, to reduce memory usage.</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>Read : Not support</span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/sca/</span><span
lang=X-NONE>yuv_range</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write YUV range of SCA at each one of the
channel.</span></p>

<p class=MsoNormal style='margin-left:12.0pt;text-indent:11.0pt'><b><span
style='font-size:11.0pt;font-family:"新細明體",serif;color:red'>※</span></b><b><span
lang=X-NONE style='font-size:11.0pt;color:red'>Parameter can be set by put job
of AP depends on channel requests, it is not recommend to be set by this proc
command or ioctl to avoid conflicts. This command is used for debugging.</span></b><span
lang=X-NONE style='font-size:11.0pt;color:red'> </span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target
  Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [fd range]
  &gt; /proc/videograph/vpe/sca /yuv_range</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>yuv_range: 0, 2,
  3, 255 (disable)</span></p>
  <p class=MsoNormal><span style='font-size:10.0pt;font-family:"新細明體",serif'>※</span><span
  lang=X-NONE style='font-size:10.0pt'>disable represent AP directly control
  parameters</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>des_drt</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/sca/yuv_range</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=204
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image076.png"
alt="Command : &#13;&#10;echo &lt; fd range &gt;(0:bypass, 2:TV, 3:PC, 255:diable)&#13;&#10;===============================================================&#13;&#10;&#13;&#10;fd(0x40000000) yuv range = 0&#13;&#10;fd(0x40000001) yuv range = 0&#13;&#10;fd(0x40000002) yuv range = 0&#13;&#10;fd(0x40000003) yuv range = 0&#13;&#10;"></span></b></p>

<p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>&nbsp;</span></p>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570767"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>7.3.2<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Vendor API</span></a></h3>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Get and set the
scaling parameters corresponding to current path_id.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>Get</b></span><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_get(HD_PATH_ID path_id, VENDOR_VIDEO_SCA,
</span><span lang=X-NONE style='font-size:11.0pt'>VENDOR_VIDEO_PARAM_SCA_SET</span><span
lang=X-NONE style='font-size:14.0pt'> </span><span lang=X-NONE
style='font-size:11.0pt'>*p_param);</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <b>Set</b></span><b><span
style='font-family:"新細明體",serif'>：</span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_set(HD_PATH_ID path_id, VENDOR_VIDEO_SCA,
</span><span lang=X-NONE style='font-size:11.0pt'>VENDOR_VIDEO_PARAM_SCA_SET</span><span
lang=X-NONE style='font-size:11.0pt'> *p_param);</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Definition]</span></b></p>

<p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt;font-family:
"Calibri",sans-serif'><img width=641 height=553
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image077.png"
alt="typedef struct _VENDOR_VIDEO_PARMA_SCA_CTRL {&#13;&#10;	INT32 sca_ceffH[4]; 				///&lt; LPF coefficient in horizontal direction&#13;&#10;	INT32 sca_ceffV[4]; 				///&lt; LPF coefficient in vertical direction&#13;&#10;} VENDOR_VIDEO_PARMA_SCA_CTRL;&#13;&#10;&#13;&#10;typedef struct _VENDOR_VIDEO_PARAM_SCA_SET {&#13;&#10;	UINT8 sca_y_luma_algo_en; 			///&lt; Algorithm select for vertical luma scaler&#13;&#10;	UINT8 sca_x_luma_algo_en; 			///&lt; Algorithm select for horizontal luma scaler&#13;&#10;	UINT8 sca_y_chroma_algo_en; 		///&lt; Algorithm select for vertical chroma scaler&#13;&#10;	UINT8 sca_x_chroma_algo_en; 		///&lt; Algorithm select for horizontal chroma scaler&#13;&#10;	UINT8 sca_map_sel; 					///&lt; Scaler source mapping format select&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_1000x_param;  ///&lt; scaling parameter for scaling ratio 1.00x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_1250x_param;  ///&lt; scaling parameter for scaling ratio 1.25x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_1500x_param;  ///&lt; scaling parameter for scaling ratio 1.50x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_1750x_param;  ///&lt; scaling parameter for scaling ratio 1.75x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_2000x_param;  ///&lt; scaling parameter for scaling ratio 2.00x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_2250x_param;  ///&lt; scaling parameter for scaling ratio 2.25x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_2500x_param;  ///&lt; scaling parameter for scaling ratio 2.50x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_2750x_param;  ///&lt; scaling parameter for scaling ratio 2.75x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_3000x_param;  ///&lt; scaling parameter for scaling ratio 3.00x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_3250x_param;  ///&lt; scaling parameter for scaling ratio 3.25x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_3500x_param;  ///&lt; scaling parameter for scaling ratio 3.50x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_3750x_param;  ///&lt; scaling parameter for scaling ratio 3.75x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_4000x_param;  ///&lt; scaling parameter for scaling ratio 4.00x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_5000x_param;  ///&lt; scaling parameter for scaling ratio 5.00x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_6000x_param;  ///&lt; scaling parameter for scaling ratio 6.00x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_7000x_param;  ///&lt; scaling parameter for scaling ratio 7.00x&#13;&#10;	VENDOR_VIDEO_PARMA_SCA_CTRL sca_8000x_param;  ///&lt; scaling parameter for scaling ratio 8.00x&#13;&#10;} VENDOR_VIDEO_PARAM_SCA_SET;&#13;&#10;"></span></b></p>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc99727892"></a><a
name="_Toc97552333"></a><a name="_Toc75451831"></a><a name="_Toc100570768"></a><a
name="_Toc42699393"><span lang=X-NONE>8<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Distortion Correction Engine (DCE)</span></a></h1>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570769"></a><a
name="_Toc42699394"><span lang=EN-US>8.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Overview</span></a></h2>

<p class=MsoNormal><span lang=X-NONE>This is lens distortion calibration module,
it can perform calibration on wide-angle lens and fish-eye lens.</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570770"></a><a
name="_Toc42699395"><span lang=EN-US>8.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>DCE Parameter Description</span></a></h2>

<p class=MsoCaption><a name="_Toc100570786"></a><a name="_Toc14368634"><span
lang=EN-US>Table 8&#8209;</span></a><span
lang=EN-US>1</span><span lang=EN-US> DCE Parameter List</span></p>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=652
 style='width:489.05pt;margin-left:5.4pt;border-collapse:collapse'>
 <tr>
  <td width=140 valign=top style='width:105.25pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:72.05pt;text-align:center;
  text-indent:-72.05pt'><b><span lang=EN-US style='font-size:11.0pt'>Parameter</span></b></p>
  </td>
  <td width=96 valign=top style='width:72.15pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Range</span></b></p>
  </td>
  <td width=114 valign=top style='width:85.35pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Def</span></b></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"新細明體",serif'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>dce_mode</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0~1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;color:black'>Select distortion function</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;color:black'>0: GDC lens calibration</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;color:black'>1: 2DLUT self-define XY coordinate
  distortion</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>lut2d_sz</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~5</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;color:black'>Size selection of 2D look-up table. The
  larger the size, the more precision to describe distortion.</span></p>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt;color:black'>0: 9x9</span></p>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt;color:black'>3: 65x65</span></p>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt;color:black'>4: 129x129</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt;color:black'>5: 257x257</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>lsb_rand</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal align=center style='text-align:center;line-height:15.0pt;
  layout-grid-mode:char;text-autospace:ideograph-numeric'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0~1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>LSB 2 bit random generation for internal 10
  bit-&gt;8 bit image.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0: fixed fill 0</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>1: random generate 0~3</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>fovbound</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>FOV boundary process method selection.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>When the distortion result can not fill the total
  output image, select different way to proceed the exceed range.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0: Replace out of boundary pixels with duplicate
  nearest pixel</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>1:
  Replace out of boundary pixels with bound pixels</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>boundy</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~1023</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Bound value for Y component(u8.2)</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>boundu</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~1023</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Bound value for U component(u8.2)</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>boundv</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~1023</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Bound value for V component(u8.2)</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>cent_x_s</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>2<sup>13</sup>-1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Define lens center of x-axis.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>It
  is recommend to set width/2.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>cent_y_s</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>2<sup>13</sup>-1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Define lens center of y-axis.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set height/2.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>xdist</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~4095</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>X input distance factor, for oval shape modeling.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set 4095, which is suitable for
  most situation.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>ydist</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~4095</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt;color:navy'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Y input distance factor, for oval shape modeling.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set 4095, which is suitable for
  most situation.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>geo_lut </span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~65535</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>The GEO deformation gain table, a total of 65
  points, indicates the magnification of each pixel in the image at a different
  distance from the deformation center (magnification = 65535 * input radius /
  output radius), the gainbase is 65535, please refer to Note 2 for the gain
  table example. </span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Value range</span><span style='font-size:11.0pt;
  font-family:"新細明體",serif'>：</span><span lang=EN-US style='font-size:11.0pt'>[0,
  65535]</span><span style='font-size:11.0pt;font-family:"新細明體",serif'>。</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>normfact</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~255</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>128</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Radius normalization factor.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Normfact = 1 &lt;&lt; (normbit + 7) / R<sup>2</sup></span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>normbit</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~31</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>31</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Radius normalization shift bit.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>R<sup>2</sup> = (width/2)<sup>2</sup>+(height/2)<sup>2</sup></span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>The
  total bit number of R<sup>2</sup> is normbit.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Example: 960<sup>2</sup>+540<sup>2</sup> = 1213200 (21
  bits)</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>fovgain</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~4095</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Adjust the scaling ratio of the final distortion
  coordinate to preserve FOV.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Scale down factor for FOV preservation.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Due
  to it will effect the calibration performance, it is recommend to set 1024.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>hfact</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0 ~ 2<sup>24</sup> -1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Horizontal scaling factor for 2DLut scaling
  up(u0.24).</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>((2DLUT
  horizontal pixel number – 1) &lt;&lt; 24) / (width – 1)</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>vfact</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0 ~ 2<sup>24</sup> -1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Vertical scaling factor for 2DLut scaling up(u0.24).</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>((2DLUT vertical pixel number – 1) &lt;&lt; 24) /
  (height – 1)</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>xofs_i</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~127</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>2DLut x offset, integer part.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set 0, if user need to adjust the
  DCE performance, user need to change the 2DLUT value.&nbsp; &nbsp;<span
  style='color:red'>&nbsp;</span></span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>xofs_f</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~2<sup>24</sup>-1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>2DLut x offset, fraction part.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>It
  is recommend to set 0, if user need to adjust the DCE performance, user need
  to change the 2DLUT value.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>yofs_i</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~127</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>2DLut y offset, integer part.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set 0, if user need to adjust the
  DCE performance, user need to change the 2DLUT value.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>yofs_f</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph align=center style='margin-left:0cm;text-align:
  center'><span lang=EN-US style='font-size:11.0pt'>0~2<sup>24</sup>-1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>2DLut y offset, fraction part.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>It is recommend to set 0, if user need to adjust the
  DCE performance, user need to change the 2DLUT value.</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE>[Note 1] </span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:22.0pt'><span
lang=EN-US style='font-size:11.0pt'>Adjust geo_fov_gain, the left side is 1024,
the right side is 1320, you can observe the increase in the field of view on
the right side. </span></p>

<p class=MsoNormal align=center style='margin-left:24.0pt;text-align:center'><span
lang=EN-US style='font-family:"Arial",sans-serif'><img width=273 height=205
id="Picture 844" src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image078.jpg"
alt="new_fovgain1024"></span><span lang=EN-US style='font-family:"Arial",sans-serif'>&nbsp;<img
width=275 height=206 id="Picture 845"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image079.jpg" alt="new_fovgain1320"></span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE>[Note 2] </span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:22.0pt'><span
lang=EN-US style='font-size:11.0pt'>The example of the GEO deformation gain
table, from left to right, corresponds to the deformation amount from the
center of the image to the edge. This parameter group indicates that the larger
the deformation amount toward the edge is. This example is a barrel deformation
correction. </span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:22.0pt'><span
lang=EN-US style='font-size:11.0pt'>R is the distance from the center of the
image to each point. This distance can be understood as the radius of the
circle.</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:22.0pt'><span
lang=EN-US style='font-size:11.0pt'>Ri represents the radius of each point of
the input (before correction) image.</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:22.0pt'><span
lang=EN-US style='font-size:11.0pt'>Ro represents the radius of each point of
the output (corrected) image.</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:22.0pt'><span
lang=EN-US style='font-size:11.0pt'>RoMax represents the longest distance from
the center of the output image to the four corners. If the center of the image
falls at 1/2 of the width and height, the four corners are all equal, and they
are the longest distances. </span><span
lang=EN-US style='font-size:12.0pt;font-family:"Times New Roman",serif;
position:relative;top:13.5pt'><img width=139 height=48
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image080.png"></span><span
lang=EN-US style='font-family:"Arial",sans-serif'><img width=560 height=420
id="圖片 9" src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image081.png"></span></p>

<p class=MsoNormal><span lang=EN-US>&nbsp;</span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570771"></a><a
name="_Toc42699396"><span lang=EN-US>8.3<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Setting Interface</span></a></h2>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570772"></a><a
name="_Toc42699397"><span lang=X-NONE style='font-size:16.0pt;line-height:300%'>8.3.1<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Proc</span></a></h3>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/dce/dump_info</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read all DCE parameters at the current camera channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : Not support.</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt'>Read : cat /proc/videograph/vpe/dce/dump_info</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=900
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image082.png"
alt="dce_en = 0&#13;&#10;dce_mode = 1&#13;&#10;lut2d_sz = 3&#13;&#10;lut2d_vaddr = 0x0000000000000000&#13;&#10;lut2d_paddr = 0x0&#13;&#10;lsb_rand = 0&#13;&#10;fovbound = 1&#13;&#10;boundy = 512&#13;&#10;boundu = 512&#13;&#10;boundv = 512&#13;&#10;cent_x_s = 720&#13;&#10;cent_y_s = 720&#13;&#10;xdist = 4095&#13;&#10;ydist = 4095&#13;&#10;normfact = 0&#13;&#10;normbit = 0&#13;&#10;fovgain = 1024&#13;&#10;hfact = 745654&#13;&#10;vfact = 745654&#13;&#10;xofs_i = 0&#13;&#10;xofs_f = 0&#13;&#10;yofs_i = 0&#13;&#10;yofs_f = 0&#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 &#13;&#10;geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0 geo_lut[i]=0&#13;&#10;&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>&nbsp;</span></b></p>

<h5 style='margin-top:6.0pt;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE>/proc/videograph/vpe/dce/</span><span
lang=X-NONE>ch</span><span lang=X-NONE>_en</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=X-NONE
style='font-size:11.0pt'>Read or write the enable status of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>Target Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt'>echo [ dc_en
  0~1 ] &gt; /proc/videograph/vpe/dce/ch_en</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt'>dc_en</span></b></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><b><span lang=X-NONE
style='font-size:11.0pt'>cat /proc/videograph/vpe/dce/ch_en</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt'><img width=618 height=36
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image083.png" alt="dc_en = 0"></span></b></p>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570773"><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>8.3.2<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Vendor API</span></a></h3>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Get and set the dce
parameters corresponding to current path_id.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Get</span><span
style='font-family:"新細明體",serif'>：</span></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_video_get(HD_PATH_ID path_id, VENDOR_VIDEOPROC_DEWARP_INFO,
VENDOR_DEWARP_INFO *p_param); </span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set</span><span
style='font-family:"新細明體",serif'>：</span></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT c(HD_PATH_ID path_id, VENDOR_ VENDOR_VIDEOPROC_DEWARP_INFO,
VENDOR_DEWARP_INFO *p_param);</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Define]</span></b></p>

<p class=MsoNormal style='text-indent:27.55pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=641
height=783 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image084.png"
alt="typedef struct _VENDOR_DEWARP_CTRL {&#13;&#10;	BOOL dc_enable;&#13;&#10;	BOOL dctg_enable;&#13;&#10;} VENDOR_DEWARP_CTRL;&#13;&#10;&#13;&#10;typedef enum _VENDOR_DEWARP_MODE {&#13;&#10;	VENDOR_DEWARP_DEWARP_MODE_GDC	= 0,&#13;&#10;	VENDOR_DEWARP_DEWARP_MODE_2DLUT	= 1,&#13;&#10;	ENUM_DUMMY4WORD(VENDOR_DEWARP_DEWARP_MODE)&#13;&#10;} VENDOR_DEWARP_MODE;&#13;&#10;&#13;&#10;typedef struct _VENDOR_DEWARP_DGC_PARM {&#13;&#10;	INT32 cent_x_s;		///&lt; Lens center of x axis (signed)&#13;&#10;	INT32 cent_y_s;    	///&lt; Lens center of y axis (signed)&#13;&#10;	UINT32 lens_r;		///&lt; Radius of Lens&#13;&#10;	UINT32 xdist;  		///&lt; X input distance factor, for oval shape modeling&#13;&#10;	UINT32 ydist;  		///&lt; Y input distance factor, for oval shape modeling&#13;&#10;	UINT8 normfact;  	///&lt; Radius normalization factor (u1.7)&#13;&#10;	UINT8 normbit;  	     ///&lt; Radius normalization shift bit&#13;&#10;	UINT16 geo_lut[VENDOR_GEO_LUT_X]; ///&lt; GDC look-up table&#13;&#10;} VENDOR_DEWARP_DGC_PARM;&#13;&#10;&#13;&#10;typedef struct _VENDOR_DEWARP_2DLUT_PARM {&#13;&#10;	UINT8 lut2d_sz;		///&lt; Size selection of 2D look-up table, 0:9x9, 3:65x65&#13;&#10;	UINT32 hfact;  		///&lt; Horizontal scaling factor for 2DLut scaling up (u0.24)&#13;&#10;	UINT32 vfact;  		///&lt; Vertical scaling factor for 2DLut scaling up (u0.24)&#13;&#10;	UINT8 xofs_i;  		///&lt; 2DLUT x offset, integer part&#13;&#10;	UINT32 xofs_f;     	///&lt; 2DLUT x offset, fraction part&#13;&#10;	UINT8 yofs_i;  		///&lt; 2DLUT y offset, integer part&#13;&#10;	UINT32 yofs_f;    	///&lt; 2DLUT xy offset, fraction part&#13;&#10;} VENDOR_DEWARP_2DLUT_PARM;&#13;&#10;&#13;&#10;typedef struct _VENDOR_DEWARP_FOV_PARM {&#13;&#10;	UINT8 fovbound;  	///&lt; FOV boundary process method selection&#13;&#10;	UINT16 boundy;   	///&lt; Bound value for Y component (u8.2)&#13;&#10;	UINT16 boundu;   	///&lt; Bound value for U component (u8.2)&#13;&#10;	UINT16 boundv;   	///&lt; Bound value for V component (u8.2)&#13;&#10;	UINT16 fovgain;   	///&lt; Scale down factor for FOV preservation (u2.10)&#13;&#10;} VENDOR_DEWARP_FOV_PARM;&#13;&#10;&#13;&#10;&#13;&#10;"></span></b></p>

<p class=MsoNormal><b><span lang=X-NONE style='font-size:11.0pt;font-family:
"Calibri",sans-serif'><img width=641 height=217
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image085.png"
alt="typedef struct _VENDOR_DEWARP_INFO {&#13;&#10;	VENDOR_DEWARP_MODE mode;&#13;&#10;	VENDOR_DEWARP_DGC_PARM dgc;&#13;&#10;	VENDOR_DEWARP_2DLUT_PARM lut2d;&#13;&#10;	VENDOR_DEWARP_FOV_PARM fov;&#13;&#10;} VENDOR_DEWARP_INFO;&#13;&#10;&#13;&#10;typedef struct _VENDOR_DEWARP_2DLUT_TABLE {&#13;&#10;	UINT32 tbl[VENDOR_GEO_LUT];&#13;&#10;} VENDOR_DEWARP_2DLUT_TABLE;&#13;&#10;&#13;&#10;"></span></b></p>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570774"><span
lang=X-NONE>9<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>DC Table </span></a><span lang=X-NONE
style='font-family:"Calibri",sans-serif'>Generator</span><span lang=X-NONE>(DCTG</span><span
lang=X-NONE>)</span></h1>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570775"><span
lang=EN-US>9.1<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Overview</span></a></h2>

<p class=MsoNormal><a name="_Hlk99728570"><span lang=X-NONE>For perspective
projection application, in order to increase the convenience of usage, DCTG
module let user to set the desired angle and size with an instinct way to
generate DCTG parameters automaticall<span style='color:black'>y. </span></span></a><span
lang=X-NONE style='color:black'>Whenever this function is enabled, manual set
DCE 2D-LUT function will be invalid.</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal><b><span lang=X-NONE>[Note]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;When using DCTG function, user
needs to set two parameters enable, one is dc_enable, the other is dctg_en.</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal><span lang=X-NONE>Please refer to the following description:</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>The “theta” is the top/bottom angle.</span></p>

<p class=MsoNormal><span lang=EN-US>The “phi” is the rotate angle. </span></p>

<p class=MsoNormal><span lang=EN-US>The “rot_y” is the rotate offset of (x, z)
plane towards Y-axis. </span></p>

<p class=MsoNormal><span lang=EN-US>The “rot_z” is the rotate offset of (x, y)
plane towards Z-axis.</span></p>

<p class=MsoNormal><span lang=EN-US style='font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p class=MsoNormal><span lang=EN-US>Generate LUT:</span></p>

<p class=MsoNormal><span lang=EN-US>Define the rotate angle of FOV by
phi_st/phi_ed, and then rotate to FOV location by rot_y.</span></p>

<p class=MsoNormal><span lang=EN-US>Define the top/bottom angle of FOV by theta_st/theta_ed,
and then rotate to FOV location by rot_z.</span></p>

<p class=MsoNormal><span lang=EN-US><img width=320 height=271 id="圖片 82"
src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image086.jpg"><img width=304
height=274 id="圖片 83" src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image087.jpg"></span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc99728134"></a><a
name="_Toc75509273"></a><a name="_Toc75452199"></a><a name="_Toc100570776"><span
lang=EN-US>9.2<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Parameter Description</span></a></h2>

<p class=MsoCaption><a name="_Toc100570787"><span lang=EN-US style='font-family:
"Arial",sans-serif'>Table 9&#8209;</span></a><span
lang=EN-US style='font-family:"Arial",sans-serif'>1</span><span lang=EN-US
style='font-family:"Arial",sans-serif'> DCT</span><span lang=EN-US
style='font-family:"Arial",sans-serif'>G parameter list</span></p>

<table class=MsoNormalTable border=0 cellspacing=0 cellpadding=0 width=652
 style='width:489.05pt;margin-left:5.4pt;border-collapse:collapse'>
 <tr>
  <td width=140 valign=top style='width:105.25pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:72.05pt;text-align:center;
  text-indent:-72.05pt'><b><span lang=EN-US style='font-size:11.0pt'>Parameter</span></b></p>
  </td>
  <td width=96 valign=top style='width:72.15pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Range</span></b></p>
  </td>
  <td width=114 valign=top style='width:85.35pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt'>Def</span></b></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border-top:solid #1D1DFF 1.5pt;
  border-left:none;border-bottom:solid #1D1DFF 1.5pt;border-right:none;
  background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"新細明體",serif'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>dctg_en</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0-1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>DCTG ON/OFF</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>mount_type</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0~1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt'>Camera mount type. </span></p>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt'>0: Ceiling mount</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>1: Floor mount</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>lut2d_sz</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt;color:black'>0, 3</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt;color:black'>3</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt'>Select size of 2D look-up table, this
  parameter must the same with DCE parameter.</span></p>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt'>0: 9x9</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>3: 65x65</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>lens_r</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0~2<sup>15</sup>-1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt'>Valid radius of fish-eye lens, the unit
  is pixel.</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Please refer to advance description.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>lens_x_st</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0~2<sup>14</sup>-1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>The start x position of fish-eye lens at the source
  image, the unit is pixel.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>lens_y_st</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0~2<sup>14</sup>-1</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>The start y position of fish-eye lens at the source
  image, the unit is pixel.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>theta_st</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>-180 ~ 180</span></p>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>(-*pi ~ *pi)</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt'>FOV theta start radian.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>theta_ed</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>-180 ~ 180</span></p>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>(-*pi ~ *pi)</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt'>FOV theta end radian.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>theta_end
  &gt; theta_st: normal image</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>theta_end &lt; theta_st: flip image</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>phi_st</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>-360 ~ 360<br>
  (-2*pi ~ 2*pi)</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>OV phi start radian.</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>phi_ed</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>-360 ~ 360<br>
  (-2*pi ~ 2*pi)</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:22.0pt;text-indent:-22.0pt'><span
  lang=EN-US style='font-size:11.0pt'>FOV phi end radian.</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>(-2*pi
  ~ 2*pi)</span></p>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>phi_end
  &gt; theta_st: normal image</span></p>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>phi_end &lt; theta_st: flip image</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>rot_z</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>-360 ~ 360<br>
  (-2*pi ~ 2*pi)</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Z-axis rotate radian</span></p>
  </td>
 </tr>
 <tr>
  <td width=140 style='width:105.25pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><b><i><span lang=EN-US
  style='font-size:11.0pt'>rot_y</span></i></b></p>
  </td>
  <td width=96 style='width:72.15pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>-360 ~ 360<br>
  (-2*pi ~ 2*pi)</span></p>
  </td>
  <td width=114 style='width:85.35pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=10 align=center style='margin-left:0cm;text-align:center'><span
  lang=EN-US style='font-size:11.0pt'>0</span></p>
  </td>
  <td width=302 valign=top style='width:226.3pt;border:none;border-bottom:solid #1D1DFF 1.0pt;
  background:white;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoListParagraph style='margin-left:0cm'><span lang=EN-US
  style='font-size:11.0pt'>Y-zxis rotate radian.</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal><b><span lang=EN-US>&nbsp;</span></b></p>

<p class=MsoNormal><b><span lang=EN-US>Advance description:</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>lens_r: </span></i></b><span
lang=EN-US style='font-size:11.0pt'>The valid radius of fish-eye device.</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>lens_x_st :
</span></i></b><span lang=EN-US style='font-size:11.0pt'>The start x position
of fish-eye lens at the source image, the unit is pixel.</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-indent:-24.0pt'><span
lang=EN-US style='font-size:11.0pt;font-family:Wingdings'>l<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp; </span></span><b><i><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>lens_y_st :</span></i></b><span
lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'> </span><span
lang=EN-US style='font-size:11.0pt'>The start y position of fish-eye lens at
the source image, the unit is pixel.</span></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=EN-US
style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=321
height=234 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image088.png"></span></p>

<h2 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570777"><span
lang=EN-US>9.3<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Setting Interface</span></a></h2>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570778"></a><a
name="_Toc99727896"><span lang=X-NONE style='font-size:16.0pt;line-height:300%'>9.3.1<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Proc</span></a></h3>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE style='font-family:"Calibri",sans-serif'>/proc/videograph/vpe/dctg/dump_info</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='text-indent:27.5pt'><span lang=X-NONE
style='font-size:11.0pt'>Read all dctg parameters of the current channel.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Write : Not support.</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Read :
cat /proc/videograph/vpe/dctg/dump_info</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
width=618 height=264 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image089.png"
alt="fd(0x00000000)&#13;&#10;dctg_en = 0&#13;&#10;mount_type = 1&#13;&#10;lut2d_sz = 3&#13;&#10;lens_r = 540&#13;&#10;lens_x_st = 0(0)&#13;&#10;lens_y_st = 0(0)&#13;&#10;theta_st = 45(51471)&#13;&#10;theda_ed = 90(102943)&#13;&#10;phi_st = -40(-45753)&#13;&#10;phi_ed = 40(45752)&#13;&#10;rot_z = 0&#13;&#10;rot_y = 0&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE style='font-family:"Calibri",sans-serif'>/proc/videograph/vpe/dctg/ch_en</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set
dctg enable.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>Target Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:19.2pt'>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:19.2pt'>
  <p class=MsoNormal style='text-autospace:none'><span lang=X-NONE
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>echo [dctg_en] &gt;
  /proc/videograph/vpe/dctg/ch_en</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt;height:19.2pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-family:"Calibri",sans-serif'>dctg_en:
  dctg enable</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>cat
/proc/videograph/vpe/dctg/ch_en</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
width=618 height=36 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image090.png"
alt="dctg_en = 1"></span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE style='font-family:"Calibri",sans-serif'>/proc/videograph/vpe/dctg/phi</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt'><span lang=EN-US
style='font-size:11.0pt'>Set FOV phi start radian</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>proc command</span></b></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>Target Parameter</span></b></p>
  </td>
 </tr>
 <tr style='height:20.0pt'>
  <td width=438 valign=top style='width:328.7pt;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt;height:20.0pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt;font-family:
  "Calibri",sans-serif'>ech</span><span lang=X-NONE style='font-size:10.0pt;
  font-family:"Calibri",sans-serif'>o [st] [ed] &gt; /p</span><span
  lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>roc/videog</span><span
  lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>raph/vpe/dctg/phi</span></p>
  </td>
  <td width=187 valign=top style='width:140.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid navy 1.0pt;
  padding:0cm 5.4pt 0cm 5.4pt;height:20.0pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-family:"Calibri",sans-serif'>st:
  </span><a name="_Hlk99729192"><span lang=EN-US style='font-size:11.0pt'>FOV
  phi start radian</span></a></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt;font-family:
  "Calibri",sans-serif'>ed : </span><span lang=EN-US style='font-size:11.0pt'>FOV
  phi end radian</span></p>
  <p class=MsoNormal><span style='font-size:11.0pt;font-family:細明體'>※</span><span
  lang=X-NONE style='font-family:"Calibri",sans-serif'>angle range: -360 ~ 360</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>cat
/proc/videograph/vpe/dctg/phi</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
width=618 height=84 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image091.png"
alt="echo &lt;st&gt; &lt;ed&gt; (range -360~360)&#13;&#10;phi_st degree= -40&#13;&#10;phi_ed degree = 40&#13;&#10;"></span></b></p>

<p class=MsoNormal style='margin-left:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>&nbsp;</span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE style='font-family:"Calibri",sans-serif'>/proc/videograph/vpe/dctg/rot</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set
</span><span lang=EN-US style='font-size:11.0pt'>Z-axis and Y-zxis rotate
radian.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>Target Parameter</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>echo [z] [y] &gt; /prc/videograph/vpe/dctg/rot</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-family:"Calibri",sans-serif'>&nbsp;</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-family:"Calibri",sans-serif'>z:
  </span><a name="_Hlk99729311"><span lang=EN-US style='font-size:11.0pt'>Z-axis
  rotate radian.</span></a></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt;font-family:
  "Calibri",sans-serif'>y: </span><span lang=EN-US style='font-size:11.0pt'>Y-zxis
  rotate radian</span></p>
  <p class=MsoNormal><span style='font-size:11.0pt;font-family:細明體'>※</span><span
  lang=X-NONE style='font-family:"Calibri",sans-serif'>angle range: -360 ~ 360</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>cat
/proc/videograph/vpe/dctg/rot</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Output : </span></b></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img
width=618 height=84 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image092.png"
alt="echo &lt;z&gt; &lt;y&gt; (range -360~360)&#13;&#10;rot_z degree = 0&#13;&#10;rot_y degree = 0&#13;&#10;"></span></p>

<h5 style='margin-top:0cm;margin-right:6.0pt;margin-bottom:0cm;margin-left:
46.0pt;margin-bottom:.0001pt;text-indent:-22.0pt'><span lang=X-NONE
style='font-family:Wingdings;font-weight:normal'>l<span style='font:7.0pt "Times New Roman"'>&nbsp;
</span></span><span lang=X-NONE style='font-family:"Calibri",sans-serif'>/proc/videograph/vpe/dctg/theta</span></h5>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='margin-left:24.0pt'><span lang=EN-US
style='font-size:11.0pt'>Set FOV theta start radian.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Write : </span></b></p>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0 width=625
 style='width:468.7pt;margin-left:26.7pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-bottom:none;background:#E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>proc command</span></b></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:solid navy 1.0pt;
  border-left:none;border-bottom:none;border-right:solid navy 1.0pt;background:
  #E5EAFF;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><b><span style='font-size:10.0pt;font-family:"新細明體",serif'>目標參數</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=454 valign=top style='width:12.0cm;border:solid navy 1.0pt;
  border-top:none;padding:0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-size:10.0pt;font-family:
  "Calibri",sans-serif'>ech</span><span lang=X-NONE style='font-size:10.0pt;
  font-family:"Calibri",sans-serif'>o [st] [ed] &gt; /p</span><span
  lang=X-NONE style='font-size:10.0pt;font-family:"Calibri",sans-serif'>rc/videograph/vpe/dctg/theta</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-family:"Calibri",sans-serif'>&nbsp;</span></p>
  </td>
  <td width=171 valign=top style='width:128.5pt;border-top:none;border-left:
  none;border-bottom:solid navy 1.0pt;border-right:solid navy 1.0pt;padding:
  0cm 5.4pt 0cm 5.4pt'>
  <p class=MsoNormal><span lang=X-NONE style='font-family:"Calibri",sans-serif'>st:
  </span><span lang=EN-US style='font-size:11.0pt'>FOV theta start radian.</span></p>
  <p class=MsoNormal><span lang=X-NONE style='font-size:11.0pt;font-family:
  "Calibri",sans-serif'>ed : </span><span lang=EN-US style='font-size:11.0pt'>FOV
  theta end radian</span></p>
  <p class=MsoNormal><span style='font-size:11.0pt;font-family:細明體'>※</span><span
  lang=X-NONE style='font-family:"Calibri",sans-serif'>angle range: -180 ~ 180</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Read : </span></b></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>cat
/proc/videograph/vpe/dctg/theta</span></p>

<p class=MsoNormal style='text-indent:24.0pt;text-autospace:none'><b><span
lang=X-NONE style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Output :</span></b></p>

<p class=MsoNormal style='text-indent:22.0pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=618
height=84 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image093.png"
alt="echo &lt;st&gt; &lt;ed&gt; (range -180~180)&#13;&#10;theta_st degree = 45&#13;&#10;theda_ed degree = 90&#13;&#10;"></span></b></p>

<h3 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570779"></a><a
name="_Toc99727897"><span lang=X-NONE style='font-size:16.0pt;line-height:300%'>9.3.2<span
style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </span></span><span
lang=X-NONE style='font-size:16.0pt;line-height:300%'>Vendor API</span></a></h3>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Description]</span></b></p>

<p class=MsoNormal style='text-indent:24.0pt'><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Get and set the dctg
parameters corresponding to current path_id.</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Command]</span></b></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Get</span><span
style='font-family:"新細明體",serif'>：</span></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_videoproc_get(HD_PATH_ID path_id,
VENDOR_VIDEOPROC_DEWARP_DCTG_INFO,</span><span lang=X-NONE style='font-size:
11.0pt'> VENDOR_DEWARP_DCTG_INFO</span><span lang=X-NONE style='font-size:11.0pt'>
*p_param); </span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;</span></p>

<p class=MsoNormal><span lang=X-NONE>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Set</span><span
style='font-family:"新細明體",serif'>：</span></p>

<p class=MsoNormal style='margin-left:24.1pt'><span lang=X-NONE
style='font-size:11.0pt'>HD_RESULT vendor_videoproc_set(HD_PATH_ID path_id,
VENDOR_VIDEOPROC_DEWARP_DCTG_INFO, </span><span lang=X-NONE style='font-size:
11.0pt'>VENDOR_DEWARP_DCTG_INFO</span><span lang=X-NONE style='font-size:11.0pt'>
*p_param);</span></p>

<p class=MsoNormal style='margin-top:9.0pt;margin-right:0cm;margin-bottom:0cm;
margin-left:24.0pt;margin-bottom:.0001pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'>[Define]</span></b></p>

<p class=MsoNormal style='text-indent:27.55pt'><b><span lang=X-NONE
style='font-size:11.0pt;font-family:"Calibri",sans-serif'><img width=641
height=662 src="NT9833x_VPE_IQ_Tuning_Guide_en.files/image094.png"
alt="typedef struct _VENDOR_DEWARP_CTRL {&#13;&#10;	BOOL dc_enable;&#13;&#10;	BOOL dctg_enable;&#13;&#10;} VENDOR_DEWARP_CTRL;&#13;&#10;&#13;&#10;typedef struct _VENDOR_DEWARP_DCTG_INFO {&#13;&#10;        VENDOR_DEWARP_DCTG_MODE mode;&#13;&#10;        VENDOR_DEWARP_DCTG_LENS_PARM lens;&#13;&#10;        VENDOR_DEWARP_DCTG_FOV_PARM fov;&#13;&#10;} VENDOR_DEWARP_DCTG_INFO;&#13;&#10;&#13;&#10;typedef enum _VENDOR_DEWARP_DCTG_MODE {&#13;&#10;	VENDOR_DEWARP_DCTG_MODE_90	= 0,&#13;&#10;	VENDOR_DEWARP_DCTG_MODE_360	= 1,&#13;&#10;	ENUM_DUMMY4WORD(VENDOR_DEWARP_DCTG_MODE)&#13;&#10;} VENDOR_DEWARP_DCTG_MODE;&#13;&#10;&#13;&#10;typedef struct _VENDOR_DEWARP_DCTG_LENS_PARM {&#13;&#10;        UINT8 mount_type;         ///&lt; Camera mount type. 0:Ceiling mount, 1:Floor mount&#13;&#10;        UINT8 lut2d_sz;         ///&lt; Size selection of 2D look-up table, 0:9x9, 3:65x65, should the same with DCE setting.&#13;&#10;        UINT32 lens_r;          ///&lt; Radius of Lens&#13;&#10;        UINT32 lens_x_st;     ///&lt; Lens start x position at a source image&#13;&#10;        UINT32 lens_y_st;     ///&lt; Lens start y position at a source image&#13;&#10;} VENDOR_DEWARP_DCTG_LENS_PARM;&#13;&#10;&#13;&#10;typedef struct _VENDOR_DEWARP_DCTG_FOV_PARM {&#13;&#10;        INT32 theta_st;           ///&lt; FOV theta start radian (s4.16) Range: -*pi ~ *pi&#13;&#10;        INT32 theta_ed;          ///&lt; FOV theta end radian (s4.16) Range: -*pi ~ *pi&#13;&#10;        INT32 phi_st;                  ///&lt; FOV phi start radian (s4.16) Range: -2*pi ~ 2*pi&#13;&#10;        INT32 phi_ed;                ///&lt; FOV phi end radian (s4.16) Range: -2*pi ~ 2*pi&#13;&#10;        INT32 rot_z;               ///&lt; Z-axis rotate radian (s4.16) Range: -2*pi ~ 2*pi&#13;&#10;        INT32 rot_y;                   ///&lt; Y-axis rotate radian (s4.16) Range: -2*pi ~ 2*pi&#13;&#10;} VENDOR_DEWARP_DCTG_FOV_PARM;&#13;&#10;&#13;&#10;"></span></b></p>

<b><span lang=X-NONE style='font-size:11.0pt;line-height:300%;font-family:"Calibri",sans-serif'><br
clear=all style='page-break-before:always'>
</span></b>

<h1 style='margin-left:0cm;text-indent:0cm'><a name="_Toc100570780"><span
lang=X-NONE>10<span style='font:7.0pt "Times New Roman"'>&nbsp;&nbsp;&nbsp;&nbsp;
</span></span><span lang=X-NONE>Revise History</span></a></h1>

<table class=MsoNormalTable border=1 cellspacing=0 cellpadding=0
 style='margin-left:1.4pt;border-collapse:collapse;border:none'>
 <tr>
  <td width=72 style='width:53.85pt;border:solid windowtext 1.0pt;padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Version</span></b></p>
  </td>
  <td width=84 style='width:63.15pt;border:solid windowtext 1.0pt;border-left:
  none;padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Date</span></b></p>
  </td>
  <td width=178 style='width:133.4pt;border:solid windowtext 1.0pt;border-left:
  none;padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Advisor</span></b></p>
  </td>
  <td width=280 valign=top style='width:210.0pt;border:solid windowtext 1.0pt;
  border-left:none;padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><b><span
  lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Description</span></b></p>
  </td>
 </tr>
 <tr>
  <td width=72 style='width:53.85pt;border:solid windowtext 1.0pt;border-top:
  none;padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0.1.00</span></p>
  </td>
  <td width=84 style='width:63.15pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif;color:black'>2021/01/20</span></p>
  </td>
  <td width=178 style='width:133.4pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif;color:black'>Allen
  Hsu</span></p>
  </td>
  <td width=280 valign=top style='width:210.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>First
  version.</span></p>
  </td>
 </tr>
 <tr>
  <td width=72 style='width:53.85pt;border:solid windowtext 1.0pt;border-top:
  none;padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0.2.00</span></p>
  </td>
  <td width=84 style='width:63.15pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif;color:black'>2021/3/26</span></p>
  </td>
  <td width=178 style='width:133.4pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif;color:black'>Allen
  Hsu</span></p>
  </td>
  <td width=280 valign=top style='width:210.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Add
  description of Vendor command.</span></p>
  </td>
 </tr>
 <tr>
  <td width=72 style='width:53.85pt;border:solid windowtext 1.0pt;border-top:
  none;padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif'>0.3.00</span></p>
  </td>
  <td width=84 style='width:63.15pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif;color:black'>2022/4/11</span></p>
  </td>
  <td width=178 style='width:133.4pt;border-top:none;border-left:none;
  border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal align=center style='text-align:center'><span lang=EN-US
  style='font-size:11.0pt;font-family:"Calibri",sans-serif;color:black'>Mina
  Wang</span></p>
  </td>
  <td width=280 valign=top style='width:210.0pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;
  padding:0cm 1.4pt 0cm 1.4pt'>
  <p class=MsoNormal><span lang=EN-US style='font-size:11.0pt;font-family:"Calibri",sans-serif'>Add
  description for dce and dctg</span></p>
  </td>
 </tr>
</table>

<p class=MsoNormal style='text-align:justify;text-justify:inter-ideograph'><span
lang=EN-US style='font-family:"Arial",sans-serif'>&nbsp;</span></p>

<p class=MsoNormal style='text-align:justify;text-justify:inter-ideograph'><span
lang=EN-US style='font-family:"Arial",sans-serif'>&nbsp;</span></p>

</div>

</body>


