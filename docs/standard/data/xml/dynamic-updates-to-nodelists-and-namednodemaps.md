---
title: Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
ms.openlocfilehash: 0199f24e9ef8dd28f91976edd50f78399dc893ef
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292088"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="dcbfb-102">Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="dcbfb-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="dcbfb-103">Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawierają zestaw węzłów, a dokument XML jest ładowany do pamięci i jest modyfikowany, organizacja World Wide Web Consortium (W3C) stwierdza, że te obiekty, które zawierają zestawy węzłów, muszą być dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="dcbfb-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="dcbfb-104">Oznacza to, że jeśli dokument źródłowy ulegnie zmianie, dane w tych dwóch obiektach powinny być również zmienione.</span><span class="sxs-lookup"><span data-stu-id="dcbfb-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="dcbfb-105">W związku z tym, jeśli masz element **XmlNodeList** , który zawiera wszystkie elementy podrzędne określonego elementu (na przykład element x), następnie Dodaj dodatkowy element, element Q do dokumentu w obszarze element x. **XmlNodeList** powinien również mieć dodany nowy element Q do swojej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="dcbfb-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="dcbfb-106">Ta sama wartość dotyczy odwrócenia.</span><span class="sxs-lookup"><span data-stu-id="dcbfb-106">The same is true in reverse.</span></span> <span data-ttu-id="dcbfb-107">Jeśli węzeł zostanie dodany do **XmlNodeList**, dokument źródłowy również zostanie zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="dcbfb-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcbfb-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcbfb-108">See also</span></span>

- [<span data-ttu-id="dcbfb-109">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="dcbfb-109">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
