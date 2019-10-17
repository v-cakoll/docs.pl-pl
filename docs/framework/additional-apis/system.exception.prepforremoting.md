---
title: Exception. PrepForRemoting — Metoda (system)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405033"
---
# <a name="exceptionprepforremoting-method"></a>Exception. PrepForRemoting, Metoda

Zachowuje ślad stosu po stronie serwera, dołączając go do wiadomości przed ponownym wyrzucaniem wyjątku w lokacji wywołania klienta.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Zwraca

<xref:System.Exception>  
To <xref:System.Exception> wystąpienie.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `Exception.PrepForRemoting` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System>

**Zestaw:** mscorlib. dll (w bibliotece Mscorlib. dll)

**.NET Framework wersje:** Dostępne od 1,0.
