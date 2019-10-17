---
title: SqlStreamChars. Read (Char [], Int32, Int32) Metoda (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395753"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>SqlStreamChars. Read (Char [], Int32, Int32) — Metoda

Gdy jest zastępowany w klasie pochodnej, odczytuje następny zestaw znaków ze strumienia wejściowego. Zestaw, który zawiera tę metodę, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll. Jest on przeznaczony do użycia przez SQL Server. W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>Parametry

`buffer`\
Tablica znaków do odczytania.

`offset`\
Przesunięcie względem pochodzenia.

`count`\
Liczba znaków, które mają być odczytane z bieżącego strumienia.

## <a name="returns"></a>Zwraca

<xref:System.Int32>\
Całkowita liczba znaków odczytywanych w buforze.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `SqlStreamChars.Read` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Data.SqlTypes>

**Zestaw:** System. Data (w pliku System. Data. dll)

**.NET Framework wersje:** Dostępne od 2,0.
