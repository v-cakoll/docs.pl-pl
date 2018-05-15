---
title: Weryfikowanie XDR przy użyciu kolekcji XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 00833027-1428-4586-83c1-42f5de3323d1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d4e970423693bbe221f0146ecc07dd69e27bc35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xdr-validation-with-xmlschemacollection"></a><span data-ttu-id="f810e-102">Weryfikowanie XDR przy użyciu kolekcji XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="f810e-102">XDR Validation with XmlSchemaCollection</span></span>
<span data-ttu-id="f810e-103">Jeśli jest sprawdzana poprawność względem schematu XML danych (XDR) są przechowywane w **kolekcji XmlSchemaCollection**, jest on skojarzony z przestrzenią nazw, identyfikator URI określony, jeśli schemat został dodany do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f810e-103">If the XML-Data Reduced (XDR) schema you are validating against is stored in the **XmlSchemaCollection**, it is associated with the namespace URI specified when the schema was added to the collection.</span></span> <span data-ttu-id="f810e-104">**Elementu XmlValidatingReader** mapuje identyfikator URI przestrzeni nazw w dokumencie XML do schematu, do którego odnosi się do tego identyfikatora URI w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f810e-104">**XmlValidatingReader** maps the namespace URI in the XML document to the schema that corresponds to that URI in the collection.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f810e-105"><xref:System.Xml.Schema.XmlSchemaCollection> Klasy jest teraz przestarzałe i zostało zastąpione <xref:System.Xml.Schema.XmlSchemaSet> klasy.</span><span class="sxs-lookup"><span data-stu-id="f810e-105">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="f810e-106">Aby uzyskać więcej informacji na temat <xref:System.Xml.Schema.XmlSchemaSet> , zobacz klasy [XmlSchemaSet kompilowania schematu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="f810e-106">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
 <span data-ttu-id="f810e-107">Na przykład, jeśli element główny dokumentu XML jest `<bookstore xmlns="urn:newbooks-schema">`, gdy schemat zostanie dodany do **kolekcji XmlSchemaCollection** odwołuje się ona do tego samego obszaru nazw, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f810e-107">For example, if the root element of the XML document is `<bookstore xmlns="urn:newbooks-schema">`, when the schema is added to the **XmlSchemaCollection** it references the same namespace, as follows:</span></span>  
  
```  
xsc.Add("urn:newbooks-schema", "newbooks.xdr")  
```  
  
 <span data-ttu-id="f810e-108">Poniższy przykład kodu tworzy **elementu XmlValidatingReader** pobierającej **XmlTextReader** i dodaje do schematu XDR HeadCount.xdr, **kolekcji XmlSchemaCollection**.</span><span class="sxs-lookup"><span data-stu-id="f810e-108">The following code example creates an **XmlValidatingReader** that takes an **XmlTextReader** and adds an XDR schema, HeadCount.xdr, to the **XmlSchemaCollection**.</span></span>  
  
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
      ' Main  
  
      Public Shared Sub PrintTypeInfo(vr As XmlValidatingReader)  
         If Not (vr.SchemaType Is Nothing) Then  
            If TypeOf vr.SchemaType Is XmlSchemaDatatype Or TypeOf vr.SchemaType Is XmlSchemaSimpleType Then  
               Dim value As Object = vr.ReadTypedValue()  
               Console.WriteLine("{0}({1},{2}):{3}", vr.NodeType, vr.Name, value.GetType().Name, value)  
            End If  
         End If  
      End Sub  
      ' PrintTypeInfo  
  
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
  
         vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr");  
         vr.ValidationType = ValidationType.XDR;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read())  
         {  
            PrintTypeInfo(vr);  
            if(vr.NodeType == XmlNodeType.Element)  
            {  
               while(vr.MoveToNextAttribute())  
                  PrintTypeInfo(vr);  
            }  
         }  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void PrintTypeInfo(XmlValidatingReader vr)  
      {  
         if(vr.SchemaType != null)  
         {  
            if(vr.SchemaType is XmlSchemaDatatype || vr.SchemaType is XmlSchemaSimpleType)  
            {  
               object value = vr.ReadTypedValue();  
               Console.WriteLine("{0}({1},{2}):{3}", vr.NodeType, vr.Name, value.GetType().Name, value);  
            }  
         }  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage:{0}", args.Message);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="f810e-109">Poniżej opisano zawartość pliku wejściowego HeadCount.xml do sprawdzenia poprawności.</span><span class="sxs-lookup"><span data-stu-id="f810e-109">The following outlines the contents of the input file, HeadCount.xml, to be validated.</span></span>  
  
```xml  
<!--Load HeadCount.xdr in SchemaCollection for Validation-->  
<HeadCount xmlns='xdrHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</HeadCount>  
```  
  
 <span data-ttu-id="f810e-110">Poniżej opisano zawartość pliku schematu XDR, HeadCount.xdr, aby być weryfikowany pod kątem.</span><span class="sxs-lookup"><span data-stu-id="f810e-110">The following outlines the contents of the XDR schema file, HeadCount.xdr, to be validated against.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f810e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f810e-111">See Also</span></span>  
 <xref:System.Xml.XmlValidatingReader.ValidationType%2A>  
 <!--zz <xref:System.Xml.XmlValidatingReader.Settings%2A>-->  `System.Xml.XmlValidatingReader.Settings`  
 [<span data-ttu-id="f810e-112">Kompilacja schematu a klasa XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="f810e-112">XmlSchemaCollection Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)
