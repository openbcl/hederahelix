# Fire tests with "Hedera helix" on different scales to enable fire simulation on green facades
In addition to large-scale fire tests, numerical fire simulations offer a cost- and time-efficient way to calculate fire spread on green facades for varying conditions or measures. However, accurate simulation of fire spread using mathematical models remains a major challenge in fire safety science and requires fundamental material investigations and model validation at different scales. FDS's thermal degradiation model for vegetation relies on fuel reaction kinetics and thermophysical parameters. These parameters cannot be measured directly, but are derived from cross-scale experiments.

**This repository contains the results of fire tests on ivy (Hedera helix) to obtain pyrolysis parameters for simulating fire spread on green facades.**

For further information, please refer to corresponding paper, which is also available in the repository [^1].

### TUBE FURNACE WITH MASS LOSS MEASUREMENT

Thermogravimetric Analysis (TGA) are often used to determine reaction parameters. Typically, a TGA sample weighs a few milligrams. An ivy leaf, on the other hand, weighs up to 2 g. Given the heterogeneous nature of the plant components, it is advantageous to analyse the entire sample. Therefore, experiments were performed inside a tube furnace at Forschungszentrum Jülich. The modified tube furnace was equipped with a balance, allowing for precise measurement of the mass change during heating of individual ivy leaves. Single fresh ivy leaves (approximately 0.3 g each) with a moisture content around M = 200 % were analysed. The leaves were heated from ambient temperature to 900 °C at a rate of 5 K/min. The tube furnace was purged with air at a flow rate of 10 l/min. The repository contains the results of a representative test.

### TGA ANALYSIS WITH FDS

The Arrhenius parameters, which consist of the pre-exponential factor A and activation energy E, are crucial for describing temperature-dependent reactions. Within FDS, a feature TGA_ANALYSIS = T is employed to estimate these parameters, considering the temperature range relevant to pyrolysis. Two key parameters, REFERENCE_TEMPERATURE and PYROLYSIS_RANGE, are introduced for this purpose. The six reaction parameters for the three predominant reactions, as well as the moisture fraction, were determined from from the above test using the inverse modelling framework PROPTI.

| | Unit | Moisture evaporation | Pyrolysis of dry vegetation | Char oxidation |
| --- | --- | --- | --- | --- |
| REFERENCE_TEMPERATURE | °C | 139.4 | 343.1 | 444.8 |
| PYROLYSIS_RANGE | °C | 71.3 | 227.0 | 42.5 |
| Pre-Exponential Factor A | 1/s | 2.947E+11 | 4.999E+03 | 7.980E+37 |
| Activation Energy E | J/mol | 1.079E+05 | 7.550E+04 | 5.481E+05 |

The MOISTURE_FRACTION, related on a dry weight basis, was determined as M = 194 % = 1.94.

The repository contains the PROPTI input files and the results of the run with the best fitting.

### FURNITURE CALORIMETER: BENCH SCALE EXPERIEMENTS

To validate the FDS model fitted with the pyrolysis parameters determined from micro-scale experimentes, bench-scale experiments were carried out under controlled boundary conditions. The experimental setup consisted of a prefabricated vertical greenery system (VGS) positioned on a calcium silicate board. The dimensions of the VGS, consisted of ivy tendrils on a steel grid, were 1.3 m in height and 1.0 m in width. The depth of the vegetation was 0.15 m.

A propane-fueled gas burner was placed directly in front of the middle of the vertical greenery system, emitting 20 kW (tests 1-5) or 40 kW (test 6). The vertical greenery system was placed on a balance with a resolution of 0.5 g. The tests were conducted inside a furniture calorimeter according to ISO 9705. The heat release rate was determined using oxygen consumption calorimetry.

In total six experiments with different conditions were performed:

| | Plant | Moisture Content | HRR Burner |
| --- | --- | --- | --- |
| Test 1 | Fresh ivy (Hedera helix) | 188 % | 20 kW |
| Test 2 | Fresh ivy (Hedera helix) | 194 % | 20 kW |
| Test 3 | Wilted ivy (Hedera helix) | 149 % | 20 kW |
| Test 4 | Wilted ivy (Hedera helix) | 141 % | 20 kW |
| Test 5 | Dried ivy (Hedera helix) | 28 % | 20 kW |
| Test 6 | Dried ivy (Hedera helix) | 29 % | 40 kW |

The repository contains the results of the tests (heat release rate and mass loss).

## ACKNOWLEDGEMENT

Special thanks are extended to Forschungszentrum Jülich, Germany for making it possible to conduct thermogravimetric analyses in the Tube Furnace.
We extend our gratitude to the Verein zur Förderung der Ingenieurmethoden im Brandschutz e.V. (VIB) for their co-financing of the bench-scale experiments.

[^1]: Johannes Schliebe, Manuel Osburg, Karen De Lannoye: Fire tests with "Hedera helix" on different scales to enable fire simulation on green facades, 4th International Symposium on Fire Safety of Facades FSF 2024, June 10 - 12, 2024, Lund, Sweden.
