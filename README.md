##R Cheat Sheet

Turn off scientific notation except for very large numbers

	options(scipen=20)

[source](http://stackoverflow.com/questions/5352099/how-to-disable-scientific-notation-in-r)

###Data transformation

Make a new date column from a column with datetime data stored as a string

	data$date <- as.POSIXct(data$month, format='%m/%d/%Y')

[source](http://stackoverflow.com/questions/10128529/creating-a-new-column-for-date-info-with-specific-date-format)

Group and sum a column into a new dataframe
					
	# Assuming a following data frame structured as data[store, revenue, date]

	new <- aggregate(data$revenue, by=list(date=data$date), FUN=sum)

[source](http://stackoverflow.com/questions/1660124/how-to-group-columns-by-sum-in-r)

###Graphing

Make a timeseries line chart by group
	
	# Assuming a following data frame structured as data[store, revenue, date]
	# and library("ggplot2")

	qplot(date, revenue, data=data, group=store, geom="line")

[source](http://docs.ggplot2.org/current/geom_line.html)

Turn off axes, and add your own customized verions

	plot(data, axes=FALSE)

	# See ?axes for options
	axes(...)

[source](http://stackoverflow.com/questions/11019870/changing-y-axis-tick-labels-from-standard-form-to-the-full-number)

###Mapping

Amanda Cox's [R Training](https://gist.github.com/ashaw/94072018b242cf0605dd) from #NICAR13