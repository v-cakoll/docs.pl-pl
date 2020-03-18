---
title: Jak zaimplementować niestandardowe akcesory zdarzeń - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 34e816799f472e8945962e334b9a90b2582e0393
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705356"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Jak zaimplementować niestandardowe akcesory zdarzeń (Przewodnik programowania C#)
Zdarzenie jest specjalny rodzaj delegata multiemisji, które mogą być wywoływane tylko z wewnątrz klasy, która jest zadeklarowana w. Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, która powinna być wywoływana podczas odpalania zdarzenia. Metody te są dodawane do listy wywołania delegata za pośrednictwem akcesorów zdarzeń, które `add` przypominają `remove`akcesory właściwości, z tą różnicą, że akcesory zdarzeń są nazwane i . W większości przypadków nie trzeba podać niestandardowych akcesorów zdarzeń. Jeśli w kodzie nie są dostarczane żadne niestandardowe akcesory zdarzeń, kompilator doda je automatycznie. Jednak w niektórych przypadkach może być trzeba podać zachowanie niestandardowe. Jeden taki przypadek jest pokazany w temacie [Jak zaimplementować zdarzenia interfejsu](./how-to-implement-interface-events.md).
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak zaimplementować niestandardowe dodawanie i usuwanie akcesorów zdarzeń. Mimo że można zastąpić dowolny kod wewnątrz akcesorów, zaleca się zablokowanie zdarzenia przed dodaniem lub usunięciem nowej metody obsługi zdarzeń.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](./index.md)
- [Zdarzenie](../../language-reference/keywords/event.md)
