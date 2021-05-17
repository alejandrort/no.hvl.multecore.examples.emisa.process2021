# Multilevel Modelling with MultEcore: A contribution to theMULTI Process challenge
## Submitted to the EMISAJ Special Issue: "Multi-Level Process Challenge"
In this repository one can find all the necessary files to inspect the multilevel hierarchy presented in the article, as well as reproduce the executions shown.
Before actually showing how to do this, **for the moment the MultEcore-Maude implementation only works on Windows**. There are also some installation required:
- Install [Maude for Windows](http://maude.sip.ucm.es/strategies/#downloads) The only thing one has to do is to put all the downloaded files into a directory, and create the appropiate environment variables so it is runnable from any point. This last step is very important for the infrastructure within MultEcore to work and recognise Maude commands.
- Install the latest version of [Obeo Designer](https://www.obeodesigner.com/en/download).
- Include all the given MultEcore installation files within the *plugins* folder in the Obeo installed directory.
- Once running Obeo, make sure you install the first two packages under the "Xtext" group, using the update site and the instructions that they provide at: https://eclipse.org/Xtext/download.html.
##  Running the examples
We encourage the reader to check [MultEcore](https://bitbucket.org/phd-fernando/no.hvl.multecore/src/master/) and [MultEcore MCMTs](https://bitbucket.org/phdalejandro/no.hvl.multecore.mcmt/src/master/) main repositories webpages for an intuition on how MultEcore works and can be activated on a concrete project.
Import all the projects within the [Solution](https://github.com/MultEcore/no.hvl.multecore.examples.emisa.process2021/blob/master/solution.zip) folder of this repository (three projects should have been imported: *no.hvl.multecore.examples.emisa.process2021.main*, *no.hvl.multecore.examples.emisa.process2021.timestamp* and *no.hvl.multecore.mcmt.examples.emisa.process2021.main*. Then activate MultEcore with the main project selected *no.hvl.multecore.examples.emisa.process2021.main*. If everything worked, one should see a tab where the structure of the multilevel hierarchy is shown (if this view is not shown one can open it in Window > Show View > Other... > MultEcore Views > Hierarchy View) and show something similar to:

![Hierarchy View](https://i.imgur.com/A0H3Q6x.jpg)

To open one of the graphical representation of the models, just double click in one in the shown view. Also one can open the .aird representation file through the Project Explorer and select the already existing Diagrams:

![Project Explorer](https://i.imgur.com/zFqoIjZ.jpg)

The MCMT rules created can be seen in its text editor opening the *process.mcmt* within the *no.hvl.multecore.mcmt.examples.emisa.process2021.main* project.
## Using the Maude facilities
To get to this point, one has to have activated MultEcore in *no.hvl.multecore.examples.emisa.process2021.main*, and do a modification and save the *process.mcmt* so the rules are loaded (adding a white space and removing it in any line and saving the changes is enough).
Also, in the Console view, go to the right and unfold the ▼ arrow to select another Console view and select the MultEcore Console.
Now, right click on *no.hvl.multecore.examples.emisa.process2021.main* and navigate to MultEcore > MultEcore to Maude. Once you click it, a wizard will appear where different models are listed (only the instance models are shown), select one and press OK. After this, a new dialog will appear to select which MCMT rules want to be transformed. You can select all of them so they are all available for the execution. This will load the Maude files and use the selected model as the model to be executed.
After this, all the necessary Maude files should have been created under the *maude-outputs* folder, which are ready to be run. These can be taken and run with the Maude facilities through its console as well. Now there are two possibilities to perform an execution. We provide two Maude strategies, one is by selecting the number of steps to be directly performed (this is, how many of the available rules are going to be executed, if they are applicable) and the other is by explicitely giving the rules order to be done. In the following we show both possibilities.
### Execute N steps
Select the corresponding icon (highlighted in the figure), and a dialog to introduce the number of steps will appear (1 in the figure). After introducing it, you will be asked to name the new model state (2 in the figure). Once named it, the engine will run and if there is not error, a notification dialog should appear stating that the new model has been succesfully created (3 in the figure). This model can be opened through the corresponding .aird file in the Project Explorer. The figure below shows all the steps for clarification:

![Execute 3 steps](https://i.imgur.com/cPZ8fDY.png)

**Note the current state of the engine forces the modeller to stop the Maude process before performing another execution, unless it is going to be done in the current loaded instance model. Therefore, if we are about to run over some new created model, one has to press the right-most forbidden symbol in the editor. Then once you have been notification that the process has been succesfully stopped, you can proceed again to transform the new MultEcore state (steps described in the last paragraph of *Using the Maude facilities* section**)
### Sequential execution
Select the corresponding icon (highlighted in the figure), and set the name of the new output model in the dialog. Then A wizard will appear where we can set the rules, the number of times each one should be applied and in which order. In the figure below, the example shown will produce a finaltask using the *xsure-execution-step1 as initial model*:

![Sequential execution towards finaltask](https://i.imgur.com/dEtZ5B6.png)

Thus, if we open the created finaltask model (through its .aird, see figure below), we have the produced finaltask with a freshly created id:

![finaltask128 created](https://i.imgur.com/FWfHtft.jpg)
