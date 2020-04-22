---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021678"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="4ad8b-101">Metody JsonEncodedText.Encode mają dodatkowy argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="4ad8b-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="4ad8b-102">Począwszy od .NET Core 3.0 <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> Preview 8, metody zawierają opcjonalny <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span><span class="sxs-lookup"><span data-stu-id="4ad8b-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4ad8b-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="4ad8b-103">Change description</span></span>

<span data-ttu-id="4ad8b-104">Program .NET Core 3.0 zawiera nowy typ, odnośnik xref:System.Text.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4ad8b-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ad8b-105">Począwszy od .NET Core 3.0 Preview <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> 8, podpis wszystkich przeciążeń metody został zmieniony, aby uwzględnić parametr opcjonalny. <xref:System.Text.Encodings.Web.JavaScriptEncoder></span><span class="sxs-lookup"><span data-stu-id="4ad8b-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="4ad8b-106">Ta zmiana została wyzwolona w celu umożliwienia innego lub niestandardowego kodera.</span><span class="sxs-lookup"><span data-stu-id="4ad8b-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="4ad8b-107">Podpis metod `Encode` w .NET Core 3.0 Preview 7 jest:</span><span class="sxs-lookup"><span data-stu-id="4ad8b-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="4ad8b-108">Podpis tych samych `Encode` metod w wersji .NET Core 3.0 Preview 8 i nowszych jest:</span><span class="sxs-lookup"><span data-stu-id="4ad8b-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="4ad8b-109">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="4ad8b-109">Version introduced</span></span>

<span data-ttu-id="4ad8b-110">.NET Core 3.0 Wersja zapoznawcza 8</span><span class="sxs-lookup"><span data-stu-id="4ad8b-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4ad8b-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="4ad8b-111">Recommended action</span></span>

<span data-ttu-id="4ad8b-112">Jest to tylko zmiana podziału binarnego; ponowna kompilacja względem platformy .NET Core 3.0 Preview 8 lub nowszej wersji rozwiąże wszelkie problemy ze środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4ad8b-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="4ad8b-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4ad8b-113">Category</span></span>

<span data-ttu-id="4ad8b-114">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="4ad8b-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4ad8b-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4ad8b-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
