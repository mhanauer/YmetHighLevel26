# Example for Jags-Ymet-XmetSsubj-MrobustHier.R 
#------------------------------------------------------------------------------- 
# Optional generic preliminaries:
graphics.off() # This closes all of R's graphics windows.
rm(list=ls())  # Careful! This clears all of R's memory!
#------------------------------------------------------------------------------- 
# Load data file and specity column names of x (predictor) and y (predicted):
setwd("~/Desktop/Extending")
myData = read.csv( file="testData500.csv")
xName = "X" ; x2Name = "X2"; x3Name = "X3"; x4name = "X4"; x5name = "X5"; x6name = "X6"; x7name = "X7"; x8name = "X8"; x9name = "X9"; x10name = "X10"; x11name = "X11"; x12name = "X12"; x13Name = "X13" ; x14Name = "X14"; x15Name = "X15"; x16name = "X16"; x17name = "X17"; x18name = "X18"; x19name = "X19"; x20name = "X20"; x21name = "X21"; x22name = "X22"; x23name = "X23"; x24name = "X24"; x25name = "X25"; x26name = "X26"; yName = "Y" ; sName="Subj"
fileNameRoot = "HierLinRegressData-Jags-" 

graphFileType = "eps" 
#------------------------------------------------------------------------------- 
# Load the relevant model into R's working memory:
setwd("~/Desktop/Extending")
source("Jags-Ymet-XmetSsubj-26Vars-MrobustHierExtend.R")
#------------------------------------------------------------------------------- 
# Generate the MCMC chain:
#startTime = proc.time()
mcmcCoda = genMCMC(data=myData , xName=xName ,x2Name = x2Name, x3Name = x3Name, x4name = x4name, x5name = x5name, x6name = x6name, x7name = x7name, x8name = x8name, x9name = x9name, x10name = x10name, x11name = x11name, x12name = x12name, x13Name=x13Name ,x14Name = x14Name,x15Name = x15Name, x16name = x16name, x17name = x17name, x18name = x18name, x19name = x19name, x20name = x20name, x21name = x21name, x22name = x22name, x23name = x23name, x24name = x24name, x25name = x25name, x26name = x26name, yName=yName , sName=sName, numSavedSteps=20000 , thinSteps=15 , saveName=fileNameRoot )

#------------------------------------------------------------------------------- 
# Get summary statistics of chain:
summaryInfo = smryMCMC( mcmcCoda , saveName=fileNameRoot )
show(summaryInfo)

