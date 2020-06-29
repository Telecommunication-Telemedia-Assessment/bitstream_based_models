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
We used it to validate the ITU-T P.1204.3 model independently, see [QoMEX 2020 paper](https://www.researchgate.net/publication/341792225_Bitstream-based_Model_Standard_for_4KUHD_ITU-T_P12043_-_Model_Details_Evaluation_Analysis_and_Open_Source_Implementation).


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

