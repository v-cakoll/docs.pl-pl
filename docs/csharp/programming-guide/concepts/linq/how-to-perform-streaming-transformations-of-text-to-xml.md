---
title: 'Instrukcje: Wykonaj przekształcenia strumieniowe tekstu do pliku XMLC#()'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: 1507c628731a11e06c73f253c1a0c0f9a85a2269
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253525"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="b45e1-102">Instrukcje: Wykonaj przekształcenia strumieniowe tekstu do pliku XMLC#()</span><span class="sxs-lookup"><span data-stu-id="b45e1-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="b45e1-103">Jednym z metod przetwarzania pliku tekstowego jest zapisanie metody rozszerzenia, która przesyła strumieniowo plik tekstowy w czasie przy użyciu `yield return` konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="b45e1-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="b45e1-104">Następnie można napisać zapytanie LINQ, które przetwarza plik tekstowy w opóźniony sposób.</span><span class="sxs-lookup"><span data-stu-id="b45e1-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="b45e1-105">Jeśli następnie <xref:System.Xml.Linq.XStreamingElement> używasz do przesyłania strumieniowego danych wyjściowych, możesz utworzyć transformację z pliku tekstowego w formacie XML, który używa minimalnej ilości pamięci, niezależnie od rozmiaru źródłowego pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="b45e1-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="b45e1-106">Istnieją pewne zastrzeżenia dotyczące transformacji przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="b45e1-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="b45e1-107">Transformacja przesyłania strumieniowego jest najlepiej stosowana w sytuacjach, w których można przetwarzać cały plik jeden raz, a także przetwarzać linie w kolejności, w której występują w dokumencie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="b45e1-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="b45e1-108">Jeśli trzeba przetworzyć plik więcej niż raz lub trzeba posortować wiersze przed ich przetworzeniem, utracisz wiele korzyści wynikających z używania techniki przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="b45e1-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b45e1-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="b45e1-109">Example</span></span>  
 <span data-ttu-id="b45e1-110">Następujący plik tekstowy, ludzie. txt, jest źródłem dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b45e1-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```text  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="b45e1-111">Poniższy kod zawiera metodę rozszerzenia, która przesyła strumieniowo wiersze pliku tekstowego w sposób odroczony.</span><span class="sxs-lookup"><span data-stu-id="b45e1-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
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
  
 <span data-ttu-id="b45e1-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="b45e1-112">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b45e1-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b45e1-113">See also</span></span>

- <xref:System.Xml.Linq.XStreamingElement>
