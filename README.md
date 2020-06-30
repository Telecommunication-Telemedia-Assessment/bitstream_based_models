# ITU-T P.1203 and P.1204 model and development
We developed several video quality models that are using bitstream based data to predict subjective video/audiovisual quality in the context of DASH/HAS based video streaming.

## ITU-T P.1204.3
ITU-T P.1204.3 is part of ITU-T P.1204, considering UHD-1/4K short term video quality.

The standard is accessible [here](https://www.itu.int/rec/T-REC-P.1204.3/en).

### Reference Implementation
Open source reference implementation of [ITU-T P.1204.3](https://github.com/Telecommunication-Telemedia-Assessment/bitstream_mode3_p1204_3).
ITU-T P.1204.3 is a short term video quality prediction model that uses full bitstream data to estimate video quality scores on a segment level.


### Mode 3 Video Parser
To run the reference implementation a [bitstream paser](https://github.com/Telecommunication-Telemedia-Assessment/bitstream_mode3_videoparser) is required, we also open sourced this.
This bitstream parser can be used for H.264, H.265 and VP9 encoded videos, and it will extract beside QP values additional statistics derived from the bitstream.


### Open Access Video Quality Test Dataset -- AVT-VQDB-UHD-1
We further published a large scale [Video Quality Database for UHD-1](https://github.com/Telecommunication-Telemedia-Assessment/AVT-VQDB-UHD-1), subjective data and videos can be downloaded.
We used it to validate the ITU-T P.1204.3 model independently.


## ITU-T P.1203
ITU-T Rec. P.1203 is the world’s first standard for measuring the Quality of Experience of HTTP Adaptive Streaming services.

The standard is accessible [here](https://www.itu.int/rec/T-REC-P.1203).

#### Reference Software
We developed a reference implementation of the [ITU-T Rec. P.1203 standard](https://github.com/itu-p1203/itu-p1203).


### Open Dataset
An [open dataset](https://github.com/itu-p1203/open-dataset) was created for the ITU-T P.1203 model, which contains training and validation databases from the standardization procedure.

### Codec Extension
Moreover, to include never video codecs, we developed a [codec extension](https://github.com/Telecommunication-Telemedia-Assessment/itu-p1203-codecextension) from our lab.


## Additional Software
During development of the described models, we conducted several subjective video quality tests.
And performed analysis with othe state of the art video quality metrics.

### avrateNG
To run such a test, we use [avrateNG](https://github.com/Telecommunication-Telemedia-Assessment/avrateNG).
It is a video, image, and general multimedia rating system, based on a  web interface (server client architecture).

### cencro
[Cencro](https://github.com/Telecommunication-Telemedia-Assessment/cencro) is a center cropped variant of Netflix's VMAF, that we used to compare our models during the development.


## Who are we?
The [Audiovisual Technology Group group](https://www.tu-ilmenau.de/en/audio-visual-technology/) is part of the Institute of Media Technology at TU Ilmenau, Germany, headed by Prof. Alexander Raake.
The Audiovisual Technology Group (AVT) deals with the function, application and perception of audio and video equipment and systems.

## Publications

### 2020

* Susanna Schwarzmann, Nick Hainke, Thomas Zinner, Christian Sieber,  Werner Robitza and Alexander Raake. **"Comparing fixed and variable segment durations for adaptive video streaming: a holistic analysis."** _Proceedings of the 11th ACM Multimedia Systems Conference_. 2020. [[url]](https://dl.acm.org/doi/abs/10.1145/3339825.3391858)

* Rakesh Rao Ramachandra Rao, Steve Göring, Werner Robitza, Alexander Raake, Bernhard Feiten, Peter List, and Ulf Wüstenhagen. **"Bitstream-based Model Standard for 4K/UHD: ITU-T P.1204.3 -- Model Details, Evaluation, Analysis and Open Source Implementation."** _Twelfth International Conference on Quality of Multimedia Experience (QoMEX)_. Athlone, Ireland. May 2020. [[url]](https://www.researchgate.net/publication/341792225_Bitstream-based_Model_Standard_for_4KUHD_ITU-T_P12043_-_Model_Details_Evaluation_Analysis_and_Open_Source_Implementation)

* Werner Robitza, Alexander M. Dethof, Steve Göring, Alexander Raake, Tim Polzehl, and Andre Beyer. **"Are You Still Watching? Streaming Video Quality and Engagement Assessment in the Crowd."** _Twelfth International Conference on Quality of Multimedia Experience (QoMEX)_. Athlone, Ireland. May 2020. [[url]]("https://www.researchgate.net/publication/341736567_Are_You_Still_Watching_Streaming_Video_Quality_and_Engagement_Assessment_in_the_Crowd")

### 2019

* Steve Göring, Christopher Krämmer, and Alexander Raake. **"cencro -- Speedup of Video Quality Calculation using Center Cropping."** _21st IEEE International Symposium on Multimedia (2019 IEEE ISM)_. Dec 2019. [[url]](https://www.researchgate.net/publication/338200687_cencro_--_Speedup_of_Video_Quality_Calculation_using_Center_Cropping)

* Rakesh Rao Ramachandra Rao, Steve Göring, Werner Robitza, Bernhard Feiten, and Alexander Raake. **"AVT-VQDB-UHD-1: A Large Scale Video Quality Database for UHD-1."** _21st IEEE International Symposium on Multimedia (2019 IEEE ISM)_. Dec 2019. [[url]](https://www.researchgate.net/publication/338201010_AVT-VQDB-UHD-1_A_Large_Scale_Video_Quality_Database_for_UHD-1)

* Rakesh Rao Ramachandra Rao, Steve Göring, Patrick Vogel, Nicolas Pachatz, Juan Jose Villamar Villarreal, Werner Robitza, Peter List, Bernhard Feiten, and Alexander Raake. **"Adaptive video streaming with current codecs and formats: Extensions to parametric video quality model ITU-T P.1203."** _Electronic Imaging_. 2019. [[url]](https://ist.publisher.ingentaconnect.com/contentone/ist/ei/2019/00002019/00000010/art00015)


### 2018

* Werner Robitza, Steve Göring, Alexander Raake, David Lindegren, Gunnar Heikkil&#228;, Jörgen Gustafsson, Peter List, Bernhard Feiten, Ulf Wüstenhagen, Marie-Neige Garcia, Kazuhisa Yamagishi, and Simon Broom. **"HTTP Adaptive Streaming QoE Estimation with ITU-T Rec. P.1203 -- Open Databases and Software."** _9th ACM Multimedia Systems Conference_. Amsterdam. 2018. [[url]](https://www.researchgate.net/publication/325780595_HTTP_adaptive_streaming_QoE_estimation_with_ITU-T_rec_P_1203_open_databases_and_software)


* Werner Robitza, Dhananjaya G. Kittur, Alexander M. Dethof, Steve Göring, Bernhard Feiten and Alexander Raake. **"Measuring YouTube QoE with ITU-T P. 1203 under Constrained Bandwidth Conditions."** _Tenth International Conference on Quality of Multimedia Experience (QoMEX)_. IEEE. 2018. [[ulr]](https://www.researchgate.net/publication/325780662_Measuring_YouTube_QoE_with_ITU-T_P1203_under_Constrained_Bandwidth_Conditions)

### 2017

* Steve Göring, Alexander Raake and Bernhard Feiten. **"A framework for QoE analysis of encrypted video streams."** _Ninth International Conference on Quality of Multimedia Experience (QoMEX)_. May 2017. [[url]](https://www.researchgate.net/publication/317616945_A_Framework_for_QoE_Analysis_of_Encrypted_Videos_Streams)

* Alexander Raake, Marie-Neige Garcia, Werner Robitza, Peter List, Steve Göring and Bernhard Feiten. **"A bitstream-based, scalable video-quality model for HTTP adaptive streaming: ITU-T P.1203.1."** _Ninth International Conference on Quality of Multimedia Experience (QoMEX)_. May 2017. [[url]](https://www.researchgate.net/publication/317368539_A_bitstream-based_scalable_video-quality_model_for_HTTP_adaptive_streaming_ITU-T_P12031)

* Robitza, Werner, Marie-Neige Garcia, and Alexander Raake. **"A modular HTTP adaptive streaming QoE model - Candidate for ITU-T P. 1203 (''P. NATS')."** _Ninth International Conference on Quality of Multimedia Experience (QoMEX)_. IEEE, 2017.[[url]](https://ieeexplore.ieee.org/iel7/7958434/7965624/07965689.pdf)