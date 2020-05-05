---
ms.openlocfilehash: 87ada29e70a94c39e7ffb74767b99d49c52444af
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021642"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Operacje analizowania zmiennoprzecinkowe nie będą już kończyć się niepowodzeniem lub nie generują wyjątku overflow

Metody analizy zmiennoprzecinkowej <xref:System.OverflowException> nie generują już ani nie zwracają `false` podczas analizowania ciągu, którego wartość liczbowa jest spoza zakresu <xref:System.Single> lub <xref:System.Double> typu zmiennoprzecinkowego.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 2,2 i starszych wersjach metody <xref:System.Double.Parse%2A?displayProperty=nameWithType> i <xref:System.Single.Parse%2A?displayProperty=nameWithType> generują <xref:System.OverflowException> dla wartości, które wykraczają poza zakres odpowiedniego typu. Metody <xref:System.Double.TryParse%2A?displayProperty=nameWithType> i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> zwracają `false` dla reprezentacji ciągów wartości liczbowych poza zakresem.

Począwszy od platformy .NET Core 3,0, <xref:System.Double.Parse%2A?displayProperty=nameWithType>metody <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType>, i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> nie kończą się niepowodzeniem podczas analizowania ciągów liczbowych poza zakresem. Zamiast tego metody <xref:System.Double> analizy zwracają <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> wartości, które przekraczają <xref:System.Double.MaxValue?displayProperty=nameWithType>, i zwracają <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> dla wartości, które są mniejsze niż <xref:System.Double.MinValue?displayProperty=nameWithType>. <xref:System.Single> Podobnie metody analizy zwracają <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> wartości, które przekraczają <xref:System.Single.MaxValue?displayProperty=nameWithType>, i zwracają <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> dla wartości, które są mniejsze niż. <xref:System.Single.MinValue?displayProperty=nameWithType>

Ta zmiana została wprowadzona w celu uzyskania ulepszonej zgodności ze standardem IEEE 754:2008.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana może mieć wpływ na kod na jeden z dwóch sposobów:

- Kod zależy od programu obsługi do wykonania, <xref:System.OverflowException> gdy występuje przepełnienie. W takim przypadku `catch` należy usunąć instrukcję i umieścić dowolny kod w `If` instrukcji, która sprawdza, czy <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> lub <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> jest. `true`

- W kodzie założono, że wartości zmiennoprzecinkowe nie `Infinity`są. W takim przypadku należy dodać wymagany kod w celu sprawdzenia wartości zmiennoprzecinkowych `PositiveInfinity` i. `NegativeInfinity`

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

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
