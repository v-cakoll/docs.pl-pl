---
title: "Tworzenie nowego odwołania do jednostek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22e9b66f58275141cf9da154573ca43a0b90affc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="e8e75-102">Tworzenie nowego odwołania do jednostek</span><span class="sxs-lookup"><span data-stu-id="e8e75-102">Creating New Entity References</span></span>
<span data-ttu-id="e8e75-103">**CreateEntityReference** metoda tworzy nowy **XmlEntityReference** węzła.</span><span class="sxs-lookup"><span data-stu-id="e8e75-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="e8e75-104">XML modelu DOM (Document Object) sprawdza, czy nazwa jednostki, do którego nastąpiło odwołanie została już zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="e8e75-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="e8e75-105">Jeśli tak, węzły podrzędne **XmlEntityReference** węzła są kopiowane z węzła deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="e8e75-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="e8e75-106">Jeśli nie ma żadnych deklaracji jednostki, która jest zgodna, węzeł pusty tekst jest dołączony jako element podrzędny tylko jednostki węzła odniesienia.</span><span class="sxs-lookup"><span data-stu-id="e8e75-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="e8e75-107">Ponieważ węzły podrzędne **XmlEntityReference** węzła to kopie inne węzły, te węzły podrzędne są tylko do odczytu i nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="e8e75-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="e8e75-108">W przypadku kopiowania węzły, w zakresie w punkcie odwołanie do jednostki mogą istnieć przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e8e75-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="e8e75-109">Ta przestrzeń nazw wpływa na konfigurację węzły elementu lub atrybutu wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="e8e75-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8e75-110">Węzły podrzędne dodaje modelu DOM **EntityReference** tylko po wstawieniu **EntityReference** węzła do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e8e75-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="e8e75-111">Nowo utworzona **EntityReference** węzły mają bez węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="e8e75-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="e8e75-112">Mimo że **dokumentu XmlDataDocument** jest klasy pochodnej z **XmlDocument**, **dokumentu XmlDataDocument** nie obsługuje tworzenia odwołań do jednostek.</span><span class="sxs-lookup"><span data-stu-id="e8e75-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="e8e75-113">Jest to spowodowane **EntityReference** elementy podrzędne są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="e8e75-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="e8e75-114">Elementy podrzędne **EntityReference** węzeł może obejmować więcej niż jeden region.</span><span class="sxs-lookup"><span data-stu-id="e8e75-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="e8e75-115">W takim przypadku część wiersz skojarzony z regionu, który zawiera część **EntityReference** będą tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="e8e75-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e75-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8e75-116">See Also</span></span>  
 [<span data-ttu-id="e8e75-117">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="e8e75-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
