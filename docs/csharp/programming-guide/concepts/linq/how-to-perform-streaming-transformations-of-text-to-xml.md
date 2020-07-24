---
title: Jak wykonywać transformacje strumieniowe tekstu do pliku XML (C#)
description: Dowiedz się, jak wykonać transmisję strumienia tekstu do pliku XML w języku C#, gdzie można przesłać plik tekstowy w wierszu i użyć zapytania LINQ do przetworzenia pliku tekstowego.
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: f933064be70d39b59cf7dbe51b4ee92e5226647a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104750"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Jak wykonywać transformacje strumieniowe tekstu do pliku XML (C#)

Jednym z metod przetwarzania pliku tekstowego jest zapisanie metody rozszerzenia, która przesyła strumieniowo plik tekstowy w czasie przy użyciu `yield return` konstrukcji. Następnie można napisać zapytanie LINQ, które przetwarza plik tekstowy w opóźniony sposób. Jeśli następnie używasz <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego danych wyjściowych, możesz utworzyć transformację z pliku tekstowego w formacie XML, który używa minimalnej ilości pamięci, niezależnie od rozmiaru źródłowego pliku tekstowego.

 Istnieją pewne zastrzeżenia dotyczące transformacji przesyłania strumieniowego. Transformacja przesyłania strumieniowego jest najlepiej stosowana w sytuacjach, w których można przetwarzać cały plik jeden raz, a także przetwarzać linie w kolejności, w której występują w dokumencie źródłowym. Jeśli trzeba przetworzyć plik więcej niż raz lub trzeba posortować wiersze przed ich przetworzeniem, utracisz wiele korzyści wynikających z używania techniki przesyłania strumieniowego.

## <a name="example"></a>Przykład

 Następujący plik tekstowy, People.txt, jest źródłem dla tego przykładu.

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 Poniższy kod zawiera metodę rozszerzenia, która przesyła strumieniowo wiersze pliku tekstowego w sposób odroczony.

```csharp
public static class StreamReaderSequence
{
    public static IEnumerable<string> Lines(this StreamReader source)
    {
        if (source == null)
            throw new ArgumentNullException(nameof(source));

        string line;
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
        var sr = new StreamReader("People.txt");
        var xmlTree = new XStreamingElement("Root",
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
