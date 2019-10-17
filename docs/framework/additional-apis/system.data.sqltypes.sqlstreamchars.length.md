---
title: SqlStreamChars. Length — właściwość (System. Data. SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/19/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Length
- System.Data.SqlTypes.SqlStreamChars.get_Length
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 2171b10d1c0eb7bcad894cc44c5103bdab18b0a5
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395607"
---
# <a name="sqlstreamcharslength-property"></a>SqlStreamChars. Length — właściwość

Gdy jest zastępowany w klasie pochodnej, pobiera długość bieżącego strumienia. Zestaw, który zawiera tę właściwość, ma relację zaprzyjaźnioną z obiektem sqlaccess. dll. Jest on przeznaczony do użycia przez SQL Server. W przypadku innych baz danych Użyj mechanizmu hostingu dostarczonego przez tę bazę danych.

## <a name="syntax"></a>Składnia

```csharp
public abstract long Length { get; }
```

## <a name="property-value"></a>Wartość właściwości

<xref:System.Int64>\
Długość strumienia.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Właściwość `SqlStreamChars.Length` jest prywatna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje użycia tej właściwości w aplikacji produkcyjnej w żadnym przypadku.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.Data.SqlTypes>

**Zestaw:** System. Data (w pliku System. Data. dll)

**.NET Framework wersje:** Dostępne od 2,0.
