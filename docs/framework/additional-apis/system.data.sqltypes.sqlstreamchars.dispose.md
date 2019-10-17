---
title: SqlStreamChars. Dispose (Boolean) — Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395763"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>SqlStreamChars. Dispose (Boolean) — Metoda

Gdy jest zastępowany w klasie pochodnej, zwalnia zasoby używane przez strumień. Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll. Jest on przeznaczony do użycia przez SQL Server. W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>Parametry

`disposing`\
`true` w celu zwolnienia zasobów zarządzanych i niezarządzanych; `false` do zwolnienia tylko zasobów niezarządzanych.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `SqlStreamChars.Dispose` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Data.SqlTypes>

**Zestaw:** System. Data (w pliku System. Data. dll)

**.NET Framework wersje:** Dostępne od 2,0.
