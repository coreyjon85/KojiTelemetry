# Koji Incubator Telemetry Display & Logging
A low cost project to data log and display information from inside an incubator over WIFI using an ESP32, ESPhome, Home Assistant, Influx DB, and Grafana. 

# Motivation
Grow good Koji. I started with a pan, a heated low wattage seed mat, and two towels. Now I'm using a wildly overkill VWR laboratory incubator outfitted with all sorts of sensors to "Science the shit" out of growing Koji.

# Features
The main features are:
+ Low cost ESP32
+ Low cost sensors
  +  Temperature Probes (waterproof): DS18B20
  +  Temperature/Humidity Probe: DHT22
+ 3D Printed housing
+ Easy to source parts
+ Open Source software
+ Relatively accurate (after calibration*) for the price.
+ Easy to add different/more sensors.  

# Overview & Set Up
To get started, you will need Home Assistant running on a device, connected to your network. Follow the Home Assistant installation guide and ESPhome instructions to add ESPhome into Home assistant. Flash the ESP32 device using the ESPhome web flash tool. Ensure you can connect to the ESP32 within Home assistant before continuing. Install InfluxDB and Grafana inside Home Assistant. Connect and configure sensors on the ESP32. Pipe data from the ESP32 to InfluxDB via ESPhome. Use grafana to pull and display InfluxDB information. This is just the high level overview and assumes you have some experience with Influx and Grafana. 

1. [Home Assistant Installation Guide](https://www.home-assistant.io/installation/)
: I installed it on an old Linux laptop, but you can run it in Docker on a server, Raspberry Pie, Odroid, just about anything. This becomes the central hub. The IOT to world interface.
   
3. [ESP Home Website](https://esphome.io/)

4. [ESPhome Webflash Tool](https://web.esphome.io/)
   : Use this tool to flash the ESP device with ESPhome.

5. [InfluxDB & Grafana Installation video guide](https://www.youtube.com/watch?v=k-7dO1o52dQ&t=342s) - Credit to Smart Home Australia. 

6. [InfluxDB - the not so straight forward set up guide](https://community.home-assistant.io/t/the-correct-silly-walk-to-set-up-influxdb-as-of-august-2025/918306) - Credit & Thanks to Dave1041 over on H.A. Community guides.

7. Pull data from Influx into Grafana and create displays.

8. I'll admit - this guide is an "after the fact". There was definitely some keyboard smashing and general violence towards electronics. It does work (can work?). Once set up - it takes a minute to get accustomed to the lay of the land. How to configure sensors, how to pipe the data into influx. how to configure influx databases, and getting data to display in Grafana. Also, another issue (major importante) is choosing how and where you apply sensor filtering & calibration. This is definitely a compromise between absolute accuracy, and relative accuracy. The low cost sensors do not have an exactly linear output - so some calibration is required. Some calibration tips/tricks are below.

# Sensor Calibration
+ Deep Dive

# Images
+To Upload

# BOM
1. [ESP32-DEVKITM-1](https://www.digikey.com/en/products/detail/espressif-systems/ESP32-DEVKITM-1/13532113?gclsrc=aw.ds&gad_source=1&gad_campaignid=20243136172&gbraid=0AAAAADrbLlglXqGW4TPwWqV9fLs0IMHkx&gclid=CjwKCAjw1bvTBhBbEiwAzbP8L6URBTwrSLkT77qroA4ytF3CREPpHZEOK6bwIzumCABcsSR3MVFebhoCGncQAvD_BwE)
2. [DS18B20](https://www.amazon.com/dp/B0FLDRGXZD?ref=ppx_yo2ov_dt_b_fed_asin_title)
3. [DHT22](https://www.amazon.com/dp/B0795F19W6?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1)
4. [12" Micro USB extension](https://www.amazon.com/dp/B0G33MZ3VK?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1)
5. [5mm Cube Magnets](https://www.amazon.com/Caturledas-5x5x5-Earth-Neodymium-Magnets/dp/B0GTTY5TYY/ref=sr_1_1_sspa?crid=SMS991TRY9L6&dib=eyJ2IjoiMSJ9.YuysQAkgmip-e1tGxGbj1-Oumz6swO_Ggf1x9fxzHFgCCq7vGJy1EoVCvO7g1KrhdAv9EYy9KRaXUbhbGZFsAepaAuWHDoAkhknllG5vcSBIhMF6TUEDyR9fyaxhXVo7HMoWv9mWBIUOsQNjqlK9xVPSvT5g9k0PN-bIV2KnJOzRTCOwsw35isx7DAPTlqIjZ9obCnNeCw5iwOEkZiNv1cr4C2UCnOuFyAqKS3T8QUs.BpG5f234ZG2lgRRtLJvHBxrSCJ8gorNR-AL7ePW4NfA&dib_tag=se&keywords=5mm%2Bcube%2Bmagnet&qid=1785696436&sprefix=2mm%2Bcube%2Bmagnet%2Caps%2C205&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1)
6. [M3 Stainless Steel Socket Head Screws](https://www.amazon.com/Sutemribor-Stainless-Button-Socket-Assortment/dp/B07CYGD9XK/ref=sr_1_15?crid=3DFB78RMGE5T&dib=eyJ2IjoiMSJ9.6x6x32B24HjHaFxpx8pxywew0iE0LqpKPqfbnQ_8L7L1w_4SpE6wxCS6eQTsN-OFWDIfzUWWC7pL17oULapY_QArcEl1RZ7S2f1XKdmdvtaGSfTkaqnCWUtaAhFoY-pgVsRmcp_JHPBhLxu-DVUFS0k1Kow2IyKVsEPrb84dl_a3vDqFzaVVwT-yqcbMchcqB1mDbvdNZvc2xCts9bX6lWXdCKMvJhTTyJpcQL7FBYg.Gb5W-fqMa-7-iD1fged-xCWkZM04ata2qzxt6vgiTOA&dib_tag=se&keywords=stainless+steel+button+head+hex+m3+m4+m5&nsdOptOutParam=true&qid=1785696918&sprefix=stainless+steel+button+head+hex+m3+m4+m%2Caps%2C158&sr=8-15)
7. [M3 Brass Heat Embedded Nuts](https://www.amazon.com/Ktehloy-Threaded-Assortment-Printing-Components/dp/B0CLKDPN65/ref=sr_1_1_sspa?crid=1M5V553I2UVP0&dib=eyJ2IjoiMSJ9.o6PoE-P-qC5hhld3Z-KaQBlznrAc44qmILpRw9k-CYO_RfN1YuYYx5YqJxAscHvTOMimrSvOrppgnl6X9tW49fZuzpNJ3VfNUgC5-3OV8VEQDZtwLOKOhz5yG2lwdAeA07EpBglOwbWxwjWelFlGxrWz5tEQFmyjxotvqPO-Fvo3AY4KPSoiDoAIbiQbdf6l7eUnbA5NCEgmbfAOfgQjmsGdnABK7TH5WEXBlnno1hA.8fYkLMPWgmVNNDlO6WWEATlcMOAHzrAndW4OS-KEjdk&dib_tag=se&keywords=brass%2Bembedded%2Binserts&qid=1785696613&sprefix=brass%2Bembedded%2Binster%2Caps%2C157&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&th=1)
8. [1/2 breadboard](https://www.amazon.com/ELEGOO-tie-points-breadboard-Arduino-Jumper/dp/B01EV640I6/ref=sr_1_4?crid=1AFKUBYID17FQ&dib=eyJ2IjoiMSJ9.64MecujH952nZ2nId_0qVSZ4nLxKEG0K3BOewUgIsbY52ZyWfvefjL9SXY1kzSNaZPFTbj_XV4Qv_bcQuHHc7eO6Abf2L2tkXFl2sPvDiT-y0hLfNUKkY8oojwTE5d69UIsli8dU8MwZOlcos0IZff-28DNcgm8mqA7QrLNxxJUd2dvFPDvA4hIjxEnR22bXhV2qq9pcJ9naoVfDQLbQ0-TMZWlvs6ZYH4D66T3xDUE.76jcylhERc6VmYtSRVaJ0096fwuA6bgOKyCV_WgdO9Q&dib_tag=se&keywords=half%2Bbreadboard&qid=1785696994&sprefix=half%2Bbreadboar%2Caps%2C177&sr=8-4&th=1)
9. 3D Printed Housing - will upload part files.

# Part Files
+Coming Soon.
