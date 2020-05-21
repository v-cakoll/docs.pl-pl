---
ms.openlocfilehash: 13da0ef6155d65fbc894c5747cc36bb3483ba518
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721564"
---
### <a name="change-in-semantics-of-stringnull-in-utf8jsonwriter"></a><span data-ttu-id="6bafc-101">Zmień semantykę `(string)null` w Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="6bafc-101">Change in semantics of `(string)null` in Utf8JsonWriter</span></span>

<span data-ttu-id="6bafc-102">W programie .NET Core 3,0 w wersji zapoznawczej 7 ciąg o wartości null jest traktowany jako pusty ciąg w <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="6bafc-102">In .NET Core 3.0 Preview 7, the null string is treated as the empty string in <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="6bafc-103">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, ciąg o wartości null zgłasza wyjątek, gdy jest używany jako nazwa właściwości i emituje token JSON o wartości null, gdy jest używany jako wartość.</span><span class="sxs-lookup"><span data-stu-id="6bafc-103">Starting with .NET Core 3.0 Preview 8, the null string throws an exception when used as a property name, and it emits the JSON null token when used as a value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6bafc-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="6bafc-104">Change description</span></span>

<span data-ttu-id="6bafc-105">W programie .NET Core 3,0 w wersji zapoznawczej 7 `null` ciąg był traktowany jako `""` oba podczas pisania nazw właściwości i podczas pisania wartości.</span><span class="sxs-lookup"><span data-stu-id="6bafc-105">In .NET Core 3.0 Preview 7, the `null` string was treated as `""` both when writing property names and when writing values.</span></span>  

<span data-ttu-id="6bafc-106">Począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 8, `null` Nazwa właściwości zgłasza `ArgumentNullException` , a `null` wartość jest traktowana jako wywołanie <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> lub <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6bafc-106">Starting with .NET Core 3.0 Preview 8, a `null` property name throws an `ArgumentNullException`, and a `null` value is treated as a call to <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="6bafc-107">Spójrzmy na poniższy kod:</span><span class="sxs-lookup"><span data-stu-id="6bafc-107">Consider the following code:</span></span>

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

<span data-ttu-id="6bafc-108">Jeśli program jest uruchamiany z programem .NET Core 3,0 w wersji zapoznawczej 7, składnik zapisywania generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6bafc-108">If run with .NET Core 3.0 Preview 7, the writer produces the following output:</span></span>

```js
[{"":"","prop2":""},""]
```

<span data-ttu-id="6bafc-109">Począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 8, wywołanie do wyrzucania `writer.WriteString(propertyName1, propertyValue1)` <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="6bafc-109">Starting with .NET Core 3.0 Preview 8, the call to `writer.WriteString(propertyName1, propertyValue1)` throws an <xref:System.ArgumentNullException>.</span></span>  <span data-ttu-id="6bafc-110">Jeśli `propertyName1 = null` jest zastępowany przez `propertyName1 = string.Empty` , dane wyjściowe byłyby teraz:</span><span class="sxs-lookup"><span data-stu-id="6bafc-110">If `propertyName1 = null` is replaced with `propertyName1 = string.Empty`, the output would now be:</span></span>

```js
[{"":null,"prop2":null},null]
```

<span data-ttu-id="6bafc-111">Ta zmiana została wprowadzona w celu lepszego dopasowania przy użyciu oczekiwań obiektu wywołującego dla `null` wartości.</span><span class="sxs-lookup"><span data-stu-id="6bafc-111">This change was made to better align with caller expectations for `null` values.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6bafc-112">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="6bafc-112">Version introduced</span></span>

<span data-ttu-id="6bafc-113">3,0 wersja zapoznawcza 8</span><span class="sxs-lookup"><span data-stu-id="6bafc-113">3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6bafc-114">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="6bafc-114">Recommended action</span></span>

<span data-ttu-id="6bafc-115">Podczas zapisywania nazw właściwości i wartości z <xref:System.Text.Json.Utf8JsonWriter> klasą:</span><span class="sxs-lookup"><span data-stu-id="6bafc-115">When writing property names and values with the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

- <span data-ttu-id="6bafc-116">Upewnij `null` się, że nie są używane jako nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="6bafc-116">Ensure non-`null` strings are used as property names.</span></span>

- <span data-ttu-id="6bafc-117">Jeśli poprzednie zachowanie jest wymagane, użyj wywołania łączenia o wartości null; na przykład `writer.WriteString(propertyName1 ?? "", propertyValue1)` .</span><span class="sxs-lookup"><span data-stu-id="6bafc-117">If the previous behavior is desired, use a null coalescing invocation; for example, `writer.WriteString(propertyName1 ?? "", propertyValue1)`.</span></span>

- <span data-ttu-id="6bafc-118">Jeśli zapisanie `null` literału dla `null` wartości ciągu nie jest pożądane, użyj wywołania łączenia o wartości null, na przykład `writer.WriteString(propertyName2, propertyValue2 ?? "")` .</span><span class="sxs-lookup"><span data-stu-id="6bafc-118">If writing a `null` literal for a `null` string value is not desirable, use a null coalescing invocation; for example, `writer.WriteString(propertyName2, propertyValue2 ?? "")`.</span></span>

#### <a name="category"></a><span data-ttu-id="6bafc-119">Kategoria</span><span class="sxs-lookup"><span data-stu-id="6bafc-119">Category</span></span>

<span data-ttu-id="6bafc-120">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="6bafc-120">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6bafc-121">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6bafc-121">Affected APIs</span></span>

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

#### Affected APIs

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
