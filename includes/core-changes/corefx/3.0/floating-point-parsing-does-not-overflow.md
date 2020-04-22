---
ms.openlocfilehash: 87ada29e70a94c39e7ffb74767b99d49c52444af
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021642"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Operacje analizowania zmiennoprzecinkowego nie są już nieudane lub nie mogą paść za przepełnienie

Metody analizy zmiennoprzecinowej nie <xref:System.OverflowException> są `false` już rzutować ani zwracać podczas analizowania ciągu, <xref:System.Single> <xref:System.Double> którego wartość liczbowa znajduje się poza zakresem typu zmiennoprzecinkowego lub zmiennoprzecinkowego.

#### <a name="change-description"></a>Zmień opis

W .NET Core 2.2 i <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> wcześniejszych wersjach i metody i rzucać <xref:System.OverflowException> dla wartości, które poza zakresem ich odpowiedniego typu. I <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody `false` zwracają dla reprezentacji ciągów wartości liczbowych poza zakresem.

Począwszy od .NET Core <xref:System.Double.Parse%2A?displayProperty=nameWithType>3.0, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, , <xref:System.Single.Parse%2A?displayProperty=nameWithType>i <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody nie są już zawodzą podczas analizowania ciągów liczbowych poza zakresem. Zamiast tego <xref:System.Double> metody analizy zwracają <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> wartości, <xref:System.Double.MaxValue?displayProperty=nameWithType>które przekraczają <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> , i zwracają <xref:System.Double.MinValue?displayProperty=nameWithType>dla wartości, które są mniejsze niż . Podobnie metody <xref:System.Single> analizy <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> zwracają wartości, które <xref:System.Single.MaxValue?displayProperty=nameWithType>przekraczają i <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> zwracają wartości, które <xref:System.Single.MinValue?displayProperty=nameWithType>są mniejsze niż .

Ta zmiana została wywłyszona w celu poprawy zgodności z IEEE 754:2008.

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana może mieć wpływ na kod na jeden z dwóch sposobów:

- Kod zależy od programu <xref:System.OverflowException> obsługi do wykonania, gdy wystąpi przepełnienie. W takim przypadku należy `catch` usunąć instrukcję i umieścić `If` niezbędny <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> kod <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> `true`w instrukcji, która sprawdza, czy jest .

- Kod zakłada, że wartości zmiennoprzecinkowe nie `Infinity`są . W takim przypadku należy dodać kod niezbędny do sprawdzenia `PositiveInfinity` `NegativeInfinity`wartości zmiennoprzecinkowych i .

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

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
