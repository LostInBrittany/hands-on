# Step-2.1: Did you said Time series! 

You are now alone in your quest, an exoplanet hunter! But me, your personal assistant will teach you some basics knowledge to help you achieve this awesome quest!
But first just to help you, and to guide you, I will start with the beginning.

## Star's data

During this tutorial, you will study the NASA Kepler data-set. You will in charge to discover some exo-planet. But what are an exo-planet ? They are only some planet that turn around other stars that doesn't belong to our solar system. One of the method is to studied the stars lightcurve and to detect drops on them. This means that a planet moved on top of star, and if this sequence is repeated several times, this means that there is an exoplanet graviting near this specific star.

## Convert to Time series

As the lightcurve of a star evolve according to time, it can be considered as a Time-series.

## But why would we use Warp 10 ?

Warp 10 is one of the multiple Time series database that exists. It includes also the WarpScript language, saw in the previous step. This language is dedicated to Time-series manipulation.

## And What does a Time-series looks like ?

If you type the following WarpScript code: 

```
// Create an empty GTS
NEWGTS
```

You will push on top of the stack a Time series. A Time series follow this modelisation:

  - It requires a fix classname (the key "c") in quantum result, which is the main identifier of a Time series (string). 
  - The labels "l" also identifies the existing series. This corresponds to a map object of string key/values.
  - The attributes "a", same as Labels but they are global parameters of a series and can evolve without creating a new series.
  - And finally the values "v" which includes a timestamp (time of the current point), a location and a value (can be Double, Long, Boolean or string)

To update any of those parameters, you can use one of the following functions that updates the initial Time series to define a temerature sensor located in someone home.

```
// Create an empty Time series
NEWGTS

// Rename this Time series
'temperature.sensor' RENAME

// Relabel this Time series
{ 'device' 'Rosemount.214C.RTD-1' } RELABEL

// Gives an Attribute to this Time series
{ 'room' 'kitchen' } SETATTRIBUTES

//
// Add today's value to this Time series
//

// Push Today's time
NOW 

// Push location
NaN NaN NaN 

// Push 14 degrees as value 
14

// Add today's value in current Time series
ADDVALUE

// Add yesterday value to this Time series

// Compute Yesterday time (Today minus one day)
NOW 1 d - 

// Push location
NaN NaN NaN 

// Push the value 12 
12

// Add the value to current Time series
ADDVALUE
```

This will leave the initial GTS created on top of the stack, updated with each different values.

# To be continued

Luckily for you all the needed Time series for you exoplanet are already available in our back-end! You can start to explore them in our [next step](/step-2-Keplers-Data/2.2-Exploring-known-time-series/README.md).