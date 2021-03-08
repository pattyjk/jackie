#install BlandAltman package & ggplot
install.packages("BlandAltmanLeh")
install.packages("ggplot2")

#load packages
library("BlandAltmanLeh")
library("ggplot2")

#load data

acti<-read.delim('acti.txt', header=T)
ema<-read.delim("EMA.txt", header=T)

#Pull SOL data from separate dataframes 
#ACT_Onset_Latency is in the Actigraph.xlsx datasheet
#E_SOL_minutes is in the EMA.xlsx

ACT_Onset_Latency <-acti$ACT_Onset_Latency
E_SOL_minutes <-ema$E_SOL_minutes


bland.altman.stats(ema$E_SOL_minutes, acti$ACT_Onset_Latency, two=1.96, mode=1, conf.int=0.95)


#Check string length
str(ACT_Onset_LatencyNum)
str(E_SOL_minutesNum)

#Calculate BlandAltman stats for SOL
bland.altman.stats(ACT_Onset_Latency, E_SOL_minutes, two=1.96, mode=1, conf.int=0.95)
print(bland.altman.stats(ACT_Onset_Latency, E_SOL_minutes))
print(bland.altman.stats(ACT_Onset_Latency, E_SOL_minutes)$critical.diff)
