---
ms.openlocfilehash: 0778285ef1b5702bd79743038a1bd21ba04612d6
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67804322"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Wywołania System.Windows.Input.PenContext.Disable w systemach z obsługą dotykową może zgłaszać ArgumentException

|   |   |
|---|---|
|Szczegóły|W niektórych okolicznościach wywołania wewnętrznego <strong>System.Windows.Intput.PenContext.Disable</strong> metody w systemach z obsługą dotykową może zgłaszać nieobsługiwany <code>T:System.ArgumentException</code> ze względu na współużytkowania wątkowości.|
|Sugestia|Ten problem został rozwiązany w programie .NET Framework 4.7. Aby zapobiec wyjątek, uaktualnienie do wersji programu .NET Framework, począwszy od programu .NET Framework 4.7.|
|Scope|Krawędź|
|Wersja|4.6.1|
|Typ|Przekierowanie|

