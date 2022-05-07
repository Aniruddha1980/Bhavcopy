# Bhavcopy
Bhavcopy of NSE App, Where you can get all details on single click.

Below options are available 

1 --> bhavcopy display (Also you can downloand the same).
2 --> stock_deliv_data (You can see the Stock delivery data with candlestick graph).
3 --> High_low_deliv (You can sort the data based on High and Low).
4 --> stock_oi_data (You can get Stock option data).
5 --> future_builtup (Can see Future built up data with Graphical representation).
6 --> historical_option_chain (Can see Options chain data for Index as well as Stocks).
7 --> put_call_ratio (With graphical representation).

Thanks to Pynse developers who made our life easy to populate the required details from NSE (using web scrapping).

pynse

Library to extract realtime and historical data from NSE website.EOD data like bhavcopy and option chain are also saved to directory. First run will create directories for storing the data and will download the index symbols.
Installation

This module is installed via pip:

pip install pynse

Prerequisites

Python 3.6
Using the API
Overview

There is only one class in the whole library Nse.
Logging

The whole library is equipped with python's logging moduele for debugging. If more debug information is needed, enable logging using the following code.

import logging
logging.basicConfig(level=logging.DEBUG)

from pynse import *

Only one class for this python pgm
nse=Nse()

make sure datapath is absolute otherwise it will create data folders in every run
Get Market Status

nse.market_status()

Get Symbol Information

nse.info('SBIN')

Get Quote

Get realtime quote for EQ, FUT and OPT. If no expiry date is provided for derivatives, returns date for nearest expiry.

for cash

nse.get_quote('RELIANCE')

for futures

nse.get_quote('TCS', segment=Segment.FUT, expiry=dt.date( 2020, 6, 30 ))

for options

nse.get_quote('HDFC', segment=Segment.OPT, optionType=OptionType.PE)

Bhavcopy for Cash

download bhavcopy from nse or read bhavcopy if already downloaded

nse.bhavcopy()

or

nse.bhavcopy(dt.date(2020,6,17))

Bhavcopy for F&O

download bhavcopy from nse or read bhavcopy if already downloaded

nse.bhavcopy_fno()

or

nse.bhavcopy_fno(dt.date(2020,6,17))

Pre Open data

get pre open data from nse

nse.pre_open()

Option Chain

Downloads the option chain or reads if already downloaded. if req_date is not specified returns latest available option chain from nse website

This returns dictonary containing timestamp as str option chain as pd.Dataframe expiry_list as list

nse.option_chain('INFY')

or

nse.option_chain('INFY',expiry=dt.date(2020,6,30))

FII and DII Data

get FII and DII data from nse

nse.fii_dii()

Historical Data

get historical data from nse symbol index or symbol

nse.get_hist('SBIN')

or

nse.get_hist('NIFTY 50', from_date=dt.date(2020,1,1),to_date=dt.date(2020,6,26))

Realtime Index

Get realtime index value

nse.get_indices(IndexSymbol.NiftyInfra)

or

nse.get_indices(IndexSymbol.Nifty50)

Top Gainers and Losers

presently works only for SECURITIES IN F&O

nse.top_gainers(10)

or

nse.top_losers(10)

Update Symbol Lists

Update list of symbols.No need to run frequently, its only required when constituent of an index is changed or list of securities in fno are updates

nse.update_symbol_list()
