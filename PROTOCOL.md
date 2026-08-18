# PROTOCOL: Evaluating Chest X-Ray AI for Tuberculosis Against the WHO Target Product Profile

**Author:** Anastasia Mistreanu
**Date:** 2026-08-18
**Version:** 1.0
**Status:** FROZEN — Version 1.0. Amendments recorded in §9 with date and rationale.

---

## 1. Intended Use

### 1.1 The simulated CAD system

The system being evaluated takes a single frontal digital chest X-ray and produces a continuous score representing how likely the image is to show signs of pulmonary tuberculosis. It does not provide a diagnosis. Instead, the score is compared with a predefined threshold, which determines whether the patient should be referred for further testing.

The intended population is people aged 15 and over presenting to a health post or primary care clinic with signs or symptoms of pulmonary TB, in a country with medium or high TB prevalence as defined by WHO (20 or more cases per 100,000 population). The intended user is a health worker with training up to the level of an auxiliary nurse and no formal radiology training. This is based on the target population, setting and user described in the minimal column of WHO TPP Table 6.

The system has one purpose: to determine whether a person should be referred for confirmatory bacteriological testing. It is intended to replace human reading of the chest X-ray, consistent with WHO Recommendation 10.

### 1.2 This audit

This project is a **methodological audit rather than a medical device**. The aim is to investigate how much performance can be overstated when TB CAD models are evaluated using commonly available public datasets compared with the methodology used by WHO.

The primary evaluation will measure **specificity at a threshold fixed to give 90% sensitivity**, using expert radiographic reading as the reference standard. WHO Table 4 reports the same type of performance measure for CE-marked CAD products, but those products were evaluated using a microbiological reference standard.

The difference between these results is therefore a major focus of the project. I will examine four possible sources of this difference:

1. Reference standard
2. Population and disease spectrum
3. TB prevalence
4. Train-test contamination

The model developed in this project is **not intended for clinical use**. The trained model weights will be for research purposes only and must not be used to make decisions about individual patients.

### 1.3 Use case and site assignment

[CONFIRM] The primary analysis will focus on the **triage use case**, where people present to a health facility with signs or symptoms of TB. WHO describes expected TB prevalence in this setting as approximately 10–20%.

The **Shenzhen dataset** (662 images from outpatient clinics, collected in September 2012) will be used as the primary dataset. The **Montgomery dataset** (138 images from a county TB screening programme) represents a different use case and will therefore be used for external validation rather than being combined with Shenzhen for the primary analysis.

The reason for selecting Shenzhen as the primary dataset is that it is more closely aligned with the intended triage population and has a larger sample size, which should give a more precise estimate of performance.

### 1.4 Out of scope

The system is explicitly **not intended** for:

1. **Diagnosis.** A positive result only determines whether someone should be referred for confirmatory testing. Treatment decisions require bacteriological confirmation.

2. **People under 15.** WHO Recommendation 10 applies to people aged 15 and over. CAD is not currently recommended for children and adolescents. [CONFIRM] Images from patients under 15 will therefore be excluded from the primary analysis, and the number excluded will be reported.

3. **Anteroposterior (AP) X-rays.** The WHO evidence base focuses on digital posteroanterior chest radiography. [CONFIRM] AP images will be excluded from the primary analysis. Some of the paediatric Shenzhen images are AP, so there may be overlap between the age and view exclusions. The exclusions will be applied in sequence and reported separately. If view position cannot be reliably identified from the available metadata, the limitation will be documented rather than assuming the view.

4. **Extrapulmonary TB.** The minimal requirements in WHO TPP Table 6 focus on pulmonary TB.

5. **Other chest diseases.** The system is designed specifically around TB screening and should not be interpreted as a general chest X-ray screening tool. A low TB score does not mean that the patient has no other lung or chest pathology.
