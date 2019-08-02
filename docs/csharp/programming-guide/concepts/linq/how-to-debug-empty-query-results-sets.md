---
title: 'Instrukcje: Debuguj puste zestawy wyników zapytania (C#)'
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: 06c878a7751a14a3043b450d9242037ca91ad754
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710128"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="eecd0-102">Instrukcje: Debuguj puste zestawy wyników zapytania (C#)</span><span class="sxs-lookup"><span data-stu-id="eecd0-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="eecd0-103">Jednym z najczęstszych problemów związanych z kwerendą drzewa XML jest to, że jeśli drzewo XML ma domyślną przestrzeń nazw, deweloper czasami zapisuje zapytanie tak, jakby kod XML nie był w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="eecd0-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="eecd0-104">Pierwszy zestaw przykładów w tym temacie przedstawia typowy sposób ładowania kodu XML w domyślnej przestrzeni nazw i jest on nieprawidłowo przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="eecd0-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="eecd0-105">Drugi zestaw przykładów pokazuje niezbędne poprawki, aby można było zbadać kod XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="eecd0-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="eecd0-106">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="eecd0-106">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eecd0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="eecd0-107">Example</span></span>  
 <span data-ttu-id="eecd0-108">Ten przykład pokazuje tworzenie XML w przestrzeni nazw i zapytanie zwracające pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="eecd0-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="eecd0-109">Ten przykład generuje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="eecd0-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="eecd0-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="eecd0-110">Example</span></span>  
 <span data-ttu-id="eecd0-111">Ten przykład pokazuje tworzenie kodu XML w przestrzeni nazw oraz zakodowane prawidłowo zapytanie.</span><span class="sxs-lookup"><span data-stu-id="eecd0-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="eecd0-112">Rozwiązaniem jest zadeklarowanie i zainicjowanie <xref:System.Xml.Linq.XNamespace> obiektu oraz użycie go podczas określania <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="eecd0-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="eecd0-113">W tym przypadku argument <xref:System.Xml.Linq.XContainer.Elements%2A> metody <xref:System.Xml.Linq.XName> jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="eecd0-113">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
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
  
 <span data-ttu-id="eecd0-114">Ten przykład generuje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="eecd0-114">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
