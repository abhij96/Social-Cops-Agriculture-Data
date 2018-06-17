# Social-Cops-Agriculture-Data
A iPython / Jupyter notebook code to clean, process and visualize data from Maharashtra governments database. This data pertains to prices of 204 different crops being sold over 349 different APMC in the state located in 50 different districts.



## Python packages used -

  Numpy
  
  Pandas
  
  Matplotlib
  
  statsmodels
  
  IPython.display
  



## Variables used -
  
  df1 -> DataFrame used to read and store data from Monthly_data_cmo.csv file. It contains actual min_price, max_price, modal_price       inormation
  
  df2 -> DataFrame used to read and store data from CMO_MSP_Mandi.csv file. It contains Minimum Support Price information for various     crops
  
  commodity -> Used to store the unique list of commodities for which market price data is available  
  
  apmc -> Used to store the unique list of commodities for which mandi/market price data is available
  
  n -> Size of commodity list
  
  m -> Size of apmc list
  
  test -> dictonary of DataFrames, with each dataframe containing filtered price data of a combinantion of commodity and apmc
  
  i,j -> Iterable variables to establish test as dictonary of DataFrames
  
  q -> key of test. Each value of q maps against a unique DataFrame containing price information
  
  'Seasonality' -> A column describing type of seasonality observed in price timeseries data
  
  'deseasonal' -> A column containing the deseasonalized price data of commodities
  
  'Peak seasonal price fluctuation %' -> A column containing the maximum flucatuation observed in modal price form mean value
  
  'Raw vs MSP diff' -> A column containing difference in raw(actual) price and minimum support price
  
  'Desasonal vs MSP diff' -> A column containg difference in deseasonal price and minimum support price
  
  A -> A DataFrame containg list of APMC and Commodity combinations for which price information was processed.
  
  sel -> An integer variable which takes input from user to showcase the selected APMC and Commodity information
  
  
  
  
## Process Flow -
  
  1. Input market price data and minimum support price data 
  2. Perform basic data cleaning checks like-
    a. max_price > modal_price > min_price
    b. max_price>0 & modal_price>0
    c. max_price < 1000000
    d. Convert all commodities name to lower case 
    e. Reformat names of commodities bhagar/vari to bhagar-vari and thymol/lovage to thymol-lovage
  3. Creating list of unique commodity and APMC in data, and slice market price data into new dataframe for each APMC - Commodity         combination
  4. Enriching each data frame with relevant minimum support price data if available
  5. Finding seasonality in modal_price data for each APMC-Commodity combination, using both additive and multiplicative models.
  6. Find deseasonal price and peak seasonal price fluctuation, along with price difference between raw modal and MSP along with            deseasonalized modal and MSP
  7. Save the processed DataFrames in individual file
  8. Print the price trend chart of the APMC-Commodity combination selected by the user.
