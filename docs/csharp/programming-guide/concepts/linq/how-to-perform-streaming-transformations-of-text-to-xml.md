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
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="fb0cb-103">Jak wykonywać transformacje strumieniowe tekstu do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fb0cb-103">How to perform streaming transformations of text to XML (C#)</span></span>

<span data-ttu-id="fb0cb-104">Jednym z metod przetwarzania pliku tekstowego jest zapisanie metody rozszerzenia, która przesyła strumieniowo plik tekstowy w czasie przy użyciu `yield return` konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="fb0cb-104">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="fb0cb-105">Następnie można napisać zapytanie LINQ, które przetwarza plik tekstowy w opóźniony sposób.</span><span class="sxs-lookup"><span data-stu-id="fb0cb-105">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="fb0cb-106">Jeśli następnie używasz <xref:System.Xml.Linq.XStreamingElement> do przesyłania strumieniowego danych wyjściowych, możesz utworzyć transformację z pliku tekstowego w formacie XML, który używa minimalnej ilości pamięci, niezależnie od rozmiaru źródłowego pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="fb0cb-106">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>

 <span data-ttu-id="fb0cb-107">Istnieją pewne zastrzeżenia dotyczące transformacji przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="fb0cb-107">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="fb0cb-108">Transformacja przesyłania strumieniowego jest najlepiej stosowana w sytuacjach, w których można przetwarzać cały plik jeden raz, a także przetwarzać linie w kolejności, w której występują w dokumencie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="fb0cb-108">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="fb0cb-109">Jeśli trzeba przetworzyć plik więcej niż raz lub trzeba posortować wiersze przed ich przetworzeniem, utracisz wiele korzyści wynikających z używania techniki przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="fb0cb-109">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>

## <a name="example"></a><span data-ttu-id="fb0cb-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="fb0cb-110">Example</span></span>

 <span data-ttu-id="fb0cb-111">Następujący plik tekstowy, People.txt, jest źródłem dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="fb0cb-111">The following text file, People.txt, is the source for this example.</span></span>

```text
#This is a comment
1,Tai,Yee,Writer
2,Nikolay,Grachev,Programmer
3,David,Wright,Inventor
```

 <span data-ttu-id="fb0cb-112">Poniższy kod zawiera metodę rozszerzenia, która przesyła strumieniowo wiersze pliku tekstowego w sposób odroczony.</span><span class="sxs-lookup"><span data-stu-id="fb0cb-112">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>

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

 <span data-ttu-id="fb0cb-113">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fb0cb-113">This example produces the following output:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fb0cb-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb0cb-114">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
