---
title: Zapytania skompilowane statycznie (LINQ to XML)C#()
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253032"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="3b259-102">Zapytania skompilowane statycznie (LINQ to XML)C#()</span><span class="sxs-lookup"><span data-stu-id="3b259-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="3b259-103">Jedną z najważniejszych korzyści związanych z wydajnością LINQ to XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>programu, jest to, że zapytania w LINQ to XML są kompilowane statycznie, podczas gdy zapytania XPath muszą być interpretowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3b259-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="3b259-104">Ta funkcja jest wbudowana w LINQ to XML, więc nie trzeba wykonywać dodatkowych czynności, aby korzystać z nich, ale warto zrozumieć rozróżnienie podczas wybierania dwóch technologii.</span><span class="sxs-lookup"><span data-stu-id="3b259-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="3b259-105">W tym temacie opisano różnicę.</span><span class="sxs-lookup"><span data-stu-id="3b259-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="3b259-106">Zapytania skompilowane statycznie a XPath</span><span class="sxs-lookup"><span data-stu-id="3b259-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="3b259-107">Poniższy przykład pokazuje, jak uzyskać elementy podrzędne o określonej nazwie i z atrybutem o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="3b259-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="3b259-108">Poniżej znajduje się równoważne wyrażenie XPath:`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="3b259-108">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="3b259-109">Wyrażenie zapytania w tym przykładzie jest ponownie zapisywane przez kompilator do składni zapytania opartej na metodzie.</span><span class="sxs-lookup"><span data-stu-id="3b259-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="3b259-110">Poniższy przykład, który został zapisany w składni zapytania opartej na metodzie, daje takie same wyniki jak poprzedni:</span><span class="sxs-lookup"><span data-stu-id="3b259-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="3b259-111"><xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="3b259-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="3b259-112">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="3b259-112">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="3b259-113">Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest to metoda rozszerzająca, zapytanie powyżej zostało skompilowane tak, jakby było zapisywane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3b259-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="3b259-114">Ten przykład daje dokładnie te same wyniki co dwa poprzednie przykłady.</span><span class="sxs-lookup"><span data-stu-id="3b259-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="3b259-115">Ilustruje to fakt, że zapytania są efektywnie kompilowane na wywołania metod połączonych statycznie.</span><span class="sxs-lookup"><span data-stu-id="3b259-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="3b259-116">W połączeniu z odroczoną semantyką wykonywania iteratorów, zwiększa wydajność.</span><span class="sxs-lookup"><span data-stu-id="3b259-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="3b259-117">Aby uzyskać więcej informacji o odroczonej semantyki wykonywania iteratorów, zobacz [odroczone wykonywanie i ocenę z opóźnieniem w LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3b259-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3b259-118">Te przykłady są reprezentatywne dla kodu, który kompilator może napisać.</span><span class="sxs-lookup"><span data-stu-id="3b259-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="3b259-119">Rzeczywista implementacja może się nieco różnić od tych przykładów, ale wydajność będzie taka sama lub podobna do tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="3b259-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="3b259-120">Wykonywanie wyrażeń XPath przy użyciu elementu XmlDocument</span><span class="sxs-lookup"><span data-stu-id="3b259-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="3b259-121">Poniższy przykład używa <xref:System.Xml.XmlDocument> , aby wykonać te same wyniki co w poprzednich przykładach:</span><span class="sxs-lookup"><span data-stu-id="3b259-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="3b259-122">To zapytanie zwraca te same dane wyjściowe jak przykłady, które używają LINQ to XML; Jedyną różnicą jest to, że LINQ to XML wcięcia drukowanego kodu XML <xref:System.Xml.XmlDocument> , a nie.</span><span class="sxs-lookup"><span data-stu-id="3b259-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="3b259-123">Jednakże podejście zwykle nie wykonuje ani LINQ to XML, <xref:System.Xml.XmlNode.SelectNodes%2A> ponieważ metoda musi wykonać wewnętrznie przy każdym wywołaniu: <xref:System.Xml.XmlDocument></span><span class="sxs-lookup"><span data-stu-id="3b259-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="3b259-124">Analizuje ciąg zawierający wyrażenie XPath, dzieląc ciąg na tokeny.</span><span class="sxs-lookup"><span data-stu-id="3b259-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="3b259-125">Sprawdza tokeny, aby upewnić się, że wyrażenie XPath jest prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="3b259-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="3b259-126">Tłumaczy wyrażenie na wewnętrzne drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3b259-126">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="3b259-127">Wykonuje iterację w węzłach, odpowiednio wybierając węzły dla zestawu wyników na podstawie oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3b259-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="3b259-128">Jest to znacznie więcej niż pracy wykonanej przez odpowiednie LINQ to XML zapytanie.</span><span class="sxs-lookup"><span data-stu-id="3b259-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="3b259-129">Określona różnica wydajności różni się w zależności od różnych typów zapytań, ale w ogólnych zapytaniach LINQ to XML wykonuje mniej pracy i w związku z tym wykonuje lepsze, niż ocenianie wyrażeń XPath przy użyciu <xref:System.Xml.XmlDocument>.</span><span class="sxs-lookup"><span data-stu-id="3b259-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
