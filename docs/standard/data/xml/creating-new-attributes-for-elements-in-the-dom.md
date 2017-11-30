---
title: "Tworzenie nowych atrybutów dla elementów w modelu DOM"
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
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6970ffc38e900c9b47c58c8ae4b81b9551f5589b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>Tworzenie nowych atrybutów dla elementów w modelu DOM
Tworzenie nowych atrybutów różni się od tworzenia innych typów węzła, ponieważ atrybuty nie są węzłami, ale są właściwości węzeł elementu i są zawarte w **XmlAttributeCollection** skojarzone z elementem. Istnieje wiele sposobów tworzenia atrybutu i dołączenie go do elementu:  
  
-   Pobierz węzeł elementu i użyj **SetAttribute** można dodać atrybutu do kolekcji atrybutów tego elementu.  
  
-   Utwórz **XmlAttribute** za pomocą węzła **CreateAttribute** metody, Pobierz węzeł elementu, a następnie użyj **SetAttributeNode** można dodać węzła do tej kolekcji atrybutów element.  
  
 Poniższy przykład pokazuje, jak dodać atrybutu do elementu przy użyciu **SetAttribute** metody.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
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
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 W poniższym przykładzie przedstawiono nowy atrybut tworzone przy użyciu **CreateAttribute** metody. Następnie pokaże atrybut, który został dodany do kolekcji atrybut **książki** przy użyciu elementu **SetAttributeNode** metody.  
  
 Podane następujący kod XML:  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Utwórz nowy atrybut i nadaj mu wartość:  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 i dołącz je do elementu:  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **Dane wyjściowe**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Kodu pełny przykład można znaleźć w folderze <xref:System.Xml.XmlDocument.CreateAttribute%2A>.  
  
 Można również utworzyć **XmlAttribute** węzeł i użyj **InsertBefore** lub **InsertAfter** metody umieszczony w odpowiedniej pozycji w kolekcji. Jeśli atrybut o takiej samej nazwie jest już obecny w kolekcji atrybutów, istniejące **XmlAttribute** węzeł zostanie usunięty z kolekcji i nowych **XmlAttribute** wstawić węzła. Wykonuje ten sam sposób jak **SetAttribute** metody. Te metody przyjmują jako parametr istniejący węzeł jako punkt odniesienia w celu **InsertBefore** i **InsertAfter**. Jeśli nie podasz węzeł odniesienia, wskazując miejsca do wstawienia nowego węzła, wartością domyślną **InsertAfter** metodą jest Wstaw nowy węzeł na początku kolekcji. To domyślne położenie dla **InsertBefore**, jeśli żaden węzeł odniesienia jest dostępne, znajduje się na końcu kolekcji.  
  
 Jeśli utworzono **XmlNamedNodeMap** atrybutów, można dodać atrybutu przy użyciu nazwy <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Aby uzyskać więcej informacji, zobacz [węzła kolekcje NamedNodeMaps i NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## <a name="default-attributes"></a>Domyślne atrybuty  
 Jeśli utworzysz element, który jest zadeklarowana, aby mieć domyślnego atrybutu nowy atrybut domyślny z wartością domyślną jest tworzone przez XML modelu DOM (Document Object) i dołączony do elementu. Węzły podrzędne domyślny atrybut również są tworzone w tym momencie.  
  
## <a name="attribute-child-nodes"></a>Węzły podrzędne atrybutu  
 Wartość węzła atrybutu staje się węzły podrzędne. Istnieją tylko dwa typy węzłów prawidłowy element podrzędny: **XmlText** węzłów i **XmlEntityReference** węzłów. Są to węzłów podrzędnych w tym sensie, że metod, takich jak **FirstChild** i **LastChild** ich przetworzyć jako węzły podrzędne. Podczas próby usunięcia atrybuty lub atrybut węzły podrzędne, ważne jest tej różnicy atrybutu o węzłów podrzędnych. Aby uzyskać więcej informacji, zobacz [usuwanie atrybutów z węzłem elementu w modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
