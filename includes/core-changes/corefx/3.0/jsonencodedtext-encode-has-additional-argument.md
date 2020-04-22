---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021678"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a>Metody JsonEncodedText.Encode mają dodatkowy argument JavaScriptEncoder

Począwszy od .NET Core 3.0 <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> Preview 8, metody zawierają opcjonalny <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.

#### <a name="change-description"></a>Zmień opis

Program .NET Core 3.0 zawiera nowy typ, odnośnik xref:System.Text.JsonEncodedText.Encode%2A?displayProperty=nameWithType>. Począwszy od .NET Core 3.0 Preview <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8, podpis wszystkich przeciążeń metody został zmieniony, aby uwzględnić parametr opcjonalny. <xref:System.Text.Encodings.Web.JavaScriptEncoder> Ta zmiana została wyzwolona w celu umożliwienia innego lub niestandardowego kodera.

Podpis metod `Encode` w .NET Core 3.0 Preview 7 jest:

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

#### <a name="version-introduced"></a>Wprowadzono wersję

.NET Core 3.0 Wersja zapoznawcza 8

#### <a name="recommended-action"></a>Zalecana akcja

Jest to tylko zmiana podziału binarnego; ponowna kompilacja względem platformy .NET Core 3.0 Preview 8 lub nowszej wersji rozwiąże wszelkie problemy ze środowiska uruchomieniowego.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki .NET

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
