---
title: Zachowane odwołania do jednostek
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1c48e42e55025aff0ce1a24a3ef45ddf8005eab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934537"
---
# <a name="entity-references-are-preserved"></a>Zachowane odwołania do jednostek
Gdy odwołanie do jednostki nie jest rozwinięty, ale zachowane, XML Document Object Model (DOM) tworzy **XmlEntityReference** węzła po napotkaniu odwołania do jednostki.  
  
 Za pomocą następujący kod XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 kompilacje w modelu DOM **XmlEntityReference** węzła po napotkaniu `&publisher;` odwołania. **XmlEntityReference** zawiera węzły podrzędne, skopiowane z zawartości w deklaracji entity. W poprzednim przykładzie kodu zawiera tekst w deklaracji jednostki, więc **XmlText** węzeł jest tworzony jako węzeł podrzędny węzła odwołanie do jednostki.  
  
 ![Struktura zachowanych odwołań jednostki drzewa](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Strukturę drzewa dla odwołań do jednostek, które są zachowywane  
  
 Węzły podrzędne **XmlEntityReference** to kopie wszystkich podrzędnych węzłów przygotowane na podstawie **XmlEntity** węzła, gdy napotkano deklaracji entity.  
  
> [!NOTE]
>  Węzły skopiowane z **XmlEntity** nie zawsze są dokładne kopie raz umieszczone w węźle odwołania jednostki. Może to być przestrzenie nazw, które znajdują się w zakresie w węźle odwołania jednostki, a to ma wpływ na Konfiguracja końcowa węzłów podrzędnych.  
  
 Domyślnie, takich jak ogólne jednostek `&abc;` są zachowywane i **XmlEntityReference** węzłów przygotowane na zawsze.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
