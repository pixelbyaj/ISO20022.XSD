# ISO2022.XSD
[![Nuget](https://img.shields.io/nuget/v/ISO20022.XSD)](https://www.nuget.org/packages/ISO20022.XSD/)

## ISO20022.XSD is a .NET library designed to convert ISO 20022 XSD files into standard JSON format.


## Install package

1. Install the `ISO20022.XSD` NuGet package.
  * .NET CLI
  ```cs
    dotnet add package ISO20022.XSD
  ```
  * PackageManager
  ```cs
  Install-Package ISO20022.XSD
  ```

## Usage

```C#
using ISO20022.XSD;

var fileInfo = new FileInfo(fileName);
if (File.Exists(fileName) && fileInfo.Extension.Equals(".xsd"))
{
    XsdToJson xsdLib = new(fileName);
    xsdLib.Convert();
    File.AppendAllText(fileInfo.FullName.Replace(".xsd", ".json"), xsdLib.SchemaJson);
}
```
## Model of JSON
```cs
public class XsdSchema
{
    public string Namespace { get; set; }
    public SchemaElement SchemaElement { get; set; }
}

public class SchemaElement
{
    public string Id { get; set; }
    public string Name { get; set; }
    public string DataType { get; set; }
    public string MinOccurs { get; set; }
    public string MaxOccurs { get; set; }
    public string MinLength { get; set; }
    public string MaxLength { get; set; }
    public string Pattern { get; set; }
    public string FractionDigits { get; set; }
    public string TotalDigits { get; set; }
    public string MinExclusive { get; set; }
    public string MaxExclusive { get; set; }
    public string MinInclusive { get; set; }
    public string MaxInclusive { get; set; }
    public string[] Values { get; set; }
    public bool IsCurrency { get; set; }
    public string XPath { get; set; }
    public List<SchemaElement> Elements { get; set; }
}
```
### Example
```json
{
    "namespace": "urn:iso:std:iso:20022:tech:xsd:camt.053.001.10",
    "schemaElement": {
        "id": "Document",
        "name": "Document",
        "dataType": null,
        "minOccurs": "1",
        "maxOccurs": null,
        "minLength": null,
        "maxLength": null,
        "pattern": null,
        "fractionDigits": null,
        "totalDigits": null,
        "minInclusive": null,
        "maxInclusive": null,
        "values": null,
        "isCurrency": false,
        "xpath": "Document",
        "elements":[
          ...
        ]
    }
}
```