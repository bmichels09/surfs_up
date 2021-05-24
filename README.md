# Oahu Temperature Analysis

## Overview of Analysis
The purpose of this analysis is to compare temperatures in June and December to see if the surf and ice cream shop will be viable year round.

## Results
- The mean (and median) temperature for June is 75°.
- The mean (and median) temperature for December is 71°.
- The minimum temperature for June is 64°.
- The minimum temperature for December is 56°.
- December temperatures have a slightly higher standard deviation than June temperatures.

## Summary
December temperatures are only a few degrees lower than June temperatures, so the number of customers shouldn't vary much throughout the year.

We could check the precipitation in June and December using the following queries:
    session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 6)
	session.query(Measurement.date, Measurement.prcp).filter(extract('month', Measurement.date) == 12)
	
We could also break down the data further by looking at the mean temperature at each station, using these queries:
    session.query(Measurement.station, func.avg(Measurement.tobs)).filter(extract('month', Measurement.date) == 6).group_by(Measurement.station)
	session.query(Measurement.station, func.avg(Measurement.tobs)).filter(extract('month', Measurement.date) == 12).group_by(Measurement.station)
