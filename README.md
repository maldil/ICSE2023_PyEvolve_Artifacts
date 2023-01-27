# PYEVOLVE: Automating Frequent Code Changes in Python ML Systems
We made all the tools and data used in the research publicly available in order to claim "Available" and "Reusable" batches. This artifact consists of the open-source versions of the tool ([PyEvolve](https://github.com/maldil/PyEvolve)) and two kinds of data sets that are used to evaluate the tool. We have readily installed tool on a VirtualBox VM image and included the evaluation subjects for the reviewer’s convenience. The git repositories of the tools contain detailed instructions for building and using the tools, allowing the public to reuse them.

> Note 1: The VirtualBox VM image is a 19GB file. The time it takes to download this file is determined by the internet connection speed. Therefore, we would like to kindly request that reviewers begin downloading this file prior to beginning the review process. Furthermore, reviewers must have at least 30 GB of free space on their computer in order to load the file into VirtualBox. 

> Note 2:  We have generated a VirtualBox image on a Mac computer with an Intel chip. The evaluation process heavily relies on the ability to load and run the virtual machine, which may pose challenges as VirtualBox is known to have specific compatibility issues with certain operating systems. To mitigate this, we recommend the reviewer have **Mac computer with an Intel chip** to run the attached image. 


> Note 4: We tested the compatibility of the VM image and evaluation instructions on a different machine (Mac-Intel chip), not the one used for creating the image, in order to ensure that all steps will run without interruption. 

# About the artifact
In Section 1, we first presented the steps to execute the tool in VirtualBox VM image which can be done in under 30 minutes. In section 2, we described our public datasets. The public may access all of these resources (tool and data) through our primary [website](https://pythoninfer.github.io) or archived repositories at [Zenodo](https://zenodo.org/record/7566407#.Y9At3C1h2cY).


We release one tool
* [PyEvolve](https://github.com/maldil/PyEvolve) - a tool that automatically transplants code change patterns to Python software systems 

We made two types of large datasets available.

* More than 40,000 code transformation trials were used to evaluate PyEvolve. This was achieved using a dataset of change patterns collected from real repositories. The dataset is publically available. 
* PyEvolve atomatically transplanted code change patterns by submitting 40 pull requests to open source repositories. We made the list of the pull requests public.

# 1. Tool - [PyEvolve](https://github.com/maldil/PyEvolve)
### a. Initial setup
**Step 1.1:** If you do not already have VirtualBox installed, please use this link (https://www.virtualbox.org) and follow the instructions in the link to install VirtualBox on your computer.

**Step 1.2:** We offer a VM image with all the tools and data pre-installed. The image (named `pyevolve.ova`) can be downloaded from the links provided below. The image file is 19GB in size and may take some time to download depending on your internet connection speed. We have provided a few links below in case the first one does not work. You can get the image by clicking on one of the links provided below.
* [Link 1](https://drive.google.com/drive/folders/1X3zqSKwOnVuLm-qeAELszcEw6gYb9flX?usp=sharing)
* [Link 2](https://o365coloradoedu-my.sharepoint.com/:f:/g/personal/mama1839_colorado_edu/EkWHc6MENFBDgYuD837me4UBM3xw9xyGTsXgUQB2zpYzbg?e=9aqbih)
* [Link 3](https://drive.google.com/drive/folders/1HX-cD_hm_CAo2zQvSCXjBPbIleIcQhYo?usp=sharing)

**Step 1.3:** Open VirtualBox. Click on the tools tab and then import the downloaded image file (`pyevolve.ova`) to VirtualBox, as shown below. For the image to be loaded into VirtualBox, you might need at least 30GB of free space. If not, you are likely to experience an error with the error code `NS ERROR_INVALID_ARG`.

<img width="400" alt="Import1" src="https://user-images.githubusercontent.com/20140049/214741823-c463c2e9-e95f-4416-b43f-65ff7734ed73.png">



You will be taken to the window shown below, where the settings should appear as depicted. Click the 'Import' button, as indicated in the image. This may take a few minutes to import the image into VirtualBox.

<img src="https://github.com/maldil/ICSE2023_PyEvolve_Artifacts/blob/main/import2.png" width="400">

**Step 1.4:** To set up the configurations successfully, you need to disable the USB port of the virtual machine. To do this, follow the steps outlined in the following image. If this is not done properly, you will receive an error  in the step **Step 1.5** with the error code `NS_ERROR_FAILURE`.

https://user-images.githubusercontent.com/20140049/213983265-3ddb4eed-ebdc-4192-8da7-ae8c49176234.mov


**Step 1.5:** Start the virtual machine by pressing the "Start" button at the top of the window.

**Step 1.6:** The virtual machine should ideally start now. However, sometimes it may enter into a shell prompt as shown below. 

<img width="400" alt="Screen Shot 2023-01-22 at 11 36 41 PM" src="https://user-images.githubusercontent.com/20140049/213987438-92b6e9db-c72d-4b3e-8c2a-72b0c5205921.png">

If this is the case, you will need to manually run the following two commands one after the other.
* `FS1:`
* `System\Library\CoreServices\boot.efi`

The following video illustrates the steps described above.


https://user-images.githubusercontent.com/20140049/214788226-e08bc953-8d6f-4c41-976a-648cf12e8969.mov


**Step 1.7:** The above step may take several minutes to start the machine, and you should see the startup screen as shown below. Use the password `abc@123` to log in to the machine. Once logged in, you will find a folder named `PYEVOLVE_FILES` which contains the executables, source code, and data for PyEvolve.

<img width="400" alt="startup" src="https://user-images.githubusercontent.com/20140049/213992302-eec06474-acf9-4f26-8655-d0012c5de9c2.png">

You have successfully configured all the necessary setup for executing PyEvolve.

### b. Executing PyEvolve
Under the evaluation, we demostrate transplantation of following patterns to the project `Keras`. 

```
                                     \
:[[l1]] = open(:[[l2]], "r")      ----\    with open(:[[l2]], "r") as :[[l1]]:
:[l4] = :[[l1]].readlines()       ----/        :[[l4]] = :[[l1]].readlines()
:[[l1]].close()                      /
```


These changes were submited to the project `keras` and was accepted throught this pull request (https://github.com/keras-team/keras/pull/16874). 

**Step 2.1:** Open the teminal application in the virtual machine and Navigate to the folder `PYEVOLVE_FILES` using the command `cd  ~/Desktop/PYEVOLVE_FILES`.  

**Step 2.2:** Execute `ls` to view the PyEvolve executable `pyevolve-1.0-SNAPSHOT.jar` and other data.

*For your convenience, we have included all the commands needed in the following steps in the file `~/Desktop/commands.txt`, so that you do not have to type the long commands.*

**Step 2.3:** You can use the command `java --enable-preview -jar pyevolve-1.0-SNAPSHOT.jar` to view all the required input arguments to successfully run the tool.
Below are the arguments for your knowledge (you do not have any action to perform). 

* `-p,--patterns`    This folder contains code change patterns with two types of filenames: those that begin with 'l_', and those that begin with 'r_'. These prefixes indicate the rule of a code change before and after. It is essential that the names following the prefixes are the same for the tool to correctly identify the files that belong to the same change. For example, you can check the folder `~/Desktop/PYEVOLVE_FILES/PATTERNS/` which contains patterns that we are planning to use in this evaluation.  
* `-r,--repositories`  The path to the project repository where the code change must be transplanted. This folder houses all of the projects.
*  `-f,--files`        This file contains the project files that must be reviewed and modified. The paths has to be a relative path to the folder indicated by the argument `-r`.
* `-t,--types`       This folder holds the "type" information of the program elements of the projects found in the project repository (-r). This information needs to be inferred and stored in this folder before running the "PyEvolve". Instructions for inferring type information can be found in this repository: https://github.com/mlcodepatterns/PythonTypeInformation. For your convenience, the type information has already been included in the VirtualBox Image.



**Step 2.4:** To clone the project `keras` to the folder `~/Desktop/PYEVOLVE_FILES/PROJECTS/keras-team/` please execute following commands.
* Navigate to the `cd ~/Desktop/PYEVOLVE_FILES/PROJECTS/keras-team/` 
* To clone `git clone https://github.com/keras-team/keras.git ./keras/`
* To retrieve the previous snapshot, before merging the pull request, execute `git checkout f49e66c72ea5fe337c5292ee42f61cd75bc74727`.

**Step 2.5:** To apply the patterns in the folder `./PATTERNS/` execute the following command. The argument descriptions are provided in the *Step 2.4*.

* You should first navigate to the folder `PYEVOLVE_FILES` using the command `cd ~/Desktop/PYEVOLVE_FILES/`
* To apply patterns execute `java --enable-preview -jar pyevolve-1.0-SNAPSHOT.jar -r ./PROJECTS/ -f ./refactoring_files.txt -p ./PATTERNS/ -t ./TYPE_REPO/`

The above command executes the main function of Pyevolve given in this [link](https://github.com/maldil/PyEvolve/blob/d24e28a2c95c9484f5ea5de215e359a04582d045/src/main/java/com/MainAdaptor.java#L30) and makes the code changes for the project included in the folder `~/Desktop/PYEVOLVE_FILES/PROJECTS/`.


**Step 2.6:** To check the changed files, navigate to the folder `~/Desktop/PYEVOLVE_FILES/PROJECTS/keras-team/keras` execute `git diff`, scroll down to see all the changes. You can observe a successful transplantation of the patten given in [Section 2](https://github.com/maldil/ICSE2023_PyEvolve_Artifacts/blob/master/README.md#b-executing-pyevolve).

**You have successfully executed PyEvolve and transplanted patterns to the Keras project.** 

# 2. Dataset
We have made available two distinct types of large datasets. To evaluate PyEvolve, we utilized over 40,000 code transformation trials by utilizing a dataset of change patterns collected from actual repositories. This dataset is readily accessible to the public. Additionally, PyEvolve automatically transplanted code change patterns by submitting 40 pull requests to open-source repositories. We have also made the list of these pull requests publicly available.

## Cross validation dataset 
PyEvolve was evaluated using the corss validation dataset. This data set contains frequent code changes made in open source Python projects. We evaluated PyEvolve with over 40,000 transformation trials. To provide easy access to data, we released [data]( https://github.com/pythonInfer/pythoninfer.github.io/blob/main/CrossValidationICSE2023.xlsx) on a website hosted on GitHub, as described above. We have, however, archived all tools and data in accordance with ICSE 2023 Open Science Policies.
* Zendo link for cross validation dataset : https://zenodo.org/record/7566407#.Y9At3C1h2cY



## Pull requests patches generated by PyEvolve
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


