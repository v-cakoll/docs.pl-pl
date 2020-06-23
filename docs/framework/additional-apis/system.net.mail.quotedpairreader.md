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
# <a name="quotedpairreader-class"></a><span data-ttu-id="dec61-102">QuotedPairReader, klasa</span><span class="sxs-lookup"><span data-stu-id="dec61-102">QuotedPairReader class</span></span>

<span data-ttu-id="dec61-103">Określa, które znaki są cytowane (ucieczki) w ciągu ujętym w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="dec61-103">Determines which characters are quoted (escaped) in a quoted string.</span></span> <span data-ttu-id="dec61-104">Klasa ta nie może być dziedziczona.</span><span class="sxs-lookup"><span data-stu-id="dec61-104">This class cannot be inherited.</span></span>

```csharp
internal static class QuotedPairReader
```

> [!WARNING]
> <span data-ttu-id="dec61-105">Ta klasa jest wewnętrzna i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="dec61-105">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="dec61-106">Firma Microsoft nie obsługuje korzystania z tej klasy w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="dec61-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="countquotedchars-method"></a><span data-ttu-id="dec61-107">CountQuotedChars, Metoda</span><span class="sxs-lookup"><span data-stu-id="dec61-107">CountQuotedChars method</span></span>

<span data-ttu-id="dec61-108">Zlicza kolejne cudzysłowy, w tym wiele poprzedzających ukośników odwrotnych, w określonym ciągu.</span><span class="sxs-lookup"><span data-stu-id="dec61-108">Counts the number of consecutive quoted characters, including multiple preceding quoted backslashes, in the specified string.</span></span> <span data-ttu-id="dec61-109">Na przykład, podano ciąg `a\\\b` i indeks `4` , metoda zwraca `4` , ponieważ `b` jest cytowane i tak jak trzy poprzednie ukośniki odwrotne.</span><span class="sxs-lookup"><span data-stu-id="dec61-109">For example, given the string `a\\\b` and an index of `4`, the method returns `4`, because `b` is quoted and so are the three preceding backslashes.</span></span>

```csharp
internal static int CountQuotedChars(string data, int index, bool permitUnicodeEscaping)
```

### <a name="parameters"></a><span data-ttu-id="dec61-110">Parametry</span><span class="sxs-lookup"><span data-stu-id="dec61-110">Parameters</span></span>

- <span data-ttu-id="dec61-111">`data` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="dec61-111">`data` <xref:System.String></span></span>

  <span data-ttu-id="dec61-112">Ciąg danych, w którym mają być zliczane kolejne cudzysłowy.</span><span class="sxs-lookup"><span data-stu-id="dec61-112">The data string in which to count consecutive quoted characters.</span></span>

- <span data-ttu-id="dec61-113">`index` <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="dec61-113">`index` <xref:System.Int32></span></span>

  <span data-ttu-id="dec61-114">Pozycja w określonym ciągu do i włącznie z tym, które kolejne cudzysłowy powinny być zliczane.</span><span class="sxs-lookup"><span data-stu-id="dec61-114">The position in the specified string up to and including which consecutive quoted characters should be counted.</span></span>

- <span data-ttu-id="dec61-115">`permitUnicodeEscaping` <xref:System.Boolean></span><span class="sxs-lookup"><span data-stu-id="dec61-115">`permitUnicodeEscaping` <xref:System.Boolean></span></span>

  <span data-ttu-id="dec61-116">`true`Aby zezwolić na sekwencję znaków Unicode; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="dec61-116">`true` to permit Unicode characters to be escaped; otherwise, `false`.</span></span>

### <a name="return-value"></a><span data-ttu-id="dec61-117">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dec61-117">Return value</span></span>

<xref:System.Int32?displayProperty=nameWithType>

<span data-ttu-id="dec61-118">`0`Jeśli znak w określonym indeksie nie zostanie zmieniony; w przeciwnym razie Liczba kolejnych znaków cudzysłowu do i włącznie z znakiem w `index` .</span><span class="sxs-lookup"><span data-stu-id="dec61-118">`0` if the character at the specified index is not escaped; otherwise, the number of consecutive quoted characters up to and including the character at `index`.</span></span>

### <a name="exceptions"></a><span data-ttu-id="dec61-119">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="dec61-119">Exceptions</span></span>

<xref:System.FormatException?displayProperty=nameWithType>

<span data-ttu-id="dec61-120">Znaleziono znak Unicode o zmienionym znaczeniu, ale jest on niedozwolony.</span><span class="sxs-lookup"><span data-stu-id="dec61-120">An escaped Unicode character was found but is not permitted.</span></span>

## <a name="requirements"></a><span data-ttu-id="dec61-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dec61-121">Requirements</span></span>

<span data-ttu-id="dec61-122">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="dec61-122">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="dec61-123">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="dec61-123">**Assembly:** System (in System.dll)</span></span>
