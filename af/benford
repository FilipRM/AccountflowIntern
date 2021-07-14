#Transactions
import pandas as pd
import math
import numpy as np
import matplotlib.pyplot as plt



df = pd.read_csv("/Users/filiprm/Documents/Accountflow/transactions.csv", 
       names=["TransactionNr", "Type", "Date", "Value", "PeriodNr", "Year", "u"])

class Transactions:
    
    def zeroCheckIB(self, data):
        x = data.where(data.PeriodNr == 0).Value.sum()
        return x
    
    def zeroCheckYear(self, data):
        y = data.groupby(["Year"])["Value"].sum()
        return y

    def extractFirsts(self, data):
        data.Value = data.Value.astype(str).str.replace("-", "")
        firsts = list(data.Value.str[0])
        return firsts
    
    def numbCounter(self, data):
        numbers = []
        percentages = []
        for i in range(1,10):
            numbers.append(self.extractFirsts(data).count(str(i)))
            
        for i in range(0, 9):
            percentages.append(numbers[i]/sum(numbers))
        
        return percentages
    
    def graphPlot(self, data):
        percentages = self.numbCounter(data)
        expected = [math.log10(1+1/d) for d in range(1,10)]
        
        dataLists = pd.DataFrame({"Expected": expected, "Actual": percentages}, index = range(1,10))
        dataLists.plot.bar()
    


tr = Transactions()    
e = tr.zeroCheckIB(df)
percentages = tr.numbCounter(df)
g = tr.extractFirsts(df)
n = tr.numbCounter(df)
tr.graphPlot(df)




                

    
        


