# ChipWhisperer Setup Guide

## Windows Setup

### Prerequisites
1. Open Command Prompt
2. Install WSL (Windows Subsystem for Linux):
   ```
   wsl --install
   ```
   *Skip this step if WSL is already installed*
3. Install USBIPD:
   ```
   winget install usbipd
   ```
4. Download and install Docker Desktop from the official website - https://docs.docker.com/desktop/setup/install/windows-install/
5. Reboot your computer after installation

### Running ChipWhisperer Docker Image
1. Open Docker Desktop
2. Run the ChipWhisperer docker image by navigating to the Docker terminal in the bottom right of the app
3. Enter the following command:
   ```
   docker run -it --device=/dev/bus/usb:/dev/bus/usb --privileged -p 8888:8888 saravan29/hhh-notebooks4:latest
   ```
4. Wait till the docker image gets downloaded and your output looks like this
    <img width="1506" alt="Image" src="https://github.com/user-attachments/assets/a94b8391-f17c-4077-aa38-f8b3fb66e7b7" />
5. After the docker image downloads and runs, open your browser
6. Navigate to `localhost:8888`
7. Enter the password: `bob`
8. To close/open it again you toggle the play button in contianer section of the app as shown below
   <img width="1506" alt="Image" src="https://github.com/user-attachments/assets/4493033a-9b57-405d-bc5a-5a1e00bd572c" />

### Connecting Hardware (Windows)
To connect your ChipWhisperer hardware to the Docker container via WSL:

1. List available USB devices:
   ```
   usbipd list
   ```
2. Bind ChipWhisperer to USBIPD:
   ```
   usbipd bind --busid <BUS_ID of chipwhispers>
   ```
3. Attach ChipWhisperer to WSL:
   ```
   usbipd attach --wsl --busid <BUS_ID of chipwhispers>
   ```
4. Once these steps are completed, you can proceed with hardware operations

### Note 
1) To install any extra libraries then use pip command to install them in the code block itself and kindly note them somewhere so that we can preinstall them in the final dockerfile for the event ( navigate to libraries.ipynb for more details )
2) wherever you are ploting any graphs use %%matplotlib widget rather than %%matplotlib notebook (did this change in most of the places , still if you encounter any ploting issue then follow this)
3) Two folders which are useful for us 
   * notebooks_main inside the notebooks folder
   * sca101,sca201,sca202 inside courses inside jupyter folder 


## Linux Setup

1. Install Docker from the official website - https://docs.docker.com/desktop/setup/install/linux/ubuntu/
   * Follow the installation steps provided in the documentation
2. Run the ChipWhisperer Docker image with the following command:
   ```
   docker run -it --device=/dev/bus/usb:/dev/bus/usb --privileged -p 8888:8888 saravan29/hhh-notebooks4:latest
   ```
3. Setup is now complete for both simulation and hardware use


### Note 
1) To install any extra libraries then use pip command to install them in the code block itself and kindly note them somewhere so that we can preinstall them in the final dockerfile for the event ( navigate to libraries.ipynb for more details )
2) wherever you are ploting any graphs use %%matplotlib widget rather than %%matplotlib notebook (did this change in most of the places , still if you encounter any ploting issue then follow this)
3) Two folders which are useful for us 
   * notebooks_main inside the notebooks folder
   * sca101,sca201,sca202 inside courses inside jupyter folder 
