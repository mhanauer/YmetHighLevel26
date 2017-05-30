# Example for Jags-Ymet-XmetSsubj-MrobustHier.R 
#------------------------------------------------------------------------------- 
# Optional generic preliminaries:
graphics.off() # This closes all of R's graphics windows.
rm(list=ls())  # Careful! This clears all of R's memory!
#------------------------------------------------------------------------------- 
# Load data file and specity column names of x (predictor) and y (predicted):
setwd("~/Desktop/Extending")
myData = read.csv( file="testData15.csv")
xName = "X" ; x2Name = "X2"; x3Name = "X3"; x4Name = "X4"; x5Name = "X5"; x6Name = "X6"; x7Name = "X7"; x8Name = "X8"; x9Name = "X9"; x10Name = "X10"; x11Name = "X11"; x12Name = "X12"; x13Name = "X13" ; x14Name = "X14"; x15Name = "X15"; x16Name = "X16"; x17Name = "X17"; x18Name = "X18"; x19Name = "X19"; x20Name = "X20"; x21Name = "X21"; x22Name = "X22"; x23Name = "X23"; x24Name = "X24"; x25Name = "X25"; x26Name = "X26"; yName = "Y" ; sName="Subj"
fileNameRoot = "HierLinRegressData-Jags-" 

graphFileType = "eps" 
#------------------------------------------------------------------------------- 
# Load the relevant model into R's working memory:
setwd("~/Desktop/Extending")
source("Jags-Ymet-XmetSsubj-26Vars-MrobustHierExtend.R")
#------------------------------------------------------------------------------- 
# Generate the MCMC chain:
#startTime = proc.time()
mcmcCoda = genMCMC(data=myData , xName=xName ,x2Name = x2Name, x3Name = x3Name, x4Name = x4Name, x5Name = x5Name, x6Name = x6Name, x7Name = x7Name, x8Name = x8Name, x9Name = x9Name, x10Name = x10Name, x11Name = x11Name, x12Name = x12Name, x13Name=x13Name ,x14Name = x14Name,x15Name = x15Name, x16Name = x16Name, x17Name = x17Name, x18Name = x18Name, x19Name = x19Name, x20Name = x20Name, x21Name = x21Name, x22Name = x22Name, x23Name = x23Name, x24Name = x24Name, x25Name = x25Name, x26Name = x26Name, yName=yName , sName=sName, numSavedSteps=20000 , thinSteps=15 , saveName=fileNameRoot )

#------------------------------------------------------------------------------- 
# Get summary statistics of chain:
summaryInfo = smryMCMC( mcmcCoda , saveName=fileNameRoot )
show(summaryInfo)

