---
title: Jak serializować i deserializować kod JSON przy użyciu języka C# — .NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6324fe28b23e4df74bcf3fd1dbb7e0c14d5e3d1b
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135805"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="9aec2-102">Jak serializować i deserializować (Marshaling and unmarshaling) JSON w programie .NET</span><span class="sxs-lookup"><span data-stu-id="9aec2-102">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="9aec2-103">W tym artykule pokazano, <xref:System.Text.Json> jak używać przestrzeni nazw do serializacji i deserializacji do i z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="9aec2-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="9aec2-104">W przypadku przenoszenia istniejącego kodu z programu `Newtonsoft.Json`zapoznaj się z tematem [Jak przeprowadzić migrację do programu `System.Text.Json` ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="9aec2-104">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="9aec2-105">Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="9aec2-105">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="9aec2-106">Większość przykładowych kodów serializacji <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> do `true` "DB-Print" w formacie JSON (z wcięciem i białym znakiem).</span><span class="sxs-lookup"><span data-stu-id="9aec2-106">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="9aec2-107">Do użycia w środowisku produkcyjnym zwykle przyjmuje się wartość domyślną `false` dla tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="9aec2-107">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="9aec2-108">Przykłady kodu odnoszą się do następującej klasy i wariantów:</span><span class="sxs-lookup"><span data-stu-id="9aec2-108">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="9aec2-109">Namespaces</span><span class="sxs-lookup"><span data-stu-id="9aec2-109">Namespaces</span></span>

<span data-ttu-id="9aec2-110"><xref:System.Text.Json> Przestrzeń nazw zawiera wszystkie punkty wejścia i typy główne.</span><span class="sxs-lookup"><span data-stu-id="9aec2-110">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="9aec2-111"><xref:System.Text.Json.Serialization> Przestrzeń nazw zawiera atrybuty i interfejsy API dla zaawansowanych scenariuszy i dostosowań specyficznych dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-111">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="9aec2-112">Przykłady kodu przedstawione w tym artykule wymagają `using` dyrektyw dla jednej lub obu tych przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="9aec2-112">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="9aec2-113">Atrybuty z <xref:System.Runtime.Serialization> przestrzeni nazw nie są obecnie obsługiwane `System.Text.Json`w programie.</span><span class="sxs-lookup"><span data-stu-id="9aec2-113">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="9aec2-114">Pisanie obiektów .NET w formacie JSON (Serializacja)</span><span class="sxs-lookup"><span data-stu-id="9aec2-114">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="9aec2-115">Aby zapisać dane <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> JSON do ciągu lub do pliku, wywołaj metodę.</span><span class="sxs-lookup"><span data-stu-id="9aec2-115">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9aec2-116">Poniższy przykład tworzy kod JSON jako ciąg:</span><span class="sxs-lookup"><span data-stu-id="9aec2-116">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-117">Poniższy przykład używa kodu synchronicznego do utworzenia pliku JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-117">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-118">W poniższym przykładzie jest tworzony plik JSON przy użyciu kodu asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="9aec2-118">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-119">Powyższe przykłady używają wnioskowania typu dla serializowanego typu.</span><span class="sxs-lookup"><span data-stu-id="9aec2-119">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="9aec2-120">Przeciążenie `Serialize()` przyjmuje parametr typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="9aec2-120">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="9aec2-121">Przykład serializacji</span><span class="sxs-lookup"><span data-stu-id="9aec2-121">Serialization example</span></span>

<span data-ttu-id="9aec2-122">Oto przykładowa Klasa, która zawiera kolekcje i zagnieżdżoną klasę:</span><span class="sxs-lookup"><span data-stu-id="9aec2-122">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="9aec2-123">Dane wyjściowe JSON serializowania wystąpienia poprzedniego typu wyglądają podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9aec2-123">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="9aec2-124">Dane wyjściowe JSON domyślnie są zminimalizowanego:</span><span class="sxs-lookup"><span data-stu-id="9aec2-124">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="9aec2-125">W poniższym przykładzie przedstawiono ten sam kod JSON, sformatowany (to jest całkiem wydruk z odstępami i wcięciami):</span><span class="sxs-lookup"><span data-stu-id="9aec2-125">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a><span data-ttu-id="9aec2-126">Serializacja do UTF-8</span><span class="sxs-lookup"><span data-stu-id="9aec2-126">Serialize to UTF-8</span></span>

<span data-ttu-id="9aec2-127">Aby serializować do UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> metodę:</span><span class="sxs-lookup"><span data-stu-id="9aec2-127">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-128">Dostępne <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.Utf8JsonWriter> jest również Przeciążenie, które trwa.</span><span class="sxs-lookup"><span data-stu-id="9aec2-128">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="9aec2-129">Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach.</span><span class="sxs-lookup"><span data-stu-id="9aec2-129">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="9aec2-130">Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="9aec2-130">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="9aec2-131">Zachowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="9aec2-131">Serialization behavior</span></span>

* <span data-ttu-id="9aec2-132">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="9aec2-132">By default, all public properties are serialized.</span></span> <span data-ttu-id="9aec2-133">Można [określić właściwości do wykluczenia](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="9aec2-133">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="9aec2-134">[Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem języka HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="9aec2-134">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="9aec2-135">Domyślnie JSON jest zminimalizowanego.</span><span class="sxs-lookup"><span data-stu-id="9aec2-135">By default, JSON is minified.</span></span> <span data-ttu-id="9aec2-136">Można tu [wydrukować kod JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="9aec2-136">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="9aec2-137">Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET.</span><span class="sxs-lookup"><span data-stu-id="9aec2-137">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="9aec2-138">Można [dostosować wielkość liter w nazwach JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="9aec2-138">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="9aec2-139">Wykryto odwołania cykliczne i zostały zgłoszone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="9aec2-139">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="9aec2-140">Obecnie pola są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="9aec2-140">Currently, fields are excluded.</span></span>

<span data-ttu-id="9aec2-141">Obsługiwane typy to:</span><span class="sxs-lookup"><span data-stu-id="9aec2-141">Supported types include:</span></span>

* <span data-ttu-id="9aec2-142">Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="9aec2-142">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="9aec2-143">Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="9aec2-143">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="9aec2-144">Tablice jednowymiarowe i nieregularne (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="9aec2-144">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="9aec2-145">`Dictionary<string,TValue>`gdzie `TValue` is `object`to `JsonElement`, lub poco.</span><span class="sxs-lookup"><span data-stu-id="9aec2-145">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="9aec2-146">Kolekcje z następujących przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9aec2-146">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="9aec2-147">Można [zaimplementować niestandardowe konwertery](system-text-json-converters-how-to.md) w celu obsługi dodatkowych typów lub zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="9aec2-147">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="9aec2-148">Jak odczytywać dane JSON do obiektów .NET (deserializacji)</span><span class="sxs-lookup"><span data-stu-id="9aec2-148">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="9aec2-149">Aby zdeserializować z ciągu lub pliku, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="9aec2-149">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="9aec2-150">Poniższy przykład odczytuje dane JSON z ciągu i tworzy wystąpienie `WeatherForecast` klasy pokazanej wcześniej dla [przykładu serializacji](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="9aec2-150">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="9aec2-151">Aby zdeserializować z pliku przy użyciu kodu synchronicznego, Odczytaj plik do ciągu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-151">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="9aec2-152">Aby zdeserializować z pliku przy użyciu kodu asynchronicznego, wywołaj <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> metodę:</span><span class="sxs-lookup"><span data-stu-id="9aec2-152">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="9aec2-153">Deserializacja z UTF-8</span><span class="sxs-lookup"><span data-stu-id="9aec2-153">Deserialize from UTF-8</span></span>

<span data-ttu-id="9aec2-154">Aby zdeserializować z UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Przeciążenie, które pobiera `Utf8JsonReader` lub a `ReadOnlySpan<byte>`, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="9aec2-154">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="9aec2-155">W przykładach założono, że kod JSON znajduje się w tablicy bajtów o nazwie jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="9aec2-155">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="9aec2-156">Zachowanie deserializacji</span><span class="sxs-lookup"><span data-stu-id="9aec2-156">Deserialization behavior</span></span>

* <span data-ttu-id="9aec2-157">Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="9aec2-157">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="9aec2-158">Można [określić wielkość liter](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="9aec2-158">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="9aec2-159">Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9aec2-159">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="9aec2-160">Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="9aec2-160">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="9aec2-161">Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="9aec2-161">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="9aec2-162">Domyślnie wyliczenia są obsługiwane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="9aec2-162">By default, enums are supported as numbers.</span></span> <span data-ttu-id="9aec2-163">[Nazwy wyliczenia można serializować jako ciągi](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="9aec2-163">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="9aec2-164">Pola nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="9aec2-164">Fields aren't supported.</span></span>
* <span data-ttu-id="9aec2-165">Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON.</span><span class="sxs-lookup"><span data-stu-id="9aec2-165">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="9aec2-166">Można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="9aec2-166">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="9aec2-167">[Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.</span><span class="sxs-lookup"><span data-stu-id="9aec2-167">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="9aec2-168">[Konwertery niestandardowe można zaimplementować](system-text-json-converters-how-to.md) w celu zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="9aec2-168">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="9aec2-169">Serializacja do sformatowanego pliku JSON</span><span class="sxs-lookup"><span data-stu-id="9aec2-169">Serialize to formatted JSON</span></span>

<span data-ttu-id="9aec2-170">Aby całkiem wydrukować dane wyjściowe JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true`:</span><span class="sxs-lookup"><span data-stu-id="9aec2-170">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="9aec2-171">Oto przykład typu do serializacji i całkiem wydrukowanych danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-171">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="9aec2-172">Dostosowywanie nazw i wartości JSON</span><span class="sxs-lookup"><span data-stu-id="9aec2-172">Customize JSON names and values</span></span>

<span data-ttu-id="9aec2-173">Domyślnie nazwy właściwości i klucze słownika nie są zmieniane w danych wyjściowych JSON, włącznie z wielkością liter.</span><span class="sxs-lookup"><span data-stu-id="9aec2-173">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="9aec2-174">Wartości wyliczeniowe są reprezentowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="9aec2-174">Enum values are represented as numbers.</span></span> <span data-ttu-id="9aec2-175">W tej sekcji wyjaśniono, jak:</span><span class="sxs-lookup"><span data-stu-id="9aec2-175">This section explains how to:</span></span>

* [<span data-ttu-id="9aec2-176">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="9aec2-176">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="9aec2-177">Konwertuj wszystkie nazwy właściwości na notacji CamelCase przypadku</span><span class="sxs-lookup"><span data-stu-id="9aec2-177">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="9aec2-178">Implementowanie zasad nazewnictwa właściwości niestandardowych</span><span class="sxs-lookup"><span data-stu-id="9aec2-178">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="9aec2-179">Konwertuj klucze słownika na notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="9aec2-179">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="9aec2-180">Konwertuj wyliczenia na ciągi i notacji CamelCase wielkość liter</span><span class="sxs-lookup"><span data-stu-id="9aec2-180">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="9aec2-181">W przypadku innych scenariuszy, które wymagają specjalnej obsługi nazw i wartości właściwości JSON, można [zaimplementować konwertery niestandardowe](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="9aec2-181">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="9aec2-182">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="9aec2-182">Customize individual property names</span></span>

<span data-ttu-id="9aec2-183">Aby ustawić nazwę poszczególnych właściwości, Użyj atrybutu [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="9aec2-183">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="9aec2-184">Oto przykład typu do serializacji i powstającego JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-184">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="9aec2-185">Nazwa właściwości ustawiona przez ten atrybut:</span><span class="sxs-lookup"><span data-stu-id="9aec2-185">The property name set by this attribute:</span></span>

* <span data-ttu-id="9aec2-186">Stosuje się w obu kierunkach dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-186">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="9aec2-187">Ma pierwszeństwo przed zasadami nazewnictwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="9aec2-187">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="9aec2-188">Użyj notacji CamelCase przypadku dla wszystkich nazw właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="9aec2-188">Use camel case for all JSON property names</span></span>

<span data-ttu-id="9aec2-189">Aby użyć notacji CamelCase przypadku wszystkich nazw właściwości JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> tak `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-189">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="9aec2-190">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-190">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="9aec2-191">Zasady nazewnictwa właściwości przypadku notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="9aec2-191">The camel case property naming policy:</span></span>

* <span data-ttu-id="9aec2-192">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-192">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="9aec2-193">Jest zastępowany `[JsonPropertyName]` przez atrybuty.</span><span class="sxs-lookup"><span data-stu-id="9aec2-193">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="9aec2-194">Jest to dlatego, że nazwa `Wind` właściwości JSON w przykładzie nie jest notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="9aec2-194">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="9aec2-195">Użyj niestandardowych zasad nazewnictwa właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="9aec2-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="9aec2-196">Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę, która pochodzi od <xref:System.Text.Json.JsonNamingPolicy> i przesłania <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> metodę, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="9aec2-197">Następnie ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> właściwość na wystąpienie klasy zasad nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="9aec2-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-198">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-198">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="9aec2-199">Zasady nazewnictwa właściwości JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="9aec2-200">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="9aec2-201">Jest zastępowany `[JsonPropertyName]` przez atrybuty.</span><span class="sxs-lookup"><span data-stu-id="9aec2-201">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="9aec2-202">Jest to dlatego, że nazwa `Wind` właściwości JSON w przykładzie nie jest wielką literą.</span><span class="sxs-lookup"><span data-stu-id="9aec2-202">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="9aec2-203">Klucze słownika przypadku notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="9aec2-203">Camel case dictionary keys</span></span>

<span data-ttu-id="9aec2-204">Jeśli właściwość obiektu, który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>`, `string` klucze mogą być konwertowane na notacji CamelCase przypadku.</span><span class="sxs-lookup"><span data-stu-id="9aec2-204">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="9aec2-205">W tym celu ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-205">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-206">Serializacja obiektu ze słownikiem o nazwie `TemperatureRanges` , który ma pary `"ColdMinTemp", 20` klucz-wartość i `"HotMinTemp", 40` spowodowałaby wyjście JSON podobne do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="9aec2-206">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="9aec2-207">Zasady nazewnictwa przypadków notacji CamelCase dla kluczy słownika mają zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-207">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="9aec2-208">W przypadku deserializacji słownika klucze będą zgodne z plikiem JSON nawet w przypadku określenia `JsonNamingPolicy.CamelCase` dla. `DictionaryKeyPolicy`</span><span class="sxs-lookup"><span data-stu-id="9aec2-208">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="9aec2-209">Wyliczenia jako ciągi</span><span class="sxs-lookup"><span data-stu-id="9aec2-209">Enums as strings</span></span>

<span data-ttu-id="9aec2-210">Domyślnie wyliczenia są serializowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="9aec2-210">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="9aec2-211">Aby serializować nazwy wyliczenia jako ciągi, użyj <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="9aec2-211">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="9aec2-212">Załóżmy na przykład, że trzeba serializować następujące klasy, które mają Wyliczenie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-212">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="9aec2-213">Jeśli podsumowanie jest `Hot`, domyślnie SERIALIZOWANY kod JSON ma wartość liczbową 3:</span><span class="sxs-lookup"><span data-stu-id="9aec2-213">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="9aec2-214">Następujący przykładowy kod serializować nazwy wyliczenia zamiast wartości liczbowych i konwertuje nazwy na notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="9aec2-214">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-215">Wynikowy kod JSON wygląda podobnie do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="9aec2-215">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="9aec2-216">Można również deserializować nazwy ciągów wyliczenia, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-216">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="9aec2-217">Wyklucz właściwości z serializacji</span><span class="sxs-lookup"><span data-stu-id="9aec2-217">Exclude properties from serialization</span></span>

<span data-ttu-id="9aec2-218">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="9aec2-218">By default, all public properties are serialized.</span></span> <span data-ttu-id="9aec2-219">Jeśli nie chcesz, aby niektóre z nich pojawiały się w danych wyjściowych JSON, masz kilka opcji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-219">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="9aec2-220">W tej sekcji wyjaśniono, jak wykluczyć:</span><span class="sxs-lookup"><span data-stu-id="9aec2-220">This section explains how to exclude:</span></span>

* [<span data-ttu-id="9aec2-221">Poszczególne właściwości</span><span class="sxs-lookup"><span data-stu-id="9aec2-221">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="9aec2-222">Wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9aec2-222">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="9aec2-223">Wszystkie właściwości o wartości null</span><span class="sxs-lookup"><span data-stu-id="9aec2-223">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="9aec2-224">Wyklucz pojedyncze właściwości</span><span class="sxs-lookup"><span data-stu-id="9aec2-224">Exclude individual properties</span></span>

<span data-ttu-id="9aec2-225">Aby zignorować poszczególne właściwości, Użyj atrybutu [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="9aec2-225">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="9aec2-226">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-226">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="9aec2-227">Wyklucz wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9aec2-227">Exclude all read-only properties</span></span>

<span data-ttu-id="9aec2-228">Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="9aec2-228">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="9aec2-229">Aby wykluczyć wszystkie właściwości tylko <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> do odczytu, ustaw wartość na `true`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-230">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-230">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="9aec2-231">Ta opcja ma zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-231">This option applies only to serialization.</span></span> <span data-ttu-id="9aec2-232">Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9aec2-232">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="9aec2-233">Wyklucz wszystkie właściwości wartości null</span><span class="sxs-lookup"><span data-stu-id="9aec2-233">Exclude all null value properties</span></span>

<span data-ttu-id="9aec2-234">Aby wykluczyć wszystkie właściwości wartości null, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> właściwość na `true`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-234">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-235">Oto przykład obiektu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-235">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="9aec2-236">Właściwość</span><span class="sxs-lookup"><span data-stu-id="9aec2-236">Property</span></span> |<span data-ttu-id="9aec2-237">Wartość</span><span class="sxs-lookup"><span data-stu-id="9aec2-237">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="9aec2-238">Date</span><span class="sxs-lookup"><span data-stu-id="9aec2-238">Date</span></span>    | <span data-ttu-id="9aec2-239">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="9aec2-239">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="9aec2-240">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="9aec2-240">TemperatureCelsius</span></span>| <span data-ttu-id="9aec2-241">25</span><span class="sxs-lookup"><span data-stu-id="9aec2-241">25</span></span> |
| <span data-ttu-id="9aec2-242">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="9aec2-242">Summary</span></span>| <span data-ttu-id="9aec2-243">wartość null</span><span class="sxs-lookup"><span data-stu-id="9aec2-243">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="9aec2-244">To ustawienie dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-244">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="9aec2-245">Aby uzyskać informacje o jego wpływie na deserializacji, zobacz [Ignore null podczas deserializacji](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="9aec2-245">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="9aec2-246">Dostosuj kodowanie znaków</span><span class="sxs-lookup"><span data-stu-id="9aec2-246">Customize character encoding</span></span>

<span data-ttu-id="9aec2-247">Domyślnie serializator wyprowadza wszystkie znaki nienależące do zestawu znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="9aec2-247">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="9aec2-248">Oznacza to, że zastępuje je, `\uxxxx` gdzie `xxxx` jest kodem Unicode znaku.</span><span class="sxs-lookup"><span data-stu-id="9aec2-248">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="9aec2-249">Na przykład, jeśli `Summary` właściwość jest ustawiona na wartość cyrylicy жарко, `WeatherForecast` obiekt jest serializowany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-249">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="9aec2-250">Serializowanie zestawów znaków języka</span><span class="sxs-lookup"><span data-stu-id="9aec2-250">Serialize language character sets</span></span>

<span data-ttu-id="9aec2-251">Aby serializować zestawy znaków z co najmniej jednego języka bez ucieczki, określ [zakresy Unicode](xref:System.Text.Unicode.UnicodeRanges) podczas tworzenia wystąpienia <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-251">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="9aec2-252">Ten kod nie ma ucieczki znaków cyrylicy lub greckich.</span><span class="sxs-lookup"><span data-stu-id="9aec2-252">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="9aec2-253">Jeśli `Summary` właściwość jest ustawiona na wartość cyrylicy жарко, `WeatherForecast` obiekt jest serializowany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-253">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="9aec2-254">Aby serializować wszystkie zestawy językowe bez ucieczki, użyj <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9aec2-254">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="9aec2-255">Serializacja określonych znaków</span><span class="sxs-lookup"><span data-stu-id="9aec2-255">Serialize specific characters</span></span>

<span data-ttu-id="9aec2-256">Alternatywą jest określenie pojedynczych znaków, które mają być dozwolone, bez konieczności ucieczki.</span><span class="sxs-lookup"><span data-stu-id="9aec2-256">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="9aec2-257">Poniższy przykład serializacji tylko dwa pierwsze znaki жарко:</span><span class="sxs-lookup"><span data-stu-id="9aec2-257">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="9aec2-258">Oto przykład kodu JSON utworzonego przez poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="9aec2-258">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="9aec2-259">Serializować wszystkie znaki</span><span class="sxs-lookup"><span data-stu-id="9aec2-259">Serialize all characters</span></span>

<span data-ttu-id="9aec2-260">Aby zminimalizować liczbę ucieczki, można <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>użyć, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-260">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="9aec2-261">W porównaniu z domyślnym koderem `UnsafeRelaxedJsonEscaping` koder jest bardziej ograniczając, aby umożliwić przekazywanie znaków przez niezmieniony:</span><span class="sxs-lookup"><span data-stu-id="9aec2-261">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="9aec2-262">Nie ucieczk znaków w języku HTML, takich jak `<`, `>`, `&`, i `'`.</span><span class="sxs-lookup"><span data-stu-id="9aec2-262">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="9aec2-263">Nie oferuje żadnej dodatkowej ochrony przed atakami na ataki typu XSS lub ujawnienie informacji, takich jak te, które mogą wynikać z klienta i serwera bez zgody na *zestaw znaków*.</span><span class="sxs-lookup"><span data-stu-id="9aec2-263">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="9aec2-264">Używaj niebezpiecznego kodera tylko wtedy, gdy wiadomo, że klient będzie interpretować otrzymany ładunek jako zakodowany w formacie JSON UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9aec2-264">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="9aec2-265">Można na przykład użyć go, jeśli serwer wysyła nagłówek `Content-Type: application/json; charset=utf-8`odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9aec2-265">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="9aec2-266">Nigdy nie Zezwalaj na `UnsafeRelaxedJsonEscaping` emitowanie nieprzetworzonych danych wyjściowych do strony HTML `<script>` lub elementu.</span><span class="sxs-lookup"><span data-stu-id="9aec2-266">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="9aec2-267">Serializowanie właściwości klas pochodnych</span><span class="sxs-lookup"><span data-stu-id="9aec2-267">Serialize properties of derived classes</span></span>

<span data-ttu-id="9aec2-268">Serializacja hierarchii typów polimorficznych nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="9aec2-268">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="9aec2-269">Na przykład, jeśli właściwość jest zdefiniowana jako interfejs lub Klasa abstrakcyjna, tylko właściwości zdefiniowane w interfejsie lub klasie abstrakcyjnej są serializowane, nawet jeśli typ środowiska uruchomieniowego ma dodatkowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="9aec2-269">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="9aec2-270">Wyjątki dotyczące tego zachowania zostały omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-270">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="9aec2-271">Załóżmy na przykład, że masz `WeatherForecast` klasę i klasę `WeatherForecastDerived`pochodną:</span><span class="sxs-lookup"><span data-stu-id="9aec2-271">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="9aec2-272">I Załóżmy, że argument typu `Serialize` metody w czasie kompilacji to: `WeatherForecast`</span><span class="sxs-lookup"><span data-stu-id="9aec2-272">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="9aec2-273">W tym scenariuszu `WindSpeed` właściwość nie jest serializowana, nawet jeśli `weatherForecast` obiekt jest rzeczywiście `WeatherForecastDerived` obiektem.</span><span class="sxs-lookup"><span data-stu-id="9aec2-273">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="9aec2-274">Tylko właściwości klasy bazowej są serializowane:</span><span class="sxs-lookup"><span data-stu-id="9aec2-274">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="9aec2-275">Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="9aec2-275">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="9aec2-276">Aby serializować właściwości typu pochodnego w poprzednim przykładzie, należy użyć jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="9aec2-276">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="9aec2-277">Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A> , które pozwala określić typ w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="9aec2-277">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="9aec2-278">Zadeklaruj obiekt, który ma zostać `object`Zserializowany jako.</span><span class="sxs-lookup"><span data-stu-id="9aec2-278">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="9aec2-279">W poprzednim przykładowym scenariuszu oba podejścia powodują, `WindSpeed` że właściwość powinna zostać uwzględniona w danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-279">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="9aec2-280">Te podejścia zapewniają serializację polimorficzne tylko dla obiektu głównego, który ma być serializowany, a nie dla właściwości tego obiektu głównego.</span><span class="sxs-lookup"><span data-stu-id="9aec2-280">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="9aec2-281">Można uzyskać serializację polimorficzny dla obiektów niższego poziomu, jeśli zdefiniujesz je jako `object`typ.</span><span class="sxs-lookup"><span data-stu-id="9aec2-281">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="9aec2-282">Na przykład `WeatherForecast` Załóżmy, że Klasa ma właściwość o nazwie `PreviousForecast` , która może być zdefiniowana jako typ `WeatherForecast` lub `object`:</span><span class="sxs-lookup"><span data-stu-id="9aec2-282">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="9aec2-283">Jeśli `PreviousForecast` Właściwość zawiera wystąpienie `WeatherForecastDerived`:</span><span class="sxs-lookup"><span data-stu-id="9aec2-283">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="9aec2-284">Dane wyjściowe JSON z serializacji `WeatherForecastWithPrevious` **nie obejmują** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="9aec2-284">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="9aec2-285">Dane wyjściowe JSON z serializacji `WeatherForecastWithPreviousAsObject` **obejmują** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="9aec2-285">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="9aec2-286">Aby serializować `WeatherForecastWithPreviousAsObject`, nie jest konieczne wywołanie `Serialize<object>` lub `GetType` ponieważ obiekt główny nie jest tym, który może znajdować się w typie pochodnym.</span><span class="sxs-lookup"><span data-stu-id="9aec2-286">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="9aec2-287">Poniższy przykład kodu nie wywołuje `Serialize<object>` lub: `GetType`</span><span class="sxs-lookup"><span data-stu-id="9aec2-287">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="9aec2-288">Powyższy kod poprawnie serializować `WeatherForecastWithPreviousAsObject`:</span><span class="sxs-lookup"><span data-stu-id="9aec2-288">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="9aec2-289">To samo podejście do definiowania właściwości jako `object` współdziałanie z interfejsami.</span><span class="sxs-lookup"><span data-stu-id="9aec2-289">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="9aec2-290">Załóżmy, że masz następujący interfejs i implementacja, i chcesz serializować klasę o właściwościach zawierających wystąpienia implementacji:</span><span class="sxs-lookup"><span data-stu-id="9aec2-290">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="9aec2-291">Podczas serializacji wystąpienia `Forecasts`elementu, wyświetlana jest tylko `Tuesday` `WindSpeed` właściwość, ponieważ `Tuesday` jest zdefiniowana jako: `object`</span><span class="sxs-lookup"><span data-stu-id="9aec2-291">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="9aec2-292">Poniższy przykład pokazuje kod JSON, który wynika z poprzedniego kodu:</span><span class="sxs-lookup"><span data-stu-id="9aec2-292">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="9aec2-293">Aby uzyskać więcej informacji na temat **serializacji**polimorficznej i informacje o **deserializacji**, zobacz [Migrowanie z Newtonsoft. JSON do System. Text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="9aec2-293">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="9aec2-294">Zezwalaj na komentarze i końcowe przecinki</span><span class="sxs-lookup"><span data-stu-id="9aec2-294">Allow comments and trailing commas</span></span>

<span data-ttu-id="9aec2-295">Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON.</span><span class="sxs-lookup"><span data-stu-id="9aec2-295">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="9aec2-296">Aby zezwolić na komentarze w formacie JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> właściwość na `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="9aec2-296">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="9aec2-297">I aby zezwolić na końcowe przecinki, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> właściwość na `true`.</span><span class="sxs-lookup"><span data-stu-id="9aec2-297">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="9aec2-298">Poniższy przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="9aec2-298">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="9aec2-299">Oto przykładowy kod JSON z komentarzami i końcowym przecinkiem:</span><span class="sxs-lookup"><span data-stu-id="9aec2-299">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="9aec2-300">Dopasowanie właściwości bez uwzględniania wielkości liter</span><span class="sxs-lookup"><span data-stu-id="9aec2-300">Case-insensitive property matching</span></span>

<span data-ttu-id="9aec2-301">Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9aec2-301">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="9aec2-302">Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> opcję `true`na:</span><span class="sxs-lookup"><span data-stu-id="9aec2-302">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="9aec2-303">Oto przykład JSON z nazwami właściwości przypadku notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="9aec2-303">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="9aec2-304">Można ją zdeserializować do następującego typu, który ma nazwy właściwości przypadku języka Pascal.</span><span class="sxs-lookup"><span data-stu-id="9aec2-304">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="9aec2-305">Obsługa przepełnienia kodu JSON</span><span class="sxs-lookup"><span data-stu-id="9aec2-305">Handle overflow JSON</span></span>

<span data-ttu-id="9aec2-306">Podczas deserializacji można odbierać dane w formacie JSON, które nie są reprezentowane przez właściwości typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="9aec2-306">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="9aec2-307">Załóżmy na przykład, że typ docelowy to:</span><span class="sxs-lookup"><span data-stu-id="9aec2-307">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="9aec2-308">I kod JSON do deserializacji jest następujący:</span><span class="sxs-lookup"><span data-stu-id="9aec2-308">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="9aec2-309">W przypadku deserializacji kodu JSON pokazanego w pokazanym `SummaryWords` typie, właściwości i mają wartość `DatesAvailable` Nowhere to go i są tracone.</span><span class="sxs-lookup"><span data-stu-id="9aec2-309">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="9aec2-310">Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub: `Dictionary<string,JsonElement>`</span><span class="sxs-lookup"><span data-stu-id="9aec2-310">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="9aec2-311">Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie próbkowania dodatkowe dane staną się parami klucz-wartość `ExtensionData` właściwości:</span><span class="sxs-lookup"><span data-stu-id="9aec2-311">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="9aec2-312">Właściwość</span><span class="sxs-lookup"><span data-stu-id="9aec2-312">Property</span></span> |<span data-ttu-id="9aec2-313">Wartość</span><span class="sxs-lookup"><span data-stu-id="9aec2-313">Value</span></span>  |<span data-ttu-id="9aec2-314">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9aec2-314">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="9aec2-315">Date</span><span class="sxs-lookup"><span data-stu-id="9aec2-315">Date</span></span>    | <span data-ttu-id="9aec2-316">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="9aec2-316">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="9aec2-317">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="9aec2-317">TemperatureCelsius</span></span>| <span data-ttu-id="9aec2-318">0</span><span class="sxs-lookup"><span data-stu-id="9aec2-318">0</span></span> | <span data-ttu-id="9aec2-319">Niezgodność z rozróżnianiem`temperatureCelsius` wielkości liter (w formacie JSON), więc właściwość nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="9aec2-319">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="9aec2-320">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="9aec2-320">Summary</span></span> | <span data-ttu-id="9aec2-321">Gorąca</span><span class="sxs-lookup"><span data-stu-id="9aec2-321">Hot</span></span> ||
| <span data-ttu-id="9aec2-322">ExtensionData —</span><span class="sxs-lookup"><span data-stu-id="9aec2-322">ExtensionData</span></span> | <span data-ttu-id="9aec2-323">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="9aec2-323">temperatureCelsius: 25</span></span> |<span data-ttu-id="9aec2-324">Ponieważ przypadek nie jest zgodny, ta właściwość JSON jest dodatkową i jest parą klucz-wartość w słowniku.</span><span class="sxs-lookup"><span data-stu-id="9aec2-324">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="9aec2-325">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="9aec2-325">DatesAvailable:</span></span><br>  <span data-ttu-id="9aec2-326">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="9aec2-326">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="9aec2-327">8/2/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="9aec2-327">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="9aec2-328">Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="9aec2-328">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="9aec2-329">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="9aec2-329">SummaryWords:</span></span><br><span data-ttu-id="9aec2-330">Chłodna</span><span class="sxs-lookup"><span data-stu-id="9aec2-330">Cool</span></span><br><span data-ttu-id="9aec2-331">Wiatr</span><span class="sxs-lookup"><span data-stu-id="9aec2-331">Windy</span></span><br><span data-ttu-id="9aec2-332">Humid</span><span class="sxs-lookup"><span data-stu-id="9aec2-332">Humid</span></span> |<span data-ttu-id="9aec2-333">Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="9aec2-333">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="9aec2-334">Gdy obiekt docelowy jest serializowany, pary wartości klucza danych rozszerzenia stają się właściwościami JSON tak samo jak w przychodzących danych JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-334">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="9aec2-335">Zauważ, że `ExtensionData` nazwa właściwości nie pojawia się w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="9aec2-335">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="9aec2-336">Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.</span><span class="sxs-lookup"><span data-stu-id="9aec2-336">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="9aec2-337">Ignoruj wartość null podczas deserializacji</span><span class="sxs-lookup"><span data-stu-id="9aec2-337">Ignore null when deserializing</span></span>

<span data-ttu-id="9aec2-338">Domyślnie, jeśli właściwość w formacie JSON ma wartość null, odpowiadająca jej właściwość w obiekcie docelowym ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="9aec2-338">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="9aec2-339">W niektórych scenariuszach właściwość target może mieć wartość domyślną i nie ma potrzeby przesłonięcia wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="9aec2-339">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="9aec2-340">Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:</span><span class="sxs-lookup"><span data-stu-id="9aec2-340">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="9aec2-341">Załóżmy, że następujący kod JSON jest deserializowany:</span><span class="sxs-lookup"><span data-stu-id="9aec2-341">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="9aec2-342">Po deserializacji `Summary` Właściwość `WeatherForecastWithDefault` obiektu ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="9aec2-342">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="9aec2-343">Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> wartość `true`tak, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-343">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="9aec2-344">W przypadku tej opcji `Summary` Właściwość `WeatherForecastWithDefault` obiektu jest wartością domyślną "Brak podsumowania" po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-344">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="9aec2-345">Wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="9aec2-345">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="9aec2-346">Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki.</span><span class="sxs-lookup"><span data-stu-id="9aec2-346">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="9aec2-347">Utf8JsonReader, Utf8JsonWriter i JsonDocument</span><span class="sxs-lookup"><span data-stu-id="9aec2-347">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="9aec2-348"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>jest wysoką wydajnością, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, `ReadOnlySpan<byte>` Odczytaj z lub `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="9aec2-348"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="9aec2-349">`Utf8JsonReader` Jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-349">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="9aec2-350"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Metoda używa `Utf8JsonReader` w obszarze okładki.</span><span class="sxs-lookup"><span data-stu-id="9aec2-350">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="9aec2-351"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>jest wysoce wydajnym sposobem pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy `String`.NET `Int32`, takich `DateTime`jak,, i.</span><span class="sxs-lookup"><span data-stu-id="9aec2-351"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="9aec2-352">Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="9aec2-352">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="9aec2-353"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> Metoda używa `Utf8JsonWriter` w obszarze okładki.</span><span class="sxs-lookup"><span data-stu-id="9aec2-353">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="9aec2-354"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>zapewnia możliwość tworzenia Document Object Model tylko do odczytu (DOM) za pomocą programu `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="9aec2-354"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="9aec2-355">DOM zapewnia losowy dostęp do danych w ładunku JSON.</span><span class="sxs-lookup"><span data-stu-id="9aec2-355">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="9aec2-356">Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typu.</span><span class="sxs-lookup"><span data-stu-id="9aec2-356">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="9aec2-357">`JsonElement` Typ udostępnia moduł wyliczający tablic i obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET.</span><span class="sxs-lookup"><span data-stu-id="9aec2-357">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="9aec2-358">`JsonDocument`uwidacznia <xref:System.Text.Json.JsonDocument.RootElement> właściwość.</span><span class="sxs-lookup"><span data-stu-id="9aec2-358">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="9aec2-359">W poniższych sekcjach pokazano, jak używać tych narzędzi do odczytywania i pisania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="9aec2-359">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="9aec2-360">Korzystanie z JsonDocument do uzyskiwania dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="9aec2-360">Use JsonDocument for access to data</span></span>

<span data-ttu-id="9aec2-361">Poniższy przykład pokazuje, <xref:System.Text.Json.JsonDocument> jak używać klasy do losowego dostępu do danych w ciągu JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-361">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="9aec2-362">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-362">The preceding code:</span></span>

* <span data-ttu-id="9aec2-363">Przyjęto, że kod JSON do analizy jest w `jsonString`ciągu o nazwie.</span><span class="sxs-lookup"><span data-stu-id="9aec2-363">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="9aec2-364">Oblicza średnią ocenę dla obiektów w `Students` tablicy, która ma `Grade` właściwość.</span><span class="sxs-lookup"><span data-stu-id="9aec2-364">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="9aec2-365">Przypisuje domyślną ocenę 70 dla studentów, którzy nie posiadają klasy.</span><span class="sxs-lookup"><span data-stu-id="9aec2-365">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="9aec2-366">Zlicza uczniów przez zwiększenie `count` zmiennej przy każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="9aec2-366">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="9aec2-367">Alternatywą jest wywołanie <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-367">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="9aec2-368">Oto przykład pliku JSON, który jest przetwarzany przez ten kod:</span><span class="sxs-lookup"><span data-stu-id="9aec2-368">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="9aec2-369">Użyj JsonDocument, aby zapisać kod JSON</span><span class="sxs-lookup"><span data-stu-id="9aec2-369">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="9aec2-370">Poniższy przykład pokazuje, <xref:System.Text.Json.JsonDocument>jak napisać kod JSON z:</span><span class="sxs-lookup"><span data-stu-id="9aec2-370">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="9aec2-371">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-371">The preceding code:</span></span>

* <span data-ttu-id="9aec2-372">Odczytuje plik JSON, ładuje dane do `JsonDocument`i zapisuje sformatowany plik JSON w formacie.</span><span class="sxs-lookup"><span data-stu-id="9aec2-372">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="9aec2-373">Używa <xref:System.Text.Json.JsonDocumentOptions> do określenia, czy komentarze w wejściowym formacie JSON są dozwolone, ale ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9aec2-373">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="9aec2-374">Po zakończeniu wywołania <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> na składniku zapisywania.</span><span class="sxs-lookup"><span data-stu-id="9aec2-374">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="9aec2-375">Alternatywą jest umożliwienie składnika zapisywania AutoFlush, gdy zostanie on usunięty.</span><span class="sxs-lookup"><span data-stu-id="9aec2-375">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="9aec2-376">Oto przykład danych wejściowych JSON do przetworzenia przez przykładowy kod:</span><span class="sxs-lookup"><span data-stu-id="9aec2-376">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="9aec2-377">Wynikiem są następujące niedrukowane dane wyjściowe JSON:</span><span class="sxs-lookup"><span data-stu-id="9aec2-377">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="9aec2-378">Użyj Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="9aec2-378">Use Utf8JsonWriter</span></span>

<span data-ttu-id="9aec2-379">Poniższy przykład pokazuje, <xref:System.Text.Json.Utf8JsonWriter> jak używać klasy:</span><span class="sxs-lookup"><span data-stu-id="9aec2-379">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="9aec2-380">Użyj Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="9aec2-380">Use Utf8JsonReader</span></span>

<span data-ttu-id="9aec2-381">Poniższy przykład pokazuje, <xref:System.Text.Json.Utf8JsonReader> jak używać klasy:</span><span class="sxs-lookup"><span data-stu-id="9aec2-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="9aec2-382">Poprzedni kod założono, że `jsonUtf8` zmienna jest tablicą bajtową, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9aec2-382">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="9aec2-383">Filtrowanie danych za pomocą Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="9aec2-383">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="9aec2-384">Poniższy przykład pokazuje, jak odczytywać plik synchronicznie i wyszukiwać wartość:</span><span class="sxs-lookup"><span data-stu-id="9aec2-384">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="9aec2-385">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="9aec2-385">The preceding code:</span></span>

* <span data-ttu-id="9aec2-386">Przyjęto, że kod JSON zawiera tablicę obiektów, a każdy obiekt może zawierać właściwość "name" typu String.</span><span class="sxs-lookup"><span data-stu-id="9aec2-386">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="9aec2-387">Zlicza obiekty i wartości właściwości "name", które kończą się znakiem "University".</span><span class="sxs-lookup"><span data-stu-id="9aec2-387">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="9aec2-388">Przyjęto założenie, że plik jest zakodowany jako UTF-16 i transkoduje go do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9aec2-388">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="9aec2-389">Plik zakodowany jako UTF-8 może być odczytywany bezpośrednio do `ReadOnlySpan<byte>`programu, przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9aec2-389">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="9aec2-390">Jeśli plik zawiera znacznik kolejności bajtów UTF-8, usuń go przed przekazaniem bajtów do `Utf8JsonReader`, ponieważ czytnik oczekuje tekstu.</span><span class="sxs-lookup"><span data-stu-id="9aec2-390">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="9aec2-391">W przeciwnym razie BOM jest traktowany jako nieprawidłowy kod JSON, a czytelnik zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="9aec2-391">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="9aec2-392">Oto przykład JSON, który może odczytać poprzedzający kod.</span><span class="sxs-lookup"><span data-stu-id="9aec2-392">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="9aec2-393">Otrzymany komunikat podsumowujący to "2 z 4 mają nazwy kończące się na" University ":</span><span class="sxs-lookup"><span data-stu-id="9aec2-393">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="9aec2-394">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="9aec2-394">Additional resources</span></span>

* <span data-ttu-id="9aec2-395">[System.Text.JsonPodsumowanie](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="9aec2-395">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="9aec2-396">Jak pisać konwertery niestandardowe</span><span class="sxs-lookup"><span data-stu-id="9aec2-396">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="9aec2-397">[Jak przeprowadzić migrację zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="9aec2-397">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="9aec2-398">[Obsługa DateTime i DateTimeOffset wSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="9aec2-398">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="9aec2-399">[System.Text.JsonDokumentacja interfejsu API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="9aec2-399">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
