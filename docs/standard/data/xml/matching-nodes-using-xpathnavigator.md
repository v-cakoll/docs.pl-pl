---
title: Dopasowywanie węzłów przy użyciu klasy XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: f0988c3a112fefc351175de02c790dc25fe6e94a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710690"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="31b85-102">Dopasowywanie węzłów przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="31b85-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="31b85-103">Klasa <xref:System.Xml.XPath.XPathNavigator> zapewnia metodę <xref:System.Xml.XPath.XPathNavigator.Matches%2A>, aby określić, czy węzeł dopasowuje wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="31b85-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="31b85-104">Metoda <xref:System.Xml.XPath.XPathNavigator.Matches%2A> przyjmuje wyrażenie XPath jako dane wejściowe i zwraca <xref:System.Boolean>, które wskazuje, czy bieżący węzeł odpowiada danemu wyrażeniu XPath lub podanemu skompilowanemu obiektowi <xref:System.Xml.XPath.XPathExpression>.</span><span class="sxs-lookup"><span data-stu-id="31b85-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="31b85-105">Zgodne węzły</span><span class="sxs-lookup"><span data-stu-id="31b85-105">Matching Nodes</span></span>  
 <span data-ttu-id="31b85-106">Metoda <xref:System.Xml.XPath.XPathNavigator.Matches%2A> zwraca `true`, jeśli bieżący węzeł pasuje do określonego wyrażenia XPath.</span><span class="sxs-lookup"><span data-stu-id="31b85-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="31b85-107">Na przykład w poniższym przykładzie kodu Metoda <xref:System.Xml.XPath.XPathNavigator.Matches%2A> zwróci `true`, jeśli bieżącym węzłem jest element `b`, a element `b` ma atrybut `c`.</span><span class="sxs-lookup"><span data-stu-id="31b85-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31b85-108">Metoda <xref:System.Xml.XPath.XPathNavigator.Matches%2A> nie zmienia stanu <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="31b85-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="31b85-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="31b85-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="31b85-110">Przetwarzanie danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="31b85-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="31b85-111">Wybieranie danych XML przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="31b85-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="31b85-112">Obliczanie wyrażeń XPath przy użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="31b85-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="31b85-113">Typy węzłów rozpoznawanych w zapytaniach XPath</span><span class="sxs-lookup"><span data-stu-id="31b85-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="31b85-114">Zapytania XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="31b85-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="31b85-115">Skompilowane wyrażenia XPath</span><span class="sxs-lookup"><span data-stu-id="31b85-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
