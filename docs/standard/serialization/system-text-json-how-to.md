---
title: Jak serializować i deserializować kod JSON przy użyciu języka C# — .NET
description: W tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET. Zawiera przykładowy kod.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: ad748508b73c3e141ae345efa0abb66c009740cd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378720"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="3a33e-104">Jak serializować i deserializować (Marshaling and unmarshaling) JSON w programie .NET</span><span class="sxs-lookup"><span data-stu-id="3a33e-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="3a33e-105">W tym artykule pokazano, jak używać <xref:System.Text.Json> przestrzeni nazw do serializacji i deserializacji do i z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="3a33e-105">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="3a33e-106">W przypadku przenoszenia istniejącego kodu z programu `Newtonsoft.Json` zapoznaj się z tematem [jak `System.Text.Json` przeprowadzić migrację do programu ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="3a33e-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="3a33e-107">Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="3a33e-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="3a33e-108">Większość przykładowych kodów serializacji <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> do `true` "DB-Print" w formacie JSON (z wcięciem i białym znakiem).</span><span class="sxs-lookup"><span data-stu-id="3a33e-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="3a33e-109">Do użycia w środowisku produkcyjnym zwykle przyjmuje się wartość domyślną `false` dla tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="3a33e-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="3a33e-110">Przykłady kodu odnoszą się do następującej klasy i wariantów:</span><span class="sxs-lookup"><span data-stu-id="3a33e-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="3a33e-111">Namespaces</span><span class="sxs-lookup"><span data-stu-id="3a33e-111">Namespaces</span></span>

<span data-ttu-id="3a33e-112"><xref:System.Text.Json>Przestrzeń nazw zawiera wszystkie punkty wejścia i typy główne.</span><span class="sxs-lookup"><span data-stu-id="3a33e-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="3a33e-113"><xref:System.Text.Json.Serialization>Przestrzeń nazw zawiera atrybuty i interfejsy API dla zaawansowanych scenariuszy i dostosowań specyficznych dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="3a33e-114">Przykłady kodu przedstawione w tym artykule wymagają `using` dyrektyw dla jednej lub obu tych przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="3a33e-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="3a33e-115">Atrybuty z <xref:System.Runtime.Serialization> przestrzeni nazw nie są obecnie obsługiwane w programie `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="3a33e-116">Pisanie obiektów .NET w formacie JSON (Serializacja)</span><span class="sxs-lookup"><span data-stu-id="3a33e-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="3a33e-117">Aby zapisać dane JSON do ciągu lub do pliku, wywołaj <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="3a33e-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="3a33e-118">Poniższy przykład tworzy kod JSON jako ciąg:</span><span class="sxs-lookup"><span data-stu-id="3a33e-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-119">Poniższy przykład używa kodu synchronicznego do utworzenia pliku JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-120">W poniższym przykładzie jest tworzony plik JSON przy użyciu kodu asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="3a33e-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-121">Powyższe przykłady używają wnioskowania typu dla serializowanego typu.</span><span class="sxs-lookup"><span data-stu-id="3a33e-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="3a33e-122">Przeciążenie `Serialize()` przyjmuje parametr typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="3a33e-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="3a33e-123">Przykład serializacji</span><span class="sxs-lookup"><span data-stu-id="3a33e-123">Serialization example</span></span>

<span data-ttu-id="3a33e-124">Oto przykładowa Klasa, która zawiera kolekcje i zagnieżdżoną klasę:</span><span class="sxs-lookup"><span data-stu-id="3a33e-124">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="3a33e-125">Dane wyjściowe JSON serializowania wystąpienia poprzedniego typu wyglądają podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3a33e-125">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="3a33e-126">Dane wyjściowe JSON domyślnie są zminimalizowanego:</span><span class="sxs-lookup"><span data-stu-id="3a33e-126">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="3a33e-127">W poniższym przykładzie przedstawiono ten sam kod JSON, sformatowany (to jest całkiem wydruk z odstępami i wcięciami):</span><span class="sxs-lookup"><span data-stu-id="3a33e-127">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="3a33e-128">Serializacja do UTF-8</span><span class="sxs-lookup"><span data-stu-id="3a33e-128">Serialize to UTF-8</span></span>

<span data-ttu-id="3a33e-129">Aby serializować do UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> metodę:</span><span class="sxs-lookup"><span data-stu-id="3a33e-129">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-130"><xref:System.Text.Json.JsonSerializer.Serialize%2A>Dostępne jest również Przeciążenie, które trwa <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="3a33e-130">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="3a33e-131">Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach.</span><span class="sxs-lookup"><span data-stu-id="3a33e-131">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="3a33e-132">Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="3a33e-132">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="3a33e-133">Zachowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="3a33e-133">Serialization behavior</span></span>

* <span data-ttu-id="3a33e-134">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="3a33e-134">By default, all public properties are serialized.</span></span> <span data-ttu-id="3a33e-135">Można [określić właściwości do wykluczenia](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="3a33e-135">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="3a33e-136">[Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem języka HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="3a33e-136">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="3a33e-137">Domyślnie JSON jest zminimalizowanego.</span><span class="sxs-lookup"><span data-stu-id="3a33e-137">By default, JSON is minified.</span></span> <span data-ttu-id="3a33e-138">Można tu [wydrukować kod JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="3a33e-138">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="3a33e-139">Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET.</span><span class="sxs-lookup"><span data-stu-id="3a33e-139">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="3a33e-140">Można [dostosować wielkość liter w nazwach JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="3a33e-140">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="3a33e-141">Wykryto odwołania cykliczne i zostały zgłoszone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="3a33e-141">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="3a33e-142">Obecnie pola są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="3a33e-142">Currently, fields are excluded.</span></span>

<span data-ttu-id="3a33e-143">Obsługiwane typy to:</span><span class="sxs-lookup"><span data-stu-id="3a33e-143">Supported types include:</span></span>

* <span data-ttu-id="3a33e-144">Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="3a33e-144">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="3a33e-145">Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="3a33e-145">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="3a33e-146">Tablice jednowymiarowe i nieregularne ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="3a33e-146">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="3a33e-147">`Dictionary<string,TValue>`gdzie `TValue` is to `object` , `JsonElement` lub poco.</span><span class="sxs-lookup"><span data-stu-id="3a33e-147">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="3a33e-148">Kolekcje z następujących przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3a33e-148">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="3a33e-149">Można [zaimplementować niestandardowe konwertery](system-text-json-converters-how-to.md) w celu obsługi dodatkowych typów lub zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="3a33e-149">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="3a33e-150">Jak odczytywać dane JSON do obiektów .NET (deserializacji)</span><span class="sxs-lookup"><span data-stu-id="3a33e-150">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="3a33e-151">Aby zdeserializować z ciągu lub pliku, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="3a33e-151">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="3a33e-152">Poniższy przykład odczytuje dane JSON z ciągu i tworzy wystąpienie `WeatherForecast` klasy pokazanej wcześniej dla [przykładu serializacji](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="3a33e-152">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="3a33e-153">Aby zdeserializować z pliku przy użyciu kodu synchronicznego, Odczytaj plik do ciągu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-153">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="3a33e-154">Aby zdeserializować z pliku przy użyciu kodu asynchronicznego, wywołaj <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> metodę:</span><span class="sxs-lookup"><span data-stu-id="3a33e-154">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="3a33e-155">Deserializacja z UTF-8</span><span class="sxs-lookup"><span data-stu-id="3a33e-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="3a33e-156">Aby zdeserializować z UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Przeciążenie, które pobiera `Utf8JsonReader` lub a `ReadOnlySpan<byte>` , jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="3a33e-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="3a33e-157">W przykładach założono, że kod JSON znajduje się w tablicy bajtów o nazwie jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="3a33e-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="3a33e-158">Zachowanie deserializacji</span><span class="sxs-lookup"><span data-stu-id="3a33e-158">Deserialization behavior</span></span>

* <span data-ttu-id="3a33e-159">Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="3a33e-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="3a33e-160">Można [określić wielkość liter](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="3a33e-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="3a33e-161">Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3a33e-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="3a33e-162">Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="3a33e-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="3a33e-163">Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="3a33e-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="3a33e-164">Domyślnie wyliczenia są obsługiwane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="3a33e-164">By default, enums are supported as numbers.</span></span> <span data-ttu-id="3a33e-165">[Nazwy wyliczenia można serializować jako ciągi](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="3a33e-165">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="3a33e-166">Pola nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="3a33e-166">Fields aren't supported.</span></span>
* <span data-ttu-id="3a33e-167">Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON.</span><span class="sxs-lookup"><span data-stu-id="3a33e-167">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="3a33e-168">Można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="3a33e-168">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="3a33e-169">[Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.</span><span class="sxs-lookup"><span data-stu-id="3a33e-169">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="3a33e-170">[Konwertery niestandardowe można zaimplementować](system-text-json-converters-how-to.md) w celu zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="3a33e-170">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="3a33e-171">Serializacja do sformatowanego pliku JSON</span><span class="sxs-lookup"><span data-stu-id="3a33e-171">Serialize to formatted JSON</span></span>

<span data-ttu-id="3a33e-172">Aby całkiem wydrukować dane wyjściowe JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-172">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="3a33e-173">Oto przykład typu do serializacji i całkiem wydrukowanych danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-173">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="3a33e-174">Dostosowywanie nazw i wartości JSON</span><span class="sxs-lookup"><span data-stu-id="3a33e-174">Customize JSON names and values</span></span>

<span data-ttu-id="3a33e-175">Domyślnie nazwy właściwości i klucze słownika nie są zmieniane w danych wyjściowych JSON, włącznie z wielkością liter.</span><span class="sxs-lookup"><span data-stu-id="3a33e-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="3a33e-176">Wartości wyliczeniowe są reprezentowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="3a33e-176">Enum values are represented as numbers.</span></span> <span data-ttu-id="3a33e-177">W tej sekcji wyjaśniono, jak:</span><span class="sxs-lookup"><span data-stu-id="3a33e-177">This section explains how to:</span></span>

* [<span data-ttu-id="3a33e-178">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="3a33e-178">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="3a33e-179">Konwertuj wszystkie nazwy właściwości na notacji CamelCase przypadku</span><span class="sxs-lookup"><span data-stu-id="3a33e-179">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="3a33e-180">Implementowanie zasad nazewnictwa właściwości niestandardowych</span><span class="sxs-lookup"><span data-stu-id="3a33e-180">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="3a33e-181">Konwertuj klucze słownika na notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="3a33e-181">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="3a33e-182">Konwertuj wyliczenia na ciągi i notacji CamelCase wielkość liter</span><span class="sxs-lookup"><span data-stu-id="3a33e-182">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="3a33e-183">W przypadku innych scenariuszy, które wymagają specjalnej obsługi nazw i wartości właściwości JSON, można [zaimplementować konwertery niestandardowe](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="3a33e-183">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="3a33e-184">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="3a33e-184">Customize individual property names</span></span>

<span data-ttu-id="3a33e-185">Aby ustawić nazwę poszczególnych właściwości, Użyj atrybutu [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3a33e-185">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="3a33e-186">Oto przykład typu do serializacji i powstającego JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-186">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="3a33e-187">Nazwa właściwości ustawiona przez ten atrybut:</span><span class="sxs-lookup"><span data-stu-id="3a33e-187">The property name set by this attribute:</span></span>

* <span data-ttu-id="3a33e-188">Stosuje się w obu kierunkach dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-188">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="3a33e-189">Ma pierwszeństwo przed zasadami nazewnictwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="3a33e-189">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="3a33e-190">Użyj notacji CamelCase przypadku dla wszystkich nazw właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="3a33e-190">Use camel case for all JSON property names</span></span>

<span data-ttu-id="3a33e-191">Aby użyć notacji CamelCase przypadku wszystkich nazw właściwości JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` tak, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-191">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="3a33e-192">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-192">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="3a33e-193">Zasady nazewnictwa właściwości przypadku notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="3a33e-193">The camel case property naming policy:</span></span>

* <span data-ttu-id="3a33e-194">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-194">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="3a33e-195">Jest zastępowany przez `[JsonPropertyName]` atrybuty.</span><span class="sxs-lookup"><span data-stu-id="3a33e-195">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="3a33e-196">Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="3a33e-196">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="3a33e-197">Użyj niestandardowych zasad nazewnictwa właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="3a33e-197">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="3a33e-198">Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę, która pochodzi od <xref:System.Text.Json.JsonNamingPolicy> i przesłania <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> metodę, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-198">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="3a33e-199">Następnie ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> Właściwość na wystąpienie klasy zasad nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="3a33e-199">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-200">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-200">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="3a33e-201">Zasady nazewnictwa właściwości JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-201">The JSON property naming policy:</span></span>

* <span data-ttu-id="3a33e-202">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-202">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="3a33e-203">Jest zastępowany przez `[JsonPropertyName]` atrybuty.</span><span class="sxs-lookup"><span data-stu-id="3a33e-203">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="3a33e-204">Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest wielką literą.</span><span class="sxs-lookup"><span data-stu-id="3a33e-204">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="3a33e-205">Klucze słownika przypadku notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="3a33e-205">Camel case dictionary keys</span></span>

<span data-ttu-id="3a33e-206">Jeśli właściwość obiektu, który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>` , `string` klucze mogą być konwertowane na notacji CamelCase przypadku.</span><span class="sxs-lookup"><span data-stu-id="3a33e-206">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="3a33e-207">W tym celu ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase` , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-207">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-208">Serializacja obiektu ze słownikiem o nazwie `TemperatureRanges` , który ma pary klucz-wartość `"ColdMinTemp", 20` i `"HotMinTemp", 40` spowodowałaby wyjście JSON podobne do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="3a33e-208">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="3a33e-209">Zasady nazewnictwa przypadków notacji CamelCase dla kluczy słownika mają zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-209">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="3a33e-210">W przypadku deserializacji słownika klucze będą zgodne z plikiem JSON nawet w przypadku określenia `JsonNamingPolicy.CamelCase` dla `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-210">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="3a33e-211">Wyliczenia jako ciągi</span><span class="sxs-lookup"><span data-stu-id="3a33e-211">Enums as strings</span></span>

<span data-ttu-id="3a33e-212">Domyślnie wyliczenia są serializowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="3a33e-212">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="3a33e-213">Aby serializować nazwy wyliczenia jako ciągi, użyj <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="3a33e-213">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="3a33e-214">Załóżmy na przykład, że trzeba serializować następujące klasy, które mają Wyliczenie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-214">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="3a33e-215">Jeśli podsumowanie jest `Hot` , domyślnie serializowany kod JSON ma wartość liczbową 3:</span><span class="sxs-lookup"><span data-stu-id="3a33e-215">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="3a33e-216">Następujący przykładowy kod serializować nazwy wyliczenia zamiast wartości liczbowych i konwertuje nazwy na notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="3a33e-216">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-217">Wynikowy kod JSON wygląda podobnie do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="3a33e-217">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="3a33e-218">Można również deserializować nazwy ciągów wyliczenia, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-218">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="3a33e-219">Wyklucz właściwości z serializacji</span><span class="sxs-lookup"><span data-stu-id="3a33e-219">Exclude properties from serialization</span></span>

<span data-ttu-id="3a33e-220">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="3a33e-220">By default, all public properties are serialized.</span></span> <span data-ttu-id="3a33e-221">Jeśli nie chcesz, aby niektóre z nich pojawiały się w danych wyjściowych JSON, masz kilka opcji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-221">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="3a33e-222">W tej sekcji wyjaśniono, jak wykluczyć:</span><span class="sxs-lookup"><span data-stu-id="3a33e-222">This section explains how to exclude:</span></span>

* [<span data-ttu-id="3a33e-223">Poszczególne właściwości</span><span class="sxs-lookup"><span data-stu-id="3a33e-223">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="3a33e-224">Wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3a33e-224">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="3a33e-225">Wszystkie właściwości o wartości null</span><span class="sxs-lookup"><span data-stu-id="3a33e-225">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="3a33e-226">Wyklucz pojedyncze właściwości</span><span class="sxs-lookup"><span data-stu-id="3a33e-226">Exclude individual properties</span></span>

<span data-ttu-id="3a33e-227">Aby zignorować poszczególne właściwości, Użyj atrybutu [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="3a33e-227">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="3a33e-228">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="3a33e-229">Wyklucz wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3a33e-229">Exclude all read-only properties</span></span>

<span data-ttu-id="3a33e-230">Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="3a33e-230">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="3a33e-231">Aby wykluczyć wszystkie właściwości tylko do odczytu, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true` , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-231">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-232">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-232">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="3a33e-233">Ta opcja ma zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-233">This option applies only to serialization.</span></span> <span data-ttu-id="3a33e-234">Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="3a33e-234">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="3a33e-235">Wyklucz wszystkie właściwości wartości null</span><span class="sxs-lookup"><span data-stu-id="3a33e-235">Exclude all null value properties</span></span>

<span data-ttu-id="3a33e-236">Aby wykluczyć wszystkie właściwości wartości null, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> Właściwość na `true` , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-236">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-237">Oto przykład obiektu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-237">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="3a33e-238">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3a33e-238">Property</span></span> |<span data-ttu-id="3a33e-239">Wartość</span><span class="sxs-lookup"><span data-stu-id="3a33e-239">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="3a33e-240">Date</span><span class="sxs-lookup"><span data-stu-id="3a33e-240">Date</span></span>    | <span data-ttu-id="3a33e-241">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="3a33e-241">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="3a33e-242">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="3a33e-242">TemperatureCelsius</span></span>| <span data-ttu-id="3a33e-243">25</span><span class="sxs-lookup"><span data-stu-id="3a33e-243">25</span></span> |
| <span data-ttu-id="3a33e-244">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="3a33e-244">Summary</span></span>| <span data-ttu-id="3a33e-245">wartość null</span><span class="sxs-lookup"><span data-stu-id="3a33e-245">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="3a33e-246">To ustawienie dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-246">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="3a33e-247">Aby uzyskać informacje o jego wpływie na deserializacji, zobacz [Ignore null podczas deserializacji](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="3a33e-247">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="3a33e-248">Dostosuj kodowanie znaków</span><span class="sxs-lookup"><span data-stu-id="3a33e-248">Customize character encoding</span></span>

<span data-ttu-id="3a33e-249">Domyślnie serializator wyprowadza wszystkie znaki nienależące do zestawu znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="3a33e-249">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="3a33e-250">Oznacza to, że zastępuje je, `\uxxxx` gdzie `xxxx` jest kodem Unicode znaku.</span><span class="sxs-lookup"><span data-stu-id="3a33e-250">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="3a33e-251">Na przykład, jeśli `Summary` Właściwość jest ustawiona na wartość cyrylicy жарко, `WeatherForecast` obiekt jest serializowany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-251">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="3a33e-252">Serializowanie zestawów znaków języka</span><span class="sxs-lookup"><span data-stu-id="3a33e-252">Serialize language character sets</span></span>

<span data-ttu-id="3a33e-253">Aby serializować zestawy znaków z co najmniej jednego języka bez ucieczki, określ [zakresy Unicode](xref:System.Text.Unicode.UnicodeRanges) podczas tworzenia wystąpienia <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-253">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="3a33e-254">Ten kod nie ma ucieczki znaków cyrylicy lub greckich.</span><span class="sxs-lookup"><span data-stu-id="3a33e-254">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="3a33e-255">Jeśli `Summary` Właściwość jest ustawiona na wartość cyrylicy жарко, `WeatherForecast` obiekt jest serializowany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-255">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="3a33e-256">Aby serializować wszystkie zestawy językowe bez ucieczki, użyj <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3a33e-256">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="3a33e-257">Serializacja określonych znaków</span><span class="sxs-lookup"><span data-stu-id="3a33e-257">Serialize specific characters</span></span>

<span data-ttu-id="3a33e-258">Alternatywą jest określenie pojedynczych znaków, które mają być dozwolone, bez konieczności ucieczki.</span><span class="sxs-lookup"><span data-stu-id="3a33e-258">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="3a33e-259">Poniższy przykład serializacji tylko dwa pierwsze znaki жарко:</span><span class="sxs-lookup"><span data-stu-id="3a33e-259">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="3a33e-260">Oto przykład kodu JSON utworzonego przez poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="3a33e-260">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="3a33e-261">Serializować wszystkie znaki</span><span class="sxs-lookup"><span data-stu-id="3a33e-261">Serialize all characters</span></span>

<span data-ttu-id="3a33e-262">Aby zminimalizować liczbę ucieczki, można użyć <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-262">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="3a33e-263">W porównaniu z domyślnym koderem `UnsafeRelaxedJsonEscaping` koder jest bardziej ograniczając, aby umożliwić przekazywanie znaków przez niezmieniony:</span><span class="sxs-lookup"><span data-stu-id="3a33e-263">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="3a33e-264">Nie ucieczk znaków w języku HTML, takich jak `<` , `>` , `&` , i `'` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-264">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="3a33e-265">Nie oferuje żadnej dodatkowej ochrony przed atakami na ataki typu XSS lub ujawnienie informacji, takich jak te, które mogą wynikać z klienta i serwera bez zgody na *zestaw znaków*.</span><span class="sxs-lookup"><span data-stu-id="3a33e-265">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="3a33e-266">Używaj niebezpiecznego kodera tylko wtedy, gdy wiadomo, że klient będzie interpretować otrzymany ładunek jako zakodowany w formacie JSON UTF-8.</span><span class="sxs-lookup"><span data-stu-id="3a33e-266">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="3a33e-267">Można na przykład użyć go, jeśli serwer wysyła nagłówek odpowiedzi `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-267">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="3a33e-268">Nigdy nie Zezwalaj na `UnsafeRelaxedJsonEscaping` emitowanie nieprzetworzonych danych wyjściowych do strony HTML lub `<script>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3a33e-268">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="3a33e-269">Serializowanie właściwości klas pochodnych</span><span class="sxs-lookup"><span data-stu-id="3a33e-269">Serialize properties of derived classes</span></span>

<span data-ttu-id="3a33e-270">Serializacja hierarchii typów polimorficznych nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="3a33e-270">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="3a33e-271">Na przykład, jeśli właściwość jest zdefiniowana jako interfejs lub Klasa abstrakcyjna, tylko właściwości zdefiniowane w interfejsie lub klasie abstrakcyjnej są serializowane, nawet jeśli typ środowiska uruchomieniowego ma dodatkowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="3a33e-271">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="3a33e-272">Wyjątki dotyczące tego zachowania zostały omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-272">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="3a33e-273">Załóżmy na przykład, że masz `WeatherForecast` klasę i klasę pochodną `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="3a33e-274">I Załóżmy, że argument typu `Serialize` metody w czasie kompilacji to `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="3a33e-275">W tym scenariuszu `WindSpeed` Właściwość nie jest serializowana, nawet jeśli `weatherForecast` obiekt jest rzeczywiście `WeatherForecastDerived` obiektem.</span><span class="sxs-lookup"><span data-stu-id="3a33e-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="3a33e-276">Tylko właściwości klasy bazowej są serializowane:</span><span class="sxs-lookup"><span data-stu-id="3a33e-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="3a33e-277">Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="3a33e-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="3a33e-278">Aby serializować właściwości typu pochodnego w poprzednim przykładzie, należy użyć jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="3a33e-278">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="3a33e-279">Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A> , które pozwala określić typ w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="3a33e-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="3a33e-280">Zadeklaruj obiekt, który ma zostać Zserializowany jako `object` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-280">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="3a33e-281">W poprzednim przykładowym scenariuszu oba podejścia powodują, że `WindSpeed` Właściwość powinna zostać uwzględniona w danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="3a33e-282">Te podejścia zapewniają serializację polimorficzne tylko dla obiektu głównego, który ma być serializowany, a nie dla właściwości tego obiektu głównego.</span><span class="sxs-lookup"><span data-stu-id="3a33e-282">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="3a33e-283">Można uzyskać serializację polimorficzny dla obiektów niższego poziomu, jeśli zdefiniujesz je jako typ `object` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-283">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="3a33e-284">Na przykład załóżmy, `WeatherForecast` że Klasa ma właściwość o nazwie `PreviousForecast` , która może być zdefiniowana jako typ `WeatherForecast` lub `object` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-284">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="3a33e-285">Jeśli `PreviousForecast` Właściwość zawiera wystąpienie `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-285">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="3a33e-286">Dane wyjściowe JSON z serializacji `WeatherForecastWithPrevious` **nie obejmują** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-286">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="3a33e-287">Dane wyjściowe JSON z serializacji `WeatherForecastWithPreviousAsObject` **obejmują** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-287">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="3a33e-288">Aby serializować `WeatherForecastWithPreviousAsObject` , nie jest konieczne wywołanie `Serialize<object>` lub `GetType` ponieważ obiekt główny nie jest tym, który może znajdować się w typie pochodnym.</span><span class="sxs-lookup"><span data-stu-id="3a33e-288">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="3a33e-289">Poniższy przykład kodu nie wywołuje `Serialize<object>` lub `GetType` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-289">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="3a33e-290">Powyższy kod poprawnie serializować `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-290">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="3a33e-291">To samo podejście do definiowania właściwości jako `object` współdziałanie z interfejsami.</span><span class="sxs-lookup"><span data-stu-id="3a33e-291">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="3a33e-292">Załóżmy, że masz następujący interfejs i implementacja, i chcesz serializować klasę o właściwościach zawierających wystąpienia implementacji:</span><span class="sxs-lookup"><span data-stu-id="3a33e-292">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="3a33e-293">Podczas serializacji wystąpienia elementu `Forecasts` , `Tuesday` wyświetlana `WindSpeed` jest tylko właściwość, ponieważ `Tuesday` jest zdefiniowana jako `object` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-293">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="3a33e-294">Poniższy przykład pokazuje kod JSON, który wynika z poprzedniego kodu:</span><span class="sxs-lookup"><span data-stu-id="3a33e-294">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="3a33e-295">Aby uzyskać więcej informacji na temat **serializacji**polimorficznej i informacje o **deserializacji**, zobacz [Migrowanie z Newtonsoft. JSON do System. Text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="3a33e-295">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="3a33e-296">Zezwalaj na komentarze i końcowe przecinki</span><span class="sxs-lookup"><span data-stu-id="3a33e-296">Allow comments and trailing commas</span></span>

<span data-ttu-id="3a33e-297">Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON.</span><span class="sxs-lookup"><span data-stu-id="3a33e-297">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="3a33e-298">Aby zezwolić na komentarze w formacie JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> Właściwość na `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-298">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="3a33e-299">I aby zezwolić na końcowe przecinki, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> Właściwość na `true` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-299">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="3a33e-300">Poniższy przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="3a33e-300">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="3a33e-301">Oto przykładowy kod JSON z komentarzami i końcowym przecinkiem:</span><span class="sxs-lookup"><span data-stu-id="3a33e-301">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="3a33e-302">Dopasowanie właściwości bez uwzględniania wielkości liter</span><span class="sxs-lookup"><span data-stu-id="3a33e-302">Case-insensitive property matching</span></span>

<span data-ttu-id="3a33e-303">Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3a33e-303">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="3a33e-304">Aby zmienić to zachowanie, ustaw opcję <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-304">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="3a33e-305">Oto przykład JSON z nazwami właściwości przypadku notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="3a33e-305">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="3a33e-306">Można ją zdeserializować do następującego typu, który ma nazwy właściwości przypadku języka Pascal.</span><span class="sxs-lookup"><span data-stu-id="3a33e-306">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="3a33e-307">Obsługa przepełnienia kodu JSON</span><span class="sxs-lookup"><span data-stu-id="3a33e-307">Handle overflow JSON</span></span>

<span data-ttu-id="3a33e-308">Podczas deserializacji można odbierać dane w formacie JSON, które nie są reprezentowane przez właściwości typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="3a33e-308">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="3a33e-309">Załóżmy na przykład, że typ docelowy to:</span><span class="sxs-lookup"><span data-stu-id="3a33e-309">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="3a33e-310">I kod JSON do deserializacji jest następujący:</span><span class="sxs-lookup"><span data-stu-id="3a33e-310">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="3a33e-311">W przypadku deserializacji kodu JSON pokazanego w pokazanym typie, `DatesAvailable` `SummaryWords` właściwości i mają wartość Nowhere to go i są tracone.</span><span class="sxs-lookup"><span data-stu-id="3a33e-311">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="3a33e-312">Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="3a33e-312">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="3a33e-313">Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie próbkowania dodatkowe dane staną się parami klucz-wartość `ExtensionData` Właściwości:</span><span class="sxs-lookup"><span data-stu-id="3a33e-313">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="3a33e-314">Właściwość</span><span class="sxs-lookup"><span data-stu-id="3a33e-314">Property</span></span> |<span data-ttu-id="3a33e-315">Wartość</span><span class="sxs-lookup"><span data-stu-id="3a33e-315">Value</span></span>  |<span data-ttu-id="3a33e-316">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a33e-316">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="3a33e-317">Date</span><span class="sxs-lookup"><span data-stu-id="3a33e-317">Date</span></span>    | <span data-ttu-id="3a33e-318">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="3a33e-318">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="3a33e-319">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="3a33e-319">TemperatureCelsius</span></span>| <span data-ttu-id="3a33e-320">0</span><span class="sxs-lookup"><span data-stu-id="3a33e-320">0</span></span> | <span data-ttu-id="3a33e-321">Niezgodność z rozróżnianiem wielkości liter ( `temperatureCelsius` w formacie JSON), więc właściwość nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="3a33e-321">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="3a33e-322">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="3a33e-322">Summary</span></span> | <span data-ttu-id="3a33e-323">Gorąca</span><span class="sxs-lookup"><span data-stu-id="3a33e-323">Hot</span></span> ||
| <span data-ttu-id="3a33e-324">ExtensionData —</span><span class="sxs-lookup"><span data-stu-id="3a33e-324">ExtensionData</span></span> | <span data-ttu-id="3a33e-325">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="3a33e-325">temperatureCelsius: 25</span></span> |<span data-ttu-id="3a33e-326">Ponieważ przypadek nie jest zgodny, ta właściwość JSON jest dodatkową i jest parą klucz-wartość w słowniku.</span><span class="sxs-lookup"><span data-stu-id="3a33e-326">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="3a33e-327">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="3a33e-327">DatesAvailable:</span></span><br>  <span data-ttu-id="3a33e-328">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="3a33e-328">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="3a33e-329">8/2/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="3a33e-329">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="3a33e-330">Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="3a33e-330">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="3a33e-331">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="3a33e-331">SummaryWords:</span></span><br><span data-ttu-id="3a33e-332">Chłodna</span><span class="sxs-lookup"><span data-stu-id="3a33e-332">Cool</span></span><br><span data-ttu-id="3a33e-333">Wiatr</span><span class="sxs-lookup"><span data-stu-id="3a33e-333">Windy</span></span><br><span data-ttu-id="3a33e-334">Humid</span><span class="sxs-lookup"><span data-stu-id="3a33e-334">Humid</span></span> |<span data-ttu-id="3a33e-335">Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="3a33e-335">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="3a33e-336">Gdy obiekt docelowy jest serializowany, pary wartości klucza danych rozszerzenia stają się właściwościami JSON tak samo jak w przychodzących danych JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-336">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="3a33e-337">Zauważ, że `ExtensionData` Nazwa właściwości nie pojawia się w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="3a33e-337">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="3a33e-338">Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.</span><span class="sxs-lookup"><span data-stu-id="3a33e-338">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="3a33e-339">Ignoruj wartość null podczas deserializacji</span><span class="sxs-lookup"><span data-stu-id="3a33e-339">Ignore null when deserializing</span></span>

<span data-ttu-id="3a33e-340">Domyślnie, jeśli właściwość w formacie JSON ma wartość null, odpowiadająca jej właściwość w obiekcie docelowym ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="3a33e-340">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="3a33e-341">W niektórych scenariuszach właściwość target może mieć wartość domyślną i nie ma potrzeby przesłonięcia wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="3a33e-341">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="3a33e-342">Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:</span><span class="sxs-lookup"><span data-stu-id="3a33e-342">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="3a33e-343">Załóżmy, że następujący kod JSON jest deserializowany:</span><span class="sxs-lookup"><span data-stu-id="3a33e-343">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="3a33e-344">Po deserializacji `Summary` Właściwość `WeatherForecastWithDefault` obiektu ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="3a33e-344">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="3a33e-345">Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> wartość `true` tak, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-345">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="3a33e-346">W przypadku tej opcji `Summary` Właściwość `WeatherForecastWithDefault` obiektu jest wartością domyślną "Brak podsumowania" po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-346">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="3a33e-347">Wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="3a33e-347">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="3a33e-348">Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki.</span><span class="sxs-lookup"><span data-stu-id="3a33e-348">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="3a33e-349">Utf8JsonReader, Utf8JsonWriter i JsonDocument</span><span class="sxs-lookup"><span data-stu-id="3a33e-349">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="3a33e-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>jest wysoką wydajnością, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, Odczytaj z `ReadOnlySpan<byte>` lub `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="3a33e-351">`Utf8JsonReader`Jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-351">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="3a33e-352"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>Metoda używa `Utf8JsonReader` w obszarze okładki.</span><span class="sxs-lookup"><span data-stu-id="3a33e-352">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="3a33e-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>jest wysoce wydajnym sposobem pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy .NET, takich jak `String` , `Int32` , i `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="3a33e-354">Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3a33e-354">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="3a33e-355"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>Metoda używa `Utf8JsonWriter` w obszarze okładki.</span><span class="sxs-lookup"><span data-stu-id="3a33e-355">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="3a33e-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>zapewnia możliwość tworzenia Document Object Model tylko do odczytu (DOM) za pomocą programu `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="3a33e-357">DOM zapewnia losowy dostęp do danych w ładunku JSON.</span><span class="sxs-lookup"><span data-stu-id="3a33e-357">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="3a33e-358">Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typu.</span><span class="sxs-lookup"><span data-stu-id="3a33e-358">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="3a33e-359">`JsonElement`Typ udostępnia moduł wyliczający tablic i obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET.</span><span class="sxs-lookup"><span data-stu-id="3a33e-359">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="3a33e-360">`JsonDocument`uwidacznia <xref:System.Text.Json.JsonDocument.RootElement> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="3a33e-360">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="3a33e-361">W poniższych sekcjach pokazano, jak używać tych narzędzi do odczytywania i pisania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="3a33e-361">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="3a33e-362">Korzystanie z JsonDocument do uzyskiwania dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="3a33e-362">Use JsonDocument for access to data</span></span>

<span data-ttu-id="3a33e-363">Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.JsonDocument> klasy do losowego dostępu do danych w ciągu JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-363">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="3a33e-364">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-364">The preceding code:</span></span>

* <span data-ttu-id="3a33e-365">Przyjęto, że kod JSON do analizy jest w ciągu o nazwie `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="3a33e-365">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="3a33e-366">Oblicza średnią ocenę dla obiektów w `Students` tablicy, która ma `Grade` Właściwość.</span><span class="sxs-lookup"><span data-stu-id="3a33e-366">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="3a33e-367">Przypisuje domyślną ocenę 70 dla studentów, którzy nie posiadają klasy.</span><span class="sxs-lookup"><span data-stu-id="3a33e-367">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="3a33e-368">Zlicza uczniów przez zwiększenie `count` zmiennej przy każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="3a33e-368">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="3a33e-369">Alternatywą jest wywołanie <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-369">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="3a33e-370">Oto przykład pliku JSON, który jest przetwarzany przez ten kod:</span><span class="sxs-lookup"><span data-stu-id="3a33e-370">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="3a33e-371">Użyj JsonDocument, aby zapisać kod JSON</span><span class="sxs-lookup"><span data-stu-id="3a33e-371">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="3a33e-372">Poniższy przykład pokazuje, jak napisać kod JSON z <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="3a33e-372">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="3a33e-373">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-373">The preceding code:</span></span>

* <span data-ttu-id="3a33e-374">Odczytuje plik JSON, ładuje dane do `JsonDocument` i zapisuje sformatowany plik JSON w formacie.</span><span class="sxs-lookup"><span data-stu-id="3a33e-374">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="3a33e-375">Używa <xref:System.Text.Json.JsonDocumentOptions> do określenia, czy komentarze w wejściowym formacie JSON są dozwolone, ale ignorowane.</span><span class="sxs-lookup"><span data-stu-id="3a33e-375">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="3a33e-376">Po zakończeniu wywołania <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> na składniku zapisywania.</span><span class="sxs-lookup"><span data-stu-id="3a33e-376">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="3a33e-377">Alternatywą jest umożliwienie składnika zapisywania AutoFlush, gdy zostanie on usunięty.</span><span class="sxs-lookup"><span data-stu-id="3a33e-377">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="3a33e-378">Oto przykład danych wejściowych JSON do przetworzenia przez przykładowy kod:</span><span class="sxs-lookup"><span data-stu-id="3a33e-378">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="3a33e-379">Wynikiem są następujące niedrukowane dane wyjściowe JSON:</span><span class="sxs-lookup"><span data-stu-id="3a33e-379">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="3a33e-380">Użyj Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="3a33e-380">Use Utf8JsonWriter</span></span>

<span data-ttu-id="3a33e-381">Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.Utf8JsonWriter> klasy:</span><span class="sxs-lookup"><span data-stu-id="3a33e-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="3a33e-382">Użyj Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="3a33e-382">Use Utf8JsonReader</span></span>

<span data-ttu-id="3a33e-383">Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.Utf8JsonReader> klasy:</span><span class="sxs-lookup"><span data-stu-id="3a33e-383">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="3a33e-384">Poprzedni kod założono, że `jsonUtf8` zmienna jest tablicą bajtową, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="3a33e-384">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="3a33e-385">Filtrowanie danych za pomocą Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="3a33e-385">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="3a33e-386">Poniższy przykład pokazuje, jak odczytywać plik synchronicznie i wyszukiwać wartość:</span><span class="sxs-lookup"><span data-stu-id="3a33e-386">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="3a33e-387">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="3a33e-387">The preceding code:</span></span>

* <span data-ttu-id="3a33e-388">Przyjęto, że kod JSON zawiera tablicę obiektów, a każdy obiekt może zawierać właściwość "name" typu String.</span><span class="sxs-lookup"><span data-stu-id="3a33e-388">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="3a33e-389">Zlicza obiekty i wartości właściwości "name", które kończą się znakiem "University".</span><span class="sxs-lookup"><span data-stu-id="3a33e-389">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="3a33e-390">Przyjęto założenie, że plik jest zakodowany jako UTF-16 i transkoduje go do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="3a33e-390">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="3a33e-391">Plik zakodowany jako UTF-8 może być odczytywany bezpośrednio do programu `ReadOnlySpan<byte>` , przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="3a33e-391">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="3a33e-392">Jeśli plik zawiera znacznik kolejności bajtów UTF-8, usuń go przed przekazaniem bajtów do `Utf8JsonReader` , ponieważ czytnik oczekuje tekstu.</span><span class="sxs-lookup"><span data-stu-id="3a33e-392">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="3a33e-393">W przeciwnym razie BOM jest traktowany jako nieprawidłowy kod JSON, a czytelnik zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="3a33e-393">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="3a33e-394">Oto przykład JSON, który może odczytać poprzedzający kod.</span><span class="sxs-lookup"><span data-stu-id="3a33e-394">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="3a33e-395">Otrzymany komunikat podsumowujący to "2 z 4 mają nazwy kończące się na" University ":</span><span class="sxs-lookup"><span data-stu-id="3a33e-395">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="3a33e-396">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="3a33e-396">Additional resources</span></span>

* <span data-ttu-id="3a33e-397">[System.Text.JsonPodsumowanie](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="3a33e-397">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="3a33e-398">Jak pisać konwertery niestandardowe</span><span class="sxs-lookup"><span data-stu-id="3a33e-398">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="3a33e-399">[Jak przeprowadzić migrację zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="3a33e-399">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="3a33e-400">[Obsługa DateTime i DateTimeOffset wSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="3a33e-400">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="3a33e-401">[System.Text.JsonDokumentacja interfejsu API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="3a33e-401">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
