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
# <a name="entity-references-are-preserved"></a>Odwołania do jednostek są zachowywane.
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
