---
title: Jak przesyłać strumieniowo fragmenty XML z czytnika XmlReader (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714651"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Jak przesyłać strumieniowo fragmenty XML z czytnika XmlReader (C#)

Gdy trzeba przetworzyć duże pliki XML, może nie być możliwe załadowanie całego drzewa XML do pamięci. W tym temacie pokazano, <xref:System.Xml.XmlReader>jak przesyłać strumieniowo fragmenty przy użyciu pliku .  
  
 Jednym z najbardziej skutecznych <xref:System.Xml.XmlReader> sposobów <xref:System.Xml.Linq.XElement> używania do odczytu obiektów jest napisać własną metodę osi niestandardowej. Metoda osi zazwyczaj zwraca kolekcję, takich jak <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie. W metodzie osi niestandardowej po utworzeniu fragmentu XML przez wywołanie <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody, zwróć kolekcję przy użyciu . `yield return` Zapewnia to semantyki odroczonego wykonania do metody osi niestandardowej.  
  
 Podczas tworzenia drzewa XML <xref:System.Xml.XmlReader> z obiektu, <xref:System.Xml.XmlReader> musi być umieszczony na elemencie. Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nie zwraca, dopóki nie odczytał tag zamknięcia elementu.  
  
 Jeśli chcesz utworzyć częściowe drzewo, możesz utworzyć wystąpienie <xref:System.Xml.XmlReader>czytnika w węźle, który chcesz <xref:System.Xml.Linq.XElement> przekonwertować na <xref:System.Xml.Linq.XElement> drzewo, a następnie utworzyć obiekt.  
  
Temat [Jak przesyłać strumieniowo fragmenty XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i przykład sposobu przesyłania strumieniowego bardziej złożonego dokumentu.
  
 Temat [Jak wykonać transformację przesyłania strumieniowego dużych dokumentów XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład użycia LINQ do XML do przekształcania bardzo dużych dokumentów XML przy zachowaniu małej ilości pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy metodę osi niestandardowej. Można go zbadać za pomocą kwerendy LINQ. Metoda osi niestandardowej , jest metodą, `StreamRootChildDoc`która jest przeznaczona specjalnie do `Child` odczytu dokumentu, który ma element powtarzający.  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
bbb  
ccc  
```  
  
 W tym przykładzie dokument źródłowy jest bardzo mały. Jednak nawet jeśli istnieją `Child` miliony elementów, w tym przykładzie nadal będzie miał niewielki rozmiar pamięci.  
