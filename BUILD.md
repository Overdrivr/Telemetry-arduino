# Build flow

Grabs core sources from [Telemetry core repository](github.com/Overdrivr/Telemetry)

```
gradle prepare
```

Build and install tests
```
gradle installTestDebugExecutable
```

Run tests
```
cd build/install/test/debug/test.bat
test.bat
cd ../../../../
```

Pack all required files into a zip file for distribution
```
gradle distribute
```
