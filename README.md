# SaveDat
ML Based GPS Data Comoression

For deeper understanding of our work, please refer to the SaveDat paper we published:
  TODO: PAPER LINK

## Installing project
### Requirements

  Python Version 3.8.3
  * numpy 1.19.2
  * pandas 1.1.3

  #### Standard Python Modules
  * os 
  * random
  * shutil
  * datetime
  * time
  * socket
  * sys
  * threading
  * pickle
  * traceback
  * concurrent


  #### Simulator
  * json 2.0.9
  * re 2.2.1
  * haversine 2.3.1
  * pyproj 2.6.1
  * shapely 1.7.1
  * tensorflow 2.4.0
  * keras 2.4.3
  * sklearn 0.23.2

  #### UI
  * plotly 4.14.3
  * dash 1.20.0
  * dash_daq 0.5.0
  * dash_bootstrap_components 0.12.2
  * dash_core_components 1.16.0
  * dash_html_components 1.1.3


## Running the Poject
  1. Data source: https://drive.google.com/drive/folders/1AFY9MxoyZfKCfpbeH04Zqx2GaK54D96T?usp=sharing.
      In the above link you will find four CSV files.

  #### Running the UI
  1. Download Concluded_Data.csv file to "SaveDat\UI\data" directory.
  2. In terminal, go to "SaveDat" directory.
  3. Run "<python env var> SaveDat_UI.py".
  4. Open browser at "http://localhost:8050".

  #### Running the Simulator
  1. Download the three trajectories files to "SaveDat\Simulator\data" directory.
  2. In terminal, go to "SaveDat\src" directory.
  3. Run "<python env var> main.py".
  4. After executing "main.py", cli menu will suggest either.
     * 4.a "1" - Preprocessing and neural networks training (must be chosen at first execution).
     * 4.b "2" - Loading the models from the latter execution, skipping preprocessing and training.



## Using SaveDat Project

  #### Simulator
  1. Running "main.py" and choosing "1", will  split our data to train and test sets.
     The train set will be used for preprocessing, LSTM NN building, training and evaluating,
     and the test set for Client-Server real-time simulation.
     Choosing "2" in the cli menu will preform the client-server simulation as described in <Running the Simulator, 4.b>

  2. While the simulation runs, cli logs are preformed, indicating the completed steps, NN training data 
      provided by tensorflow, and client-server comunication updates

  3. At the end of the process, three directories will be generated:
      * 3.a 'Models' directory, contains tensorflow sequential models, and sklearn k-means model
      * 3.b 'Clients Data' directory, contains trajectories real-time generated data
      * 3.c 'Concluded Data' directory, contains the trajectories that was predicted by the server with acceptable error 

  #### UI
  1. In order to run the UI dashboard, 'Clients Data' (<Simulator, 3.b> above) files are being transform in a series
      of transformations executed by a single script that can be found in the "SaveDat\UI" directory, as "Clients Data Transformation"
      * 1.a Add extentions
      * 1.b Union dataframes
      * 1.c Rename Columns
      * 1.d Transform NAD38 to WGS84 COORDS
      * 1.e Fix labels
      * 1.f Data enrichment

  2. After completing the last step, locate the transformation output in the "SaveDat\UI\data" directory and launch "SaveDat.py"

  3. When the cli outputs that the dash application is running, use the browser to watch the client-server 
      comunication and data generated by the simulation



### Credits

Thanks to all of our team members:
* Shir Boxer : shirboxer@gmail.com
* Dan Shmirer : dshmirer@gmail.com
* Guy Cohen : guyc13@gmail.com
* Itai Blumenkrantz : itai6495@gmail.com
* Mike Lasry : mikelasry123@gmail.com

Thanks to our supervisor Dr.Horovitz Shay : shay.horovitz@gmail.com

Special thanks to U.S. Department of Transportation for "Next Generation Simulation" project, providing high 
  resolution geo-spatial and temporal data sets:
  https://data.transportation.gov/Automobiles/Next-Generation-Simulation-NGSIM-Vehicle-Trajector/8ect-6jqj

