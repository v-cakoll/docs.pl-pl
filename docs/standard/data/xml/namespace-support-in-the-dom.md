---
title: "Obsługa Namespace w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2b8135a55c537f480e0d595e127c2cad55e977ca
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="namespace-support-in-the-dom"></a><span data-ttu-id="89af8-102">Obsługa Namespace w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="89af8-102">Namespace Support in the DOM</span></span>
<span data-ttu-id="89af8-103">XML modelu DOM (Document Object) jest całkowicie przestrzeni nazw aware.</span><span class="sxs-lookup"><span data-stu-id="89af8-103">The XML Document Object Model (DOM) is completely namespace-aware.</span></span> <span data-ttu-id="89af8-104">Obsługiwane są tylko dokumenty obsługujących przestrzeń nazw XML.</span><span class="sxs-lookup"><span data-stu-id="89af8-104">Only namespace-aware XML documents are supported.</span></span> <span data-ttu-id="89af8-105">Sieci World Wide Web konsorcjum W3C Określa, czy aplikacje modelu DOM, które implementują poziomu 1 może być nie rozpoznający — przestrzeń nazw i funkcje DOM poziomu 2 rozpoznają przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="89af8-105">The World Wide Web Consortium (W3C) specifies that DOM applications that implement Level 1 can be non-namespace-aware, and DOM Level 2 features are namespace-aware.</span></span> <span data-ttu-id="89af8-106">Jednak są wszystkie funkcje w modelu DOM XML obsługujących przestrzeń nazw, niezależnie od tego, czy metoda jest z poziomu 1 lub poziom 2 DOM zalecenie.</span><span class="sxs-lookup"><span data-stu-id="89af8-106">However, all features in the XML DOM are namespace-aware, regardless if the method is from the Level 1 or Level 2 DOM Recommendation.</span></span>  
  
 <span data-ttu-id="89af8-107">Na przykład w środowisku nie rozpoznający — przestrzeń nazw wywoływania `setAttribute("A:b", "123")`, jak określono w modelu DOM poziomu 1 zalecenie, nie powoduje atrybutu z prefiksem `A` i nazwę lokalną `b`.</span><span class="sxs-lookup"><span data-stu-id="89af8-107">For example, in a non-namespace-aware setting, calling `setAttribute("A:b", "123")`, as specified in the DOM Level 1 Recommendation, does not result in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="89af8-108">Spowoduje to atrybut o wartości `A:b`.</span><span class="sxs-lookup"><span data-stu-id="89af8-108">It would result in an attribute with the value `A:b`.</span></span>  
  
 <span data-ttu-id="89af8-109">W środowisku obsługujących przestrzeń nazw wywołanie DOM poziomu 2 `setAttribute("A:b", "123")` powoduje atrybutu z prefiksem `A` i nazwę lokalną `b`.</span><span class="sxs-lookup"><span data-stu-id="89af8-109">In a namespace-aware environment, the call to the DOM Level 2 `setAttribute("A:b", "123")` results in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="89af8-110">Jest to, jak działa system Microsoft .NET Framework w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="89af8-110">This is how the Microsoft .NET Framework DOM works.</span></span>  
  
 <span data-ttu-id="89af8-111">W związku z tym dla wszystkich metod, które przyjmują parametr name, te metody także zająć prefiks nazwy.</span><span class="sxs-lookup"><span data-stu-id="89af8-111">Therefore, for all methods that take a name parameter, these methods also take a prefix to qualify the name.</span></span> <span data-ttu-id="89af8-112">Parametr name, takich jak `A:b` w **setAttribute** metodę modelu DOM poziomu 1 jest analizowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="89af8-112">The name parameter, such as the `A:b` in the **setAttribute** DOM Level 1 method, is parsed as follows:</span></span>  
  
-   <span data-ttu-id="89af8-113">Jeśli występują znaki nie dwukropka (:), a następnie ustawiono nazwę lokalną `name` parametru i prefiks i NamespaceURI są puste ciągi.</span><span class="sxs-lookup"><span data-stu-id="89af8-113">If there are no colon (:) characters, then the local name is set to the `name` parameter, and the prefix and NamespaceURI are empty strings.</span></span>  
  
-   <span data-ttu-id="89af8-114">Jeśli zostanie znaleziony dwukropek, nazwa jest podzielony na dwie części na podstawie położenia pierwszym znakiem dwukropka.</span><span class="sxs-lookup"><span data-stu-id="89af8-114">If a colon is found, then the name is split into two parts based on the position of the first colon character.</span></span> <span data-ttu-id="89af8-115">Prefiks jest ustawiona na ciąg znaleziono przed dwukropkiem, a nazwa lokalna jest ustawiona na ciąg po dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="89af8-115">The prefix is set to the string found before the colon, and local name is set to the string found after the colon.</span></span> <span data-ttu-id="89af8-116">Dla metod, które nie przyjmują wartości NamespaceURI, jego identyfikator NamespaceURI nie został rozwiązany i pozostanie ustawiony na pusty ciąg.</span><span class="sxs-lookup"><span data-stu-id="89af8-116">For methods that do not take a NamespaceURI value, the NamespaceURI is not resolved and remains set to empty string.</span></span> <span data-ttu-id="89af8-117">W przeciwnym razie jego identyfikator NamespaceURI ma ustawioną wartość ciągu przekazany do metody.</span><span class="sxs-lookup"><span data-stu-id="89af8-117">Otherwise, the NamespaceURI is set to the string passed to the method.</span></span> <span data-ttu-id="89af8-118">Jeśli zdefiniowano prefiksu, a następnie **zapisać** — metoda i **InnerXml** i **OuterXml** właściwości kończyć się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="89af8-118">If the prefix is undefined, then the **Save** method and **InnerXml** and **OuterXml** properties fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89af8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89af8-119">See Also</span></span>  
 [<span data-ttu-id="89af8-120">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="89af8-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
