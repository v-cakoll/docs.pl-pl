---
ms.openlocfilehash: f5ae4669c85ae4f5d57d88ab55f6e1c758a625a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147591"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>JsonEncodedText.Encode metody mają dodatkowy argument JavaScriptEncoder

Począwszy od .NET Core 3.0 Preview 8, <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> metody zawierają opcjonalny <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.

#### <a name="change-description"></a>Zmień opis

.NET Core 3.0 zawiera nowy typ, odnośnik:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>. Począwszy od .NET Core 3.0 Preview <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8, podpis wszystkich przeciążeń metody został zmieniony w celu uwzględnienia parametru opcjonalnego. <xref:System.Text.Encodings.Web.JavaScriptEncoder> Ta zmiana została wmazana, aby umożliwić inny lub niestandardowy koder.

Podpis metod `Encode` w wersji .NET Core 3.0 Preview 7 jest następujące:

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

Podpis tych samych `Encode` metod w wersji .NET Core 3.0 Preview 8 i nowszych jest:

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

Podgląd .NET Core 3.0 8

#### <a name="recommended-action"></a>Zalecana akcja

Jest to tylko zmiana podziału binarnego; ponowna kompilacja względem wersji .NET Core 3.0 Preview 8 lub nowszej rozwiąże wszelkie problemy z wykonywaniem.

#### <a name="category"></a>Kategoria

CoreFx

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
