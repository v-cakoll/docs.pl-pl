---
title: 'Porady: Stream fragmentów kodu XML z elementu XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: cb3e9fbc9567593cdc77ae116273f4c0fede4af3
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195806"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Porady: Stream fragmentów kodu XML z elementu XmlReader (C#)
W przypadku przetwarzania dużych plików XML, może nie być możliwe do załadowania całego drzewa XML do pamięci. W tym temacie pokazano, jak przesyłać strumieniowo fragmentów przy użyciu <xref:System.Xml.XmlReader>.  
  
 Jedną z najbardziej skutecznych sposobów użycia <xref:System.Xml.XmlReader> odczytać <xref:System.Xml.Linq.XElement> obiektów jest napisanie własnej metody osi niestandardowych. Metody osi takich jak zwykle zwraca kolekcję <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie. W metodzie niestandardowej osi po utworzeniu XML fragment, wywołując <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody zwracają kolekcję przy użyciu `yield return`. Dzięki temu semantyki wykonanie odroczone do metody osi niestandardowych.  
  
 Podczas tworzenia drzewa XML z <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader> musi być umieszczony w elemencie. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Metoda nie zwraca, dopóki odczyta Zamknij tagu elementu.  
  
 Jeśli chcesz utworzyć drzewo częściowe, można utworzyć wystąpienie <xref:System.Xml.XmlReader>, umieść czytelnika na węźle, który chcesz przekonwertować <xref:System.Xml.Linq.XElement> drzewa, a następnie utwórz <xref:System.Xml.Linq.XElement> obiektu.  
  
 Temat [jak: Stream XML fragmentów z dostępem do informacji w nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i obejrzeć przykład do przesyłania strumieniowego bardziej złożonych dokumentów.  
  
 Temat [jak: wykonywać przesyłania strumieniowego Przekształcanie z dużymi dokumentami XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład korzystania z LINQ to XML do transformowania bardzo dużych dokumentów XML przy zachowaniu zużycie pamięci.  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Analizowanie kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
