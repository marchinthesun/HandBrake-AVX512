# HandBrake (ZenScale & Threadripper Edition) [![macOS Build](https://github.com/HandBrake/HandBrake/workflows/macOS%20build/badge.svg)](https://github.com/HandBrake/HandBrake/actions?query=workflow%3A%22macOS+build%22) [![Windows Build](https://github.com/HandBrake/HandBrake/workflows/Windows%20Build/badge.svg)](https://github.com/HandBrake/HandBrake/actions?query=workflow%3A%22Windows+Build%22) [![Linux Build](https://github.com/HandBrake/HandBrake/workflows/Linux%20Build/badge.svg)](https://github.com/HandBrake/HandBrake/actions?query=workflow%3A%22Linux+Build%22)

This is a high-performance fork of **HandBrake** specifically optimized for **AMD Ryzen 9 (7950X, 9950X)** and **Threadripper / Threadripper PRO (3990X, 7995WX)** processors. 

While the original HandBrake is an excellent general-purpose video transcoder, it often hits scalability bottlenecks on high-core-count architectures. This fork rewrites thread scheduling, memory allocation, and vectorization pipelines to fully unlock the power of multi-CCD, NUMA, and AVX-512 capable Zen architectures.

---

## 🚀 Key Optimization Features

Unlike upstream builds, this fork includes custom architectural enhancements tailored for professional workstation CPUs:

*   **Multi-CCD Thread Affinity:** Smart thread scheduling across Core Complex Dies (CCDs). The encoder forces heavy, inter-dependent video blocks to stay within a single CCD, significantly minimizing costly inter-die data penalties over the AMD Infinity Fabric.
*   **AVX-512 Native Pipeline:** Compiled from the ground up with native hardware acceleration flags (`-mavx512f -mavx512vl -mavx512dq`). This drastically accelerates CPU-bound video filters, including deinterlacing, color space conversions, and high-quality scaling on Ryzen 7950X and Threadripper 7000/9000 series.
*   **NUMA-Aware Scaling for 3990X & 7995WX:** Advanced memory-allocation optimizations designed for 64-core and 96-core monsters. The transcoder allocates memory pools locally to the active CPU node, preventing memory latency bottlenecks across massive logical core environments.
*   **Latest SVT-AV1 & x265 High-Thread Integration:** Injects the absolute bleeding-edge versions of SVT-AV1 and x265 directly from GitHub, featuring custom NUMA-node and thread-pool pooling that can seamlessly scale past 128+ threads without dropping encoding efficiency.

---

## Overview

HandBrake is an open-source video transcoder available for Linux, Mac, and Windows, licensed under the [GNU General Public License (GPL) Version 2](LICENSE).

HandBrake takes videos you already have and makes new ones that work on your mobile phone, tablet, TV media player, game console, computer, or web browser—nearly anything that supports modern video formats.

HandBrake works with most common video files and formats, including ones created by consumer and professional video cameras, mobile devices such as phones and tablets, game and computer screen recordings, and DVD and Blu-ray discs. HandBrake leverages tools such as FFmpeg, x264, and x265, SVT-AV1 to create new MP4, MKV or WebM video files from these *Sources*.

For information on downloading, building/installing, and using HandBrake, see the official [HandBrake Documentation](https://handbrake.fr/docs).

## Community Support

For information on HandBrake's community support channels, please see [Community Support](https://handbrake.fr/docs/en/latest/help/community-support.html).

Please familiarise yourself with our [code of conduct](https://github.com/HandBrake/HandBrake/blob/master/CODE_OF_CONDUCT.md).

## Contributing

We welcome most contributions. While it is our goal to allow everyone to contribute, contributions not meeting the project's goals or standards may be rejected.

Please read our [guide to contributing](https://handbrake.fr/docs/en/latest/contributing/contribute.html). This will provide you with all the information you need to start contributing to the project. 

## Translations

We are now accepting translations via  [Transifex](https://explore.transifex.com/HandBrakeProject/) 

Please read our [Translations Guide](https://github.com/HandBrake/HandBrake/blob/master/TRANSLATION.markdown) and follow the instructions if you are interested in joining the translation effort.


## Additional Information

[Application / Project Information](https://github.com/HandBrake/HandBrake/wiki/Application-Information)  
[Authors](AUTHORS.markdown)  
[License](LICENSE)  
[News](NEWS.markdown)  

## Special Thanks

<a href="https://www.macstadium.com/"><img width="200" alt="MacStadium" src="https://uploads-ssl.webflow.com/5ac3c046c82724970fc60918/5c019d917bba312af7553b49_MacStadium-developerlogo.png"></a>

and to many others who have contributed! [Thanks](THANKS.markdown)
