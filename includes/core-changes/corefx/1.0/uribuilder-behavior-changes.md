---
ms.openlocfilehash: b3cc04d5675ea63a0a6b967e293da8a1bd79830d
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595688"
---
### <a name="uribuilder-properties-no-longer-prepend-leading-characters"></a>Właściwości UriBuilder nie dołączają już znaków wiodących

<xref:System.UriBuilder.Fragment?displayProperty=nameWithType>nie dołącza już znaku wiodącego `#` i nie <xref:System.UriBuilder.Query?displayProperty=nameWithType> dołącza już znaku wiodącego `?` , gdy jeden już istnieje.

#### <a name="change-description"></a>Zmień opis

<xref:System.UriBuilder.Fragment?displayProperty=nameWithType> W .NET Framework właściwości <xref:System.UriBuilder.Query?displayProperty=nameWithType> i zawsze są poprzedzone znakiem `?` `#` lub, odpowiednio, do przechowywanej wartości. Takie zachowanie może skutkować `#` wielokrotnym `?` znakiem w wartości przechowywanej, jeśli ciąg zawiera już jeden z tych znaków wiodących. Na przykład wartość <xref:System.UriBuilder.Fragment?displayProperty=nameWithType> może być równa `##main`.

Począwszy od platformy .NET Core 1,0, te właściwości nie `#` dołączają `?` lub do przechowywanej wartości, jeśli jeden już występuje na początku ciągu.

#### <a name="version-introduced"></a>Wprowadzona wersja

1.0

#### <a name="recommended-action"></a>Zalecana akcja

Nie trzeba już jawnie usuwać żadnego z tych znaków wiodących podczas ustawiania wartości właściwości. Jest to szczególnie przydatne podczas dołączania wartości, ponieważ nie jest już konieczne usuwanie interlinii `#` lub `?` każdorazowe dołączanie.

Na przykład poniższy fragment kodu przedstawia różnicę zachowania między .NET Framework i .NET Core.

```csharp
var builder = new UriBuilder();
builder.Query = "one=1";
builder.Query += "&two=2";
builder.Query += "&three=3";
builder.Query += "&four=4";

Console.WriteLine(builder.Query);
```

- W .NET Framework dane wyjściowe to `????one=1&two=2&three=3&four=4`.
- W programie .NET Core dane wyjściowe to `?one=1&two=2&three=3&four=4`.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.UriBuilder.Fragment?displayProperty=fullName>
- <xref:System.UriBuilder.Query?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.UriBuilder.Fragment`
- `T:System.UriBuilder.Query`

-->
