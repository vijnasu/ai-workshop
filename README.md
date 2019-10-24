## **Intel AI workshop** </br>

1. Link to download the course - https://software.seek.intel.com/DataCenter_to_Edge_REG - Subscribe through your mail id. You will receive a mail having link to the course content (~250 MB). Don't download it now, I have uploaded the same in dropbox. </br>

2. Get Intel AI Devcloud access through https://software.intel.com/en-us/devcloud/datacenter/sign-up (Approved in 24 hours & retained for 4 weeks)</br>

```
User Name: u*****
Node Name: c***
Instructions: https://devcloud.intel.com/datacenter/?uuid=************************
```

2. Open the AI Devcloud in a browser: (https://devcloud.intel.com/datacenter/?uuid=************************)</br>
 
3. Connect with a Jupyter* Notebook - One Click Log In, which opens up a Jupyter GUI</br>

4. Click the 'New > Terminal' in the Top right corner. It will open up a new tab connecting to the terminal of AI Devcloud login node.</br>

5. Download, extract & rename the course folder. Navigate to the root directory of the class.</br>

```
wget https://www.dropbox.com/s/617aq0ft4khxucb/dc_to_the_edge.zip
unzip dc_to_the_edge.zip
mv 'DC to Edge Course' dc_to_edge_course
cd dc_to_the_edge_course/Notebooks
```

4. Create the conda environment (tf_training)</br>

```
conda env create -f environment.yml
```

5. Now, to add this environment to the list of available environments you’ll see in your Jupyter notebook by running:</br>

```
python -m ipykernel install --user --name tf_training --display-name "Python (tf_training)"
```

6. Run to activate the environment.</br>

```
conda activate tf_training
```

7. Navigate to the tab in your browser which has Jupyter GUI and refresh the folder using the refresh button in the top right corner.</br>

8. Click dc_to_edge_course and find download the "AI From the Data Center to the Edge An Optimized Path Using Intel Architecture.pdf" and refer this document through out the workshop.</br>

9. Navigate to Notebooks folder in Jupyter UI and start the course in order:-</br>

1) Part1-Exploratory_Data_Analysis.ipynb</br>
2) Part2-Training_InceptionV3-Student.ipynb</br>
3) Part3-Model_Analysis.ipynb (Quiz - Fetches a certificate from Intel on success. Attempt once. If failed, attempt later.</br>
4) Optional-OpenVINO_Video_Inference.ipynb</br>

10. **OpenVINO demos:-**</br>

Select the base conda kernal in the Jupyter notebook</br>

```
vi ~/.bash_profile</br>
```
---
```
source /glob/deep-learning/openvino/bin/setupvars.sh
```
---


**Build the samples:-**</br>
```
cd /glob/deep-learning/openvino/deployment_tools/inference_engine/samples</br>
./build_samples.sh</br>
```
Use the following library in the source code - </br>
```
$HOME/inference_engine_samples_build/intel64/Release/lib/libcpu_extension.so</br>
```

11. **Open Visual Cloud demos:-**</br>

![alt text](https://01.org/sites/default/files/users/u66592/ovc-_pipeline_v3.png)
</br></br>

    1 [CONTENT DELIVERY NETWORK (CDN) - TRANSCODE SAMPLE](https://github.com/OpenVisualCloud/CDN-Transcode-Sample)</br>
    2 [VIDEO CONFERENCING SAMPLE](https://github.com/OpenVisualCloud/Video-Conferencing-Sample)</br>
    3 [SMART CITY TRAFFIC MANAGEMENT SAMPLE](https://github.com/OpenVisualCloud/Smart-City-Sample)</br>
    4 [INTELLIGENT AD-INSERTION SAMPLE](https://github.com/OpenVisualCloud/Ad-Insertion-Sample)</br>
    5 [CLOUD GAMING FOR WINDOWS SAMPLE](https://github.com/OpenVisualCloud/Cloud-Gaming-Windows-Sample)</br>

12. **Open Source Reference Implementations:- https://software.intel.com/en-us/iot/reference-implementations**</br>

13. **OpenVINO Youtube Channel:-**
</br>
[![Watch the video tutorials](http://img.youtube.com/vi/kY9nZbX1DWM/0.jpg)](http://www.youtube.com/watch?v=kY9nZbX1DWM)
</br>

## **__Troubleshooting:-__**</br>

  1. If there is a protobuf, opencv, vmmr_utils error, it may be due to jupyter kernel not pointing to proper environment. To correct this in the terminal do the following:-</br>
```python
python
>>>import sys
>>>sys.executable
'/home/u****/.conda/envs/tf_training/bin/python'
>>>exit()
```

```
$jupyter kernelspec list</br>
```
Available kernels:</br>
  base             /home/u****/.local/share/jupyter/kernels/base</br>
  python3          /home/u****/.local/share/jupyter/kernels/python3</br>
  tf_training      /home/u****/.local/share/jupyter/kernels/tf_training</br>

```
$vi /home/u****/.local/share/jupyter/kernels/tf_training/kernel.json</br>
```

```
{
 "argv": [
  "REPLACE-THIS-WITH-THE-CORRECT-EXECUTABLE-PATH - /home/u****/.conda/envs/tf_training/bin/python",
  "-m",
  "ipykernel_launcher",
  "-f",
  "{connection_file}"
 ],
 "display_name": "heterodimers",
 "language": "python"
}
```
