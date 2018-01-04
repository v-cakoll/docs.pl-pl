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
# <a name="entity-references-are-preserved"></a>Odwołania do jednostek zostaną zachowane.
Gdy odwołanie do jednostki nie jest rozwinięty, ale zachowane, XML modelu DOM (Document Object) tworzy **XmlEntityReference** węzła po napotkaniu odwołania do jednostki.  
  
 Przy użyciu następującego pliku XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 kompilacje w modelu DOM **XmlEntityReference** węzła po napotkaniu `&publisher;` odwołania. **XmlEntityReference** zawiera węzły podrzędne skopiowane z zawartości w deklaracji entity. W poprzednim przykładzie kodu zawiera tekst w deklaracji jednostki, więc **XmlText** jest tworzony węzeł jako węzeł podrzędny węzła odniesienia jednostki.  
  
 ![Struktura zachowanych odwołań jednostki drzewa](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Struktura drzewa dla odwołań do jednostek, które zostaną zachowane  
  
 Węzły podrzędne **XmlEntityReference** to kopie wszystkich podrzędnych węzłów utworzone na podstawie **XmlEntity** węzeł po napotkano deklaracji entity.  
  
> [!NOTE]
>  Węzły skopiowanych z **XmlEntity** nie zawsze są kopie dokładnie raz umieszczone w węźle odwołania jednostki. Może być przestrzenie nazw, które znajdują się w zakresie, w węźle odwołania jednostki i które dotyczy konfiguracji końcowej węzłów podrzędnych.  
  
 Domyślnie ogólne jednostek, takich jak `&abc;` zostaną zachowane i **XmlEntityReference** zawsze tworzona węzłów.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
