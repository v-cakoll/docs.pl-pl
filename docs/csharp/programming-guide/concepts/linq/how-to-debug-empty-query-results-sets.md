---
title: "Porady: debugowanie zestawów wyników zapytania pusty (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f8fb77a65c2c5023685251435d3028ffa9b3c2b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-debug-empty-query-results-sets-c"></a><span data-ttu-id="28559-102">Porady: debugowanie zestawów wyników zapytania pusty (C#)</span><span class="sxs-lookup"><span data-stu-id="28559-102">How to: Debug Empty Query Results Sets (C#)</span></span>
<span data-ttu-id="28559-103">Jest jedną z najczęściej występujących problemów podczas wykonywania zapytania drzewa XML, że jeśli drzewo składni XML ma domyślnej przestrzeni nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie zostały w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="28559-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="28559-104">Pierwszy zestaw przykłady w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest załadowany czy jest poddawany kwerendzie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="28559-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="28559-105">Drugi zestaw przykładach niezbędnych poprawek, aby wykonać zapytanie XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="28559-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="28559-106">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="28559-106">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="28559-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="28559-107">Example</span></span>  
 <span data-ttu-id="28559-108">Ten przykład przedstawia tworzenie XML w przestrzeni nazw, a następnie ustaw kwerendę, która zwraca żadnego wyniku.</span><span class="sxs-lookup"><span data-stu-id="28559-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
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
  
 <span data-ttu-id="28559-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28559-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="28559-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="28559-110">Example</span></span>  
 <span data-ttu-id="28559-111">Ten przykład przedstawia tworzenie XML w przestrzeni nazw i zapytanie zakodowanej poprawnie.</span><span class="sxs-lookup"><span data-stu-id="28559-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="28559-112">Rozwiązanie to zadeklarować i zainicjuj <xref:System.Xml.Linq.XNamespace> obiektu i używać go podczas określania <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="28559-112">The solution is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="28559-113">W tym przypadku argument <xref:System.Xml.Linq.XElement.Elements%2A> jest metoda <xref:System.Xml.Linq.XName> obiektu.</span><span class="sxs-lookup"><span data-stu-id="28559-113">In this case, the argument to the <xref:System.Xml.Linq.XElement.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>  
  
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
  
 <span data-ttu-id="28559-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="28559-114">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="28559-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28559-115">See Also</span></span>  
 [<span data-ttu-id="28559-116">Podstawowe zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="28559-116">Basic Queries (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
