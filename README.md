# Intrusion Detection System
## Unsupervised Learning

### Overview

The goal of intrusion detection is to correctly distinguish between when the system is under attack and when the system is not under attack. The goal of this project is to minimize the number of false positives (ideally to zero) while at the same time maximizing the number of true positives. The code in this repository achieves this goal:

* The supplied model achieves a Matthews correlation coefficient of 0.886 on the test set (1.0 is perfect correlation, 0.0 is random guessing)

* The supplied model achieves a true positive rate of 0.840 on the test set (1.0 is best value)

* The supplied model achieves a false positive rate of 0.005 on the test set (0.0 is best value)

* The supplied model achieves these metrics even when the attacker manipulates the data from a compromised sensor to conceal their actions. A typical strategy found in the datasets is known as a replay attack, when the attacker records normal sensor data and then "replays" it when they actually carry out the attack, concealing the true abnormal sensor data.

Confusion matrix for the test dataset: 

![img](img/best_test.png)

### Domain

Industrial control systems (ICS) are computer systems that control the operation of industrial processes and historically have been designed to be operated in isolated environments. Increasingly over time components of these systems have been integrated into larger corporate networks and connected to the Internet without a corresponding attention to security. One domain where this has occurred is water distribution systems with the adoption of smart water technologies.

The Battle of the Attack Detection ALgorithms ([BATADAL](https://www.batadal.net)) was a recent competition to compare the performance of attack detection algorithms specifically for water distribution systems. There are three datasets provided by the [competition's website](https://www.batadal.net/data.html). They provide a simulated attack against a real, moderately-sized [water distribution system](https://www.researchgate.net/profile/Kegong_Diao/publication/235694686_Battle_of_the_Water_Calibration_Networks/links/00b7d5229e0cfe9afc000000.pdf). Each was generated by running extended-time hydraulic simulations with [EPANET toolkit](https://github.com/OpenWaterAnalytics/EPANET-Matlab-Toolkit).

### Files

report.md and report.pdf each contains the final written report.

img directory contains generated images for the written report

src directory contains python code for the project
* metrics.py implements necessary metrics 
* model.py implements classifier, including the final model
* preprocessing.py implements various preprocessing routines
* util.py implements loading and transforming datasets
* visualization.py implement plotting code

Scrips:
* best.py is a script to run the most successful configuration
* datasets.py is a script to download and label the datasets from the competition's website.
* experiments.py is a script to evaluate various configurations of models
* visualize.py is a script with visualization code.

### Data

The simulated attack data is obtained from the BATADAL [competition website](https://www.batadal.net/data.html).

Each dataset contains tabular data reporting the time stamp and the observed values from 43 selected sensors (not all the sensors in the network). 

Available readings are: 

* the date and time of the sensor reading ('DATETIME') in the format DD/MM/YY HH.

* the water level in meters for each of seven water tanks ('L_T1' through 'L_T7').
    
* the status (binary: 0 for off/closed, 1 for on/open) of elven pumps and one valve in the system ('S_PU1' through 'S_PU11' and 'S_V2').

* the flow in liters per second for each pump and valve in the system (pumps are 'F_PU1' through 'F_PU11' and the only valve is 'F_V2').

* the suction pressure and discharge pressure in pascals for twelve junctions in the system (e.g. 'P_J280' or 'P_J14'). For example, 'P_J280' is the suction pressure for the first pumping station ('PU1', 'PU2', 'PU3') and 'P_269' is the discharge pressure.

### Reference

Riccardo Taormina and Stefano Galelli and Nils Ole Tippenhauer and Elad Salomons and Avi Ostfeld and Demetrios G. Eliades and Mohsen Aghashahi and Raanju Sundararajan and Mohsen Pourahmadi and M. Katherine Banks and B. M. Brentan and Enrique Campbell and G. Lima and D. Manzi and D. Ayala-Cabrera and M. Herrera and I. Montalvo and J. Izquierdo and E. Luvizotto and Sarin E. Chandy and Amin Rasekh and Zachary A. Barker and Bruce Campbell and M. Ehsan Shafiee and Marcio Giacomoni and Nikolaos Gatsis and Ahmad Taha and Ahmed A. Abokifa and Kelsey Haddad and Cynthia S. Lo and Pratim Biswas and M. Fayzul K. Pasha and Bijay Kc and Saravanakumar Lakshmanan Somasundaram and Mashor Housh and Ziv Ohar; "The Battle Of The Attack Detection Algorithms: Disclosing Cyber Attacks On Water Distribution Networks." Journal of Water Resources Planning and Management, 144 (8), August 2018. ([doi link](http://dx.doi.org/10.1061/(ASCE)WR.1943-5452.0000969), [bib](https://www.batadal.net/taormina18battle.bib))

### License

MIT. See LICENSE.md for details.
