---
title: "Porady: wykonania przesyłania strumieniowego przekształcenia tekstu do pliku XML (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03c5ed5ef66db311ade751b5aad21de70b78f063
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a><span data-ttu-id="fc136-102">Porady: wykonania przesyłania strumieniowego przekształcenia tekstu do pliku XML (C#)</span><span class="sxs-lookup"><span data-stu-id="fc136-102">How to: Perform Streaming Transformations of Text to XML (C#)</span></span>
<span data-ttu-id="fc136-103">Jeden ze sposobów przetwarzania pliku tekstowego służy do zapisania — metoda rozszerzenia pliku tekstowego strumieni linii w czasie przy użyciu `yield return` utworzenia.</span><span class="sxs-lookup"><span data-stu-id="fc136-103">One approach to processing a text file is to write an extension method that streams the text file a line at a time using the `yield return` construct.</span></span> <span data-ttu-id="fc136-104">Następnie można pisać zapytania LINQ, który przetwarza w pliku tekstowym w sposób odroczonego opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="fc136-104">You then can write a LINQ query that processes the text file in a lazy deferred fashion.</span></span> <span data-ttu-id="fc136-105">Jeśli następnie użyć <xref:System.Xml.Linq.XStreamingElement> do strumienia wyjściowego, następnie utworzyć transformację z pliku tekstowego z kod XML, który używa minimalnej ilości pamięci, niezależnie od rozmiaru pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="fc136-105">If you then use <xref:System.Xml.Linq.XStreamingElement> to stream output, you then can create a transformation from the text file to XML that uses a minimal amount of memory, regardless of the size of the source text file.</span></span>  
  
 <span data-ttu-id="fc136-106">Istnieją pewne ostrzeżenia dotyczące przesyłania strumieniowego przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="fc136-106">There are some caveats regarding streaming transformations.</span></span> <span data-ttu-id="fc136-107">Transformację przesyłania strumieniowego najlepiej jest stosowane w sytuacji, w którym można przetwarzać cały plik po i może przetwarzać wierszy w kolejności występowania w dokumencie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="fc136-107">A streaming transformation is best applied in situations where you can process the entire file once, and if you can process the lines in the order that they occur in the source document.</span></span> <span data-ttu-id="fc136-108">Jeśli masz więcej niż raz przetworzyć pliku lub jeśli zajdzie potrzeba sortowania wierszy przed ich przetwarzania, utracisz wiele korzyści wynikające ze stosowania technik przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="fc136-108">If you have to process the file more than once, or if you have to sort the lines before you can process them, you will lose many of the benefits of using a streaming technique.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc136-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc136-109">Example</span></span>  
 <span data-ttu-id="fc136-110">Następujący plik tekstowy, People.txt, jest źródła w ramach tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="fc136-110">The following text file, People.txt, is the source for this example.</span></span>  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 <span data-ttu-id="fc136-111">Poniższy kod zawiera metody rozszerzenia, które wiersze w pliku tekstowym w sposób odroczonego strumieni.</span><span class="sxs-lookup"><span data-stu-id="fc136-111">The following code contains an extension method that streams the lines of the text file in a deferred fashion.</span></span>  
  
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
  
 <span data-ttu-id="fc136-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="fc136-112">This example produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc136-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc136-113">See Also</span></span>  
 <xref:System.Xml.Linq.XStreamingElement>  
 [<span data-ttu-id="fc136-114">Zaawansowane techniki zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="fc136-114">Advanced Query Techniques (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
