---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887818"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Wywołania do System.Windows.Input.PenContext.Wyłącz na dotykowych systemów może rzucać ArgumentException

|   |   |
|---|---|
|Szczegóły|W pewnych okolicznościach wywołania wewnętrznej **system.Windows.Intput.PenContext.Disable** metody w systemach dotykowych może rzucać nieobsługiwał <code>T:System.ArgumentException</code> z powodu ponownego internalrancy.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4.7. Aby zapobiec wyjątek, uaktualnić do wersji programu .NET Framework, począwszy od .NET Framework 4.7.|
|Zakres|Brzeg|
|Wersja|4.6.1|
|Typ|Przekierowanie|
