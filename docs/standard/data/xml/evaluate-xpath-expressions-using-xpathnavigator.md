---
title: Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: b6e18fe02a828ae307ac7ade15650d3303f2600c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287808"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="92c3f-102">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="92c3f-102">Evaluate XPath Expressions using XPathNavigator</span></span>
<span data-ttu-id="92c3f-103"><xref:System.Xml.XPath.XPathNavigator>Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metodę szacowania wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="92c3f-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="92c3f-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda przyjmuje wyrażenie XPath, szacuje go i zwraca typ W3C XPath o wartości logicznej, liczb, ciągu lub zestawu węzłów na podstawie wyniku wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="92c3f-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="92c3f-105">Metoda szacowania</span><span class="sxs-lookup"><span data-stu-id="92c3f-105">The Evaluate Method</span></span>  
 <span data-ttu-id="92c3f-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda przyjmuje wyrażenie XPath, oblicza go i zwraca wynik z typem Boolean ( <xref:System.Boolean> ), Number ( <xref:System.Double> ), String ( <xref:System.String> ) lub Set ( <xref:System.Xml.XPath.XPathNodeIterator> ).</span><span class="sxs-lookup"><span data-stu-id="92c3f-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="92c3f-107">Na przykład <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda może być użyta w metodzie matematycznej.</span><span class="sxs-lookup"><span data-stu-id="92c3f-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="92c3f-108">Poniższy przykładowy kod oblicza łączną cenę wszystkich ksiąg w `books.xml` pliku.</span><span class="sxs-lookup"><span data-stu-id="92c3f-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
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
  
 <span data-ttu-id="92c3f-109">Przykład pobiera `books.xml` plik jako dane wejściowe.</span><span class="sxs-lookup"><span data-stu-id="92c3f-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="92c3f-110">Funkcja position i Last</span><span class="sxs-lookup"><span data-stu-id="92c3f-110">position and last Functions</span></span>  
 <span data-ttu-id="92c3f-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Metoda jest przeciążona.</span><span class="sxs-lookup"><span data-stu-id="92c3f-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="92c3f-112">Jedna z <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> metod przyjmuje <xref:System.Xml.XPath.XPathNodeIterator> obiekt jako parametr.</span><span class="sxs-lookup"><span data-stu-id="92c3f-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="92c3f-113">Ta konkretna <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda jest taka sama jak <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Metoda, która przyjmuje tylko <xref:System.Xml.XPath.XPathExpression> obiekt jako parametr, z tą różnicą, że zezwala na argument zestawu węzłów, aby określić bieżący kontekst do przeprowadzenia oceny.</span><span class="sxs-lookup"><span data-stu-id="92c3f-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="92c3f-114">Ten kontekst jest wymagany dla wyrażenia XPath `position()` i `last()` funkcji, ponieważ odnoszą się do bieżącego węzła kontekstu.</span><span class="sxs-lookup"><span data-stu-id="92c3f-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="92c3f-115">O ile nie jest używany jako predykat w kroku lokalizacji, `position()` `last()` funkcje i wymagają odwołania do zestawu węzłów, aby można je było oszacować w przeciwnym razie `position` funkcje i `last` zwracają `0` .</span><span class="sxs-lookup"><span data-stu-id="92c3f-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c3f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92c3f-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="92c3f-117">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="92c3f-117">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="92c3f-118">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="92c3f-118">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="92c3f-119">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="92c3f-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="92c3f-120">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="92c3f-120">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="92c3f-121">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="92c3f-121">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="92c3f-122">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="92c3f-122">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
