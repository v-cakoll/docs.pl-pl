---
title: 'Porady: strumienia fragmenty XML z element XmlReader (C#)'
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: 8e2baed3ca32ea4273993fe5bed43fef768204ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321067"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Porady: strumienia fragmenty XML z element XmlReader (C#)
Podczas przetwarzania dużych plików XML, może nie być możliwe do załadowania całego drzewa XML do pamięci. W tym temacie przedstawiono sposób strumienia fragmenty przy użyciu <xref:System.Xml.XmlReader>.  
  
 Jedną z najbardziej skutecznych sposobów użycia <xref:System.Xml.XmlReader> odczytać <xref:System.Xml.Linq.XElement> obiektów jest napisanie własnej metody niestandardowe osi. Metoda osi takich jak zwykle zwraca kolekcję <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, jak pokazano w przykładzie w tym temacie. W metodzie niestandardowych osi, po utworzeniu fragmentu XML przez wywołanie metody <xref:System.Xml.Linq.XNode.ReadFrom%2A> metody zwrócić przy użyciu kolekcji `yield return`. Zapewnia to wykonanie odroczone semantyki do metody niestandardowe osi.  
  
 Po utworzeniu drzewo XML z <xref:System.Xml.XmlReader> obiektu <xref:System.Xml.XmlReader> musi być umieszczony w elemencie. <xref:System.Xml.Linq.XNode.ReadFrom%2A> Nie może zwracać metoda dopóki odczyta tagu zamknięcia elementu.  
  
 Jeśli chcesz utworzyć drzewa częściowe, można utworzyć wystąpienia <xref:System.Xml.XmlReader>, umieść czytnik na węźle, który ma zostać przekonwertowany na <xref:System.Xml.Linq.XElement> drzewa, a następnie utwórz <xref:System.Xml.Linq.XElement> obiektu.  
  
 Temat [porady: strumień fragmenty XML z dostępem do informacji w nagłówku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-stream-xml-fragments-with-access-to-header-information.md) zawiera informacje i przykład dotyczące strumienia bardziej złożonych dokumentu.  
  
 Temat [porady: wykonaj przesyłania strumieniowego przekształcenie o dużych dokumentów XML (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-perform-streaming-transform-of-large-xml-documents.md) zawiera przykład LINQ do XML do transformacji dokumentów XML wyjątkowa przy zachowaniu zużycia pamięci.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie tworzy metodę niestandardowych osi. Odpytywaną przy użyciu [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania. Metody niestandardowe osi `StreamRootChildDoc`, to metoda, która jest zaprojektowany specjalnie w celu odczytu dokumentu, który zawiera powtarzające się `Child` elementu.  
  
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
  
 W tym przykładzie dokument źródłowy jest bardzo mała. Jednak nawet wtedy, gdy było miliony `Child` elementów, w tym przykładzie nadal będzie miał zużycie pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [Analiza kodu XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
