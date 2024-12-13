# Divorce24
Analysis code and data for Abraham, Sheldon, and Firth 2024 - Timing and social consequences of divorce in wild great tits: a phenomenological approach

---Study Summary---
                             
Three years of wild great tit social data were used to analyse how winter (non-breeding) behaviour differs between breeding pairs which do and do not remain together for consecutive springs. This analysis was conducted at two different spatiotemporal scales: number of shared flocking events at supplementary  feeders, and how often pairs came to the feeder immediately before or after each other within flocking events that they shared. 

All data analysis was done in R Version 4.2.2.

---File Summary---
                              
 
--Individual feeder visits--

"records_and_events_allyears.Rds"

This list contains each record of a tagged bird at a feeder, along with additional information, such as flocking event of that record and preceding/following birds, to help with analysis and cross-reference. 

List object 1 contains records from winter 2011/12, LO2 from winter 2012/13, and LO3 from winter 2013/14. Columns are the same across each list object.

Column summary:

 - id
   ID number for each individual bird
   
 - location
   Feeder id where the visit was recorded
   
 - time
   Time at which the visit was recorded
   
 - day
   Day of the year that the visit was recorded (e.g February 2 = 33)
   
 - year
   Data year in which the visit was recorded
   Data years are calculated as follows
    Winter 2011/12 = 2012
    Winter 2012/13 = 2013
    Winter 2013/14 = 2014
    
 - flockevent
   Flocking event that this record is classified in, to allow cross referencing with other data. 
   
 - lastbird
   ID of the bird observed at the relevant feeder in the record before
   
 - nextbird
   ID of the bird observed at the relevant feeder in the record after
   
 - arrive
   Is this the first consecutive record of this bird at this feeder? I.e has this bird just 'arrived'

 - leave
   Is this the last consecutive record of this bird at this feeder? I.e after this record does the bird 'leave'
   
 - exday
   'Experimental day' - day of data being recorded during that data year. As recording is only on weekends and started at slightly different times across years, the relationship between exday and day will differ between data years.



--Event information--

"event_information_allyears.Rds"

This list contains each flocking event calculated from data used in the analysis, including information about flock size, location, and time. Flocking events were calculated using the asnipe package.

List object 1 contains records from winter 2011/12, LO2 from winter 2012/13, and LO3 from winter 2013/14. Columns are the same across each list object.

Column summary:

 - flockevent
   Flocking event number
   
 - location
   Feeder id where the flocking event occurred
   
 - start.time
   Time when the flocking event was estimated to begin
   
 - stop.time
   Time when the flocking event was estimated to end
   
 - flocksize
   Number of tagged birds observed in the flocking event
   
 - day
   Day of the year that the flocking event was recorded (e.g February 2 = 33)
   
 - year
   Data year in which the flocking event was recorded
   Data years are calculated as follows
    Winter 2011/12 = 2012
    Winter 2012/13 = 2013
    Winter 2013/14 = 2014 


--Pair status definitions--

"pair_statuses_allyears.Rds"

This data frame provides the foundation for the pairs which are used for analysis, as well as allowing a more detailed demonstration of how pair statuses are estimated.

Column summary:

 - MaleID
   ID of the male bird within the pair
   
 - FemaleID
   ID of the female bird within the pair
   
 - PairID
   Unique identifier for pairs (consistent across years) created by pasting together the male id and female id
   
 - Year
   Data year for which pair status is being calculated. For the breeding season, data year is the spring in which the pair was observed (i.e spring 2012 = 2012)
   
 - pairobsYear
   Whether the pair bred together during the data year

 - maleobsYear
   Whether the male was observed breeding during that year
   
 - femaleobsYear
   Whether the female was observed breeding during that year
   
 - pairobsPrev
   Whether the pair bred together during the previous year
   
 - maleobsPrev
   Whether the male was observed breeding during the previous year
   
 - femaleobsPrev
   Whether the female was observed breeding during the previous year
   
 - maleJuv
   Is the male a juvenile (born in the previous year)?

 - femaleJuv
   Is the female a juvenile (born in the previous year)?
   
 - maleLater
   Is the male observed in any year after this one (do we know he is not dead)?
   
 - femaleLater
   Is the female observed in any year after this one (do we know she is not dead)?
   
 - status
   Defined pair status (see manuscript Appendix for a description of status options)
   
 - simplestatus
   Statuses condensed into fewer, more usable categories
   
 - maledataPrev
   Is there usable feeder record data for the male in the winter before the relevant spring
   
 - femaledataPrev
   Is there usable feeder record data for the female in the winter before the relevant spring   

 - maledataPrev
   Is there usable feeder record data for the male in the winter following the relevant spring
   
 - femaledataPrev
   Is there usable feeder record data for the female in the winter following therelevant spring
   
 - pairdataPrev
   Is there usable feeder record data for both birds in the winter before the relevant spring

 - pairdataNext
   Is there usable feeder record data for both birds in the winter following therelevant spring


--Flocking events by bird--

"bird_flocking_events_allyears.Rds"

This list provides a record of every flocking event a bird was a part of, along with the location, date, and time of that event.

List object 1 contains records from winter 2011/12, LO2 from winter 2012/13, and LO3 from winter 2013/14. Columns are the same across each list object.

Column summary:

 - ring
   Bird BTO ring number
   
 - flockevent
   Flocking event number (unique within but not between data years)
   
 - location
   Feeder the flocking event occurred at
   
 - start_time
   Time the flocking event began 
   
 - stop_time
   Time the flocking event ended 
   
 - nwkend 
   Weekend of the year that the flocking event occurred in 
   
 - arrive
   Was the individual's flocking event before this one at a different feeder?
   
 - leave
   Was the individual's flocking event after this one at a different feeder?
   
 - day
   Julian day that the flocking event occurred
   
 - year
   Data year in which the flocking event was recorded
   Data years are calculated as follows
    Winter 2011/12 = 2012
    Winter 2012/13 = 2013
    Winter 2013/14 = 2014 

 - exday
   'Experimental day' - day of data being recorded during that data year. As recording is only on weekends and started at slightly different times across years, the relationship between exday and day will differ between data years.
   
 - exwknd
   'Experimental weekend' - weekend of data being recorded during that year. Similarly to exday, relationship between exwknd and nwkend will differ between data years.
   
 - sex
   Sex (M, F, or U (unknown)) of the individual
 


--All non-pair associations--

"rand_assoc_list.Rds"

This dataframe provides a list of, for each focal individual used in the analysis, every individual they were observed sharing a flocking event.

Column summary:

 - id
   Focal bird BTO ring number 
   
 - pairnum
   Unique identifier for the pair which the focal individual is a part of
   
 - year
   Data year for the pair and relevant winter.
   Data years are calculated as follows
    Winter 2011/12 = 2012
    Winter 2012/13 = 2013
    Winter 2013/14 = 2014 
   
 - original_pairid
   The BTO ring number of the bird in the focal bird's original analysis pair.
   
 - sex
   The focal bird's sex (M, F, or U)
   
 - pairtype
   'original' = the pair recorded in this row is an original pair, used in the other analyses
   'random' = the pair recorded in this row is the focal bird and a non-pair associate
   
 - rand_pairid
   BTO ring number of the non-pair associate
   
 - day
   Julian day that the association was observed
   
 - maxpairs
   The number of non-pair associates the focal bird had on that day 
   
 - final_pairid 
   The 'original_pairid' and 'final_pairid' columns merged, recording the relevant partner of the focal bird for that row
   
 - exday
   'Experimental day' - day of data being recorded during that data year. As recording is only on weekends and started at slightly different times across years, the relationship between exday and day will differ between data years.
   
 - sharedevents
   Number of flocking events the focal bird and partner (final_pairid) were observed in together on that day
   
 - focal.n.events
   Number of flocking events the focal bird was observed in on that day 
   
 - partner.n.events
   Number of flocking events the partner was observed in on that day 
   
 - simplestatus 
   Pair status of the 'original' pair
   
 - sri
   Winter association score as calculated with sharedevents, focal.n.events, and partner.n.events 
   
 - failures
   partner.n.events + focal.n.events + sharedevents, to be used in modelling
 

--Individual demographic records--

"individual_records.Rds"

This list contains demographic information for each individual observed across the years of data collection.

List object 1 contains records from winter 2011/12, LO2 from winter 2012/13, and LO3 from winter 2013/14. Columns are the same across each list object.

 - id
   BTO ring number of the individual
   
 - species
   Species codes are as follows:
    'bluti' = Blue tit 
    'greti' = Great tit 
    'coati' = Coal tit 
    'marti' = Marsh tit 
    'nutha' = Nuthatch
   Only great tit records are used in this analysis
   
 - sex
   The individual's sex (M, F, or U (unknown))
   
 - age
   Estimated age of the individual from ringing records
   
 - immigrant
   'FALSE' if the bird was ringed as a chick in the woods, 'TRUE' otherwise
   
 
