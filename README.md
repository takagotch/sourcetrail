### sourcetrailDB
---
https://github.com/CoatiSoftware/SourcetrailBugTracker

https://www.sourcetrail.com/

```cc
sourcetrail::SourcetrailDBWriter writer;



```

```sh
cd path/toSourcetrailDB
mkdir build
cd build
cmake 
make lib_core

make test_core
./core/test_core

cd path/to/SourcetrailDB
mkdir build
cd build
cmake -DBUILD_BINDINGS_PYTHON=ON
make _sourcetraildb
```

```
```


