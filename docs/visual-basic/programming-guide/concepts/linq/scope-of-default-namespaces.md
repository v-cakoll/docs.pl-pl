---
title: Zakres domyślne obszary nazw w Visual Basic
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: a0c07c1b6ca4fea836bd37e4a311655fcb1d7878
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645746"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="74c92-102">Zakres domyślne obszary nazw w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74c92-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="74c92-103">Domyślne obszary nazw reprezentowany w drzewie XML nie są w zakresie zapytania.</span><span class="sxs-lookup"><span data-stu-id="74c92-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="74c92-104">Jeśli masz kod XML, który znajduje się w domyślnej przestrzeni nazw, nadal należy zadeklarować <xref:System.Xml.Linq.XNamespace> zmienną i połączyć ją z nazwą lokalną aby kwalifikowana nazwa do użycia w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="74c92-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="74c92-105">Jest jedną z najczęściej występujących problemów podczas wykonywania zapytania drzewa XML, że jeśli drzewo składni XML ma domyślnej przestrzeni nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie zostały w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74c92-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="74c92-106">Pierwszy zestaw przykłady w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest załadowany, ale jest poddawany kwerendzie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="74c92-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="74c92-107">Drugi zestaw przykładach niezbędnych poprawek, aby wykonać zapytanie XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74c92-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74c92-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="74c92-108">Example</span></span>  
 <span data-ttu-id="74c92-109">Ten przykład przedstawia tworzenie XML w przestrzeni nazw, a następnie ustaw kwerendę, która zwraca żadnego wyniku.</span><span class="sxs-lookup"><span data-stu-id="74c92-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="74c92-110">Kod</span><span class="sxs-lookup"><span data-stu-id="74c92-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="74c92-111">Komentarze</span><span class="sxs-lookup"><span data-stu-id="74c92-111">Comments</span></span>  
 <span data-ttu-id="74c92-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="74c92-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="74c92-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="74c92-113">Example</span></span>  
 <span data-ttu-id="74c92-114">Ten przykład przedstawia tworzenie XML w przestrzeni nazw i zapytanie zakodowanej poprawnie.</span><span class="sxs-lookup"><span data-stu-id="74c92-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="74c92-115">W przeciwieństwie do niepoprawnie zakodowany powyższym przykładzie właściwe podejście, korzystając z języka Visual Basic jest zadeklarować i zainicjować domyślnej globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74c92-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="74c92-116">Wszystkie właściwości XML to umieszcza w domyślnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74c92-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="74c92-117">Nie inne zmiany są wymagane, na przykład aby działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="74c92-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="74c92-118">Kod</span><span class="sxs-lookup"><span data-stu-id="74c92-118">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="74c92-119">Komentarze</span><span class="sxs-lookup"><span data-stu-id="74c92-119">Comments</span></span>  
 <span data-ttu-id="74c92-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="74c92-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="74c92-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74c92-121">See Also</span></span>  
 [<span data-ttu-id="74c92-122">Praca z przestrzeni nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74c92-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
