---
title: Jak wykonać przekształcenia strumieniowe tekstu do pliku XML (C#)
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 496535b7f868095a62be2b72b1eea2b082e00a44
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345792"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Jak wykonać przekształcenia strumieniowe tekstu do pliku XML (C#)

Jednym z metod przetwarzania pliku tekstowego jest zapisanie metody rozszerzającej, która strumieniuje plik tekstowy w wierszu przy użyciu konstrukcji `yield return`. Następnie można napisać zapytanie LINQ, które przetwarza plik tekstowy w opóźniony sposób. Jeśli następnie używasz <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego danych wyjściowych, możesz utworzyć transformację z pliku tekstowego w formacie XML, który używa minimalnej ilości pamięci, niezależnie od rozmiaru źródłowego pliku tekstowego.

 Istnieją pewne zastrzeżenia dotyczące transformacji przesyłania strumieniowego. Transformacja przesyłania strumieniowego jest najlepiej stosowana w sytuacjach, w których można przetwarzać cały plik jeden raz, a także przetwarzać linie w kolejności, w której występują w dokumencie źródłowym. Jeśli trzeba przetworzyć plik więcej niż raz lub trzeba posortować wiersze przed ich przetworzeniem, utracisz wiele korzyści wynikających z używania techniki przesyłania strumieniowego.

## <a name="example"></a>Przykład

 Następujący plik tekstowy, ludzie. txt, jest źródłem dla tego przykładu.

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XStreamingElement>
