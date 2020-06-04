---
title: Obiekt lub klasa nie obsługuje zbioru zdarzeń
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: bc75e031c2d05bea3aa64774a9d3817756e51e8b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409364"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a>Obiekt lub klasa nie obsługuje zbioru zdarzeń
Podjęto próbę użycia `WithEvents` zmiennej ze składnikiem, który nie może współpracować ze źródłem zdarzenia dla określonego zestawu zdarzeń. Na przykład chcesz wypróbować zdarzenia obiektu, a następnie utworzyć inny obiekt, który `Implements` jest pierwszym obiektem. Mimo że można zastanowić się, że można wymyślić zdarzenia z zaimplementowanego obiektu, nie zawsze jest to przypadek. `Implements`implementuje interfejs tylko dla metod i właściwości. `WithEvents`nie jest obsługiwany w przypadku prywatnych `UserControls` , ponieważ informacje o typie, które są konieczne do podniesienia, `ObjectEvent` nie są dostępne w czasie wykonywania.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1. Nie można ujścia zdarzeń dla składnika, który nie jest źródłem zdarzeń.  
  
## <a name="see-also"></a>Zobacz też

- [WithEvents](../modifiers/withevents.md)
- [Implements — Instrukcja](../statements/implements-statement.md)
