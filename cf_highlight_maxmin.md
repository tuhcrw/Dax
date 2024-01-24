/*
Obtains the highest and lowest values per bar in a chart and colours them differently.

Will need to change the all selected to what is on the axis and the item you want to calculate
  */
CF_MaxMin = 
VAR BHours = [Billed Hours]
VAR MaxHoursOverall = 
    MAXX(
        ALLSELECTED(HarvestTimeEntries[fullname]),
        CALCULATE( [Billed Hours] )
    )
VAR MinHoursOverall = 
    MINX(
        ALLSELECTED(HarvestTimeEntries[fullname] ),
        CALCULATE( [Billed Hours] )
    )
VAR Result = 
SWITCH(
    TRUE,
    BHours = MaxHoursOverall, "#22957e",
    BHours = MinHoursOverall, "#ff908c",
    "#7bc8fe"
)
RETURN
Result
