---
title: Skompilowane statycznie zapytania (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 842f8c1c2fa07e1658992e94e5163222f38f80ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61681081"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="f9920-102">Skompilowane statycznie zapytania (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f9920-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f9920-103">Jedną z najważniejszych wydajności korzyści programu LINQ to XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, jest statycznie są zapytania w LINQ to XML kompilowane, dlatego należy interpretować zapytania XPath w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f9920-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="f9920-104">Ta funkcja jest wbudowana w LINQ to XML, dzięki czemu nie trzeba wykonać dodatkowe kroki, aby z niej korzystać, ale warto zrozumieć różnicę, wybierając między te dwie technologie.</span><span class="sxs-lookup"><span data-stu-id="f9920-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="f9920-105">W tym temacie opisano różnicę.</span><span class="sxs-lookup"><span data-stu-id="f9920-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="f9920-106">Statycznie zapytania skompilowane vs. XPath</span><span class="sxs-lookup"><span data-stu-id="f9920-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="f9920-107">Poniższy przykład pokazuje, jak można pobrać elementów podrzędnych o określonej nazwie i z atrybutem z określoną wartością.</span><span class="sxs-lookup"><span data-stu-id="f9920-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="f9920-108">Równoważne wyrażenie XPath jest następująca:</span><span class="sxs-lookup"><span data-stu-id="f9920-108">The following is the equivalent XPath expression:</span></span>  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f9920-109">Wyrażenia zapytania w tym przykładzie jest ponownie zapisywany przez kompilator, aby składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="f9920-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="f9920-110">Poniższy przykład, który został napisany w składni zapytania oparte na metodzie, jest taki sam jak poprzedni:</span><span class="sxs-lookup"><span data-stu-id="f9920-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f9920-111"><xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f9920-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="f9920-112">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="f9920-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="f9920-113">Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia, powyższe zapytania jest kompilowany tak, jakby zostały napisane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f9920-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="f9920-114">Ten przykład generuje dokładnie te same wyniki poprzednich dwóch przykładach.</span><span class="sxs-lookup"><span data-stu-id="f9920-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="f9920-115">Obrazuje to fakt, że zapytania skutecznie są kompilowane do wywołania metody statycznie połączone.</span><span class="sxs-lookup"><span data-stu-id="f9920-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="f9920-116">W połączeniu z semantyką odroczonego wykonania iteratorów, zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="f9920-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="f9920-117">Aby uzyskać więcej informacji dotyczących semantyki odroczonego wykonania iteratorów, zobacz [wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f9920-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9920-118">Te przykłady są reprezentatywne kodu, który może zapisać kompilator.</span><span class="sxs-lookup"><span data-stu-id="f9920-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="f9920-119">Rzeczywiste wdrożenie może różnić się nieco od tych przykładach, ale wydajność będą takie same lub podobne do tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="f9920-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="f9920-120">Wykonywanie wyrażeń XPath z parametrem XmlDocument</span><span class="sxs-lookup"><span data-stu-id="f9920-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="f9920-121">W poniższym przykładzie użyto <xref:System.Xml.XmlDocument> wykonywać te same wyniki poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="f9920-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="f9920-122">Ta kwerenda zwraca ten sam wynik jako przykłady, które używają programu LINQ to XML; Jedyna różnica polega na czy LINQ to XML wcięcia XML drukowane, podczas gdy <xref:System.Xml.XmlDocument> nie.</span><span class="sxs-lookup"><span data-stu-id="f9920-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="f9920-123">Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj nie wykonuje oraz LINQ to XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> metody należy wykonać następujące czynności wewnętrznie za każdym razem, gdy jest to:</span><span class="sxs-lookup"><span data-stu-id="f9920-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="f9920-124">Analizuje ciąg, który zawiera wyrażenie XPath podzielenie ciągu na tokeny.</span><span class="sxs-lookup"><span data-stu-id="f9920-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="f9920-125">Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f9920-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="f9920-126">Tłumaczy je wyrażenia do drzewa wyrażenie wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="f9920-126">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="f9920-127">Iterację węzłów, odpowiednio Wybieranie węzłów do zestawu wyników na podstawie oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f9920-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="f9920-128">Jest to znacznie więcej niż pracy wykonanej przez odpowiednie zapytaniu składnika LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="f9920-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="f9920-129">Różnica dotyczącego wydajności różni się dla różnych typów kwerend, ale w ogólne LINQ to XML zapytania są mniej pracy i w związku z tym mają lepszą wydajność, niż oceny wyrażeń XPath przy użyciu <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="f9920-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9920-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f9920-130">See also</span></span>

- [<span data-ttu-id="f9920-131">Wydajność (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f9920-131">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
