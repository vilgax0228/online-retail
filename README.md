This is a transactional data set which contains all the transactions occurring between 01/12/2010 and 09/12/2011 for a UK-based and registered non-store online retail.The company mainly sells unique all-occasion gifts. Many customers of the company are wholesalers.

**InvoiceNo:** Invoice number. Nominal, a 6-digit integral number uniquely assigned to each transaction. If this code starts with letter 'c', it indicates a cancellation.  
**StockCode:** Product (item) code. Nominal, a 5-digit integral number uniquely assigned to each distinct product.  
**Description:** Product (item) name. Nominal.  
**Quantity:** The quantities of each product (item) per transaction. Numeric.  
**InvoiceDate:** Invoice Date and time. Numeric, the day and time when each transaction was generated.  
**UnitPrice:** Unit price. Numeric, Product price per unit in sterling.  
**CustomerID:** Customer number. Nominal, a 5-digit integral number uniquely assigned to each customer.  
**Country:** Country name. Nominal, the name of the country where each customer resides.


Instalando e chamando os pacotes necessários
```R
install.packages(c("tidyverse", "readxl", "lubridate", "skimr", "scales"))
library(tidyverse)
library(readxl)
library(lubridate)
library(skimr)
library(scales)
```

Visualizando por cima as informações do dataset
```R
data <- read_excel("Online Retail.xlsx")
nrow(data)
ncol(data)
str(data)
head(data)
glimpse(data)
skim(data)
summary(data)
```

Que pergunta queremos responder? Aqui, vamos supor que temos interesse em quais itens foram vendidos, quantidade de itens vendidos e o preço.

Outra coisa, quais as variáveis relevantes do dataset para nossa pergunta? Podemos tirar, por exemplo, as seguintes variáveis: InvoiceNo, StockCode, InvoiceDate, CustomerID e Country.

Vamos ver se há NA valores e tirar caso tenha.
```R
colSums(is.na(data))
data <- data %>% drop_na(Description)
```






