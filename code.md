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

#merge data frame by ID and dates
new_data<-merge(acti, ema, by.x=c("ACT_Start_Date", "ID"), by.y=c("E_CorrectedDate", "ID"))

# calculate data
bland.altman.stats(new_data$E_SOL_minutes, new_data$ACT_Onset_Latency, two=1.96, mode=1, conf.int=0.95)

#write data frame to file
write.csv(new_data, 'jaque_merged.csv', row.names=F)

#Check string length
str(ACT_Onset_LatencyNum)
str(E_SOL_minutesNum)

#Calculate BlandAltman stats for SOL
bland.altman.stats(ACT_Onset_Latency, E_SOL_minutes, two=1.96, mode=1, conf.int=0.95)
print(bland.altman.stats(ACT_Onset_Latency, E_SOL_minutes))
print(bland.altman.stats(ACT_Onset_Latency, E_SOL_minutes)$critical.diff)
