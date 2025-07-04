MoE-XGB Ground Motion Prediction Model
===
The repository serves as the code support for the manuscript A Mixture of Experts Model for Shallow Crustal Earthquake Ground Motion Prediction in Japan, enabling reproduction of the manuscript's content. MoE-XGB is an innovative ground motion prediction model combining the Mixture of Experts (MoE) architecture with the XGBoost algorithm, designed specifically for earthquake engineering and disaster assessment. By dynamically assigning weights through a gating network, the model effectively handles the heterogeneity of earthquake data, significantly improving prediction accuracy and generalization. MoE-XGB innovatively integrates latitude and longitude features of stations and seismic sources, enhancing its ability to characterize seismic wave propagation paths and regional tectonic properties. Trained on a 1997–2019 strong-motion dataset of shallow crustal earthquakes in Japan, the model reduces the mean squared error by 39.2%, decreases the standard deviation by 22.0%, and increases the correlation coefficient by 4.8% compared to the baseline XGBoost-SC model. Cross-regional testing on a New Zealand earthquake dataset further validates the model’s robust generalization across different geological conditions. By efficiently integrating spatial features and a dynamic expert mechanism, MoE-XGB provides a high-precision, reliable solution for ground motion prediction under complex geological conditions.

Repository Contents
---
MoE_XGB_Calling_Code.py: Python script to load the pre-trained MoE-XGB model and make predictions.

MoE-XGB.pickle: Pre-trained model file .

requirements.txt: List of required Python dependencies.

Requirements
----
To run the model, install the required Python libraries:
The requirements.txt includes:
xgboost==1.7.6
torch==2.3.0
numpy==1.26.4
pandas==2.2.2
matplotlib==3.9.0
scikit-learn==1.4.2
scipy==3.4.1
joblib==1.4.2

Input Parameters
-----
The model requires the following input features, in this exact order:
Depth. (km): Earthquake source depth (km)
Mag.: Magnitude (MJMA)
Rhypo: Hypo-central distance (km)
Vs30: Site condition (m/s)
Station Lat.: Station latitude (degrees)
Station Long.: Station longitude (degrees)
Long.: Seismic source longitude (degrees)
Lat.: Seismic source latitude (degrees)
Station Height(m): Station altitude (m)
mech: Focal mechanism ('R' for Reverse, 'S' for Strike-slip, 'N' for Normal)

Output
-----
The model outputs spectral accelerations (gal) for 35 periods:
PGA
SA0.01, SA0.02, ..., SA5

Outputs are saved as:

SA-output.txt: Text file with input parameters and predicted SA values.

SA-figure.png: Attenuation curve plot.



Usage
-------
Download the model file:

Place MoE-XGB.pickle in a local directory.

Edit the calling script:

Open MoE_XGB_Calling_Code.py in a text editor or IDE (e.g., PyCharm).

Modify the following sections:

modelFilePath: Path to MoE-XGB.pickle.

Input parameters: Set values for Depth_km, Mag, Rhypo, Vs30, Station_Lat, Station_Long, Long, Lat, Station_Height_m, mech.

txtFilePath: Directory for SA-output.txt (optional, leave empty to skip).

curveFilePath: Directory for SA-figure.png (optional, leave empty to skip).

Example configuration:

![image](https://github.com/user-attachments/assets/6ab7aff2-a9a1-428a-85aa-18028223a2f7)

Run the script:

Check outputs:

Console: Displays predicted SA values (PGA and periods 0.01s to 5s).

SA-output.txt: Contains input parameters and SA values (if txtFilePath is set).

SA-figure.png: Attenuation curve plot (if curveFilePath is set).


Example Output
----

![image](https://github.com/user-attachments/assets/0322b744-5fcd-4fa9-8ace-319addca2204)

![SA-figure](https://github.com/user-attachments/assets/2b255ab3-9ce4-4f21-a079-aeeb4f91382e)

SA-figure.png: A logarithmic plot of SA (gal) vs. period (s), with input parameters annotated.



Notes
---
Ensure MoE-XGB.pickle is compatible with the xgboost version specified in requirements.txt.

The model assumes input parameters are in the units specified above (e.g., km, degrees, m/s).


Contact
---
For questions or issues, please open an issue on the GitHub repository: https://github.com/daiyunze-09/MoE-XGB.












