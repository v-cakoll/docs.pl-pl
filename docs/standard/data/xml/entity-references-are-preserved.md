---
title: Odwołania do jednostek są zachowywane.
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1c48e42e55025aff0ce1a24a3ef45ddf8005eab
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204324"
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="7ae12-102">Odwołania do jednostek są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="7ae12-102">Entity References are Preserved</span></span>
<span data-ttu-id="7ae12-103">Gdy odwołanie do jednostki nie jest rozwinięty, ale zachowane, XML Document Object Model (DOM) tworzy **XmlEntityReference** węzła po napotkaniu odwołania do jednostki.</span><span class="sxs-lookup"><span data-stu-id="7ae12-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="7ae12-104">Za pomocą następujący kod XML</span><span class="sxs-lookup"><span data-stu-id="7ae12-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="7ae12-105">kompilacje w modelu DOM **XmlEntityReference** węzła po napotkaniu `&publisher;` odwołania.</span><span class="sxs-lookup"><span data-stu-id="7ae12-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="7ae12-106">**XmlEntityReference** zawiera węzły podrzędne, skopiowane z zawartości w deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="7ae12-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="7ae12-107">W poprzednim przykładzie kodu zawiera tekst w deklaracji jednostki, więc **XmlText** węzeł jest tworzony jako węzeł podrzędny węzła odwołanie do jednostki.</span><span class="sxs-lookup"><span data-stu-id="7ae12-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="7ae12-108">![Struktura zachowanych odwołań jednostki drzewa](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="7ae12-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="7ae12-109">Strukturę drzewa dla odwołań do jednostek, które są zachowywane</span><span class="sxs-lookup"><span data-stu-id="7ae12-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="7ae12-110">Węzły podrzędne **XmlEntityReference** to kopie wszystkich podrzędnych węzłów przygotowane na podstawie **XmlEntity** węzła, gdy napotkano deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="7ae12-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ae12-111">Węzły skopiowane z **XmlEntity** nie zawsze są dokładne kopie raz umieszczone w węźle odwołania jednostki.</span><span class="sxs-lookup"><span data-stu-id="7ae12-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="7ae12-112">Może to być przestrzenie nazw, które znajdują się w zakresie w węźle odwołania jednostki, a to ma wpływ na Konfiguracja końcowa węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="7ae12-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="7ae12-113">Domyślnie, takich jak ogólne jednostek `&abc;` są zachowywane i **XmlEntityReference** węzłów przygotowane na zawsze.</span><span class="sxs-lookup"><span data-stu-id="7ae12-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ae12-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ae12-114">See also</span></span>

- [<span data-ttu-id="7ae12-115">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="7ae12-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
