---
title: Assignment 1
subtitle: Computer performance, reliability, and scalability calculation
author: Rebecca Lewis
---

## 1.2 

#### a. Data Sizes

| Data Item                                  | Size per Item | 
|--------------------------------------------|--------------:|
| 128 character message.                     | 128 Bytes [1] |
| 1024x768 PNG image                         | .75 MB [2]    |
| 1024x768 RAW image                         | 1.5 MB [3]    | 
| HD (1080p) HEVC Video (15 minutes)         | 51 GB [4]     |
| HD (1080p) Uncompressed Video (15 minutes) | 51 GB [5]     |
| 4K UHD HEVC Video (15 minutes)             | 217 GB [6]    |
| 4k UHD Uncompressed Video (15 minutes)     | 218 GB [7]    |
| Human Genome (Uncompressed)                | 725 MB [8]    |

[1] Character Sets. (n.d.). Retrieved December 2, 2020, from https://web.cortland.edu/flteach/mm-course/characters.html
[2] Calculated assuming a bit depth of 8 and calculation from https://4nsi.com/faq/how-do-i-calculate-the-file-size-for-a-digital-image. Determined bit depth from https://en.wikipedia.org/wiki/Portable_Network_Graphics
[3] Calculated assuming a bit depth of 16 and calculation from https://4nsi.com/faq/how-do-i-calculate-the-file-size-for-a-digital-image.  Determined  bit depth from https://www.nikonimgsupport.com/na/NSG_article?articleNo=000026447&configured=1&lang=en_SG.
[4] Calculated using the formula from https://www.circlehd.com/blog/how-to-calculate-video-file-size.  Retrieved compression ratio of 1000:1 from https://en.wikipedia.org/wiki/High_Efficiency_Video_Coding.
	bitrate = 1024 x 1920 x 30fps = 58982400 = 58mbps
	File Size = 58mbps x 900s x 1000/1001 = 52147.8 mb / 1024 = 51gb			
[5] Calculated using same formula as [4] but with no compression ratio
	bitrate = 1024 x 1920 x 30fps = 58982400 = 58mbps
	File Size = 58mbps x 900s  = 52200.8 mb / 1024 = 51gb			
[6] Calculated using same formula as [4] but with 4k frame size
	bitrate = 3840	x 2160 x 30fps = 58982400 = 248 mbps
	File Size = 248 mbps x 900s x 1000/1001 = 222976.8 mb / 1024 = 217gb
[7] Calculated using same formula as [4] but with 4k frame size and without compression ratio
	bitrate = 3840	x 2160 x 30fps = 58982400 = 248 mbps
	File Size = 248 mbps x 900s  = 223200 mb / 1024 = 218gb
[8] https://en.wikipedia.org/wiki/Human_genome#Information_content
	

#### b. Scaling

|                                           | Size     | # HD | 
|-------------------------------------------|---------:|-----:|
| Daily Twitter Tweets (Uncompressed)       | 192 GB   |  1   | [9]
| Daily Twitter Tweets (Snappy Compressed)  | 83 GB    |  1   | [10]
| Daily Instagram Photos                    | 56 MB    |  1   | [11]
| Daily YouTube Videos                      | 2387 TB  |  717 | [12]
| Yearly Twitter Tweets (Uncompressed)      | 67 TB    |  21  | [13]
| Yearly Twitter Tweets (Snappy Compressed) | 234gb    |  9   | [14]
| Yearly Instagram Photos                   | 20 GB    |  1   | [15]
| Yearly YouTube Videos                     | 871255 TB|261,377| [16]

[9] 500 Million tweets = 128 * 500,000,000 = 64,000,000,000 = 64gb
	Hadoop conv = 64 gb * 3 = 192 gb

[10] Based on example provided in the article https://blog.openbridge.com/what-is-google-snappy-high-speed-data-compression-and-decompression-f6919f20dce4
	Example 2.4mb/5.6mb = ~43% smaller
	192 GB * .43 = 82.56 gb
	Hadoop conversion = 83 * 3 = 248gb

[11] 75 million png photos *.75 MB = 56 MB
	Hadoop conversion = 56mb * 3 = 168mb
[12] 500 hours of video is uploaded to YouTube every minute.
	60 minutes * 24 hours = 1440 minutes
	1440 minutes * 500 hours of videos per minute = 720000 hours of videos per day
     	720000 hours * 60 minutes = 
	bitrate = 1024 x 1920 x 30fps = 58982400 = 58mbps
	File Size = 58mbps x 43200000s x 1000/1001 = 2503094400 mb / 1024 /1024 = 2387 TB

	Hadoop conversion: 2387 TB * 3 = 7161 TB / 10 TB = 716.14
[13] 183gb* 365 = 66795gb = 67 TB
	Hadoop conversion: 67 * 3 = 201 TB / 10 TB = 21
[14] 83 gb * 365 = 30295gb = 30 TB
	Hadoop conversion: 30 TB * 3 = 90 TB / 10 TB = 9
[15] 56mb * 365 = 20440 mb = 20gb
	Hadoop conversion: 20* 3 = 60gb
[16] 2387 TB * 365 = 871255 TB
	Hadoop Conversion: 871255 TB * 3 =2613765 TB / 10 TB = 261,377


#### c. Reliability
|                                    | # HD 	| # Failures |
|------------------------------------|-----:	|-----------:|
| Twitter Tweets (Uncompressed)      | 21    	|      .21   | [17]
| Twitter Tweets (Snappy Compressed) | 9    	|      .09   | [17]
| Instagram Photos                   | 1    	|      .01   | [17]
| YouTube Videos                     | 261,377  |  2613.77   | [17]

[17] Using a failure rate of 1% from the 2019 Annualized Hard Drive Failure Rates for the 10TB hard drive
https://www.backblaze.com/blog/hard-drive-stats-for-2019/

#### d. Latency

|                           | One Way Latency      |
|---------------------------|---------------------:|
| Los Angeles to Amsterdam  | 147.424 ms           | [18]
| Low Earth Orbit Satellite | 20 ms                | [19]
| Geostationary Satellite   | 120 ms               | [20]
| Earth to the Moon         | 2560 ms              | [21]
| Earth to Mars             | 4-24 minutes         | [22]

[18] Referenced from https://wondernetwork.com/pings/Los%20Angeles/Amsterdam
[19] Estimated at 40 ms round trip per https://en.wikipedia.org/wiki/Satellite_Internet_access#:~:text=high%2Dlatency%20environments.-,Medium%20and%20Low%20Earth%20Orbits,are%20closer%20to%20the%20ground.&text=The%20O3b%20MEO%20constellation%20orbits,latency%20of%20approximately%20125%20ms.
[20] https://en.wikipedia.org/wiki/Satellite_Internet_access
[21] https://en.wikipedia.org/wiki/Earth%E2%80%93Moon%E2%80%93Earth_communication#:~:text=Propagation%20time%20to%20the%20Moon,milliseconds%20of%20wave%20travel%20time.
[22] https://blogs.esa.int/mex/2012/08/05/time-delay-between-mars-and-earth/#:~:text=Mars%20is%20so%20far%20away,maximum%20of%20around%2024%20minutes.