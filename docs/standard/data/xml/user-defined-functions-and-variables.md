---
title: "Funkcje i zmienne zdefiniowane przez użytkownika"
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
ms.assetid: 4772f20e-1e7f-496e-93c2-1484473be555
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b6870861541a063c56f83dcb286d21a5a970d1b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="user-defined-functions-and-variables"></a><span data-ttu-id="fa48e-102">Funkcje i zmienne zdefiniowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="fa48e-102">User Defined Functions and Variables</span></span>
<span data-ttu-id="fa48e-103"><xref:System.Xml.XPath.XPathNavigator> Klasa udostępnia zestaw metod, które są używane do interakcji z <xref:System.Xml.XPath.XPathDocument> danych.</span><span class="sxs-lookup"><span data-stu-id="fa48e-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods that are used to interact with <xref:System.Xml.XPath.XPathDocument> data.</span></span> <span data-ttu-id="fa48e-104">Standardowe funkcje XPath można uzupełnić zaimplementowanie rozszerzenia funkcje i zmienne do użytku przez wyrażenia zapytania XPath.</span><span class="sxs-lookup"><span data-stu-id="fa48e-104">You can supplement the standard XPath functions by implementing extension functions and variables for use by XPath query expressions.</span></span> <span data-ttu-id="fa48e-105"><xref:System.Xml.XPath.XPathExpression.SetContext%2A> Metody może zaakceptować kontekst zdefiniowane przez użytkownika pochodzące z <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="fa48e-105">The <xref:System.Xml.XPath.XPathExpression.SetContext%2A> method can accept a user defined context derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="fa48e-106">Funkcje zdefiniowane przez użytkownika są rozpoznawane przez kontekst niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fa48e-106">User defined functions are resolved by the custom context.</span></span>  
  
 <span data-ttu-id="fa48e-107">Rozszerzenie funkcji i zmiennych, może być przydatne w zapobieganiu atakom iniekcji kodu XML.</span><span class="sxs-lookup"><span data-stu-id="fa48e-107">Extension functions and variables can be useful in prevention of XML injection attacks.</span></span> <span data-ttu-id="fa48e-108">W tych scenariuszach danych wejściowych użytkownika jest przypisany do niestandardowych zmiennych i przetwarzane przez funkcje rozszerzeń nie jako nieprzetworzone dane wejściowe, połączony z instrukcji przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="fa48e-108">In these scenarios user input is assigned to custom variables and processed by extension functions, not as raw input concatenated with processing instructions.</span></span> <span data-ttu-id="fa48e-109">Rozszerzenie funkcje i zmienne zawierają dane wejściowe użytkownika tak, aby tylko pełnił w danych XML zgodnie z założeniami przez projektanta.</span><span class="sxs-lookup"><span data-stu-id="fa48e-109">Extension functions and variables contain user input so that it only acts on XML data as intended by the designer.</span></span>  
  
 <span data-ttu-id="fa48e-110">Aby korzystać z rozszerzeń zaimplementowania niestandardowego <xref:System.Xml.Xsl.XsltContext> klasy wraz z interfejsów <xref:System.Xml.Xsl.IXsltContextFunction> i <xref:System.Xml.Xsl.IXsltContextVariable> obsługujących rozszerzenia funkcje i zmienne.</span><span class="sxs-lookup"><span data-stu-id="fa48e-110">To use extensions you implement a custom <xref:System.Xml.Xsl.XsltContext> class along with the interfaces <xref:System.Xml.Xsl.IXsltContextFunction> and <xref:System.Xml.Xsl.IXsltContextVariable> that support extension functions and variables.</span></span> <span data-ttu-id="fa48e-111"><xref:System.Xml.XPath.XPathExpression> Dodaje dane wejściowe użytkownika z jego <xref:System.Xml.Xsl.XsltArgumentList> niestandardowe <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="fa48e-111">An <xref:System.Xml.XPath.XPathExpression> adds user input with its <xref:System.Xml.Xsl.XsltArgumentList> to the custom <xref:System.Xml.Xsl.XsltContext>.</span></span>  
  
 <span data-ttu-id="fa48e-112"><xref:System.Xml.XPath.XPathExpression> Reprezentuje skompilowane zapytanie <xref:System.Xml.XPath.XPathNavigator> używa do znalezienia i przetworzyć węzłów zidentyfikowane przez wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="fa48e-112">The <xref:System.Xml.XPath.XPathExpression> represents a compiled query that <xref:System.Xml.XPath.XPathNavigator> uses to find and process the nodes identified by the expression.</span></span>  
  
 <span data-ttu-id="fa48e-113">W poniższym przykładzie przedstawiono Implementacja klasy kontekstowych pochodną <xref:System.Xml.Xsl.XsltContext>.</span><span class="sxs-lookup"><span data-stu-id="fa48e-113">The following example shows implementation of a custom context class derived from <xref:System.Xml.Xsl.XsltContext>.</span></span> <span data-ttu-id="fa48e-114">Komentarze w kodzie opisano elementy członkowskie klasy i ich użycie w funkcji niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fa48e-114">Comments in the code describe class members and their use in custom functions.</span></span> <span data-ttu-id="fa48e-115">Implementacje funkcji i zmiennej i przykładowej aplikacji, która używa tych implementacji wykonaj ten segment kodu.</span><span class="sxs-lookup"><span data-stu-id="fa48e-115">Function and variable implementations and a sample application that uses these implementations follow this code segment.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#2](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#2)]
 [!code-vb[XPathExtensionFunctions#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#2)]  
  
 <span data-ttu-id="fa48e-116">Poniższy kod implementuje <xref:System.Xml.Xsl.IXsltContextFunction>.</span><span class="sxs-lookup"><span data-stu-id="fa48e-116">The following code implements <xref:System.Xml.Xsl.IXsltContextFunction>.</span></span> <span data-ttu-id="fa48e-117">Klasa implementująca <xref:System.Xml.Xsl.IXsltContextFunction> rozpoznaje i wykonuje funkcje zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fa48e-117">The class that implements <xref:System.Xml.Xsl.IXsltContextFunction> resolves and executes user-defined functions.</span></span> <span data-ttu-id="fa48e-118">W tym przykładzie użyto funkcji określone przez deklarację: `private int CountChar(string title, char charTocount)`.</span><span class="sxs-lookup"><span data-stu-id="fa48e-118">This example uses the function identified by the declaration: `private int CountChar(string title, char charTocount)`.</span></span>  
  
 <span data-ttu-id="fa48e-119">Komentarze w kodzie opisano elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="fa48e-119">Code comments describe class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#3](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#3)]
 [!code-vb[XPathExtensionFunctions#3](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#3)]  
  
 <span data-ttu-id="fa48e-120">Poniższy kod implementuje <xref:System.Xml.Xsl.IXsltContextVariable>.</span><span class="sxs-lookup"><span data-stu-id="fa48e-120">The following code implements <xref:System.Xml.Xsl.IXsltContextVariable>.</span></span> <span data-ttu-id="fa48e-121">Ta klasa jest rozpoznawany jako odwołań do zmiennych zdefiniowanych przez użytkownika w wyrażeniach kwerend XPath w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fa48e-121">This class resolves references to user-defined variables in XPath query expressions at run time.</span></span> <span data-ttu-id="fa48e-122">Wystąpienia tej klasy jest tworzone i zwrócony przez przesłoniętych <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> metoda niestandardowa <xref:System.Xml.Xsl.XsltContext> klasy.</span><span class="sxs-lookup"><span data-stu-id="fa48e-122">An instance of this class is created and returned by the overridden <xref:System.Xml.Xsl.XsltContext.ResolveVariable%2A> method of the custom <xref:System.Xml.Xsl.XsltContext> class.</span></span>  
  
 <span data-ttu-id="fa48e-123">Komentarze w kodzie opisano elementy członkowskie klasy.</span><span class="sxs-lookup"><span data-stu-id="fa48e-123">Code comments describe the class members.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#4](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#4)]
 [!code-vb[XPathExtensionFunctions#4](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#4)]  
  
 <span data-ttu-id="fa48e-124">Z poprzednich definicje klas w zakresie następujący kod funkcja niestandardowych liczba znaków w elementach `Tasks.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fa48e-124">With the previous class definitions in scope, the following code uses the custom function to count characters in the elements of the `Tasks.xml` document.</span></span> <span data-ttu-id="fa48e-125">Komentarze w kodzie opisano kod funkcji niestandardowej kompiluje i uruchamia go przed `Tasks.xml` dokumentu.</span><span class="sxs-lookup"><span data-stu-id="fa48e-125">Comments in the code describe the code that compiles the custom function and runs it against the `Tasks.xml` document.</span></span>  
  
 [!code-csharp[XPathExtensionFunctions#1](../../../../samples/snippets/csharp/VS_Snippets_Data/xpathextensionfunctions/cs/xpathextensionfunctions.cs#1)]
 [!code-vb[XPathExtensionFunctions#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/xpathextensionfunctions/vb/xpathextensionfunctions.vb#1)]  
  
 <span data-ttu-id="fa48e-126">W tym przykładzie używane są następujące dane XML.</span><span class="sxs-lookup"><span data-stu-id="fa48e-126">This example uses the following XML data.</span></span>  
  
 [!code-xml[XPathExtensionFunctions#5](../../../../samples/snippets/xml/VS_Snippets_Data/xpathextensionfunctions/XML/tasks.xml#5)]
