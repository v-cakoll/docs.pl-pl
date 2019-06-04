---
title: 'Instrukcje: Stream fragmentów kodu XML z elementu XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 6937a7160c83def3238c8d2fe3e2b83c996396fd
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484907"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Instrukcje: Stream fragmentów kodu XML z elementu XmlReader (C#)
W przypadku przetwarzania dużych plików XML, może nie być możliwe do załadowania całego drzewa XML do pamięci. W tym temacie pokazano, jak przesyłać strumieniowo fragmentów przy użyciu <xref:System.Xml.XmlReader>.  
  
 Jedną z najbardziej skutecznych sposobów użycia <xref:System.Xml.XmlReader> odczytać <xref:System.Xml.Linq.XElement> obiektów jest napisanie własnej metody osi niestandardowych. Metody osi takich jak zwykle zwraca kolekcję <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie. W metodzie niestandardowej osi po utworzeniu XML fragment, wywołując <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody zwracają kolekcję przy użyciu `yield return`. Dzięki temu semantyki wykonanie odroczone do metody osi niestandardowych.  
  
 Podczas tworzenia drzewa XML z <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader> musi być umieszczony w elemencie. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nie zwraca, dopóki odczyta Zamknij tagu elementu.  
  
 Jeśli chcesz utworzyć drzewo częściowe, można utworzyć wystąpienie <xref:System.Xml.XmlReader>, umieść czytelnika na węźle, który chcesz przekonwertować <xref:System.Xml.Linq.XElement> drzewa, a następnie utwórz <xref:System.Xml.Linq.XElement> obiektu.  
  
 Temat [jak: Stream strumieniowe fragmentów z dostępem do informacji o nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i obejrzeć przykład do przesyłania strumieniowego bardziej złożonych dokumentów.  
  
 Temat [jak: Wykonaj przesyłania strumieniowego Przekształcanie z dużymi dokumentami XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład korzystania z LINQ to XML do transformowania bardzo dużych dokumentów XML przy zachowaniu zużycie pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy metodę niestandardowe osi. Można tworzyć zapytania przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Metoda niestandardowe osi `StreamRootChildDoc`, to metoda, która jest przeznaczona specjalnie do odczytu dokumentu, który zawiera powtarzające się `Child` elementu.  
  
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
  
 W tym przykładzie dokument źródłowy jest bardzo mały. Jednak nawet wtedy, gdy było milionów `Child` elementów, w tym przykładzie nadal będzie miał zużycie pamięci.  
  