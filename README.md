# Emotions Dashboard

## Mockup
![edb mockup](https://github.com/milesccoleman/emotionsdashboard/blob/master/Presentation1.png?raw=true "Emotions Dashboard Mockup")

## Recognizing the Face
First we need to know when a face is present so we can snap a photo. Perhpas [OpenCV]("https://www.pyimagesearch.com/2018/06/25/raspberry-pi-face-recognition/")

## Analyzing the Face
After we snap a photo of a face, we need to analyze the emotoinal content. With the returned values, we can then have our dials and meters light up and move. A possible API for this might be [Emotient]("https://imotions.com/api/")

## Ethical Questions
1. Can we avoid using an API so that we are not sending peoples' faces across the internet? 
2. Can we add in a script that immediately overwrites any image files, to avoid storing peoples' faces? 
3. Can we add a button, alongside a disclaimer, to get peoples' permission to take their photo? 
 
