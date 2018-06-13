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
ms.openlocfilehash: 6d0181a93831fa054d7ba1a740bafe1f228bfc15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331152"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)
Zdarzenie jest specjalnym rodzajem multiemisji delegata, który można wywołać tylko z należące do klasy, która jest zadeklarowana w. Kod klienta subskrybuje zdarzenia, podając odniesienie do metody, która powinna być wywoływana, gdy zdarzenie jest wywoływane. Te metody są dodawane do listy wywołania delegata za pomocą metod dostępu zdarzeń, która jest podobna do metod dostępu do właściwości, z wyjątkiem tego, że są nazywane metod dostępu zdarzeń `add` i `remove`. W większości przypadków nie trzeba podać niestandardowych metod dostępu zdarzeń. Gdy nie niestandardowych metod dostępu zdarzeń są dostarczane w kodzie, kompilator doda je automatycznie. W niektórych przypadkach może mieć zapewniające niestandardowych. Jeden taki przypadek przedstawiono w temacie [porady: Implementowanie interfejsu zdarzenia](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób implementować niestandardowe zdarzenie dostępu add i remove. Mimo że można zastąpić wszelkiego kodu wewnątrz metody dostępu, firma Microsoft zaleca, aby zablokować zdarzeń, aby dodać lub usunąć nowa metoda obsługi zdarzeń.  
  
```csharp
event EventHandler IDrawingObject.OnDraw  
{  
    add  
    {  
        lock (PreDrawEvent)  
        {  
            PreDrawEvent += value;  
        }  
    }  
    remove  
    {  
        lock (PreDrawEvent)  
        {  
            PreDrawEvent -= value;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia](../../../csharp/programming-guide/events/index.md)  
 [event](../../../csharp/language-reference/keywords/event.md)