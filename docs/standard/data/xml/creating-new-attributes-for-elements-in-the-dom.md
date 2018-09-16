---
title: Tworzenie nowych atrybutów dla elementów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 870e800220031338557792fa612d4a3101e79f90
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45675564"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>Tworzenie nowych atrybutów dla elementów w modelu DOM
Tworzenie nowych atrybutów różni się od tworzenia innych typów węzła, ponieważ atrybutów nie są węzłami, ale są właściwości węzeł elementu i są zawarte w **XmlAttributeCollection** skojarzone z elementem. Istnieje wiele sposobów, aby utworzyć atrybut i dołączyć go do elementu:  
  
-   Pobierz węzeł elementu i użyć **SetAttribute** Dodawanie atrybutu do kolekcji atrybutu tego elementu.  
  
-   Tworzenie **XmlAttribute** za pomocą węzła **CreateAttribute** metody, Pobierz węzła elementu, a następnie użyj **SetAttributeNode** można dodać węzła do kolekcji atrybutów tego element.  
  
 Poniższy przykład przedstawia sposób dodawania atrybutu do elementu za pomocą **SetAttribute** metody.  
  
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
  
 W poniższym przykładzie pokazano nową atrybutu tworzone przy użyciu **CreateAttribute** metody. Następnie wyświetla atrybut dodawane do kolekcji atrybut **książki** elementu za pomocą **SetAttributeNode** metody.  
  
 Biorąc pod uwagę następujący kod XML:  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Utwórz nowy atrybut i wartości:  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 i dołączyć go do elementu:  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **Output**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 Przykładowe pełny kod znajduje się w temacie <xref:System.Xml.XmlDocument.CreateAttribute%2A>.  
  
 Można również utworzyć **XmlAttribute** węzła i użyj **InsertBefore** lub **InsertAfter** metody, aby umieścić go w odpowiedniej pozycji w kolekcji. Jeśli atrybut o tej samej nazwie istnieje już w kolekcji atrybutów istniejących **XmlAttribute** węzeł zostanie usunięty z kolekcji, a nowe **XmlAttribute** wstawić węzła. Spowoduje to wykonanie taki sam sposób jak **SetAttribute** metody. Te metody przyjmują jako parametru, istniejący węzeł jako punkt odniesienia w celu **InsertBefore** i **InsertAfter**. Jeśli nie podasz węzeł odniesienia, wskazując, skąd można wstawić nowy węzeł, wartość domyślna dla **InsertAfter** metoda polega na Wstaw nowy węzeł na początku kolekcji. Domyślne położenie **InsertBefore**, jeśli nie podano żadnego węzła odwołanie, znajduje się na końcu kolekcji.  
  
 Jeśli utworzono **XmlNamedNodeMap** atrybutów, można dodać atrybutu przy użyciu nazwy <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Aby uzyskać więcej informacji, zobacz [kolekcje węzłów: namednodemaps i NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## <a name="default-attributes"></a>Atrybuty domyślne  
 Jeśli utworzysz element, który jest zadeklarowany ma atrybut domyślny, nowy domyślny atrybut o jego wartość domyślna jest tworzone przez XML Document Object Model (DOM) i dołączony do elementu. Węzły podrzędne domyślnego atrybutu są również tworzone w tej chwili.  
  
## <a name="attribute-child-nodes"></a>Węzły podrzędne atrybutu  
 Wartość węzła atrybutu staje się jego węzłów podrzędnych. Istnieją tylko dwa typy węzłów prawidłowy element podrzędny: **XmlText** węzłów i **XmlEntityReference** węzłów. Są węzły podrzędne, w tym sensie, że metody, takie jak **FirstChild** i **LastChild** przetwarzać je jako węzły podrzędne. Wykonywania tego rozróżnienia atrybutu o węzłów podrzędnych jest ważne, podczas próby usunięcia atrybutów i węzłów podrzędnych atrybutu. Aby uzyskać więcej informacji, zobacz [usuwanie atrybutów z węzła elementu w modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
