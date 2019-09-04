---
title: 'Instrukcje: Napisz zapytanie, które znajduje elementy na podstawie kontekstu (C#)'
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: e3ac8fc965132521b85cce6391908634cdb17127
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253216"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="0cdce-102">Instrukcje: Napisz zapytanie, które znajduje elementy na podstawie kontekstu (C#)</span><span class="sxs-lookup"><span data-stu-id="0cdce-102">How to: Write a Query that Finds Elements Based on Context (C#)</span></span>
<span data-ttu-id="0cdce-103">Czasami może być konieczne zapisanie zapytania, które wybiera elementy na podstawie ich kontekstu.</span><span class="sxs-lookup"><span data-stu-id="0cdce-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="0cdce-104">Można filtrować na podstawie poprzedzających lub następujących elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="0cdce-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="0cdce-105">Można filtrować na podstawie elementów podrzędnych lub nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="0cdce-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="0cdce-106">Można to zrobić przez zapisanie zapytania i użycie wyników zapytania w `where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0cdce-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="0cdce-107">Jeśli konieczne jest pierwsze przetestowanie na wartość null, a następnie przetestowanie wartości, bardziej wygodne jest wykonanie zapytania w `let` klauzuli, a następnie użycie wyników `where` w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0cdce-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cdce-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0cdce-108">Example</span></span>  
 <span data-ttu-id="0cdce-109">W poniższym przykładzie wybrano `p` wszystkie elementy, które są bezpośrednio następuje `ul` po elemencie.</span><span class="sxs-lookup"><span data-stu-id="0cdce-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="0cdce-110">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0cdce-110">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="0cdce-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0cdce-111">Example</span></span>  
 <span data-ttu-id="0cdce-112">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0cdce-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="0cdce-113">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0cdce-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="0cdce-114">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0cdce-114">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cdce-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0cdce-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
