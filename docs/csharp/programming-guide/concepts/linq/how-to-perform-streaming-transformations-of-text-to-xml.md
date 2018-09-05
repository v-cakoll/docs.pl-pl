---
title: 'Porady: wykonywanie przekształceń strumieniowych tekstu do pliku XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 98fa8bd9ae393e9c87b67ae3f2874a2c279415af
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526950"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Porady: wykonywanie przekształceń strumieniowych tekstu do pliku XML (C#)
Jedno z podejść do przetwarzania pliku tekstowego jest napisanie metody rozszerzenia, która przesyła strumieniowo plik tekstowy linię w chwili `yield return` konstruowania. Następnie można napisać zapytanie LINQ, która przetwarza plik tekstowy, który w sposób odroczonego z opóźnieniem. Jeśli używasz <xref:System.Xml.Linq.XStreamingElement> do strumienia wyjściowego, będzie można utworzyć przekształcenie z pliku tekstowego do pliku XML, który używa minimalnej ilości pamięci, bez względu na rozmiar do źródłowego pliku tekstowego.  
  
 Istnieją pewne zastrzeżenia dotyczące przekształceń strumieniowych. Przekształcenie przesyłania strumieniowego najlepiej jest stosowany w sytuacjach, w którym może przetwarzać cały plik po i może przetwarzać wierszy w kolejności występowania w dokumencie źródłowym. Jeśli masz więcej niż jeden raz przetworzyć pliku lub jeśli trzeba posortować wiersze przed ich przetwarzania, utracisz wiele korzyści z używania przesyłania strumieniowego techniki.  
  
## <a name="example"></a>Przykład  
 W następującym pliku tekstowym People.txt, jest źródłem w tym przykładzie.  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 Poniższy kod zawiera metodę rozszerzenia, która przesyła strumieniowo wierszy w pliku tekstowym w sposób odroczone.  
  
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

- <xref:System.Xml.Linq.XStreamingElement>  
- [Zaawansowane techniki zapytań (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
