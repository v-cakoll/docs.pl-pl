---
title: "Odwołania do jednostek zostaną zachowane."
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f5a867d1301355f4c9a77654556229274f96d00c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="abd3b-102">Odwołania do jednostek zostaną zachowane.</span><span class="sxs-lookup"><span data-stu-id="abd3b-102">Entity References are Preserved</span></span>
<span data-ttu-id="abd3b-103">Gdy odwołanie do jednostki nie jest rozwinięty, ale zachowane, XML modelu DOM (Document Object) tworzy **XmlEntityReference** węzła po napotkaniu odwołania do jednostki.</span><span class="sxs-lookup"><span data-stu-id="abd3b-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="abd3b-104">Przy użyciu następującego pliku XML</span><span class="sxs-lookup"><span data-stu-id="abd3b-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="abd3b-105">kompilacje w modelu DOM **XmlEntityReference** węzła po napotkaniu `&publisher;` odwołania.</span><span class="sxs-lookup"><span data-stu-id="abd3b-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="abd3b-106">**XmlEntityReference** zawiera węzły podrzędne skopiowane z zawartości w deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="abd3b-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="abd3b-107">W poprzednim przykładzie kodu zawiera tekst w deklaracji jednostki, więc **XmlText** jest tworzony węzeł jako węzeł podrzędny węzła odniesienia jednostki.</span><span class="sxs-lookup"><span data-stu-id="abd3b-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="abd3b-108">![Struktura zachowanych odwołań jednostki drzewa](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="abd3b-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="abd3b-109">Struktura drzewa dla odwołań do jednostek, które zostaną zachowane</span><span class="sxs-lookup"><span data-stu-id="abd3b-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="abd3b-110">Węzły podrzędne **XmlEntityReference** to kopie wszystkich podrzędnych węzłów utworzone na podstawie **XmlEntity** węzeł po napotkano deklaracji entity.</span><span class="sxs-lookup"><span data-stu-id="abd3b-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abd3b-111">Węzły skopiowanych z **XmlEntity** nie zawsze są kopie dokładnie raz umieszczone w węźle odwołania jednostki.</span><span class="sxs-lookup"><span data-stu-id="abd3b-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="abd3b-112">Może być przestrzenie nazw, które znajdują się w zakresie, w węźle odwołania jednostki i które dotyczy konfiguracji końcowej węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="abd3b-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="abd3b-113">Domyślnie ogólne jednostek, takich jak `&abc;` zostaną zachowane i **XmlEntityReference** zawsze tworzona węzłów.</span><span class="sxs-lookup"><span data-stu-id="abd3b-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd3b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abd3b-114">See Also</span></span>  
 [<span data-ttu-id="abd3b-115">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="abd3b-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
