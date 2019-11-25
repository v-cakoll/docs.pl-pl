---
title: Jak serializować i deserializować kod JSON C# przy użyciu-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 3d3dc0011562e25854938aff857f2832a5978b49
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283333"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="74e18-102">Jak serializować i deserializować kod JSON w programie .NET</span><span class="sxs-lookup"><span data-stu-id="74e18-102">How to serialize and deserialize JSON in .NET</span></span>

<span data-ttu-id="74e18-103">W tym artykule pokazano, jak używać przestrzeni nazw <xref:System.Text.Json> do serializacji i deserializacji do i z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="74e18-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="74e18-104">Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="74e18-104">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="74e18-105">Większość przykładowych kodów serializacji <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType>, aby `true` do "DB-Print" pliku JSON (z wcięciem i białym znakiem).</span><span class="sxs-lookup"><span data-stu-id="74e18-105">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="74e18-106">Do użycia w środowisku produkcyjnym zwykle przyjmuje się wartość domyślną `false` dla tego ustawienia.</span><span class="sxs-lookup"><span data-stu-id="74e18-106">For production use, you would typically accept the default value of `false` for this setting.</span></span>

## <a name="namespaces"></a><span data-ttu-id="74e18-107">Namespaces</span><span class="sxs-lookup"><span data-stu-id="74e18-107">Namespaces</span></span>

<span data-ttu-id="74e18-108">Przestrzeń nazw <xref:System.Text.Json> zawiera wszystkie punkty wejścia i typy główne.</span><span class="sxs-lookup"><span data-stu-id="74e18-108">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="74e18-109">Przestrzeń nazw <xref:System.Text.Json.Serialization> zawiera atrybuty i interfejsy API dla zaawansowanych scenariuszy i dostosowań specyficznych dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-109">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="74e18-110">Przykłady kodu przedstawione w tym artykule wymagają `using` dyrektyw dla jednej lub obu tych przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="74e18-110">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="74e18-111">Atrybuty z przestrzeni nazw <xref:System.Runtime.Serialization> nie są obecnie obsługiwane w `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="74e18-111">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="74e18-112">Pisanie obiektów .NET w formacie JSON (Serializacja)</span><span class="sxs-lookup"><span data-stu-id="74e18-112">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="74e18-113">Aby zapisać dane JSON do ciągu lub do pliku, wywołaj metodę <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74e18-113">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="74e18-114">Poniższy przykład tworzy kod JSON jako ciąg:</span><span class="sxs-lookup"><span data-stu-id="74e18-114">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-115">Poniższy przykład używa kodu synchronicznego do utworzenia pliku JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-115">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-116">W poniższym przykładzie jest tworzony plik JSON przy użyciu kodu asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="74e18-116">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-117">Powyższe przykłady używają wnioskowania typu dla serializowanego typu.</span><span class="sxs-lookup"><span data-stu-id="74e18-117">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="74e18-118">Przeciążenie `Serialize()` przyjmuje parametr typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="74e18-118">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="74e18-119">Przykład serializacji</span><span class="sxs-lookup"><span data-stu-id="74e18-119">Serialization example</span></span>

<span data-ttu-id="74e18-120">Oto przykładowa Klasa, która zawiera kolekcje i zagnieżdżoną klasę:</span><span class="sxs-lookup"><span data-stu-id="74e18-120">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="74e18-121">Dane wyjściowe JSON serializowania wystąpienia poprzedniego typu wyglądają podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="74e18-121">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="74e18-122">Dane wyjściowe JSON domyślnie są zminimalizowanego:</span><span class="sxs-lookup"><span data-stu-id="74e18-122">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="74e18-123">W poniższym przykładzie przedstawiono ten sam kod JSON, sformatowany (to jest całkiem wydruk z odstępami i wcięciami):</span><span class="sxs-lookup"><span data-stu-id="74e18-123">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="74e18-124">Serializacja do UTF-8</span><span class="sxs-lookup"><span data-stu-id="74e18-124">Serialize to UTF-8</span></span>

<span data-ttu-id="74e18-125">Aby serializować do UTF-8, wywołaj metodę <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="74e18-125">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-126">Dostępne jest również Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A>, które pobiera <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="74e18-126">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="74e18-127">Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach.</span><span class="sxs-lookup"><span data-stu-id="74e18-127">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="74e18-128">Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="74e18-128">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="74e18-129">Zachowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="74e18-129">Serialization behavior</span></span>

* <span data-ttu-id="74e18-130">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="74e18-130">By default, all public properties are serialized.</span></span> <span data-ttu-id="74e18-131">Można [określić właściwości do wykluczenia](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="74e18-131">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="74e18-132">[Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem języka HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="74e18-132">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="74e18-133">Domyślnie JSON jest zminimalizowanego.</span><span class="sxs-lookup"><span data-stu-id="74e18-133">By default, JSON is minified.</span></span> <span data-ttu-id="74e18-134">Można tu [wydrukować kod JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="74e18-134">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="74e18-135">Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET.</span><span class="sxs-lookup"><span data-stu-id="74e18-135">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="74e18-136">Można [dostosować wielkość liter w nazwach JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="74e18-136">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="74e18-137">Wykryto odwołania cykliczne i zostały zgłoszone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="74e18-137">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="74e18-138">Aby uzyskać więcej informacji, zobacz [problem 38579 dotyczący odwołań cyklicznych](https://github.com/dotnet/corefx/issues/38579) w repozytorium dotnet/corefx w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="74e18-138">For more information, see [issue 38579 on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="74e18-139">Obecnie pola są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="74e18-139">Currently, fields are excluded.</span></span>

<span data-ttu-id="74e18-140">Obsługiwane typy to:</span><span class="sxs-lookup"><span data-stu-id="74e18-140">Supported types include:</span></span>

* <span data-ttu-id="74e18-141">Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="74e18-141">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="74e18-142">Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="74e18-142">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="74e18-143">Tablice jednowymiarowe i nieregularne (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="74e18-143">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="74e18-144">`Dictionary<string,TValue>`, gdzie `TValue` jest `object`, `JsonElement`lub POCO.</span><span class="sxs-lookup"><span data-stu-id="74e18-144">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="74e18-145">Kolekcje z następujących przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="74e18-145">Collections from the following namespaces.</span></span> <span data-ttu-id="74e18-146">Aby uzyskać więcej informacji, zobacz [problem związany z obsługą kolekcji](https://github.com/dotnet/corefx/issues/36643) w repozytorium dotnet/corefx w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="74e18-146">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="74e18-147">Można [zaimplementować niestandardowe konwertery](system-text-json-converters-how-to.md) w celu obsługi dodatkowych typów lub zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="74e18-147">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="74e18-148">Jak odczytywać dane JSON do obiektów .NET (deserializacji)</span><span class="sxs-lookup"><span data-stu-id="74e18-148">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="74e18-149">Aby zdeserializować z ciągu lub pliku, wywołaj metodę <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74e18-149">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="74e18-150">Poniższy przykład odczytuje dane JSON z ciągu i tworzy wystąpienie klasy `WeatherForecast` pokazanej wcześniej dla [przykładu serializacji](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="74e18-150">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="74e18-151">Aby zdeserializować z pliku przy użyciu kodu synchronicznego, Odczytaj plik do ciągu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-151">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="74e18-152">Aby zdeserializować z pliku przy użyciu kodu asynchronicznego, wywołaj metodę <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:</span><span class="sxs-lookup"><span data-stu-id="74e18-152">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="74e18-153">Deserializacja z UTF-8</span><span class="sxs-lookup"><span data-stu-id="74e18-153">Deserialize from UTF-8</span></span>

<span data-ttu-id="74e18-154">Aby zdeserializować z UTF-8, wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>, które pobiera `Utf8JsonReader` lub `ReadOnlySpan<byte>`, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="74e18-154">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="74e18-155">W przykładach założono, że kod JSON znajduje się w tablicy bajtów o nazwie jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="74e18-155">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="74e18-156">Zachowanie deserializacji</span><span class="sxs-lookup"><span data-stu-id="74e18-156">Deserialization behavior</span></span>

* <span data-ttu-id="74e18-157">Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="74e18-157">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="74e18-158">Można [określić wielkość liter](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="74e18-158">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="74e18-159">Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="74e18-159">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="74e18-160">Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="74e18-160">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="74e18-161">Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="74e18-161">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="74e18-162">Aby uzyskać więcej informacji, zobacz artykuł [dotyczący usługi GitHub 38569 w przypadku niemodyfikowalnej obsługi obiektów](https://github.com/dotnet/corefx/issues/38569) i [problem 38163 w przypadku obsługi właściwości tylko do odczytu](https://github.com/dotnet/corefx/issues/38163) w repozytorium dotnet/corefx w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="74e18-162">For more information, see GitHub [issue 38569 on immutable object support](https://github.com/dotnet/corefx/issues/38569) and [issue 38163 on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="74e18-163">Domyślnie wyliczenia są obsługiwane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="74e18-163">By default, enums are supported as numbers.</span></span> <span data-ttu-id="74e18-164">[Nazwy wyliczenia można serializować jako ciągi](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="74e18-164">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="74e18-165">Pola nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="74e18-165">Fields aren't supported.</span></span>
* <span data-ttu-id="74e18-166">Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON.</span><span class="sxs-lookup"><span data-stu-id="74e18-166">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="74e18-167">Można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="74e18-167">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="74e18-168">[Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.</span><span class="sxs-lookup"><span data-stu-id="74e18-168">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="74e18-169">[Konwertery niestandardowe można zaimplementować](system-text-json-converters-how-to.md) w celu zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="74e18-169">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="74e18-170">Serializacja do sformatowanego pliku JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-170">Serialize to formatted JSON</span></span>

<span data-ttu-id="74e18-171">Aby wydrukować dane wyjściowe JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="74e18-171">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="74e18-172">Oto przykład typu do serializacji i całkiem wydrukowanych danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-172">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="74e18-173">Dostosowywanie nazw i wartości JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-173">Customize JSON names and values</span></span>

<span data-ttu-id="74e18-174">Domyślnie nazwy właściwości i klucze słownika nie są zmieniane w danych wyjściowych JSON, włącznie z wielkością liter.</span><span class="sxs-lookup"><span data-stu-id="74e18-174">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="74e18-175">Wartości wyliczeniowe są reprezentowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="74e18-175">Enum values are represented as numbers.</span></span> <span data-ttu-id="74e18-176">W tej sekcji wyjaśniono, jak:</span><span class="sxs-lookup"><span data-stu-id="74e18-176">This section explains how to:</span></span>

* [<span data-ttu-id="74e18-177">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="74e18-177">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="74e18-178">Konwertuj wszystkie nazwy właściwości na notacji CamelCase przypadku</span><span class="sxs-lookup"><span data-stu-id="74e18-178">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="74e18-179">Implementowanie zasad nazewnictwa właściwości niestandardowych</span><span class="sxs-lookup"><span data-stu-id="74e18-179">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="74e18-180">Konwertuj klucze słownika na notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="74e18-180">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="74e18-181">Konwertuj wyliczenia na ciągi i notacji CamelCase wielkość liter</span><span class="sxs-lookup"><span data-stu-id="74e18-181">Convert enums to strings and camel case</span></span>](#enums-as-strings) 

<span data-ttu-id="74e18-182">W przypadku innych scenariuszy, które wymagają specjalnej obsługi nazw i wartości właściwości JSON, można [zaimplementować konwertery niestandardowe](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="74e18-182">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="74e18-183">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="74e18-183">Customize individual property names</span></span>

<span data-ttu-id="74e18-184">Aby ustawić nazwę poszczególnych właściwości, Użyj atrybutu [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="74e18-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="74e18-185">Oto przykład typu do serializacji i powstającego JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-185">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="74e18-186">Nazwa właściwości ustawiona przez ten atrybut:</span><span class="sxs-lookup"><span data-stu-id="74e18-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="74e18-187">Stosuje się w obu kierunkach dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="74e18-188">Ma pierwszeństwo przed zasadami nazewnictwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="74e18-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="74e18-189">Użyj notacji CamelCase przypadku dla wszystkich nazw właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="74e18-190">Aby użyć notacji CamelCase przypadku dla wszystkich nazw właściwości JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="74e18-191">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-191">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="74e18-192">Zasady nazewnictwa właściwości przypadku notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="74e18-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="74e18-193">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="74e18-194">Jest zastępowany przez atrybuty `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="74e18-194">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="74e18-195">Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie notacji CamelCase wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="74e18-195">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="74e18-196">Użyj niestandardowych zasad nazewnictwa właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-196">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="74e18-197">Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę pochodzącą z <xref:System.Text.Json.JsonNamingPolicy> i Zastąp metodę <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-197">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="74e18-198">Następnie ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na wystąpienie klasy zasad nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="74e18-198">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-199">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-199">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="74e18-200">Zasady nazewnictwa właściwości JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-200">The JSON property naming policy:</span></span>

* <span data-ttu-id="74e18-201">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-201">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="74e18-202">Jest zastępowany przez atrybuty `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="74e18-202">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="74e18-203">Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest wielką literą.</span><span class="sxs-lookup"><span data-stu-id="74e18-203">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="74e18-204">Klucze słownika przypadku notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="74e18-204">Camel case dictionary keys</span></span>

<span data-ttu-id="74e18-205">Jeśli właściwość obiektu, który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>`, klucze `string` można przekonwertować na notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="74e18-205">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="74e18-206">W tym celu ustaw <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-206">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-207">Serializacja obiektu przy użyciu słownika o nazwie `TemperatureRanges`, który ma pary klucz-wartość, `"ColdMinTemp", 20` i `"HotMinTemp", 40` spowoduje to wyjście JSON podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="74e18-207">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="74e18-208">Zasady nazewnictwa przypadków notacji CamelCase dla kluczy słownika mają zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-208">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="74e18-209">W przypadku deserializacji słownika klucze będą zgodne z plikiem JSON nawet wtedy, gdy dla `DictionaryKeyPolicy`określono `JsonNamingPolicy.CamelCase`.</span><span class="sxs-lookup"><span data-stu-id="74e18-209">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="74e18-210">Wyliczenia jako ciągi</span><span class="sxs-lookup"><span data-stu-id="74e18-210">Enums as strings</span></span>

<span data-ttu-id="74e18-211">Domyślnie wyliczenia są serializowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="74e18-211">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="74e18-212">Aby serializować nazwy wyliczenia jako ciągi, użyj <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="74e18-212">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="74e18-213">Załóżmy na przykład, że trzeba serializować następujące klasy, które mają Wyliczenie:</span><span class="sxs-lookup"><span data-stu-id="74e18-213">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="74e18-214">Jeśli podsumowanie jest `Hot`, domyślnie serializowany kod JSON ma wartość liczbową 3:</span><span class="sxs-lookup"><span data-stu-id="74e18-214">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="74e18-215">Następujący przykładowy kod serializować nazwy wyliczenia zamiast wartości liczbowych i konwertuje nazwy na notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="74e18-215">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-216">Wynikowy kod JSON wygląda podobnie do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="74e18-216">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="74e18-217">Można również deserializować nazwy ciągów wyliczenia, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-217">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="74e18-218">Wyklucz właściwości z serializacji</span><span class="sxs-lookup"><span data-stu-id="74e18-218">Exclude properties from serialization</span></span>

<span data-ttu-id="74e18-219">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="74e18-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="74e18-220">Jeśli nie chcesz, aby niektóre z nich pojawiały się w danych wyjściowych JSON, masz kilka opcji.</span><span class="sxs-lookup"><span data-stu-id="74e18-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="74e18-221">W tej sekcji wyjaśniono, jak wykluczyć:</span><span class="sxs-lookup"><span data-stu-id="74e18-221">This section explains how to exclude:</span></span>

* [<span data-ttu-id="74e18-222">Poszczególne właściwości</span><span class="sxs-lookup"><span data-stu-id="74e18-222">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="74e18-223">Wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="74e18-223">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="74e18-224">Wszystkie właściwości o wartości null</span><span class="sxs-lookup"><span data-stu-id="74e18-224">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="74e18-225">Wyklucz pojedyncze właściwości</span><span class="sxs-lookup"><span data-stu-id="74e18-225">Exclude individual properties</span></span>

<span data-ttu-id="74e18-226">Aby zignorować poszczególne właściwości, Użyj atrybutu [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="74e18-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="74e18-227">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-227">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="74e18-228">Wyklucz wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="74e18-228">Exclude all read-only properties</span></span>

<span data-ttu-id="74e18-229">Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="74e18-229">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="74e18-230">Aby wykluczyć wszystkie właściwości tylko do odczytu, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-230">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-231">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-231">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="74e18-232">Ta opcja ma zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-232">This option applies only to serialization.</span></span> <span data-ttu-id="74e18-233">Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="74e18-233">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="74e18-234">Wyklucz wszystkie właściwości wartości null</span><span class="sxs-lookup"><span data-stu-id="74e18-234">Exclude all null value properties</span></span>

<span data-ttu-id="74e18-235">Aby wykluczyć wszystkie właściwości wartości null, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na `true`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-236">Oto przykład obiektu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="74e18-237">Właściwość</span><span class="sxs-lookup"><span data-stu-id="74e18-237">Property</span></span> |<span data-ttu-id="74e18-238">Wartość</span><span class="sxs-lookup"><span data-stu-id="74e18-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="74e18-239">Data</span><span class="sxs-lookup"><span data-stu-id="74e18-239">Date</span></span>    | <span data-ttu-id="74e18-240">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="74e18-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="74e18-241">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="74e18-241">TemperatureCelsius</span></span>| <span data-ttu-id="74e18-242">25</span><span class="sxs-lookup"><span data-stu-id="74e18-242">25</span></span> |
| <span data-ttu-id="74e18-243">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="74e18-243">Summary</span></span>| <span data-ttu-id="74e18-244">wartość null</span><span class="sxs-lookup"><span data-stu-id="74e18-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="74e18-245">To ustawienie dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="74e18-246">Aby uzyskać informacje o jego wpływie na deserializacji, zobacz [Ignore null podczas deserializacji](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="74e18-246">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="74e18-247">Dostosuj kodowanie znaków</span><span class="sxs-lookup"><span data-stu-id="74e18-247">Customize character encoding</span></span>

<span data-ttu-id="74e18-248">Domyślnie serializator wyprowadza wszystkie znaki nienależące do zestawu znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="74e18-248">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="74e18-249">Oznacza to, że zastępuje je `\uxxxx` gdzie `xxxx` jest kodem Unicode znaku.</span><span class="sxs-lookup"><span data-stu-id="74e18-249">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="74e18-250">Na przykład, jeśli właściwość `Summary` jest ustawiona na wartość cyrylicy жарко, obiekt `WeatherForecast` zostanie Zserializowany, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-250">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="74e18-251">Serializowanie zestawów znaków języka</span><span class="sxs-lookup"><span data-stu-id="74e18-251">Serialize language character sets</span></span>

<span data-ttu-id="74e18-252">Aby serializować zestawy znaków z co najmniej jednego języka bez ucieczki, określ [zakresy Unicode](xref:System.Text.Unicode.UnicodeRanges) podczas tworzenia wystąpienia <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-252">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="74e18-253">Ten kod nie ma ucieczki znaków cyrylicy lub greckich.</span><span class="sxs-lookup"><span data-stu-id="74e18-253">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="74e18-254">Jeśli właściwość `Summary` jest ustawiona na wartość cyrylicy жарко, obiekt `WeatherForecast` zostanie Zserializowany, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-254">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="74e18-255">Aby serializować wszystkie zestawy językowe bez ucieczki, użyj <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="74e18-255">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="74e18-256">Serializacja określonych znaków</span><span class="sxs-lookup"><span data-stu-id="74e18-256">Serialize specific characters</span></span>

<span data-ttu-id="74e18-257">Alternatywą jest określenie pojedynczych znaków, które mają być dozwolone, bez konieczności ucieczki.</span><span class="sxs-lookup"><span data-stu-id="74e18-257">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="74e18-258">Poniższy przykład serializacji tylko dwa pierwsze znaki жарко:</span><span class="sxs-lookup"><span data-stu-id="74e18-258">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="74e18-259">Oto przykład kodu JSON utworzonego przez poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="74e18-259">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="74e18-260">Serializować wszystkie znaki</span><span class="sxs-lookup"><span data-stu-id="74e18-260">Serialize all characters</span></span>

<span data-ttu-id="74e18-261">Aby zminimalizować liczbę ucieczki, można użyć <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-261">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="74e18-262">W porównaniu z domyślnym koderem, koder `UnsafeRelaxedJsonEscaping` jest bardziej ograniczając, aby umożliwić Przechodzenie znaków przez niezmieniony:</span><span class="sxs-lookup"><span data-stu-id="74e18-262">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="74e18-263">Nie wpływa to na znaki w języku HTML, takie jak `<`, `>`, `&`i `'`.</span><span class="sxs-lookup"><span data-stu-id="74e18-263">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="74e18-264">Nie oferuje żadnej dodatkowej ochrony przed atakami na ataki typu XSS lub ujawnienie informacji, takich jak te, które mogą wynikać z klienta i serwera bez zgody na *zestaw znaków*.</span><span class="sxs-lookup"><span data-stu-id="74e18-264">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="74e18-265">Używaj niebezpiecznego kodera tylko wtedy, gdy wiadomo, że klient będzie interpretować otrzymany ładunek jako zakodowany w formacie JSON UTF-8.</span><span class="sxs-lookup"><span data-stu-id="74e18-265">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="74e18-266">Można na przykład użyć go, jeśli serwer wysyła nagłówek odpowiedzi `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="74e18-266">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="74e18-267">Nigdy nie Zezwalaj na emitowanie nieprzetworzonych danych wyjściowych `UnsafeRelaxedJsonEscaping` do strony HTML lub `<script>` elementu.</span><span class="sxs-lookup"><span data-stu-id="74e18-267">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="74e18-268">Serializowanie właściwości klas pochodnych</span><span class="sxs-lookup"><span data-stu-id="74e18-268">Serialize properties of derived classes</span></span>

<span data-ttu-id="74e18-269">Serializacja polimorficzna nie jest obsługiwana w przypadku określenia w czasie kompilacji typu, który ma być serializowany.</span><span class="sxs-lookup"><span data-stu-id="74e18-269">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="74e18-270">Załóżmy na przykład, że masz klasę `WeatherForecast` i klasę pochodną `WeatherForecastWithWind`:</span><span class="sxs-lookup"><span data-stu-id="74e18-270">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="74e18-271">I Załóżmy, że argument typu metody `Serialize` w czasie kompilacji jest `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="74e18-271">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="74e18-272">W tym scenariuszu Właściwość `WindSpeed` nie jest serializowana, nawet jeśli obiekt `weatherForecast` jest w rzeczywistości obiektem `WeatherForecastWithWind`.</span><span class="sxs-lookup"><span data-stu-id="74e18-272">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="74e18-273">Tylko właściwości klasy bazowej są serializowane:</span><span class="sxs-lookup"><span data-stu-id="74e18-273">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="74e18-274">Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="74e18-274">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="74e18-275">Aby serializować właściwości typu pochodnego, należy użyć jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="74e18-275">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="74e18-276">Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A>, które pozwala określić typ w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="74e18-276">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="74e18-277">Zadeklaruj obiekt do serializacji jako `object`.</span><span class="sxs-lookup"><span data-stu-id="74e18-277">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="74e18-278">W poprzednim przykładowym scenariuszu oba podejścia powodują, że właściwość `WindSpeed` ma zostać uwzględniona w danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-278">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="74e18-279">Aby uzyskać informacje na temat deserializacji polimorficznej, zobacz [Obsługa deserializacji polimorficznej](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="74e18-279">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="74e18-280">Zezwalaj na komentarze i końcowe przecinki</span><span class="sxs-lookup"><span data-stu-id="74e18-280">Allow comments and trailing commas</span></span>

<span data-ttu-id="74e18-281">Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON.</span><span class="sxs-lookup"><span data-stu-id="74e18-281">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="74e18-282">Aby zezwolić na komentarze w formacie JSON, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="74e18-282">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="74e18-283">I aby zezwolić na końcowe przecinki, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="74e18-283">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="74e18-284">Poniższy przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="74e18-284">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="74e18-285">Oto przykładowy kod JSON z komentarzami i końcowym przecinkiem:</span><span class="sxs-lookup"><span data-stu-id="74e18-285">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="74e18-286">Dopasowanie właściwości bez uwzględniania wielkości liter</span><span class="sxs-lookup"><span data-stu-id="74e18-286">Case-insensitive property matching</span></span>

<span data-ttu-id="74e18-287">Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="74e18-287">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="74e18-288">Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="74e18-288">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="74e18-289">Oto przykład JSON z nazwami właściwości przypadku notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="74e18-289">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="74e18-290">Można ją zdeserializować do następującego typu, który ma nazwy właściwości przypadku języka Pascal.</span><span class="sxs-lookup"><span data-stu-id="74e18-290">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="74e18-291">Obsługa przepełnienia kodu JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-291">Handle overflow JSON</span></span>

<span data-ttu-id="74e18-292">Podczas deserializacji można odbierać dane w formacie JSON, które nie są reprezentowane przez właściwości typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="74e18-292">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="74e18-293">Załóżmy na przykład, że typ docelowy to:</span><span class="sxs-lookup"><span data-stu-id="74e18-293">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="74e18-294">I kod JSON do deserializacji jest następujący:</span><span class="sxs-lookup"><span data-stu-id="74e18-294">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="74e18-295">W przypadku deserializacji kodu JSON pokazanego w pokazanym typie właściwości `DatesAvailable` i `SummaryWords` mają wartość Nowhere i są tracone.</span><span class="sxs-lookup"><span data-stu-id="74e18-295">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="74e18-296">Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="74e18-296">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="74e18-297">Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie przykładowym dodatkowe dane staną się parami klucz-wartość właściwości `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="74e18-297">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="74e18-298">Właściwość</span><span class="sxs-lookup"><span data-stu-id="74e18-298">Property</span></span> |<span data-ttu-id="74e18-299">Wartość</span><span class="sxs-lookup"><span data-stu-id="74e18-299">Value</span></span>  |<span data-ttu-id="74e18-300">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74e18-300">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="74e18-301">Data</span><span class="sxs-lookup"><span data-stu-id="74e18-301">Date</span></span>    | <span data-ttu-id="74e18-302">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="74e18-302">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="74e18-303">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="74e18-303">TemperatureCelsius</span></span>| <span data-ttu-id="74e18-304">0</span><span class="sxs-lookup"><span data-stu-id="74e18-304">0</span></span> | <span data-ttu-id="74e18-305">Niezgodność z wielkością liter (`temperatureCelsius` w formacie JSON), więc właściwość nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="74e18-305">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="74e18-306">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="74e18-306">Summary</span></span> | <span data-ttu-id="74e18-307">Ręczne</span><span class="sxs-lookup"><span data-stu-id="74e18-307">Hot</span></span> ||
| <span data-ttu-id="74e18-308">ExtensionData —</span><span class="sxs-lookup"><span data-stu-id="74e18-308">ExtensionData</span></span> | <span data-ttu-id="74e18-309">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="74e18-309">temperatureCelsius: 25</span></span> |<span data-ttu-id="74e18-310">Ponieważ przypadek nie jest zgodny, ta właściwość JSON jest dodatkową i jest parą klucz-wartość w słowniku.</span><span class="sxs-lookup"><span data-stu-id="74e18-310">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="74e18-311">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="74e18-311">DatesAvailable:</span></span><br>  <span data-ttu-id="74e18-312">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="74e18-312">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="74e18-313">8/2/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="74e18-313">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="74e18-314">Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="74e18-314">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="74e18-315">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="74e18-315">SummaryWords:</span></span><br><span data-ttu-id="74e18-316">Ochłodzenia</span><span class="sxs-lookup"><span data-stu-id="74e18-316">Cool</span></span><br><span data-ttu-id="74e18-317">Wiatr</span><span class="sxs-lookup"><span data-stu-id="74e18-317">Windy</span></span><br><span data-ttu-id="74e18-318">Humid</span><span class="sxs-lookup"><span data-stu-id="74e18-318">Humid</span></span> |<span data-ttu-id="74e18-319">Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="74e18-319">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="74e18-320">Gdy obiekt docelowy jest serializowany, pary wartości klucza danych rozszerzenia stają się właściwościami JSON tak samo jak w przychodzących danych JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-320">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="74e18-321">Zauważ, że nazwa właściwości `ExtensionData` nie jest wyświetlana w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="74e18-321">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="74e18-322">Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.</span><span class="sxs-lookup"><span data-stu-id="74e18-322">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="74e18-323">Ignoruj wartość null podczas deserializacji</span><span class="sxs-lookup"><span data-stu-id="74e18-323">Ignore null when deserializing</span></span>

<span data-ttu-id="74e18-324">Domyślnie, jeśli właściwość w formacie JSON ma wartość null, odpowiadająca jej właściwość w obiekcie docelowym ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="74e18-324">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="74e18-325">W niektórych scenariuszach właściwość target może mieć wartość domyślną i nie ma potrzeby przesłonięcia wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="74e18-325">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="74e18-326">Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:</span><span class="sxs-lookup"><span data-stu-id="74e18-326">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="74e18-327">Załóżmy, że następujący kod JSON jest deserializowany:</span><span class="sxs-lookup"><span data-stu-id="74e18-327">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="74e18-328">Po deserializacji właściwość `Summary` obiektu `WeatherForecastWithDefault` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="74e18-328">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="74e18-329">Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na `true`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-329">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="74e18-330">W przypadku tej opcji Właściwość `Summary` obiektu `WeatherForecastWithDefault` jest wartością domyślną "Brak podsumowania" po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-330">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="74e18-331">Wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="74e18-331">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="74e18-332">Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki.</span><span class="sxs-lookup"><span data-stu-id="74e18-332">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="74e18-333">Aby uzyskać więcej informacji, zobacz artykuł [dotyczący problemu 40922 w przypadku typów wartości niedopuszczających wartości null](https://github.com/dotnet/corefx/issues/40922) w repozytorium dotnet/corefx w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="74e18-333">For more information, see [issue 40922 on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="74e18-334">Utf8JsonReader, Utf8JsonWriter i JsonDocument</span><span class="sxs-lookup"><span data-stu-id="74e18-334">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="74e18-335"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> jest wysoce wydajnym, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, Odczytaj z `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="74e18-335"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="74e18-336">`Utf8JsonReader` jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="74e18-336">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="74e18-337">Metoda <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> używa `Utf8JsonReader` w obszarze okładek.</span><span class="sxs-lookup"><span data-stu-id="74e18-337">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="74e18-338"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> to wysoce wydajny sposób pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy .NET, takich jak `String`, `Int32`i `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="74e18-338"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="74e18-339">Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="74e18-339">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="74e18-340">Metoda <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> używa `Utf8JsonWriter` w obszarze okładek.</span><span class="sxs-lookup"><span data-stu-id="74e18-340">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="74e18-341"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> zapewnia możliwość tworzenia Document Object Model tylko do odczytu (DOM) przy użyciu `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="74e18-341"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="74e18-342">DOM zapewnia losowy dostęp do danych w ładunku JSON.</span><span class="sxs-lookup"><span data-stu-id="74e18-342">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="74e18-343">Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem typu <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="74e18-343">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="74e18-344">Typ `JsonElement` zapewnia moduł wyliczający tablic i obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET.</span><span class="sxs-lookup"><span data-stu-id="74e18-344">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="74e18-345">`JsonDocument` uwidacznia Właściwość <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="74e18-345">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="74e18-346">W poniższych sekcjach pokazano, jak używać tych narzędzi do odczytywania i pisania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="74e18-346">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="74e18-347">Korzystanie z JsonDocument do uzyskiwania dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="74e18-347">Use JsonDocument for access to data</span></span>

<span data-ttu-id="74e18-348">Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.JsonDocument> do losowego dostępu do danych w ciągu JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-348">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="74e18-349">Powyższy kod:</span><span class="sxs-lookup"><span data-stu-id="74e18-349">The preceding code:</span></span>

* <span data-ttu-id="74e18-350">Przyjęto, że kod JSON do analizy znajduje się w ciągu o nazwie `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="74e18-350">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="74e18-351">Oblicza średnią ocenę dla obiektów w tablicy `Students`, która ma właściwość `Grade`.</span><span class="sxs-lookup"><span data-stu-id="74e18-351">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="74e18-352">Przypisuje domyślną ocenę 70 dla studentów, którzy nie posiadają klasy.</span><span class="sxs-lookup"><span data-stu-id="74e18-352">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="74e18-353">Zlicza uczniów przez zwiększenie zmiennej `count` przy każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="74e18-353">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="74e18-354">Alternatywą jest wywołanie <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="74e18-354">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="74e18-355">Oto przykład pliku JSON, który jest przetwarzany przez ten kod:</span><span class="sxs-lookup"><span data-stu-id="74e18-355">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="74e18-356">Użyj JsonDocument, aby zapisać kod JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-356">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="74e18-357">Poniższy przykład pokazuje, jak napisać kod JSON z <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="74e18-357">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="74e18-358">Powyższy kod:</span><span class="sxs-lookup"><span data-stu-id="74e18-358">The preceding code:</span></span>

* <span data-ttu-id="74e18-359">Odczytuje plik JSON, ładuje dane do `JsonDocument`i zapisuje sformatowany plik JSON w formacie.</span><span class="sxs-lookup"><span data-stu-id="74e18-359">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="74e18-360">Używa <xref:System.Text.Json.JsonDocumentOptions>, aby określić, że komentarze w wejściowym formacie JSON są dozwolone, ale ignorowane.</span><span class="sxs-lookup"><span data-stu-id="74e18-360">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="74e18-361">Po zakończeniu wywołuje <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> w składniku zapisywania.</span><span class="sxs-lookup"><span data-stu-id="74e18-361">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="74e18-362">Alternatywą jest umożliwienie składnika zapisywania AutoFlush, gdy zostanie on usunięty.</span><span class="sxs-lookup"><span data-stu-id="74e18-362">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="74e18-363">Oto przykład danych wejściowych JSON do przetworzenia przez przykładowy kod:</span><span class="sxs-lookup"><span data-stu-id="74e18-363">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="74e18-364">Wynikiem są następujące niedrukowane dane wyjściowe JSON:</span><span class="sxs-lookup"><span data-stu-id="74e18-364">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="74e18-365">Użyj Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="74e18-365">Use Utf8JsonWriter</span></span>

<span data-ttu-id="74e18-366">Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.Utf8JsonWriter>:</span><span class="sxs-lookup"><span data-stu-id="74e18-366">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="74e18-367">Użyj Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="74e18-367">Use Utf8JsonReader</span></span>

<span data-ttu-id="74e18-368">Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.Utf8JsonReader>:</span><span class="sxs-lookup"><span data-stu-id="74e18-368">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="74e18-369">Poprzedni kod założono, że zmienna `jsonUtf8` jest tablicą bajtów, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="74e18-369">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="74e18-370">Filtrowanie danych za pomocą Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="74e18-370">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="74e18-371">Poniższy przykład pokazuje, jak odczytywać plik synchronicznie i wyszukiwać wartość:</span><span class="sxs-lookup"><span data-stu-id="74e18-371">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="74e18-372">Powyższy kod:</span><span class="sxs-lookup"><span data-stu-id="74e18-372">The preceding code:</span></span>

* <span data-ttu-id="74e18-373">Przyjęto założenie, że plik jest zakodowany jako UTF-16 i transkoduje go do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="74e18-373">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="74e18-374">Plik zakodowany jako UTF-8 można odczytać bezpośrednio w `ReadOnlySpan<byte>`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="74e18-374">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="74e18-375">Przyjęto, że kod JSON zawiera tablicę obiektów, a każdy obiekt może zawierać właściwość "name" typu String.</span><span class="sxs-lookup"><span data-stu-id="74e18-375">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="74e18-376">Zlicza obiekty i `name` wartości właściwości, które kończą się na Uniwersytecie.</span><span class="sxs-lookup"><span data-stu-id="74e18-376">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="74e18-377">Oto przykład JSON, który może odczytać poprzedzający kod.</span><span class="sxs-lookup"><span data-stu-id="74e18-377">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="74e18-378">Otrzymany komunikat podsumowujący to "2 z 4 mają nazwy kończące się na" University ":</span><span class="sxs-lookup"><span data-stu-id="74e18-378">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="74e18-379">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="74e18-379">Additional resources</span></span>

* [<span data-ttu-id="74e18-380">System. Text. JSON — Omówienie</span><span class="sxs-lookup"><span data-stu-id="74e18-380">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="74e18-381">Dokumentacja interfejsu API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-381">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="74e18-382">Zapisuj niestandardowe konwertery dla elementu System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-382">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="74e18-383">Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="74e18-383">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="74e18-384">Problemy z usługą GitHub w repozytorium dotnet/corefx z etykietą JSON-funkcja-doc</span><span class="sxs-lookup"><span data-stu-id="74e18-384">GitHub issues in the dotnet/corefx repository labeled json-functionality-doc</span></span>](https://github.com/dotnet/corefx/labels/json-functionality-doc) 
