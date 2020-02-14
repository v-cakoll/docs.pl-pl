---
title: Exception. PrepForRemoting — Metoda (system)
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: ce1c24578690a1643b7f5af0e44eaae95ed7b0a2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214898"
---
# <a name="exceptionprepforremoting-method"></a>Metoda Exception.PrepForRemoting

Zachowuje ślad stosu po stronie serwera, dołączając go do wiadomości przed ponownym wyrzucaniem wyjątku w lokacji wywołania klienta.

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>Zwraca

<xref:System.Exception>  
To wystąpienie <xref:System.Exception>.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `Exception.PrepForRemoting` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System>

**Zestaw:** mscorlib. dll (w bibliotece Mscorlib. dll)

**.NET Framework wersje:** Dostępne od 1,0.
