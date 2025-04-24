# Ionosphere Mapping based GNSS Ground Station

## 1. Introduction

This assignment explores different aspects of GNSS technology. Task 1 compares advanced GNSS techniques like DGNSS, RTK, PPP, and PPP-RTK for smartphone navigation. Task 2 focuses on improving GNSS performance in challenging urban areas. Task 3 looks at RAIM (Receiver Autonomous Integrity Monitoring) to enhance positioning accuracy and detect errors. Task 4 discusses the challenges of using Low Earth Orbit (LEO) satellites for navigation, and Task 5 explores how GNSS is applied in remote sensing fields like reflectometry and ionosphere mapping.


## 2. Assignment Tasks

### 2.1 Task 1: Differential GNSS Positioning

#### **Differential GNSS (DGNSS)**

##### **Technical Overview**

Differential GNSS (DGNSS) is a technology that improves positioning accuracy by correcting GNSS signal errors. It uses one or more reference stations with known locations to calculate errors in GNSS signals (such as satellite orbit errors, clock errors, atmospheric delays, etc.), and broadcasts these correction information to nearby user receivers, which use these correction data to optimize positioning results.

The correction is expressed as:

$$
\Delta \rho = \rho_{\text{measured}} - \rho_{\text{true}}
$$

Where:
- $\Delta \rho$ is the correction for pseudorange measurements.
- $\rho_{\text{measured}}$ is the pseudorange measured by the reference station.
- $\rho_{\text{true}}$ is the actual pseudorange based on the reference station’s known position.

User receivers apply the correction:

$$
\rho_{\text{corrected}} = \rho_{\text{measured}} - \Delta \rho
$$

This method significantly reduces errors caused by satellite orbit inaccuracies, clock errors, and atmospheric delays, achieving sub-meter to centimeter accuracy.

---

##### **Pros, Cons and Future Directions in Smartphone Navigation**

DGNSS has a wide range of applications in smartphone navigation, which can significantly improve positioning accuracy. For example, in location-based services, augmented reality, and pedestrian navigation, DGNSS can provide sub-meter positioning accuracy. By accessing SBAS (such as WAAS, EGNOS) or commercial differential services, smartphones can receive correction data in real time without the need for additional hardware support. In addition, applications such as geotagging, fitness tracking, and ride-hailing services have also benefited greatly from the reliability and accuracy of DGNSS.

DGNSS brings significant advantages to smartphone navigation. First, it effectively reduces GNSS positioning errors and can achieve sub-meter or even centimeter-level accuracy. Second, DGNSS provides correction data through wide-area augmentation systems or commercial services, allowing users to use it over a large area without local base station support. Finally, DGNSS supports real-time corrections, which is suitable for scenarios that require fast response, such as dynamic navigation.

However, DGNSS also has some limitations. It has a strong dependence on correction signals and usually needs to receive correction data through the Internet, which may not be possible in remote areas with poor network coverage. In addition, smartphones have limited GNSS hardware performance, with weaker antenna sensitivity and signal processing capabilities than professional receivers. Multipath effects and signal blocking in urban environments can also weaken the effectiveness of DGNSS.

To improve the performance of DGNSS in smartphone navigation, future improvements include enhancing the GNSS hardware performance of smartphones (such as more sensitive antennas and more powerful processing chips). In addition, the use of high-speed network technologies such as 5G can more reliably transmit correction data. Finally, combining DGNSS with other technologies (such as RTK or PPP) can further improve its accuracy and reliability in complex environments.

---

#### **Real-Time Kinematic (RTK)**

##### **Technical Overview**

Real-Time Kinematic (RTK) is a high-precision GNSS technology that achieves centimeter-level positioning accuracy by measuring carrier phase rather than pseudorange. RTK relies on the base station to send correction data to the rover in real time. The key to RTK is to solve the integer ambiguity problem of the carrier phase, that is, to determine the integer number of wavelengths between the satellite and the receiver.

The corrected position is calculated as:

$$
\rho_{\text{corrected}} = \rho_{\text{measured}} - \Delta \rho - N \cdot \lambda
$$

Where:
- $\Delta \rho$ is the pseudorange correction.
- $N$ is the integer ambiguity.
- $\lambda$ is the wavelength of the carrier signal.

RTK achieves high accuracy by resolving $N$ and applying corrections to the carrier phase measurements.

---

##### **Pros, Cons and Future Directions in Smartphone Navigation**

RTK not only provides high-precision positioning services up to centimeters for smartphone navigation, but is also suitable for application scenarios such as autonomous driving, drone navigation, and augmented reality. RTK correction data is transmitted in real time via radio and mobile network services, allowing smartphones to dynamically adjust positioning results. In addition, some modern smartphones already support RTK functions, which has further promoted its application in consumer devices.

The advantages of RTK are its high accuracy and dynamic performance. Centimeter-level accuracy makes it ideal for high-end applications such as engineering surveying and drone flights. The real-time correction feature ensures stable performance in dynamic scenarios while supporting technologies such as autonomous driving and precision agriculture.

However, RTK also has some shortcomings. First, it has a high dependence on the base station, which usually requires the distance between the base station and the user receiver to be no more than 10-20 kilometers, which limits its applicability in remote areas. In addition, the high cost of RTK infrastructure and services hinders its large-scale application in the consumer field. Finally, multipath effects and signal blocking in urban environments interfere with carrier phase measurements and reduce the reliability of RTK.

As I understand it, in the future, the development of RTK should focus on reducing hardware costs and simplifying infrastructure. Improving the GNSS hardware performance of smartphones to better support RTK signals is the key. At the same time, combining RTK with other technologies (such as PPP or inertial navigation systems in mobile phones) can further improve its applicability in complex environments.

---

#### **Precise Point Positioning (PPP)**

##### **Technical Overview**

Precise Point Positioning (PPP) is a standalone GNSS technique that uses precise satellite orbit and clock corrections, along with advanced error modeling, to achieve decimeter to centimeter-level accuracy. Unlike DGNSS or RTK, PPP does not require a local base station. Instead, it relies on globally distributed reference stations to provide corrections.

The PPP position is calculated by correcting pseudorange and carrier phase measurements:

$$
\rho_{\text{corrected}} = \rho_{\text{measured}} - \Delta_{\text{orbit}} - \Delta_{\text{clock}} - \Delta_{\text{iono}} - \Delta_{\text{tropo}}
$$

Where:
- $\Delta_{\text{orbit}}$ and $\Delta_{\text{clock}}$ are satellite orbit and clock corrections.
- $\Delta_{\text{iono}}$ and $\Delta_{\text{tropo}}$ are ionospheric and tropospheric delay corrections.

---

##### **Pros, Cons and Future Directions in Smartphone Navigation**

Because of its principle design, PPP is available worldwide and is particularly suitable for smartphone navigation in remote or rural areas without local base stations. Its decimeter-level positioning accuracy supports mapping, location tracking, and location-based services. In addition, the most notable feature is that PPP does not require base station support, which reduces infrastructure dependence and expands its scope of application in smartphones.

The advantage of PPP lies in its global applicability, which can achieve high-precision positioning anywhere there is a GNSS signal without the need for local base stations. Its decimeter to centimeter-level positioning accuracy supports a variety of applications in urban and remote areas. In addition, as a stand-alone technology, PPP is easier to operate and users do not need to rely directly on ground base stations.

However, PPP also has some limitations. Its main disadvantage is that it has a long convergence time, which usually takes 10-30 minutes to achieve full accuracy, which may cause delays in time-sensitive applications. In addition, multipath effects and signal blocking in urban environments affect its performance. Finally, PPP's reliance on precise correction models and advanced algorithms increases the complexity of its implementation.

Based on my understanding of PPP, PPP should focus on shortening convergence time through multi-constellation GNSS systems. Further combining PPP with RTK (i.e. PPP-RTK) can provide a balance of accuracy and speed. In addition, improved GNSS hardware in smartphones and more accurate error modeling will further unleash the potential of PPP in consumer applications.

---

#### **PPP-RTK**

##### **Technical Overview**

PPP-RTK combines the strengths of PPP and RTK to achieve centimeter-level accuracy with rapid convergence times. It uses globally distributed reference stations to provide precise satellite orbit and clock corrections (as in PPP), while also applying localized corrections (as in RTK) for faster ambiguity resolution.

The PPP-RTK position is calculated as:

$$
\rho_{\text{corrected}} = \rho_{\text{measured}} - \Delta_{\text{PPP}} - \Delta_{\text{RTK}}
$$

Where:
- $\Delta_{\text{PPP}}$ includes precise satellite orbit, clock, and atmospheric corrections.
- $\Delta_{\text{RTK}}$ includes real-time local corrections and ambiguity resolution.

---

##### **Pros, Cons and Future Directions in Smartphone Navigation**

PPP-RTK is able to provide centimeter-level positioning services with fast algorithm convergence, which makes it very suitable for dynamic application scenarios such as navigation, augmented reality and automated systems. By combining global and local corrections, PPP-RTK can also provide stable performance in complex environments.

The advantage of PPP-RTK is that it combines the high accuracy of RTK with the global coverage of PPP. Its fast convergence time makes it suitable for real-time scenarios, while the combination of global and local corrections ensures stable performance. This makes PPP-RTK an ideal choice for high-end navigation and geospatial data collection.

At the same time, PPP-RTK also faces challenges. Because its infrastructure is relatively complex, it requires the support of global and local correction networks. The high cost of correction services may limit its popularity in consumer applications. In addition, smartphones require advanced GNSS hardware to fully support PPP-RTK, which is not yet fully popular on all current smartphones.

Future improvements should include simplifying the PPP-RTK algorithm to make it easier to implement on consumer devices. Developing lower-cost correction services and improving GNSS hardware will be the key to the popularity of PPP-RTK. In addition, combining PPP-RTK with other technologies can further improve its performance in complex environments.

### 2.2 Task 2: GNSS in Urban Areas

#### **Task Overview**
The objective is to improve GNSS positioning accuracy in urban environments, which are affected by signal blockage, multipath effects, and poor satellite visibility. A skymask file (`skymask_A1_urban.csv`) is provided to indicate satellite visibility blockage based on azimuth and elevation angles. The task involves using this skymask to filter obstructed satellites and enhance the positioning solution.

#### **Ground Truth Coordinates**
- **Latitude**: 22.3198722  
- **Longitude**: 114.209101777778  
- **Altitude**: 3.0 m  

---

#### **Approach**

To improve positioning accuracy, the following steps were planned:

1. **Use the skymask for satellite selection**: Filter out satellites obstructed by urban structures using the skymask.
2. **Switch to Weighted Least Squares (WLS)**: Apply weights to satellites based on elevation angles or signal-to-noise ratio (SNR).
3. **Enable RAIM (Receiver Autonomous Integrity Monitoring)**: Detect and exclude faulty satellites.
4. **Optimize skymask smoothing**: Ensure the skymask is accurate and smooth enough to represent realistic satellite visibility.

---

#### **Implementation Process**

##### **Step 1: Load and Smooth the Skymask**
The skymask (`skymask_A1_urban.csv`) was read and processed to create a continuous satellite visibility function:
- **Raw Data**: Azimuth and elevation angles representing satellite visibility blockage.
- **Smoothing**: Cubic spline interpolation (`csaps`) was applied to smooth the skymask data.

```matlab
angles_smooth = linspace(min(angles), max(angles), 1e4); % Smooth 10,000 points
smoothing_param = 0.95; % Slight smoothing for better detail
pp = csaps(angles, elevations, smoothing_param);
elevations_smooth = fnval(pp, angles_smooth);
settings.sys.skymask = [angles_smooth', elevations_smooth'];
```
##### **Step 2: Enable Skymask Filtering**
The system was configured to use the skymask for satellite visibility filtering during navigation.

```matlab
settings.sys.skymask_type = 1; % Enable skymask filtering
```

##### **Step 3: Switch to Weighted Least Squares (WLS)**
The position estimation method was changed to Weighted Least Squares (WLS), prioritizing satellites with higher elevation angles for better accuracy.

```matlab
settings.sys.ls_type = 1; % Switch to Weighted Least Squares
```

##### **Step 4: Enable RAIM**
RAIM (Receiver Autonomous Integrity Monitoring) was enabled to detect and exclude faulty satellites.

```matlab
settings.sys.raim_type = 0; % Enable RAIM for fault detection
```

##### **Step 5: Execute Navigation**
The navigation solution was computed using the processed observation (obsData), satellite (satData), and ephemeris (ephData) data.

```matlab
[obsData, satData, navData] = doNavigation(obsData, settings, ephData);
```

#### **Challenges Encountered**

While implementing the skymask filtering, I encountered a technical issue that prevented the navigation solution from producing results. Specifically, the integration of the skymask data from skymask_A1_urban.csv into the navigation system failed due to inconsistencies in the skymask data.

##### **Details of the Issue**
The skymask smoothing process produced invalid elevation values for certain azimuth angles.

These issues caused the skymask filtering mechanism to malfunction, preventing valid satellite selection during the navigation process.

Despite implementing skymask filtering, WLS, and RAIM, the failure to properly integrate the skymask data into the navigation system resulted in no output. 

### 2.4 Task 4: LEO Satellites for Navigation

Low Earth Orbit (LEO) satellites are widely used in the communication field of various industries due to their low orbital altitude (usually 500 to 2000 kilometers). In recent years, with the launch of LEO satellites and the rapid development of their constellations, their potential in the field of navigation has gradually attracted the attention of the GNSS industry. However, it is still very challenging to use LEO communication satellites for navigation, and its technical implementation faces many difficulties and challenges. I will discuss in detail the main issues of LEO communication satellites in navigation applications from aspects such as orbital characteristics, system complexity, signal transmission and multipath effects, combined with my understanding.

#### **Challenges Brought by Orbital Characteristics**

The orbital altitude of LEO satellites is much lower than that of medium earth orbit (MEO) satellites used in traditional GNSS (such as GPS and Beidou). This feature brings both advantages and challenges. From the perspective of advantages, the low orbital altitude of LEO satellites makes its signal transmission delay lower and the signal strength higher, which can provide navigation users with higher accuracy and faster response speed. However, this low orbit characteristic also causes a series of problems.

The most fatal challenge is that due to the small coverage of LEO satellites, a single satellite cannot cover a large area. Therefore, in order to achieve global navigation coverage, LEO constellations need to deploy a large number of satellites to form a dense constellation, which significantly increases the complexity and construction cost of the system. Compared with the traditional GNSS constellation that only needs to deploy dozens of satellites, the LEO navigation system may require hundreds or even thousands of satellites to achieve the same global coverage capability.

Secondly, it should be noted that the orbital period of LEO satellites is short, generally between 90 and 120 minutes, which results in a very limited visible time of the satellite on the ground, usually only a few minutes. Users need to frequently switch visible satellites for positioning, which puts higher requirements on the navigation algorithm. In addition, the high-speed movement of LEO satellites will bring about a more significant Doppler effect, and user equipment will also require higher-precision frequency tracking capabilities, which further increases the complexity of receiver design.

#### **System Complexity and Constellation Management Challenges**

The core of implementing or designing LEO satellite navigation systems lies in the coordination and management of large-scale constellations. As just mentioned, compared with traditional MEO satellites, LEO satellites are numerous and have complex orbits, so the real-time management and scheduling of our constellations are extremely demanding.

In detail, in a large constellation, communication and data exchange between satellites become a major challenge. LEO satellites need to collaborate and link data efficiently through inter-satellite links (ISLs) to ensure the rapid transmission and update of navigation information. However, inter-satellite link technology is not yet mature, especially in large-scale constellations, low-latency and high-reliability communications still face technical bottlenecks. In addition, the high power consumption requirements of inter-satellite links will also put great pressure on the energy supply of satellites, and further increase the manufacturing and orbiting costs of individual satellites.

In addition, the lifespan of LEO satellites is usually short, generally 5-7 years, while the lifespan of MEO satellites can reach more than 15 years. This means that LEO constellations need to frequently replace and supplement satellites to maintain the normal operation of the system. This high frequency of launch and maintenance requirements not only greatly increases the operating cost of the system, but also places extremely high demands on the launch capability.

Finally, the time synchronization problem of the multi-satellite system is also a major problem. Due to the low orbital altitude, LEO satellites are easily disturbed by factors such as the earth's gravitational field and solar radiation pressure, resulting in a large orbital deviation of the satellite per unit time, which puts higher requirements on the time synchronization accuracy and orbit determination accuracy of the constellation. If the time synchronization error cannot be effectively curbed, it will also directly affect the accuracy of navigation positioning.

#### **Challenges of Signal Transmission and Multipath Effects**

Another major difficulty in using LEO satellites for navigation is the reliability and anti-interference ability of signal transmission. Traditional GNSS signal design is mainly aimed at the characteristics of MEO satellites, while the signal transmission environment and requirements of LEO satellites are different.

For example, the low orbit altitude of LEO satellites mentioned in the previous section makes its signal path more susceptible to the influence of the Earth's ionosphere and troposphere. Especially in the case of intense ionospheric activity, the propagation delay and attenuation of the signal may increase significantly. This places higher demands on the error modeling ability of the navigation system.

This problem also leads to another problem, that is, the signal frequency and transmission power of LEO satellites are usually linked to communication needs rather than navigation needs. Communication satellites usually use wide-band high-throughput signals, which is not ideal for navigation. On the one hand, wideband signals may greatly increase the processing complexity of navigation receivers; on the other hand, high-throughput signals have weak anti-interference capabilities and are easily interfered by other radio sources, that is, they are more easily distorted. In addition, the signal beam design of communication satellites usually favors ground stations rather than user equipment, which may lead to uneven coverage of navigation signals.

It is also worth mentioning that the multipath effect has become particularly significant in LEO satellite navigation. Due to the low orbital altitude of LEO satellites, their signals are easily reflected on the surfaces of obstacles such as ground buildings and mountains, forming multiple multipath signals. This multipath effect is particularly serious in urban environments and may significantly reduce the accuracy of navigation positioning. The multipath effect suppression algorithm of traditional GNSS receivers may not be fully adapted to the special environment of LEO satellites, so new algorithms or new paradigms need to be developed to solve this problem.

#### **Potential Solutions**

Although LEO communication satellites face many challenges in navigation applications, it is undeniable that their potential for application in the GNSS field is still huge, especially in the field of high-precision navigation and positioning. Based on the summary of the above shortcomings, I think we can think about it from the following aspects.

First, in view of the high dynamic characteristics of LEO satellites, more advanced receiver technology can be developed. For example, multi-band signal design and more accurate Doppler frequency tracking algorithms can be used to cope with the high-speed movement and Doppler effect of LEO satellites. In addition, the navigation method that integrates multiple constellations (such as LEO and MEO constellations) can also improve the reliability and accuracy of the system.

Second, in terms of system design, the constellation configuration and inter-satellite link technology can be further optimized to reduce the complexity of constellation management and communication. For example, by using artificial intelligence technology to optimize satellite scheduling strategies and improve constellation operation efficiency. At the same time, develop low-power, high-reliability inter-satellite link communication technology to support efficient collaboration of large-scale constellations.

Finally, in terms of signal design, LEO navigation systems need to design more robust signals for multipath effects and interference problems. Using narrow beam signals or beamforming technology to reduce the impact of multipath signals is a method worth trying. In addition, LEO satellite signals can be corrected in conjunction with ground enhancement systems (such as existing base station networks) to improve signal transmission reliability and navigation accuracy.

### 2.5 Task 5: GNSS Remote Sensing

With the continuous development of GNSS technology, its potential in the field of remote sensing has gradually emerged, especially in seismology. GNSS seismology has opened up a new path for earthquake research and disaster response by monitoring crustal movement and surface deformation caused by earthquakes in real time. As I come from the Department of Land Surveying and Geo-Informatics, I will discuss the application and potential of GNSS in seismology from the perspective of geodetic surveying, from the aspects of technical principles, application scenarios, advantages and challenges.


#### **Principles of GNSS Seismology**

GNSS seismology is a discipline that uses GNSS receivers to accurately measure crustal movement to detect earthquakes and other related disasters. Its core is to use the high-precision positioning function of GNSS signals to monitor the displacement and deformation of ground control points. Compared with traditional triangulation, this service is basically based on real-time and dynamic, and is seamless observation, which is very revolutionary. It can be said that the current mainstream earthquake monitoring is based on GNSS technology.

Principles of GNSS earthquake detection and research:

RTK and PPP: RTK technology uses the relative positioning between the base station and the mobile station to achieve high-precision displacement measurement in a short time. PPP technology relies on precise orbit and clock corrections and can achieve high-precision positioning without the support of the base station. These two technologies provide technical guarantees for monitoring instantaneous crustal displacement caused by earthquakes.

Carrier phase observation: The high accuracy of GNSS seismology is mainly due to the use of carrier phase observation data. Compared with pseudo-range observation, carrier phase measurement has higher accuracy and can be used to capture small surface deformations caused by earthquakes.

Data processing and model inversion: After spatial and temporal filtering and error correction, the displacement data collected by the GNSS receiver can be used to construct a surface deformation model when an earthquake occurs. Through inversion calculation with the seismological model, key information such as the epicenter location, magnitude, and fault slip can be inferred.

#### **Main application scenarios of GNSS seismology**

The application of GNSS seismology in the field of remote sensing has broad social significance and academic value, especially in earthquake monitoring, disaster assessment and crustal dynamics research. I will introduce the application of GNSS in seismology from the beginning, middle and end of the earthquake.

GNSS can monitor the surface deformation caused by earthquakes in real time, providing important data support for earthquake early warning. When an earthquake occurs, GNSS receivers can capture the rapid displacement changes of the crust within seconds to tens of seconds, and quickly evaluate the source mechanism and magnitude through data processing and model inversion. This real-time monitoring capability is crucial to reducing the impact of earthquake disasters. For example, in the Great East Japan Earthquake in 2011, GNSS data was used to quickly determine the epicenter and fault slip mode of the earthquake, providing an important reference for disaster prevention and mitigation.The slip of submarine faults caused by earthquakes may lead to tsunamis. GNSS seismology can quickly identify earthquake events that may cause tsunamis by monitoring the crustal movement in coastal areas, and monitor the changes in sea level height in combination with the ocean GNSS buoy system, thereby achieving efficient tsunami early warning.

GNSS seismology also provides new tools for geodynamic research. By monitoring crustal movement over a long period of time, scientists can study phenomena such as plate tectonic activity, accumulated strain on faults, and periodic release of earthquakes. For example, in active tectonic zones such as the Qinghai-Tibet Plateau and the Himalayas, GNSS monitoring reveals the dynamic process of plate collision and provides important data support for understanding the causes of earthquakes around the world.】

After an earthquake, GNSS data can be used for post-disaster assessments, such as measuring fault displacement, surface subsidence, and topographic changes. This information is of great significance and reference for planning post-disaster reconstruction and for the government to formulate emergency response strategies.

#### **Advantages of GNSS seismology**

GNSS technology has unique advantages over traditional earthquake monitoring equipment (such as seismometers). GNSS seismology can directly measure the three-dimensional displacement of the surface, while traditional seismometers mainly record ground acceleration and velocity, which cannot intuitively reflect the spatial distribution of surface deformation. The absolute displacement measured by GNSS has higher physical significance for studying and judging earthquake fault slip and source mechanism.

In spatial terms, the global coverage of GNSS systems enables earthquake monitoring to be carried out worldwide, especially in remote areas far away from the seismometer network. For example, it is difficult to monitor submarine earthquakes, and GNSS seismology can monitor crustal movement in ocean areas through submarine GNSS buoy systems.

In temporal terms, GNSS seismology has good time continuity and real-time performance. GNSS receivers can record crustal movement at high frequencies (such as 1 Hz or higher), ensuring that the complete deformation process is captured at the moment of the earthquake. This high temporal resolution data is of great significance for rapid source inversion and disaster response.

## 3. Reference Lists

Yoon, D., Kee, C., Seo, J., & Park, B. (2016). Position accuracy improvement by implementing the DGNSS-CP algorithm in smartphones. Sensors, 16(6), 910.
Bisnath, S., & Gao, Y. (2009). Precise point positioning. GPS world, 20(4), 43-50.
Teunissen, P. J. G., & Khodabandeh, A. (2015). Review and principles of PPP-RTK methods. Journal of Geodesy, 89(3), 217-240.
Takasu, T., & Yasuda, A. (2009, November). Development of the low-cost RTK-GPS receiver with an open source program package RTKLIB. In International symposium on GPS/GNSS (Vol. 1, pp. 1-6). Seogwipo-si, Republic of Korea: International Convention Center Jeju Korea.
Li, X., Ma, F., Li, X., Lv, H., Bian, L., Jiang, Z., & Zhang, X. (2019). LEO constellation-augmented multi-GNSS for rapid PPP convergence. Journal of Geodesy, 93, 749-764.
Ge, H., Li, B., Jia, S., Nie, L., Wu, T., Yang, Z., ... & Ge, M. (2022). LEO enhanced global navigation satellite system (LeGNSS): Progress, opportunities, and challenges. Geo-spatial Information Science, 25(1), 1-13.
Kassas, Z., Neinavaie, M., Khalife, J., Khairallah, N., Kozhaya, S., Haidar-Ahmad, J., & Shadram, Z. (2021). Enter LEO on the GNSS stage: Navigation with Starlink satellites.
Jin, S., Occhipinti, G., & Jin, R. (2015). GNSS ionospheric seismology: Recent observation evidences and characteristics. Earth-Science Reviews, 147, 54-64.
Li, X., Guo, B., Lu, C., Ge, M., Wickert, J., & Schuh, H. (2014). Real-time GNSS seismology using a single receiver. Geophysical Journal International, 198(1), 72-89.

## 4 Acknowledgement
Task1 and task 4 of this report used the GenAI model for information collection and brainstorming. But it does not involve direct plagiarism and copying. 

```matlab
Model: ChatGPT 4o
Chatroom Link: https://poe.com/s/71fGKmxlY1SIpbwIErAI
```
