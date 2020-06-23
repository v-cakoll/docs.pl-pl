---
title: HttpStatusDescription, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.HttpStatusDescription
- System.Net.HttpStatusDescription.Get
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 0214d8259c735de11abe204680d619a7298466de
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990391"
---
# <a name="httpstatusdescription-class"></a>HttpStatusDescription, klasa

Zawiera standardowe opisy stanu HTTP. Klasa ta nie może być dziedziczona.

```csharp
internal static class HttpStatusDescription
```

> [!WARNING]
> Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="get-method"></a>Metoda Get

Zwraca opis skojarzony z określonym kodem stanu HTTP.

```csharp
internal static string Get(int code)
```

### <a name="parameters"></a>Parametry

`code` <xref:System.Int32>

Kod stanu HTTP, na przykład `404` .

### <a name="return-value"></a>Wartość zwracana

<xref:System.String?displayProperty=nameWithType>

Opis stanu HTTP.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)
