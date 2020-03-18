---
title: Jak napisać kwerendę, która znajduje elementy na podstawie kontekstu (C#)
ms.date: 07/20/2015
ms.assetid: 3ff79ef0-fc8b-42fe-8cc0-10dc32b06b4e
ms.openlocfilehash: 3fc131fdeb8dbf8871bfa455bc54eab0eeca7022
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75348364"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-c"></a><span data-ttu-id="91001-102">Jak napisać kwerendę, która znajduje elementy na podstawie kontekstu (C#)</span><span class="sxs-lookup"><span data-stu-id="91001-102">How to write a query that finds elements based on context (C#)</span></span>
<span data-ttu-id="91001-103">Czasami może być trzeba napisać kwerendę, która wybiera elementy na podstawie ich kontekstu.</span><span class="sxs-lookup"><span data-stu-id="91001-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="91001-104">Można filtrować na podstawie poprzednich lub następujących elementów równorzędnych.</span><span class="sxs-lookup"><span data-stu-id="91001-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="91001-105">Można filtrować na podstawie elementów podrzędnych lub elementów przodka.</span><span class="sxs-lookup"><span data-stu-id="91001-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="91001-106">Można to zrobić, pisząc kwerendę i przy użyciu `where` wyników kwerendy w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="91001-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="91001-107">Jeśli trzeba najpierw przetestować przed null, a następnie przetestować wartość, jest `let` bardziej wygodne do wykonania `where` kwerendy w klauzuli, a następnie użyć wyników w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="91001-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91001-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="91001-108">Example</span></span>  
 <span data-ttu-id="91001-109">W poniższym przykładzie `p` zaznaczono wszystkie `ul` elementy, po których natychmiast następuje element.</span><span class="sxs-lookup"><span data-stu-id="91001-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
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
  
 <span data-ttu-id="91001-110">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="91001-110">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="91001-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="91001-111">Example</span></span>  
 <span data-ttu-id="91001-112">W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="91001-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="91001-113">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="91001-113">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="91001-114">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="91001-114">This code produces the following output:</span></span>  
  
```output  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="91001-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91001-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
