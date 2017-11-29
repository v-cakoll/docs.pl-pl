---
title: "Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
caps.latest.revision: "7"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ff5fedeeaa427bb62991f9b406c167647dc376d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Porady: implementowanie niestandardowych metod dostępu zdarzeń (Przewodnik programowania w języku C#)
Zdarzenie jest specjalnym rodzajem multiemisji delegata, który można wywołać tylko z należące do klasy, która jest zadeklarowana w. Kod klienta subskrybuje zdarzenia, podając odniesienie do metody, która powinna być wywoływana, gdy zdarzenie jest wywoływane. Te metody są dodawane do listy wywołania delegata za pomocą metod dostępu zdarzeń, która jest podobna do metod dostępu do właściwości, z wyjątkiem tego, że są nazywane metod dostępu zdarzeń `add` i `remove`. W większości przypadków nie trzeba podać niestandardowych metod dostępu zdarzeń. Gdy nie niestandardowych metod dostępu zdarzeń są dostarczane w kodzie, kompilator doda je automatycznie. W niektórych przypadkach może mieć zapewniające niestandardowych. Jeden taki przypadek przedstawiono w temacie [porady: Implementowanie interfejsu zdarzenia](../../../csharp/programming-guide/events/how-to-implement-interface-events.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób implementować niestandardowe zdarzenie dostępu add i remove. Mimo że można zastąpić wszelkiego kodu wewnątrz metody dostępu, firma Microsoft zaleca, aby zablokować zdarzeń, aby dodać lub usunąć nowa metoda obsługi zdarzeń.  
  
```  
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
 [zdarzenia](../../../csharp/language-reference/keywords/event.md)
