## **Intel AI workshop** </br>

1. Link to download the course - https://software.seek.intel.com/DataCenter_to_Edge_REG - Subscribe through your mail id. You will receive a mail having link to the course content (~250 MB). Download and upload it to the server by wget or curl (You can follow the method provided below) </br>

2. Get Intel AI Devcloud access through https://software.intel.com/en-us/devcloud/datacenter/sign-up (Approved in 24 hours & retained for 4 weeks)</br>

```
User Name: u*****
Node Name: c***
Instructions: https://devcloud.intel.com/datacenter/?uuid=************************
```

3. Open the AI Devcloud in a browser: (https://devcloud.intel.com/datacenter/?uuid=************************)</br>
 
4. Connect with a Jupyter* Notebook - One Click Log In, which opens up a Jupyter GUI</br>

5. Click the 'New > Terminal' in the Top right corner. It will open up a new tab connecting to the terminal of AI Devcloud login node.</br>

6. Download, extract & rename the course folder. Navigate to the root directory of the class.</br>

```
wget https://<your_course_weblink>/dc_to_the_edge.zip (E.g., wget https://www.dropbox.com/s/617aq0ft4khxucb/dc_to_the_edge.zip)
unzip dc_to_the_edge.zip
mv 'DC to Edge Course' dc_to_edge_course
cd dc_to_the_edge_course/Notebooks
```

7. Create the conda environment (tf_training)</br>

```
conda env create -f environment.yml
```

8. Now, to add this environment to the list of available environments you’ll see in your Jupyter notebook by running:</br>

```
python -m ipykernel install --user --name tf_training --display-name "Python (tf_training)"
```

9. Run to activate the environment.</br>

```
conda activate tf_training
```

10. Navigate to the tab in your browser which has Jupyter GUI and refresh the folder using the refresh button in the top right corner.</br>

11. Click dc_to_edge_course and find download the "AI From the Data Center to the Edge An Optimized Path Using Intel Architecture.pdf" and refer this document through out the workshop.</br>

12. Navigate to Notebooks folder in Jupyter UI and start the course in order:-</br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1) Part1-Exploratory_Data_Analysis.ipynb</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2) Part2-Training_InceptionV3-Student.ipynb</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3) Part3-Model_Analysis.ipynb (Quiz - Fetches a certificate from Intel on success. Attempt once. If failed, attempt later.</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4) Optional-OpenVINO_Video_Inference.ipynb</br>

13. **OpenVINO demos:-**</br>

Select the base conda kernal in the Jupyter notebook</br>

```
vi ~/.bash_profile
```
Include the following line at the end of the file and save it.
```
source /glob/deep-learning/openvino/bin/setupvars.sh
```

**Build the samples:-**</br>
```
cd /glob/deep-learning/openvino/deployment_tools/inference_engine/samples
./build_samples.sh
```
Use the following library in the source code - </br>
```
$HOME/inference_engine_samples_build/intel64/Release/lib/libcpu_extension.so
```

14. **Open Visual Cloud demos:-**</br>

![alt text](https://01.org/sites/default/files/users/u66592/ovc-_pipeline_v3.png)
</br></br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1 [Content Delivery Network (CDN) - Transcode Sample](https://github.com/OpenVisualCloud/CDN-Transcode-Sample)</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2 [Video Conferencing Sample](https://github.com/OpenVisualCloud/Video-Conferencing-Sample)</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;3 [Smart City Traffic Management Sample](https://github.com/OpenVisualCloud/Smart-City-Sample)</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4 [Intelligent Ad-Insertion Sample](https://github.com/OpenVisualCloud/Ad-Insertion-Sample)</br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;5 [Cloud Gaming for Windows Sample](https://github.com/OpenVisualCloud/Cloud-Gaming-Windows-Sample)</br>

15. **Open Source Reference Implementations:- https://software.intel.com/en-us/iot/reference-implementations**</br>

16. **OpenVINO Youtube Channel:-**</br>

[![Watch the video tutorials](https://github.com/vijnasu/ai-workshop/blob/master/images/final_5db1565885d3500014a8e867_181580.gif)](http://www.youtube.com/watch?v=kY9nZbX1DWM)

17. **Data Analytics Acceleration Library (DAAL):-**</br>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1. Installation:- https://github.com/IntelPython/daal4py </br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;2. Samples:- https://intelpython.github.io/daal4py/examples.html </br>

#### DAAL Demo:-

```
export http_proxy=http://proxy01.iind.intel.com:911
export https_proxy=https://proxy01.iind.intel.com:911
source ~/.bashrc
conda activate DAAL4PY
cd aiworkshop/daal4py/examples
jupyter notebook daal4py_data_science.ipynb
```

Open http://10.224.54.45:8888 in browser and run the notebook.</br>
___
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
$jupyter kernelspec list

Available kernels:
  base             /home/u****/.local/share/jupyter/kernels/base
  python3          /home/u****/.local/share/jupyter/kernels/python3
  tf_training      /home/u****/.local/share/jupyter/kernels/tf_training
```
```
$vi /home/u****/.local/share/jupyter/kernels/tf_training/kernel.json
```
Replace the executable path to pick the respective conda python </br>

```
{
 "argv": [
  "/home/u****/.conda/envs/tf_training/bin/python",
  "-m",
  "ipykernel_launcher",
  "-f",
  "{connection_file}"
 ],
 "display_name": "heterodimers",
 "language": "python"
}
```
