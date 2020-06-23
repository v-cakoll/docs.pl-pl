---
title: WebHeaderCollection. addinternal — Metoda (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.WebHeaderCollection.AddInternal
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: fd7b13ccd1baad48ab99a85d80ccd6154651c608
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990355"
---
# <a name="webheadercollectionaddinternal-method"></a>WebHeaderCollection. Add— Metoda wewnętrzna

Dodaje nowy nagłówek z określoną nazwą i wartością do kolekcji, pomijając sprawdzanie.

```csharp
internal void AddInternal(string name, string value)
```

> [!WARNING]
> Ta metoda jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="parameters"></a>Parametry

- `name` <xref:System.String>

  Nazwa nagłówka.

- `value` <xref:System.String>

  Wartość nagłówka.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)
