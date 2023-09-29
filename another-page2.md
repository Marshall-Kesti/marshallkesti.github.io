---
layout: default
---

# Welcome to my Python Project Page!

[Back to Main Page](./index.md)

---
## _Python Stock Indicator_
### Description

During the time of this project, I was being mentored by a full time trader. One of the processes that he was educating me on was backtesting. This involves collecting trades that meet your specficed critera from a stock that you are intrested in trading. At first collecting the trades was educative, but after the hundreth some trade, I decided to reallocate my time to finding a more efficent way to quickly and accuratly collect the desired data. 

### Note

Due to this project involving information not obtainble by the general public, broad terms will be used in place of specfic terms throughout the project (especially within the code).

### Process

In order to begin writing the code for this project, I needed to make sure that I was able to define the patterns that I wanted Python to uncover. I did this by grabbing a piece of scratch paper and jotting down the terms. Then, I established my main objective for the project... to create a simple system that could detect the relationships between numbers. 

The first step I took was importing the data using a package in python called "yfinance."

```
import yfinance as yf

stock = yf.Ticker("ticker")

dataframe = stock.history(period="1y")

print(dataframe.to_csv())
```

``` 
# Python output (example)
```
```
2023-09-20 00:00:00-04:00,267.0400085449219,273.92999267578125,262.4599914550781,262.5899963378906,122514600,0.0,0.0
2023-09-21 00:00:00-04:00,257.8500061035156,260.8599853515625,254.2100067138672,255.6999969482422,119531000,0.0,0.0
2023-09-22 00:00:00-04:00,257.3999938964844,257.7900085449219,244.47999572753906,244.8800048828125,127024300,0.0,0.0
2023-09-25 00:00:00-04:00,243.3800048828125,247.10000610351562,238.30999755859375,246.99000549316406,104636600,0.0,0.0
2023-09-26 00:00:00-04:00,242.97999572753906,249.5500030517578,241.66000366210938,244.1199951171875,101741600,0.0,0.0
2023-09-27 00:00:00-04:00,244.26199340820312,245.3300018310547,241.4199981689453,243.13999938964844,36984949,0.0,0.0
```

Next, in order to transfer the output into a csv file, I entered the following into the terminal:

```
Python3 name_of_project.py > name_of_file.csv
```

```
# Python output (example)
```
```
Date,Open,High,Low,Close,Volume,Dividends,Stock Splits                                                             
2022-09-26 00:00:00-04:00,271.8299865722656,284.0899963378906,270.30999755859375,276.010009765625,58076900,0.0,0.0 
2022-09-27 00:00:00-04:00,283.8399963378906,288.6700134277344,277.510009765625,282.94000244140625,61925200,0.0,0.0 
2022-09-28 00:00:00-04:00,283.0799865722656,289.0,277.57000732421875,287.80999755859375,54664800,0.0,0.0           
2022-09-29 00:00:00-04:00,282.760009765625,283.6499938964844,265.7799987792969,268.2099914550781,77620600,0.0,0.0
```

Once I had the data in a csv file, it was time to start writing the code for the stock indicator. The first step in this process was creating definitions and importing a csv package. 

```
import csv


def is_bearish_candlestick(candle):
    return float(candle['criteria'] > candle['critera'])

def is_bullish_candlestick(candle):
    return float(candle['criteria'] > candle['criteria'])

def pattern1(candles, index):
    current_day = candles[index]
    previous_day = candles[index-1]

    if is_bearish_candlestick(previous_day) \
        and float(current_day['criteria'] > previous_day['critera']) \
        and float(current_day ['critera'] > previous_day['criteria']):
        return True

def swing_down(candles, index):
    current_day = candles[index]
    previous_day = candles[index-1]

    if is_bullish_candlestick(previous_day) \
        and float(current_day['critera] < previous_day['critera']) \
        and float(current_day ['critera'] < previous_day['critera']):
        return True
```

Once everything was defined, I had to write the code for the indicator to be printed out and properly formatted. Below is that code:

```
with open('dataframe.csv') as f:
    reader = csv.DictReader(f)
    print(reader)
    candles = list(reader)

    for i in range(1, len(candles)):
        if swing_up(candles, i):
            print("Pattern Detected              {}                            {}                                  {}".       format(candles[i]['High'], candles[i]['Low'], candles[i]['Date']))
        elif swing_down(candles, i):
            print("Second Pattern Detected       {}                            {}                                  {}". format(candles[i]['High'], candles[i]['Low'], candles[i]['Date']))

```

```
# Python ouput (example)
Pattern Detected              273.92999267578125                            262.4599914550781                                  2023-09-20 00:00:00-04:00
Second Pattern Detected       260.8599853515625                            254.2100067138672                                  2023-09-21 00:00:00-04:00
Second Pattern Detected       257.7900085449219                            244.47999572753906                                  2023-09-22 00:00:00-04:00
Second Pattern Detected       247.10000610351562                            238.30999755859375                                  2023-09-25 00:00:00-04:00
Pattern Detected              249.54989624023438                            241.6699981689453                                  2023-09-26 00:00:00-04:00
```

Finally, I could take the data that met the specified criteria and insert it into a csv file for further analysis. To do this, I entered the following into the terminal:

```
python3 project.py > newdata.csv
```

```
# Python output (example)
```
```
Pattern Detected              288.6700134277344                            277.510009765625                                  2022-09-27 00:00:00-04:00
Pattern Detected              289.0                            277.57000732421875                                  2022-09-28 00:00:00-04:00
Second Pattern Detected       283.6499938964844                            265.7799987792969                                  2022-09-29 00:00:00-04:00
Second Pattern Detected       275.57000732421875                            262.4700012207031                                  2022-09-30 00:00:00-04:00
```

### Conclusion

This project made the process of collecting specific data quick and easy, resulting in the ability to conducts analyses faster. 
