---
title: Rozwinięte odwołania do jednostek, które nie zostały zachowane
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
ms.openlocfilehash: ae3db77d7659b7e1d36a9bccf7143f52c536dbbf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710937"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Rozwinięte odwołania do jednostek, które nie zostały zachowane
Gdy odwołanie do jednostki zostanie rozwinięte i zastąpione tekstem, który reprezentuje, węzeł **XmlEntityReference** nie zostanie utworzony. Zamiast tego, deklaracja jednostki jest analizowana, a węzły utworzone na podstawie zawartości deklaracji są kopiowane w miejscu **XmlEntityReference**. W związku z tym `&publisher;` , w tym `&publisher;` przykładzie, nie jest zapisany, ale zamiast tego jest tworzony węzeł **XmlText** .  
  
 ![rozwinięta struktura drzewa](../../../../docs/standard/data/xml/media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Struktura drzewa dla rozszerzonych odwołań do jednostek  
  
 Jednostki znaku, takie `B` jak `<` lub, nie są zachowywane. Zamiast tego są zawsze rozwinięte i reprezentowane jako węzły tekstowe.  
  
 Aby zachować węzły **XmlEntityReference** i węzły podrzędne odwołania do jednostki, należy ustawić flagę **EntityHandling** na **ExpandCharEntities**. W przeciwnym razie pozostaw flagę **EntityHandling** domyślną, która ma **ExpandEntities**. W takim przypadku w modelu DOM nie będą wyświetlane węzły odwołań do obiektów. Węzły są zastępowane węzłami, które są kopiami węzłów podrzędnych deklaracji Entity.  
  
 Jeden efekt uboczny niezachowywania odwołań do jednostek polega na tym, że gdy dokument jest zapisywany i przekazano do innej aplikacji, aplikacja otrzymująca nie wie, że węzły zostały wygenerowane przez odwołanie do jednostki. Jeśli jednak odwołania do jednostek są zachowywane, aplikacja do odbioru widzi odwołanie do jednostki i odczytuje węzły podrzędne. Istnieje oczywiste, że węzły podrzędne reprezentują informacje, które były w deklaracji jednostki. Na przykład, model DOM teoretycznie ma następującą strukturę, jeśli odwołania do jednostek są zachowywane.  
  
 XmlElement: Wydawca  
  
 XmlEntityReference:`&publisher;`  
  
 XmlText: Microsoft Press  
  
 Jeśli odwołania do jednostek są rozwinięte w modelu DOM, który jest metodą domyślną, struktura ma ten typ drzewa:  
  
 XmlElement: Wydawca  
  
 XmlText: Microsoft Press  
  
 Zwróć uwagę, że węzeł odwołania do jednostki został usunięty, a aplikacja do odbioru nie może stwierdzić, czy węzeł **XmlText** zawierający "Microsoft Press" został utworzony z deklaracji jednostki.  
  
 Jeśli używasz czytnika, który nie może rozpoznać jednostek, Metoda **ładowania** zgłasza wyjątek podczas napotkania odwołania do jednostki.  
  
## <a name="see-also"></a>Zobacz też

- [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
