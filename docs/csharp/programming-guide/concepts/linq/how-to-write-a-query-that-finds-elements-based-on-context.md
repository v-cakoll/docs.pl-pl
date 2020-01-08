---
title: Jak napisać zapytanie, które znajduje elementy na podstawie kontekstu (C#)
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 3fc131fdeb8dbf8871bfa455bc54eab0eeca7022
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348364"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="d9ee7-102">Jak napisać zapytanie, które znajduje elementy na podstawie kontekstu (C#)</span><span class="sxs-lookup"><span data-stu-id="d9ee7-102">How to write a query that finds elements based on context (C#)</span></span>
<span data-ttu-id="d9ee7-103">Czasami może być konieczne zapisanie zapytania, które wybiera elementy na podstawie ich kontekstu.</span><span class="sxs-lookup"><span data-stu-id="d9ee7-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="d9ee7-104">Można filtrować na podstawie poprzedzających lub następujących elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="d9ee7-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="d9ee7-105">Można filtrować na podstawie elementów podrzędnych lub nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="d9ee7-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="d9ee7-106">Można to zrobić przez zapisanie zapytania i użycie wyników zapytania w klauzuli `where`.</span><span class="sxs-lookup"><span data-stu-id="d9ee7-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="d9ee7-107">Jeśli konieczne jest pierwsze przetestowanie na wartość null, a następnie przetestowanie wartości, bardziej wygodne jest wykonanie zapytania w klauzuli `let`, a następnie użycie wyników w klauzuli `where`.</span><span class="sxs-lookup"><span data-stu-id="d9ee7-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9ee7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9ee7-108">Example</span></span>  
 <span data-ttu-id="d9ee7-109">Poniższy przykład zaznacza wszystkie elementy `p`, po których bezpośrednio następuje element `ul`.</span><span class="sxs-lookup"><span data-stu-id="d9ee7-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="d9ee7-110">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d9ee7-110">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="d9ee7-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9ee7-111">Example</span></span>  
 <span data-ttu-id="d9ee7-112">W poniższym przykładzie pokazano to samo zapytanie dla kodu XML, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d9ee7-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="d9ee7-113">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d9ee7-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="d9ee7-114">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="d9ee7-114">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9ee7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9ee7-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
