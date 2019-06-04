---
title: 'Instrukcje: Debugowanie zestawów wyników zapytania (C#)'
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: ba82e37ef4f57c78e7ba66676ba90312c2a9400f
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485764"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="a8575-102">Instrukcje: Debugowanie zestawów wyników zapytania (C#)</span><span class="sxs-lookup"><span data-stu-id="a8575-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="a8575-103">Jedną z najbardziej typowych problemów podczas wykonywania zapytań dotyczących drzew XML jest, że jeśli drzewa XML ma domyślny obszar nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie znajdowały się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a8575-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="a8575-104">Pierwszy zestaw przykładów w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest ładowany i jest wykonywane zapytanie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a8575-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="a8575-105">Drugi zestaw przykładach pokazano niezbędnych poprawek, dzięki czemu można tworzyć zapytania XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a8575-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="a8575-106">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a8575-106">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8575-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8575-107">Example</span></span>  
 <span data-ttu-id="a8575-108">Ten przykład przedstawia tworzenie XML w przestrzeni nazw i ustaw zapytania, które zwraca żadnego wyniku.</span><span class="sxs-lookup"><span data-stu-id="a8575-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="a8575-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="a8575-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="a8575-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8575-110">Example</span></span>  
 <span data-ttu-id="a8575-111">Ten przykład przedstawia tworzenie XML w przestrzeni nazw i zapytanie, które są poprawnie kodowane.</span><span class="sxs-lookup"><span data-stu-id="a8575-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="a8575-112">Rozwiązanie jest do zadeklarowania i zainicjowania <xref:System.Xml.Linq.XNamespace> obiektu i z niej korzystać, podczas określania <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a8575-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="a8575-113">W tym przypadku argument <xref:System.Xml.Linq.XContainer.Elements%2A> metodą jest <xref:System.Xml.Linq.XName> obiektu.</span><span class="sxs-lookup"><span data-stu-id="a8575-113">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
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
  
 <span data-ttu-id="a8575-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="a8575-114">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
