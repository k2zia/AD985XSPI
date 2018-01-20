/********************************************************************************************
* Arduino library for AD9850 and AD9851
* Created 23/08/2014
* Christophe Caiveau f4goj@free.fr
* Upgrade to SPI Anthony F4GOH
*
* Updated Version: Farrukh Zia, K2ZIA 2018_0101
* – Updated library functions to comply with latest SPI library in IDE v1.8.5
* – Implemented correct SPI bus initialization sequence
* – Implemented correct AD985x initialization sequence
* – Added support for AD9851 (30 MHz oscillator, 180 MHz system clock)
* – Increased SPI-DDS bus speed to 8MHz (default) (other options are 4MHz and 2MHz)
*
* This library uses the Serial Peripheral Interface (SPI)
* to accelerate the update of the AD985x from 700µs in software serial to:
* – 90µs (54µs for deltaphase calculation and 36µs for transfer) @ 2MHz SPI bus speed
* – 68µs (54µs for deltaphase calculation and 14µs for transfer) @ 8MHz SPI bus speed (default)
*
* Use this library freely
*
* Hardware connections :
* W_CLK -> D13 arduino UNO/NANO, D52 MEGA
* FQ_UD -> any pin except 10 and 12 UNO/NANO, 50 and 53 MEGA
* DATA/D7 -> D11 arduino UNO/NANO, D51 MEGA
* RESET -> any pin except 10 and 12 UNO/NANO, 50 and 53 MEGA
*
* Functions :
* DDS.begin(W_CLK pin, FQ_UD pin, RESET pin); initialize the output pins and master reset AD985x
* DDS.calibrate(trimFreq); compensation of crystal oscillator frequency
* DDS.setfreq(frequency); frequency in Hz
* DDS.down(); power down mode reducing the dissipated power from 380mW to 30mW @5V
* DDS.up(); wake-up the AD985x from power down mode
*
* AD9850 datasheet at http://www.analog.com/static/imported-files/data_sheets/AD9850.pdf
* AD9851 datasheet at http://www.analog.com/static/imported-files/data_sheets/AD9851.pdf
*
*******************************************************************************************/
