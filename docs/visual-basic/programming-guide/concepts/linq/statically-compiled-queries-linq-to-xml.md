---
title: Zapytania skompilowane statycznie (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f020c1ed8627df8c8386a059f0cea372e8df363e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406771"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a><span data-ttu-id="d9d36-102">Zapytania skompilowane statycznie (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9d36-102">Statically Compiled Queries (LINQ to XML) (Visual Basic)</span></span>

<span data-ttu-id="d9d36-103">Jedną z najważniejszych korzyści związanych z wydajnością LINQ to XML, w przeciwieństwie do programu <xref:System.Xml.XmlDocument> , jest to, że zapytania w LINQ to XML są kompilowane statycznie, podczas gdy zapytania XPath muszą być interpretowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d9d36-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="d9d36-104">Ta funkcja jest wbudowana w LINQ to XML, więc nie trzeba wykonywać dodatkowych czynności, aby korzystać z nich, ale warto zrozumieć rozróżnienie podczas wybierania dwóch technologii.</span><span class="sxs-lookup"><span data-stu-id="d9d36-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="d9d36-105">W tym temacie opisano różnicę.</span><span class="sxs-lookup"><span data-stu-id="d9d36-105">This topic explains the difference.</span></span>

## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="d9d36-106">Zapytania skompilowane statycznie a XPath</span><span class="sxs-lookup"><span data-stu-id="d9d36-106">Statically Compiled Queries vs. XPath</span></span>

<span data-ttu-id="d9d36-107">Poniższy przykład pokazuje, jak uzyskać elementy podrzędne o określonej nazwie i z atrybutem o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="d9d36-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>

<span data-ttu-id="d9d36-108">Poniżej znajduje się równoważne wyrażenie XPath:</span><span class="sxs-lookup"><span data-stu-id="d9d36-108">The following is the equivalent XPath expression:</span></span>

```vb
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

<span data-ttu-id="d9d36-109">Wyrażenie zapytania w tym przykładzie jest ponownie zapisywane przez kompilator do składni zapytania opartej na metodzie.</span><span class="sxs-lookup"><span data-stu-id="d9d36-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="d9d36-110">Poniższy przykład, który został zapisany w składni zapytania opartej na metodzie, daje takie same wyniki jak poprzedni:</span><span class="sxs-lookup"><span data-stu-id="d9d36-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="d9d36-111"><xref:System.Linq.Enumerable.Where%2A>Metoda jest metodą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="d9d36-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="d9d36-112">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="d9d36-112">For more information, see [Extension Methods](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="d9d36-113">Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest to metoda rozszerzająca, zapytanie powyżej zostało skompilowane tak, jakby było zapisywane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d9d36-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<span data-ttu-id="d9d36-114">Ten przykład daje dokładnie te same wyniki co dwa poprzednie przykłady.</span><span class="sxs-lookup"><span data-stu-id="d9d36-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="d9d36-115">Ilustruje to fakt, że zapytania są efektywnie kompilowane na wywołania metod połączonych statycznie.</span><span class="sxs-lookup"><span data-stu-id="d9d36-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="d9d36-116">W połączeniu z odroczoną semantyką wykonywania iteratorów, zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="d9d36-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="d9d36-117">Aby uzyskać więcej informacji o odroczonej semantyki wykonywania iteratorów, zobacz [odroczone wykonywanie i obliczanie z opóźnieniem w LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d9d36-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d9d36-118">Te przykłady są reprezentatywne dla kodu, który kompilator może napisać.</span><span class="sxs-lookup"><span data-stu-id="d9d36-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="d9d36-119">Rzeczywista implementacja może się nieco różnić od tych przykładów, ale wydajność będzie taka sama lub podobna do tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="d9d36-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>

## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="d9d36-120">Wykonywanie wyrażeń XPath przy użyciu elementu XmlDocument</span><span class="sxs-lookup"><span data-stu-id="d9d36-120">Executing XPath Expressions with XmlDocument</span></span>

<span data-ttu-id="d9d36-121">Poniższy przykład używa <xref:System.Xml.XmlDocument> , aby wykonać te same wyniki co w poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="d9d36-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>

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

<span data-ttu-id="d9d36-122">To zapytanie zwraca te same dane wyjściowe jak przykłady, które używają LINQ to XML; Jedyną różnicą jest to, że LINQ to XML wcięcia drukowanego kodu XML, a nie <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="d9d36-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>

<span data-ttu-id="d9d36-123">Jednakże <xref:System.Xml.XmlDocument> podejście zwykle nie wykonuje ani LINQ to XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> Metoda musi wykonać wewnętrznie przy każdym wywołaniu:</span><span class="sxs-lookup"><span data-stu-id="d9d36-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>

- <span data-ttu-id="d9d36-124">Analizuje ciąg zawierający wyrażenie XPath, dzieląc ciąg na tokeny.</span><span class="sxs-lookup"><span data-stu-id="d9d36-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>

- <span data-ttu-id="d9d36-125">Sprawdza tokeny, aby upewnić się, że wyrażenie XPath jest prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="d9d36-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>

- <span data-ttu-id="d9d36-126">Tłumaczy wyrażenie na wewnętrzne drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d9d36-126">It translates the expression into an internal expression tree.</span></span>

- <span data-ttu-id="d9d36-127">Wykonuje iterację w węzłach, odpowiednio wybierając węzły dla zestawu wyników na podstawie oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d9d36-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>

<span data-ttu-id="d9d36-128">Jest to znacznie więcej niż pracy wykonanej przez odpowiednie LINQ to XML zapytanie.</span><span class="sxs-lookup"><span data-stu-id="d9d36-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="d9d36-129">Określona różnica wydajności różni się w zależności od różnych typów zapytań, ale w ogólnych zapytaniach LINQ to XML wykonuje mniej pracy i w związku z tym wykonuje lepsze, niż ocenianie wyrażeń XPath przy użyciu <xref:System.Xml.XmlDocument> .</span><span class="sxs-lookup"><span data-stu-id="d9d36-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9d36-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9d36-130">See also</span></span>

- [<span data-ttu-id="d9d36-131">Wydajność (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9d36-131">Performance (LINQ to XML) (Visual Basic)</span></span>](performance-linq-to-xml.md)
