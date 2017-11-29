---
title: "Uzyskiwanie dostępu do atrybutów w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a433ec5f83a50aa4fe4b2017a0dac3d2a5e5710c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="accessing-attributes-in-the-dom"></a>Uzyskiwanie dostępu do atrybutów w modelu DOM
Atrybuty są właściwościami elementu nie elementów podrzędnych elementu. Ta różnica jest istotna z powodu metody używane do nawigacji element równorzędny, nadrzędny i węzły podrzędne elementu XML modelu DOM (Document Object). Na przykład **parametr PreviousSibling** i **NextSibling** metod nie są używane do nawigacji z elementu, atrybutu lub między atrybutami. Zamiast tego atrybutu jest właściwością elementu i jest własnością elementu, ma **OwnerElement** właściwości i nie **parentNode** właściwości, oraz różne metody nawigacji.  
  
 Jeśli bieżący węzeł jest elementem, użyj **HasAttribute** metodę, aby sprawdzić, czy są jakiekolwiek atrybuty skojarzone z elementem. Gdy wiadomo, że element ma atrybuty, istnieje wiele metod dostępu do atrybutów. Aby pobrać jednego atrybutu elementu, można użyć **GetAttribute** i **GetAttributeNode** metody **XmlElement** lub możesz uzyskać wszystkie atrybuty do kolekcji. Uzyskiwanie kolekcji jest przydatne, jeśli zachodzi konieczność wykonania iteracji w kolekcji. Jeśli chcesz, aby wszystkie atrybuty z elementu, użyj **atrybuty** właściwości elementu, aby pobrać wszystkie atrybuty w kolekcji.  
  
## <a name="retrieving-all-attributes-into-a-collection"></a>Pobieranie wszystkich atrybutów do kolekcji  
 Jeśli wszystkie atrybuty węzeł elementu wprowadzane do kolekcji, należy wywołać **XmlElement.Attributes** właściwości. Pobiera to **XmlAttributeCollection** zawiera wszystkie atrybuty elementu. **XmlAttributeCollection** klasa dziedziczy **XmlNamedNode** mapy. W związku z tym metody i właściwości dostępne w kolekcji obejmują dostępnych na mapie nazwany węzeł dodatkowo do metod i właściwości specyficzne dla **XmlAttributeCollection** klas, takich jak **ItemOf ** właściwości lub **Append** metody. Reprezentuje każdego elementu w kolekcji atrybutów **XmlAttribute** węzła. Aby znaleźć liczby atrybutów w elemencie, Pobierz **XmlAttributeCollection**i użyj **liczba** właściwości, aby wyświetlić liczbę **XmlAttribute** węzły są w kolekcji.  
  
 W poniższym przykładzie pokazano, jak można pobrać atrybutu kolekcji i przy użyciu **liczba** metodę indeksem pętli iteracja go. Następnie kod pokazano, jak pobrać jeden atrybut z kolekcji i wyświetlić jej wartość.  
  
```vb  
Imports System  
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
  
 W tym przykładzie wyświetlane są następujące dane wyjściowe:  
  
 **Dane wyjściowe**  
  
 Wyświetl wszystkie atrybuty w kolekcji.  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 Informacje zawarte w kolekcji atrybutów można pobrać według nazwy lub numeru indeksu. W powyższym przykładzie pokazano, jak można pobrać danych według nazwy. Kolejnym przykładzie pokazano, jak można pobrać danych za pomocą numeru indeksu.  
  
 Ponieważ **XmlAttributeCollection** jest kolekcją i można powtórzyć przez nazwę lub indeks, w tym przykładzie pokazano, wybierając pierwszy atrybut z kolekcji przy użyciu liczony od zera indeks i następującego pliku **baseuri.xml**, jak wejściowego.  
  
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
  
Imports System  
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
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
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
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a>Trwa pobieranie węzła atrybutu poszczególnych  
 Można pobrać węzła jeden atrybut z elementu <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> metoda jest używana. Zwraca obiekt typu **XmlAttribute**. Po utworzeniu **XmlAttribute**, wszystkie metody i właściwości dostępne w <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> klasy są dostępne dla tego obiektu, takich jak znajdowanie **OwnerElement**.  
  
```vb  
Imports System  
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
  
 Można również zrobić opisane w poprzednim przykładzie, gdzie węzeł pojedynczy atrybut jest pobierana z kolekcji atrybutów. Poniższy przykład kodu pokazuje sposób jeden wiersz kodu mogą być zapisywane na jeden atrybut pobrać za pomocą numeru indeksu od elementu głównego dokumentu XML drzewa, znanej również jako **DocumentElement** właściwości.  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
