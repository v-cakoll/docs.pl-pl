---
title: Uzyskiwanie dostępu do atrybutów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b456dc407f634e7f40f69bbac9b6d932f1f4420
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350706"
---
# <a name="accessing-attributes-in-the-dom"></a>Uzyskiwanie dostępu do atrybutów w modelu DOM

Atrybuty są właściwościami elementu, a nie elementem podrzędnym elementu. Ta różnica jest ważna ze względu na metody używane do nawigowania w węzłach elementów równorzędnych, nadrzędnych i podrzędnych Document Object Model XML (DOM). Na przykład metody **PreviousSibling** i **NextSibling** nie są używane do nawigowania po elemencie do atrybutu lub między atrybutami. Zamiast tego atrybut jest właściwością elementu i jest własnością elementu, ma właściwość **OwnerElement** , a nie Właściwość **ParentNode** i ma odrębne metody nawigacji.

Gdy bieżącym węzłem jest element, użyj metody **HasAttribute** , aby sprawdzić, czy istnieją atrybuty skojarzone z elementem. Gdy wiadomo, że element ma atrybuty, istnieje wiele metod uzyskiwania dostępu do atrybutów. Aby pobrać pojedynczy atrybut z elementu, można użyć metody **GetAttribute** i **GetAttributeNode** w elemencie **XmlElement** lub można uzyskać wszystkie atrybuty do kolekcji. Uzyskanie kolekcji jest przydatne, jeśli trzeba wykonać iterację w kolekcji. Jeśli chcesz uzyskać wszystkie atrybuty z elementu, użyj właściwości **atrybuty** elementu, aby pobrać wszystkie atrybuty do kolekcji.

## <a name="retrieving-all-attributes-into-a-collection"></a>Pobieranie wszystkich atrybutów do kolekcji

Jeśli chcesz, aby wszystkie atrybuty węzła elementu zostały umieszczone w kolekcji, wywołaj Właściwość **XmlElement. Attributes** . Spowoduje to pobranie **XmlAttributeCollection** , który zawiera wszystkie atrybuty elementu. Klasa **XmlAttributeCollection** dziedziczy z mapy **XmlNamedNode** . W związku z tym metody i właściwości dostępne w kolekcji obejmują te, które są dostępne na mapie nazwanych węzłów, a także metody i właściwości specyficzne dla klasy **XmlAttributeCollection** , takie jak Właściwość **ItemOf** lub metoda **append** . Każdy element w kolekcji atrybutów reprezentuje węzeł **XmlAttribute** . Aby znaleźć liczbę atrybutów dla elementu, należy pobrać **XmlAttributeCollection**i użyć właściwości **Count** , aby zobaczyć, ile węzłów **XmlAttribute** znajduje się w kolekcji.

Poniższy przykład kodu przedstawia sposób pobierania kolekcji atrybutów i, przy użyciu metody **Count** dla indeksu pętli, iteracji nad nim. Następnie kod pokazuje, jak pobrać pojedynczy atrybut z kolekcji i wyświetlić jego wartość.

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim myElement As XmlElement = doc.DocumentElement

        ' Create an attribute collection from the element.
        Dim attrColl As XmlAttributeCollection = myElement.Attributes

        ' Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...")
        Dim i As Integer
        For i = 0 To attrColl.Count - 1
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)
            Console.Write("{0}", attrColl.ItemOf(i).Value)
            Console.WriteLine()
        Next

        ' Retrieve a single attribute from the collection; specifically, the
        ' attribute with the name "misc".
        Dim attr As XmlAttribute = attrColl("misc")

        ' Retrieve the value from that attribute.
        Dim miscValue As String = attr.InnerXml

        Console.WriteLine("Display the attribute information.")
        Console.WriteLine(miscValue)

    End Sub
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{

    public static void Main()
    {
        XmlDocument doc = new XmlDocument();
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +
                      "<title>The Handmaid's Tale</title>" +
                      "<price>14.95</price>" +
                      "</book>");

        // Move to an element.
        XmlElement myElement = doc.DocumentElement;

        // Create an attribute collection from the element.
        XmlAttributeCollection attrColl = myElement.Attributes;

        // Show the collection by iterating over it.
        Console.WriteLine("Display all the attributes in the collection...");
        for (int i = 0; i < attrColl.Count; i++)
        {
            Console.Write("{0} = ", attrColl[i].Name);
            Console.Write("{0}", attrColl[i].Value);
            Console.WriteLine();
        }

        // Retrieve a single attribute from the collection; specifically, the
        // attribute with the name "misc".
        XmlAttribute attr = attrColl["misc"];

        // Retrieve the value from that attribute.
        String miscValue = attr.InnerXml;

        Console.WriteLine("Display the attribute information.");
        Console.WriteLine(miscValue);

    }
}
```

W tym przykładzie są wyświetlane następujące dane wyjściowe:

**Output**

Wyświetl wszystkie atrybuty w kolekcji.

```console
genre = novel
ISBN = 1-861001-57-5
misc = sale item
Display the attribute information.
sale item
```

Informacje w kolekcji atrybutów można pobrać według nazwy lub numeru indeksu. Powyższy przykład pokazuje, jak pobrać dane według nazwy. W następnym przykładzie pokazano, jak pobrać dane według numeru indeksu.

Ponieważ **XmlAttributeCollection** jest kolekcją i można ją powtórzyć według nazwy lub indeksu, w tym przykładzie pokazano, jak wybrać pierwszy atrybut z kolekcji przy użyciu indeksu opartego na zero i przy użyciu następującego pliku, **baseUri. XML**, jako dane wejściowe.

### <a name="input"></a>Dane wejściowe

```xml
<!-- XML fragment -->
<book genre="novel">
  <title>Pride And Prejudice</title>
</book>
```

```vb
Option Explicit On
Option Strict On

Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()
        ' Create the XmlDocument.
        Dim doc As New XmlDocument()
        doc.Load("http://localhost/baseuri.xml")

        ' Display information on the attribute node. The value
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)
        Console.WriteLine("The value of the attribute:  {0}", attr.InnerText)
    End Sub 'Main
End Class 'Sample
```

```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
  public static void Main()
  {
    // Create the XmlDocument.
    XmlDocument doc = new XmlDocument();

    doc.Load("http://localhost/baseuri.xml");

    // Display information on the attribute node. The value
    // returned for BaseURI is 'http://localhost/baseuri.xml'.
    XmlAttribute attr = doc.DocumentElement.Attributes[0];
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);
    Console.WriteLine("The value of the attribute:  {0}", attr.InnerText);
  }
}
```

## <a name="retrieving-an-individual-attribute-node"></a>Pobieranie pojedynczego węzła atrybutu

Aby pobrać pojedynczy węzeł atrybutu z elementu, używana jest metoda <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType>. Zwraca obiekt typu **XmlAttribute**. Po utworzeniu elementu **XmlAttribute**wszystkie metody i właściwości dostępne w klasie <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> są dostępne dla tego obiektu, takich jak znalezienie elementu **OwnerElement**.

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As XmlDocument = New XmlDocument()
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _
               "<title>The Handmaid's Tale</title>" & _
               "<price>14.95</price>" & _
               "</book>")

        ' Move to an element.
        Dim root As XmlElement
        root = doc.DocumentElement

        ' Get an attribute.
        Dim attr As XmlAttribute
        attr = root.GetAttributeNode("ISBN")

        ' Display the value of the attribute.
        Dim attrValue As String
        attrValue = attr.InnerXml
        Console.WriteLine(attrValue)

    End Sub
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;

 public class Sample
 {
      public static void Main()
      {
    XmlDocument doc = new XmlDocument();
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +
                   "<title>The Handmaid's Tale</title>" +
                   "<price>14.95</price>" +
                   "</book>");

    // Move to an element.
     XmlElement root = doc.DocumentElement;

    // Get an attribute.
     XmlAttribute attr = root.GetAttributeNode("ISBN");

    // Display the value of the attribute.
     String attrValue = attr.InnerXml;
     Console.WriteLine(attrValue);

    }
}
```

Można również jak pokazano w poprzednim przykładzie, gdzie jeden węzeł atrybutu jest pobierany z kolekcji atrybutów. Poniższy przykład kodu pokazuje, jak można napisać jeden wiersz kodu w celu pobrania pojedynczego atrybutu według numeru indeksu z katalogu głównego drzewa dokumentu XML, znanego również jako właściwość **DocumentElement** .

```csharp
XmlAttribute attr = doc.DocumentElement.Attributes[0];
```

## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
