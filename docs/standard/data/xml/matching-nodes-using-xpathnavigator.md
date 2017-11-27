---
title: "Zgodne węzły użyciu klasy XPathNavigator"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a51c358ecb50c94ccde9f86ba80fc8f0670f82d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="31551-102">Zgodne węzły użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="31551-102">Matching Nodes using XPathNavigator</span></span>
<span data-ttu-id="31551-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metodę, aby określić, czy węzeł zgodne wyrażenie XPath.</span><span class="sxs-lookup"><span data-stu-id="31551-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="31551-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda pobiera wyrażenie XPath jako dane wejściowe i zwraca <xref:System.Boolean> wskazująca, czy bieżący węzeł zgodne danego wyrażenia XPath lub podane skompilowanych <xref:System.Xml.XPath.XPathExpression> obiektu.</span><span class="sxs-lookup"><span data-stu-id="31551-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="31551-105">Zgodne węzły</span><span class="sxs-lookup"><span data-stu-id="31551-105">Matching Nodes</span></span>  
 <span data-ttu-id="31551-106"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> Metoda zwraca `true` Jeśli określono wyrażenie XPath pasuje do bieżącego węzła.</span><span class="sxs-lookup"><span data-stu-id="31551-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="31551-107">Na przykład w przykładzie poniżej <xref:System.Xml.XPath.XPathNavigator.Matches%2A> metoda zwróci `true` Jeśli bieżący węzeł jest elementem `b`, a element `b` ma atrybut `c`.</span><span class="sxs-lookup"><span data-stu-id="31551-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31551-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> — Metoda nie zmienia stanu <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="31551-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="31551-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31551-109">See Also</span></span>  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [<span data-ttu-id="31551-110">Przetwarzania danych XML przy użyciu modelu danych XPath</span><span class="sxs-lookup"><span data-stu-id="31551-110">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [<span data-ttu-id="31551-111">Wybierz dane XML przy użyciu parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="31551-111">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [<span data-ttu-id="31551-112">Ocena wyrażenia XPath użyciu klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="31551-112">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [<span data-ttu-id="31551-113">Typy węzłów rozpoznany z kwerendy XPath</span><span class="sxs-lookup"><span data-stu-id="31551-113">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [<span data-ttu-id="31551-114">Kwerendy XPath i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="31551-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [<span data-ttu-id="31551-115">Wyrażenia XPath skompilowanych</span><span class="sxs-lookup"><span data-stu-id="31551-115">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
