---
title: Zakres domyślnych przestrzeni nazw w języku C#
ms.date: 07/20/2015
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 7615351f6e5f8b18bd6466a83d54aa65a6c99b50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253041"
---
# <a name="scope-of-default-namespaces-in-c"></a><span data-ttu-id="b679b-102">Zakres domyślnych obszarów nazw w języku C\#</span><span class="sxs-lookup"><span data-stu-id="b679b-102">Scope of Default Namespaces in C\#</span></span>
<span data-ttu-id="b679b-103">Domyślne obszary nazw reprezentowane w drzewie XML nie znajdują się w zakresie kwerend.</span><span class="sxs-lookup"><span data-stu-id="b679b-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="b679b-104">Jeśli masz XML, który znajduje się w domyślnym <xref:System.Xml.Linq.XNamespace> obszarze nazw, nadal należy zadeklarować zmienną i połączyć ją z nazwą lokalną, aby kwalifikowana nazwa była używana w kwerendzie.</span><span class="sxs-lookup"><span data-stu-id="b679b-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="b679b-105">Jednym z najczęstszych problemów podczas wykonywania zapytań drzew XML jest to, że jeśli drzewo XML ma domyślny obszar nazw, deweloper czasami zapisuje kwerendę tak, jakby XML nie znajdował się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b679b-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="b679b-106">Pierwszy zestaw przykładów w tym temacie pokazuje typowy sposób, że XML w domyślnym obszarze nazw jest ładowany, ale jest przeszukiwany nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="b679b-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="b679b-107">Drugi zestaw przykładów pokazuje niezbędne poprawki, dzięki czemu można wysyłać zapytania do języka XML w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="b679b-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b679b-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="b679b-108">Example</span></span>  
 <span data-ttu-id="b679b-109">W tym przykładzie przedstawiono utworzenie języka XML w obszarze nazw i kwerendę, która zwraca pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="b679b-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b679b-110">Code</span><span class="sxs-lookup"><span data-stu-id="b679b-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="b679b-111">Komentarze</span><span class="sxs-lookup"><span data-stu-id="b679b-111">Comments</span></span>  
 <span data-ttu-id="b679b-112">W tym przykładzie daje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="b679b-112">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="b679b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="b679b-113">Example</span></span>  
 <span data-ttu-id="b679b-114">W tym przykładzie przedstawiono tworzenie języka XML w obszarze nazw i kwerendę, która jest poprawnie zakodowana.</span><span class="sxs-lookup"><span data-stu-id="b679b-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="b679b-115">W przeciwieństwie do niepoprawnie zakodowane powyżej, poprawne podejście podczas korzystania z <xref:System.Xml.Linq.XNamespace> Języka C# jest zadeklarować <xref:System.Xml.Linq.XName> i zainicjować obiekt i używać go podczas określania obiektów.</span><span class="sxs-lookup"><span data-stu-id="b679b-115">In contrast to the incorrectly coded example above, the correct approach when using C# is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="b679b-116">W takim przypadku argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody jest <xref:System.Xml.Linq.XName> obiektem.</span><span class="sxs-lookup"><span data-stu-id="b679b-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b679b-117">Code</span><span class="sxs-lookup"><span data-stu-id="b679b-117">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="b679b-118">Komentarze</span><span class="sxs-lookup"><span data-stu-id="b679b-118">Comments</span></span>  
 <span data-ttu-id="b679b-119">W tym przykładzie daje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="b679b-119">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="b679b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b679b-120">See also</span></span>

- [<span data-ttu-id="b679b-121">Omówienie przestrzeni nazw (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="b679b-121">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
