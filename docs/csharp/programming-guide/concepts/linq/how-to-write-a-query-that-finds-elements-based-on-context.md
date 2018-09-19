---
title: 'Porady: pisanie zapytania odnajdującego elementy na podstawie kontekstu (C#)'
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: c1c43bc47df1612be26c78351a9d30272a020160
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45987958"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="c8958-102">Porady: pisanie zapytania odnajdującego elementy na podstawie kontekstu (C#)</span><span class="sxs-lookup"><span data-stu-id="c8958-102">How to: Write a Query that Finds Elements Based on Context (C#)</span></span>
<span data-ttu-id="c8958-103">Czasami może być napisać zapytanie wybierające elementy na podstawie ich kontekstu.</span><span class="sxs-lookup"><span data-stu-id="c8958-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="c8958-104">Można filtrować na podstawie poprzedzające lub następujące elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="c8958-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="c8958-105">Można filtrować na podstawie podrzędnej lub elementów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c8958-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="c8958-106">Można to zrobić przez napisanie zapytania i używanie wyniki zapytania w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c8958-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="c8958-107">Jeśli musisz najpierw testujemy współpracę z wartością null, a następnie sprawdź wartość, jest bardziej wygodne wykonać zapytanie w `let` klauzuli, a następnie użyć wyników w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c8958-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8958-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8958-108">Example</span></span>  
 <span data-ttu-id="c8958-109">Poniższy przykład powoduje zaznaczenie wszystkich `p` elementy, które są od razu następuje `ul` elementu.</span><span class="sxs-lookup"><span data-stu-id="c8958-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants("p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name.LocalName == "ul"  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="c8958-110">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="c8958-110">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="c8958-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8958-111">Example</span></span>  
 <span data-ttu-id="c8958-112">Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c8958-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c8958-113">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="c8958-113">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
```csharp  
XElement doc = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
    <p id=""1""/>  
    <ul>abc</ul>  
    <Child>  
        <p id=""2""/>  
        <notul/>  
        <p id=""3""/>  
        <ul>def</ul>  
        <p id=""4""/>  
    </Child>  
    <Child>  
        <p id=""5""/>  
        <notul/>  
        <p id=""6""/>  
        <ul>abc</ul>  
        <p id=""7""/>  
    </Child>  
</Root>");  
  
XNamespace ad = "http://www.adatum.com";  
  
IEnumerable<XElement> items =  
    from e in doc.Descendants(ad + "p")  
    let z = e.ElementsAfterSelf().FirstOrDefault()  
    where z != null && z.Name == ad.GetName("ul")  
    select e;  
  
foreach (XElement e in items)  
    Console.WriteLine("id = {0}", (string)e.Attribute("id"));  
```  
  
 <span data-ttu-id="c8958-114">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="c8958-114">This code produces the following output:</span></span>  
  
```  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8958-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8958-115">See Also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>  
- <xref:System.Xml.Linq.XContainer.Descendants%2A>  
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>  
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>  
- [<span data-ttu-id="c8958-116">Podstawowe zapytania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c8958-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
