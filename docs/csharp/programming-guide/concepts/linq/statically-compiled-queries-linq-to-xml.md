---
title: Statycznie skompilowane zapytania (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 98725cece1006ba13afb64bb8ae17ae6e62c53cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253032"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a><span data-ttu-id="8d339-102">Statycznie skompilowane zapytania (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8d339-102">Statically Compiled Queries (LINQ to XML) (C#)</span></span>
<span data-ttu-id="8d339-103">Jedną z najważniejszych korzyści wydajności LINQ do XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, jest to, że zapytania w LINQ do XML są statycznie skompilowany, podczas gdy zapytania XPath muszą być interpretowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8d339-103">One of the most important performance benefits LINQ to XML, as opposed to <xref:System.Xml.XmlDocument>, is that queries in LINQ to XML are statically compiled, whereas XPath queries must be interpreted at run time.</span></span> <span data-ttu-id="8d339-104">Ta funkcja jest wbudowana w LINQ do XML, więc nie trzeba wykonywać dodatkowych kroków, aby z niej skorzystać, ale warto zrozumieć rozróżnienie przy wyborze między dwiema technologiami.</span><span class="sxs-lookup"><span data-stu-id="8d339-104">This feature is built in to LINQ to XML, so you do not have to perform extra steps to take advantage of it, but it is helpful to understand the distinction when choosing between the two technologies.</span></span> <span data-ttu-id="8d339-105">W tym temacie wyjaśniono różnicę.</span><span class="sxs-lookup"><span data-stu-id="8d339-105">This topic explains the difference.</span></span>  
  
## <a name="statically-compiled-queries-vs-xpath"></a><span data-ttu-id="8d339-106">Statycznie skompilowane zapytania vs. XPath</span><span class="sxs-lookup"><span data-stu-id="8d339-106">Statically Compiled Queries vs. XPath</span></span>  
 <span data-ttu-id="8d339-107">W poniższym przykładzie pokazano, jak uzyskać elementy podrzędne o określonej nazwie i z atrybutem o określonej wartości.</span><span class="sxs-lookup"><span data-stu-id="8d339-107">The following example shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="8d339-108">Poniżej przedstawiono równoważne wyrażenie XPath:`//Address[@Type='Shipping']`</span><span class="sxs-lookup"><span data-stu-id="8d339-108">The following is the equivalent XPath expression: `//Address[@Type='Shipping']`</span></span>
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8d339-109">Wyrażenie kwerendy w tym przykładzie jest ponownie zapisywane przez kompilator do składni zapytań opartych na metodach.</span><span class="sxs-lookup"><span data-stu-id="8d339-109">The query expression in this example is re-written by the compiler to method-based query syntax.</span></span> <span data-ttu-id="8d339-110">Poniższy przykład, który jest napisany w składni kwerendy opartej na metodach, daje takie same wyniki jak poprzedni:</span><span class="sxs-lookup"><span data-stu-id="8d339-110">The following example, which is written in method-based query syntax, produces the same results as the previous one:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8d339-111">Metoda <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="8d339-111">The <xref:System.Linq.Enumerable.Where%2A> method is an extension method.</span></span> <span data-ttu-id="8d339-112">Aby uzyskać więcej informacji, zobacz [Metody rozszerzenia](../../classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="8d339-112">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span> <span data-ttu-id="8d339-113">Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia, powyższa kwerenda jest kompilowana tak, jakby została napisana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="8d339-113">Because <xref:System.Linq.Enumerable.Where%2A> is an extension method, the query above is compiled as though it were written as follows:</span></span>  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="8d339-114">W tym przykładzie daje dokładnie takie same wyniki jak w poprzednich dwóch przykładach.</span><span class="sxs-lookup"><span data-stu-id="8d339-114">This example produces exactly the same results as the previous two examples.</span></span> <span data-ttu-id="8d339-115">Ilustruje to fakt, że zapytania są skutecznie kompilowane do wywołań metod połączonych statycznie.</span><span class="sxs-lookup"><span data-stu-id="8d339-115">This illustrates the fact that queries are effectively compiled into statically linked method calls.</span></span> <span data-ttu-id="8d339-116">To, w połączeniu z semantyką odroczonego wykonania iteratorów, poprawia wydajność.</span><span class="sxs-lookup"><span data-stu-id="8d339-116">This, combined with the deferred execution semantics of iterators, improves performance.</span></span> <span data-ttu-id="8d339-117">Aby uzyskać więcej informacji na temat semantyki odroczonego wykonywania iteratorów, zobacz [Odroczone wykonanie i ocena z opóźnieniem w LINQ do XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8d339-117">For more information about the deferred execution semantics of iterators, see [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d339-118">Te przykłady są reprezentatywne dla kodu, który kompilator może napisać.</span><span class="sxs-lookup"><span data-stu-id="8d339-118">These examples are representative of the code that the compiler might write.</span></span> <span data-ttu-id="8d339-119">Rzeczywista implementacja może nieznacznie różnić się od tych przykładów, ale wydajność będzie taka sama lub podobna do tych przykładów.</span><span class="sxs-lookup"><span data-stu-id="8d339-119">The actual implementation might differ slightly from these examples, but the performance will be the same or similar to these examples.</span></span>  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a><span data-ttu-id="8d339-120">Wykonywanie wyrażeń XPath za pomocą xmlDocument</span><span class="sxs-lookup"><span data-stu-id="8d339-120">Executing XPath Expressions with XmlDocument</span></span>  
 <span data-ttu-id="8d339-121">W poniższym <xref:System.Xml.XmlDocument> przykładzie użyto do osiągnięcia tych samych wyników, co poprzednie przykłady:</span><span class="sxs-lookup"><span data-stu-id="8d339-121">The following example uses <xref:System.Xml.XmlDocument> to accomplish the same results as the previous examples:</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 <span data-ttu-id="8d339-122">Ta kwerenda zwraca te same dane wyjściowe, co przykłady, które używają LINQ do XML; Jedyną różnicą jest to, że LINQ do XML <xref:System.Xml.XmlDocument> wcina wydrukowany kod XML, podczas gdy nie.</span><span class="sxs-lookup"><span data-stu-id="8d339-122">This query returns the same output as the examples that use LINQ to XML; the only difference is that LINQ to XML indents the printed XML, whereas <xref:System.Xml.XmlDocument> does not.</span></span>  
  
 <span data-ttu-id="8d339-123">Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj nie działa tak dobrze, jak LINQ <xref:System.Xml.XmlNode.SelectNodes%2A> do XML, ponieważ metoda musi wykonać następujące wewnętrznie za każdym razem, gdy jest wywoływana:</span><span class="sxs-lookup"><span data-stu-id="8d339-123">However, the <xref:System.Xml.XmlDocument> approach generally does not perform as well as LINQ to XML, because the <xref:System.Xml.XmlNode.SelectNodes%2A> method must do the following internally every time it is called:</span></span>  
  
- <span data-ttu-id="8d339-124">Analizuje ciąg, który zawiera wyrażenie XPath, podział ciągu na tokeny.</span><span class="sxs-lookup"><span data-stu-id="8d339-124">It parses the string that contains the XPath expression, breaking the string into tokens.</span></span>  
  
- <span data-ttu-id="8d339-125">Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8d339-125">It validates the tokens to make sure that the XPath expression is valid.</span></span>  
  
- <span data-ttu-id="8d339-126">Tłumaczy wyrażenie na wewnętrzne drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="8d339-126">It translates the expression into an internal expression tree.</span></span>  
  
- <span data-ttu-id="8d339-127">Iteretują przez węzły, odpowiednio wybierając węzły dla zestawu wyników na podstawie oceny wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="8d339-127">It iterates through the nodes, appropriately selecting the nodes for the result set based on the evaluation of the expression.</span></span>  
  
 <span data-ttu-id="8d339-128">Jest to znacznie więcej niż praca wykonana przez odpowiednie linq do xml kwerendy.</span><span class="sxs-lookup"><span data-stu-id="8d339-128">This is significantly more than the work done by the corresponding LINQ to XML query.</span></span> <span data-ttu-id="8d339-129">Różnica w wydajności zależy od różnych typów zapytań, ale ogólnie linq do xml zapytania zrobić mniej pracy <xref:System.Xml.XmlDocument>i dlatego lepiej, niż oceny wyrażeń XPath przy użyciu .</span><span class="sxs-lookup"><span data-stu-id="8d339-129">The specific performance difference varies for different types of queries, but in general LINQ to XML queries do less work, and therefore perform better, than evaluating XPath expressions using <xref:System.Xml.XmlDocument>.</span></span>  
