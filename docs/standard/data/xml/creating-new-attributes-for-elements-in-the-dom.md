---
title: Tworzenie nowych atrybutów dla elementów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
ms.openlocfilehash: 79a3390933256ed862d35c90db0aab2177cdfc41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711015"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>Tworzenie nowych atrybutów dla elementów w modelu DOM

Tworzenie nowych atrybutów jest inne niż tworzenie innych typów węzłów, ponieważ atrybuty nie są węzłami, ale są właściwościami węzła elementu i są zawarte w **XmlAttributeCollection** skojarzonym z elementem. Istnieje wiele sposobów utworzenia atrybutu i dołączenia go do elementu:

- Pobierz węzeł elementu i Użyj **Właściwości SetAttribute** , aby dodać atrybut do kolekcji atrybutów tego elementu.

- Utwórz węzeł **XmlAttribute** przy użyciu metody **CreateAttribute** , Pobierz węzeł elementu, a następnie użyj **SetAttributeNode** , aby dodać węzeł do kolekcji atrybutów tego elementu.

Poniższy przykład pokazuje, jak dodać atrybut do elementu przy użyciu metody **SetAttribute** :

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As New XmlDocument()
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _
                    "<title>Pride And Prejudice</title>" & _
                    "</book>")
        Dim root As XmlElement = doc.DocumentElement

        ' Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel")

        Console.WriteLine("Display the modified XML...")
        Console.WriteLine(doc.InnerXml)
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
        var doc = new XmlDocument();
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +
                    "<title>Pride And Prejudice</title>" +
                    "</book>");
        XmlElement root = doc.DocumentElement;

        // Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel");

        Console.WriteLine("Display the modified XML...");
        Console.WriteLine(doc.InnerXml);
    }
}
```

Poniższy przykład przedstawia nowy atrybut tworzony przy użyciu metody **CreateAttribute** . Następnie pokazuje atrybut dodany do kolekcji atrybutów elementu **Book** przy użyciu metody **SetAttributeNode** .

Uwzględniając następujący kod XML:
  
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

i Dołącz do elementu:

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

Pełny przykładowy kod można znaleźć w <xref:System.Xml.XmlDocument.CreateAttribute%2A>.

Można również utworzyć węzeł **XmlAttribute** i użyć metod **InsertBefore** lub **InsertAfter** , aby umieścić go w odpowiedniej pozycji w kolekcji. Jeśli atrybut o tej samej nazwie już istnieje w kolekcji atrybutów, istniejący węzeł **XmlAttribute** zostanie usunięty z kolekcji, a nowy węzeł **XmlAttribute** zostanie wstawiony. Jest to tak samo samo jak Metoda **SetAttribute** . Metody te przyjmują jako parametr, istniejący węzeł jako punkt odniesienia do wykonania **InsertBefore** i **InsertAfter**. Jeśli nie podasz węzła referencyjnego wskazującego, gdzie wstawić nowy węzeł, wartość domyślna dla metody **InsertAfter** polega na wstawieniu nowego węzła na początku kolekcji. Domyślna pozycja **InsertBefore**, jeśli nie podano węzła odwołania, znajduje się na końcu kolekcji.

Jeśli utworzono **XmlNamedNodeMap** atrybutów, można dodać atrybut według nazwy przy użyciu metody <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Aby uzyskać więcej informacji, zobacz [kolekcje węzłów w NamedNodeMaps i aktualizacja](node-collections-in-namednodemaps-and-nodelists.md).

## <a name="default-attributes"></a>Atrybuty domyślne

Jeśli utworzysz element, który jest zadeklarowany jako mający atrybut domyślny, wówczas nowy domyślny atrybut z jego wartością domyślną jest tworzony przez XML Document Object Model (DOM) i dołączony do elementu. Węzły podrzędne atrybutu domyślnego są również tworzone w tym momencie.

## <a name="attribute-child-nodes"></a>Węzły podrzędne atrybutu

Wartość węzła atrybutu staną się węzłami podrzędnymi. Istnieją tylko dwa typy prawidłowych węzłów podrzędnych: węzły **XmlText** i **XmlEntityReference** . Są to węzły podrzędne w sensie, że metody, takie jak **FirstChild** i **LastChild** , przetwarzają je jako węzły podrzędne. Takie rozróżnienie atrybutu z węzłami podrzędnymi jest ważne przy próbie usunięcia atrybutów lub węzłów podrzędnych atrybutu. Aby uzyskać więcej informacji, zobacz [usuwanie atrybutów z węzła elementu w modelu dom](removing-attributes-from-an-element-node-in-the-dom.md).

## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](xml-document-object-model-dom.md)
