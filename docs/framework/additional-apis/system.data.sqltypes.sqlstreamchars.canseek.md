---
title: SqlStreamChars. CanSeek — Właściwość (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.CanSeek
- System.Data.SqlTypes.SqlStreamChars.get_CanSeek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: eb32978f62b7d46f0abf715e2bca347592c0fda8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395779"
---
# <a name="sqlstreamcharscanseek-property"></a>SqlStreamChars. CanSeek — Właściwość

Gdy jest zastępowany w klasie pochodnej, pobiera wartość wskazującą, czy bieżąca para obsługuje operację wyszukiwania. Zestaw, który zawiera tę właściwość, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll. Jest on przeznaczony do użycia przez SQL Server. W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.

```csharp
public abstract bool CanSeek { get; }
```

## <a name="property-value"></a>Wartość właściwości

<xref:System.Boolean>\
`true`, jeśli bieżąca para obsługuje operację wyszukiwania; w przeciwnym razie `false`.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Właściwość `SqlStreamChars.CanSeek` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Data.SqlTypes>

**Zestaw:** System. Data (w pliku System. Data. dll)

**.NET Framework wersje:** Dostępne od 2,0.
