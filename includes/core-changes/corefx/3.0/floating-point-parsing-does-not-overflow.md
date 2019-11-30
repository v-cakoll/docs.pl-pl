---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568097"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Operacje analizowania zmiennoprzecinkowe nie będą już kończyć się niepowodzeniem lub nie generują wyjątku overflow

Metody analizy zmiennoprzecinkowej nie generują już <xref:System.OverflowException> ani nie zwracają `false` podczas analizowania ciągu, którego wartość liczbowa znajduje się poza zakresem <xref:System.Single> lub <xref:System.Double> typu zmiennoprzecinkowego.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 2,2 i starszych wersjach metody <xref:System.Double.Parse%2A?displayProperty=nameWithType> i <xref:System.Single.Parse%2A?displayProperty=nameWithType> zgłaszają <xref:System.OverflowException> dla wartości, które są poza zakresem odpowiedniego typu. Metody <xref:System.Double.TryParse%2A?displayProperty=nameWithType> i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> zwracają `false` dla reprezentacji ciągów dla wartości liczbowych spoza zakresu.

Począwszy od platformy .NET Core 3,0, metody <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nie kończą się niepowodzeniem podczas analizowania ciągów liczbowych poza zakresem. Zamiast tego <xref:System.Double> metody analizy zwracają <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> dla wartości, które przekraczają <xref:System.Double.MaxValue?displayProperty=nameWithType>i zwracają <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> dla wartości, które są mniejsze niż <xref:System.Double.MinValue?displayProperty=nameWithType>. Podobnie metody analizy <xref:System.Single> zwracają <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> dla wartości, które przekraczają <xref:System.Single.MaxValue?displayProperty=nameWithType>i zwracają <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> dla wartości, które są mniejsze niż <xref:System.Single.MinValue?displayProperty=nameWithType>.

Ta zmiana została wprowadzona w celu uzyskania ulepszonej zgodności ze standardem IEEE 754:2008.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecane działanie

Ta zmiana może mieć wpływ na kod na jeden z dwóch sposobów:

- Kod zależy od programu obsługi <xref:System.OverflowException> do wykonania, gdy wystąpi przepełnienie. W takim przypadku należy usunąć instrukcję `catch` i umieścić dowolny kod w instrukcji `If`, która sprawdza, czy <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> lub <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> jest `true`.

- W kodzie założono, że wartości zmiennoprzecinkowe nie są `Infinity`. W takim przypadku należy dodać wymagany kod w celu sprawdzenia wartości zmiennoprzecinkowych `PositiveInfinity` i `NegativeInfinity`.

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
