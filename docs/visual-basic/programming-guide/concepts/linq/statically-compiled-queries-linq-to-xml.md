---
title: Skompilowane statycznie zapytania (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: ff708dd14d27b34be797f1630dabe27a56c5a219
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834910"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="dfdcc-102">Skompilowane statycznie zapytania (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfdcc-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="dfdcc-103">Jedną z najważniejszych wydajności korzyści programu LINQ to XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, jest statycznie są zapytania w LINQ to XML kompilowane, dlatego należy interpretować zapytania XPath w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="dfdcc-104">Ta funkcja jest wbudowana w LINQ to XML, dzięki czemu nie trzeba wykonać dodatkowe kroki, aby z niej korzystać, ale warto zrozumieć różnicę, wybierając między te dwie technologie.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="dfdcc-105">W tym temacie opisano różnicę.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="dfdcc-106">Statycznie zapytania skompilowane vs. XPath</span><span class="sxs-lookup"><span data-stu-id="dfdcc-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="dfdcc-107">Poniższy przykład pokazuje, jak można pobrać elementów podrzędnych o określonej nazwie i z atrybutem z określoną wartością.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="dfdcc-108">Równoważne wyrażenie XPath jest następująca:</span><span class="sxs-lookup"><span data-stu-id="dfdcc-108">The following is the equivalent XPath expression:</span></span>  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="dfdcc-109">Wyrażenia zapytania w tym przykładzie jest ponownie zapisywany przez kompilator, aby składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="dfdcc-110">Poniższy przykład, który został napisany w składni zapytania oparte na metodzie, jest taki sam jak poprzedni:</span><span class="sxs-lookup"><span data-stu-id="dfdcc-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <span data-ttu-id="dfdcc-111"><xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="dfdcc-112">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="dfdcc-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="dfdcc-113">Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia, powyższe zapytania jest kompilowany tak, jakby zostały napisane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="dfdcc-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="dfdcc-114">Ten przykład generuje dokładnie te same wyniki poprzednich dwóch przykładach.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="dfdcc-115">Obrazuje to fakt, że zapytania skutecznie są kompilowane do wywołania metody statycznie połączone.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="dfdcc-116">W połączeniu z semantyką odroczonego wykonania iteratorów, zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="dfdcc-117">Aby uzyskać więcej informacji dotyczących semantyki odroczonego wykonania iteratorów, zobacz [wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dfdcc-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfdcc-118">Te przykłady są reprezentatywne kodu, który może zapisać kompilator.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="dfdcc-119">Rzeczywiste wdrożenie może różnić się nieco od tych przykładach, ale wydajność będą takie same lub podobne do tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="dfdcc-120">Wykonywanie wyrażeń XPath z parametrem XmlDocument</span><span class="sxs-lookup"><span data-stu-id="dfdcc-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="dfdcc-121">W poniższym przykładzie użyto <xref:System.Xml.XmlDocument> wykonywać te same wyniki poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="dfdcc-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 <span data-ttu-id="dfdcc-122">Ta kwerenda zwraca ten sam wynik jako przykłady, które używają programu LINQ to XML; Jedyna różnica polega na czy LINQ to XML wcięcia XML drukowane, podczas gdy <xref:System.Xml.XmlDocument> nie.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="dfdcc-123">Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj nie wykonuje oraz LINQ to XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> metody należy wykonać następujące czynności wewnętrznie za każdym razem, gdy jest to:</span><span class="sxs-lookup"><span data-stu-id="dfdcc-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="dfdcc-124">Analizuje ciąg, który zawiera wyrażenie XPath podzielenie ciągu na tokeny.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="dfdcc-125">Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="dfdcc-126">Tłumaczy je wyrażenia do drzewa wyrażenie wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="dfdcc-127">Iterację węzłów, odpowiednio Wybieranie węzłów do zestawu wyników na podstawie oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="dfdcc-128">Jest to znacznie więcej niż pracy wykonanej przez odpowiednie zapytaniu składnika LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="dfdcc-129">Różnica dotyczącego wydajności różni się dla różnych typów kwerend, ale w ogólne LINQ to XML zapytania są mniej pracy i w związku z tym mają lepszą wydajność, niż oceny wyrażeń XPath przy użyciu <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="dfdcc-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfdcc-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dfdcc-130">See also</span></span>

- [<span data-ttu-id="dfdcc-131">Wydajność (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfdcc-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
