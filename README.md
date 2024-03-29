# ITU-T P.1203 and P.1204 model and development
We developed several video quality models that are using bitstream-based data to predict subjective video/audiovisual quality in the context of video streaming using HAS (HTTP-based adaptive streaming), such as MPEG-DASH (Dynamic Adaptive Streaming over HTTP).

<figure>
  <img src="./assets/imgs/pnats_phase2.svg" alt="pnats overall structure"/>
  <figcaption>Overall P.1203 and P.1204 structure. Here, the P.1204 models are complementary to the Pv-module, P.1203.1, and provide short-term video-quality estimations. The P.1204.3 model developed by our group is bitstream-based, like the P.1203.1 Pv-module, as described further below.</figcaption>
</figure>


## ITU-T P.1204.3
[ITU-T P.1204.3](https://www.itu.int/rec/T-REC-P.1204.3/en) is part of [ITU-T P.1204](https://www.itu.int/rec/T-REC-P.1204), a set of video-quality models developed for up to UHD-1/4K resolution. ITU-T P.1204.3 is a short-term video quality prediction model that uses full bitstream data to estimate video-quality scores.

It provides two outputs:

1. A score at segment level, for an input bitstream of a video between 5 to 10 sec duration, on a 5-point scale [1,5], reflecting the Mean Opinion Score (MOS) collected from more than 600 subjects in a series of laboratory tests on almost 5,000 video sequences. These quality tests were carried out during the so-called P.NATS Phase 2 competition conducted within ITU-T's Question Q14, Study Group 12, in collaboration with the Video Quality Experts Group (VQEG).

2. A per-1-sec video-quality score that can be used for longer-term quality or QoE integraction, following the model architecture of [ITU-T Rec. P.1203](https://www.itu.int/rec/T-REC-P.1203) (see details below).

The P.1204.3 standard is accessible [here](https://www.itu.int/rec/T-REC-P.1204.3/en).

### Reference Implementation
We have created an open-source reference implementation that is now available for [ITU-T P.1204.3](https://github.com/Telecommunication-Telemedia-Assessment/bitstream_mode3_p1204_3).
The model and its evaluation are described in an accompanying conference paper, see [(Rao et al., IEEE QoMEX 2020)](https://www.researchgate.net/publication/341792225_Bitstream-based_Model_Standard_for_4KUHD_ITU-T_P12043_-_Model_Details_Evaluation_Analysis_and_Open_Source_Implementation).

### Mode 3 Video Parser
To run the reference implementation, a [bitstream parser](https://github.com/Telecommunication-Telemedia-Assessment/bitstream_mode3_videoparser) is required, which is also available open source.
This bitstream parser can be used for H.264, H.265 and VP9 encoded videos. It extracts a number of features from the bitstream, such as QP-values and statistics about motion vectors and transform coefficients. The bitstream parser is described in more detail in [(Rao et al., IEEE QoMEX 2020)](https://www.researchgate.net/publication/341792225_Bitstream-based_Model_Standard_for_4KUHD_ITU-T_P12043_-_Model_Details_Evaluation_Analysis_and_Open_Source_Implementation).

### Open Access Video Quality Test Dataset -- AVT-VQDB-UHD-1
We further published a large scale [Video Quality Database for UHD-1](https://github.com/Telecommunication-Telemedia-Assessment/AVT-VQDB-UHD-1), and subjective data as well as most of the used videos can be downloaded. The database is described in [(Rao et al., IEEE ISM 2019)](https://www.researchgate.net/publication/338201010_AVT-VQDB-UHD-1_A_Large_Scale_Video_Quality_Database_for_UHD-1).
We used this database for a complementary evaluation of the ITU-T P.1204.3 model, besides the validation during the P.1204 standard development, see [(Rao et al., IEEE QoMEX 2020)](https://www.researchgate.net/publication/341792225_Bitstream-based_Model_Standard_for_4KUHD_ITU-T_P12043_-_Model_Details_Evaluation_Analysis_and_Open_Source_Implementation).

## ITU-T P.1203
[ITU-T Rec. P.1203](https://www.itu.int/rec/T-REC-P.1203) is the world’s first standard for measuring the Quality of Experience of HTTP Adaptive Streaming services for longer viewing sessions between 1 and 5 min duration.

P.1203 comprises three modules:
1. Short-term video-quality module Pv ("P" for "prediction"; [ITU-T Rec. P.1203.1](https://www.itu.int/rec/T-REC-P.1203.1/en)), providing per-1-sec video-quality scores on the aforementioned 5-point "MOS scale". The bitstream model is available in different "Modes" that take input information of different complexity, depending on what is available to a corresponding probe. Input information ranges from metadata such as audio codec used, video resolution and framerate, audio and video bitrate (Mode 0) over information about encoded frame type and size (Mode 1) to frame-type specific QP information available from full access to the bitstream (Modes 2 and 3). The Pv model was initially developed for H.264/MPEG-4 AVC encoding.

2. Short-term audio-quality module Pa [(ITU-T Rec. P.1203.2)](https://www.itu.int/rec/T-REC-P.1203.2/en), delivering per-1-sec audio-quality scores on the 5-point "MOS scale". The audio-quality module can handle a variety of audio codecs and is based on metadata only ("Mode 0").

3. Quality integration module Pq [(ITU-T Rec. P.1203.2)](https://www.itu.int/rec/T-REC-P.1203.3/en), delivering (a) a per-1-sec audiovisual quality score, (b) an integral audiovisual quality score for the complete session addressed, and (c) as main output an integral session quality score, reflecting the Quality of Experience (QoE) resulting from audio and video quality as well as typical adaptive-streaming related factors such as quality-adaptation and hence visible / audible switches, the initial loading delay at the beginning of a session and possible stalling events that occur when the playout buffer has depleted.

The accompanying general standard document that outlines the application scope and other more general features of P.1203 is available as [ITU-T Rec. P.1203](https://www.itu.int/rec/T-REC-P.1203).

Related scientific publications from our group describing specific model components are [(Raake et al., IEEE QoMEX 2017)](https://www.researchgate.net/publication/317368539_A_bitstream-based_scalable_video-quality_model_for_HTTP_adaptive_streaming_ITU-T_P12031) (scalable video-quality model for different types of input information) and [(Robitza et al., ACM MMSys 2018)](https://www.researchgate.net/publication/325780595_HTTP_adaptive_streaming_QoE_estimation_with_ITU-T_rec_P_1203_open_databases_and_software) (open source implementation for P.1203, see below).

#### Reference Software
We developed a reference implementation of the [ITU-T Rec. P.1203 standard](https://github.com/itu-p1203/itu-p1203).
It is described in [(Robitza et al., ACM MMSys 2018)](https://www.researchgate.net/publication/325780595_HTTP_adaptive_streaming_QoE_estimation_with_ITU-T_rec_P_1203_open_databases_and_software).

### Open Dataset
An [open dataset](https://github.com/itu-p1203/open-dataset) was created for the ITU-T P.1203 model, which contains training and validation databases from the standardization procedure. The database is described in [(Robitza et al., ACM MMSys 2018)](https://www.researchgate.net/publication/325780595_HTTP_adaptive_streaming_QoE_estimation_with_ITU-T_rec_P_1203_open_databases_and_software) together with the open-source model implementation.

### Technical Report

We have compiled a [technical report](https://telecommunication-telemedia-assessment.github.io/bitstream_based_models/documents/tech-report-bitstream-based-models.pdf) detailing the model performance of the P.1203 series and P.1204.3 models on open datasets.

### Codec Extensions
Moreover, to include the complementary video codecs H.265/MPEG-H HEVC and VP9, we developed a [codec extension](https://github.com/Telecommunication-Telemedia-Assessment/itu-p1203-codecextension) for the Mode 0 part of P.1203.

## Additional Software
During development of the different bitstream models, we conducted several subjective video-quality tests.
Further, we performed analyses with other state-of-the-art video-quality metrics and models.

### avrateNG
To run a subjective test, we use our test-tool [avrateNG](https://github.com/Telecommunication-Telemedia-Assessment/avrateNG).
It is a video, image, and general multimedia rating system, based on a  web interface (server-client architecture).

### AVrate Voyager
To run an online/remote/crowd test for image/video/audio quality assessment, the developed [AVrate Voyager](https://github.com/Telecommunication-Telemedia-Assessment/AVrateVoyager) tool can be used.

### cencro
[Cencro](https://github.com/Telecommunication-Telemedia-Assessment/cencro) is a center cropped variant of Netflix's VMAF (Video Multi-Method Assessment Fusion), that we used to compare our models during the development. With the center-cropping it can run significantly faster than the full-frame VMAF, with only slight decrease in prediction accuracy.

### Processing Chain for P.NATS Phase2 and other repos
[Processing chain](https://github.com/pnats2avhd) used to generate sequences for the P.NATS Phase 2 / AHVD-AS project from ITU-T SG12 and VQEG.

## Who are we?
The [Audiovisual Technology Group](https://www.tu-ilmenau.de/en/audio-visual-technology/) is part of the Institute of Media Technology at TU Ilmenau, Germany, headed by Prof. Alexander Raake.
The Audiovisual Technology Group (AVT) deals with the function, application and perception of audio and video equipment and systems.

## Publications

### 2022
* Ramachandra Rao, Rakesh Rao, Göring, Steve, and Raake, Alexander. **"AVQBits-Adaptive Video Quality Model Based on Bitstream Information for Various Video Applications."** __IEEE Access. vol. 10. 2022__. [[url]](https://ieeexplore.ieee.org/document/9846967)

* Robitza, Werner, Rakesh Rao Ramachandra-Rao, Steve Göring, Alexander Dethof, and Alexander Raake. **"Deploying the ITU-T P. 1203 QoE model in the wild and retraining for new codecs."** __In Proceedings of the 1st Mile-High Video Conference__, pp. 121-122 (2022). [[url]](https://dl.acm.org/doi/pdf/10.1145/3510450.3517310)

### 2021
* Göring, Steve, Rakesh Rao Ramachandra Rao, Stephan Fremerey, and Alexander Raake. **"AVrate Voyager: an open source online testing platform."** __In 2021 IEEE 23rd International Workshop on Multimedia Signal Processing (MMSP)__, pp. 1-6. IEEE, 2021. [[url]](https://ieeexplore.ieee.org/iel7/9733399/9733432/09733561.pdf) 

* Göring, Steve, Rakesh Rao Ramachandra Rao, Bernhard Feiten, and Alexander Raake. **"Modular framework and instances of pixel-based video quality models for UHD-1/4K."** __IEEE Access 9 (2021)__: 31842-31864. [[url]](https://ieeexplore.ieee.org/iel7/6287639/9312710/09355144.pdf)

* Rao, Rakesh Rao Ramachandra, Steve Göring, and Alexander Raake. **"Towards High Resolution Video Quality Assessment in the Crowd."** __In 2021 13th International Conference on Quality of Multimedia Experience (QoMEX)__, pp. 1-6. IEEE, 2021. [[url]](https://ieeexplore.ieee.org/iel7/9465370/9465375/09465425.pdf)

* Robitza, Werner, Rakesh Rao Ramachandra Rao, Steve Göring, and Alexer Raake. **"Impact of Spatial and Temporal Information on Video Quality and Compressibility."** __In 2021 13th International Conference on Quality of Multimedia Experience (QoMEX)__, pp. 65-68. IEEE, 2021. [[url]](https://ieeexplore.ieee.org/iel7/9465370/9465375/09465452.pdf)

* Ramachandra Rao, Rakesh Rao, Steve Göring, and Alexander Raake. **"Enhancement of Pixel-based Video Quality Models using Meta-data."** __Electronic Imaging 2021, no. 9 (2021)__:. [[url]](https://www.ingentaconnect.com/content/ist/ei/2021/00002021/00000009/art00022?crawler=true&mimetype=application/pdf)


### 2020
* Raake, Alexander, Silvio Borer, Shahid M. Satti, Jörgen Gustafsson, Rakesh Rao Ramachandra Rao, Stefano Medagli, Peter List et al. **"Multi-model standard for bitstream-, pixel-based and hybrid video quality assessment of UHD/4K: ITU-T P. 1204."** __IEEE Access__ 8 (2020): 193020-193049. [[url]](https://ieeexplore.ieee.org/iel7/6287639/8948470/09234526.pdf)

* Rakesh Rao Ramachandra Rao, Steve Göring, Robert Steger, Saman Zadtootaghaj, Nabajeet Barman, Stephan Fremerey, Sebastian Möller and Alexander Raake. **“A Large-scale Evaluation of the bitstream-based video-quality model ITU-T P.1204.3 on Gaming Content.”** _22nd International Workshop on Multimedia Signal Processing (MMSP), IEEE_. Tampere, Finland. Sep 2020. [[url]](https://ieeexplore.ieee.org/iel7/9287028/9287048/09287055.pdf)

* Susanna Schwarzmann, Nick Hainke, Thomas Zinner, Christian Sieber,  Werner Robitza and Alexander Raake. **"Comparing fixed and variable segment durations for adaptive video streaming: a holistic analysis."** _Proceedings of the 11th ACM Multimedia Systems Conference_. 2020. [[url]](https://dl.acm.org/doi/abs/10.1145/3339825.3391858)

* Rakesh Rao Ramachandra Rao, Steve Göring, Werner Robitza, Alexander Raake, Bernhard Feiten, Peter List, and Ulf Wüstenhagen. **"Bitstream-based Model Standard for 4K/UHD: ITU-T P.1204.3 -- Model Details, Evaluation, Analysis and Open Source Implementation."** _Twelfth International Conference on Quality of Multimedia Experience (QoMEX)_. Athlone, Ireland. May 2020. [[url]](https://www.researchgate.net/publication/341792225_Bitstream-based_Model_Standard_for_4KUHD_ITU-T_P12043_-_Model_Details_Evaluation_Analysis_and_Open_Source_Implementation)

* Werner Robitza, Alexander M. Dethof, Steve Göring, Alexander Raake, Tim Polzehl, and Andre Beyer. **"Are You Still Watching? Streaming Video Quality and Engagement Assessment in the Crowd."** _Twelfth International Conference on Quality of Multimedia Experience (QoMEX)_. Athlone, Ireland. May 2020. [[url]](https://www.researchgate.net/publication/341736567_Are_You_Still_Watching_Streaming_Video_Quality_and_Engagement_Assessment_in_the_Crowd)

### 2019

* Steve Göring, Christopher Krämmer, and Alexander Raake. **"cencro -- Speedup of Video Quality Calculation using Center Cropping."** _21st IEEE International Symposium on Multimedia (2019 IEEE ISM)_. Dec 2019. [[url]](https://www.researchgate.net/publication/338200687_cencro_--_Speedup_of_Video_Quality_Calculation_using_Center_Cropping)

* Rakesh Rao Ramachandra Rao, Steve Göring, Werner Robitza, Bernhard Feiten, and Alexander Raake. **"AVT-VQDB-UHD-1: A Large Scale Video Quality Database for UHD-1."** _21st IEEE International Symposium on Multimedia (2019 IEEE ISM)_. Dec 2019. [[url]](https://www.researchgate.net/publication/338201010_AVT-VQDB-UHD-1_A_Large_Scale_Video_Quality_Database_for_UHD-1)

* Rakesh Rao Ramachandra Rao, Steve Göring, Patrick Vogel, Nicolas Pachatz, Juan Jose Villamar Villarreal, Werner Robitza, Peter List, Bernhard Feiten, and Alexander Raake. **"Adaptive video streaming with current codecs and formats: Extensions to parametric video quality model ITU-T P.1203."** _Electronic Imaging_. 2019. [[url]](https://ist.publisher.ingentaconnect.com/contentone/ist/ei/2019/00002019/00000010/art00015)


### 2018

* Werner Robitza, Steve Göring, Alexander Raake, David Lindegren, Gunnar Heikkil&#228;, Jörgen Gustafsson, Peter List, Bernhard Feiten, Ulf Wüstenhagen, Marie-Neige Garcia, Kazuhisa Yamagishi, and Simon Broom. **"HTTP Adaptive Streaming QoE Estimation with ITU-T Rec. P.1203 -- Open Databases and Software."** _9th ACM Multimedia Systems Conference_. Amsterdam. 2018. [[url]](https://www.researchgate.net/publication/325780595_HTTP_adaptive_streaming_QoE_estimation_with_ITU-T_rec_P_1203_open_databases_and_software)


* Werner Robitza, Dhananjaya G. Kittur, Alexander M. Dethof, Steve Göring, Bernhard Feiten and Alexander Raake. **"Measuring YouTube QoE with ITU-T P. 1203 under Constrained Bandwidth Conditions."** _Tenth International Conference on Quality of Multimedia Experience (QoMEX)_. IEEE. 2018. [[url]](https://www.researchgate.net/publication/325780662_Measuring_YouTube_QoE_with_ITU-T_P1203_under_Constrained_Bandwidth_Conditions)

### 2017

* Steve Göring, Alexander Raake and Bernhard Feiten. **"A framework for QoE analysis of encrypted video streams."** _Ninth International Conference on Quality of Multimedia Experience (QoMEX)_. May 2017. [[url]](https://www.researchgate.net/publication/317616945_A_Framework_for_QoE_Analysis_of_Encrypted_Videos_Streams)

* Alexander Raake, Marie-Neige Garcia, Werner Robitza, Peter List, Steve Göring and Bernhard Feiten. **"A bitstream-based, scalable video-quality model for HTTP adaptive streaming: ITU-T P.1203.1."** _Ninth International Conference on Quality of Multimedia Experience (QoMEX)_. May 2017. [[url]](https://www.researchgate.net/publication/317368539_A_bitstream-based_scalable_video-quality_model_for_HTTP_adaptive_streaming_ITU-T_P12031)

* Robitza, Werner, Marie-Neige Garcia, and Alexander Raake. **"A modular HTTP adaptive streaming QoE model - Candidate for ITU-T P. 1203 (''P. NATS')."** _Ninth International Conference on Quality of Multimedia Experience (QoMEX)_. IEEE, 2017. [[url]](https://ieeexplore.ieee.org/iel7/7958434/7965624/07965689.pdf)
