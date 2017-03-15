Analyze NYC Noise Complaints with R, MongoDB, and Mongolite
===========================================================

Accompanying code example for my article, [The Noisiest Block in the Neighborhood: Analyzing NYC Data with Mongolite](https://emptysqua.re/blog/analyze-noise-complaints-r-mongodb-mongolite/).

Download records of calls to NYC's complaint line, 3-1-1. 
Draw trend lines for increase in call volume and proportion of noise complaints near my old apartment on Orchard Street. Map noise complaint locations and contours of
complaint density.

![Contour map of noise complaint density near Orchard Street in Manhattan](https://github.com/ajdavis/three-eleven-mongolite-demo/blob/master/noise-contour.png?raw=true)

Install MongoDB
---------------

Install MongoDB (at least 3.2) and run it on your local machine listening on the default port.

Get the data
------------

The data subset required for this demo is included in the repo: ``three_eleven.bson``. The R code ``mongolite-demo.R`` shows how to load that BSON dump into MongoDB with Mongolite.

The original ten-gigabyte CSV file is available from NYC's open data:

[311 Service Requests from 2010 to Present](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9)

Download it, install Python and PyMongo 3.4 or later, and run:

```
cat ~/Downloads/311_Service_Requests_from_2010_to_Present.csv |
  python three-eleven-to-json.py | 
  mongoimport --collection three_eleven
```

Run the demo
------------

The R file ``mongolite-demo.R`` lists its prerequisite libraries in its header comment. It will drop the ``three_eleven`` collection and load the data subset into MongoDB; if you want to use the complete data set comment those lines out.
