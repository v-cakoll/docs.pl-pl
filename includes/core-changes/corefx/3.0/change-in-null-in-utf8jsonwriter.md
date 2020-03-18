---
ms.openlocfilehash: 7c39fe7ffd59fa7a5564bb45f32a6a2fbe0ddb33
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568174"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="cb3c8-101">Zmiana semantyki `(string)null` w Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="cb3c8-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="cb3c8-102">W wersji .NET Core 3.0 Preview 7 ciąg zerowy jest traktowany jako pusty ciąg w pliku <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="cb3c8-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="cb3c8-103">Począwszy od .NET Core 3.0 Preview 8, ciąg zerowy zgłasza wyjątek, gdy jest używany jako nazwa właściwości i emituje token null JSON, gdy jest używany jako wartość.</span><span class="sxs-lookup"><span data-stu-id="cb3c8-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cb3c8-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="cb3c8-104">Change description</span></span>

<span data-ttu-id="cb3c8-105">W .NET Core 3.0 `null` Preview 7 `""` ciąg był traktowany zarówno podczas zapisywania nazw właściwości, jak i podczas zapisywania wartości.</span><span class="sxs-lookup"><span data-stu-id="cb3c8-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="cb3c8-106">Począwszy od .NET Core 3.0 Preview 8, `null` nazwa właściwości `ArgumentNullException`zgłasza , a `null` wartość jest traktowana jako wywołanie <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> lub <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cb3c8-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="cb3c8-107">Spójrzmy na poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="cb3c8-107">Consider the following code:</span></span>

```csharp
string propertyName1 = null;
string propertyValue1 = null;
string propertyName2 = "prop2";
string propertyValue2 = null;
string simpleValue1 = null;

using (Utf8JsonWriter writer = new Utf8JsonWriter(stream))
{
    writer.WriteStartArray();

    writer.WriteStartObject();
    writer.WriteString(propertyName1, propertyValue1);
    writer.WriteString(propertyName2, propertyValue2);
    writer.WriteEndObject();

    writer.WriteStringValue(simpleValue1);

    writer.WriteEndArray();
}
```

<span data-ttu-id="cb3c8-108">Jeśli zostanie uruchomiony z .NET Core 3.0 Preview 7, moduł zapisujący generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="cb3c8-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="cb3c8-109">Począwszy od .NET Core 3.0 `writer.WriteString(propertyName1, propertyValue1)` Preview 8, wywołanie do wyrzucając . <xref:System.ArgumentNullException></span><span class="sxs-lookup"><span data-stu-id="cb3c8-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="cb3c8-110">Jeśli `propertyName1 = null` zostanie `propertyName1 = string.Empty`zastąpiony , wyjście będzie teraz:</span><span class="sxs-lookup"><span data-stu-id="cb3c8-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="cb3c8-111">Ta zmiana została wmazana w `null` celu lepszego dostosowania się do oczekiwań dzwoniącego dla wartości.</span><span class="sxs-lookup"><span data-stu-id="cb3c8-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cb3c8-112">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="cb3c8-112">Version introduced</span></span>

<span data-ttu-id="cb3c8-113">3.0 Podgląd 8</span><span class="sxs-lookup"><span data-stu-id="cb3c8-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cb3c8-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="cb3c8-114">Recommended action</span></span>

<span data-ttu-id="cb3c8-115">Podczas zapisywania nazw właściwości <xref:System.Text.Json.Utf8JsonWriter> i wartości z klasą:</span><span class="sxs-lookup"><span data-stu-id="cb3c8-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="cb3c8-116">Upewnij się, że ciągi inne są`null` używane jako nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb3c8-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="cb3c8-117">Jeśli poprzednie zachowanie jest pożądane, należy użyć wywołania zerowego łączenia; na przykład `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span><span class="sxs-lookup"><span data-stu-id="cb3c8-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="cb3c8-118">Jeśli pisanie `null` literału dla wartości `null` ciągu nie jest pożądane, należy użyć wywołania null łączenia; na przykład `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span><span class="sxs-lookup"><span data-stu-id="cb3c8-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="cb3c8-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="cb3c8-119">Category</span></span>

<span data-ttu-id="cb3c8-120">CoreFx</span><span class="sxs-lookup"><span data-stu-id="cb3c8-120">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cb3c8-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cb3c8-121">Affected APIs</span></span>

- <xref:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Byte%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan%7BSystem.Char%7D)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)?displayProperty=nameWithType>
- <xref:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.Utf8JsonWriter.WriteBase64String(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteBoolean(System.String,System.Boolean)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNull(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Int64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt32)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.UInt64)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Single)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Double)`
- `M:System.Text.Json.Utf8JsonWriter.WriteNumber(System.String,System.Decimal)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartArray(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStartObject(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Byte})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.ReadOnlySpan{System.Char})`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Text.Json.JsonEncodedText)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTime)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.DateTimeOffset)`
- `M:System.Text.Json.Utf8JsonWriter.WriteString(System.String,System.Guid)`
- `M:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)`
- `M:System.Text.Json.Utf8JsonWriter.WritePropertyName(System.String)`

-->
