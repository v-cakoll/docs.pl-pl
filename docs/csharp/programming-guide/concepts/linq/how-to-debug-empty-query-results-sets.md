---
title: Jak debugować puste zestawy wyników kwerendy (C#)
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 2716f7c525ac6bee8d2fb374e4ecc4c975d852a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141293"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="3ada1-102">Jak debugować puste zestawy wyników kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="3ada1-102">How to debug empty query results sets (C#)</span></span>
<span data-ttu-id="3ada1-103">Jednym z najczęstszych problemów podczas wykonywania zapytań drzew XML jest to, że jeśli drzewo XML ma domyślny obszar nazw, deweloper czasami zapisuje kwerendę tak, jakby XML nie znajdował się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3ada1-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="3ada1-104">Pierwszy zestaw przykładów w tym temacie pokazuje typowy sposób, że XML w domyślnym obszarze nazw jest ładowany i jest przeszukiwany nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="3ada1-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="3ada1-105">Drugi zestaw przykładów pokazuje niezbędne poprawki, dzięki czemu można wysyłać zapytania do języka XML w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="3ada1-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="3ada1-106">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3ada1-106">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ada1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ada1-107">Example</span></span>  
 <span data-ttu-id="3ada1-108">W tym przykładzie przedstawiono tworzenie języka XML w obszarze nazw i kwerendę, która zwraca pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="3ada1-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="3ada1-109">W tym przykładzie daje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="3ada1-109">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="3ada1-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="3ada1-110">Example</span></span>  
 <span data-ttu-id="3ada1-111">W tym przykładzie przedstawiono tworzenie języka XML w obszarze nazw i kwerendę, która jest poprawnie zakodowana.</span><span class="sxs-lookup"><span data-stu-id="3ada1-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="3ada1-112">Rozwiązaniem jest zadeklarowanie i zainicjowanie <xref:System.Xml.Linq.XNamespace> obiektu oraz użycie go <xref:System.Xml.Linq.XName> podczas określania obiektów.</span><span class="sxs-lookup"><span data-stu-id="3ada1-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="3ada1-113">W takim przypadku argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody jest <xref:System.Xml.Linq.XName> obiektem.</span><span class="sxs-lookup"><span data-stu-id="3ada1-113">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
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
  
 <span data-ttu-id="3ada1-114">W tym przykładzie daje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="3ada1-114">This example produces the following result:</span></span>  
  
```output  
Result set follows:  
1  
2  
3  
End of result set  
```  
