---
title: SqlStreamChars. Write (Char [], Int32, Int32) Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395578"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>SqlStreamChars. Write (Char [], Int32, Int32) — Metoda

Gdy jest zastępowany w klasie pochodnej, zapisuje sekwencję znaków w bieżącym strumieniu i przesuwa bieżącą pozycję w tym strumieniu o liczbę pisanych znaków. Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll. Jest on przeznaczony do użycia przez SQL Server. W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parametry

`buffer`  
Tablica znaków do zapisania.

`offset`  
Przesunięcie względem pochodzenia.

`count`  
Liczba znaków, które mają być zapisywane w bieżącym strumieniu.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `SqlStreamChars.Write` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody zapisu w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Data.SqlTypes>

**Zestaw:** System. Data (w pliku System. Data. dll)

**.NET Framework wersje:** Dostępne od 2,0.
