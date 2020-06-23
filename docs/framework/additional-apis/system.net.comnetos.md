---
title: ComNetOS, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.ComNetOS
- System.Net.ComNetOS.IsWin7orLater
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ed2b970d07df2c338870b386e75c1688703f1d68
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990402"
---
# <a name="comnetos-class"></a>ComNetOS, klasa

Zawiera informacje o bieżącym systemie operacyjnym, takie jak jego wersja i typ instalacji (klient lub serwer). Klasa ta nie może być dziedziczona.
  
```csharp  
internal static class ComNetOS
```

> [!WARNING]
> Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="iswin7orlater-field"></a>Pole IsWin7orLater

Określa, czy wersja systemu operacyjnego to Windows 7, czy nowsza.

```csharp
internal static readonly bool IsWin7orLater
```

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)
