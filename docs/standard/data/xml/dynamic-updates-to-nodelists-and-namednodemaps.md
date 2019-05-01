---
title: Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 76c511fd-6704-4ca4-8078-860a68d898ad
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9f56ba8711988f2f7d743dc4ff7b69272e2642a2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934475"
---
# <a name="dynamic-updates-to-nodelists-and-namednodemaps"></a><span data-ttu-id="643af-102">Aktualizacja dynamiczna obiektów NodeLists i NamedNodeMaps</span><span class="sxs-lookup"><span data-stu-id="643af-102">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>
<span data-ttu-id="643af-103">Ponieważ **XmlNodeList** i **XmlNamedNodeMap** zawierają zestaw węzłów, jeszcze dokument XML jest ładowany do pamięci i jest modyfikowana, World Wide Web Consortium (W3C) stwierdza, że te obiekty które zawierają zestawy węzły muszą być dynamiczne.</span><span class="sxs-lookup"><span data-stu-id="643af-103">Because the **XmlNodeList** and the **XmlNamedNodeMap** contain a set of nodes, yet the XML document is loaded into memory and is being modified, the World Wide Web Consortium (W3C) states that these objects that contain sets of nodes need to be dynamic.</span></span> <span data-ttu-id="643af-104">Oznacza to jeśli zmieni się dokumentu podstawowego, następnie dane w tych dwóch obiektów należy zmieniać również.</span><span class="sxs-lookup"><span data-stu-id="643af-104">That is, if the underlying document changes, then the data in these two objects should change also.</span></span> <span data-ttu-id="643af-105">W związku z tym jeśli masz **XmlNodeList** zawierający wszystkie elementy podrzędne danego elementu (na przykład element X), a następnie dodaj element dodatkowy element Q, do dokumentu w elemencie X. **XmlNodeList** powinien również zawierać tego nowego elementu w funkcji pytania i dodać do swojej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="643af-105">Therefore, if you have an **XmlNodeList** that contains all the child elements of a particular element (for example, element X), then you add an additional element, element Q, to the document under element X. The **XmlNodeList** should also have that new element Q added to its collection.</span></span> <span data-ttu-id="643af-106">Dotyczy to także w odwrotnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="643af-106">The same is true in reverse.</span></span> <span data-ttu-id="643af-107">Jeśli węzeł zostanie dodany do **XmlNodeList**, również zostanie zaktualizowany dokumentu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="643af-107">If a node is added to the **XmlNodeList**, the underlying document is updated as well.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643af-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="643af-108">See also</span></span>

- [<span data-ttu-id="643af-109">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="643af-109">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
