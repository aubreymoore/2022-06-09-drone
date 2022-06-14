---
title: 'Harmonic Radar: Drone Trial 2022-06-09'
toc: structure
author: Aubrey Moore and Glenn Dulla
date: Last revised June 14, 2022

documentclass: scrartcl
geometry: margin=2cm
lang: en

pagesize: letter
fontsize: 12pt
graphics: yes
colorlinks: true
---

<!--
pandoc techreport.md -f markdown -o techreport.pdf --number-sections
mupdf techreport.pdf
-->

\newpage

# Objective

The objective of this trial was was to map the location of a single harmonic radar target placed beneath a linear transect flown by a drone.  

# Methods

A RECCO hand-held harmonic radar transceiver was suspended with rope about 1.5 feet beneath the landing struts of a DJI AGRIS MG-1 drone. A target consisting of 2 harmonic radar tags with antennae placed at right angles (\autoref{target}) was positioned in an open field and the drone was programmed to fly along a line which crossed this position.

\begin{figure}[]
\centering
\includegraphics[width=0.5\textwidth]{target.png}
\caption{Target.}
\label{target}
\end{figure}


## Harmonic radar recording

The RECCO hand-held harmonic radar device generates an audio signal to indicate that a reflection from a harmonic radar tag has been detected. The amplitude of this signal is maximum when the receiving antennae points at the target and it increases as the target gets closer. A human operator locates the direction of a tag by directional scanning with the antenna while monitoring the signal using a built-in speaker or headphones. In this application, we point the receiving antenna straight down and record the signal by connecting a small digital audio field recorder (ZOOM F2) to the audio jack. The F2 records monophonic 32-bit floating point WAV files at a rate of 48,000 samples per second.

An Audacity screenshot displays the waveform and spectrogram of the record created during the trial (\autoref{audacity}). The WAV file was processed using a Jupyter notebook which performed the following steps.

* Noise reduction: Background noise was removed from the signal by the [noisereduce Python library](https://pypi.org/project/noisereduce/).  
* Data reduction: The mean absolute amplitude (MAA) of the signal was calculated for each second within the WAV file. MAA is used as a measure of signal strength.

\autoref{audacity-noise-reduction}

\begin{figure}[p]
\centering
\includegraphics[]{audacity.png}
\caption{Audacity.}
\label{audacity}
\end{figure}

\begin{figure}[p]
\centering
\includegraphics[]{audacity-noise-reduction.png}
\caption{Audacity-noise-reduction.}
\label{audacity-noise-reduction}
\end{figure}

\clearpage
## GPS track recording

The flight data log was downloaded as FLY275.DAT from the drone. This file was parsed using a free Java program named DatCon using parameters recorded in \autoref{DataCon}. DataCon creates three files:

* a CSV containing 1,275 columns. I set the sample rate to one row per second (1 Hz).
* a text file containing event messages.
* a KML file containing latitude and longitude of points along the drone's track \autoref{GoogleEarth}.

\begin{figure}[]
\centering
\includegraphics[width=\textwidth]{DataCon.png}
\caption{DataCon.}
\label{DataCon}
\end{figure}

\begin{figure}[]
\centering
\includegraphics[width=\textwidth]{GoogleEarth.png}
\caption{Google Earth.}
\label{DataCon}
\end{figure}

\begin{figure}[]
\centering
\includegraphics[width=\textwidth]{flightpath.png}
\caption{flightpath}
\label{flightpath}
\end{figure}

\begin{figure}[]
\centering
\includegraphics[width=\textwidth]{latlonmaa.png}
\caption{latlonmaah}
\label{latlonmaa}
\end{figure}

\newpage

# Results and Discussion
## Harmonic radar recording
## GPS track recording
