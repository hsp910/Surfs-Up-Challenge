# Surfs Up Challenge

## Background
This challenge is meant to help us analyze weather data from Oahu, Hawaii to determine how viable a surf shop would be there based on weather patterns throughout the year. We're doing this to let all investors know about any possible slow times/hazards that might come up due to the weather of the area. To this end we are using jupyter notebooks in combination of numpy and pandas to help analyze the weather data which is currently stored in a SQLite file that we need to extract the data from. To extract the data we used SQLAlchemy and extracted the data in the form of tuples, from which we made two lists that were fed into dataframes. The dataframes were then used to generate the final results posted in hte Results section. All temperatures are measured in Fahrenheit in this analysis. 

## Results
### June Results
![June results](https://i.imgur.com/HJZC87U.png)

- Roughly an average temparature of 75 degrees with a standard deviation of 3.1 degrees
- The absolute lowest temparture recorded is 64 degrees and the bottom 25% is under 73 degrees 
- Max of 85 degrees more than likely does not matter as surfing is a pass time that only isn't done when it is too cold, not too hot.

### December Results
![December Results](https://i.imgur.com/Aarkgu8.png)

- Average temparature of roughly 71 degrees with a standard deviation of 3.7 degrees
- Minimum temparature of 56 degrees and the bottom 25% is under 69 degrees
- Maximum temparature of 83 degrees means the highs of December are of similar weather to those of June.

## Summary
Now from these two data sets we can gather a multitude of conclusions. Now as a baseline let's say that surf shops begin to lose their business when temparatures dip below 65 degrees, just as an example of notably colder weather. If we were to follow this logic there is only a few times even in December that are unsuitable for surfing and the surf shop would lose business. This is because even in December the lowest temparature recorded is still 56 degrees. On even colder days in December, using the 25% marker at 69 degrees as the baseline for such days, we can see that the temperature would only be too cold for surfing about 20% of December on the whole. And the temparature never goes too high as well, as even in June the max temparature recorded is only at 85 degrees. Now that we know the temparature will not largely impact the surf shop we have to consider other factors. The most likely factor to impact the surf shop would be percipitation. 

### Additional Queries
- results = session.query(Measurement.date, Measurement.prcp).filter((extract('month',Measurement.date)==6).all()

From this query we would be able to find the percipitation for June to understand how many days, roughly, we would have to worry about being rained out of surfing. As we can follow the same steps used to analyze the temparature we can find the average percipitation expected throughout a month as well as how many days are above a certain amount of percipitation.

- results = session.query(Measurement.date, Measurement.tobs).\
        filter(Measurement.date >= start).\
        filter(Measurement.date <= end).all()
        
By replacing the start and end variables we can use this query to find specific periods of time to check for weather data. We can use this to find weather data for busier periods of time such as from June to August for summer vacationers, or for the months of December and January to help find data pertaining to winter rushes on Hawaii.
        
