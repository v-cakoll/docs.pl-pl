---
title: Weryfikacja schematu XML (XSD) przy użyciu klasy XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
ms.openlocfilehash: 994153ba93848ebb120f23bdf6a979462a65142d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159484"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a>Weryfikacja schematu XML (XSD) przy użyciu klasy XmlSchemaCollection
Za pomocą <xref:System.Xml.Schema.XmlSchemaCollection> można sprawdzić poprawność dokumentu XML względem schematów języka definicji schematu XML (XSD). <xref:System.Xml.Schema.XmlSchemaCollection> zwiększa wydajność przez przechowywanie schematów w kolekcji, dzięki czemu nie są one ładowane do pamięci po każdym wystąpieniu walidacji. Jeśli schemat istnieje w kolekcji schematów, atrybut `schemaLocation` jest używany do wyszukania schematu w kolekcji.  
  
> [!IMPORTANT]
> Klasa <xref:System.Xml.Schema.XmlSchemaCollection> jest obecnie przestarzała i została zastąpiona klasą <xref:System.Xml.Schema.XmlSchemaSet>. Aby uzyskać więcej informacji na temat klasy <xref:System.Xml.Schema.XmlSchemaSet>, zobacz zestaw [XmlSchemaSet dla kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).  
  
 Poniższy przykład pokazuje element główny pliku danych.  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 Dla tego przykładu wartość atrybutu `targetNamespace` jest `urn:bookstore-schema`, która jest tą samą przestrzenią nazw, która jest używana podczas dodawania schematu do <xref:System.Xml.Schema.XmlSchemaCollection>.  
  
 Poniższy przykład kodu dodaje schemat XML do <xref:System.Xml.Schema.XmlSchemaCollection>.  
  
```vb  
Dim xsc As New XmlSchemaCollection()  
' XML Schema.  
xsc.Add("urn:bookstore-schema", schema)
reader = New XmlTextReader(filename)  
vreader = New XmlValidatingReader(reader)  
vreader.Schemas.Add(xsc)  
```  
  
```csharp  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
// XML Schema.  
xsc.Add("urn:bookstore-schema", schema);  
reader = new XmlTextReader (filename);  
vreader = new XmlValidatingReader (reader);  
vreader.Schemas.Add(xsc);  
```  
  
 Atrybut `targetNamespace` jest zazwyczaj używany podczas dodawania właściwości `namespaceURI` w metodzie <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> dla <xref:System.Xml.Schema.XmlSchemaCollection>. Można określić odwołanie o wartości null przed dodaniem schematu do <xref:System.Xml.Schema.XmlSchemaCollection>. Pusty ciąg ("") powinien być używany w schematach bez przestrzeni nazw. <xref:System.Xml.Schema.XmlSchemaCollection> może mieć tylko jeden schemat bez przestrzeni nazw.  
  
 Poniższy przykład kodu dodaje schemat XML, wartość osobowy. xsd, do <xref:System.Xml.Schema.XmlSchemaCollection> i sprawdza poprawność. XML.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Schema  
  
Namespace ValidationSample  
  
   Class Sample  
  
      Public Shared Sub Main()  
         Dim tr As New XmlTextReader("HeadCount.xml")  
         Dim vr As New XmlValidatingReader(tr)  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd")  
         vr.ValidationType = ValidationType.Schema  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)  
         Console.WriteLine("***Validation error")  
         Console.WriteLine("Severity:{0}", args.Severity)  
         Console.WriteLine("Message:{0}", args.Message)  
      End Sub  
      ' ValidationHandler  
   End Class  
   ' Sample  
End Namespace  
' ValidationSample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Schema;  
  
namespace ValidationSample  
{  
   class Sample  
   {  
      public static void Main()  
      {  
         XmlTextReader tr = new XmlTextReader("HeadCount.xml");  
         XmlValidatingReader vr = new XmlValidatingReader(tr);  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd");  
         vr.ValidationType = ValidationType.Schema;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read());  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage  :{0}", args.Message);  
      }  
   }  
}  
```  
  
 Poniżej przedstawiono zawartość pliku wejściowego, np. XML, do zweryfikowania.  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 Poniżej przedstawiono zawartość pliku schematu XML, np. xsd, do zweryfikowania.  
  
```xml  
<xs:schema xmlns="xsdHeadCount" targetNamespace="xsdHeadCount" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name='HeadCount' type="HEADCOUNT"/>  
   <xs:complexType name="HEADCOUNT">  
      <xs:sequence>  
         <xs:element name='Name' type='xs:string' maxOccurs='unbounded'/>  
      </xs:sequence>  
      <xs:attribute name='division' type='xs:int' use='optional' default='8'/>  
   </xs:complexType>  
</xs:schema>  
```  
  
 Poniższy przykład kodu tworzy <xref:System.Xml.XmlValidatingReader>, który przyjmuje <xref:System.Xml.XmlTextReader>. Plik wejściowy sample4. XML jest sprawdzany pod kątem schematu XML sample4. xsd.  
  
```vb  
Dim tr As New XmlTextReader("sample4.xml")  
Dim vr As New XmlValidatingReader(tr)  
vr.ValidationType = ValidationType.Schema  
vr.Schemas.Add("datatypesTest", "sample4.xsd")  
AddHandler vr.ValidationEventHandler, AddressOf ValidationCallBack  
While vr.Read()  
   Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name)  
End While  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("sample4.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
vr.ValidationType = ValidationType.Schema;  
        vr.Schemas.Add("datatypesTest", "sample4.xsd");  
vr.ValidationEventHandler += new ValidationEventHandler(ValidationCallBack);  
while(vr.Read()) {  
    Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name);  
    }  
```  
  
 Poniżej przedstawiono zawartość pliku wejściowego (sample4. xml) do zweryfikowania.  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 Poniżej przedstawiono zawartość pliku schematu XML, sample4. xsd, aby sprawdzić poprawność.  
  
```xml  
<xs:schema
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
    xmlns:tns="datatypesTest"
    targetNamespace="datatypesTest"  
    elementFormDefault="qualified">  
  
<xs:element name = "datatypes">  
  <xs:complexType>  
    <xs:all>  
        <xs:element name="number">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="number_1" type="xs:decimal" maxOccurs="unbounded"/>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
    </xs:all>  
  </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlParserContext>
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>
- [Kompilacja schematu a klasa XmlSchemaCollection](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)
