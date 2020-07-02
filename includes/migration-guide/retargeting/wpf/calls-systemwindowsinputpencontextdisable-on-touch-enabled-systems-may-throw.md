---
ms.openlocfilehash: a44458484ea09c566defeabc9b604bd55d994e93
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617545"
---
### <a name="calls-to-systemwindowsinputpencontextdisable-on-touch-enabled-systems-may-throw-an-argumentexception"></a>Wywołania metody System. Windows. Input. PenContext. Disable w systemach z obsługą dotykową mogą zgłosić ArgumentException

#### <a name="details"></a>Szczegóły

W pewnych okolicznościach wywołania wewnętrznej metody **System. Windows. Intput. PenContext. Disable** w systemach z obsługą dotykową mogą zgłosić nieobsłużony `T:System.ArgumentException` skutek z powodu współużytkowania wątkowości.

#### <a name="suggestion"></a>Sugestia

Ten problem został rozwiązany w .NET Framework 4,7. Aby zapobiec wyjątku, należy przeprowadzić uaktualnienie do wersji .NET Framework począwszy od .NET Framework 4,7.

| Nazwa    | Wartość       |
|:--------|:------------|
| Zakres   | Brzeg        |
| Wersja | 4.6.1       |
| Typ    | Przekierowanie |
