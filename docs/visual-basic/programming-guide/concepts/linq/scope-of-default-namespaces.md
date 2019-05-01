---
title: Zakres domyślnych przestrzeni nazw w języku Visual Basic
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: e33505dd8e8ad94e3c758f15f245d0cbaf6987bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786805"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="818ff-102">Zakres domyślnych przestrzeni nazw w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="818ff-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="818ff-103">Domyślne obszary nazw, reprezentowany w drzewie XML nie są uwzględnione w zakresie zapytania.</span><span class="sxs-lookup"><span data-stu-id="818ff-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="818ff-104">Jeśli masz plik XML, który znajduje się w domyślnej przestrzeni nazw, nadal należy zadeklarować <xref:System.Xml.Linq.XNamespace> zmienną i łączą je z nazwą lokalną, można utworzyć kwalifikowane nazwy ma być używany w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="818ff-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="818ff-105">Jedną z najbardziej typowych problemów podczas wykonywania zapytań dotyczących drzew XML jest, że jeśli drzewa XML ma domyślny obszar nazw, deweloper czasami zapisuje zapytanie tak, jakby plik XML nie znajdowały się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="818ff-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="818ff-106">Pierwszy zestaw przykładów w tym temacie przedstawiono typowy sposób XML w domyślnej przestrzeni nazw jest ładowany, że jest nieprawidłowo wysyłane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="818ff-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="818ff-107">Drugi zestaw przykładach pokazano niezbędnych poprawek, dzięki czemu można tworzyć zapytania XML w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="818ff-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="818ff-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="818ff-108">Example</span></span>  
 <span data-ttu-id="818ff-109">W tym przykładzie pokazano tworzenie obiektu XML w przestrzeni nazw i ustaw zapytania, które zwraca żadnego wyniku.</span><span class="sxs-lookup"><span data-stu-id="818ff-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="818ff-110">Kod</span><span class="sxs-lookup"><span data-stu-id="818ff-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="818ff-111">Komentarze</span><span class="sxs-lookup"><span data-stu-id="818ff-111">Comments</span></span>  
 <span data-ttu-id="818ff-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="818ff-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="818ff-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="818ff-113">Example</span></span>  
 <span data-ttu-id="818ff-114">W tym przykładzie pokazano tworzenie obiektu XML w przestrzeni nazw i zapytanie, które są poprawnie kodowane.</span><span class="sxs-lookup"><span data-stu-id="818ff-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="818ff-115">W przeciwieństwie do kodowane niepoprawnie powyższym przykładzie właściwe podejście, korzystając z języka Visual Basic jest zadeklarowania i zainicjowania domyślnej globalnej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="818ff-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="818ff-116">Umieszcza wszystkie właściwości XML domyślny obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="818ff-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="818ff-117">Nie inne modyfikacje są wymagane do przykładu tak, aby upewnić się, że działa prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="818ff-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="818ff-118">Kod</span><span class="sxs-lookup"><span data-stu-id="818ff-118">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="818ff-119">Komentarze</span><span class="sxs-lookup"><span data-stu-id="818ff-119">Comments</span></span>  
 <span data-ttu-id="818ff-120">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="818ff-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="818ff-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="818ff-121">See also</span></span>

- [<span data-ttu-id="818ff-122">Praca z przestrzeniami nazw XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="818ff-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
