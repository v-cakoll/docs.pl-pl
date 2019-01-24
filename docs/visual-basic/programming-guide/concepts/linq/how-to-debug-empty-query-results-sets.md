---
title: 'Instrukcje: Debugowanie zestawów wyników zapytania (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 72233981e6e9a309c3f328041736f3fce71746cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715455"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="288c1-102">Instrukcje: Debugowanie zestawów wyników zapytania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="288c1-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>
<span data-ttu-id="288c1-103">Jedną z najbardziej typowych problemów podczas wykonywania zapytań dotyczących drzew XML jest, że jeśli drzewa XML ma domyślny obszar nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie znajdowały się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="288c1-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="288c1-104">Pierwszy zestaw przykładów w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest ładowany i jest wykonywane zapytanie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="288c1-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>  
  
 <span data-ttu-id="288c1-105">Drugi zestaw przykładach pokazano niezbędnych poprawek, dzięki czemu można tworzyć zapytania XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="288c1-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
 <span data-ttu-id="288c1-106">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="288c1-106">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="288c1-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="288c1-107">Example</span></span>  
 <span data-ttu-id="288c1-108">Ten przykład przedstawia tworzenie XML w przestrzeni nazw i ustaw zapytania, które zwraca żadnego wyniku.</span><span class="sxs-lookup"><span data-stu-id="288c1-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns='http://www.adventure-works.com'>  
        <Child>1</Child>  
        <Child>2</Child>  
        <Child>3</Child>  
        <AnotherChild>4</AnotherChild>  
        <AnotherChild>5</AnotherChild>  
        <AnotherChild>6</AnotherChild>  
    </Root>  
Dim c1 As IEnumerable(Of XElement) = _  
        From el In root.<Child> _  
        Select el  
Console.WriteLine("Result set follows:")  
For Each el As XElement In c1  
    Console.WriteLine(el.Value)  
Next  
Console.WriteLine("End of result set")  
```  
  
 <span data-ttu-id="288c1-109">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="288c1-109">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="288c1-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="288c1-110">Example</span></span>  
 <span data-ttu-id="288c1-111">Ten przykład przedstawia tworzenie XML w przestrzeni nazw i zapytanie, które są poprawnie kodowane.</span><span class="sxs-lookup"><span data-stu-id="288c1-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="288c1-112">To rozwiązanie jest zadeklarowania i zainicjowania domyślnej globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="288c1-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="288c1-113">Umieszcza wszystkie właściwości XML domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="288c1-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="288c1-114">Nie inne modyfikacje są wymagane do przykładu tak, aby upewnić się, że działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="288c1-114">No other modifications are required to the example to make it work properly.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="288c1-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="288c1-115">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="288c1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="288c1-116">See also</span></span>
- [<span data-ttu-id="288c1-117">Podstawowe zapytania (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="288c1-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
