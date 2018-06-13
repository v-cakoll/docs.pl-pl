---
title: Odwołania do jednostek są rozwinięte i nie są zachowywane
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa03532200a89aa164648c1278c9dbafc2aee214
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569535"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Odwołania do jednostek są rozwinięte i nie są zachowywane
Gdy odwołanie do jednostki jest rozszerzony i zastępuje reprezentuje on **XmlEntityReference** węzeł nie został utworzony. Zamiast tego jest analizowana z deklaracji jednostki i węzły utworzone na podstawie zawartości w deklaracji zostaną skopiowane zamiast z **XmlEntityReference**. W związku z tym w `&publisher;` przykład `&publisher;` nie zostanie zapisana, ale zamiast tego **XmlText** jest tworzony węzeł.  
  
 ![rozszerzona struktury drzewa](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Struktura drzewa dla odwołań do jednostek, które zostaną rozwinięte  
  
 Znak jednostek, takich jak `B` lub `<` nie są zachowywane. Zamiast tego są zawsze rozwinięty i reprezentowane jako węzły tekstowe.  
  
 Aby zachować **XmlEntityReference** węzły i węzłów podrzędnych odwołanie do jednostki dołączone do niego, ustaw **EntityHandling** flaga **ExpandCharEntities**. W przeciwnym razie pozostaw **EntityHandling** flagi na wartość domyślna, czyli **ExpandEntities**. W takim przypadku nie będzie mógł przeglądać węzłów odwołanie do jednostki w modelu DOM. Węzły zostały zastąpione przez węzły, które są kopiami węzłów podrzędnych deklaracji entity.  
  
 Jeden po stronie nie zachowuje odwołań do jednostek powoduje, że po zapisaniu dokumentu i przekazywane do innej aplikacji, aplikacja odbierająca nie wie, że węzły zostały wygenerowane przez odwołanie do jednostki. Jednak podczas odwołań do jednostek zostaną zachowane, aplikacja odbierająca widzi odwołania do jednostki i odczytuje podrzędnych węzłów. Okaże się, że węzły podrzędne reprezentują informacje, które były w deklaracji entity. Na przykład modelu DOM teoretycznie ma następującą strukturę, jeśli zostaną zachowane odwołań do jednostek.  
  
 Element XmlElement: wydawcy  
  
 XmlEntityReference: `&publisher;`  
  
 XmlText: Naciśnij przycisk Microsoft  
  
 Odwołania do jednostek są rozwijane w modelu DOM, który jest domyślną metodą, struktura zawiera tego typu drzewa:  
  
 Element XmlElement: wydawcy  
  
 XmlText: Naciśnij przycisk Microsoft  
  
 Powiadomienie ma węzeł odwołanie do jednostki, czy aplikacja odbierająca nie wiadomo, że **XmlText** węzła zawierającego "Microsoft Press" został utworzony na podstawie deklaracji entity.  
  
 Jeśli używasz czytnik nie może rozpoznać jednostki **obciążenia** metoda zgłosi wyjątek po napotkaniu odwołania do jednostki.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
