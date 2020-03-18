---
title: Jak wykonać strumieniowe przekształcenia tekstu do języka XML (C#)
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 496535b7f868095a62be2b72b1eea2b082e00a44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345792"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Jak wykonać strumieniowe przekształcenia tekstu do języka XML (C#)

Jednym z podejść do przetwarzania pliku tekstowego jest napisanie metody rozszerzenia, `yield return` która przesyła strumieniowo plik tekstowy wiersza w czasie przy użyciu konstrukcji. Następnie można napisać kwerendę LINQ, która przetwarza plik tekstowy w sposób leniwy odroczonego. Jeśli następnie <xref:System.Xml.Linq.XStreamingElement> użyć do strumienia danych wyjściowych, następnie można utworzyć transformację z pliku tekstowego do XML, który używa minimalnej ilości pamięci, niezależnie od rozmiaru pliku tekstowego źródłowego.

 Istnieją pewne zastrzeżenia dotyczące przekształceń przesyłania strumieniowego. Transformacja przesyłania strumieniowego jest najlepiej stosowana w sytuacjach, w których można przetworzyć cały plik raz i jeśli można przetworzyć wiersze w kolejności, w jakiej występują w dokumencie źródłowym. Jeśli musisz przetworzyć plik więcej niż jeden raz lub jeśli musisz posortować wiersze, zanim będzie można je przetworzyć, stracisz wiele korzyści z używania techniki przesyłania strumieniowego.

## <a name="example"></a>Przykład

 Poniższy plik tekstowy, People.txt, jest źródłem tego przykładu.

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
