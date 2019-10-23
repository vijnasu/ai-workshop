# ai-workshop
For AI training

1. Link to download the course - https://software.seek.intel.com/DataCenter_to_Edge_REG - Subscribe through your mail id. You will receive a mail having link to the course content (~250 MB). Don't download it now, I have uploaded the same in dropbox. 

2. Get Intel AI Devcloud access through https://software.intel.com/en-us/devcloud/datacenter/sign-up (Approved in 24 hours & retained for 4 weeks)
User Name: u*****
Node Name: c***
Instructions: https://devcloud.intel.com/datacenter/?uuid=************************

2. Open the AI Devcloud in a browser: https://devcloud.intel.com/datacenter/?uuid=************************
 
3. Connect with a Jupyter* Notebook - One Click Log In, which opens up a Jupyter GUI

4. Click the 'New > Terminal' in the Top right corner. It will open up a new tab connecting to the terminal of AI Devcloud login node.

5. Download, extract & rename the course folder. Navigate to the root directory of the class.

wget https://www.dropbox.com/s/617aq0ft4khxucb/dc_to_the_edge.zip
unzip dc_to_the_edge.zip
mv 'DC to Edge Course' dc_to_edge_course
cd dc_to_the_edge_course/Notebooks

4. Create the conda environment (tf_training)

conda env create -f environment.yml

5. Now, to add this environment to the list of available environments you’ll see in your Jupyter notebook by running:

python -m ipykernel install --user --name tf_training --display-name "Python (tf_training)"

6. Run to activate the environment.

conda activate tf_training

7. Navigate to the tab in your browser which has Jupyter GUI and refresh the folder using the refresh button in the top right corner.

8. Click dc_to_edge_course and find download the "AI From the Data Center to the Edge An Optimized Path Using Intel Architecture.pdf" and refer this document through out the workshop.

9. Navigate to Notebooks folder in Jupyter UI and start the course in order:-

1) Part1-Exploratory_Data_Analysis.ipynb
2) Part2-Training_InceptionV3-Student.ipynb
3) Part3-Model_Analysis.ipynb (Quiz - Fetches a certificate from Intel on success. Attempt once. If failed, attempt later.
4) Optional-OpenVINO_Video_Inference.ipynb

10. OpenVINO demos:-

Select the base conda kernal in the Jupyter notebook

vi ~/.bash_profile
****
source /glob/deep-learning/openvino/bin/setupvars.sh
****

Build the samples:-
cd /glob/deep-learning/openvino/deployment_tools/inference_engine/samples

./build_samples.sh

Use the following library in the source code - 

$HOME/inference_engine_samples_build/intel64/Release/lib/libcpu_extension.so

Troubleshooting:-

1. If there is a protobuf, opencv, vmmr_utils error, it may be due to jupyter kernel not pointing to proper environment. To correct this in the terminal do the following:-
python
>>>import sys
>>>sys.executable
'/home/u****/.conda/envs/tf_training/bin/python'
>>>exit()

$jupyter kernelspec list

Available kernels:
  base             /home/u****/.local/share/jupyter/kernels/base
  python3          /home/u****/.local/share/jupyter/kernels/python3
  tf_training      /home/u****/.local/share/jupyter/kernels/tf_training
  
$vi /home/u****/.local/share/jupyter/kernels/tf_training/kernel.json

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
