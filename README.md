# chenostrovski_card_database_exc_v1_2

Mobile Game Developer Home Exercise.

## Implementation

### Part 1
- Added a new abstract class [`FileType`](Assets/Database/FileProcessing/FileType.cs) to start a fresh 'pathway' for file processing and keeping other classes clean.  
  In addition, I created a factory (following the design pattern) class [`FileFactory`](Assets/Database/FileProcessing/FileFactory.cs) for this object;  
  allowing a structured approach for handling specific file types (JSON/XML) and future flexibility (extending for YAML support).
- [`ModelTransformer`](Assets/Database/FileProcessing/ModelTransformer/ModelTransformer.cs) - Since I don't want to be instantiating `ScriptableObjects` like `CardData` myself,   
  This abstract class will hold Deserialization logic into **my own models** that correspond to the external data files.  
  The Serialization specifics are also kept inside of this class (For example, for XML export I decided to serialize to JSON first).  
  This leaves our [`Import()/Export()`](Assets/Database/FileProcessing/JsonFile.cs) methods with a single responsibility of creating a new asset or writing to a target file, respectively.  
- [`ExtraDataConverter`](Assets/Database/Implementation/ExtraDataConverter.cs) - Helper class that dynamically creates an `ExtraData` instance based on the type attribute.

**Notes**: 
- As for extending file type support, a new developer on the project will need to create a new `ModelTransformer`  
  that inherits from this class and implements the abstract [`Transform()/Serialize()`](Assets/Database/FileProcessing/ModelTransformer/ModelTransformer.cs) methods  
  (`YamlModelTransformer`, for example).  
  Of course it would also be necessary to create a new `FileType` that will be available to get from the factory.  
  More info is available in code documentation.
- [`ExtraDataConverter`](Assets/Database/Implementation/ExtraDataConverter.cs) - prior to writing this, my original attempt was to create a custom [`JsonConverter`](https://www.newtonsoft.com/json/help/html/CustomJsonConverter.htm),  
  which failed due to [`.Populate()`](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonSerializer_Populate.htm) not being able to do it's thing with setter-less properties (`MinionExtraData.Health`, for example).

<img src="screenshots/1_1.jpeg"> <img src="screenshots/1_2.jpeg">

### Part 2
- A
- B
- C

## Unit Tests

I have added several unit tests which cover basic functionality.

##### Running the unit tests:

Click on `run test` in unity.
