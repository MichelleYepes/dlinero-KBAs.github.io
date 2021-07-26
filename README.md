# dlinero-KBAs.github.io
Locating KBAs: An automated workflow for identifying potential Key Biodiversity Areas

## Locating KBAs: An automated workflow for identifying potential Key Biodiversity Areas
##### Daniela Linero - [National Audubon Society](https://www.audubon.org/)  
 \
This GitHub repository is associated with the following website: [dlinero-KBAs.github.io](dlinero-KBAs.github.io)

### Introduction 
***
In the face of an alarming and accelerating loss of biodiversity, it is essential to safeguard the places that contribute significantly to the persistence of species around the world. The IUCN Species Survival and World Protected Areas Commissions recently led an effort to develop a [standard](https://portals.iucn.org/library/sites/library/files/documents/2016-048.pdf) for identifying the places with the highest conservation value, the Key Biodiversity Areas (KBAs; IUCN, 2016). In the process of identifying KBAs, it is recommended to first conduct a comprehensive scoping analysis. However, this analysis requires a great effort to obtain, compile and analyze spatial data for as many taxonomic groups as possible. The *Locating KBAs workflow* helps to streamline the scoping analysis by using the R programming language and leveraging GBIF data. The workflow code accesses the occurrence data of species present in a user-defined area and determines all those that could trigger the criteria of the KBA standard. Subsequently, it helps users identifying the places where the potential trigger species occur in significant numbers. In this way, the workflow enables users to efficiently and transparently identify the sites where it is most appropriate to focus efforts on gathering information on mature individuals, engaging stakeholders, and applying the standard’s criteria. 


### Methodology 
***

#### 1. Installation and initial requirements

To get started, you need to confirm that you have the following requirements:

* Have R and RStudio installed on your computer. If you do not have them, please download and install [R](https://cran.r-project.org/) first and continue downloading and installing [RStudio](https://www.rstudio.com/products/rstudio/).

* Have a GitHub account and GitHub Desktop installed on your computer. You can create a free GitHub account [here](https://github.com/) and download GitHub Desktop [here](https://desktop.github.com/). 

* Have a GBIF account. If you do not have one yet, create it using this [link](https://www.gbif.org/user/profile).

* Request an API Key [here](https://apiv3.iucnredlist.org/) to access the IUCN Red List information. 


Once you have met all the above requirements, open RStudio and make sure you have the following packages installed; otherwise use the following code to install them:


```{r, eval=FALSE}

install.packages(c("tidyverse", "Hmisc", "rgbif", "wellknown", "rredlist", "ggplot2", "ggspatial", "RCurl", “xml2”, “rvest”, “sf”, “DT”, “leaflet”, “knitr”))
```


#### 2. Workflow 

The workflow code  is designed to facilitate and streamline the scoping analysis for KBAs identification by leveraging the free and open access data of GBIF. Before exploring and running the workflow code, I encourage users to familiarize themselves with the [Global Standard for the Identification of Key Biodiversity Areas](https://portals.iucn.org/library/sites/library/files/documents/2016-048.pdf) (IUCN, 2016) and the [Guidelines for using this standard](https://portals.iucn.org/library/sites/library/files/documents/2020-033-En.pdf) (KBA Standards and Appeals Committee, 2020).

In this workflow we will focus solely on the following species-based criteria:

* A1 for globally threatened species
* B for restricted-range species
* D1 for congregations of species during a particular stage of their life cycle


The workflow is divided into **three main steps**. First, the user downloads and cleans GBIF occurrence data. The code then retrieves information for each species present in the dataset, accessing the IUCN Red List and Bird Data Zone portals and the tools provided in the following KBA [webpage](http://www.keybiodiversityareas.org/working-with-kbas/proposing-updating/criteria-tools). With this information, the code **selects the species present in the study area that have the potential to trigger the aforementioned KBA criteria.** The second step is to apply two functions that allow the user to map the location of the potential trigger species and **identify the sites where they occur in significant numbers.** In the case of bird species, it is also possible to locate the places where they meet the thresholds of the KBA criteria considered. The last step of the workflow is to **obtain the citations** of the different sources of information consulted in the previous steps. 

The scheme below represents the overall workflow 

![](methods/Workflow.jpeg)

#### 3. Detailed step-by-step instructions 

Please visit this [website](dlinero-KBAs.github.io) and select the Notebook tab. There you will find the explanation of all the steps to complete the workflow and their associated code.  Additionally, you will be able to interact with the most important results of the workflow, such as the table of potential trigger species and the maps of the sites where they occur in significant numbers. 


### Example outputs
***

The following is a preview of the table to identify potential trigger species for the above criteria (globally threatened species, restricted range species, species that form seasonal congregations). For bird species, it is also possible to obtain the global number of mature individuals and calculate the criteria thresholds,


<center>
![](https://media.giphy.com/media/MRHsAJgDVj926npzAR/giphy.gif){width=600px}
</center>



The code also contains a function that will help the user to identify the sites where the potential trigger species have large counts or where there are multiple records of potential trigger species.

<center>
![](https://media.giphy.com/media/oWrsaglCvK79HCkV82/giphy.gif){width=500px}
<center>


A second function, available only for bird species, creates an interactive map showing the location of records that meet the threshold of individuals for each criterion evaluated.


<center>
![](https://media.giphy.com/media/n7im3EPT7aMvoEBgr7/giphy.gif){width=500px}
<center>


### GitHub repository structure
***

```
│   README.md                             : Description of the repository
│   LICENSE                               : Repository license  
│   dlinero-KBAs.github.io.Rproj          : RStudio project file 
│   site.yml                              : Website configuration file
│   index.Rmd                             : Markdown file with workflow overview
│   index.html                            : html file derived from markdown
│   Notebook.Rmd                          : Markdown file with workflow code
│   Notebook.html                         : html file derived from markdown
│
└───data
│   └───   Quindio.shp                    : Shapefile of the study area
│   
└───methods
│   └───   Workflow.jpeg                  : Workflow schema
│   
└───outputs
    └───   Map_1.png                      : Example of the output of map function 1
    └───   Map_2.png                      : Example of the output of map function 2

```

### How to run the workflow code in your local computer
***


1. Sign in into your GitHub account here. 

2. What were going to do is copy an existing repository into your profile. In the search tab type "dlinero/". CLick on it. You will be taken to this repository. 

3. If you want to copy all the files to your own profile, including the ones used to create the website, then select Fork on the upper right corner. 

4. Then you will be able to see the repository in your profile. 

5. If you want to open or modify the files and run the code in your local computer, open the GitHub Desktop software. 

6. To connect it with your GitHub account go to preferences, under accounts select sign in and fill the information. 

7. Then under the Git option put your user name and your user email. 

8. Select Save. 

9. Now when you click on the dropdown of Current repository,
Select Add, choose clone repository and then click on the Locating KBAs workflow. Select the local path where you will like to store all the files. Click clone. 


10. Click show in finder to open the file explorer in the path you specified. Open the dlinero-KBAs.github.io.Rproj file to open the R project in RStudio. On the bottom right corner, where all the files are listed, select the Notebook.Rmd to open the Rmarkdown file. 

11. Now, you are ready to modify the code and run it!

12. If you have modified the file and want to record the changes in your github repository. Go to the GitHub Desktop software, write the description of the change, and press the commit to master button 

13. Finally, press push origin.  


### Additional resources
***

Explanation video: 

### License
***

Content in the repository is licensed under the [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/)

### Citation
***

Linero D (2018) Locating KBAs: An automated workflow for identifying potential Key Biodiversity Areas. [https://github.com/dLinero-KBAs/dlinero-KBAs.github.io](https://github.com/dLinero-KBAs/dlinero-KBAs.github.io)

### Contact
***

Feel free to email me at daniela.linero@audubon.org

[ResearchGate profile](https://www.researchgate.net/profile/Daniela-Linero)

[LinkedIn profile](www.linkedin.com/in/daniela-linero)

### References
***

* Gueta, T., Carmel, Y. (2016). Quantifying the value of user-level data cleaning for big data: A case study using mammal distribution models. Ecological Informatics, 34, 139-145. https://doi.org/10.1016/j.ecoinf.2016.06.001

* IUCN (2016). A Global Standard for the Identification of Key Biodiversity Areas, Version 1.0. First edition. Gland, Switzerland: IUCN.

* KBA Standards and Appeals Committee (2020). Guidelines for using A Global Standard for the Identification of Key Biodiversity Areas. Version 1.1. Prepared by the KBA Standards and Appeals Committee of the IUCN Species Survival Commission and IUCN World Commission on Protected Areas. Gland, Switzerland: IUCN. viii + 206 pp.