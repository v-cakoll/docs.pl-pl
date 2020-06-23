---
title: QuotedPairReader, Klasa (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.QuotedPairReader
- System.Net.QuotedPairReader.CountQuotedChars
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 9b0bf835a34eecc651894f4336648b73a81b665c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990373"
---
# <a name="quotedpairreader-class"></a>QuotedPairReader, klasa

Określa, które znaki są cytowane (ucieczki) w ciągu ujętym w cudzysłów. Klasa ta nie może być dziedziczona.

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.
>
> Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.

## <a name="countquotedchars-method"></a>CountQuotedChars, Metoda

Zlicza kolejne cudzysłowy, w tym wiele poprzedzających ukośników odwrotnych, w określonym ciągu. Na przykład, podano ciąg `a\\\b` i indeks `4` , metoda zwraca `4` , ponieważ `b` jest cytowane i tak jak trzy poprzednie ukośniki odwrotne.

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a>Parametry

- `data` <xref:System.String>

  Ciąg danych, w którym mają być zliczane kolejne cudzysłowy.

- `index` <xref:System.Int32>

  Pozycja w określonym ciągu do i włącznie z tym, które kolejne cudzysłowy powinny być zliczane.

- `permitUnicodeEscaping` <xref:System.Boolean>

  `true`Aby zezwolić na sekwencję znaków Unicode; w przeciwnym razie `false` .

### <a name="return-value"></a>Wartość zwracana

<xref:System.Int32?displayProperty=nameWithType>

`0`Jeśli znak w określonym indeksie nie zostanie zmieniony; w przeciwnym razie Liczba kolejnych znaków cudzysłowu do i włącznie z znakiem w `index` .

### <a name="exceptions"></a>Wyjątki

<xref:System.FormatException?displayProperty=nameWithType>

Znaleziono znak Unicode o zmienionym znaczeniu, ale jest on niedozwolony.

## <a name="requirements"></a>Wymagania

**Przestrzeń nazw:**<xref:System.Net>

**Zestaw:** System (w System.dll)
