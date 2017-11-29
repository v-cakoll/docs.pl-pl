---
title: Statycznie skompilowane zapytania (LINQ do XML) (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 15ba867951ca4df1d203b837318ca2cc9eb91e7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="9cc72-102">Statycznie skompilowane zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9cc72-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="9cc72-103">Jedną z najważniejszych wydajności przynosi korzyści LINQ do XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, statycznie są kwerendy w składniku LINQ to XML kompilowania, podczas gdy kwerendy XPath muszą być interpretowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9cc72-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="9cc72-104">Ta funkcja jest wbudowana w LINQ do XML, więc nie trzeba wykonywać dodatkowe czynności, aby móc korzystać z niego, ale jest przydatne rozróżnienie, gdy Wybieranie między te dwie technologie.</span><span class="sxs-lookup"><span data-stu-id="9cc72-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="9cc72-105">W tym temacie objaśniono różnicę.</span><span class="sxs-lookup"><span data-stu-id="9cc72-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="9cc72-106">Statycznie vs skompilowane zapytania. XPath</span><span class="sxs-lookup"><span data-stu-id="9cc72-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="9cc72-107">Poniższy przykład pokazuje, jak można uzyskać elementów podrzędnych o określonej nazwie i z atrybutem o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="9cc72-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="9cc72-108">Poniżej przedstawiono równoważne wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="9cc72-108">The following is the equivalent XPath expression:</span></span>  
  
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
  
 <span data-ttu-id="9cc72-109">Wyrażenia zapytania w tym przykładzie są ponownie zapisywane przez kompilator do składni zapytania oparte na metodzie.</span><span class="sxs-lookup"><span data-stu-id="9cc72-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="9cc72-110">Poniższy przykład, który został napisany w składni zapytania oparte na metodzie, jest taki sam jak poprzedni:</span><span class="sxs-lookup"><span data-stu-id="9cc72-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="9cc72-111"><xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="9cc72-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="9cc72-112">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9cc72-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="9cc72-113">Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia zapytania powyżej jest kompilowana tak, jakby były zapisywane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="9cc72-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="9cc72-114">W tym przykładzie powoduje dokładnie takie same wyniki jak poprzednich dwóch przykładach.</span><span class="sxs-lookup"><span data-stu-id="9cc72-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="9cc72-115">Przedstawiono to fakt skutecznie kompilowane zapytania do wywołania metody statycznie połączone.</span><span class="sxs-lookup"><span data-stu-id="9cc72-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="9cc72-116">Tym połączeniu z semantykę wykonanie odroczone Iteratory, poprawia wydajność.</span><span class="sxs-lookup"><span data-stu-id="9cc72-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="9cc72-117">Aby uzyskać więcej informacji na temat semantyki wykonanie odroczone Iteratory, zobacz [termin odroczonego wykonania i obliczanie leniwe w składniku LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="9cc72-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cc72-118">Te przykłady są reprezentatywne kodu, który może zapisać kompilatora.</span><span class="sxs-lookup"><span data-stu-id="9cc72-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="9cc72-119">Rzeczywista implementacja może różnić się nieznacznie w tych przykładach, ale wydajność będą takie same lub podobne do tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="9cc72-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="9cc72-120">Wykonywania wyrażenia XPath z parametrem XmlDocument</span><span class="sxs-lookup"><span data-stu-id="9cc72-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="9cc72-121">W poniższym przykładzie użyto <xref:System.Xml.XmlDocument> na takie same wyniki jak w poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="9cc72-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="9cc72-122">Ta kwerenda zwraca tych samych danych wyjściowych jako przykłady, które używają LINQ do XML; Jedyna różnica polega na czy LINQ do XML wcięcia drukowanymi XML, podczas gdy <xref:System.Xml.XmlDocument> nie.</span><span class="sxs-lookup"><span data-stu-id="9cc72-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="9cc72-123">Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj wykonuje oraz LINQ do XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> metody musi wykonać następujące czynności wewnętrznie za każdym razem, gdy jest to:</span><span class="sxs-lookup"><span data-stu-id="9cc72-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
-   <span data-ttu-id="9cc72-124">Analizuje ciąg, który zawiera wyrażenie XPath, dzielenie ciąg na tokeny.</span><span class="sxs-lookup"><span data-stu-id="9cc72-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
-   <span data-ttu-id="9cc72-125">Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="9cc72-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
-   <span data-ttu-id="9cc72-126">Tłumaczy go wyrażenia na drzewo wyrażenia wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="9cc72-126">It translates the expression into an internal expression tree.</span></span>  
  
-   <span data-ttu-id="9cc72-127">Iteruje węzłów, odpowiednio zaznaczania węzłów w zestawie wyników na podstawie oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9cc72-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="9cc72-128">Jest to znacznie więcej niż pracy wykonanej przez odpowiednie zapytania składnika LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="9cc72-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="9cc72-129">Różnice dotyczące wydajności może być różna dla różnych typów kwerend, ale w ogólne LINQ do XML zapytania mniej pracy i w związku z tym działać lepiej niż obliczenia za pomocą wyrażenia XPath <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="9cc72-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cc72-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cc72-130">See Also</span></span>  
 [<span data-ttu-id="9cc72-131">Wydajność (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="9cc72-131">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
