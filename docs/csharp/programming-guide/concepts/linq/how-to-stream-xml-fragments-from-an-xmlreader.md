---
title: 'Instrukcje: Strumieniowe fragmenty XML z elementu XmlReaderC#()'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: c27c2165af95b8b781564e14efc0668f596e3057
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592408"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Instrukcje: Strumieniowe fragmenty XML z elementu XmlReaderC#()
W przypadku konieczności przetworzenia dużych plików XML może nie być możliwe załadowanie całego drzewa XML do pamięci. W tym temacie pokazano, jak przesyłać fragmenty strumieni <xref:System.Xml.XmlReader>przy użyciu.  
  
 Jednym z najbardziej skutecznych sposobów używania <xref:System.Xml.XmlReader> do odczytu <xref:System.Xml.Linq.XElement> obiektów jest napisanie własnej niestandardowej metody osi. Metoda osi zwykle zwraca kolekcję <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>, taką jak, jak pokazano w przykładzie w tym temacie. W metodzie osi niestandardowej po utworzeniu fragmentu kodu XML przez wywołanie <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody Zwróć kolekcję przy użyciu. `yield return` Zapewnia to odroczoną semantykę wykonania do niestandardowej metody osi.  
  
 Podczas tworzenia drzewa XML na podstawie <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader> , musi on być umieszczony w elemencie. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nie zwraca do momentu odczytania tagu zamknięcia elementu.  
  
 Jeśli chcesz utworzyć drzewo częściowe, można stworzyć wystąpienie <xref:System.Xml.XmlReader>obiektu, umieścić go na węźle, który ma zostać przekonwertowany <xref:System.Xml.Linq.XElement> na drzewo <xref:System.Xml.Linq.XElement> , a następnie utworzyć obiekt.  
  
 Temat [jak: Fragmenty strumienia XML z dostępem do informacji nagłówka (C#)](./how-to-stream-xml-fragments-with-access-to-header-information.md) zawierają informacje i przykład na potrzeby przesyłania strumieniowego bardziej złożonego dokumentu.  
  
 Temat [jak: Przekształcenie przesyłania strumieniowego dużych dokumentów XMLC#(](./how-to-perform-streaming-transform-of-large-xml-documents.md) ) zawiera przykład użycia LINQ to XML do przekształcania bardzo dużych dokumentów XML przy zachowaniu małej ilości pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie jest tworzona Metoda osi niestandardowej. Zapytanie można wykonać za pomocą [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Metoda osi niestandardowej, `StreamRootChildDoc`, jest metodą, która jest przeznaczona specjalnie do odczytywania dokumentu, który ma powtarzalny `Child` element.  
  
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
  
```  
bbb  
ccc  
```  
  
 W tym przykładzie dokument źródłowy jest bardzo mały. Jednak nawet w przypadku milionów `Child` elementów ten przykład nadal ma niewielki rozmiar pamięci.  
  