---
title: Tworzenie nowych odwołań do jednostek
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67fdbcdbff64bcd91c80fbeaec0c41982b68d98f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46561127"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="411e0-102">Tworzenie nowych odwołań do jednostek</span><span class="sxs-lookup"><span data-stu-id="411e0-102">Creating New Entity References</span></span>
<span data-ttu-id="411e0-103">**CreateEntityReference** metoda tworzy nowy **XmlEntityReference** węzła.</span><span class="sxs-lookup"><span data-stu-id="411e0-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="411e0-104">XML Document Object Model (DOM) sprawdza, jeśli został już zadeklarowany nazwa jednostki, do którego nastąpiło odwołanie.</span><span class="sxs-lookup"><span data-stu-id="411e0-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="411e0-105">Jeśli tak, węzły podrzędne **XmlEntityReference** węzłów są kopiowane z węzła deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="411e0-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="411e0-106">W przypadku deklaracja nie jednostki, który odpowiada pusty węzeł tekstowy jest dołączony jako tylko element podrzędny węzła odwołanie do jednostki.</span><span class="sxs-lookup"><span data-stu-id="411e0-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="411e0-107">Ponieważ węzły podrzędne **XmlEntityReference** węzła to kopie innych węzłów, tych węzłów podrzędnych są przeznaczone tylko do odczytu i nie może być modyfikowany.</span><span class="sxs-lookup"><span data-stu-id="411e0-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="411e0-108">Jeśli węzły są kopiowane, w zakresie punkcie odwołania do jednostki może powstać przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="411e0-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="411e0-109">Ta przestrzeń nazw ma wpływ na konfigurację węzłów elementów lub atrybutów generowane.</span><span class="sxs-lookup"><span data-stu-id="411e0-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="411e0-110">Model DOM dodaje węzły podrzędne **EntityReference** tylko po wstawieniu **EntityReference** węzeł w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="411e0-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="411e0-111">Nowo utworzony **EntityReference** węzły mają bez węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="411e0-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="411e0-112">Mimo że **XmlDataDocument** klasy pochodnej jest **XmlDocument**, **XmlDataDocument** nie obsługuje tworzenia odwołań do jednostek.</span><span class="sxs-lookup"><span data-stu-id="411e0-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="411e0-113">Jest to spowodowane **EntityReference** elementy podrzędne są przeznaczone tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="411e0-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="411e0-114">Elementy podrzędne **EntityReference** węzła może obejmować więcej niż jednym regionie.</span><span class="sxs-lookup"><span data-stu-id="411e0-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="411e0-115">W tym przypadku część wiersz skojarzony region, który zawiera część **EntityReference** będą tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="411e0-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411e0-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="411e0-116">See also</span></span>

- [<span data-ttu-id="411e0-117">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="411e0-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
