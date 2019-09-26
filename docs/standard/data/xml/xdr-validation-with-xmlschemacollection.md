---
title: Weryfikacja XDR przy użyciu klasy XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 00833027-1428-4586-83c1-42f5de3323d1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83eabbccfa2116142e9ee5889e3368ad4273b541
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306394"
---
# <a name="xdr-validation-with-xmlschemacollection"></a><span data-ttu-id="c079f-102">Weryfikacja XDR przy użyciu klasy XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="c079f-102">XDR Validation with XmlSchemaCollection</span></span>

<span data-ttu-id="c079f-103">Jeśli sprawdzany schemat danych XML (XDR) jest przechowywany w elemencie **XmlSchemaCollection**, jest on SKOJARZONY z identyfikatorem URI przestrzeni nazw określonym podczas dodawania schematu do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c079f-103">If the XML-Data Reduced (XDR) schema you are validating against is stored in the **XmlSchemaCollection**, it is associated with the namespace URI specified when the schema was added to the collection.</span></span> <span data-ttu-id="c079f-104">**XmlValidatingReader** MAPUJE identyfikator URI przestrzeni nazw w dokumencie XML do schematu, który odnosi się do tego identyfikatora URI w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c079f-104">**XmlValidatingReader** maps the namespace URI in the XML document to the schema that corresponds to that URI in the collection.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c079f-105">Klasa jest obecnie przestarzała i została zastąpiona <xref:System.Xml.Schema.XmlSchemaSet> klasą. <xref:System.Xml.Schema.XmlSchemaCollection></span><span class="sxs-lookup"><span data-stu-id="c079f-105">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="c079f-106">Aby uzyskać więcej informacji na <xref:System.Xml.Schema.XmlSchemaSet> temat klasy, zobacz zestaw [XmlSchemaSet dla kompilacji schematu](xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="c079f-106">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](xmlschemaset-for-schema-compilation.md).</span></span>

<span data-ttu-id="c079f-107">Na przykład, jeśli element główny dokumentu XML to `<bookstore xmlns="urn:newbooks-schema">`, gdy schemat zostanie dodany do obiektu **XmlSchemaCollection** , odwołuje się do tej samej przestrzeni nazw, co następuje:</span><span class="sxs-lookup"><span data-stu-id="c079f-107">For example, if the root element of the XML document is `<bookstore xmlns="urn:newbooks-schema">`, when the schema is added to the **XmlSchemaCollection** it references the same namespace, as follows:</span></span>

```
xsc.Add("urn:newbooks-schema", "newbooks.xdr")
```

<span data-ttu-id="c079f-108">Poniższy przykład kodu tworzy element **XmlValidatingReader** , który pobiera **XmlTextReader** i dodaje schemat XDR, wartość osobowy. XDR do obiektu **XmlSchemaCollection**:</span><span class="sxs-lookup"><span data-stu-id="c079f-108">The following code example creates an **XmlValidatingReader** that takes an **XmlTextReader** and adds an XDR schema, HeadCount.xdr, to the **XmlSchemaCollection**:</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Schema

Namespace ValidationSample

    Class Sample

        Public Shared Sub Main()
            Dim tr As New XmlTextReader("HeadCount.xml")
            Dim vr As New XmlValidatingReader(tr)

            vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr")
            vr.ValidationType = ValidationType.XDR
            AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler

            While vr.Read()
                PrintTypeInfo(vr)
                If vr.NodeType = XmlNodeType.Element Then
                    While vr.MoveToNextAttribute()
                        PrintTypeInfo(vr)
                    End While
                End If
            End While
            Console.WriteLine("Validation finished")
        End Sub

        Public Shared Sub PrintTypeInfo(vr As XmlValidatingReader)
            If vr.SchemaType IsNot Nothing Then
                If TypeOf vr.SchemaType Is XmlSchemaDatatype Or TypeOf vr.SchemaType Is XmlSchemaSimpleType Then
                    Dim value As Object = vr.ReadTypedValue()
                    Console.WriteLine($"{vr.NodeType}({vr.Name},{value.GetType().Name}):{value}")
                End If
            End If
        End Sub

        Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)
            Console.WriteLine("***Validation error")
            Console.WriteLine($"Severity:{args.Severity}")
            Console.WriteLine($"Message:{args.Message}")
        End Sub
    End Class
End Namespace
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
            var tr = new XmlTextReader("HeadCount.xml");
            var vr = new XmlValidatingReader(tr);

            vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr");
            vr.ValidationType = ValidationType.XDR;
            vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);

            while(vr.Read())
            {
                PrintTypeInfo(vr);
                if (vr.NodeType == XmlNodeType.Element)
                {
                   while(vr.MoveToNextAttribute())
                       PrintTypeInfo(vr);
                }
            }
            Console.WriteLine("Validation finished");
        }

        public static void PrintTypeInfo(XmlValidatingReader vr)
        {
            if (vr.SchemaType != null)
            {
                if(vr.SchemaType is XmlSchemaDatatype || vr.SchemaType is XmlSchemaSimpleType)
                {
                    object value = vr.ReadTypedValue();
                    Console.WriteLine($"{vr.NodeType}({vr.Name},{value.GetType().Name}):{value}");
                }
            }
        }

        public static void ValidationHandler(object sender, ValidationEventArgs args)
        {
            Console.WriteLine("***Validation error");
            Console.WriteLine($"\tSeverity:{args.Severity}");
            Console.WriteLine($"\tMessage:{args.Message}");
        }
    }
}
```

<span data-ttu-id="c079f-109">Poniżej przedstawiono zawartość pliku wejściowego, np *. XML*, do zweryfikowania:</span><span class="sxs-lookup"><span data-stu-id="c079f-109">The following outlines the contents of the input file, *HeadCount.xml*, to be validated:</span></span>

```xml
<!--Load HeadCount.xdr in SchemaCollection for Validation-->
<HeadCount xmlns='xdrHeadCount'>
   <Name>Waldo Pepper</Name>
   <Name>Red Pepper</Name>
</HeadCount>
```

<span data-ttu-id="c079f-110">Poniżej przedstawiono zawartość pliku schematu XDR, np *. XDR*, do zweryfikowania:</span><span class="sxs-lookup"><span data-stu-id="c079f-110">The following outlines the contents of the XDR schema file, *HeadCount.xdr*, to be validated against:</span></span>

```xml
<Schema xmlns="urn:schemas-microsoft-com:xml-data" xmlns:dt="urn:schemas-microsoft-com:datatypes">
   <ElementType name="Name" content="textOnly"/>
   <AttributeType name="Bldg" default="2"/>
   <ElementType name="HeadCount" content="eltOnly">
      <element type="Name"/>
      <attribute type="Bldg"/>
   </ElementType>
</Schema>
```

## <a name="see-also"></a><span data-ttu-id="c079f-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c079f-111">See also</span></span>

- <xref:System.Xml.XmlValidatingReader.ValidationType%2A>
- [<span data-ttu-id="c079f-112">Kompilacja schematu a klasa XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="c079f-112">XmlSchemaCollection Schema Compilation</span></span>](xmlschemacollection-schema-compilation.md)
