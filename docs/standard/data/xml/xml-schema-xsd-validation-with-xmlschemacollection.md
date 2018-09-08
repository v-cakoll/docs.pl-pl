---
title: Walidacja schematu (XSD) XML przy użyciu klasy XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c570f812ec06c6ead0d12dc14c33fcdfd1f075c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128368"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a><span data-ttu-id="4719e-102">Walidacja schematu (XSD) XML przy użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="4719e-102">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>
<span data-ttu-id="4719e-103">Możesz użyć <xref:System.Xml.Schema.XmlSchemaCollection> do weryfikowania dokumentu XML względem schematów języka (XSD) definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="4719e-103">You can use the <xref:System.Xml.Schema.XmlSchemaCollection> to validate an XML document against XML Schema definition language (XSD) schemas.</span></span> <span data-ttu-id="4719e-104"><xref:System.Xml.Schema.XmlSchemaCollection> Zwiększa wydajność dzięki przechowywaniu schematów w kolekcji, aby nie były ładowane do pamięci występuje każdego sprawdzania poprawności czasu.</span><span class="sxs-lookup"><span data-stu-id="4719e-104">The <xref:System.Xml.Schema.XmlSchemaCollection> improves performance by storing schemas in the collection so they are not loaded into memory each time validation occurs.</span></span> <span data-ttu-id="4719e-105">Jeśli schemat istnieje w kolekcji schematów `schemaLocation` atrybut jest używany w celu wyszukania schematu w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4719e-105">If the schema exists in the schema collection, the `schemaLocation` attribute is used to look up the schema in the collection.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4719e-106"><xref:System.Xml.Schema.XmlSchemaCollection> Klasa jest obecnie przestarzały i został zastąpiony <xref:System.Xml.Schema.XmlSchemaSet> klasy.</span><span class="sxs-lookup"><span data-stu-id="4719e-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="4719e-107">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaSet> , zobacz klasę [klasa XmlSchemaSet na potrzeby kompilacji schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="4719e-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
 <span data-ttu-id="4719e-108">Poniższy przykład pokazuje element główny pliku danych.</span><span class="sxs-lookup"><span data-stu-id="4719e-108">The following example shows the root element of a data file.</span></span>  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 <span data-ttu-id="4719e-109">W tym przykładzie wartość `targetNamespace` atrybut jest `urn:bookstore-schema`, który jest w tej samej przestrzeni nazw, która jest używana podczas dodawania schemat <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="4719e-109">For this example, the value of the `targetNamespace` attribute is `urn:bookstore-schema`, which is the same namespace that is used when adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
 <span data-ttu-id="4719e-110">Poniższy przykład kodu dodaje schematu XML do <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="4719e-110">The following code example adds an XML Schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
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
  
 <span data-ttu-id="4719e-111">`targetNamespace` Atrybutu jest zazwyczaj używana podczas dodawania `namespaceURI` właściwość <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metodę <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="4719e-111">The `targetNamespace` attribute is generally used when you add the `namespaceURI` property in the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method for the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="4719e-112">Odwołanie o wartości null można określić przed dodaniem schemat <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="4719e-112">You can specify a null reference before adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="4719e-113">Ciąg pusty ("") powinna być używana dla schematy bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4719e-113">An empty string ("") should be used for schemas without a namespace.</span></span> <span data-ttu-id="4719e-114"><xref:System.Xml.Schema.XmlSchemaCollection> Może mieć tylko jeden schemat bez przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4719e-114">The <xref:System.Xml.Schema.XmlSchemaCollection> can have only one schema without a namespace.</span></span>  
  
 <span data-ttu-id="4719e-115">Poniższy przykład kodu dodaje do schematu XML HeadCount.xsd, <xref:System.Xml.Schema.XmlSchemaCollection> i sprawdza poprawność HeadCount.xml.</span><span class="sxs-lookup"><span data-stu-id="4719e-115">The following code example adds an XML Schema, HeadCount.xsd, to the <xref:System.Xml.Schema.XmlSchemaCollection> and validates HeadCount.xml.</span></span>  
  
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
  
 <span data-ttu-id="4719e-116">Poniżej opisano zawartość pliku wejściowego HeadCount.xml ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="4719e-116">The following outlines the contents of the input file, HeadCount.xml, to be validated.</span></span>  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 <span data-ttu-id="4719e-117">Poniżej opisano zawartość pliku schematu XML, HeadCount.xsd, aby być weryfikowany pod kątem.</span><span class="sxs-lookup"><span data-stu-id="4719e-117">The following outlines the contents of the XML Schema file, HeadCount.xsd, to be validated against.</span></span>  
  
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
  
 <span data-ttu-id="4719e-118">Poniższy przykład kodu tworzy <xref:System.Xml.XmlValidatingReader> przyjmującej <xref:System.Xml.XmlTextReader>.</span><span class="sxs-lookup"><span data-stu-id="4719e-118">The following code example creates an <xref:System.Xml.XmlValidatingReader> that takes an <xref:System.Xml.XmlTextReader>.</span></span> <span data-ttu-id="4719e-119">Plik wejściowy, sample4.xml, jest weryfikowane względem schematu XML sample4.xsd.</span><span class="sxs-lookup"><span data-stu-id="4719e-119">The input file, sample4.xml, is validated against the XML Schema, sample4.xsd.</span></span>  
  
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
  
 <span data-ttu-id="4719e-120">Poniżej opisano zawartość pliku wejściowego sample4.xml ma zostać zweryfikowana.</span><span class="sxs-lookup"><span data-stu-id="4719e-120">The following outlines the contents of the input file, sample4.xml, to be validated.</span></span>  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 <span data-ttu-id="4719e-121">Poniżej opisano zawartość pliku schematu XML, sample4.xsd, aby być weryfikowany pod kątem.</span><span class="sxs-lookup"><span data-stu-id="4719e-121">The following outlines the contents of the XML Schema file, sample4.xsd, to be validated against.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4719e-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4719e-122">See also</span></span>

- <xref:System.Xml.XmlParserContext>  
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>  
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="4719e-123">Kompilacja schematu a klasa XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="4719e-123">XmlSchemaCollection Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)
