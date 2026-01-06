AppleALC For iMac12,2
========

[![Build Status](https://github.com/acidanthera/AppleALC/actions/workflows/main.yml/badge.svg?branch=master)](https://github.com/acidanthera/AppleALC/actions) [![Scan Status](https://scan.coverity.com/projects/16166/badge.svg?flat=1)](https://scan.coverity.com/projects/16166)

I have an iMac (27-inch, Mid 2011) model.
There’s no design reason for its audio quality to be worse than in 2020, yet the sound quality was poor.
The midrange was overemphasized, making the highs sound buried.
Measurements revealed that Apple’s DSP tuning was suboptimal. So, I created my own new tuning.

For reference, the default OCLP patch includes an older version of AppleALC, which causes issues on iMac12,2 where the built-in DSP and audio sleep functions do not work. When using only the OCLP patch, Apple’s DSP tuning is not applied, resulting in even worse sound quality. My tuned file uses version 1.9.6 with all bugs fixed, ensuring the built-in DSP, audio sleep, and other features work perfectly.

## Features
- New DSP Tuning
- Currently compatible with OCLP macOS 11-15

## Content

![Original](image/iMac%2027%202011%20Original.png)

This is the original frequency response.
The midrange is slightly boosted, frequencies above 2.5kHz drop by about 6dB, and there’s a high peak at 10kHz.

<br/><br/>

![Tuned](image/iMac%2027%202011%20Final%20DSP.png)

This is the frequency response after my tuning.
It became nearly flat from 140Hz to 6kHz. The peak at 10kHz was significantly reduced.
The dip at 7kHz is due to the speaker itself, so I decided it was unfixable and skipped it.
This resulted in an almost flat response overall.
Listening tests confirmed balanced improvements, with highs that were previously buried now audible.
Compared to the final 2020 iMac 27-inch model—which has a design inevitably limiting sound quality (speaker holes are too small due to thinness) and feels like artificially boosted highs for resolution—my 2011 model, with larger speaker holes, achieves very natural highs and better resolution through this tuning.

<br/><br/>

![Volume](image/iMac%2027%202011%20Final%20DSP%20Vol.png)

This is the frequency response at different volume levels.
Measurements were taken at Vol 4, 8, 12, and 16 notches.

## Installation

It’s very simple.
Download the zip file from the Release, mount the EFI partition, navigate to /EFI/OC/Kexts/, delete the existing AppleALC.kext, overwrite it with the new one, and reboot.

That's it.
