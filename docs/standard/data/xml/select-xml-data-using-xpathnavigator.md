---
title: Wybierz dane XML przy użyciu parametrem XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c937754f031420d90f89bf89563db17ddaaf3bbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="ba4cf-102">Wybierz dane XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ba4cf-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="ba4cf-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod używany do wybierania zestawu węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="ba4cf-104">Po wybraniu można iteracja wybranego zestawu węzłów.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="ba4cf-105">Element XPathNavigator wybór metody</span><span class="sxs-lookup"><span data-stu-id="ba4cf-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="ba4cf-106"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod używany do wybierania zestawu węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="ba4cf-107"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia również zestaw metod zoptymalizowany do wybierania węzły nadrzędne, podrzędne i obiekt podrzędny szybciej niż przy użyciu wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="ba4cf-108">Wybrany zestaw węzłów jest zwracany w <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="ba4cf-109">Wybieranie węzłów za pomocą wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="ba4cf-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="ba4cf-110">Aby wybrać zestaw węzłów za pomocą wyrażenia XPath, użyj jednej z następujących metod zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="ba4cf-111">Po wywołaniu, te metody zwracają zestaw węzłów, które można przejść za darmo przy użyciu <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="ba4cf-112">Nawigacja przy <xref:System.Xml.XPath.XPathNodeIterator> obiekt nie ma wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator> obiekt używany do jej utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="ba4cf-113"><xref:System.Xml.XPath.XPathNavigator> Obiektu zwróconego z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metody znajduje się na jednym węźle zwrócony i nie dotyczy również pozycja <xref:System.Xml.XPath.XPathNavigator> obiekt używany do jej utworzenia.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="ba4cf-114">W poniższym przykładzie pokazano tworzenie <xref:System.Xml.XPath.XPathNavigator> obiekt z <xref:System.Xml.XPath.XPathDocument> obiektu, użycie <xref:System.Xml.XPath.XPathNavigator.Select%2A> metody, aby wybrać węzły w <xref:System.Xml.XPath.XPathDocument> obiektu, a także korzystanie z <xref:System.Xml.XPath.XPathNodeIterator> obiekt, aby przejść przez wybrane węzły.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 <span data-ttu-id="ba4cf-115">Przykład przyjmuje `books.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="ba4cf-116">Zoptymalizowane metody</span><span class="sxs-lookup"><span data-stu-id="ba4cf-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="ba4cf-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, I <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy reprezentują wyrażenia XPath najczęściej używane do pobierania węzłów podrzędnych, podrzędnym i nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="ba4cf-118">Te metody są zoptymalizowane pod kątem wydajności i szybsze niż ich odpowiedniego wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="ba4cf-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, I <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody wybiera nadrzędne, podrzędne i węzłów elementów podrzędnych na podstawie <xref:System.Xml.XPath.XPathNodeType> wartość lub lokalna nazwa i identyfikator URI węzłów, aby wybrać przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="ba4cf-120">Wybranego elementu nadrzędnego, podrzędne i węzły podrzędne są zwracane w <xref:System.Xml.XPath.XPathNodeIterator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="ba4cf-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba4cf-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba4cf-121">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="ba4cf-122">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="ba4cf-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="ba4cf-123">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ba4cf-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="ba4cf-124">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="ba4cf-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [<span data-ttu-id="ba4cf-125">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="ba4cf-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="ba4cf-126">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="ba4cf-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="ba4cf-127">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="ba4cf-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
