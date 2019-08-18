---
title: "Motion Detection in Dual-Mode Endomicroscopy"
date: 2019-08-17
tags: [image processing, classification, machine learning]
#header:
  #images: "/assets/images/"
excerpt: "Motion Detection in Dual-Mode Endomicroscopy"
mathjax: true
---
# Motion Detection in DME
## Classifying motion in video data from a dual-mode endomicroscopic setup for early identification of precancerous developments in the oral epithelium.

Remy Shea, BC Cancer Agency, February 2019

This is work I had completed during my time at the BC Cancer Research Center's Integrative Oncology Department under Dr. Calum MacAulay. The work was presented at the 2019 SPIE Photonics West conference in San Francisco in February.

---

<iframe src=”/assets/pdfs/DME Poster BCCRC.pdf" width=”100%” height=”100%”>
</iframe>

---

## Introduction
This was a project I had completed while working at the British Columbia Cancer Research Center, in the Integrative Oncology department under Dr. Calum MacAulay. While the work shown here in this poster was not traditional data science work, my time at the CRC was the initial motivation for me to get into data science as a field. I am very proud of the work I was able to do in the year or so that I was there, and also to be able to present my findings at the SPIE Photonics West conference in San Francisco, in February of 2019. In the following sections, I will try to give a high level overview of the work, why it was important, and what advances it may lead to, for the understanding of a non-technical audience.

## Background
The motivation for this work mainly stems from the high morbidity and massive impact on quality-of-life that are related to oral cancers. In 2013, oral cancers caused more than 135,000 deaths globally. The disease has 5-year survival rate of only 65% in the United States, far better than the survival rates in developing economies where the disease is both more, and increasingly more prevalent. Things like chewing tobacco and smoking are particularly disastrous in this regard.

As with all cancers, the likelihood of successfully treating oral cancers increases drastically the earlier you can identify the cancerous growth and begin treatment. Stages of dysplastic tissue transformation precede full-blown oral cancers, as the cells in the epithelium (surface layer of tissue) get progressively crowded (cancer is often characterized by cells multiplying uncontrollably) closer and closer to the surface of the tissue. It is easier to treat but harder to detect when the transformations are still only going on deeper within the tissue.

Part of the reason why oral caner is so deadly is that it has often proved alarmingly difficult to locate where exactly the cancerous tissue is, until it is too late. When reviewing images of the tongues of patients suffering from the late stages of oral pre-cancer AND using a 1-cm margin of error when excising tissue, teams of expert oncologists can miss significant portions of the deadly precancerous developments in almost 9% of cases. Missing half your tongue and still getting oral cancer is a pretty raw deal. There is clearly a lot of room to improve. Both in diagnostic power of the tests, as well as how early the pre-cancers can be caught and successfully treated.

## Dual Mode Endomicroscopy
Dr.MacAulay's group at the IO department of the BCCRC has in recent years developed a new way of looking at whats going on in the deeper layers of the oral epithelium (the inside lining of your mouth, and tongue), where the easier-to-treat, early pre-cancers lay. The imaging modality, named Dual-Mode Endomicroscopy combines Fluorescence Endomicroscopy and Diffuse Optical Microscopy into a single, affordable, compact wheely-cart system.

### Fluoresecence Endomicroscopy
Fluorescence Endomicroscopy (FE) uses a surface staining technique to highlight the cell nuclei, and gives useful information about the density of cells in the few surface layers of the epithelium. If there is severe dysplastic transformation going on, it'll stick out like a sore thumb - a super-crowded image with way more nuclei relative to what we know healthy baselines should look like, given the location within the mouth and potentially other demographic information of the patient. However, this information is more-or-less limited to the surface of the epithelium. Since the surface-staining dye doesn't get to make its way into the depths of the epithelium and be absorbed by the cell nuclei there, FE doesn't give us the juicy scoop as to whats going on deeper in the tissue, which is what we're looking for as previously mentioned. That's where DOM comes in.

### Diffuse Optical Microscopy
Diffuse Optical Microscopy (DOM) is a much lower resolution, and much more finicky imaging technique. An extremely rough analogy is like a murder-mystery detective knocking on a wall and noticing the wall isn't a wall *BUT A DOOR*. You can get information on the density of a material just by interfacing with its surface. A more accurate description is a scaled down version of spatial frequency domain imaging (SFDI). By looking at the signal returned from projecting various structured patterns of light onto the tissue, we can gain information on the density of the tissue at various depths within the epithelium.
