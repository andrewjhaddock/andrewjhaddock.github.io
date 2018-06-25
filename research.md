---
layout: page
title: Research
permalink: /research/
---

#### **Automated Deep Brain Stimulation Programming**

Deep brain stimulation (DBS) programming is a basic aspect of clinical care for patients, yet it is an especially challenging and resource-intensive procedure for clinicians to complete. Currently, patients travel potentially great distances to a DBS clinic to be seen by a specialist who then systematically fine-tunes stimulation parameters (stimulation contact, amplitude, frequency, and pulsewidth) in order to achieve satisfactory therapy, which is determined on the basis of standardized clinical rating scales and patient reports of side effects that can be induced by DBS, including muscle contractions or tingling, speech difficulty, double vision, mood changes, and more.

As DBS electrode technology evolves the number of potential DBS parameters for patient therapy is expanding rapidly, and this poses an even greater challenge to clinicians in efficiently identifying the optimal therapy settings for a patient in a short clinic visit. An alternative approach is to use a software-based approach in which an integrated system controls a patient's implanted DBS settings, receives feedback on patient symptoms and side effects, and uses this information to _automatically_ determine the optimal therapy settings, without the need for human intervention. Wearable and implanted sensors can potentially provide surrogate assessments of disease state, especially in movement disorders such as **Parkinson's disease** (PD) and **essential tremor** (ET), which are, to date, the primary indications for DBS surgery.

<img align="right" src="https://i.imgur.com/ymjBiSi.png" width="50%" height="50%">

For my dissertation research, I explored this idea in collaboration with the UCSF Movement Disorders and Neuromodulation Center by using a custom API to communicate with patients' implanted DBS systems in a clinical experiment. Together, we developed a software system that was suitable for clinical use, with patient safety and acceptance being paramount concerns, and the study objective being to demonstrate automated DBS programming that was _at least as effective_ as expert clinicians in selecting DBS therapy parameters for patients. Tremor severity was assessed in each DBS setting tested using smartwatch IMU data with a multinomial logistic regression model that was fit to hundreds of examples of tremor with clinical ratings provided by movement disorder neurologists.

<img align="right" src="https://i.imgur.com/N5J0Q0x.png" width="75%" height="75%">

As every patient has unique disease course, physiology, and reponse to DBS, automated programming algorithms must be adaptable and robust to uncertainty. In our pilot study with 10 patients (4 with ET, 6 with PD), we tested patients in two stages: first, we completed a brute-force search of the parameter space; then, we used the initial search results to formulate a patient-specific model, which was used to optimize therapy settings by using a multi-armed bandit algorithm to sequentially test DBS settings that were believed to provide acceptable therapy.

The results of this study showed that automated DBS programming was _at least as effective_ as expert clinicians in selecting optimal therapy settings for patients. Additionally, we found that the power expenditure for automated DBS settings was significantly lower than that of clinically-defined DBS settings, which may reflect a clinical bias towards selecting more energy-intensive (i.e. battery depleting) DBS settings. 

<img src="https://i.imgur.com/DgXllOD.png" width="100%" height="100%">

**A. Haddock**, K. T. Mitchell, A. Miller, J. L. Ostrem, H. J. Chizeck, S. Miocinovic, "Automated deep brain stimulation programming for tremor" to appear in _IEEE Transactions on Neural Systems and Rehabilitation Engineering_, 2018.

#### **Neural Correlates of Effective Deep Brain Stimulation**

A corollary inquiry to the topic of automated DBS programming is whether stimulation parameters can be selected on the basis of neural signals _alone_. The pathophysiology of both PD and ET suggests a neural mechanism for movement disorders - possibly excessive neural synchrony or phase-amplitude coupling in motor system networks - and the efficacy of DBS in disrupting movement disorder symptoms strongly supports the hypothesis that stimulation functionally disrupts the neurophysiological mechanisms underlying these neurodegenerative diseases. However, despite these sucesses in demonstrating the effects of DBS on cortical oscillations in PD and ET patients in operating room studies, it is unknown how effective vs. ineffective DBS alters neural activity, especially in chronically implanted patients. Neural-based DBS programming could also eliminate the need for patients to perform overt movement disorder symptom testing and potentially serve as a more reliable biomarker for programming than symptoms, which can vary unpredictably.

<img align="right" src="https://i.imgur.com/yMXPCD1.png" width="70%" height="70%">

To investigate the possibility of neural-based DBS programming, at UW we are conducting ongoing experiments with 4 ET patients who are implanted with an electrocorticographic (ECoG) electrode strip over motor/sensory cortex in addition to the typical DBS leads implanted in thalamus. Neural activity from motor cortex (bipolar referenced against sensory cortex) is recorded as local field potentials from ECoG while randomly cycling through DBS settings as in the previous study. In each DBS setting, ECoG activity is recorded for 30 seconds while the patient is at rest in addition to the tremor tests performed to assess symptoms. Effective vs. ineffective DBS settings are discriminated based on having greater or less than 90% of the total improvement seen in tremor across all tested settings. In our initial testing with 3 of the 4 patients, effective DBS settings were associated with significantly lower theta (4-8Hz), alpha (8-13Hz), and low beta (13-20Hz) signal power, compared with ineffective DBS and off DBS conditions. These results are indicative of a possible biomarker for effective therapy in ET by which DBS settings can be selected.

**A. Haddock**, H. J. Chizeck, A. L. Ko, "Neural correlates of effective deep brain stimulation", presented at the American Society of Stereotactic and Functional Neurosurgery Annual Meeting, 2018.

#### **Deep Learning Applications in Biomarker Discovery**

In addition to my DBS-centric research, I am exploring a number of applications of deep learning methodologies to uncover biomarkers of disease or activity state from large datasets. Because generalizable biomarkers, or features, can take many years or decades of research to discover, deep learning may be especially useful in this domain, as it is capable of _automated feature extraction_ from data. Deep learning architectures are capable of learning highly nonlinear representations of data, and this may be especially useful in domains like neuroscience where cross-frequency coupling and other nonlinear phenomena may encode useful information.

#### **Parkinsonian Speech Analysis to Predict Medication State**

I am using the [mPower mobile Parkinson's disease data set](https://parkinsonmpower.org/) to develop a model that predicts medication state from monosyllabic speech samples recorded from smartphones. This data set contains over 65,000 voice samples from thousands of participants, including hundreds of patients diagnosed with PD. Speech samples are labeled with medication state (ON meds, OFF meds), which is in effect an indicator of symptom severity, and also contains survey data about other aspects of PD impairment (motor, speech, depression, cognition).

<img align="right" src="https://i.imgur.com/CgjkElC.png" width="70%" height="70%">
I am testing multiple deep learning approaches to developing models for medication state prediction: **1)** a spectrogram-based approach in which raw audio data is transformed into a short-time Fourier transform representation and fed into a deep convolutional neural net (CNN) as a set of images, and **2)** a time-series approach in which raw audio is directly fed into a CNN preceding multiple layers of a recurrent neural network (RNN). Initial results using method 1 have yielded medication state prediction accuracies close to 90%, which greatly outperforms standard machine learning algorithms (SVM, LDA, MLR) using hand-picked features such as mel-frequency cepstral coefficients and other frequency domain representations of speech. The medication state classifier may be used in applications such as medication reminder systems for PD patients with cognitive/memory deficits, remote monitoring of symptoms for neurology clinics, and potentially in closed-loop and automated DBS programming applications as a feedback signal for therapeutic efficacy.

**A. Haddock**, A. L. Ko, R. H. Ghomi, "Deep Learning Methodologies for Predicting Parkinsonian Medication State from Monosyllabic Speech Recordings", _in preparation_.

#### **Activity Recognition from Chronic ECoG Implants**

Much of the extant work in brain-computer interfaces (BCI) and closed-loop DBS in ET relies on discriminating neural signals related to arm/hand movement vs. rest. Many human studies have recorded LFPs from ECoG arrays placed atop the arm/hand area of motor cortex and found that, relative to rest, movement is characterized by significant beta band desynchronization and an increase in high-gamma signal power. However, the predictive capabilities of these features is somewhat limited, typically hovering around 75-80% in chronically implanted patients, and this level of performance may not be suitable for BCI or closed-loop DBS, which rely on fast, accurate prediction of activity state to maintain an effectively responsive system.

<img align="right" src="https://i.imgur.com/sFbt6Tq.png" width="50%" height="50%">

Currently I am working on applying a deep learning architecture, consisting of a CNN stacked on top of several RNNs, to increase predictive performance in this application. I am also investigating whether these architectures can discriminate between different types of movement - rest, postural maintentance, visually guided movements, and rhythmic arm movements as in walking.

**A. Haddock**, A. L. Ko, "Activity Recognition from Chronically Implanted Electrocorticography with Recurrent Neural Networks", _in preparation_.

