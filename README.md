Jones Radiology Assessment:
==========================

*Description:* To extract the data from given website and create a meaningful CSV file with details.


*Demo Video link :* https://www.dropbox.com/s/tbguviiqx9sa02e/Ref_Video_UiPath_Automation_For_Jones_Radiology.mp4?dl=0


*How to run this project* ( You can see the ref video uploaded for complete process of installing and executing the process in uipath)

- Download the Uipath Community edition from here https://download.uipath.com/UiPathStudioCommunity.msi
- Install Uipath and enable the extension as shown in the video.
- Enable "Ask where to save each file before downloading" in chrome settings.
- Download the project zip file from Github.
- Extract complete folder.
- Open Main.Xaml from the folder in UiPath studio application community edition.
- Run/Debug the project in UiPath Studio.
- Note: Uipath extension should be pre-enabled in the chrome and Excel plugin for uipath should be installed as well.


Project developed using RE Framework.
====================================
* Uses *State Machine* layout for the phases of automation project.
* Offers high level logging, exception handling and recovery.
* Keeps external settings in *Config.xlsx* file stored in Data folder of the project.


### How It Works ###
====================

 1. **INITIALIZE PROCESS**
 + ./Framework/*InitiAllSettings* - Load configuration data from Config.xlsx file and from assets
 + ./Framework/*KillAllProcesses* - Kill any open instance of Chrome and Excel

 2. **MAIN PROCESSING**
 + *Process* - Process invoke other workflow of "WebPageExtraction" related to the process being automated.
 + *WebPageDataExtraction* - This will give user to select End date year and month and based on those values it will try to extract the required data from the website and if it ia available it will save it to a file, else it will push Business rule exception of data not available. 
 + *ReadExtractedFile* - Reads the Extracted file of data and store it in Data table, manipulate the data to create meaningful CSV report.
 + *TakeScreenShot* - will take the screen shot when ever this workflow is invoked anywhere in the automation project and will store in Screenshot folder in project, this usually executes on system exception.

 3. **END PROCESS**
 + ./Framework/*CloseAllApplications* - closes applications used throughout the process and logs if there was any exception of BUsiness exception type or system exception type.

Final report is saved at Project\Data\Output folder with Name as "Final_Report_dd_MM_yy_hh_mm.CSV" where dd, MM, yy, hh and mm represents the current date , month, year, hour and minutes at which this process executed. 


