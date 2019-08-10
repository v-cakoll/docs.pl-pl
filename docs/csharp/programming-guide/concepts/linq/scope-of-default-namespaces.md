---
title: Zakres domyślnych przestrzeni nazw w języku C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 0c5f5cccda6ba6a75a8631ed095921b90b02916b
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868869"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="f207a-102">Zakres domyślnych przestrzeni nazw w języku C\#</span><span class="sxs-lookup"><span data-stu-id="f207a-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="f207a-103">Domyślne przestrzenie nazw reprezentowane w drzewie XML nie znajdują się w zakresie zapytań.</span><span class="sxs-lookup"><span data-stu-id="f207a-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="f207a-104">Jeśli masz kod XML, który znajduje się w domyślnym obszarze nazw, nadal musisz zadeklarować <xref:System.Xml.Linq.XNamespace> zmienną i połączyć ją z nazwą lokalną, aby określić kwalifikowaną nazwę do użycia w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="f207a-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="f207a-105">Jednym z najczęstszych problemów związanych z kwerendą drzewa XML jest to, że jeśli drzewo XML ma domyślną przestrzeń nazw, deweloper czasami zapisuje zapytanie tak, jakby kod XML nie był w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f207a-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="f207a-106">Pierwszy zestaw przykładów w tym temacie przedstawia typowy sposób ładowania kodu XML w domyślnej przestrzeni nazw, ale jest ono nieprawidłowo wykonywane.</span><span class="sxs-lookup"><span data-stu-id="f207a-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="f207a-107">Drugi zestaw przykładów pokazuje niezbędne poprawki, aby można było zbadać kod XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f207a-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f207a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="f207a-108">Example</span></span>  
 <span data-ttu-id="f207a-109">Ten przykład pokazuje tworzenie XML w przestrzeni nazw i zapytanie zwracające pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="f207a-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f207a-110">Kod</span><span class="sxs-lookup"><span data-stu-id="f207a-110">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a><span data-ttu-id="f207a-111">Komentarze</span><span class="sxs-lookup"><span data-stu-id="f207a-111">Comments</span></span>  
 <span data-ttu-id="f207a-112">Ten przykład generuje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="f207a-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="f207a-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f207a-113">Example</span></span>  
 <span data-ttu-id="f207a-114">Ten przykład pokazuje tworzenie kodu XML w przestrzeni nazw oraz zakodowane prawidłowo zapytanie.</span><span class="sxs-lookup"><span data-stu-id="f207a-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="f207a-115">W odróżnieniu od nieprawidłowo zakodowanego przykładu, poprawne podejście podczas C# korzystania z programu polega na zadeklarowaniu i zainicjowaniu <xref:System.Xml.Linq.XNamespace> obiektu oraz użyciu go podczas określania <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f207a-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="f207a-116">W tym przypadku argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody <xref:System.Xml.Linq.XName> jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="f207a-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f207a-117">Kod</span><span class="sxs-lookup"><span data-stu-id="f207a-117">Code</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
### <a name="comments"></a><span data-ttu-id="f207a-118">Komentarze</span><span class="sxs-lookup"><span data-stu-id="f207a-118">Comments</span></span>  
 <span data-ttu-id="f207a-119">Ten przykład generuje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="f207a-119">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="f207a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f207a-120">See also</span></span>

- [<span data-ttu-id="f207a-121">Przegląd przestrzeni nazw (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="f207a-121">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
