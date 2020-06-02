---
title: Rozwinięte odwołania do jednostek, które nie zostały zachowane
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: ffd97806-ab43-4538-8de2-5828bfbbde57
ms.openlocfilehash: 1d26e9a35497bb0d5293e8a5b630bf4356325401
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292049"
---
# <a name="entity-references-are-expanded-and-not-preserved"></a>Rozwinięte odwołania do jednostek, które nie zostały zachowane
Gdy odwołanie do jednostki zostanie rozwinięte i zastąpione tekstem, który reprezentuje, węzeł **XmlEntityReference** nie zostanie utworzony. Zamiast tego, deklaracja jednostki jest analizowana, a węzły utworzone na podstawie zawartości deklaracji są kopiowane w miejscu **XmlEntityReference**. W związku z tym, w tym `&publisher;` przykładzie, `&publisher;` nie jest zapisany, ale zamiast tego jest tworzony węzeł **XmlText** .  
  
 ![rozwinięta struktura drzewa](media/xmlentityref-expanded-nodes.gif "xmlentityref_expanded_nodes")  
Struktura drzewa dla rozszerzonych odwołań do jednostek  
  
 Jednostki znaku, takie jak `B` lub, `<` nie są zachowywane. Zamiast tego są zawsze rozwinięte i reprezentowane jako węzły tekstowe.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
