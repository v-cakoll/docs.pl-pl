---
title: Exception. PrepForRemoting — Metoda (system)
description: Przejrzyj metodę Exception. PrepForRemoting w programie .NET. Metoda dodaje ślad stosu po stronie serwera do komunikatu przed ponownym zgłoszeniem wyjątku na kliencie.
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 9ceb73499ae3bb308975e6db5b961bfe40165ba3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105262"
---
# <a name="exceptionprepforremoting-method"></a>Metoda Exception.PrepForRemoting

Zachowuje ślad stosu po stronie serwera, dołączając go do wiadomości przed ponownym wyrzucaniem wyjątku w lokacji wywołania klienta.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Zwraca

<xref:System.Exception>  
To <xref:System.Exception> wystąpienie.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> `Exception.PrepForRemoting`Metoda jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System>

**Zestaw:** mscorlib.dll (w mscorlib.dll)

**.NET Framework wersje:** Dostępne od 1,0.
