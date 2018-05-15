---
title: Statycznie skompilowane zapytania (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f6230864eb125d493d38f85adf5806c80a31c910
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="74d95-102">Statycznie skompilowane zapytania (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74d95-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="74d95-103">Jedną z najważniejszych wydajności przynosi korzyści LINQ do XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, statycznie są kwerendy w składniku LINQ to XML kompilowania, podczas gdy kwerendy XPath muszą być interpretowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="74d95-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="74d95-104">Ta funkcja jest wbudowana w LINQ do XML, więc nie trzeba wykonywać dodatkowe czynności, aby móc korzystać z niego, ale jest przydatne rozróżnienie, gdy Wybieranie między te dwie technologie.</span><span class="sxs-lookup"><span data-stu-id="74d95-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="74d95-105">W tym temacie objaśniono różnicę.</span><span class="sxs-lookup"><span data-stu-id="74d95-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="74d95-106">Statycznie vs skompilowane zapytania. XPath</span><span class="sxs-lookup"><span data-stu-id="74d95-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="74d95-107">Poniższy przykład pokazuje, jak można uzyskać elementów podrzędnych o określonej nazwie i z atrybutem o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="74d95-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="74d95-108">Poniżej przedstawiono równoważne wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="74d95-108">The following is the equivalent XPath expression:</span></span>  
  
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
  
 <span data-ttu-id="74d95-109">Wyrażenia zapytania w tym przykładzie są ponownie zapisywane przez kompilator do składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="74d95-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="74d95-110">Poniższy przykład, który został napisany w składni zapytania oparte na metodzie, jest taki sam jak poprzedni:</span><span class="sxs-lookup"><span data-stu-id="74d95-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <span data-ttu-id="74d95-111"><xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="74d95-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="74d95-112">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="74d95-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="74d95-113">Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia zapytania powyżej jest kompilowana tak, jakby były zapisywane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="74d95-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 <span data-ttu-id="74d95-114">W tym przykładzie powoduje dokładnie takie same wyniki jak poprzednich dwóch przykładach.</span><span class="sxs-lookup"><span data-stu-id="74d95-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="74d95-115">Przedstawiono to fakt skutecznie kompilowane zapytania do wywołania metody statycznie połączone.</span><span class="sxs-lookup"><span data-stu-id="74d95-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="74d95-116">Tym połączeniu z semantykę wykonanie odroczone Iteratory, poprawia wydajność.</span><span class="sxs-lookup"><span data-stu-id="74d95-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="74d95-117">Aby uzyskać więcej informacji na temat semantyki wykonanie odroczone Iteratory, zobacz [termin odroczonego wykonania i obliczanie leniwe w składniku LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="74d95-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74d95-118">Te przykłady są reprezentatywne kodu, który może zapisać kompilatora.</span><span class="sxs-lookup"><span data-stu-id="74d95-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="74d95-119">Rzeczywista implementacja może różnić się nieznacznie w tych przykładach, ale wydajność będą takie same lub podobne do tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="74d95-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="74d95-120">Wykonywania wyrażenia XPath z parametrem XmlDocument</span><span class="sxs-lookup"><span data-stu-id="74d95-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="74d95-121">W poniższym przykładzie użyto <xref:System.Xml.XmlDocument> na takie same wyniki jak w poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="74d95-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
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
  
 <span data-ttu-id="74d95-122">Ta kwerenda zwraca tych samych danych wyjściowych jako przykłady, które używają LINQ do XML; Jedyna różnica polega na czy LINQ do XML wcięcia drukowanymi XML, podczas gdy <xref:System.Xml.XmlDocument> nie.</span><span class="sxs-lookup"><span data-stu-id="74d95-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="74d95-123">Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj wykonuje oraz LINQ do XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> metody musi wykonać następujące czynności wewnętrznie za każdym razem, gdy jest to:</span><span class="sxs-lookup"><span data-stu-id="74d95-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="74d95-124">Analizuje ciąg, który zawiera wyrażenie XPath, dzielenie ciąg na tokeny.</span><span class="sxs-lookup"><span data-stu-id="74d95-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="74d95-125">Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="74d95-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="74d95-126">Tłumaczy go wyrażenia na drzewo wyrażenia wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="74d95-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="74d95-127">Iteruje węzłów, odpowiednio zaznaczania węzłów w zestawie wyników na podstawie oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="74d95-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="74d95-128">Jest to znacznie więcej niż pracy wykonanej przez odpowiednie zapytania składnika LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="74d95-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="74d95-129">Różnice dotyczące wydajności może być różna dla różnych typów kwerend, ale w ogólne LINQ do XML zapytania mniej pracy i w związku z tym działać lepiej niż obliczenia za pomocą wyrażenia XPath <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="74d95-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d95-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74d95-130">See Also</span></span>  
 [<span data-ttu-id="74d95-131">Wydajność (LINQ do XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74d95-131">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
