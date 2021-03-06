<h2 style="padding-top:0">Humidity</h2>

### Device Compatibility
<img class="creator-compatibility-icon" src="../../img/creator-icon.svg">

## Overview

The humidity sensor reports values for:

* Humidity
* Temperature

## References

Below is the overview of the humidity sensor implementation. Code example can be found [here](/matrix-hal/examples/humidity).

These header files are required to use the humidity sensor.

```language-cpp
// Interfaces with humidity sensor
#include "matrix_hal/humidity_sensor.h"
// Holds data from humidity sensor
#include "matrix_hal/humidity_data.h"
// Communicates with MATRIX device
#include "matrix_hal/matrixio_bus.h"
```

<details open>
<summary style="font-size: 1.75rem; font-weight: 300;">HumidityData</summary>
`HumidityData` is a required **object** that contains the humidity sensor's supported data parameters.

```language-cpp
// Create HumidityData object
matrix_hal::HumidityData humidity_data;
```

The following code accesses the parameters of `HumidityData`.

```language-cpp
// Output is represented in %
float humidity = humidity_data.humidity; 
// Output is represented in °C
float temperature = humidity_data.temperature; 
```
</details>

<details open>
<summary style="font-size: 1.75rem; font-weight: 300;">HumiditySensor</summary>
`HumiditySensor` is a required **object** that contains functions to interface with the humidity sensor.

```language-cpp
// Create HumiditySensor object
matrix_hal::HumiditySensor humidity_sensor;
```
The functions below are part of `HumiditySensor`.

<details>
<summary style="font-size: 1.5rem; font-weight: 300;">.Setup</summary>
`Setup` is a **function** that takes a `MatrixIOBus` object as a parameter and sets that object as the bus to use for communicating with MATRIX device.

```language-cpp
// Function declaration in header file
void Setup(MatrixIOBus *bus);
```

```language-cpp
// Set humidity_sensor to use MatrixIOBus bus
humidity_sensor.Setup(&bus);
```
</details>

<details>
<summary style="font-size: 1.5rem; font-weight: 300;">.Read</summary>
`Read` is a **function** that takes a `HumidityData` object as a parameter and writes the current humidity sensor data into the `HumidityData` object.

```language-cpp
// Function declaration in header file
bool Read(HumidityData *data);
```

```language-cpp
// Overwrites humidity_data with new data from humidity sensor
humidity_sensor.Read(&humidity_data);
```
</details>
</details>