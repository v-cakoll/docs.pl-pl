---
title: Jak strumieniowo fragmenty XML z elementu XmlReader (C#)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714651"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Jak strumieniowo fragmenty XML z elementu XmlReader (C#)

W przypadku konieczności przetworzenia dużych plików XML może nie być możliwe załadowanie całego drzewa XML do pamięci. W tym temacie pokazano, jak przesyłać fragmenty strumieni przy użyciu <xref:System.Xml.XmlReader>.  
  
 Jednym z najbardziej skutecznych sposobów używania <xref:System.Xml.XmlReader> do odczytu obiektów <xref:System.Xml.Linq.XElement> jest pisanie własnej niestandardowej metody osi. Metoda osi zwykle zwraca kolekcję, taką jak <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie. W metodzie osi niestandardowej po utworzeniu fragmentu kodu XML przez wywołanie metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> Zwróć kolekcję przy użyciu `yield return`. Zapewnia to odroczoną semantykę wykonania do niestandardowej metody osi.  
  
 Podczas tworzenia drzewa XML na podstawie obiektu <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlReader> musi być umieszczony w elemencie. Metoda <xref:System.Xml.Linq.XNode.ReadFrom%2A> nie zwraca do momentu odczytania tagu zamknięcia elementu.  
  
 Jeśli chcesz utworzyć częściowe drzewo, Utwórz wystąpienie <xref:System.Xml.XmlReader>, umieść czytnik w węźle, który ma zostać przekonwertowany na drzewo <xref:System.Xml.Linq.XElement>, a następnie Utwórz obiekt <xref:System.Xml.Linq.XElement>.  
  
Temat [jak przesyłać fragmenty XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i przykład na potrzeby przesyłania strumieniowego bardziej złożonego dokumentu.
  
 Temat [jak wykonywać transformację strumieniową dużych dokumentów XML (C#)](./how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład użycia LINQ to XML do przekształcania bardzo dużych dokumentów XML przy zachowaniu małej ilości pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest tworzona Metoda osi niestandardowej. Zapytanie można wykonać za pomocą zapytania LINQ. Metoda osi niestandardowej, `StreamRootChildDoc`, to metoda, która jest przeznaczona specjalnie do odczytywania dokumentu, który ma powtarzający się element `Child`.  
  
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
  
 W tym przykładzie dokument źródłowy jest bardzo mały. Jednak nawet jeśli wystąpiły miliony elementów `Child`, ten przykład nadal ma niewielki wpływ na pamięć.  
