

```python
import csv
import pandas as pd
import random
import numpy as np
import string
```


```python
city = "./raw_data/city_data.csv"
ride = "./raw_data/ride_data.csv"
```


```python
city_df = pd.read_csv(city)
ride_df = pd.read_csv(ride)

city_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>driver_count</th>
      <th>type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nguyenbury</td>
      <td>8</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>2</th>
      <td>East Douglas</td>
      <td>12</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>3</th>
      <td>West Dawnfurt</td>
      <td>34</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rodriguezburgh</td>
      <td>52</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>5</th>
      <td>South Josephville</td>
      <td>4</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>6</th>
      <td>West Sydneyhaven</td>
      <td>70</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Travisville</td>
      <td>37</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Torresshire</td>
      <td>70</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Lisaville</td>
      <td>66</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Mooreview</td>
      <td>34</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Smithhaven</td>
      <td>67</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Carrollfort</td>
      <td>55</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Port Josephfurt</td>
      <td>28</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Lake Jeffreyland</td>
      <td>15</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>15</th>
      <td>South Louis</td>
      <td>12</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>16</th>
      <td>West Peter</td>
      <td>61</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Kimberlychester</td>
      <td>13</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Alyssaberg</td>
      <td>67</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Sarabury</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Yolandafurt</td>
      <td>7</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Edwardsbury</td>
      <td>11</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>22</th>
      <td>New Andreamouth</td>
      <td>42</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>23</th>
      <td>New David</td>
      <td>31</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Arnoldview</td>
      <td>41</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Williamshire</td>
      <td>70</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Lisatown</td>
      <td>47</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>27</th>
      <td>New Aaron</td>
      <td>60</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Swansonbury</td>
      <td>64</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Fosterside</td>
      <td>69</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>96</th>
      <td>New Lynn</td>
      <td>20</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>97</th>
      <td>Port Jose</td>
      <td>11</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>98</th>
      <td>Johnland</td>
      <td>13</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>99</th>
      <td>West Tony</td>
      <td>17</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>100</th>
      <td>Port James</td>
      <td>3</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>101</th>
      <td>Campbellport</td>
      <td>26</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>102</th>
      <td>Port Guytown</td>
      <td>26</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>103</th>
      <td>Webstertown</td>
      <td>26</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>104</th>
      <td>Clarkstad</td>
      <td>21</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>105</th>
      <td>North Tracyfort</td>
      <td>18</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>106</th>
      <td>Martinmouth</td>
      <td>5</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>107</th>
      <td>New Jessicamouth</td>
      <td>22</td>
      <td>Suburban</td>
    </tr>
    <tr>
      <th>108</th>
      <td>South Elizabethmouth</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>109</th>
      <td>East Troybury</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>110</th>
      <td>Kinghaven</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>111</th>
      <td>New Johnbury</td>
      <td>6</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>112</th>
      <td>Erikport</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>113</th>
      <td>Jacksonfort</td>
      <td>6</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>114</th>
      <td>Shelbyhaven</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>115</th>
      <td>Matthewside</td>
      <td>4</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>116</th>
      <td>Kennethburgh</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>117</th>
      <td>South Joseph</td>
      <td>3</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>118</th>
      <td>Manuelchester</td>
      <td>7</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Stevensport</td>
      <td>6</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>120</th>
      <td>North Whitney</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>121</th>
      <td>East Stephen</td>
      <td>6</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>122</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>123</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>124</th>
      <td>Horneland</td>
      <td>8</td>
      <td>Rural</td>
    </tr>
    <tr>
      <th>125</th>
      <td>West Kevintown</td>
      <td>5</td>
      <td>Rural</td>
    </tr>
  </tbody>
</table>
<p>126 rows × 3 columns</p>
</div>




```python
ride_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>date</th>
      <th>fare</th>
      <th>ride_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sarabury</td>
      <td>2016-01-16 13:49:27</td>
      <td>38.35</td>
      <td>5403689035038</td>
    </tr>
    <tr>
      <th>1</th>
      <td>South Roy</td>
      <td>2016-01-02 18:42:34</td>
      <td>17.49</td>
      <td>4036272335942</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Wiseborough</td>
      <td>2016-01-21 17:35:29</td>
      <td>44.18</td>
      <td>3645042422587</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spencertown</td>
      <td>2016-07-31 14:53:22</td>
      <td>6.87</td>
      <td>2242596575892</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Nguyenbury</td>
      <td>2016-07-09 04:42:44</td>
      <td>6.28</td>
      <td>1543057793673</td>
    </tr>
    <tr>
      <th>5</th>
      <td>New Jeffrey</td>
      <td>2016-02-22 18:36:25</td>
      <td>36.01</td>
      <td>9757888452346</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Port Johnstad</td>
      <td>2016-06-07 02:39:58</td>
      <td>17.15</td>
      <td>4352278259335</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Jacobfort</td>
      <td>2016-09-20 20:58:37</td>
      <td>22.98</td>
      <td>1500221409082</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Travisville</td>
      <td>2016-01-15 17:32:02</td>
      <td>27.39</td>
      <td>850152768361</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Sandymouth</td>
      <td>2016-11-16 07:27:00</td>
      <td>21.61</td>
      <td>2389035050524</td>
    </tr>
    <tr>
      <th>10</th>
      <td>New Andreamouth</td>
      <td>2016-04-11 07:20:48</td>
      <td>7.72</td>
      <td>9992929847990</td>
    </tr>
    <tr>
      <th>11</th>
      <td>New Christine</td>
      <td>2016-09-13 15:06:42</td>
      <td>24.89</td>
      <td>7918411468537</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Stewartview</td>
      <td>2016-03-29 05:15:56</td>
      <td>23.88</td>
      <td>6778235889588</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Rodriguezburgh</td>
      <td>2016-09-05 05:20:39</td>
      <td>4.54</td>
      <td>9650770953139</td>
    </tr>
    <tr>
      <th>14</th>
      <td>West Sydneyhaven</td>
      <td>2016-08-02 21:18:44</td>
      <td>12.87</td>
      <td>7994760397230</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Swansonbury</td>
      <td>2016-07-11 18:42:11</td>
      <td>39.30</td>
      <td>744481862626</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Lisatown</td>
      <td>2016-07-05 18:09:14</td>
      <td>5.82</td>
      <td>6370359473201</td>
    </tr>
    <tr>
      <th>17</th>
      <td>East Erin</td>
      <td>2016-11-03 01:03:05</td>
      <td>7.51</td>
      <td>4744239092530</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Port Martinberg</td>
      <td>2016-01-06 17:11:30</td>
      <td>8.66</td>
      <td>7298562820881</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Wiseborough</td>
      <td>2016-09-12 18:43:41</td>
      <td>26.83</td>
      <td>9304728540000</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Edwardsbury</td>
      <td>2016-02-27 03:55:54</td>
      <td>20.17</td>
      <td>8514523868075</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Jacobfort</td>
      <td>2016-06-12 17:01:29</td>
      <td>34.47</td>
      <td>4135673527977</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Pamelahaven</td>
      <td>2016-03-26 12:56:57</td>
      <td>36.43</td>
      <td>3015329826849</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Fosterside</td>
      <td>2016-08-12 11:52:41</td>
      <td>28.08</td>
      <td>133077693483</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Jacobfort</td>
      <td>2016-09-17 12:38:58</td>
      <td>38.25</td>
      <td>2182376146051</td>
    </tr>
    <tr>
      <th>25</th>
      <td>West Sydneyhaven</td>
      <td>2016-08-23 14:49:59</td>
      <td>36.12</td>
      <td>5885997568611</td>
    </tr>
    <tr>
      <th>26</th>
      <td>West Alexis</td>
      <td>2016-01-16 00:33:02</td>
      <td>26.62</td>
      <td>1574788996743</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Carrollfort</td>
      <td>2016-06-24 20:11:11</td>
      <td>6.45</td>
      <td>1092683495142</td>
    </tr>
    <tr>
      <th>28</th>
      <td>New David</td>
      <td>2016-01-12 20:48:43</td>
      <td>38.68</td>
      <td>5229089333754</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Stewartview</td>
      <td>2016-10-15 05:26:40</td>
      <td>11.74</td>
      <td>8402784599831</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2345</th>
      <td>West Kevintown</td>
      <td>2016-06-15 19:53:16</td>
      <td>13.50</td>
      <td>9577921579881</td>
    </tr>
    <tr>
      <th>2346</th>
      <td>Matthewside</td>
      <td>2016-02-23 00:43:51</td>
      <td>40.84</td>
      <td>8665248512368</td>
    </tr>
    <tr>
      <th>2347</th>
      <td>Erikport</td>
      <td>2016-11-26 04:39:52</td>
      <td>44.21</td>
      <td>9598643212986</td>
    </tr>
    <tr>
      <th>2348</th>
      <td>Kinghaven</td>
      <td>2016-07-23 08:23:50</td>
      <td>46.08</td>
      <td>8440329717166</td>
    </tr>
    <tr>
      <th>2349</th>
      <td>Hernandezshire</td>
      <td>2016-02-24 17:30:44</td>
      <td>44.68</td>
      <td>6389115653382</td>
    </tr>
    <tr>
      <th>2350</th>
      <td>Kennethburgh</td>
      <td>2016-01-01 04:31:43</td>
      <td>33.53</td>
      <td>5149088250183</td>
    </tr>
    <tr>
      <th>2351</th>
      <td>Stevensport</td>
      <td>2016-02-22 02:45:07</td>
      <td>19.91</td>
      <td>808097865942</td>
    </tr>
    <tr>
      <th>2352</th>
      <td>South Elizabethmouth</td>
      <td>2016-11-23 07:47:18</td>
      <td>46.39</td>
      <td>1939838068038</td>
    </tr>
    <tr>
      <th>2353</th>
      <td>East Stephen</td>
      <td>2016-07-30 21:25:01</td>
      <td>35.39</td>
      <td>1107870956099</td>
    </tr>
    <tr>
      <th>2354</th>
      <td>Jacksonfort</td>
      <td>2016-10-01 13:41:00</td>
      <td>34.17</td>
      <td>7750597960630</td>
    </tr>
    <tr>
      <th>2355</th>
      <td>Kennethburgh</td>
      <td>2016-04-30 20:44:27</td>
      <td>23.58</td>
      <td>4524301143267</td>
    </tr>
    <tr>
      <th>2356</th>
      <td>Horneland</td>
      <td>2016-03-25 02:05:42</td>
      <td>20.04</td>
      <td>5729327140644</td>
    </tr>
    <tr>
      <th>2357</th>
      <td>Shelbyhaven</td>
      <td>2016-01-25 01:39:16</td>
      <td>59.43</td>
      <td>8088329954312</td>
    </tr>
    <tr>
      <th>2358</th>
      <td>Erikport</td>
      <td>2016-08-03 21:19:11</td>
      <td>47.67</td>
      <td>9201708664049</td>
    </tr>
    <tr>
      <th>2359</th>
      <td>Kennethburgh</td>
      <td>2016-11-19 06:59:31</td>
      <td>18.37</td>
      <td>5897895798960</td>
    </tr>
    <tr>
      <th>2360</th>
      <td>Jacksonfort</td>
      <td>2016-10-20 16:42:54</td>
      <td>37.75</td>
      <td>4356781814784</td>
    </tr>
    <tr>
      <th>2361</th>
      <td>South Joseph</td>
      <td>2016-10-15 03:53:06</td>
      <td>32.50</td>
      <td>2758038144583</td>
    </tr>
    <tr>
      <th>2362</th>
      <td>Matthewside</td>
      <td>2016-05-18 02:00:30</td>
      <td>48.67</td>
      <td>2049161404256</td>
    </tr>
    <tr>
      <th>2363</th>
      <td>Matthewside</td>
      <td>2016-08-08 14:02:35</td>
      <td>24.97</td>
      <td>2872494724827</td>
    </tr>
    <tr>
      <th>2364</th>
      <td>South Joseph</td>
      <td>2016-10-28 09:52:15</td>
      <td>25.34</td>
      <td>6706101910500</td>
    </tr>
    <tr>
      <th>2365</th>
      <td>South Elizabethmouth</td>
      <td>2016-07-19 09:35:59</td>
      <td>31.09</td>
      <td>2959749591417</td>
    </tr>
    <tr>
      <th>2366</th>
      <td>North Whitney</td>
      <td>2016-11-11 16:24:16</td>
      <td>22.99</td>
      <td>3454326063039</td>
    </tr>
    <tr>
      <th>2367</th>
      <td>New Johnbury</td>
      <td>2016-08-29 02:36:06</td>
      <td>18.83</td>
      <td>7368222134792</td>
    </tr>
    <tr>
      <th>2368</th>
      <td>East Leslie</td>
      <td>2016-06-22 07:45:30</td>
      <td>34.54</td>
      <td>684950063164</td>
    </tr>
    <tr>
      <th>2369</th>
      <td>Kennethburgh</td>
      <td>2016-06-07 11:43:43</td>
      <td>56.02</td>
      <td>311733202150</td>
    </tr>
    <tr>
      <th>2370</th>
      <td>West Kevintown</td>
      <td>2016-02-10 00:50:04</td>
      <td>34.69</td>
      <td>9595491362610</td>
    </tr>
    <tr>
      <th>2371</th>
      <td>East Troybury</td>
      <td>2016-03-14 01:55:32</td>
      <td>38.80</td>
      <td>9205811495606</td>
    </tr>
    <tr>
      <th>2372</th>
      <td>North Whitney</td>
      <td>2016-01-26 01:06:41</td>
      <td>34.92</td>
      <td>4165974278063</td>
    </tr>
    <tr>
      <th>2373</th>
      <td>South Joseph</td>
      <td>2016-09-28 07:30:55</td>
      <td>12.55</td>
      <td>4336212615821</td>
    </tr>
    <tr>
      <th>2374</th>
      <td>South Elizabethmouth</td>
      <td>2016-04-21 10:20:09</td>
      <td>16.50</td>
      <td>5702608059064</td>
    </tr>
  </tbody>
</table>
<p>2375 rows × 4 columns</p>
</div>




```python
ride_df['city'].value_counts()

#125
```




    Port Johnstad           34
    Swansonbury             34
    Port James              32
    South Louis             32
    Arnoldview              31
    Williamshire            31
    West Peter              31
    Jacobfort               31
    Alvarezhaven            31
    Stewartview             30
    West Brandy             30
    Carrollfort             29
    West Dawnfurt           29
    West Oscar              29
    New David               28
    Kelseyland              28
    East Erin               28
    New Andreamouth         28
    Lisaville               28
    Sandymouth              27
    Port Samantha           27
    Edwardsbury             27
    Smithhaven              27
    Sarabury                27
    Kimberlychester         27
    Alyssaberg              26
    Spencertown             26
    Nguyenbury              26
    Torresshire             26
    New Jeffrey             25
                            ..
    Clarkstad               12
    Jasonfort               12
    West Evan               12
    South Joseph            12
    New Michelleberg        11
    East Leslie             11
    Williamchester          11
    Conwaymouth             11
    North Tracyfort         10
    Floresberg              10
    North Whitney           10
    Kennethburgh            10
    Carrollbury             10
    East Stephen            10
    North Tara               9
    Martinmouth              9
    Hernandezshire           9
    Anitamouth               9
    Erikport                 8
    East Troybury            7
    West Kevintown           7
    Shelbyhaven              6
    Kinghaven                6
    Jacksonfort              6
    Stevensport              5
    South Elizabethmouth     5
    New Johnbury             4
    Horneland                4
    Matthewside              4
    Manuelchester            1
    Name: city, Length: 125, dtype: int64




```python
merge_table = pd.merge(city_df, ride_df, on="city", how="outer")

merge_table

```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>driver_count</th>
      <th>type</th>
      <th>date</th>
      <th>fare</th>
      <th>ride_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-08-19 04:27:52</td>
      <td>5.51</td>
      <td>6246006544795</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-04-17 06:59:50</td>
      <td>5.54</td>
      <td>7466473222333</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-05-04 15:06:07</td>
      <td>30.54</td>
      <td>2140501382736</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-01-25 20:44:56</td>
      <td>12.08</td>
      <td>1896987891309</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-08-09 18:19:47</td>
      <td>17.91</td>
      <td>8784212854829</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-10-24 15:15:46</td>
      <td>33.56</td>
      <td>4797969661996</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-06-06 13:54:23</td>
      <td>20.81</td>
      <td>9811478565448</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-08-10 07:02:40</td>
      <td>44.53</td>
      <td>1563171128434</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-07-05 17:37:13</td>
      <td>29.02</td>
      <td>6897992353955</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-04-25 02:18:31</td>
      <td>20.05</td>
      <td>1148374505062</td>
    </tr>
    <tr>
      <th>10</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-01-25 08:47:09</td>
      <td>9.29</td>
      <td>213692794373</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-11-10 01:57:14</td>
      <td>20.58</td>
      <td>3395682132130</td>
    </tr>
    <tr>
      <th>12</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-08-15 11:55:02</td>
      <td>27.45</td>
      <td>8456148871668</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-08-01 10:51:49</td>
      <td>33.51</td>
      <td>6610565660737</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-04-13 12:07:08</td>
      <td>6.56</td>
      <td>8101498434215</td>
    </tr>
    <tr>
      <th>15</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-01-12 22:51:21</td>
      <td>20.19</td>
      <td>3054122642867</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-05-31 01:05:31</td>
      <td>35.22</td>
      <td>5946467060438</td>
    </tr>
    <tr>
      <th>17</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-07-13 16:53:07</td>
      <td>10.31</td>
      <td>2180910323678</td>
    </tr>
    <tr>
      <th>18</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-01-07 07:15:41</td>
      <td>11.45</td>
      <td>600800386573</td>
    </tr>
    <tr>
      <th>19</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-04-09 13:17:27</td>
      <td>27.85</td>
      <td>5748868894243</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-06-30 01:59:04</td>
      <td>8.27</td>
      <td>4384089549855</td>
    </tr>
    <tr>
      <th>21</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-04-20 05:36:59</td>
      <td>31.67</td>
      <td>2865704421982</td>
    </tr>
    <tr>
      <th>22</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-05-02 05:55:28</td>
      <td>40.92</td>
      <td>2769007541388</td>
    </tr>
    <tr>
      <th>23</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-06-22 06:54:57</td>
      <td>12.58</td>
      <td>6629798205387</td>
    </tr>
    <tr>
      <th>24</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-06-18 06:03:03</td>
      <td>16.77</td>
      <td>7223504701591</td>
    </tr>
    <tr>
      <th>25</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-01-09 20:28:56</td>
      <td>27.21</td>
      <td>831362906446</td>
    </tr>
    <tr>
      <th>26</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-07-22 19:28:21</td>
      <td>35.71</td>
      <td>1234880130185</td>
    </tr>
    <tr>
      <th>27</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
      <td>2016-11-26 02:34:57</td>
      <td>15.49</td>
      <td>5187807155760</td>
    </tr>
    <tr>
      <th>28</th>
      <td>Nguyenbury</td>
      <td>8</td>
      <td>Urban</td>
      <td>2016-07-09 04:42:44</td>
      <td>6.28</td>
      <td>1543057793673</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Nguyenbury</td>
      <td>8</td>
      <td>Urban</td>
      <td>2016-11-08 19:22:04</td>
      <td>19.49</td>
      <td>1702803950740</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2377</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-04-13 04:30:56</td>
      <td>40.47</td>
      <td>7075058703398</td>
    </tr>
    <tr>
      <th>2378</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-04-26 02:34:30</td>
      <td>45.80</td>
      <td>9402873395510</td>
    </tr>
    <tr>
      <th>2379</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-04-05 18:53:16</td>
      <td>44.78</td>
      <td>6113138249150</td>
    </tr>
    <tr>
      <th>2380</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-11-13 10:21:10</td>
      <td>15.71</td>
      <td>7275986542384</td>
    </tr>
    <tr>
      <th>2381</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-03-06 06:10:40</td>
      <td>51.32</td>
      <td>6841691147797</td>
    </tr>
    <tr>
      <th>2382</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-03-04 10:18:03</td>
      <td>13.43</td>
      <td>8814831098684</td>
    </tr>
    <tr>
      <th>2383</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-11-28 09:09:15</td>
      <td>37.76</td>
      <td>804829686137</td>
    </tr>
    <tr>
      <th>2384</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-09-08 19:19:38</td>
      <td>30.59</td>
      <td>8211833105097</td>
    </tr>
    <tr>
      <th>2385</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-03-02 22:09:34</td>
      <td>36.61</td>
      <td>5500269118478</td>
    </tr>
    <tr>
      <th>2386</th>
      <td>East Leslie</td>
      <td>9</td>
      <td>Rural</td>
      <td>2016-06-22 07:45:30</td>
      <td>34.54</td>
      <td>684950063164</td>
    </tr>
    <tr>
      <th>2387</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-02-20 08:17:32</td>
      <td>58.95</td>
      <td>3176534714830</td>
    </tr>
    <tr>
      <th>2388</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-06-26 20:11:50</td>
      <td>28.78</td>
      <td>6382848462030</td>
    </tr>
    <tr>
      <th>2389</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-01-24 00:21:35</td>
      <td>30.32</td>
      <td>7342649945759</td>
    </tr>
    <tr>
      <th>2390</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-03-05 10:40:16</td>
      <td>23.35</td>
      <td>7443355895137</td>
    </tr>
    <tr>
      <th>2391</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-04-11 04:44:50</td>
      <td>10.41</td>
      <td>9823290002445</td>
    </tr>
    <tr>
      <th>2392</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-06-26 11:16:28</td>
      <td>26.29</td>
      <td>304182959218</td>
    </tr>
    <tr>
      <th>2393</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-11-25 20:34:14</td>
      <td>38.45</td>
      <td>2898512024847</td>
    </tr>
    <tr>
      <th>2394</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-11-20 17:32:37</td>
      <td>26.79</td>
      <td>3095402154397</td>
    </tr>
    <tr>
      <th>2395</th>
      <td>Hernandezshire</td>
      <td>10</td>
      <td>Rural</td>
      <td>2016-02-24 17:30:44</td>
      <td>44.68</td>
      <td>6389115653382</td>
    </tr>
    <tr>
      <th>2396</th>
      <td>Horneland</td>
      <td>8</td>
      <td>Rural</td>
      <td>2016-07-19 10:07:33</td>
      <td>12.63</td>
      <td>8214498891817</td>
    </tr>
    <tr>
      <th>2397</th>
      <td>Horneland</td>
      <td>8</td>
      <td>Rural</td>
      <td>2016-03-22 21:22:20</td>
      <td>31.53</td>
      <td>1797785685674</td>
    </tr>
    <tr>
      <th>2398</th>
      <td>Horneland</td>
      <td>8</td>
      <td>Rural</td>
      <td>2016-01-26 09:38:17</td>
      <td>21.73</td>
      <td>5665544449606</td>
    </tr>
    <tr>
      <th>2399</th>
      <td>Horneland</td>
      <td>8</td>
      <td>Rural</td>
      <td>2016-03-25 02:05:42</td>
      <td>20.04</td>
      <td>5729327140644</td>
    </tr>
    <tr>
      <th>2400</th>
      <td>West Kevintown</td>
      <td>5</td>
      <td>Rural</td>
      <td>2016-11-27 20:12:58</td>
      <td>12.92</td>
      <td>6460741616450</td>
    </tr>
    <tr>
      <th>2401</th>
      <td>West Kevintown</td>
      <td>5</td>
      <td>Rural</td>
      <td>2016-02-19 01:42:58</td>
      <td>11.15</td>
      <td>8622534016726</td>
    </tr>
    <tr>
      <th>2402</th>
      <td>West Kevintown</td>
      <td>5</td>
      <td>Rural</td>
      <td>2016-03-11 09:03:43</td>
      <td>42.13</td>
      <td>4568909568268</td>
    </tr>
    <tr>
      <th>2403</th>
      <td>West Kevintown</td>
      <td>5</td>
      <td>Rural</td>
      <td>2016-06-25 08:04:12</td>
      <td>24.53</td>
      <td>8188407925972</td>
    </tr>
    <tr>
      <th>2404</th>
      <td>West Kevintown</td>
      <td>5</td>
      <td>Rural</td>
      <td>2016-07-24 13:41:23</td>
      <td>11.78</td>
      <td>2001192693573</td>
    </tr>
    <tr>
      <th>2405</th>
      <td>West Kevintown</td>
      <td>5</td>
      <td>Rural</td>
      <td>2016-06-15 19:53:16</td>
      <td>13.50</td>
      <td>9577921579881</td>
    </tr>
    <tr>
      <th>2406</th>
      <td>West Kevintown</td>
      <td>5</td>
      <td>Rural</td>
      <td>2016-02-10 00:50:04</td>
      <td>34.69</td>
      <td>9595491362610</td>
    </tr>
  </tbody>
</table>
<p>2407 rows × 6 columns</p>
</div>




```python
num_rides = merge_table['city'].value_counts()
```


```python
grp = merge_table.groupby(['city'])

#grp = grp.sum()

grp.count()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>driver_count</th>
      <th>type</th>
      <th>date</th>
      <th>fare</th>
      <th>ride_id</th>
    </tr>
    <tr>
      <th>city</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Alvarezhaven</th>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
    </tr>
    <tr>
      <th>Alyssaberg</th>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
    </tr>
    <tr>
      <th>Anitamouth</th>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
    </tr>
    <tr>
      <th>Antoniomouth</th>
      <td>22</td>
      <td>22</td>
      <td>22</td>
      <td>22</td>
      <td>22</td>
    </tr>
    <tr>
      <th>Aprilchester</th>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
    </tr>
    <tr>
      <th>Arnoldview</th>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
    </tr>
    <tr>
      <th>Campbellport</th>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Carrollbury</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Carrollfort</th>
      <td>29</td>
      <td>29</td>
      <td>29</td>
      <td>29</td>
      <td>29</td>
    </tr>
    <tr>
      <th>Clarkstad</th>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>Conwaymouth</th>
      <td>11</td>
      <td>11</td>
      <td>11</td>
      <td>11</td>
      <td>11</td>
    </tr>
    <tr>
      <th>Davidtown</th>
      <td>21</td>
      <td>21</td>
      <td>21</td>
      <td>21</td>
      <td>21</td>
    </tr>
    <tr>
      <th>Davistown</th>
      <td>25</td>
      <td>25</td>
      <td>25</td>
      <td>25</td>
      <td>25</td>
    </tr>
    <tr>
      <th>East Cherylfurt</th>
      <td>13</td>
      <td>13</td>
      <td>13</td>
      <td>13</td>
      <td>13</td>
    </tr>
    <tr>
      <th>East Douglas</th>
      <td>22</td>
      <td>22</td>
      <td>22</td>
      <td>22</td>
      <td>22</td>
    </tr>
    <tr>
      <th>East Erin</th>
      <td>28</td>
      <td>28</td>
      <td>28</td>
      <td>28</td>
      <td>28</td>
    </tr>
    <tr>
      <th>East Jenniferchester</th>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
    </tr>
    <tr>
      <th>East Leslie</th>
      <td>11</td>
      <td>11</td>
      <td>11</td>
      <td>11</td>
      <td>11</td>
    </tr>
    <tr>
      <th>East Stephen</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>East Troybury</th>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
    </tr>
    <tr>
      <th>Edwardsbury</th>
      <td>27</td>
      <td>27</td>
      <td>27</td>
      <td>27</td>
      <td>27</td>
    </tr>
    <tr>
      <th>Erikport</th>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
    </tr>
    <tr>
      <th>Eriktown</th>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
    </tr>
    <tr>
      <th>Floresberg</th>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <th>Fosterside</th>
      <td>24</td>
      <td>24</td>
      <td>24</td>
      <td>24</td>
      <td>24</td>
    </tr>
    <tr>
      <th>Hernandezshire</th>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
    </tr>
    <tr>
      <th>Horneland</th>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
    </tr>
    <tr>
      <th>Jacksonfort</th>
      <td>6</td>
      <td>6</td>
      <td>6</td>
      <td>6</td>
      <td>6</td>
    </tr>
    <tr>
      <th>Jacobfort</th>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
    </tr>
    <tr>
      <th>Jasonfort</th>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>South Roy</th>
      <td>22</td>
      <td>22</td>
      <td>22</td>
      <td>22</td>
      <td>22</td>
    </tr>
    <tr>
      <th>South Shannonborough</th>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Spencertown</th>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
    </tr>
    <tr>
      <th>Stevensport</th>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
    </tr>
    <tr>
      <th>Stewartview</th>
      <td>30</td>
      <td>30</td>
      <td>30</td>
      <td>30</td>
      <td>30</td>
    </tr>
    <tr>
      <th>Swansonbury</th>
      <td>34</td>
      <td>34</td>
      <td>34</td>
      <td>34</td>
      <td>34</td>
    </tr>
    <tr>
      <th>Thomastown</th>
      <td>24</td>
      <td>24</td>
      <td>24</td>
      <td>24</td>
      <td>24</td>
    </tr>
    <tr>
      <th>Tiffanyton</th>
      <td>13</td>
      <td>13</td>
      <td>13</td>
      <td>13</td>
      <td>13</td>
    </tr>
    <tr>
      <th>Torresshire</th>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
      <td>26</td>
    </tr>
    <tr>
      <th>Travisville</th>
      <td>23</td>
      <td>23</td>
      <td>23</td>
      <td>23</td>
      <td>23</td>
    </tr>
    <tr>
      <th>Vickimouth</th>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
      <td>15</td>
    </tr>
    <tr>
      <th>Webstertown</th>
      <td>16</td>
      <td>16</td>
      <td>16</td>
      <td>16</td>
      <td>16</td>
    </tr>
    <tr>
      <th>West Alexis</th>
      <td>20</td>
      <td>20</td>
      <td>20</td>
      <td>20</td>
      <td>20</td>
    </tr>
    <tr>
      <th>West Brandy</th>
      <td>30</td>
      <td>30</td>
      <td>30</td>
      <td>30</td>
      <td>30</td>
    </tr>
    <tr>
      <th>West Brittanyton</th>
      <td>24</td>
      <td>24</td>
      <td>24</td>
      <td>24</td>
      <td>24</td>
    </tr>
    <tr>
      <th>West Dawnfurt</th>
      <td>29</td>
      <td>29</td>
      <td>29</td>
      <td>29</td>
      <td>29</td>
    </tr>
    <tr>
      <th>West Evan</th>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>West Jefferyfurt</th>
      <td>21</td>
      <td>21</td>
      <td>21</td>
      <td>21</td>
      <td>21</td>
    </tr>
    <tr>
      <th>West Kevintown</th>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
    </tr>
    <tr>
      <th>West Oscar</th>
      <td>29</td>
      <td>29</td>
      <td>29</td>
      <td>29</td>
      <td>29</td>
    </tr>
    <tr>
      <th>West Pamelaborough</th>
      <td>14</td>
      <td>14</td>
      <td>14</td>
      <td>14</td>
      <td>14</td>
    </tr>
    <tr>
      <th>West Paulport</th>
      <td>17</td>
      <td>17</td>
      <td>17</td>
      <td>17</td>
      <td>17</td>
    </tr>
    <tr>
      <th>West Peter</th>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
    </tr>
    <tr>
      <th>West Sydneyhaven</th>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
      <td>18</td>
    </tr>
    <tr>
      <th>West Tony</th>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
    </tr>
    <tr>
      <th>Williamchester</th>
      <td>11</td>
      <td>11</td>
      <td>11</td>
      <td>11</td>
      <td>11</td>
    </tr>
    <tr>
      <th>Williamshire</th>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
      <td>31</td>
    </tr>
    <tr>
      <th>Wiseborough</th>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
      <td>19</td>
    </tr>
    <tr>
      <th>Yolandafurt</th>
      <td>20</td>
      <td>20</td>
      <td>20</td>
      <td>20</td>
      <td>20</td>
    </tr>
    <tr>
      <th>Zimmermanmouth</th>
      <td>24</td>
      <td>24</td>
      <td>24</td>
      <td>24</td>
      <td>24</td>
    </tr>
  </tbody>
</table>
<p>125 rows × 5 columns</p>
</div>




```python
df = pd.merge(grp, merge_table, on="city", how="right")

df
```


    ---------------------------------------------------------------------------

    KeyError                                  Traceback (most recent call last)

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\indexes\base.py in get_loc(self, key, method, tolerance)
       2524             try:
    -> 2525                 return self._engine.get_loc(key)
       2526             except KeyError:
    

    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()
    

    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()
    

    KeyError: 'city'

    
    During handling of the above exception, another exception occurred:
    

    KeyError                                  Traceback (most recent call last)

    <ipython-input-40-7df4a8508b48> in <module>()
    ----> 1 df = pd.merge(grp, merge_table, on="city", how="right")
          2 
          3 df
    

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\reshape\merge.py in merge(left, right, how, on, left_on, right_on, left_index, right_index, sort, suffixes, copy, indicator, validate)
         55                          right_index=right_index, sort=sort, suffixes=suffixes,
         56                          copy=copy, indicator=indicator,
    ---> 57                          validate=validate)
         58     return op.get_result()
         59 
    

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\reshape\merge.py in __init__(self, left, right, how, on, left_on, right_on, axis, left_index, right_index, sort, suffixes, copy, indicator, validate)
        563         (self.left_join_keys,
        564          self.right_join_keys,
    --> 565          self.join_names) = self._get_merge_keys()
        566 
        567         # validate the merge keys dtypes. We may need to coerce
    

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\reshape\merge.py in _get_merge_keys(self)
        835                         right_keys.append(rk)
        836                     if lk is not None:
    --> 837                         left_keys.append(left[lk]._values)
        838                         join_names.append(lk)
        839                     else:
    

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\frame.py in __getitem__(self, key)
       2137             return self._getitem_multilevel(key)
       2138         else:
    -> 2139             return self._getitem_column(key)
       2140 
       2141     def _getitem_column(self, key):
    

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\frame.py in _getitem_column(self, key)
       2144         # get column
       2145         if self.columns.is_unique:
    -> 2146             return self._get_item_cache(key)
       2147 
       2148         # duplicate columns & possible reduce dimensionality
    

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\generic.py in _get_item_cache(self, item)
       1840         res = cache.get(item)
       1841         if res is None:
    -> 1842             values = self._data.get(item)
       1843             res = self._box_item_values(item, values)
       1844             cache[item] = res
    

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\internals.py in get(self, item, fastpath)
       3841 
       3842             if not isna(item):
    -> 3843                 loc = self.items.get_loc(item)
       3844             else:
       3845                 indexer = np.arange(len(self.items))[isna(self.items)]
    

    ~\Anaconda3\envs\PythonData\lib\site-packages\pandas\core\indexes\base.py in get_loc(self, key, method, tolerance)
       2525                 return self._engine.get_loc(key)
       2526             except KeyError:
    -> 2527                 return self._engine.get_loc(self._maybe_cast_indexer(key))
       2528 
       2529         indexer = self.get_indexer([key], method=method, tolerance=tolerance)
    

    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas/_libs/index.pyx in pandas._libs.index.IndexEngine.get_loc()
    

    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()
    

    pandas/_libs/hashtable_class_helper.pxi in pandas._libs.hashtable.PyObjectHashTable.get_item()
    

    KeyError: 'city'

