---
title: Odwołania do jednostek są rozwinięte i nie są zachowywane
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a55aa71ff3976241b96dd12baef06a9a13ef9dd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873737"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Odwołania do jednostek są rozwinięte i nie są zachowywane
Gdy odwołanie do jednostki jest rozwinięte i zastąpione tekstem reprezentuje on **XmlEntityReference** węzeł nie został utworzony. Zamiast tego jest analizowany deklaracji jednostek i węzłów przygotowane na podstawie zawartości w deklaracji zostaną skopiowane zamiast z **XmlEntityReference**. Dlatego w `&publisher;` przykład `&publisher;` nie zostanie zapisana, ale zamiast tego **XmlText** jest tworzony węzeł.  
  
 ![rozwinięte struktury drzewa](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Strukturę drzewa dla odwołań do jednostek, które są rozwijane  
  
 Znak jednostki, takie jak `B` lub `<` nie są zachowywane. Zamiast tego są zawsze rozwinięte i reprezentowane jako węzły tekstowe.  
  
 Aby zachować **XmlEntityReference** węzłów i węzłów podrzędnych odwołania jednostki podłączone do niego, ustaw **EntityHandling** flaga **ExpandCharEntities**. W przeciwnym razie pozostaw **EntityHandling** flagi na wartość domyślna, czyli **ExpandEntities**. W tym przypadku nie będą widzieć węzłów odwołanie do jednostki w modelu DOM. Węzły są zastępowane przez węzły, które są kopiami węzłów podrzędnych deklaracji entity.  
  
 Jeden efekt uboczny nie zachowania odwołań do jednostek jest, czy po zapisaniu dokumentu i przekazywane do innej aplikacji, aplikacja nie wie, że węzły zostały wygenerowane przez odwołanie do jednostki. Jednak podczas odwołań do jednostek są zachowywane, aplikacja odbierająca widzi odwołania do jednostki, a odczytuje węzły podrzędne. Okaże się, że węzły podrzędne reprezentują informacje, które były w deklaracji entity. Na przykład modelu DOM synchroniczna ma następującą strukturę, jeśli odwołań do jednostek są zachowywane.  
  
 XmlElement: wydawcy  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Microsoft Press  
  
 Odwołania do jednostek zostaną rozwinięte w modelu DOM, który jest domyślną metodą, struktura zawiera ten typ drzewa:  
  
 XmlElement: wydawcy  
  
 XmlText: Microsoft Press  
  
 Zwróć uwagę, że węzeł odwołania jednostki został usunięty i aplikacja odbierająca nie wiadomo, że **XmlText** węzła zawierającego "Microsoft Press" został utworzony z deklaracji entity.  
  
 Jeśli korzystasz z czytnika zawartości, która nie może rozpoznać jednostki **obciążenia** metoda zgłasza wyjątek, po napotkaniu odwołania do jednostki.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
