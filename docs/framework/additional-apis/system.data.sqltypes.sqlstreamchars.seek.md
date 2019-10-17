---
title: SqlStreamChars. seek (Int64, SeekOrigin) — Metoda (System. Data. sqltypees)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395598"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars. seek (Int64, SeekOrigin) — Metoda

Gdy jest zastępowany w klasie pochodnej, ustawia pozycję w bieżącym strumieniu. Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll. Jest on przeznaczony do użycia przez SQL Server. W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>Parametry

`offset`\
Przesunięcie bajtów względem `origin`.

`origin`\
Jedna z wartości wyliczenia, która wskazuje punkt odniesienia, z którego ma zostać uzyskana Nowa pozycja.

## <a name="returns"></a>Zwraca

<xref:System.Int32>\
Nowa pozycja w bieżącym strumieniu.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `SqlStreamChars.Seek` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Data.SqlTypes>

**Zestaw:** System. Data (w pliku System. Data. dll)

**.NET Framework wersje:** Dostępne od 2,0.
