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
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="ec25d-102">Porady: wykonywanie przekształceń strumieniowych tekstu do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ec25d-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="ec25d-103">Jedno z podejść do przetwarzania pliku tekstowego jest napisanie metody rozszerzenia, która przesyła strumieniowo plik tekstowy linię w chwili `yield return` konstruowania.</span><span class="sxs-lookup"><span data-stu-id="ec25d-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="ec25d-104">Następnie można napisać zapytanie LINQ, która przetwarza plik tekstowy, który w sposób odroczonego z opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="ec25d-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="ec25d-105">Jeśli używasz <xref:System.Xml.Linq.XStreamingElement> do strumienia wyjściowego, będzie można utworzyć przekształcenie z pliku tekstowego do pliku XML, który używa minimalnej ilości pamięci, bez względu na rozmiar do źródłowego pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="ec25d-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="ec25d-106">Istnieją pewne zastrzeżenia dotyczące przekształceń strumieniowych.</span><span class="sxs-lookup"><span data-stu-id="ec25d-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="ec25d-107">Przekształcenie przesyłania strumieniowego najlepiej jest stosowany w sytuacjach, w którym może przetwarzać cały plik po i może przetwarzać wierszy w kolejności występowania w dokumencie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="ec25d-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="ec25d-108">Jeśli masz więcej niż jeden raz przetworzyć pliku lub jeśli trzeba posortować wiersze przed ich przetwarzania, utracisz wiele korzyści z używania przesyłania strumieniowego techniki.</span><span class="sxs-lookup"><span data-stu-id="ec25d-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec25d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec25d-109">Example</span></span>  
 <span data-ttu-id="ec25d-110">W następującym pliku tekstowym People.txt, jest źródłem w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ec25d-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="ec25d-111">Poniższy kod zawiera metodę rozszerzenia, która przesyła strumieniowo wierszy w pliku tekstowym w sposób odroczone.</span><span class="sxs-lookup"><span data-stu-id="ec25d-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
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
  
 <span data-ttu-id="ec25d-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="ec25d-112">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec25d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec25d-113">See Also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>  
- [<span data-ttu-id="ec25d-114">Zaawansowane techniki zapytań (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="ec25d-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
