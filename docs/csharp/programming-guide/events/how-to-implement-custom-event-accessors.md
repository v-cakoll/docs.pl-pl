---
title: Jak zaimplementować niestandardowe metody dostępu do zdarzeń — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705356"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Jak zaimplementować niestandardowe metody dostępu do zdarzeń (C# Przewodnik programowania)
Zdarzenie jest specjalnym rodzajem delegata multiemisji, który może być wywoływany z klasy, w której jest zadeklarowany. Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, która powinna być wywoływana, gdy zdarzenie zostanie wyzwolone. Te metody są dodawane do listy wywołań delegata za pomocą metod dostępu do zdarzeń, które przypominają metody dostępu do właściwości, z tą różnicą, że dostęp do zdarzeń nazywa się `add` i `remove`. W większości przypadków nie trzeba podawać niestandardowych metod dostępu do zdarzeń. Gdy w kodzie nie są dostarczane żadne niestandardowe metody dostępu do zdarzeń, kompilator doda je automatycznie. Jednak w niektórych przypadkach może być konieczne zapewnienie zachowania niestandardowego. W tym temacie pokazano, [jak zaimplementować zdarzenia interfejsu](./how-to-implement-interface-events.md).
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób implementacji niestandardowych metod dostępu do zdarzeń dodawania i usuwania. Chociaż można zastąpić dowolny kod wewnątrz metod dostępu, Zalecamy zablokowanie zdarzenia przed dodaniem lub usunięciem nowej metody obsługi zdarzeń.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](./index.md)
- [event](../../language-reference/keywords/event.md)
