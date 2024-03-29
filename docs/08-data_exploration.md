# (PART\*) Data Exploration {-}




# Exploring Soil Testing Data With R

In this activity, you'll have a chance to become familiar with the BioDIGS soil testing data. This dataset includes information on the inorganic components of each soil sample, particularly metal concentrations. Human activity can increase the concentration of inorganic compounds in the soil. When cars drive on roads, compounds from the exhaust, oil, and other fluids might settle onto the roads and be washed into the soil. When we put salt on roads, parking lots, and sidewalks, the salts themselves will eventually be washed away and enter the ecosystem through both water and soil. Chemicals from factories and other businesses also leech into our environment. All of this means the concentration of heavy metals and other chemicals will vary among the soil samples collected for the BioDIGS project. 

## Before You Start


If you do not already have a Google account that you would like to use for accessing Terra, [create one now](https://accounts.google.com/SignUp).

If you would like to create a Google account that is associated with your non-Gmail, institutional email address, follow [these instructions](https://support.terra.bio/hc/en-us/articles/360029186611).

## Objectives

This activity will teach you how to use the AnVIL platform to:

1. Get started working on AnVIL
1. Launch RStudio
1. Import data into RStudio
1. Examine csv file that contains the soil testing data from the BioDIGS project
1. Calculate summary statistics for variables in the soil testing data
1. Create and interpret histograms and boxplots for variables in the soil testing data.

## Getting Started

In the next few steps, you will walk through how to get set up to use RStudio on the AnVIL platform. AnVIL is centered around different “Workspaces”. Each Workspace functions almost like a mini code laboratory - it is a place where data can be examined, stored, and analyzed. The first thing we want to do is to copy or “clone” a Workspace to create a space for you to experiment.

Use a web browser to go to the AnVIL website. In the browser type:

```
anvil.terra.bio
```

:::{.notice}
**Tip**
At this point, it might make things easier to open up a new window in your browser and split your screen. That way, you can follow along with this guide on one side and execute the steps on the other.
:::

Your instructor will give you information on which workspace you should clone.

### Video overview of RStudio on AnVIL


Here is a video tutorial that describes the basics of using RStudio on AnVIL.

<iframe src="https://drive.google.com/file/d/1v72ZG8JIRDUaewFQgGfcCO_qoM4eYmYX/preview" width="640" height="360" allow="autoplay"></iframe>

### Objectives

- Start compute for your RStudio environment
- Tour RStudio on AnVIL
- Stop compute to minimize expenses

### Slides

The slides for this tutorial are are located [here](https://docs.google.com/presentation/d/1eypYLLqD11-NwHLs4adGpcuSB07dYEJfAaALSMvgzqw).

### Launching RStudio


:::{.warning}
AnVIL is very versatile and can scale up to use very powerful cloud computers. It's very important that you select a cloud computing environment appropriate to your needs to avoid runaway costs.  If you are uncertain, start with the default settings; it is fairly easy to increase your compute resources later, if needed, but harder to scale down.
:::

Note that, in order to use RStudio, you must have access to a Terra Workspace with permission to compute (i.e. you must be a "Writer" or "Owner" of the Workspace).

1. Open Terra - use a web browser to go to [`anvil.terra.bio`](https://anvil.terra.bio/)

1. In the drop-down menu on the left, navigate to "Workspaces". Click the triple bar in the top left corner to access the menu. Click "Workspaces".

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g117989bd49c_0_150.png" title="Screenshot of Terra drop-down menu.  The &quot;hamburger&quot; button to extend the drop-down menu is highlighted, and the menu item &quot;Workspaces&quot; is highlighted." alt="Screenshot of Terra drop-down menu.  The &quot;hamburger&quot; button to extend the drop-down menu is highlighted, and the menu item &quot;Workspaces&quot; is highlighted." width="100%" />

1. Click on the name of your Workspace. You should be routed to a link that looks like: `https://anvil.terra.bio/#workspaces/<billing-project>/<workspace-name>`.

1. Click on the cloud icon on the far right to access your Cloud Environment options.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_22.png" title="Screenshot of a Terra Workspace. The cloud icon to create a new cloud environment is highlighted." alt="Screenshot of a Terra Workspace. The cloud icon to create a new cloud environment is highlighted." width="100%" />

1. In the dialogue box, click the "Settings" button under RStudio.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_18.png" title="Screenshot of the Cloud Environment Details dialogue box. The Settings button under RStudio is highlighted." alt="Screenshot of the Cloud Environment Details dialogue box. The Settings button under RStudio is highlighted." width="100%" />

1. You will see some details about the default RStudio cloud environment, and a list of costs because it costs a small amount of money to use cloud computing.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_35.png" title="Screenshot of the RStudio Cloud Environment dialogue box. The cost to run the environment is highlighted." alt="Screenshot of the RStudio Cloud Environment dialogue box. The cost to run the environment is highlighted." width="100%" />



1. If you are uncertain about what you need, the default configuration is a reasonable, cost-conservative choice.  It is fairly easy to increase your compute resources later, if needed, but harder to scale down. Click the “Create” button.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_41.png" title="Screenshot of the RStudio Cloud Environment dialogue box. The &quot;CREATE&quot; button is highlighted." alt="Screenshot of the RStudio Cloud Environment dialogue box. The &quot;CREATE&quot; button is highlighted." width="100%" />



1. Otherwise, click “CUSTOMIZE” to modify the environment for your needs.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_48.png" title="Screenshot of the RStudio Cloud Environment dialogue box. The &quot;CUSTOMIZE&quot; button is highlighted." alt="Screenshot of the RStudio Cloud Environment dialogue box. The &quot;CUSTOMIZE&quot; button is highlighted." width="100%" />

    

    

    

    

    

1. The dialogue box will close and you will be returned to your Workspace.  You can see the status of your cloud environment by hovering over the RStudio logo.  It will take a few minutes for Terra to request computers and install software.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_91.png" title="Screenshot of a Terra Workspace. The hovertext for the RStudio icon is highlighted, and indicates that the status of the environment is &quot;Creating&quot;." alt="Screenshot of a Terra Workspace. The hovertext for the RStudio icon is highlighted, and indicates that the status of the environment is &quot;Creating&quot;." width="100%" />

1. When your environment is ready, its status will change to “Running”.  Click on the RStudio logo to open a new dialogue box that will let you launch RStudio.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_95.png" title="Screenshot of a Terra Workspace. The hovertext for the RStudio icon is highlighted, and indicates that the status of the environment is &quot;Running&quot;." alt="Screenshot of a Terra Workspace. The hovertext for the RStudio icon is highlighted, and indicates that the status of the environment is &quot;Running&quot;." width="100%" />
    
1. Click the launch icon to open RStudio.  This is also where you can pause, modify, or delete your environment when needed.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_99.png" title="Screenshot of the RStudio Environment Details dialogue box. The &quot;Open&quot; button is highlighted." alt="Screenshot of the RStudio Environment Details dialogue box. The &quot;Open&quot; button is highlighted." width="100%" />

1. You should now see the RStudio interface with information about the version printed to the console.

    <img src="resources/images/08-data_exploration_files/figure-html//1a35Mb8f0M-bQkBcHa1cyQc6YxXoBLtExCz96nv08vkA_g14ea2db115d_0_103.png" title="Screenshot of the RStudio environment interface." alt="Screenshot of the RStudio environment interface." width="100%" />

### Touring RStudio


Next, we will be using RStudio and the package `Glimma` to create interactive plots. See [this vignette](https://bioconductor.org/packages/release/bioc/vignettes/Glimma/inst/doc/limma_edger.html) for more information.

1. The Bioconductor team has created a very useful package to programmatically interact with Terra and Google Cloud. Install the `AnVIL` package. It will make some steps easier as we go along.

    

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g11f12bc99af_0_49.png" title="Screenshot of the RStudio environment interface. Code has been typed in the console and is highlighted." alt="Screenshot of the RStudio environment interface. Code has been typed in the console and is highlighted." width="480" />

1. You can now quickly install precompiled binaries using the AnVIL package’s `install()` function. We will use it to install the `Glimma` package and the `airway` package. The `airway` package contains a `SummarizedExperiment` data class. This data describes an RNA-Seq experiment on four human airway smooth muscle cell lines treated with dexamethasone. 

{Note: for some of the packages, you will have to install packaged from the CRAN repository, using the install.packages() function. The examples will show you which install method to use.}

    

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g11f12bc99af_0_56.png" title="Screenshot of the RStudio environment interface. Code has been typed in the console and is highlighted." alt="Screenshot of the RStudio environment interface. Code has been typed in the console and is highlighted." width="480" />

1. Load the example data.

    

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g11f12bc99af_0_56.png" title="Screenshot of the RStudio environment interface. Code has been typed in the console and is highlighted." alt="Screenshot of the RStudio environment interface. Code has been typed in the console and is highlighted." width="480" />

1. The multidimensional scaling (MDS) plot is frequently used to explore differences in samples. When this data is MDS transformed, the first two dimensions explain the greatest variance between samples, and the amount of variance decreases monotonically with increasing dimension. The following code will launch a new window where you can interact with the MDS plot.

    

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g11f12bc99af_0_70.png" title="Screenshot of the Glimma popout showing the data in an MDS plot. All data points are blue." alt="Screenshot of the Glimma popout showing the data in an MDS plot. All data points are blue." width="480" />

1. Change the `colour_by` setting to "groups" so you can easily distinguish between groups. In this data, the "group" is the treatment.

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g11f12bc99af_0_77.png" title="Screenshot of the Glimma popout showing the data in an MDS plot. Data points are colored blue and orange by group. The colour by dropdown menu on the interactive plot is hightlighted." alt="Screenshot of the Glimma popout showing the data in an MDS plot. Data points are colored blue and orange by group. The colour by dropdown menu on the interactive plot is hightlighted." width="480" />

1. You can download the interactive html file by clicking on "Save As".

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g1204ed6da7f_0_0.png" title="Screenshot of the Glimma popout showing the data in an MDS plot. The Save As menu is highlighted." alt="Screenshot of the Glimma popout showing the data in an MDS plot. The Save As menu is highlighted." width="480" />

1. You can also download plots and other files created directly in RStudio. To download the following plot, click on "Export" and save in your preferred format to the default directory. This saves the file in your cloud environment.

    

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g1204ed6da7f_0_12.png" title="Screenshot of the RStudio interface. A plot has been created. The Export menu has been highlighted." alt="Screenshot of the RStudio interface. A plot has been created. The Export menu has been highlighted." width="480" />

1. You should see the plot in the "Files" pane.

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g1204ed6da7f_0_19.png" title="Screenshot of the RStudio interface. A plot has been created. The saved pdf file is now visible under the &quot;Files&quot; pane." alt="Screenshot of the RStudio interface. A plot has been created. The saved pdf file is now visible under the &quot;Files&quot; pane." width="480" />

1. Select this file and click "More" > "Export"

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g1204ed6db6a_0_0.png" title="Screenshot of the RStudio interface. A plot has been created. The saved pdf file is now visible under the &quot;Files&quot; pane. The &quot;More&quot; and &quot;Export&quot; menus have been highlighted." alt="Screenshot of the RStudio interface. A plot has been created. The saved pdf file is now visible under the &quot;Files&quot; pane. The &quot;More&quot; and &quot;Export&quot; menus have been highlighted." width="480" />

1. Select "Download" to save the file to your local machine.

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g1204ed6db6a_0_8.png" title="Screenshot of the RStudio interface. The popup to download the selected file has been highlighted," alt="Screenshot of the RStudio interface. The popup to download the selected file has been highlighted," width="480" />

### Pausing RStudio


1. The right-hand side icon reminds you that you are accruing cloud computing costs. If you don’t see this icon, you may need to scroll to the right.

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g11f12bc99af_0_84.png" title="Screenshot of the RStudio interface. The icon on the right showing that the cloud environment is running is highlighted." alt="Screenshot of the RStudio interface. The icon on the right showing that the cloud environment is running is highlighted." width="100%" />

1. You should minimize charges when you are not performing an analysis. You can do this by clicking on the RStudio icon and selecting “Pause”. This will release the CPU and memory resources for other people to use. Note that your work will be saved in the environment and continue to accrue a very small cost.  This work will be lost if the cloud environment gets deleted.  If there is anything you would like to save permanently, it's a good idea to copy it from your compute environment to another location, such as the Workspace bucket, GitHub, or your local machine, depending on your needs.

    <img src="resources/images/08-data_exploration_files/figure-html//1BLTCaogA04bbeSD1tR1Wt-mVceQA6FHXa8FmFzIARrg_g11f12bc99af_0_91.png" title="Screenshot of the RStudio menu. The pause button which stops the cloud environment is highlighted." alt="Screenshot of the RStudio menu. The pause button which stops the cloud environment is highlighted." width="100%" />

:::{.notice}
You can also pause your cloud environment(s) at https://anvil.terra.bio/#clusters.
:::

## Part 1. Data Import

We will use the `BioDIGS` package to retrieve the data. We first need to install the package from where it is stored on GitHub.





```r
devtools::install_github("fhdsl/BioDIGSData")
```

Once you've installed the package, we can load the library and assign the soil testing data to an _object_. This command follows the code structure:

dataset_object_name <- stored_BioDIGS_dataset


```r
library(BioDIGSData)

soil.values <- BioDIGS_soil_data()
```

It _seems_ like the dataset loaded, but it's always a good idea to verify. There are many ways to check, but the easiest approach (if you're using RStudio) is to look at the Environment tab on the upper right-hand side of the screen. You should now have an object called `soil.values` that includes some number of observations for 28 variables. The _observations_ refer to the number of rows in the dataset, while the _variables_ tell you the number of columns. As long as neither the observations or variables are 0, you can be confident that your dataset loaded.

Let's take a quick look at the dataset. We can do this by clicking on soil.values object in the Environment tab. (Note: this is equivalent to typing `View(soil.values)` in the R console.)

<img src="resources/images/08-environment.png" title="If the dataset loaded, you will see an object with non-zero observations and variables in the Environment tab" alt="If the dataset loaded, you will see an object with non-zero observations and variables in the Environment tab" style="display: block; margin: auto;" />


This will open a new window for us to scroll through the dataset.

<img src="resources/images/08-scrolling_through_dataset.png" title="You can click on the object in the Environment tab to open a new window that allows you to scroll through the loaded dataset" alt="You can click on the object in the Environment tab to open a new window that allows you to scroll through the loaded dataset" style="display: block; margin: auto;" />

Well, the data definitely loaded, but those column names aren't immediately understandable. What could **As_EPA3051** possibly mean? In addition to the dataset, we need to load the _data dictionary_ as well.

:::{.dictionary}

**Data dictionary:** a file containing the names, definitions, and attributes about data in a database or dataset.

:::

In this case, the data dictionary can help us make sense of what sort of values each column represents. The data dictionary for the BioDIGS soil testing data is available in the R package (see code below), but we have also reproduced it here.


```r
?BioDIGS_soil_data()
```

:::{.dictionary}

- **site_id** Unique letter and number site name
- **full_name** Full site name
- **As_EPA3051** Arsenic (mg/kg), EPA Method 3051A. Quantities < 3.0 are not detectable.
- **Cd_EPA3051** Cadmium (mg/kg), EPA Method 3051A. Quantities < 0.2 are not detectable.
- **Cr_EPA3051** Chromium (mg/kg), EPA Method 3051A
- **Cu_EPA3051** Copper (mg/kg), EPA Method 3051A
- **Ni_EPA3051** Nickel (mg/kg), EPA Method 3051A
- **Pb_EPA3051** Lead (mg/kg), EPA Method 3051A
- **Zn_EPA3051** Zinc (mg/kg), EPA Method 3051A
- **water_pH**
- **A-E_Buffer_pH**
- **OM_by_LOI_pct** Organic Matter by Loss on Ignition
- **P_Mehlich3** Phosphorus (mg/kg), using the Mehlich 3 soil test extractant
- **K_Mehlich3 Potassium** (mg/kg), using the Mehlich 3 soil test extractant
- **Ca_Mehlich3** Calcium (mg/kg), using the Mehlich 3 soil test extractant
- **Mg_Mehlich3** Magnesium (mg/kg), using the Mehlich 3 soil test extractant
- **Mn_Mehlich3** Manganese (mg/kg), using the Mehlich 3 soil test extractant
- **Zn_Mehlich3** Zinc (mg/kg), using the Mehlich 3 soil test extractant
- **Cu_Mehlich3** Copper (mg/kg), using the Mehlich 3 soil test extractant
- **Fe_Mehlich3** Iron (mg/kg), using the Mehlich 3 soil test extractant
- **B_Mehlich3** Boron (mg/kg), using the Mehlich 3 soil test extractant
- **S_Mehlich3** Sulfur (mg/kg), using the Mehlich 3 soil test extractant
- **Na_Mehlich3** Sodium (mg/kg), using the Mehlich 3 soil test extractant
- **Al_Mehlich3** Aluminum (mg/kg), using the Mehlich 3 soil test extractant
- **Est_CEC** Cation Exchange Capacity (meq/100g) at pH 7.0 (CEC)
- **Base_Sat_pct** Base saturation (BS). This represents the percentage of CEC occupied by bases (Ca2+, Mg2+, K+, and Na+). The %BS increases with increasing soil pH. The availability of Ca2+, Mg2+, and K+ increases with increasing %BS.
- **P_Sat_ratio** Phosphorus saturation ratio. This is the ratio between the amount of phosphorus present in the soil and the total capacity of that soil to retain phosphorus. The ability of phosphorus to be bound in the soil is primary a function of iron (Fe) and aluminum (Al) content in that soil.

:::

Using the data dictionary, we find that the values in column `As_EPA3051` give us the arsenic concentration in mg/kg of each soil sample, as determined by EPA Method 3051A. While arsenic can occur naturally in soils, higher levels suggest the soil may have been contaminated by mining, hazardous waste, or pesticide application. Arsenic is toxic to humans.

We can also look at just the names of all the columns using the R console using the `colnames()` command.


```r
colnames(soil.values)
```

```
##  [1] "site_id"       "site_name"     "type"          "As_EPA3051"   
##  [5] "Cd_EPA3051"    "Cr_EPA3051"    "Cu_EPA3051"    "Ni_EPA3051"   
##  [9] "Pb_EPA3051"    "Zn_EPA3051"    "water_pH"      "OM_by_LOI_pct"
## [13] "P_Mehlich3"    "K_Mehlich3"    "Ca_Mehlich3"   "Mg_Mehlich3"  
## [17] "Mn_Mehlich3"   "Zn_Mehlich3"   "Cu_Mehlich3"   "Fe_Mehlich3"  
## [21] "B_Mehlich3"    "S_Mehlich3"    "Na_Mehlich3"   "Al_Mehlich3"  
## [25] "Est_CEC"       "Base_Sat_pct"  "P_Sat_ratio"   "region"
```

Most of the column names are found in the data dictionary, but the very last column ("region") isn't. How peculiar! Let's look at what sort of values this particular column contains. The tab with the table of the `soil.views` object should still be open in the upper left pane of the RStudio window. If not, you can open it again by clicking on  `soils.view` in the Environment pane, or by using the `View()` command.


```r
View(soil.values)
```

<img src="resources/images/08-soil_values_object.png" title="Switch to the soil.values tab to look at what values are in the region column" alt="Switch to the soil.values tab to look at what values are in the region column" style="display: block; margin: auto;" />


If you scroll to the end of the table, we can see that "region" seems to refer to the city or area where the samples were collected. For example, the first 24 samples all come from Baltimore City.

<img src="resources/images/08-region.png" title="We can see the first samples in the dataset were collected in Baltimore City" alt="We can see the first samples in the dataset were collected in Baltimore City" style="display: block; margin: auto;" />


You may notice that some cells in the `soil.values` table contain _NA_. This just means that the soil testing data for that sample isn't available yet. We'll take care of those values in the next part.

::: {.reflection}
QUESTIONS:

1. How many observations are in the soil testing values dataset that you loaded? What do each of these observations refer to?

2. What data is found in the column labeled "Fe_Mehlich3"? Why would we be interested how much of this is in the soil? (You may have to search the internet for this answer.)

:::

## Part 2. Data Summarization

Now that we have the dataset loaded, let's explore the data in more depth.

First, we should remove those samples that don't have soil testing data yet. We _could_ keep them in the dataset, but removing them at this stage will make the analysis a little cleaner. In this case, as we know the reason the data are missing (and that reason will not skew our analysis), we can safely remove these samples. This will not be the case for every data analysis.

We can remove the unanalyzed samples using the `drop_na()` function from the `tidyr` package. This function removes any rows from a table that contains _NA_ for a particular column. This command follows the code structure:

dataset_new_name <- dataset %>% drop_na(column_name)

The `%>% is called a pipe and it tells R that the commands after it should all be applied to the object in front of it. (In this case, we can filter out all samples missing a value for "As_EPA3051" as a proxy for samples without soil testing data.)


```r
library(tidyr)

soil.values.clean <- soil.values %>% drop_na(As_EPA3051)
```

Great! Now let's calculate some basic statistics. For example, we might want to know what the mean (average) lead concentration is for each soil sample. According to the data dictionary, the values for lead concentration are in the column labeled "Pb_EPA3051". We can use a combination of two functions: `pull()` and `mean()`.`pull()` lets you extract a column from your table for statistical analysis, while `mean()` calculates the average value for the extracted column.

This command follows the code structure:

OBJECT %>% pull(column_name) %>% mean()

`pull()` is a command from the `tidyverse` package, so we'll need to load that library before our command.


```r
library(tidyverse)

soil.values.clean %>% pull(As_EPA3051) %>% mean()
```

```
## [1] 5.10875
```

We can run similar commands to calculate the standard deviation, minimum, and maximum for the soil arsenic values.


```r
soil.values.clean %>% pull(As_EPA3051) %>% sd()
```

```
## [1] 5.606926
```

```r
soil.values.clean %>% pull(As_EPA3051) %>% min()
```

```
## [1] 0
```

```r
soil.values.clean %>% pull(As_EPA3051) %>% max()
```

```
## [1] 27.3
```
As you can see, the standard deviation of the arsenic concentrations is listed first, then the minimum concentration, and finally the maximum concentration.

The soil testing dataset contains samples from multiple geographic regions, so maybe it's more meaningful to find out what the average arsenic values are for each region. We have to do a little bit of clever coding trickery for this using the `group_by` and `summarize` functions. First, we tell R to split our dataset up by a particular column (in this case, region) using the `group_by` function, then we tell R to summarize the mean arsenic concentration for each group. Because there are several different functions with the name `summarize` in R, we have to specify that we want to use `summarize` from the `dplyr` package. This command follows the code structure:

dataset %>%
    group_by(column_name) %>%
    dplyr::summarize(Mean = mean(column_name))
    

```r
soil.values.clean %>%
    group_by(region) %>%
    dplyr::summarize(Mean = mean(As_EPA3051))
```

```
## # A tibble: 2 × 2
##   region             Mean
##   <chr>             <dbl>
## 1 Baltimore City     5.56
## 2 Montgomery County  4.66
```

Now we know that the mean arsenic concentration might be different for each region, and appears higher for the Baltimore City samples than the Montgomery County samples.

::: {.reflection}
QUESTIONS:

3. What is the mean iron concentration for samples in this dataset? What about the standard deviation, minimum value, and maximum value?

2. Calculate the mean iron concentration by region. Which region has the highest mean iron concentration? What about the lowest?

:::

## Part 3. Data Visualization

Often, it can be easier to immediately interpret data displayed as a plot than as a list of values. For example, we can more easily understand how the arsenic concentration of the soil samples are distributed if we create histograms compared to looking at point values like mean, standard deviation, minimum, and maximum.

One way to make histograms in R is to use the `hist()` function. We can again use the `pull()` command and pipes (`%>%`) to choose the column we want from the `soil.values.clean` dataset and make a histogram of them. Remember, this command follows the code structure:

dataset %>%
    pull(column_name) %>%
    hist(main = chart_title, xlab = x_axis_title)

In this case, we do _not_ have to use the `dplyr::summarize` command before `hist()` because there's only one function called `hist()` in the packages we're using.


```r
soil.values.clean %>% 
    pull(As_EPA3051) %>% 
    hist(main = 'Histogram of Arsenic Concentration', 
         xlab ='Concentration in mg/kg' )
```

<img src="resources/images/08-data_exploration_files/figure-html/unnamed-chunk-17-1.png" width="672" />

We can see that almost all the soil samples had very low concentrations of arsenic (which is good news for the soil health!). In fact, many of them had arsenic concentrations close to 0, and only one sampling location appears to have high levels of arsenic. 

We might also want to graphically compare arsenic concentrations among the geographic regions in our dataset. We can do this by creating boxplots. Boxplots are particularly useful when comparing the mean, variation, and distributions among multiple groups. In R, one way to create a boxplot is using the `boxplot()` function. We don't need to use pipes for this command, but instead will specify what columns we want to use from the dataset inside the `boxplot()` function itself.

This command follows the code structure:

boxplot(arsenic_concentration ~ grouping_variable, 
    data = dataset,
    main = "Title of Graph",
    xlab = "x_axis_title",
    ylab = "y_axis_title")


```r
boxplot(As_EPA3051 ~ region, data = soil.values.clean,
        main = "Arsenic Concentration by Geographic Region",
        xlab = "Region",
        ylab = "Arsenic Concentration in mg/kg")
```

<img src="resources/images/08-data_exploration_files/figure-html/unnamed-chunk-18-1.png" width="672" />

By using a boxplot, we can quickly see that, while one sampling site within Baltimore City has a very high concentration of arsenic in the soil, in general there isn't a difference in arsenic content between Baltimore City and Montgomery County.

::: {.reflection}
QUESTIONS:

5. Create a histogram for _iron_ concentration, as well as a boxplot comparing iron concentration by region. Is the iron concentration similar among regions? Are there any outlier sites with unusually high or low iron concentrations?

6. Create a histogram for _lead_ concentration, as well as a boxplot comparing lead concentration by region. Is the lead concentration similar among regions? Are there any outlier sites with unusually high or low lead concentrations?

:::
