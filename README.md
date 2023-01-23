# PYEVOLVE: Automating Frequent Code Changes in Python ML Systems
We made all the tools and data used in the research publicly available in order to claim "Available" and "Reusable" batches. This artifact consists of the open-source versions of the tool ([PyEvolve](https://github.com/maldil/PyEvolve)) and two kinds of data sets that are used to evaluate the tool. We have readily installed tool on a VirtualBox VM image and included the evaluation subjects for the reviewer’s convenience. The git repositories of the tools contain detailed instructions for building and using the tools, allowing the public to reuse them.

> Note: The VirtualBox VM image is a 30GB file. The time it takes to download this file is determined by the internet connection speed. Therefore, we would like to kindly request that reviewers begin downloading this file prior to beginning the review process. Furthermore, reviwers must have at least 30GB of free space on their computer in order to load the file into VirtualBox.


# About the artifact
In Section 1, we first presented the steps to execute the tool in VirtualBox VM image which can be done in under 30 minutes. In section 2, we described our public datasets. A comprehensive explanation of building the tools and then using it on a large dataset is provided in Section 3. You could use Mac OS CLI, Windows Powershell, or Linux terminal to execute the commands. The public may access all of these resources through our primary [website](https://pythoninfer.github.io) or archived repositories at [Zenodo](https://zenodo.org/).


We release one tool
* [PyEvolve](https://github.com/maldil/PyEvolve) - a tool that automatically transplants code change patterns to Python software systems 

We made two types of large datasets available.

* More than 40,000 code transformation trials were used to evaluate PyEvolve. This was achieved using a dataset of change patterns collected from real repositories. The dataset is publically available. 
* PyEvolve atomatically transplanted code change patterns by submitting 40 pull requests to open source repositories. We made the list of the pull requests public.

# Tool - [PyEvolve](https://github.com/maldil/PyEvolve)
### a. Initial setup
**Step 1.1:** If you do not already have VirtualBox installed, please use this link (https://www.virtualbox.org) and follow the instructions in the link to install VirtualBox on your computer.

**Step 1.2:** We provide a VM image with all the tools installed and the data. You can download the the image from this link. The image file is 20GB in size and may take some time to download depending on your internet connection speed. We have provided a few links below with various image formats in case the first one does not work.
* Link 1
* Link 2
* Link 3

**Step 1.3:** Click on the tools tab and then import the downloaded image file (`pyevolve.ova`) to VirtualBox, as shown below. 
<img src="https://github.com/maldil/ICSE2023_PyEvolve_Artifacts/blob/main/Import1.png" width="400">

You will be taken to the window shown below, where the settings should appear as depicted. Click the 'Import' button, as indicated in the image. This may take a few minutes to import the image into VirtualBox.

<img src="https://github.com/maldil/ICSE2023_PyEvolve_Artifacts/blob/main/import2.png" width="400">

**Step 1.4:** To set up the configurations successfully, you need to disable the USB port of the virtual machine. To do this, follow the steps outlined in the following image. If this is not done properly, you will receive an error with the error code `NS_ERROR_FAILURE`.

https://user-images.githubusercontent.com/20140049/213983265-3ddb4eed-ebdc-4192-8da7-ae8c49176234.mov



**Step 1.5:** Start the virtual machine by pressing the "Start" button at the top of the window.

**Step 1.6:** The virtual machine should ideally start now. However, sometimes it may enter into a shell prompt. 
FS
<img width="400" alt="Screen Shot 2023-01-22 at 11 36 41 PM" src="https://user-images.githubusercontent.com/20140049/213987438-92b6e9db-c72d-4b3e-8c2a-72b0c5205921.png">

If this is the case, you will need to manually run the following two commands one after the other.
* `FSE:`
* `System\Library\CoreServices\boot.efi`

The following video illustrates the steps described above.


https://user-images.githubusercontent.com/20140049/213990697-a4a2a02d-cc23-4ba4-ba4f-87ca76a01842.mov



**Step 1.7:** The above step may take several minutes to start the machine, and you should see the startup screen as shown below. Use the password `abc@123` to log in to the machine. Once logged in, you will find a folder named `PYEVOLVE_FILES` which contains the executables, source code, and data for PyEvolve.

<img width="400" alt="startup" src="https://user-images.githubusercontent.com/20140049/213992302-eec06474-acf9-4f26-8655-d0012c5de9c2.png">

You have successfully configured all the necessary setup for executing PyEvolve.

### b. Executing PyEvolve
Under the evaluation, we demostrate transplantation of two diffrent patterns to the project `keras`. These changes were submited to the project `keras` and was accepted throught this pull request (https://github.com/keras-team/keras/pull/16874). 

**Step 1.1:** Open the teminal application in the virtual machine and Navigate to the folder ~/ using the command `cd  `.  

# Cross validation dataset 
PyEvolve was evaluated using the corss validation dataset. This data set contains frequent code changes made in open source Python projects. We evaluated PyEvolve with over 40,000 transformation trials. To provide easy access to data, we released [data]( https://github.com/pythonInfer/pythoninfer.github.io/blob/main/CrossValidationICSE2023.xlsx) on a website hosted on GitHub, as described above. We have, however, archived all tools and data in accordance with ICSE 2023 Open Science Policies.
* Zendo link for cross validation dataset : https://zenodo.org/record/5889285#.YessCy1h2cY



# Pull requests patches generated by PyEvolve
| # |     Created at     |                              Url                               |State |Merged|
|--:|--------------------|----------------------------------------------------------------|------|------|
|  1|2022-06-26T18:21:33Z|https://github.com/HazyResearch/pdftotree/pull/122              |closed|True  |
|  2|2022-06-26T19:55:38Z|https://github.com/brightmart/text_classification/pull/149      |closed|True  |
|  3|2022-06-28T08:12:21Z|https://github.com/tensorflow/lattice/pull/73                   |closed|True  |
|  4|2022-06-29T07:44:12Z|https://github.com/quadrismegistus/prosodic/pull/37             |closed|True  |
|  5|2022-07-01T01:31:54Z|https://github.com/idaholab/raven/pull/1877                     |closed|True  |
|  6|2022-07-01T08:00:50Z|https://github.com/erikbern/ann-benchmarks/pull/303             |closed|True  |
|  7|2022-07-01T08:13:58Z|https://github.com/david-abel/simple_rl/pull/61                 |closed|True  |
|  8|2022-07-04T09:41:28Z|https://github.com/microsoft/nni/pull/4982                      |closed|True  |
|  9|2022-07-04T20:33:39Z|https://github.com/ray-project/ray/pull/26284                   |closed|True  |
| 10|2022-07-05T00:03:01Z|https://github.com/jindongwang/transferlearning/pull/341        |closed|True  |
| 11|2022-07-06T06:48:04Z|https://github.com/dipy/dipy/pull/2618                          |closed|True  |
| 12|2022-07-06T08:45:22Z|https://github.com/pgmpy/pgmpy/pull/1551                        |closed|True  |
| 13|2022-07-14T08:44:44Z|https://github.com/reframe-hpc/reframe/pull/2565                |closed|True  |
| 14|2022-07-14T08:52:19Z|https://github.com/DeepLabCut/DeepLabCut/pull/1905              |closed|True  |
| 15|2022-08-06T06:16:59Z|https://github.com/pytorch/pytorch/pull/82929                   |closed|True  |
| 16|2022-08-06T06:46:26Z|https://github.com/ray-project/ray/pull/27600                   |closed|True  |
| 17|2022-08-06T08:04:47Z|https://github.com/keras-team/keras/pull/16874                  |closed|True  |
| 18|2022-08-06T08:22:04Z|https://github.com/GoogleCloudDataproc/cloud-dataproc/pull/152  |closed|True  |
| 19|2022-08-06T08:29:03Z|https://github.com/facebookresearch/ParlAI/pull/4718            |closed|True  |
| 20|2022-08-06T09:35:13Z|https://github.com/idaholab/raven/pull/1930                     |closed|True  |
| 21|2022-08-07T05:24:26Z|https://github.com/BindsNET/bindsnet/pull/570                   |closed|True  |
| 22|2022-08-07T05:49:51Z|https://github.com/CellProfiler/CellProfiler/pull/4610          |closed|True  |
| 23|2022-08-07T06:32:24Z|https://github.com/daniellerch/aletheia/pull/21                 |closed|True  |
| 24|2022-08-07T06:51:40Z|https://github.com/deepinsight/insightface/pull/2070            |closed|True  |
| 25|2022-08-06T07:12:28Z|https://github.com/scikit-image/scikit-image/pull/6458          |open  |True  |
| 26|2022-08-07T06:14:46Z|https://github.com/danforthcenter/plantcv/pull/932              |open  |True  |
| 27|2022-08-07T00:50:05Z|https://github.com/aws/sagemaker-python-sdk/pull/3286           |closed |True |
| 28|2022-08-07T05:56:14Z|https://github.com/cesium-ml/cesium/pull/309                    |closed |True |
| 29|2022-07-05T01:40:15Z|https://github.com/LCAV/pyroomacoustics/pull/271                |closed |True |
| 30|2022-06-27T02:46:23Z|https://github.com/Pinafore/qb/pull/107                         |open  |False |
| 31|2022-06-29T02:33:54Z|https://github.com/tensorflow/transform/pull/280                |open  |False |
| 32|2022-06-29T05:18:34Z|https://github.com/tensorflow/ranking/pull/325                  |open  |False |
| 33|2022-07-01T01:47:41Z|https://github.com/google-research/google-research/pull/1189    |open  |False |
| 34|2022-07-05T08:05:16Z|https://github.com/bnpy/bnpy/pull/42                            |open  |False |
| 35|2022-07-05T08:23:56Z|https://github.com/brainiak/brainiak/pull/516                   |open  |False |
| 36|2022-07-13T20:16:05Z|https://github.com/LxMLS/lxmls-toolkit/pull/176                 |open  |False |
| 37|2022-06-26T22:09:38Z|https://github.com/cornellius-gp/gpytorch/pull/2049             |closed|False |
| 38|2022-06-30T08:12:36Z|https://github.com/lmcinnes/pynndescent/pull/192                |closed|False |
| 39|2022-07-05T05:41:14Z|https://github.com/pyRiemann/pyRiemann/pull/185                 |closed|False |
| 40|2022-07-11T06:56:15Z|https://github.com/calico/basenji/pull/125                      |closed|False |
