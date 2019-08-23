---
title: Zachowane odwołania do jednostek
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e512f2077c2e6b9feba5024c4eabc2568357ecab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965914"
---
# <a name="entity-references-are-preserved"></a>Zachowane odwołania do jednostek
Gdy odwołanie do jednostki nie jest rozwinięte, ale zachowane, Document Object Model XML (DOM) kompiluje węzeł **XmlEntityReference** , gdy napotka odwołanie do jednostki.  
  
 Przy użyciu następującego kodu XML  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 Dom kompiluje węzeł **XmlEntityReference** , gdy napotka `&publisher;` odwołanie. **XmlEntityReference** zawiera węzły podrzędne skopiowane z zawartości w deklaracji jednostki. Poprzedni przykład kodu zawiera tekst w deklaracji jednostki, więc węzeł XmlText jest tworzony jako węzeł podrzędny węzła odwołania do jednostki.  
  
 ![Struktura drzewa dla zachowanych odwołań do jednostek](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")  
Struktura drzewa dla odwołań do jednostek, które są zachowywane  
  
 Węzły podrzędne klasy XmlEntityReference są kopiami wszystkich węzłów podrzędnych utworzonych na podstawie węzła XmlEntity podczas napotkania deklaracji jednostki.  
  
> [!NOTE]
> Węzły skopiowane z elementu **XmlEntity** nie zawsze są wiernie kopiowane po umieszczeniu ich w węźle odwołania do jednostki. Mogą istnieć przestrzenie nazw, które znajdują się w zakresie w węźle odwołania do jednostki i mają wpływ na ostateczną konfigurację węzłów podrzędnych.  
  
 Domyślnie obiekty ogólne, takie jak `&abc;` są zachowywane, i węzły XmlEntityReference są zawsze tworzone.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
