---
title: 'Instrukcje: Debuguj puste zestawy wyników zapytania (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: 6fc194432b1d44c1214da32d2c6978a4eeb316dc
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351780"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="d85cc-102">Instrukcje: Debuguj puste zestawy wyników zapytania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d85cc-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="d85cc-103">Jednym z najczęstszych problemów związanych z kwerendą drzewa XML jest to, że jeśli drzewo XML ma domyślną przestrzeń nazw, deweloper czasami zapisuje zapytanie tak, jakby kod XML nie był w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d85cc-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="d85cc-104">Pierwszy zestaw przykładów w tym temacie przedstawia typowy sposób ładowania kodu XML w domyślnej przestrzeni nazw i jest on nieprawidłowo przeszukiwany.</span><span class="sxs-lookup"><span data-stu-id="d85cc-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="d85cc-105">Drugi zestaw przykładów pokazuje niezbędne poprawki, aby można było zbadać kod XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d85cc-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="d85cc-106">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d85cc-106">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>

## <a name="example"></a><span data-ttu-id="d85cc-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="d85cc-107">Example</span></span>

<span data-ttu-id="d85cc-108">Ten przykład pokazuje tworzenie XML w przestrzeni nazw i zapytanie zwracające pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="d85cc-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

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

<span data-ttu-id="d85cc-109">Ten przykład generuje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="d85cc-109">This example produces the following result:</span></span>

```console
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="d85cc-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d85cc-110">Example</span></span>

<span data-ttu-id="d85cc-111">Ten przykład pokazuje tworzenie kodu XML w przestrzeni nazw oraz zakodowane prawidłowo zapytanie.</span><span class="sxs-lookup"><span data-stu-id="d85cc-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="d85cc-112">Rozwiązaniem jest zadeklarowanie i zainicjowanie globalnej domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d85cc-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="d85cc-113">Spowoduje to umieszczenie wszystkich właściwości XML w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d85cc-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="d85cc-114">Do poprawnego działania tego przykładu nie są wymagane żadne inne modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="d85cc-114">No other modifications are required to the example to make it work properly.</span></span>

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

<span data-ttu-id="d85cc-115">Ten przykład generuje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="d85cc-115">This example produces the following result:</span></span>

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="d85cc-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d85cc-116">See also</span></span>

- [<span data-ttu-id="d85cc-117">Zapytania podstawowe (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d85cc-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
