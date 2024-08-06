# mobile-data
Python is a great language for doing data analysis, primarily because of the ecosystem of data-centric Python packages. Pandas is one of those packages and makes importing and analyzing data much easier.

Will be  using a real dataset from TRAI to analyze mobile dataspeeds and try to see the average speeds for a particular operator or state in that month. This will also show how easily Pandas could be used on any real world data to derive interesting results.

About Dataset –
Telecom Regulatory Authority of India (TRAI) releases a monthly dataset of the internet speeds it measures through the MySpeed (TRAI) app. This includes speed tests initiated by the user itself or periodic background tests done by the app. Will try to analyze this dataset and see the average speeds for a particular operator or state in that month.

Inspecting the raw structure of data:

st column is of the Network Operator – JIO, Airtel etc.
2nd column is of the Network Technology – 3G or 4G.
3rd column is the Type of Test initiated – upload or download.
4th column is the Speed Measured in Kilobytes per second.
5th column is the Signal Strength during the measurement.
6th column is the Local Service Area(LSA), or the circle where the test was done – Delhi, Orissa etc.

Packages used:
Pandas – a popular data analysis toolkit. Very powerful for crunching large sets of data.
Numpy – provides fast and efficient operations on arrays of homogeneous data. 
Matplotlib – is a plotting library. We will use its bar plotting function to make bar graphs.

