---
title: Wybieranie danych XML przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
ms.openlocfilehash: 99b6b3b6959abf4c8adc313364ad641249bd9bc3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710170"
---
# <a name="select-xml-data-using-xpathnavigator"></a><span data-ttu-id="a8cc2-102">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a8cc2-102">Select XML Data Using XPathNavigator</span></span>
<span data-ttu-id="a8cc2-103">Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia zestaw metod służących do wybierania zestawu węzłów w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="a8cc2-104">Po wybraniu można wykonać iterację w wybranym zestawie węzłów.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-104">Once selected, you can iterate over the selected set of nodes.</span></span>  
  
## <a name="xpathnavigator-selection-methods"></a><span data-ttu-id="a8cc2-105">Metody wyboru XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a8cc2-105">XPathNavigator Selection Methods</span></span>  
 <span data-ttu-id="a8cc2-106">Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia zestaw metod służących do wybierania zestawu węzłów w obiekcie <xref:System.Xml.XPath.XPathDocument> lub <xref:System.Xml.XmlDocument> za pomocą wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-106">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span> <span data-ttu-id="a8cc2-107">Klasa <xref:System.Xml.XPath.XPathNavigator> udostępnia również zestaw zoptymalizowanych metod do wybierania obiektów nadrzędnych, podrzędnych i podrzędnych szybciej niż przy użyciu wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-107">The <xref:System.Xml.XPath.XPathNavigator> class also provides a set of optimized methods for selecting ancestor, child and descendant nodes faster than using an XPath expression.</span></span> <span data-ttu-id="a8cc2-108">Wybrany zestaw węzłów jest zwracany w obiekcie <xref:System.Xml.XPath.XPathNodeIterator> lub obiekcie <xref:System.Xml.XPath.XPathNavigator> w przypadku pojedynczego wybranego węzła.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-108">The selected set of nodes is returned in an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
### <a name="selecting-nodes-using-xpath-expressions"></a><span data-ttu-id="a8cc2-109">Wybieranie węzłów przy użyciu wyrażeń XPath</span><span class="sxs-lookup"><span data-stu-id="a8cc2-109">Selecting Nodes Using XPath Expressions</span></span>  
 <span data-ttu-id="a8cc2-110">Aby wybrać zestaw węzłów za pomocą wyrażenia XPath, należy użyć jednej z następujących metod wyboru.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-110">To select a set of nodes using an XPath expression, use one of the following selection methods.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 <span data-ttu-id="a8cc2-111">Po wywołaniu te metody zwracają zestaw węzłów, za pomocą których można swobodnie poruszać się przy użyciu obiektu <xref:System.Xml.XPath.XPathNodeIterator> lub obiektu <xref:System.Xml.XPath.XPathNavigator> w przypadku jednego wybranego węzła.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-111">When called, these methods return a set of nodes that you can navigate freely using an <xref:System.Xml.XPath.XPathNodeIterator> object or an <xref:System.Xml.XPath.XPathNavigator> object in the case of a single selected node.</span></span>  
  
 <span data-ttu-id="a8cc2-112">Nawigowanie przy użyciu obiektu <xref:System.Xml.XPath.XPathNodeIterator> nie wpływa na pozycję obiektu <xref:System.Xml.XPath.XPathNavigator>, który został użyty do jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-112">Navigating with an <xref:System.Xml.XPath.XPathNodeIterator> object does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span> <span data-ttu-id="a8cc2-113">Obiekt <xref:System.Xml.XPath.XPathNavigator> zwrócony z metod <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> jest umieszczony w pojedynczym zwracanym węźle, a także nie ma wpływu na pozycję obiektu <xref:System.Xml.XPath.XPathNavigator> użytego do jego utworzenia.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-113">The <xref:System.Xml.XPath.XPathNavigator> object returned from the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> methods is positioned on the single returned node and also does not affect the position of the <xref:System.Xml.XPath.XPathNavigator> object used to create it.</span></span>  
  
 <span data-ttu-id="a8cc2-114">W poniższym przykładzie pokazano Tworzenie obiektu <xref:System.Xml.XPath.XPathNavigator> z obiektu <xref:System.Xml.XPath.XPathDocument>, użycie metody <xref:System.Xml.XPath.XPathNavigator.Select%2A> do wybrania węzłów w obiekcie <xref:System.Xml.XPath.XPathDocument> i użycie obiektu <xref:System.Xml.XPath.XPathNodeIterator> do iteracji w wybranych węzłach.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-114">The following example shows the creation of an <xref:System.Xml.XPath.XPathNavigator> object from an <xref:System.Xml.XPath.XPathDocument> object, the use of the <xref:System.Xml.XPath.XPathNavigator.Select%2A> method to select nodes in the <xref:System.Xml.XPath.XPathDocument> object, and the use of the <xref:System.Xml.XPath.XPathNodeIterator> object to iterate over the selected nodes.</span></span>  
  
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
  
 <span data-ttu-id="a8cc2-115">Przykład pobiera `books.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-115">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a><span data-ttu-id="a8cc2-116">Zoptymalizowane metody zaznaczania</span><span class="sxs-lookup"><span data-stu-id="a8cc2-116">Optimized Selection Methods</span></span>  
 <span data-ttu-id="a8cc2-117">Metody <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>i <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> klasy <xref:System.Xml.XPath.XPathNavigator> reprezentują wyrażenia XPath często używane do pobierania węzłów podrzędnych, podrzędnych i nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-117">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class represent XPath expressions commonly used to retrieve child, descendant, and ancestor nodes.</span></span> <span data-ttu-id="a8cc2-118">Te metody są zoptymalizowane pod kątem wydajności i są szybsze niż odpowiednie wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-118">These methods are optimized for performance and are faster than their corresponding XPath expressions.</span></span> <span data-ttu-id="a8cc2-119">Metody <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>i <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> wybierają węzły nadrzędne, podrzędne i podrzędne na podstawie wartości <xref:System.Xml.XPath.XPathNodeType> lub nazwy lokalnej oraz identyfikatora URI przestrzeni nazw węzłów do wybrania.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-119">The <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, and <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> methods selects ancestor, child, and descendant nodes based on an <xref:System.Xml.XPath.XPathNodeType> value or the local name and namespace URI of the nodes to select.</span></span> <span data-ttu-id="a8cc2-120">Wybrane węzły nadrzędne, podrzędne i podrzędne są zwracane w obiekcie <xref:System.Xml.XPath.XPathNodeIterator>.</span><span class="sxs-lookup"><span data-stu-id="a8cc2-120">The selected ancestor, child, and descendant nodes are returned in an <xref:System.Xml.XPath.XPathNodeIterator> object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8cc2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8cc2-121">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="a8cc2-122">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="a8cc2-122">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="a8cc2-123">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a8cc2-123">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="a8cc2-124">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="a8cc2-124">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="a8cc2-125">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="a8cc2-125">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="a8cc2-126">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="a8cc2-126">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="a8cc2-127">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="a8cc2-127">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
