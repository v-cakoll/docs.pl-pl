---
title: Zakres domyślnych przestrzeni nazw w Visual Basic
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: a08d140cfc68c36c26487ab47fc82dd3bf522fa8
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581881"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="cc349-102">Zakres domyślnych przestrzeni nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc349-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="cc349-103">Domyślne przestrzenie nazw reprezentowane w drzewie XML nie znajdują się w zakresie zapytań.</span><span class="sxs-lookup"><span data-stu-id="cc349-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="cc349-104">Jeśli masz kod XML, który znajduje się w domyślnym obszarze nazw, nadal musisz zadeklarować zmienną <xref:System.Xml.Linq.XNamespace> i połączyć ją z lokalną nazwą, aby nazwa kwalifikowana była używana w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="cc349-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="cc349-105">Jednym z najczęstszych problemów związanych z kwerendą drzewa XML jest to, że jeśli drzewo XML ma domyślną przestrzeń nazw, deweloper czasami zapisuje zapytanie tak, jakby kod XML nie był w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cc349-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="cc349-106">Pierwszy zestaw przykładów w tym temacie przedstawia typowy sposób ładowania kodu XML w domyślnej przestrzeni nazw, ale jest ono nieprawidłowo wykonywane.</span><span class="sxs-lookup"><span data-stu-id="cc349-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="cc349-107">Drugi zestaw przykładów pokazuje niezbędne poprawki, aby można było zbadać kod XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cc349-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc349-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc349-108">Example</span></span>  
 <span data-ttu-id="cc349-109">Ten przykład pokazuje tworzenie XML w przestrzeni nazw i zapytanie zwracające pusty zestaw wyników.</span><span class="sxs-lookup"><span data-stu-id="cc349-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cc349-110">Kod</span><span class="sxs-lookup"><span data-stu-id="cc349-110">Code</span></span>  
  
```vb  
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
  
### <a name="comments"></a><span data-ttu-id="cc349-111">Komentarze</span><span class="sxs-lookup"><span data-stu-id="cc349-111">Comments</span></span>  
 <span data-ttu-id="cc349-112">Ten przykład generuje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="cc349-112">This example produces the following result:</span></span>  
  
```console  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="cc349-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="cc349-113">Example</span></span>  
 <span data-ttu-id="cc349-114">Ten przykład pokazuje tworzenie kodu XML w przestrzeni nazw oraz zakodowane prawidłowo zapytanie.</span><span class="sxs-lookup"><span data-stu-id="cc349-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="cc349-115">W przeciwieństwie do nieprawidłowo zakodowanego przykładu, poprawna Metoda korzystania z Visual Basic polega na zadeklarowaniu i zainicjowaniu globalnej domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cc349-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="cc349-116">Spowoduje to umieszczenie wszystkich właściwości XML w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="cc349-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="cc349-117">Do poprawnego działania tego przykładu nie są wymagane żadne inne modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="cc349-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cc349-118">Kod</span><span class="sxs-lookup"><span data-stu-id="cc349-118">Code</span></span>  
  
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
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="cc349-119">Komentarze</span><span class="sxs-lookup"><span data-stu-id="cc349-119">Comments</span></span>  
 <span data-ttu-id="cc349-120">Ten przykład generuje następujący wynik:</span><span class="sxs-lookup"><span data-stu-id="cc349-120">This example produces the following result:</span></span>  
  
```console  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc349-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cc349-121">See also</span></span>

- [<span data-ttu-id="cc349-122">Przegląd przestrzeni nazw (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc349-122">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
