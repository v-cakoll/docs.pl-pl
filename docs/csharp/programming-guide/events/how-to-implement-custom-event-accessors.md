---
title: 'Instrukcje: Implementowanie niestandardowych metod dostępu do C# zdarzeń — Przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 4eaf8b4c3038d07d5b0fc021e21c7f1a2de85d74
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590523"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a>Instrukcje: Implementowanie niestandardowych metod dostępu doC# zdarzeń (Przewodnik programowania)
Zdarzenie jest specjalnym rodzajem delegata multiemisji, który może być wywoływany z klasy, w której jest zadeklarowany. Kod klienta subskrybuje zdarzenie, podając odwołanie do metody, która powinna być wywoływana, gdy zdarzenie zostanie wyzwolone. Te metody są dodawane do listy wywołań delegata za pomocą metod dostępu do zdarzeń, które przypominają metody dostępu do właściwości, z tą różnicą, że `add` dostęp `remove`do zdarzeń jest nazwany i. W większości przypadków nie trzeba podawać niestandardowych metod dostępu do zdarzeń. Gdy w kodzie nie są dostarczane żadne niestandardowe metody dostępu do zdarzeń, kompilator doda je automatycznie. Jednak w niektórych przypadkach może być konieczne zapewnienie zachowania niestandardowego. Jeden z takich przypadków przedstawiono w temacie [jak:  Implementuj zdarzenia](./how-to-implement-interface-events.md)interfejsu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób implementacji niestandardowych metod dostępu do zdarzeń dodawania i usuwania. Chociaż można zastąpić dowolny kod wewnątrz metod dostępu, Zalecamy zablokowanie zdarzenia przed dodaniem lub usunięciem nowej metody obsługi zdarzeń.  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia](./index.md)
- [event](../../language-reference/keywords/event.md)
