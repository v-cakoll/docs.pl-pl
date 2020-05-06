---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021678"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="d02fa-101">Metody JsonEncodedText. Encode mają dodatkowy argument JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="d02fa-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="d02fa-102">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8 <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> , <xref:System.Text.Encodings.Web.JavaScriptEncoder> metody zawierają opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="d02fa-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d02fa-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="d02fa-103">Change description</span></span>

<span data-ttu-id="d02fa-104">Program .NET Core 3,0 zawiera nowy typ linki XREF: System. Text. JSON. JsonEncodedText. Encode% 2A? displayProperty = nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d02fa-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d02fa-105">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8 <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> , sygnatura wszystkich przeciążeń metody <xref:System.Text.Encodings.Web.JavaScriptEncoder> została zmieniona w celu uwzględnienia opcjonalnego parametru.</span><span class="sxs-lookup"><span data-stu-id="d02fa-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="d02fa-106">Ta zmiana została wprowadzona w celu zezwalania na inny lub niestandardowy koder.</span><span class="sxs-lookup"><span data-stu-id="d02fa-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="d02fa-107">Sygnatura `Encode` metod w programie .net Core 3,0 Preview 7 to:</span><span class="sxs-lookup"><span data-stu-id="d02fa-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

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

<span data-ttu-id="d02fa-108">Podpis tych samych `Encode` metod w programie .net Core 3,0 w wersji zapoznawczej 8 i nowszych to:</span><span class="sxs-lookup"><span data-stu-id="d02fa-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

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

#### <a name="version-introduced"></a><span data-ttu-id="d02fa-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d02fa-109">Version introduced</span></span>

<span data-ttu-id="d02fa-110">.NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="d02fa-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d02fa-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d02fa-111">Recommended action</span></span>

<span data-ttu-id="d02fa-112">Jest to tylko zmiana w postaci binarnej. ponowna kompilacja względem programu .NET Core 3,0 w wersji zapoznawczej 8 lub nowszej spowoduje rozwiązanie wszelkich problemów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d02fa-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="d02fa-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d02fa-113">Category</span></span>

<span data-ttu-id="d02fa-114">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="d02fa-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d02fa-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d02fa-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
