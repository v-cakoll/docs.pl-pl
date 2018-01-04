---
title: "Odwołania do jednostek są rozwinięte i nie są zachowywane"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 00b997865c614756ea5fd9567ded3baa469f4c62
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Odwołania do jednostek są rozwinięte i nie są zachowywane
Gdy odwołanie do jednostki jest rozszerzony i zastępuje reprezentuje on **XmlEntityReference** węzeł nie został utworzony. Zamiast tego jest analizowana z deklaracji jednostki i węzły utworzone na podstawie zawartości w deklaracji zostaną skopiowane zamiast z **XmlEntityReference**. W związku z tym w `&publisher;` przykład `&publisher;` nie zostanie zapisana, ale zamiast tego **XmlText** jest tworzony węzeł.  
  
 ![rozszerzona struktury drzewa](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Struktura drzewa dla odwołań do jednostek, które zostaną rozwinięte  
  
 Znak jednostek, takich jak `B` lub `<` nie są zachowywane. Zamiast tego są zawsze rozwinięty i reprezentowane jako węzły tekstowe.  
  
 Aby zachować **XmlEntityReference** węzły i węzłów podrzędnych odwołanie do jednostki dołączone do niego, ustaw **EntityHandling** flaga **ExpandCharEntities**. W przeciwnym razie pozostaw **EntityHandling** flagi na wartość domyślna, czyli **ExpandEntities**. W takim przypadku nie będzie mógł przeglądać węzłów odwołanie do jednostki w modelu DOM. Węzły zostały zastąpione przez węzły, które są kopiami węzłów podrzędnych deklaracji entity.  
  
 Jeden po stronie nie zachowuje odwołań do jednostek powoduje, że po zapisaniu dokumentu i przekazywane do innej aplikacji, aplikacja odbierająca nie wie, że węzły zostały wygenerowane przez odwołanie do jednostki. Jednak podczas odwołań do jednostek zostaną zachowane, aplikacja odbierająca widzi odwołania do jednostki i odczytuje podrzędnych węzłów. Okaże się, że węzły podrzędne reprezentują informacje, które były w deklaracji entity. Na przykład modelu DOM teoretycznie ma następującą strukturę, jeśli zostaną zachowane odwołań do jednostek.  
  
 Element XmlElement: wydawcy  
  
 XmlEntityReference:`&publisher;`  
  
 XmlText: Naciśnij przycisk Microsoft  
  
 Odwołania do jednostek są rozwijane w modelu DOM, który jest domyślną metodą, struktura zawiera tego typu drzewa:  
  
 Element XmlElement: wydawcy  
  
 XmlText: Naciśnij przycisk Microsoft  
  
 Powiadomienie ma węzeł odwołanie do jednostki, czy aplikacja odbierająca nie wiadomo, że **XmlText** węzła zawierającego "Microsoft Press" został utworzony na podstawie deklaracji entity.  
  
 Jeśli używasz czytnik nie może rozpoznać jednostki **obciążenia** metoda zgłosi wyjątek po napotkaniu odwołania do jednostki.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
