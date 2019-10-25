---
ms.openlocfilehash: 6bb8c87af66e744514fb43e628c6423487342ac2
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887818"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Wywołania metody System. Windows. Input. PenContext. Disable w systemach z obsługą dotykową mogą zgłosić ArgumentException

|   |   |
|---|---|
|Szczegóły|W pewnych okolicznościach wywołania wewnętrznej metody **System. Windows. Intput. PenContext. Disable** w systemach z obsługą dotykową mogą zgłosić nieobsłużony <code>T:System.ArgumentException</code> z powodu współużytkowania wątkowości.|
|Sugestia|Ten problem został rozwiązany w .NET Framework 4,7. Aby zapobiec wyjątku, należy przeprowadzić uaktualnienie do wersji .NET Framework począwszy od .NET Framework 4,7.|
|Zakres|Krawędź|
|Wersja|4.6.1|
|Typ|Przekierowanie|
