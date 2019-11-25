---
title: Elementu MemoryStream. InternalGetOriginAndLength — Metoda (System.IO)
author: mairaw
ms.author: mairaw
ms.date: 11/19/2019
topic_type:
- apiref
api_name:
- System.IO.MemoryStream.InternalGetOriginAndLength
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: d2bfa087fe2fb247f963cfa687c27056363d5696
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74284032"
---
# <a name="memorystreaminternalgetoriginandlength-method"></a>Elementu MemoryStream. InternalGetOriginAndLength — Metoda

Pobiera wewnętrzne wartości źródłowe i długość strumienia pamięci.

```csharp
internal void InternalGetOriginAndLength(out int origin, out int length)
```

## <a name="parameters"></a>Parametry

- `origin` <xref:System.Int32>\
  Gdy ta metoda zwraca, przesunięcie tablicy bajtowej określonej podczas tworzenia nowego obiektu <xref:System.IO.MemoryStream>. Zawiera wartość 0, jeśli tablica bajtów została utworzona przez <xref:System.IO.MemoryStream>.

- `length` <xref:System.Int32>\
  Gdy ta metoda zwraca, liczba bajtów w strumieniu pamięci.

## <a name="remarks"></a>Uwagi

> [!WARNING]
> Metoda `MemoryStream.InternalGetOriginAndLength` jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej metody w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:** <xref:System.IO>

**Zestaw:** mscorlib. dll (w bibliotece Mscorlib. dll)

**.NET Framework wersje:** Dostępne od 2,0.
