---
title: 'Porady: wykonania przesyłania strumieniowego przekształcenia tekstu do pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 4313c5263b6a219ec3c8d05a7b7938c41c7cc028
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Porady: wykonania przesyłania strumieniowego przekształcenia tekstu do pliku XML (C#)
Jeden ze sposobów przetwarzania pliku tekstowego służy do zapisania — metoda rozszerzenia pliku tekstowego strumieni linii w czasie przy użyciu `yield return` utworzenia. Następnie można pisać zapytania LINQ, który przetwarza w pliku tekstowym w sposób odroczonego opóźnieniem. Jeśli następnie użyć <xref:System.Xml.Linq.XStreamingElement> do strumienia wyjściowego, następnie utworzyć transformację z pliku tekstowego z kod XML, który używa minimalnej ilości pamięci, niezależnie od rozmiaru pliku źródłowego.  
  
 Istnieją pewne ostrzeżenia dotyczące przesyłania strumieniowego przekształcenia. Transformację przesyłania strumieniowego najlepiej jest stosowane w sytuacji, w którym można przetwarzać cały plik po i może przetwarzać wierszy w kolejności występowania w dokumencie źródłowym. Jeśli masz więcej niż raz przetworzyć pliku lub jeśli zajdzie potrzeba sortowania wierszy przed ich przetwarzania, utracisz wiele korzyści wynikające ze stosowania technik przesyłania strumieniowego.  
  
## <a name="example"></a>Przykład  
 Następujący plik tekstowy, People.txt, jest źródła w ramach tego przykładu.  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 Poniższy kod zawiera metody rozszerzenia, które wiersze w pliku tekstowym w sposób odroczonego strumieni.  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XStreamingElement>  
 [Zaawansowane techniki zapytania (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
