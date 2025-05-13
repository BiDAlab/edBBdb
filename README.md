![Sin titulo](/imgs/new_edBB_logo.png)
***
# About
We present a platform [1] for student monitoring in remote education consisting of a collection of sensors and software that capture biometric and behavioral data. We define a collection of tasks to acquire behavioral data that can be useful for facing the existing challenges in automatic student monitoring during remote evaluation. Additionally, we release an initial database including data from 38 different users completing these tasks with a set of **basic sensors:** webcam, microphone, mouse, and keyboard; and also from more **advanced sensors:** NIR camera, smartwatch, additional RGB cameras, and an EEG band. Information from the computer (e.g. system logs, MAC, IP, or web browsing history) is  also stored. **This information is avalible on this web [[Download Database](#instructions-for-downloading-edBB)].**

The following table shows the sensors and the information captured:

![Sin titulo](/imgs/tabla.jpg)


During each acquisition session each user completed three different types of tasks generating data of different nature: mouse and
keystroke dynamics, face data, and audio data among others. The tasks have been designed with two main goals in mind: i) analyse the capacity of such biometric and behavioral data for detecting anomalies during remote evaluation, and ii) study the capability of these data, i.e. EEG, ECG, or NIR video, for estimating other information about the users such as their attention level, the presence of stress, or their pulse rate.

<br/>The following sections describe the platform, the public database, the targets and share challenges with the community to advance in this area:


# Sensors

   The acquisition setup consisted of the next components: 

   - 3 individual **RGB cameras** (frontal, side, and cenital), and 1 **Intel Real-Sense** (model D435i), which is composed by 1 RGB and 2 Near Infrared sensors, and which also computes also depth images combining its 3 image channels.

   - A **Huawei Watch 2** that captures pulse information in real time and has also accelerometer, magnetometer, and gyroscope; useful to measure the arm movements.


   - An **EEG headset** by NeuroSky that captures 3 channels of electroencephalogram information. These data can be employed to know the focus level, stress, vigilance, etc. of the students
  
   - A **Personal Computer** with Microsoft Windows 10 OS, a microphone to acquire audio, a regular keyboard, a mouse, and a screen. The computer is employed both to complete the tasks and also to acquire the screen data, the mouse and keyboard dynamics, audio information during the evaluation, and several types of metadata (e.g. logging, app and web history, IP and MAC addresses, etc.)


# Tasks


The activities designed to conform the database consist of 8 different tasks that can be categorized in the following three groups:
 
 - **Enrollment form:** Its target consists in obtaining personal data of the users such as their name and surname, ID number, nationality, e-mail address, etc. This form is designed to acquire different events such as the mouse dynamics, clicks, mouse wheel, keyboard use, etc.
 
 - **Writing questions:** These comprehend questions that require a complex interaction from the user. They are oriented to measure the students’ cognitive abilities under different situations such as: solving logical problems, describing images, crosswords, finding differences, etc. Additionally, some activities have been designed to induce different states of emotions to the participants, e.g. stress or nervousness. These altered states are highly relevant when working with physiological and biological signals.
 
 - **Multiple choice questions:** These are questions aimed to detect the students’ attention and focus levels. Since multiple choice exams are largely used in online assessment platforms to evaluate their students, including these in our evaluation was essential.

The questions are selected from popular riddles and they present different levels of difficulty. The interface is designed to ensure data from different nature: free text typing (writing questions), fixed text typing (enrollment form), mouse movement (multiple choice questions), visual attention (describing images and finding differences), etc.


# Database and Challenges

The initial subset of the full database that is released with the present paper is composed by 38 users captured under controlled laboratory conditions during one session. The enrollment form includes demographic information from the user (age, gender, right-handed or left-handed). The demographic distribution of the learners is summarised in the following table.

<h3 align="center">Distribution of Learners by Medical Conditions and Gender</h3>

<div align="center">

<table>
  <thead>
    <tr>
      <th>Category</th>
      <th>Subcategory</th>
      <th>Percentage</th>
      <th>Number of Learners</th>
      <th>Average Age</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>Medical Conditions</td><td>No issues</td><td>---</td><td>34</td><td>---</td></tr>
    <tr><td></td><td>Heart murmur</td><td>---</td><td>1</td><td>---</td></tr>
    <tr><td></td><td>Heart condition</td><td>---</td><td>1</td><td>---</td></tr>
    <tr><td></td><td>Colour-blind</td><td>---</td><td>1</td><td>---</td></tr>
    <tr><td></td><td>Hypertension</td><td>---</td><td>1</td><td>---</td></tr>
    <tr><td>Overall Averages</td><td>Overall Average Age</td><td>---</td><td>---</td><td>24.8158</td></tr>
    <tr><td></td><td>Average Age of Male Learners</td><td>81.58%</td><td>31</td><td>25.0645</td></tr>
    <tr><td></td><td>Average Age of Female Learners</td><td>18.42%</td><td>7</td><td>23.7143</td></tr>
    <tr><td></td><td>Age Range</td><td>---</td><td>---</td><td>38–21</td></tr>
  </tbody>
</table>

<p><em><center>Note: Percentages for medical conditions are not shown because learners may have more than one condition.</center></em></p>

</div>



Additionally, we provide the performance (accuracy and time) achieved by each user in each specific task. Together with
the raw data obtained from the sensors, the database includes information processed to better understand and model the student behavior. This information is obtained using state-of-the-art algorithms:

- **Head Pose:** head pose (pitch, roll, and yaw) is estimated from the frontal webcam using the algorithm proposed in [2].

- **Mental State:** attention and meditation is estimated from the EEG signals according to the method developed by NeuroSky. The attention indicates the intensity of mental “focus”. The value ranges from 0 to 100. The attention level increases when a student focuses on a single thought or an external object, and decreases when distracted. The meditation indicates the level of mental relaxation. The value ranges from 0 to 100, and increases when users relax the mind and decreases when they are uneasy or stressed.

- **Face Biometrics:** size of the face (related to the distance to the front webcam) and authentication score are provided using the face detection algorithm proposed in [3] and the face authentication model [4].

Next figure shows an example of the information captured during the execution of the tasks:

![Sin titulo ](/imgs/imagen_articulo.jpg)

We have designed an acquisition protocol incorporating all sensors presented in the previous sections.Some of the sensors are used to capture the groundtruth for the different challenges proposed. **We propose 5 challenges related to the monitorization of different behaviors relevant for e-learning platforms.**

For each challenge, we propose target and input data. The goal is to train new artificial intelligence models capable of predicting the
target from the input data.
**The 5 challenges proposed in this work are:** 

- **Challenge 1 - Attention Estimation:** an estimation of the attention level of the students during the execution of e-learning tasks is a very valuable resource. We propose to estimate the band signals (level of attention) from patterns captured from the basic sensors. The head pose and gaze estimation from the webcam, together with the mouse and keystroke dynamics can be used to predict attention of the students. We have published a paper where an example of this challenge appears [5] and a database called [mEBAL](https://github.com/BiDAlab/mEBAL). **Target:** attention level obtained from the band signals. **Input:** front webcam video, mouse, and keystroke sequences. 

- **Challenge 2 - Anomalous Behavior Detection:** the detection of non-allowed behaviors during the execution of evaluation tasks is an important challenge necessary to improve the trustworthiness in e-learning platforms. Ten users were instructed to perform non-allowed activities during the execution of the tasks. These activities comprise the use of material/resources with the correct responses to the questions. We propose the use of a smartphone as a non-allowed resource. These users try to hide the smartphone in their pockets. These events are labelled with a timestamp that identify the exact period when cheating really occurred.. We propose to use the basic sensors to detect these events. **Target:** detection of nonallowed events. **Input:** front webcam video, microphone, mouse, and keystroke dynamics. 
<br/><br/>The following image shows an example of this challenge:


<p align="center"><img src="/imgs/CHALLENGE.png"></p>

- **Challenge 3 - Performance Prediction:** each task is evaluated and the performance is measured in terms of
accuracy (percentage of correct responses) and time spent to complete the task. We propose to estimate the performance of the student using both basic and advance sensors. **Target:** accuracy. **Basic Input:** front webcam video, mouse, and keystroke. **Advanced Input:** basic sensors plus pulse and EEC band signals. 

- **Challenge 4 - User Authentication:** student authentication is a critical step in a e-learning platforms. All users complete the same tasks, including the enrollment form that contains personal data. Data is anonymized but an ID number is provided to identify data from each user. The dataset is rich in biometric patterns useful for authentication (face, keystroke, mouse). **Target:** identity of the student. **Basic Input:** front webcam video, mouse, and keystroke dynamics. **Advanced Input:** IR cameras, smartwatch sensors, EEG band. 

- **Challenge 5 - Pulse Estimation:** the pulse is highly related to the emotional state and stress level of the students. In this challenge, we propose to estimate the pulse from the smartwatch using the front camera. Alternatively, the IR cameras can be used to analyse the potential of these sensors. We have published a paper where an example of this challenge appears [6]. **Target:** pulse of the student. **Basic Input:** front webcam video. **Advanced Input:** IR cameras.
- 




# Instructions for Downloading edBB

1) [Download license agreement](https://bidalab.eps.uam.es/static/licenses/edBB_License_Agreement.pdf), send by email one signed and scanned copy to **atvs@uam.es** according to the instructions given in point 2.

2) Send an email to **atvs@uam.es**, as follows:

   *Subject:* **[DATABASE: edBB]**

   Body: Your name, e-mail, telephone number, organization, postal mail, purpose for which you will use the database, time and date at which you sent the email with the signed      license agreement.

3) Once the email copy of the license agreement has been received at ATVS, you will receive an email with a username, a password, and a time slot to download the database.

4) [Download the database](https://bidalab.eps.uam.es/listdatabases?id=edBB#page), for which you will need to provide the authentication information given in step 4. After you finish the download, please notify by email to **atvs@uam.es** that you have successfully completed the transaction.

5) For more information, please contact: **atvs@uam.es**


# References

edBB is a platform which is initially introduced in [arXiv technical report](https://arxiv.org/abs/1912.04786) and then accepted by the [AAAI Workshop on Artificial Intelligence for Education 2020](http://www.cse.msu.edu/~wangzh65/AI4EDU/index.html).
 
For further information on the edBB platform, we refer the reader to: 
 
+ [1] Hernandez-Ortega, J.; Daza, R.; Morales, A.; Fierrez, J.; and Ortega Garcia, J. 2019. edBB: Biometrics and Behavior for Assessing Remote Education. In *AAAI Workshop on Artificial Intelligence for Education*. [[pdf](https://arxiv.org/pdf/1912.04786.pdf)]

+ [2] Ruiz, N.; Chong, E.; and Rehg, J. M. 2018. Fine-Grained Head Pose Estimation Without Keypoints.

+ [3] Zhang, K.; Zhang, Z.; Li, Z.; and Qiao, Y. 2016. Joint face detection and alignment using multi-task cascaded convolutional networks. *IEEE Signal Processing Letters*.

+ [4] Cao, Q., et al. 2018. VGGFace2: A dataset for recognising faces across pose and age.

+ [5] Daza, R.; Morales, A.; Fierrez, J.; and Tolosana, R. 2020. mEBAL: A Multimodal Database for Eye Blink Detection and Attention Level Estimation. In *ACM International Conference on Multimodal Interaction*. [[pdf](https://arxiv.org/pdf/2006.05327v2.pdf)]

+ [6] Hernandez-Ortega, J.; Daza, R.; Morales, A.; Fierrez, J.; and Tolosana, R. 2020. Heart Rate Estimation from Face Videos for Student Assessment: Experiments on edBB. In *IEEE Computers, Software, and Applications Conference*. [[pdf](https://arxiv.org/pdf/2006.00825.pdf)]

Please remember to reference articles [1] and [6] on any work made public, whatever the form, based directly or indirectly on any part of edBB database.




# Contact:

For more information contact Aythami Morales, associate professor UAM at aythami.morales@uam.es

