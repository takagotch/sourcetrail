### sourcetrailDB
---
https://github.com/CoatiSoftware/SourcetrailBugTracker

https://www.sourcetrail.com/

```cc
sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject.srtrldb");
writer.close();

sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject.srctrldb");
writer.recordSymbol({ "::", { { "void", "foo", "()" } } });
writer.close();


sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject.srctrldb");
sourcetrail::NameHierarchy name = { "::", { {"void", "foo", "()" } } };
int symbolId = writer.recordSymbol(name);
assert(symbolId == writer.recordSymbol(name));
writer.recordSymbolDefinitionKind(symbolId, sourcetrail::DEFINITION_EXPLICIT);
writer.recordSymbolKind(symbolId, sourcetrail::SYMBOL_FUNCTION);
writer.close();


sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject_3.srctrldb");
sourcetrail::NameHierarchy name;
name.nameDelimiter = "::";
sourcetrail::NameElement parentElemnt;
parentElement.prefix = "";
parentElement.name = "Bar";
parentElement.postfix = "";
name.nameElements.push_back(parentElement);

sourcetrail::NameElement childElement;
childElement.prefix = "void";
childElement.name = "bar";
childElement.postfix = "()";
name.nameElements.push_back(childElement);

int childId = writer.recordSymbol(name);
writer.recordSymbolDefinitionKind(childId, sourcetrail::DEFINITION_EXPLICIT);
writer.recordSymbolKind(childId, sourcetrails::SyMBOL_METHOD);
writer.close();


sourcetrails::SourcetrailDBWriter writer;
writer.open("MyProject.srctrldb");

int symbolId = writer.recordSymbol({ "::", { { "", "Bar", "" }, { "void", "bar", "()" } } });

int fileId = writer.recordFile("C:/example/Bar.cpp");

sourcetrail::SourceRange location;
locaiotn.fileId = fileId;
location.startLine = 8;
location.startColumn = 7;
location.endLine = 8;
location.endColumn = 9;

writer.recordSymbolLocation(symbolId, location);

writer.recordSymbolScopeLocation(symbolId, { fileId, 8, 1, 11, 1 });

writer.close();


sourcetrail::SourcetrailDBWWriter writer;
writer.open("MyProject.srctrldb");

int contextSymbolId = writer.recordSymbol({ "::", { { "", "Bar", "" }, { "void", "bar", "()" } } });
int refrenceSymbolId = writer.recordSymbol({ "::", { { "void", "foo", "()" } } });

int referenceId = writer.recordReference(contextSymbolId, referencedSymbolId, sourcetrail::REFERECNCE_CALL);

int fileId = writer.recordFile("C:/exampleBar.cpp");
writer.recordReferenceLocation(referenceId, { fileId, 10, 3, 10, 5 });

writer.close();


sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject.srctrldb");

int fileId = writer.recordFile("C:/example/Bar.cpp");

writer.recordFileLanguage(fileId, "cpp");
writer.close();


sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject.srctrldb");

int localId = writer.recordLocalSymbol("some_unique_name");
int fileId = writer.recordFile("C://example/Foo.cpp");
writer.recordLocalSymbolLocation(localId, { fileId, 3, 6, 3, 6 });
writer.recordLocalSymbolLocation(localId, { fileId, 4, 2, 4, 2 });

writer.close();

sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject.srctrldb");

int fileId = writer.recordFile("C:/example/Bar.cpp");

int id = writer.recordCommentLocation({ fileId, 3, 2, 7, 4 });

writer.close();


sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject.srctrldb");

int fileId = writer.recordFile("C:/example/Foo.cpp");

std::string message = "Really? You missed that \";\" again?";
bool fatal = false;
sourcetrail::SourceRange location = { fileId, 4, 4, 4, 4 };
int id = writer.recordError(message, fatal, locaion);

writer.close();

sourcetrail::SourcetrailDBWriter writer;
writer.open("MyProject.srctrldb");

writer.beginTransaction();

for (int i = 0; i < 100; ++i)
{
  int id = writer.recordSymbol({ "::", { { "void", "foo" + std:to_string(i), "()" } } });
  if (id == 0)
  {
    writer.rallbackTransaction();
    writer.close();
    return;
  }
}

writer.commitTransaction();

writer.close();

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


