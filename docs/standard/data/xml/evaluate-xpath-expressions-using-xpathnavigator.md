---
title: Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8666aa9cb9f0512c600a77891b16f439c46995a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517412"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="dae97-102">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="dae97-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="dae97-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody ocena wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="dae97-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="dae97-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda przyjmuje wyrażenia XPath, oblicza ona i zwraca typ W3C XPath atrybut typu wartość logiczna, liczba, ciąg lub zestaw węzłów na podstawie wyniku wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="dae97-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="dae97-105">Oceń — metoda</span><span class="sxs-lookup"><span data-stu-id="dae97-105">The Evaluate Method</span></span>  
 <span data-ttu-id="dae97-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda przyjmuje wyrażenia XPath, oblicza ona i zwraca wynik typizowaną wartość logiczna (<xref:System.Boolean>), liczba (<xref:System.Double>), ciąg (<xref:System.String>), lub zestaw węzłów (<xref:System.Xml.XPath.XPathNodeIterator>).</span><span class="sxs-lookup"><span data-stu-id="dae97-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="dae97-107">Na przykład <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metoda może być użyta w metodzie matematyczne.</span><span class="sxs-lookup"><span data-stu-id="dae97-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="dae97-108">Poniższy przykład kodu oblicza całkowita cena wszystkie książki w `books.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="dae97-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="dae97-109">Przykład przyjmuje `books.xml` pliku jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="dae97-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="dae97-110">położenie i ostatniej funkcji</span><span class="sxs-lookup"><span data-stu-id="dae97-110">position and last Functions</span></span>  
 <span data-ttu-id="dae97-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Jest przeciążona metoda.</span><span class="sxs-lookup"><span data-stu-id="dae97-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="dae97-112">Jedną z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metod przyjmuje <xref:System.Xml.XPath.XPathNodeIterator> obiektu jako parametr.</span><span class="sxs-lookup"><span data-stu-id="dae97-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="dae97-113">Tej konkretnej <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody jest taka sama jak <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metody, która przyjmuje tylko <xref:System.Xml.XPath.XPathExpression> obiektu jako parametru, z tą różnicą, że umożliwia argument do określania bieżącego kontekstu, aby wykonać obliczenie na zestaw węzłów.</span><span class="sxs-lookup"><span data-stu-id="dae97-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="dae97-114">Ten kontekst jest wymagany dla wyrażenia XPath `position()` i `last()` funkcji, ponieważ są one względem bieżącego węzła kontekstu.</span><span class="sxs-lookup"><span data-stu-id="dae97-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="dae97-115">O ile nie jest używana jako predykat w kroku lokalizacji `position()` i `last()` funkcje wymagają odwołania do węzła, ustaw umożliwia ocenienie w przeciwnym razie `position` i `last` funkcje zwracają `0`.</span><span class="sxs-lookup"><span data-stu-id="dae97-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dae97-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dae97-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="dae97-117">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="dae97-117">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="dae97-118">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="dae97-118">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="dae97-119">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="dae97-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="dae97-120">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="dae97-120">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="dae97-121">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="dae97-121">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="dae97-122">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="dae97-122">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
