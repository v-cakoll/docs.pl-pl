---
title: Wybieranie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fea54d36759b12b01fa7a68748d069c7890d84e4
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2018
ms.locfileid: "46711327"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="5d39a-102">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5d39a-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="5d39a-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, używany do wybierania zestaw węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="5d39a-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="5d39a-104">Po wybraniu, można wykonać iterację przez wybrany zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="5d39a-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="5d39a-105">Metody wyboru klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5d39a-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="5d39a-106"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, używany do wybierania zestaw węzłów w <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> obiekt, za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="5d39a-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="5d39a-107"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia także zestaw zoptymalizowanych metod szybciej niż przy użyciu wyrażenie XPath wybierania węzłów nadrzędnych i podrzędnych obiekt podrzędny.</span><span class="sxs-lookup"><span data-stu-id="5d39a-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="5d39a-108">Wybrany zestaw węzłów jest zwracany w <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.</span><span class="sxs-lookup"><span data-stu-id="5d39a-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="5d39a-109">Wybieranie węzłów za pomocą wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="5d39a-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="5d39a-110">Aby wybrać zestaw węzłów za pomocą wyrażenia XPath, użyj jednej z następujących metod zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="5d39a-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="5d39a-111">Gdy zostanie wywołana, te metody zwracają zestaw węzłów, które możesz przejść za darmo przy użyciu <xref:System.Xml.XPath.XPathNodeIterator> obiektu lub <xref:System.Xml.XPath.XPathNavigator> obiektu w przypadku jednego wybranego węzła.</span><span class="sxs-lookup"><span data-stu-id="5d39a-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="5d39a-112">Nawigacja przy <xref:System.Xml.XPath.XPathNodeIterator> obiekt nie ma wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator> obiekt użyty do jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="5d39a-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="5d39a-113"><xref:System.Xml.XPath.XPathNavigator> Obiekt zwracany z <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> metod znajduje się w pojedynczym węźle zwracane i również nie ma wpływu na pozycję <xref:System.Xml.XPath.XPathNavigator> obiekt użyty do jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="5d39a-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="5d39a-114">W poniższym przykładzie pokazano tworzenie <xref:System.Xml.XPath.XPathNavigator> obiektu z <xref:System.Xml.XPath.XPathDocument> obiektu, korzystanie z <xref:System.Xml.XPath.XPathNavigator.Select%2A> metodę, aby wybrać węzły w <xref:System.Xml.XPath.XPathDocument> obiektu, a także korzystanie z <xref:System.Xml.XPath.XPathNodeIterator> obiektu do wykonywania iteracji wybranych węzłów.</span><span class="sxs-lookup"><span data-stu-id="5d39a-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
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
  
 <span data-ttu-id="5d39a-115">Przykład przyjmuje `books.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="5d39a-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="5d39a-116">Zoptymalizowane metody</span><span class="sxs-lookup"><span data-stu-id="5d39a-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="5d39a-117"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, I <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody <xref:System.Xml.XPath.XPathNavigator> klasy reprezentują wyrażenia XPath, które często używane do pobierania węzłów podrzędnych, obiekt podrzędny i nadrzędny.</span><span class="sxs-lookup"><span data-stu-id="5d39a-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="5d39a-118">Te metody są zoptymalizowane pod kątem wydajności i są szybsze niż ich odpowiednich wyrażeń XPath.</span><span class="sxs-lookup"><span data-stu-id="5d39a-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="5d39a-119"><xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, I <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> metody wybiera elementu nadrzędnego, podrzędnego i węzłów podrzędnych, na podstawie <xref:System.Xml.XPath.XPathNodeType> wartość lub lokalna nazwa i identyfikator URI węzłów, aby wybrać przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5d39a-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="5d39a-120">Wybranego elementu nadrzędnego, podrzędnego i węzły podrzędne, które są zwracane w <xref:System.Xml.XPath.XPathNodeIterator> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5d39a-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d39a-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d39a-121">See also</span></span>

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [<span data-ttu-id="5d39a-122">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="5d39a-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [<span data-ttu-id="5d39a-123">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5d39a-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
- [<span data-ttu-id="5d39a-124">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="5d39a-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [<span data-ttu-id="5d39a-125">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="5d39a-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [<span data-ttu-id="5d39a-126">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="5d39a-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [<span data-ttu-id="5d39a-127">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="5d39a-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
