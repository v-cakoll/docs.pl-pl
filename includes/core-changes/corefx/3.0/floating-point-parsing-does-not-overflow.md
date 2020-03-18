---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568097"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Operacje analizy zmiennoprzecinkowych nie są już inwakczliwe ani nie mogą być powodem do przepełnieniaWyjątek

Metody analizy zmiennoprzecinkowej nie <xref:System.OverflowException> są `false` już rzuty lub zwracane podczas analizowania ciągu, którego wartość liczbowa znajduje się poza zakresem <xref:System.Single> typu zmiennoprzecinkowego. <xref:System.Double>

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i <xref:System.Double.Parse%2A?displayProperty=nameWithType> wcześniejszych wersjach i <xref:System.Single.Parse%2A?displayProperty=nameWithType> metody wyrzucając <xref:System.OverflowException> dla wartości, które wykraczają poza zakres ich odpowiedniego typu. I <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody zwracają `false` dla reprezentacji ciągów wartości liczbowych poza zakresem.

Począwszy od .NET Core <xref:System.Double.Parse%2A?displayProperty=nameWithType>3.0, , <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, , <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody nie zawiodą już podczas analizowania ciągów liczbowych poza zakresem. Zamiast tego <xref:System.Double> metody analizy zwracają <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> wartości, <xref:System.Double.MaxValue?displayProperty=nameWithType>które przekraczają <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> , i zwracają <xref:System.Double.MinValue?displayProperty=nameWithType>dla wartości, które są mniejsze niż . Podobnie metody <xref:System.Single> analizy zwracają <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> wartości, które przekraczają <xref:System.Single.MaxValue?displayProperty=nameWithType>, i <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> zwracają dla wartości, które są mniejsze niż <xref:System.Single.MinValue?displayProperty=nameWithType>.

Zmiana ta została wmazana w celu poprawy zgodności ieee 754:2008.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana może mieć wpływ na kod na dwa sposoby:

- Kod zależy od programu <xref:System.OverflowException> obsługi do wykonania po wystąpieniu przepełnienia. W takim przypadku należy `catch` usunąć instrukcję i umieścić `If` niezbędny <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> kod <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true`w instrukcji, która sprawdza, czy jest .

- Kod zakłada, że wartości zmiennoprzecinkowe nie `Infinity`są . W takim przypadku należy dodać kod niezbędny do sprawdzenia `PositiveInfinity` `NegativeInfinity`wartości zmiennoprzecinkowych i .

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
