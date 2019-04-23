---
ms.openlocfilehash: 3cd5052dffcb059c240a310e0b89384f28409264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59982154"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Wywołania System.Windows.Input.PenContext.Disable w systemach z obsługą dotykową może zgłaszać ArgumentException

|   |   |
|---|---|
|Szczegóły|W niektórych okolicznościach wywołania wewnętrznego <strong>System.Windows.Intput.PenContext.Disable</strong> metody w systemach z obsługą dotykową może zgłaszać nieobsługiwany <code>T:System.ArgumentException</code> ze względu na współużytkowania wątkowości.|
|Sugestia|Ten problem został rozwiązany w programie .NET Framework 4.7. Aby zapobiec wyjątek, uaktualnienie do wersji programu .NET Framework, począwszy od programu .NET Framework 4.7.|
|Zakres|Krawędź|
|Wersja|4.6.1|
|Typ|Przekierowanie|
