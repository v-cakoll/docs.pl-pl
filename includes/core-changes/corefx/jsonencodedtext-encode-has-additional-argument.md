---
ms.openlocfilehash: 375a6f57a867c2a11fe95753c1085d6d708db2bd
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237432"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Metody JsonEncodedText. Encode mają dodatkowy argument JavaScriptEncoder

Począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 8, metody <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> zawierają opcjonalny argument <xref:System.Text.Encodings.Web.JavaScriptEncoder>.

#### <a name="change-description"></a>Zmień opis

Program .NET Core 3,0 zawiera nowy typ linki XREF: System. Text. JSON. JsonEncodedText. Encode% 2A? displayProperty = nameWithType >. Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, sygnatura wszystkich przeciążeń metody <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> zmieniła się na dołączenie opcjonalnego parametru <xref:System.Text.Encodings.Web.JavaScriptEncoder>. Ta zmiana została wprowadzona w celu zezwalania na inny lub niestandardowy koder.

Sygnatura metod `Encode` w programie .NET Core 3,0 Preview 7 to:

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value);
        public static JsonEncodedText Encode(string value);
    }
}
```

Podpis tych samych metod `Encode` w programie .NET Core 3,0 w wersji zapoznawczej 8 i jego nowszych wersjach:

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(string value, JavaScriptEncoder encoder = null);
    }
}
```

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET Core 3,0 (wersja zapoznawcza 8)

#### <a name="recommended-action"></a>Zalecana akcja

Jest to tylko zmiana w postaci binarnej. ponowna kompilacja względem programu .NET Core 3,0 w wersji zapoznawczej 8 lub nowszej spowoduje rozwiązanie wszelkich problemów w czasie wykonywania.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Narażone interfejsy API

<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
<xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
