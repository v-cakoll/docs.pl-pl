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
ms.openlocfilehash: 770c714e8f5942ea733c417ae9b06f69e4acf1a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 [Modelu obiektu dokumentu XML modelu DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
