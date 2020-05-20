---
title: ''
description: W tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET. Zawiera przykładowy kod.
ms.date: ''
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords: []
ms.openlocfilehash: f1a5da448b08f9b4f1cf3fa6cba67fb376b00a6f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702272"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="d70d6-103">Jak serializować i deserializować (Marshaling and unmarshaling) JSON w programie .NET</span><span class="sxs-lookup"><span data-stu-id="d70d6-103">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="d70d6-104">W tym artykule pokazano, jak używać <xref:System.Text.Json> przestrzeni nazw do serializacji i deserializacji do i z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="d70d6-104">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="d70d6-105">W przypadku przenoszenia istniejącego kodu z programu `Newtonsoft.Json` zapoznaj się z tematem [jak `System.Text.Json` przeprowadzić migrację do programu ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="d70d6-105">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="d70d6-106">Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="d70d6-106">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="d70d6-107">Większość przykładowych kodów serializacji <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> do `true` "DB-Print" w formacie JSON (z wcięciem i białym znakiem).</span><span class="sxs-lookup"><span data-stu-id="d70d6-107">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="d70d6-108">Do użycia w środowisku produkcyjnym zwykle przyjmuje się wartość domyślną `false` dla tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="d70d6-108">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="d70d6-109">Przykłady kodu odnoszą się do następującej klasy i wariantów:</span><span class="sxs-lookup"><span data-stu-id="d70d6-109">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="d70d6-110">Przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="d70d6-110">Namespaces</span></span>

<span data-ttu-id="d70d6-111"><xref:System.Text.Json>Przestrzeń nazw zawiera wszystkie punkty wejścia i typy główne.</span><span class="sxs-lookup"><span data-stu-id="d70d6-111">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="d70d6-112"><xref:System.Text.Json.Serialization>Przestrzeń nazw zawiera atrybuty i interfejsy API dla zaawansowanych scenariuszy i dostosowań specyficznych dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-112">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="d70d6-113">Przykłady kodu przedstawione w tym artykule wymagają `using` dyrektyw dla jednej lub obu tych przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="d70d6-113">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="d70d6-114">Atrybuty z <xref:System.Runtime.Serialization> przestrzeni nazw nie są obecnie obsługiwane w programie `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-114">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="d70d6-115">Pisanie obiektów .NET w formacie JSON (Serializacja)</span><span class="sxs-lookup"><span data-stu-id="d70d6-115">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="d70d6-116">Aby zapisać dane JSON do ciągu lub do pliku, wywołaj <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="d70d6-116">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d70d6-117">Poniższy przykład tworzy kod JSON jako ciąg:</span><span class="sxs-lookup"><span data-stu-id="d70d6-117">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-118">Poniższy przykład używa kodu synchronicznego do utworzenia pliku JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-118">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-119">W poniższym przykładzie jest tworzony plik JSON przy użyciu kodu asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="d70d6-119">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-120">Powyższe przykłady używają wnioskowania typu dla serializowanego typu.</span><span class="sxs-lookup"><span data-stu-id="d70d6-120">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="d70d6-121">Przeciążenie `Serialize()` przyjmuje parametr typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="d70d6-121">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="d70d6-122">Przykład serializacji</span><span class="sxs-lookup"><span data-stu-id="d70d6-122">Serialization example</span></span>

<span data-ttu-id="d70d6-123">Oto przykładowa Klasa, która zawiera kolekcje i zagnieżdżoną klasę:</span><span class="sxs-lookup"><span data-stu-id="d70d6-123">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="d70d6-124">Dane wyjściowe JSON serializowania wystąpienia poprzedniego typu wyglądają podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d70d6-124">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="d70d6-125">Dane wyjściowe JSON domyślnie są zminimalizowanego:</span><span class="sxs-lookup"><span data-stu-id="d70d6-125">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="d70d6-126">W poniższym przykładzie przedstawiono ten sam kod JSON, sformatowany (to jest całkiem wydruk z odstępami i wcięciami):</span><span class="sxs-lookup"><span data-stu-id="d70d6-126">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="d70d6-127">Serializacja do UTF-8</span><span class="sxs-lookup"><span data-stu-id="d70d6-127">Serialize to UTF-8</span></span>

<span data-ttu-id="d70d6-128">Aby serializować do UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> metodę:</span><span class="sxs-lookup"><span data-stu-id="d70d6-128">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-129"><xref:System.Text.Json.JsonSerializer.Serialize%2A>Dostępne jest również Przeciążenie, które trwa <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="d70d6-129">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="d70d6-130">Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach.</span><span class="sxs-lookup"><span data-stu-id="d70d6-130">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="d70d6-131">Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="d70d6-131">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="d70d6-132">Zachowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="d70d6-132">Serialization behavior</span></span>

* <span data-ttu-id="d70d6-133">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="d70d6-133">By default, all public properties are serialized.</span></span> <span data-ttu-id="d70d6-134">Można [określić właściwości do wykluczenia](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="d70d6-134">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="d70d6-135">[Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem języka HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="d70d6-135">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="d70d6-136">Domyślnie JSON jest zminimalizowanego.</span><span class="sxs-lookup"><span data-stu-id="d70d6-136">By default, JSON is minified.</span></span> <span data-ttu-id="d70d6-137">Można tu [wydrukować kod JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="d70d6-137">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="d70d6-138">Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-138">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="d70d6-139">Można [dostosować wielkość liter w nazwach JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="d70d6-139">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="d70d6-140">Wykryto odwołania cykliczne i zostały zgłoszone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="d70d6-140">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="d70d6-141">Obecnie pola są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="d70d6-141">Currently, fields are excluded.</span></span>

<span data-ttu-id="d70d6-142">Obsługiwane typy to:</span><span class="sxs-lookup"><span data-stu-id="d70d6-142">Supported types include:</span></span>

* <span data-ttu-id="d70d6-143">Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="d70d6-143">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="d70d6-144">Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="d70d6-144">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="d70d6-145">Tablice jednowymiarowe i nieregularne ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="d70d6-145">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="d70d6-146">`Dictionary<string,TValue>`gdzie `TValue` is to `object` , `JsonElement` lub poco.</span><span class="sxs-lookup"><span data-stu-id="d70d6-146">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="d70d6-147">Kolekcje z następujących przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d70d6-147">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="d70d6-148">Można [zaimplementować niestandardowe konwertery](system-text-json-converters-how-to.md) w celu obsługi dodatkowych typów lub zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="d70d6-148">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="d70d6-149">Jak odczytywać dane JSON do obiektów .NET (deserializacji)</span><span class="sxs-lookup"><span data-stu-id="d70d6-149">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="d70d6-150">Aby zdeserializować z ciągu lub pliku, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="d70d6-150">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="d70d6-151">Poniższy przykład odczytuje dane JSON z ciągu i tworzy wystąpienie `WeatherForecast` klasy pokazanej wcześniej dla [przykładu serializacji](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="d70d6-151">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="d70d6-152">Aby zdeserializować z pliku przy użyciu kodu synchronicznego, Odczytaj plik do ciągu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-152">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="d70d6-153">Aby zdeserializować z pliku przy użyciu kodu asynchronicznego, wywołaj <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> metodę:</span><span class="sxs-lookup"><span data-stu-id="d70d6-153">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="d70d6-154">Deserializacja z UTF-8</span><span class="sxs-lookup"><span data-stu-id="d70d6-154">Deserialize from UTF-8</span></span>

<span data-ttu-id="d70d6-155">Aby zdeserializować z UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Przeciążenie, które pobiera `Utf8JsonReader` lub a `ReadOnlySpan<byte>` , jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="d70d6-155">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="d70d6-156">W przykładach założono, że kod JSON znajduje się w tablicy bajtów o nazwie jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="d70d6-156">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="d70d6-157">Zachowanie deserializacji</span><span class="sxs-lookup"><span data-stu-id="d70d6-157">Deserialization behavior</span></span>

* <span data-ttu-id="d70d6-158">Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="d70d6-158">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="d70d6-159">Można [określić wielkość liter](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="d70d6-159">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="d70d6-160">Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d70d6-160">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="d70d6-161">Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="d70d6-161">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="d70d6-162">Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="d70d6-162">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="d70d6-163">Domyślnie wyliczenia są obsługiwane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="d70d6-163">By default, enums are supported as numbers.</span></span> <span data-ttu-id="d70d6-164">[Nazwy wyliczenia można serializować jako ciągi](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="d70d6-164">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="d70d6-165">Pola nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d70d6-165">Fields aren't supported.</span></span>
* <span data-ttu-id="d70d6-166">Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-166">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="d70d6-167">Można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="d70d6-167">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="d70d6-168">[Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.</span><span class="sxs-lookup"><span data-stu-id="d70d6-168">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="d70d6-169">[Konwertery niestandardowe można zaimplementować](system-text-json-converters-how-to.md) w celu zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="d70d6-169">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="d70d6-170">Serializacja do sformatowanego pliku JSON</span><span class="sxs-lookup"><span data-stu-id="d70d6-170">Serialize to formatted JSON</span></span>

<span data-ttu-id="d70d6-171">Aby całkiem wydrukować dane wyjściowe JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-171">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="d70d6-172">Oto przykład typu do serializacji i całkiem wydrukowanych danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-172">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="d70d6-173">Dostosowywanie nazw i wartości JSON</span><span class="sxs-lookup"><span data-stu-id="d70d6-173">Customize JSON names and values</span></span>

<span data-ttu-id="d70d6-174">Domyślnie nazwy właściwości i klucze słownika nie są zmieniane w danych wyjściowych JSON, włącznie z wielkością liter.</span><span class="sxs-lookup"><span data-stu-id="d70d6-174">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="d70d6-175">Wartości wyliczeniowe są reprezentowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="d70d6-175">Enum values are represented as numbers.</span></span> <span data-ttu-id="d70d6-176">W tej sekcji wyjaśniono, jak:</span><span class="sxs-lookup"><span data-stu-id="d70d6-176">This section explains how to:</span></span>

* [<span data-ttu-id="d70d6-177">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="d70d6-177">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="d70d6-178">Konwertuj wszystkie nazwy właściwości na notacji CamelCase przypadku</span><span class="sxs-lookup"><span data-stu-id="d70d6-178">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="d70d6-179">Implementowanie zasad nazewnictwa właściwości niestandardowych</span><span class="sxs-lookup"><span data-stu-id="d70d6-179">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="d70d6-180">Konwertuj klucze słownika na notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="d70d6-180">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="d70d6-181">Konwertuj wyliczenia na ciągi i notacji CamelCase wielkość liter</span><span class="sxs-lookup"><span data-stu-id="d70d6-181">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="d70d6-182">W przypadku innych scenariuszy, które wymagają specjalnej obsługi nazw i wartości właściwości JSON, można [zaimplementować konwertery niestandardowe](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="d70d6-182">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="d70d6-183">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="d70d6-183">Customize individual property names</span></span>

<span data-ttu-id="d70d6-184">Aby ustawić nazwę poszczególnych właściwości, Użyj atrybutu [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="d70d6-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="d70d6-185">Oto przykład typu do serializacji i powstającego JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-185">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="d70d6-186">Nazwa właściwości ustawiona przez ten atrybut:</span><span class="sxs-lookup"><span data-stu-id="d70d6-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="d70d6-187">Stosuje się w obu kierunkach dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="d70d6-188">Ma pierwszeństwo przed zasadami nazewnictwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="d70d6-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="d70d6-189">Użyj notacji CamelCase przypadku dla wszystkich nazw właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="d70d6-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="d70d6-190">Aby użyć notacji CamelCase przypadku wszystkich nazw właściwości JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` tak, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="d70d6-191">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-191">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="d70d6-192">Zasady nazewnictwa właściwości przypadku notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="d70d6-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="d70d6-193">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="d70d6-194">Jest zastępowany przez `[JsonPropertyName]` atrybuty.</span><span class="sxs-lookup"><span data-stu-id="d70d6-194">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="d70d6-195">Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="d70d6-195">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="d70d6-196">Użyj niestandardowych zasad nazewnictwa właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="d70d6-196">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="d70d6-197">Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę, która pochodzi od <xref:System.Text.Json.JsonNamingPolicy> i przesłania <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> metodę, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-197">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="d70d6-198">Następnie ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> Właściwość na wystąpienie klasy zasad nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="d70d6-198">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-199">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-199">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="d70d6-200">Zasady nazewnictwa właściwości JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-200">The JSON property naming policy:</span></span>

* <span data-ttu-id="d70d6-201">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-201">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="d70d6-202">Jest zastępowany przez `[JsonPropertyName]` atrybuty.</span><span class="sxs-lookup"><span data-stu-id="d70d6-202">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="d70d6-203">Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest wielką literą.</span><span class="sxs-lookup"><span data-stu-id="d70d6-203">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="d70d6-204">Klucze słownika przypadku notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="d70d6-204">Camel case dictionary keys</span></span>

<span data-ttu-id="d70d6-205">Jeśli właściwość obiektu, który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>` , `string` klucze mogą być konwertowane na notacji CamelCase przypadku.</span><span class="sxs-lookup"><span data-stu-id="d70d6-205">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="d70d6-206">W tym celu ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase` , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-206">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-207">Serializacja obiektu ze słownikiem o nazwie `TemperatureRanges` , który ma pary klucz-wartość `"ColdMinTemp", 20` i `"HotMinTemp", 40` spowodowałaby wyjście JSON podobne do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="d70d6-207">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="d70d6-208">Zasady nazewnictwa przypadków notacji CamelCase dla kluczy słownika mają zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-208">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="d70d6-209">W przypadku deserializacji słownika klucze będą zgodne z plikiem JSON nawet w przypadku określenia `JsonNamingPolicy.CamelCase` dla `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-209">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="d70d6-210">Wyliczenia jako ciągi</span><span class="sxs-lookup"><span data-stu-id="d70d6-210">Enums as strings</span></span>

<span data-ttu-id="d70d6-211">Domyślnie wyliczenia są serializowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="d70d6-211">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="d70d6-212">Aby serializować nazwy wyliczenia jako ciągi, użyj <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="d70d6-212">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="d70d6-213">Załóżmy na przykład, że trzeba serializować następujące klasy, które mają Wyliczenie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-213">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="d70d6-214">Jeśli podsumowanie jest `Hot` , domyślnie serializowany kod JSON ma wartość liczbową 3:</span><span class="sxs-lookup"><span data-stu-id="d70d6-214">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="d70d6-215">Następujący przykładowy kod serializować nazwy wyliczenia zamiast wartości liczbowych i konwertuje nazwy na notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="d70d6-215">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-216">Wynikowy kod JSON wygląda podobnie do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="d70d6-216">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="d70d6-217">Można również deserializować nazwy ciągów wyliczenia, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-217">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="d70d6-218">Wyklucz właściwości z serializacji</span><span class="sxs-lookup"><span data-stu-id="d70d6-218">Exclude properties from serialization</span></span>

<span data-ttu-id="d70d6-219">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="d70d6-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="d70d6-220">Jeśli nie chcesz, aby niektóre z nich pojawiały się w danych wyjściowych JSON, masz kilka opcji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="d70d6-221">W tej sekcji wyjaśniono, jak wykluczyć:</span><span class="sxs-lookup"><span data-stu-id="d70d6-221">This section explains how to exclude:</span></span>

* [<span data-ttu-id="d70d6-222">Poszczególne właściwości</span><span class="sxs-lookup"><span data-stu-id="d70d6-222">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="d70d6-223">Wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d70d6-223">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="d70d6-224">Wszystkie właściwości o wartości null</span><span class="sxs-lookup"><span data-stu-id="d70d6-224">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="d70d6-225">Wyklucz pojedyncze właściwości</span><span class="sxs-lookup"><span data-stu-id="d70d6-225">Exclude individual properties</span></span>

<span data-ttu-id="d70d6-226">Aby zignorować poszczególne właściwości, Użyj atrybutu [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="d70d6-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="d70d6-227">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-227">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="d70d6-228">Wyklucz wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d70d6-228">Exclude all read-only properties</span></span>

<span data-ttu-id="d70d6-229">Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="d70d6-229">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="d70d6-230">Aby wykluczyć wszystkie właściwości tylko do odczytu, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true` , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-230">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-231">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-231">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="d70d6-232">Ta opcja ma zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-232">This option applies only to serialization.</span></span> <span data-ttu-id="d70d6-233">Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="d70d6-233">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="d70d6-234">Wyklucz wszystkie właściwości wartości null</span><span class="sxs-lookup"><span data-stu-id="d70d6-234">Exclude all null value properties</span></span>

<span data-ttu-id="d70d6-235">Aby wykluczyć wszystkie właściwości wartości null, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> Właściwość na `true` , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-236">Oto przykład obiektu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="d70d6-237">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d70d6-237">Property</span></span> |<span data-ttu-id="d70d6-238">Wartość</span><span class="sxs-lookup"><span data-stu-id="d70d6-238">Value</span></span>  |
|---
<span data-ttu-id="d70d6-239">title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-239">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-240">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-240">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-241">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-241">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-242">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-242">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-243">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-243">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="d70d6-244">title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-244">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-245">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-245">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-246">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-246">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-247">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-247">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-248">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-248">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="d70d6-249">-----|---title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-249">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-250">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-250">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-251">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-251">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-252">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-252">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-253">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-253">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="d70d6-254">title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-254">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-255">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-255">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-256">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-256">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-257">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-257">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-258">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-258">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="d70d6-259">-----| | Data | 8/1/2019 12:00:00 AM-07:00 | | TemperatureCelsius | 25 | | Podsumowanie | wartość null |</span><span class="sxs-lookup"><span data-stu-id="d70d6-259">-----| | Date    | 8/1/2019 12:00:00 AM -07:00| | TemperatureCelsius| 25 | | Summary| null|</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="d70d6-260">To ustawienie dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-260">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="d70d6-261">Aby uzyskać informacje o jego wpływie na deserializacji, zobacz [Ignore null podczas deserializacji](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="d70d6-261">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="d70d6-262">Dostosuj kodowanie znaków</span><span class="sxs-lookup"><span data-stu-id="d70d6-262">Customize character encoding</span></span>

<span data-ttu-id="d70d6-263">Domyślnie serializator wyprowadza wszystkie znaki nienależące do zestawu znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="d70d6-263">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="d70d6-264">Oznacza to, że zastępuje je, `\uxxxx` gdzie `xxxx` jest kodem Unicode znaku.</span><span class="sxs-lookup"><span data-stu-id="d70d6-264">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="d70d6-265">Na przykład, jeśli `Summary` Właściwość jest ustawiona na wartość cyrylicy жарко, `WeatherForecast` obiekt jest serializowany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-265">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="d70d6-266">Serializowanie zestawów znaków języka</span><span class="sxs-lookup"><span data-stu-id="d70d6-266">Serialize language character sets</span></span>

<span data-ttu-id="d70d6-267">Aby serializować zestawy znaków z co najmniej jednego języka bez ucieczki, określ [zakresy Unicode](xref:System.Text.Unicode.UnicodeRanges) podczas tworzenia wystąpienia <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-267">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="d70d6-268">Ten kod nie ma ucieczki znaków cyrylicy lub greckich.</span><span class="sxs-lookup"><span data-stu-id="d70d6-268">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="d70d6-269">Jeśli `Summary` Właściwość jest ustawiona na wartość cyrylicy жарко, `WeatherForecast` obiekt jest serializowany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-269">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="d70d6-270">Aby serializować wszystkie zestawy językowe bez ucieczki, użyj <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="d70d6-270">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="d70d6-271">Serializacja określonych znaków</span><span class="sxs-lookup"><span data-stu-id="d70d6-271">Serialize specific characters</span></span>

<span data-ttu-id="d70d6-272">Alternatywą jest określenie pojedynczych znaków, które mają być dozwolone, bez konieczności ucieczki.</span><span class="sxs-lookup"><span data-stu-id="d70d6-272">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="d70d6-273">Poniższy przykład serializacji tylko dwa pierwsze znaki жарко:</span><span class="sxs-lookup"><span data-stu-id="d70d6-273">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="d70d6-274">Oto przykład kodu JSON utworzonego przez poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="d70d6-274">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="d70d6-275">Serializować wszystkie znaki</span><span class="sxs-lookup"><span data-stu-id="d70d6-275">Serialize all characters</span></span>

<span data-ttu-id="d70d6-276">Aby zminimalizować liczbę ucieczki, można użyć <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-276">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="d70d6-277">W porównaniu z domyślnym koderem `UnsafeRelaxedJsonEscaping` koder jest bardziej ograniczając, aby umożliwić przekazywanie znaków przez niezmieniony:</span><span class="sxs-lookup"><span data-stu-id="d70d6-277">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="d70d6-278">Nie ucieczk znaków w języku HTML, takich jak `<` , `>` , `&` , i `'` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-278">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="d70d6-279">Nie oferuje żadnej dodatkowej ochrony przed atakami na ataki typu XSS lub ujawnienie informacji, takich jak te, które mogą wynikać z klienta i serwera bez zgody na *zestaw znaków*.</span><span class="sxs-lookup"><span data-stu-id="d70d6-279">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="d70d6-280">Używaj niebezpiecznego kodera tylko wtedy, gdy wiadomo, że klient będzie interpretować otrzymany ładunek jako zakodowany w formacie JSON UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d70d6-280">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="d70d6-281">Można na przykład użyć go, jeśli serwer wysyła nagłówek odpowiedzi `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-281">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="d70d6-282">Nigdy nie Zezwalaj na `UnsafeRelaxedJsonEscaping` emitowanie nieprzetworzonych danych wyjściowych do strony HTML lub `<script>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d70d6-282">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="d70d6-283">Serializowanie właściwości klas pochodnych</span><span class="sxs-lookup"><span data-stu-id="d70d6-283">Serialize properties of derived classes</span></span>

<span data-ttu-id="d70d6-284">Serializacja hierarchii typów polimorficznych nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="d70d6-284">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="d70d6-285">Na przykład, jeśli właściwość jest zdefiniowana jako interfejs lub Klasa abstrakcyjna, tylko właściwości zdefiniowane w interfejsie lub klasie abstrakcyjnej są serializowane, nawet jeśli typ środowiska uruchomieniowego ma dodatkowe właściwości.</span><span class="sxs-lookup"><span data-stu-id="d70d6-285">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="d70d6-286">Wyjątki dotyczące tego zachowania zostały omówione w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-286">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="d70d6-287">Załóżmy na przykład, że masz `WeatherForecast` klasę i klasę pochodną `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-287">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="d70d6-288">I Załóżmy, że argument typu `Serialize` metody w czasie kompilacji to `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-288">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="d70d6-289">W tym scenariuszu `WindSpeed` Właściwość nie jest serializowana, nawet jeśli `weatherForecast` obiekt jest rzeczywiście `WeatherForecastDerived` obiektem.</span><span class="sxs-lookup"><span data-stu-id="d70d6-289">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="d70d6-290">Tylko właściwości klasy bazowej są serializowane:</span><span class="sxs-lookup"><span data-stu-id="d70d6-290">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="d70d6-291">Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="d70d6-291">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="d70d6-292">Aby serializować właściwości typu pochodnego w poprzednim przykładzie, należy użyć jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="d70d6-292">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="d70d6-293">Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A> , które pozwala określić typ w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="d70d6-293">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="d70d6-294">Zadeklaruj obiekt, który ma zostać Zserializowany jako `object` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-294">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="d70d6-295">W poprzednim przykładowym scenariuszu oba podejścia powodują, że `WindSpeed` Właściwość powinna zostać uwzględniona w danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-295">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="d70d6-296">Te podejścia zapewniają serializację polimorficzne tylko dla obiektu głównego, który ma być serializowany, a nie dla właściwości tego obiektu głównego.</span><span class="sxs-lookup"><span data-stu-id="d70d6-296">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="d70d6-297">Można uzyskać serializację polimorficzny dla obiektów niższego poziomu, jeśli zdefiniujesz je jako typ `object` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-297">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="d70d6-298">Na przykład załóżmy, `WeatherForecast` że Klasa ma właściwość o nazwie `PreviousForecast` , która może być zdefiniowana jako typ `WeatherForecast` lub `object` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-298">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="d70d6-299">Jeśli `PreviousForecast` Właściwość zawiera wystąpienie `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-299">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="d70d6-300">Dane wyjściowe JSON z serializacji `WeatherForecastWithPrevious` **nie obejmują** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-300">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="d70d6-301">Dane wyjściowe JSON z serializacji `WeatherForecastWithPreviousAsObject` **obejmują** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-301">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="d70d6-302">Aby serializować `WeatherForecastWithPreviousAsObject` , nie jest konieczne wywołanie `Serialize<object>` lub `GetType` ponieważ obiekt główny nie jest tym, który może znajdować się w typie pochodnym.</span><span class="sxs-lookup"><span data-stu-id="d70d6-302">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="d70d6-303">Poniższy przykład kodu nie wywołuje `Serialize<object>` lub `GetType` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-303">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="d70d6-304">Powyższy kod poprawnie serializować `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-304">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="d70d6-305">To samo podejście do definiowania właściwości jako `object` współdziałanie z interfejsami.</span><span class="sxs-lookup"><span data-stu-id="d70d6-305">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="d70d6-306">Załóżmy, że masz następujący interfejs i implementacja, i chcesz serializować klasę o właściwościach zawierających wystąpienia implementacji:</span><span class="sxs-lookup"><span data-stu-id="d70d6-306">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="d70d6-307">Podczas serializacji wystąpienia elementu `Forecasts` , `Tuesday` wyświetlana `WindSpeed` jest tylko właściwość, ponieważ `Tuesday` jest zdefiniowana jako `object` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-307">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="d70d6-308">Poniższy przykład pokazuje kod JSON, który wynika z poprzedniego kodu:</span><span class="sxs-lookup"><span data-stu-id="d70d6-308">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="d70d6-309">Aby uzyskać więcej informacji na temat **serializacji**polimorficznej i informacje o **deserializacji**, zobacz [Jak przeprowadzić migrację z Newtonsoft.Json do System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="d70d6-309">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="d70d6-310">Zezwalaj na komentarze i końcowe przecinki</span><span class="sxs-lookup"><span data-stu-id="d70d6-310">Allow comments and trailing commas</span></span>

<span data-ttu-id="d70d6-311">Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-311">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="d70d6-312">Aby zezwolić na komentarze w formacie JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> Właściwość na `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-312">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="d70d6-313">I aby zezwolić na końcowe przecinki, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> Właściwość na `true` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-313">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="d70d6-314">Poniższy przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="d70d6-314">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="d70d6-315">Oto przykładowy kod JSON z komentarzami i końcowym przecinkiem:</span><span class="sxs-lookup"><span data-stu-id="d70d6-315">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="d70d6-316">Dopasowanie właściwości bez uwzględniania wielkości liter</span><span class="sxs-lookup"><span data-stu-id="d70d6-316">Case-insensitive property matching</span></span>

<span data-ttu-id="d70d6-317">Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d70d6-317">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="d70d6-318">Aby zmienić to zachowanie, ustaw opcję <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-318">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="d70d6-319">Oto przykład JSON z nazwami właściwości przypadku notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="d70d6-319">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="d70d6-320">Można ją zdeserializować do następującego typu, który ma nazwy właściwości przypadku języka Pascal.</span><span class="sxs-lookup"><span data-stu-id="d70d6-320">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="d70d6-321">Obsługa przepełnienia kodu JSON</span><span class="sxs-lookup"><span data-stu-id="d70d6-321">Handle overflow JSON</span></span>

<span data-ttu-id="d70d6-322">Podczas deserializacji można odbierać dane w formacie JSON, które nie są reprezentowane przez właściwości typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="d70d6-322">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="d70d6-323">Załóżmy na przykład, że typ docelowy to:</span><span class="sxs-lookup"><span data-stu-id="d70d6-323">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="d70d6-324">I kod JSON do deserializacji jest następujący:</span><span class="sxs-lookup"><span data-stu-id="d70d6-324">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="d70d6-325">W przypadku deserializacji kodu JSON pokazanego w pokazanym typie, `DatesAvailable` `SummaryWords` właściwości i mają wartość Nowhere to go i są tracone.</span><span class="sxs-lookup"><span data-stu-id="d70d6-325">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="d70d6-326">Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="d70d6-326">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="d70d6-327">Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie próbkowania dodatkowe dane staną się parami klucz-wartość `ExtensionData` Właściwości:</span><span class="sxs-lookup"><span data-stu-id="d70d6-327">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="d70d6-328">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d70d6-328">Property</span></span> |<span data-ttu-id="d70d6-329">Wartość</span><span class="sxs-lookup"><span data-stu-id="d70d6-329">Value</span></span>  |<span data-ttu-id="d70d6-330">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d70d6-330">Notes</span></span>  |
|---
<span data-ttu-id="d70d6-331">title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-331">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-332">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-332">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-333">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-333">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-334">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-334">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-335">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-335">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="d70d6-336">title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-336">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-337">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-337">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-338">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-338">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-339">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-339">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-340">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-340">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="d70d6-341">-----|---title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-341">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-342">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-342">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-343">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-343">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-344">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-344">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-345">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-345">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="d70d6-346">title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-346">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-347">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-347">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-348">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-348">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-349">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-349">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-350">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-350">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="d70d6-351">-----|---title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-351">-----|--- title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-352">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-352">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-353">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-353">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-354">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-354">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-355">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-355">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

-
<span data-ttu-id="d70d6-356">title: Opis: "w tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-356">title: description: 'This article shows you how to use the System.Text.Json namespace to serialize to and deserialize from JSON in .NET.</span></span> <span data-ttu-id="d70d6-357">Zawiera przykładowy kod ".</span><span class="sxs-lookup"><span data-stu-id="d70d6-357">It includes sample code.'</span></span>
<span data-ttu-id="d70d6-358">MS. Date: No-Loc:</span><span class="sxs-lookup"><span data-stu-id="d70d6-358">ms.date: no-loc:</span></span>
- <span data-ttu-id="d70d6-359">'System.Text.Json'</span><span class="sxs-lookup"><span data-stu-id="d70d6-359">'System.Text.Json'</span></span>
- <span data-ttu-id="d70d6-360">" Newtonsoft.Json " helpviewer_keywords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-360">'Newtonsoft.Json' helpviewer_keywords:</span></span>
- 
- 
- 
- 

<span data-ttu-id="d70d6-361">-----| | Data | 8/1/2019 12:00:00 AM-07:00 | | | TemperatureCelsius | 0 | Niezgodność z rozróżnianiem wielkości liter ( `temperatureCelsius` w formacie JSON), więc właściwość nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="d70d6-361">-----| | Date    | 8/1/2019 12:00:00 AM -07:00|| | TemperatureCelsius| 0 | Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> <span data-ttu-id="d70d6-362">| | Podsumowanie | Gorąca | | | ExtensionData — | temperatureCelsius: 25 | Ponieważ przypadek nie jest zgodny, ta właściwość JSON jest dodatkową, a jej para klucz-wartość w słowniku. | || DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="d70d6-362">| | Summary | Hot || | ExtensionData | temperatureCelsius: 25 |Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.| || DatesAvailable:</span></span><br>  <span data-ttu-id="d70d6-363">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="d70d6-363">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="d70d6-364">8/2/2019 12:00:00 AM-07:00 | Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości. | | | SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="d70d6-364">8/2/2019 12:00:00 AM -07:00 |Extra property from the JSON becomes a key-value pair, with an array as the value object.| | |SummaryWords:</span></span><br><span data-ttu-id="d70d6-365">Chłodna</span><span class="sxs-lookup"><span data-stu-id="d70d6-365">Cool</span></span><br><span data-ttu-id="d70d6-366">Wiatr</span><span class="sxs-lookup"><span data-stu-id="d70d6-366">Windy</span></span><br><span data-ttu-id="d70d6-367">Humid | Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości. |</span><span class="sxs-lookup"><span data-stu-id="d70d6-367">Humid |Extra property from the JSON becomes a key-value pair, with an array as the value object.|</span></span>

<span data-ttu-id="d70d6-368">Gdy obiekt docelowy jest serializowany, pary wartości klucza danych rozszerzenia stają się właściwościami JSON tak samo jak w przychodzących danych JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-368">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="d70d6-369">Zauważ, że `ExtensionData` Nazwa właściwości nie pojawia się w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-369">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="d70d6-370">Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.</span><span class="sxs-lookup"><span data-stu-id="d70d6-370">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="d70d6-371">Ignoruj wartość null podczas deserializacji</span><span class="sxs-lookup"><span data-stu-id="d70d6-371">Ignore null when deserializing</span></span>

<span data-ttu-id="d70d6-372">Domyślnie, jeśli właściwość w formacie JSON ma wartość null, odpowiadająca jej właściwość w obiekcie docelowym ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d70d6-372">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="d70d6-373">W niektórych scenariuszach właściwość target może mieć wartość domyślną i nie ma potrzeby przesłonięcia wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="d70d6-373">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="d70d6-374">Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:</span><span class="sxs-lookup"><span data-stu-id="d70d6-374">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="d70d6-375">Załóżmy, że następujący kod JSON jest deserializowany:</span><span class="sxs-lookup"><span data-stu-id="d70d6-375">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="d70d6-376">Po deserializacji `Summary` Właściwość `WeatherForecastWithDefault` obiektu ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="d70d6-376">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="d70d6-377">Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> wartość `true` tak, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-377">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="d70d6-378">W przypadku tej opcji `Summary` Właściwość `WeatherForecastWithDefault` obiektu jest wartością domyślną "Brak podsumowania" po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-378">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="d70d6-379">Wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="d70d6-379">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="d70d6-380">Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki.</span><span class="sxs-lookup"><span data-stu-id="d70d6-380">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="d70d6-381">Utf8JsonReader, Utf8JsonWriter i JsonDocument</span><span class="sxs-lookup"><span data-stu-id="d70d6-381">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="d70d6-382"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>jest wysoką wydajnością, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, Odczytaj z `ReadOnlySpan<byte>` lub `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-382"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="d70d6-383">`Utf8JsonReader`Jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-383">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="d70d6-384"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>Metoda używa `Utf8JsonReader` w obszarze okładki.</span><span class="sxs-lookup"><span data-stu-id="d70d6-384">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="d70d6-385"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>jest wysoce wydajnym sposobem pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy .NET, takich jak `String` , `Int32` , i `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-385"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="d70d6-386">Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="d70d6-386">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="d70d6-387"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>Metoda używa `Utf8JsonWriter` w obszarze okładki.</span><span class="sxs-lookup"><span data-stu-id="d70d6-387">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="d70d6-388"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>zapewnia możliwość tworzenia Document Object Model tylko do odczytu (DOM) za pomocą programu `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-388"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="d70d6-389">DOM zapewnia losowy dostęp do danych w ładunku JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-389">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="d70d6-390">Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typu.</span><span class="sxs-lookup"><span data-stu-id="d70d6-390">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="d70d6-391">`JsonElement`Typ udostępnia moduł wyliczający tablic i obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET.</span><span class="sxs-lookup"><span data-stu-id="d70d6-391">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="d70d6-392">`JsonDocument`uwidacznia <xref:System.Text.Json.JsonDocument.RootElement> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="d70d6-392">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="d70d6-393">W poniższych sekcjach pokazano, jak używać tych narzędzi do odczytywania i pisania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-393">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="d70d6-394">Korzystanie z JsonDocument do uzyskiwania dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="d70d6-394">Use JsonDocument for access to data</span></span>

<span data-ttu-id="d70d6-395">Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.JsonDocument> klasy do losowego dostępu do danych w ciągu JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-395">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="d70d6-396">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-396">The preceding code:</span></span>

* <span data-ttu-id="d70d6-397">Przyjęto, że kod JSON do analizy jest w ciągu o nazwie `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-397">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="d70d6-398">Oblicza średnią ocenę dla obiektów w `Students` tablicy, która ma `Grade` Właściwość.</span><span class="sxs-lookup"><span data-stu-id="d70d6-398">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="d70d6-399">Przypisuje domyślną ocenę 70 dla studentów, którzy nie posiadają klasy.</span><span class="sxs-lookup"><span data-stu-id="d70d6-399">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="d70d6-400">Zlicza uczniów przez zwiększenie `count` zmiennej przy każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="d70d6-400">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="d70d6-401">Alternatywą jest wywołanie <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-401">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="d70d6-402">Oto przykład pliku JSON, który jest przetwarzany przez ten kod:</span><span class="sxs-lookup"><span data-stu-id="d70d6-402">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="d70d6-403">Użyj JsonDocument, aby zapisać kod JSON</span><span class="sxs-lookup"><span data-stu-id="d70d6-403">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="d70d6-404">Poniższy przykład pokazuje, jak napisać kod JSON z <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="d70d6-404">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="d70d6-405">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-405">The preceding code:</span></span>

* <span data-ttu-id="d70d6-406">Odczytuje plik JSON, ładuje dane do `JsonDocument` i zapisuje sformatowany plik JSON w formacie.</span><span class="sxs-lookup"><span data-stu-id="d70d6-406">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="d70d6-407">Używa <xref:System.Text.Json.JsonDocumentOptions> do określenia, czy komentarze w wejściowym formacie JSON są dozwolone, ale ignorowane.</span><span class="sxs-lookup"><span data-stu-id="d70d6-407">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="d70d6-408">Po zakończeniu wywołania <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> na składniku zapisywania.</span><span class="sxs-lookup"><span data-stu-id="d70d6-408">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="d70d6-409">Alternatywą jest umożliwienie składnika zapisywania AutoFlush, gdy zostanie on usunięty.</span><span class="sxs-lookup"><span data-stu-id="d70d6-409">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="d70d6-410">Oto przykład danych wejściowych JSON do przetworzenia przez przykładowy kod:</span><span class="sxs-lookup"><span data-stu-id="d70d6-410">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="d70d6-411">Wynikiem są następujące niedrukowane dane wyjściowe JSON:</span><span class="sxs-lookup"><span data-stu-id="d70d6-411">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="d70d6-412">Użyj Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="d70d6-412">Use Utf8JsonWriter</span></span>

<span data-ttu-id="d70d6-413">Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.Utf8JsonWriter> klasy:</span><span class="sxs-lookup"><span data-stu-id="d70d6-413">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="d70d6-414">Użyj Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="d70d6-414">Use Utf8JsonReader</span></span>

<span data-ttu-id="d70d6-415">Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.Utf8JsonReader> klasy:</span><span class="sxs-lookup"><span data-stu-id="d70d6-415">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="d70d6-416">Poprzedni kod założono, że `jsonUtf8` zmienna jest tablicą bajtową, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d70d6-416">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="d70d6-417">Filtrowanie danych za pomocą Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="d70d6-417">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="d70d6-418">Poniższy przykład pokazuje, jak odczytywać plik synchronicznie i wyszukiwać wartość:</span><span class="sxs-lookup"><span data-stu-id="d70d6-418">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="d70d6-419">Powyższy kod ma następujące działanie:</span><span class="sxs-lookup"><span data-stu-id="d70d6-419">The preceding code:</span></span>

* <span data-ttu-id="d70d6-420">Przyjęto, że kod JSON zawiera tablicę obiektów, a każdy obiekt może zawierać właściwość "name" typu String.</span><span class="sxs-lookup"><span data-stu-id="d70d6-420">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="d70d6-421">Zlicza obiekty i wartości właściwości "name", które kończą się znakiem "University".</span><span class="sxs-lookup"><span data-stu-id="d70d6-421">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="d70d6-422">Przyjęto założenie, że plik jest zakodowany jako UTF-16 i transkoduje go do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d70d6-422">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="d70d6-423">Plik zakodowany jako UTF-8 może być odczytywany bezpośrednio do programu `ReadOnlySpan<byte>` , przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="d70d6-423">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="d70d6-424">Jeśli plik zawiera znacznik kolejności bajtów UTF-8, usuń go przed przekazaniem bajtów do `Utf8JsonReader` , ponieważ czytnik oczekuje tekstu.</span><span class="sxs-lookup"><span data-stu-id="d70d6-424">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="d70d6-425">W przeciwnym razie BOM jest traktowany jako nieprawidłowy kod JSON, a czytelnik zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d70d6-425">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="d70d6-426">Oto przykład JSON, który może odczytać poprzedzający kod.</span><span class="sxs-lookup"><span data-stu-id="d70d6-426">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="d70d6-427">Otrzymany komunikat podsumowujący to "2 z 4 mają nazwy kończące się na" University ":</span><span class="sxs-lookup"><span data-stu-id="d70d6-427">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="d70d6-428">Odczytaj ze strumienia przy użyciu Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="d70d6-428">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="d70d6-429">W przypadku odczytywania dużego pliku (na przykład gigabajta lub więcej) można uniknąć konieczności załadowania całego pliku do pamięci jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="d70d6-429">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="d70d6-430">W tym scenariuszu można użyć <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="d70d6-430">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="d70d6-431">W przypadku `Utf8JsonReader` odczytywania ze strumienia przy użyciu programu, obowiązują następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="d70d6-431">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="d70d6-432">Bufor zawierający częściowy ładunek JSON musi być co najmniej tak duży jak największy token JSON w tym samym czasie, aby czytnik mógł postępować dalej.</span><span class="sxs-lookup"><span data-stu-id="d70d6-432">The buffer containing the partial JSON payload must be at least as big as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="d70d6-433">Bufor musi być co najmniej tak duży jak największą sekwencję białych znaków w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-433">The buffer must be at least as big as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="d70d6-434">Czytnik nie śledzi danych, które zostały odczytane, dopóki nie zostaną całkowicie odczytane dalej <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> w ładunku JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-434">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="d70d6-435">Tak więc, gdy bajty są pozostawione w buforze, należy ponownie przekazać je do czytnika.</span><span class="sxs-lookup"><span data-stu-id="d70d6-435">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="d70d6-436">Możesz użyć, <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> Aby określić, ile bajtów pozostało.</span><span class="sxs-lookup"><span data-stu-id="d70d6-436">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="d70d6-437">Poniższy kod ilustruje sposób odczytywania ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="d70d6-437">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="d70d6-438">Przykład pokazuje <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="d70d6-438">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="d70d6-439">Podobny kod będzie działał z <xref:System.IO.FileStream> , z wyjątkiem sytuacji, gdy `FileStream` zawiera BOM w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="d70d6-439">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="d70d6-440">W takim przypadku należy rozdzielić te trzy bajty z buforu przed przekazaniem pozostałych bajtów do `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="d70d6-440">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="d70d6-441">W przeciwnym razie czytelnik zgłosi wyjątek, ponieważ BOM nie jest traktowany jako prawidłowa część JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-441">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="d70d6-442">Przykładowy kod rozpoczyna się od buforu 4 KB i podwaja rozmiar buforu za każdym razem, gdy okaże się, że rozmiar nie jest wystarczająco duży, aby dopasować pełny token JSON, który jest wymagany, aby czytnik mógł postępować w ładunku JSON.</span><span class="sxs-lookup"><span data-stu-id="d70d6-442">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not big enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="d70d6-443">Przykład JSON podany w fragmencie kodu wyzwala zwiększenie rozmiaru buforu tylko wtedy, gdy ustawisz bardzo mały początkowy rozmiar buforu, na przykład 10 bajtów.</span><span class="sxs-lookup"><span data-stu-id="d70d6-443">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="d70d6-444">Jeśli ustawisz początkowy rozmiar buforu na 10, `Console.WriteLine` instrukcje ilustrują przyczynę i wpływ rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="d70d6-444">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="d70d6-445">W początkowym rozmiarze bufora 4 KB cały przykładowy kod JSON jest pokazywany przez każdy z nich `Console.WriteLine` , a rozmiar buforu nigdy nie musi zostać zwiększony.</span><span class="sxs-lookup"><span data-stu-id="d70d6-445">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="d70d6-446">W powyższym przykładzie nie określono limitu rozmiaru buforu.</span><span class="sxs-lookup"><span data-stu-id="d70d6-446">The preceding example sets no limit to how big the buffer can grow.</span></span> <span data-ttu-id="d70d6-447">Jeśli rozmiar tokenu jest zbyt duży, kod może zakończyć się niepowodzeniem z <xref:System.OutOfMemoryException> wyjątkiem.</span><span class="sxs-lookup"><span data-stu-id="d70d6-447">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="d70d6-448">Taka sytuacja może wystąpić, jeśli kod JSON zawiera token o rozmiarze około 1 GB lub więcej, ponieważ Podwajanie rozmiaru 1 GB spowoduje, że rozmiar jest zbyt duży, aby zmieścił się w `int32` buforze.</span><span class="sxs-lookup"><span data-stu-id="d70d6-448">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d70d6-449">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="d70d6-449">Additional resources</span></span>

* <span data-ttu-id="d70d6-450">[System.Text.JsonPodsumowanie](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="d70d6-450">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="d70d6-451">Jak pisać konwertery niestandardowe</span><span class="sxs-lookup"><span data-stu-id="d70d6-451">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="d70d6-452">[Jak przeprowadzić migrację zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="d70d6-452">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="d70d6-453">[Obsługa DateTime i DateTimeOffset wSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="d70d6-453">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="d70d6-454">[System.Text.JsonDokumentacja interfejsu API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="d70d6-454">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
