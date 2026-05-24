---
title: "WiFi-detector"
date: 2026-05-24
draft: false
description: "A 2.4 GHz radiation detector for 6.2300"
tags: ["Completed", "Class"]
---
![The 2.4 GHz detector device](featured.jpg "The 2.4 GHz detector")

{{< katex >}}

{{< button href="/files/62300_final_project_report.pdf" >}}
Writeup
{{< /button >}}
{{< button href="https://github.mit.edu/bljin/62040-final-project" >}}
GitHub
{{< /button >}}

For my 6.2300 (EM Waves and Applications) final project, I worked together with two of my classmates to create a 2.4 GHz radiation detector. I was personally responsible for designing the antenna, band-pass filter, and envelope detector.

For the antenna, I chose a helical antenna operating in axial mode for an easy-to-construct, high-directivity antenna. The antenna was simulated in Ansys HFSS and tuned with a network analyzer to achieve optimal performance at 2.4 GHz. A 3D printed support was added for structural stability and to keep spacing consistent, and a triangular strip of copper was added and trimmed at the base of the antenna to provide impedance matching with the amplifier.

{{< gallery >}}
  {{< figure src="gain.png" alt="Measured vs. simulated antenna gain" caption="Measured vs. simulated antenna gain. Blue is measured, red is simulated." figureClass="grid-w50" >}}
  {{< figure src="antenna.jpg" alt="Constructed antenna" caption="Constructed antenna" figureClass="grid-w50" >}}
{{< /gallery >}}

For the bandpass filter, I chose a Chebyshev hairpin microstrip filter for its small footprint and steep rolloff. The filter was designed to have a center frequency of 2.4 GHz and a bandwidth of 100 MHz to cover the entire WiFi band. The filter was designed and tuned in Ansys HFSS and implemented on a custom PCB.

{{< gallery >}}
  {{< figure src="sparams.png" alt="Simulated filter s-parameters" caption="Simulated filter s-parameters." figureClass="grid-w50" >}}
  {{< figure src="filterpcb.jpg" alt="Filter and envelope detector" caption="Filter and envelope detector PCB. Also makes for a nice keychain." figureClass="grid-w50" >}}
{{< /gallery >}}

The envelope detector is a simple half-wave rectifier with an emitter-follower buffering the output. A time constant of \\(\\tau = 1 \\, \\text{ms}\\) was chosen to prevent 2.4 GHz ripple and other effects from WiFi itself from showing up, providing a steady analog voltage representing the output power.

The final device was able to detect a cell phone's hotspot from 5 feet away with a theoretical maximum of 50 feet. The output signal shows a clear step where WiFi signals are detected.

{{< gallery >}}
  {{< figure src="bigview.jpg" alt="Large-time view" caption="WiFi beacon packets observed by detector" figureClass="grid-w33" >}}
  {{< figure src="smallview.jpg" alt="Small view" caption="View of a single WiFi packet" figureClass="grid-w33" >}}
  {{< figure src="videoview.jpg" alt="View when video being streamed" caption="Signal detected when device is streaming video" figureClass="grid-w33" >}}
{{< /gallery >}}