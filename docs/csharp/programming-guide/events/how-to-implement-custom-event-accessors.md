---
title: 'Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 759a7a4518a371449723a23669816bbc0fbc0dee
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45528133"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)
Zdarzenie jest specjalnym rodzajem multiemisji delegat, który można wywołać tylko z w ramach klasy, która jest zadeklarowana w. Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, które powinny być używane, gdy zdarzenie jest uruchamiane. Te metody są dodawane do listy wywołań obiektu delegowanego przy użyciu metod dostępu zdarzeń, która jest podobna do metody dostępu właściwości, z tą różnicą, że metody dostępu zdarzeń są nazywane `add` i `remove`. W większości przypadków nie trzeba podać niestandardowych metod dostępu zdarzeń. Gdy nie niestandardowych metod dostępu zdarzeń są podane w kodzie, kompilator będzie dodać je automatycznie. Jednak w niektórych przypadkach może trzeba będzie podać niestandardowe zachowanie. Takiej sytuacji jest wyświetlana w temacie [porady: Implementowanie zdarzenia interfejsu](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak implementować niestandardowe zdarzenie dostępu add i remove. Chociaż może zastąpić dowolny kod wewnątrz metody dostępu, zaleca się blokowanie zdarzeń, aby dodać lub usunąć nowej metody obsługi zdarzeń.  
  
[!code-csharp[IDrawingObject.OnDraw](codesnippet/CSharp/how-to-implement-interface-events_1.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Zobacz też

- [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
- [event](../../../csharp/language-reference/keywords/event.md)