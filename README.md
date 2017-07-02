# PBR-Scripts
Set of Control Scripts for PSI Bioreactor Client software developed in Department of Adaptive Biotechnologies. These scripts allow automatization of both basic and advanced funcionalities not available in standard distribution of the client software. 

## Getting Started

Put one of the below listed .js file content to PSI Bioreactor Client software protocol scripting part and modify appropriately UserDefined section (object).

1. [PP-GrowthOptimizer](https://gcri-doab.github.io/PBR-Scripts/PP-GrowthOptimizer.js)
Script for automatic quazi-continous characterization and consequent optimization of microorganism cultivated in PBRs based on programatic control of selected PBR parameters. The script is activated on a peristaltic pump scripting protocol.
2. [O2-PIcurveMeasurement](https://gcri-doab.github.io/PBR-Scripts/O2-PIcurveMeasurement.js)
Script for automatic measurement of oxygen evolution and respiration under different irradiances (PI curve measurements). The script is activated on the oxygen probe (O2 dissolved) scripting protocol.

### Examples

1. PP-GrowthOptimizer

#### Growth rate (doubling time determination) based on OD680 while diluting acording to OD720
```
turbidostatODType: 720
regressionODType: 680
```

#### Growth characterization uder different temperatures
```
controlledParameter: "temperature"
controlledParameterSteps: [ 28, 32, 34, 30, 26, 22 ]
```

#### Growth characterization under different lights
```
controlledParameter: "lights"
controlledParameterSteps: [[ 1100, 25 ], [ 440, 25 ], [ 55, 25 ]]
```
The lights setting has to be always in pairs, i.e. for each light channel the value has to be specified. Please note the double brackets at the begining and the end of values list

2. O2-PIcurveMeasurement

#### Measurement of O2 evolution/respiration synchronized with turbidostat dilutions
```
turbidostatSynchronization: true
growthStabilitySynchronization: true
lightStepMultiplierValues: [ 1 ]
```
Here it's necessary to run PP-GrowthOptimizer script at the same time with enabled growth statistics
```
growthStatistics: true
```

#### Measurement of O2 evolution/respiration synchronized with turbidostat dilutions and when the culture gets stable
```
turbidostatSynchronization: true
lightStepMultiplierValues: [ 1 ]
```


#### Measurement O2 evolution/respiration in triplicate
```
lightStepMultiplierValues: [ 1, 1, 1 ]
```

#### Measurement of PI-curve
```
lightStepMultiplierValues: [ 8, 4, 2, 1, 1/2, 1/4, 1/8, 1/16 ]
```

This setting enables measurement of PI curve in seven different light intensities defined as multiplier of actual actinic light intensity

## Authors

* **Jan Červený** - *Initial work* - [Department of Adaptive Biotechnologies](http://www.czechglobe.cz/en/institute-structure/research-sector/v-domain-adaptive-and-innovative-techniques/#doab)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

## License

Licensed under [MIT license](https://gcri-doab.github.io/PBR-Scripts/LICENSE)

## Acknowledgments

Projects supporting development:

1. Services and access to state-of-the-art facilities for systems biology across Europe; project „Center for Systems Biology ([C4Sys](http://c4sys.cz))“
2. Innovations for mitigation of global change impacts; project „[CzechGlobe 2020](http://www.czechglobe.cz/en/) – Development of the Centre of Global Climate Change Impacts Studies“
3. Investigation on dynamics of complex reaction networks in enzyme reactors and photobioreactorsproject
