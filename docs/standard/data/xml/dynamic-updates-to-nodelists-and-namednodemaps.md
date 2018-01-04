---
title: Dynamiczne aktualizacje NodeLists i NamedNodeMaps
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a7abbb7344530ca993b8d07b774da17e6d0349b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="2a658-102">Dynamiczne aktualizacje NodeLists i NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="2a658-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="2a658-103">Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawiera zestaw węzłów jeszcze dokumentu XML jest ładowany do pamięci i jest modyfikowana, sieci World Wide Web konsorcjum W3C stwierdza, że te obiekty które zawierają zestawy węzły muszą być dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="2a658-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="2a658-104">Oznacza to jeśli zmieni się dokumentu podstawowego, następnie dane w tych dwóch obiektów należy także zmienić.</span><span class="sxs-lookup"><span data-stu-id="2a658-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="2a658-105">W związku z tym jeśli masz **XmlNodeList** zawierający wszystkie elementy podrzędne danego elementu (na przykład element X), a następnie dodaj element dodatkowy element Q, do dokumentu w elemencie X. **XmlNodeList** powinien również zawierać ten nowy element Q dodane do pobrania.</span><span class="sxs-lookup"><span data-stu-id="2a658-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="2a658-106">To samo dotyczy odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="2a658-106">The same is true in reverse.</span></span> <span data-ttu-id="2a658-107">Jeśli węzeł zostanie dodany do **XmlNodeList**, również zostanie zaktualizowany dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="2a658-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a658-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a658-108">See Also</span></span>  
 [<span data-ttu-id="2a658-109">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="2a658-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
