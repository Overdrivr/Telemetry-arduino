# Telemetry-arduino

Drag-n-drop C++ Arduino wrapper of the [`Telemetry`](https://github.com/Overdrivr/Telemetry) library.

`Telemetry` lets you exchange data between an Arduino board and a computer,
 often through a serial or bluetooth connection, using a convenient interface.

Any exchanged data carries a label, called *topic*. Topics are used to identify data,
and act as a named communication channel.

* Sending data from the Arduino is called *publishing*.

```cpp
#include <Telemetry.hpp>
int32_t i;

void setup() {
  Serial.begin(9600); // Do not forget to initialize serial
  i = 0;
}

void loop() {
  // Send counter value under topic `foo`
  Telemetry.pub_i32("foo", i);   i++;
}

```

* Receiving data on the Arduino is done by attaching a variable to a topic.
When new data is received under the topic, the attached variable is updated.

```cpp
#include <Telemetry.hpp>
float thr;

void setup() {
  Serial.begin(9600);
  Telemetry.attach_f32_to("throttle", &thr);
}

void loop() {
  // thr is updated here, if new data is received under `throttle`
  Telemetry.update();
}
```

# Installation

1. Dowload `Telemetry-arduino.zip` from the [latest release](https://github.com/Overdrivr/Telemetry-arduino/releases)
2. Unzip into your Arduino library folder
3. Start Arduino IDE, go into `Sketch`->`Include Library`->`Telemetry`

# On the computer

As soon as a device publishes data, it is possible to leverage the power of
the [Pytelemetry Command Line Interface](https://github.com/Overdrivr/pytelemetrycli)
[![PyPI version](https://badge.fury.io/py/pytelemetrycli.svg)](https://badge.fury.io/py/pytelemetrycli).

This terminal application lets you interact with the device, using simple commands.

Opening a live plot is as simple as

```
:> plot someTopic
```

![Plot example](https://raw.githubusercontent.com/Overdrivr/pytelemetrycli/master/graph.png)


# Central documentation

* TODO : API Reference
* [Overview of the library](https://github.com/Overdrivr/Telemetry/wiki/Overview)
* [Protocol description](https://github.com/Overdrivr/Telemetry/wiki/Protocol-description)
* [A non-exhaustive list of all the awesome features](https://github.com/Overdrivr/Telemetry/wiki/Awesome-features-overview)

All the information can be found from the [Wiki Home](https://github.com/Overdrivr/Telemetry/wiki).
