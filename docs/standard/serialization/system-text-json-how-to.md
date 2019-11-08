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
ms.openlocfilehash: f0245feb710f33d5fcea2a7125b8753ba6064018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740433"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="91273-102">Jak serializować i deserializować kod JSON w programie .NET</span><span class="sxs-lookup"><span data-stu-id="91273-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="91273-103">Dokumentacja serializacji JSON jest w przygotowaniu.</span><span class="sxs-lookup"><span data-stu-id="91273-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="91273-104">Ten artykuł nie obejmuje wszystkich scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="91273-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="91273-105">Aby uzyskać więcej informacji, należy zapoznać się z tematami [System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) w repozytorium dotnet/corefx w witrynie GitHub, w szczególności z etykietą [JSON-funkcja-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span><span class="sxs-lookup"><span data-stu-id="91273-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="91273-106">W tym artykule pokazano, jak używać przestrzeni nazw <xref:System.Text.Json> do serializacji i deserializacji do i z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="91273-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="91273-107">Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="91273-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="91273-108">Namespaces</span><span class="sxs-lookup"><span data-stu-id="91273-108">Namespaces</span></span>

<span data-ttu-id="91273-109">Przestrzeń nazw <xref:System.Text.Json> zawiera wszystkie punkty wejścia i typy główne.</span><span class="sxs-lookup"><span data-stu-id="91273-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="91273-110">Przestrzeń nazw <xref:System.Text.Json.Serialization> zawiera atrybuty i interfejsy API dla zaawansowanych scenariuszy i dostosowań specyficznych dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="91273-111">Przykłady kodu przedstawione w tym artykule wymagają `using` dyrektyw dla jednej lub obu tych przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="91273-111">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="91273-112">Atrybuty z przestrzeni nazw <xref:System.Runtime.Serialization> nie są obecnie obsługiwane w `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="91273-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="91273-113">Pisanie obiektów .NET w formacie JSON (Serializacja)</span><span class="sxs-lookup"><span data-stu-id="91273-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="91273-114">Aby zapisać dane JSON do ciągu lub do pliku, wywołaj metodę <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91273-114">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="91273-115">Poniższy przykład tworzy kod JSON jako ciąg:</span><span class="sxs-lookup"><span data-stu-id="91273-115">The following example creates JSON as a string:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="91273-116">Poniższy przykład używa kodu synchronicznego do utworzenia pliku JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-116">The following example uses synchronous code to create a JSON file:</span></span>

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

<span data-ttu-id="91273-117">W poniższym przykładzie jest tworzony plik JSON przy użyciu kodu asynchronicznego:</span><span class="sxs-lookup"><span data-stu-id="91273-117">The following example uses asynchronous code to create a JSON file:</span></span>

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

<span data-ttu-id="91273-118">Powyższe przykłady używają wnioskowania typu dla serializowanego typu.</span><span class="sxs-lookup"><span data-stu-id="91273-118">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="91273-119">Przeciążenie `Serialize()` przyjmuje parametr typu ogólnego:</span><span class="sxs-lookup"><span data-stu-id="91273-119">An overload of `Serialize()` takes a generic type parameter:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a><span data-ttu-id="91273-120">Przykład serializacji</span><span class="sxs-lookup"><span data-stu-id="91273-120">Serialization example</span></span>

<span data-ttu-id="91273-121">Oto przykładowy typ zawierający kolekcje i klasy zagnieżdżone:</span><span class="sxs-lookup"><span data-stu-id="91273-121">Here's an example type that contains collections and nested classes:</span></span>

```csharp
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public IList<DateTimeOffset> DatesAvailable { get; set;}
    public Dictionary<string, HighLowTemperatures> TemperatureRanges { get; set; }
    public string [] SummaryWords { get; set; }
}

public class HighLowTemperatures
{
    public Temperature High { get; set; }
    public Temperature Low { get; set; }
}

public class Temperature
{
    public int DegreesCelsius { get; set; }
}
```

<span data-ttu-id="91273-122">Dane wyjściowe JSON serializowania wystąpienia poprzedniego typu wyglądają podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="91273-122">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="91273-123">Dane wyjściowe JSON domyślnie są zminimalizowanego:</span><span class="sxs-lookup"><span data-stu-id="91273-123">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="91273-124">W poniższym przykładzie przedstawiono ten sam kod JSON, sformatowany (to jest całkiem wydruk z odstępami i wcięciami):</span><span class="sxs-lookup"><span data-stu-id="91273-124">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": {
        "DegreesCelsius": 20
      },
      "Low": {
        "DegreesCelsius": -10
      }
    },
    "Hot": {
      "High": {
        "DegreesCelsius": 60
      },
      "Low": {
        "DegreesCelsius": 20
      }
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a><span data-ttu-id="91273-125">Serializacja do UTF-8</span><span class="sxs-lookup"><span data-stu-id="91273-125">Serialize to UTF-8</span></span>

<span data-ttu-id="91273-126">Aby serializować do UTF-8, wywołaj metodę <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="91273-126">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="91273-127">Dostępne jest również Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A>, które pobiera <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="91273-127">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="91273-128">Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach.</span><span class="sxs-lookup"><span data-stu-id="91273-128">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="91273-129">Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="91273-129">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="91273-130">Zachowanie serializacji</span><span class="sxs-lookup"><span data-stu-id="91273-130">Serialization behavior</span></span>

* <span data-ttu-id="91273-131">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="91273-131">By default, all public properties are serialized.</span></span> <span data-ttu-id="91273-132">Można [określić właściwości do wykluczenia](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="91273-132">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="91273-133">[Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem kodu HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="91273-133">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="91273-134">Domyślnie JSON jest zminimalizowanego.</span><span class="sxs-lookup"><span data-stu-id="91273-134">By default, JSON is minified.</span></span> <span data-ttu-id="91273-135">Można tu [wydrukować kod JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="91273-135">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="91273-136">Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET.</span><span class="sxs-lookup"><span data-stu-id="91273-136">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="91273-137">Można [dostosować wielkość liter w nazwach JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="91273-137">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="91273-138">Wykryto odwołania cykliczne i zostały zgłoszone wyjątki.</span><span class="sxs-lookup"><span data-stu-id="91273-138">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="91273-139">Aby uzyskać więcej informacji, zobacz [problem dotyczący odwołań cyklicznych](https://github.com/dotnet/corefx/issues/38579) w repozytorium dotnet/corefx w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="91273-139">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="91273-140">Obecnie pola są wykluczone.</span><span class="sxs-lookup"><span data-stu-id="91273-140">Currently, fields are excluded.</span></span>

<span data-ttu-id="91273-141">Obsługiwane typy to:</span><span class="sxs-lookup"><span data-stu-id="91273-141">Supported types include:</span></span>

* <span data-ttu-id="91273-142">Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="91273-142">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="91273-143">Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="91273-143">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="91273-144">Tablice jednowymiarowe i nieregularne (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="91273-144">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="91273-145">`Dictionary<string,TValue>` gdzie `TValue` jest `object`, `JsonElement` lub POCO.</span><span class="sxs-lookup"><span data-stu-id="91273-145">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="91273-146">Kolekcje z następujących przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="91273-146">Collections from the following namespaces.</span></span> <span data-ttu-id="91273-147">Aby uzyskać więcej informacji, zobacz [problem związany z obsługą kolekcji](https://github.com/dotnet/corefx/issues/36643) w repozytorium dotnet/corefx w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="91273-147">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="91273-148">Można [zaimplementować niestandardowe konwertery](system-text-json-converters-how-to.md) do obsługi dodatkowych typów lub udostępniać funkcje, które nie są obsługiwane przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="91273-148">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="91273-149">Jak odczytywać dane JSON do obiektów .NET (deserializacji)</span><span class="sxs-lookup"><span data-stu-id="91273-149">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="91273-150">Aby zdeserializować z ciągu lub pliku, wywołaj metodę <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91273-150">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="91273-151">Poniższy przykład odczytuje kod JSON z ciągu:</span><span class="sxs-lookup"><span data-stu-id="91273-151">The following example reads JSON from a string:</span></span>

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="91273-152">Aby zdeserializować z pliku przy użyciu kodu synchronicznego, Odczytaj plik do ciągu, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-152">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="91273-153">Aby zdeserializować z pliku przy użyciu kodu asynchronicznego, wywołaj metodę <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:</span><span class="sxs-lookup"><span data-stu-id="91273-153">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

<span data-ttu-id="91273-154">Przykładowy typ i odpowiedni kod JSON można znaleźć w sekcji [przykład serializacji](#serialization-example) .</span><span class="sxs-lookup"><span data-stu-id="91273-154">For an example type and corresponding JSON, see the [Serialization example](#serialization-example) section.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="91273-155">Deserializacja z UTF-8</span><span class="sxs-lookup"><span data-stu-id="91273-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="91273-156">Aby zdeserializować z UTF-8, wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>, które pobiera `Utf8JsonReader` lub `ReadOnlySpan<byte>`, jak pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="91273-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="91273-157">W przykładach założono, że kod JSON znajduje się w tablicy bajtów o nazwie jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="91273-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="91273-158">Zachowanie deserializacji</span><span class="sxs-lookup"><span data-stu-id="91273-158">Deserialization behavior</span></span>

* <span data-ttu-id="91273-159">Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="91273-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="91273-160">Można [określić wielkość liter](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="91273-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="91273-161">Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="91273-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="91273-162">Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="91273-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="91273-163">Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="91273-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="91273-164">Aby uzyskać więcej informacji, zobacz [problem z obsługą usługi GitHub dla niemodyfikowalnych obiektów](https://github.com/dotnet/corefx/issues/38569) i [problem związany z obsługą właściwości tylko do odczytu](https://github.com/dotnet/corefx/issues/38163) w repozytorium dotnet/corefx w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="91273-164">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="91273-165">Domyślnie wyliczenia są obsługiwane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="91273-165">By default, enums are supported as numbers.</span></span> <span data-ttu-id="91273-166">[Nazwy wyliczenia można serializować jako ciągi](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="91273-166">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="91273-167">Pola nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="91273-167">Fields aren't supported.</span></span>
* <span data-ttu-id="91273-168">Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON.</span><span class="sxs-lookup"><span data-stu-id="91273-168">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="91273-169">Można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="91273-169">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="91273-170">[Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.</span><span class="sxs-lookup"><span data-stu-id="91273-170">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="91273-171">[Konwertery niestandardowe można zaimplementować](system-text-json-converters-how-to.md) w celu zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.</span><span class="sxs-lookup"><span data-stu-id="91273-171">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="91273-172">Serializacja do sformatowanego pliku JSON</span><span class="sxs-lookup"><span data-stu-id="91273-172">Serialize to formatted JSON</span></span>

<span data-ttu-id="91273-173">Aby wydrukować dane wyjściowe JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="91273-173">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="91273-174">Oto przykład typu do serializacji i całkiem wydrukowanych danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-174">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="91273-175">Dostosowywanie nazw i wartości JSON</span><span class="sxs-lookup"><span data-stu-id="91273-175">Customize JSON names and values</span></span>

<span data-ttu-id="91273-176">Domyślnie nazwy właściwości i klucze słownika nie są zmieniane w danych wyjściowych JSON, włącznie z wielkością liter.</span><span class="sxs-lookup"><span data-stu-id="91273-176">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="91273-177">Wartości wyliczeniowe są reprezentowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="91273-177">Enum values are represented as numbers.</span></span> <span data-ttu-id="91273-178">W tej sekcji wyjaśniono, jak:</span><span class="sxs-lookup"><span data-stu-id="91273-178">This section explains how to:</span></span>

* <span data-ttu-id="91273-179">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="91273-179">Customize individual property names</span></span>
* <span data-ttu-id="91273-180">Konwertuj wszystkie nazwy właściwości na notacji CamelCase przypadku</span><span class="sxs-lookup"><span data-stu-id="91273-180">Convert all property names to camel case</span></span>
* <span data-ttu-id="91273-181">Implementowanie zasad nazewnictwa właściwości niestandardowych</span><span class="sxs-lookup"><span data-stu-id="91273-181">Implement a custom property naming policy</span></span>
* <span data-ttu-id="91273-182">Konwertuj klucze słownika na notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="91273-182">Convert dictionary keys to camel case</span></span>
* <span data-ttu-id="91273-183">Konwertuj wyliczenia na ciągi i notacji CamelCase wielkość liter</span><span class="sxs-lookup"><span data-stu-id="91273-183">Convert enums to strings and camel case</span></span> 

<span data-ttu-id="91273-184">W przypadku innych scenariuszy, które wymagają specjalnej obsługi nazw i wartości właściwości JSON, można [zaimplementować konwertery niestandardowe](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="91273-184">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="91273-185">Dostosowywanie poszczególnych nazw właściwości</span><span class="sxs-lookup"><span data-stu-id="91273-185">Customize individual property names</span></span>

<span data-ttu-id="91273-186">Aby ustawić nazwę poszczególnych właściwości, Użyj atrybutu [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="91273-186">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="91273-187">Oto przykład typu do serializacji i powstającego JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-187">Here's an example type to serialize and resulting JSON:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="91273-188">Nazwa właściwości ustawiona przez ten atrybut:</span><span class="sxs-lookup"><span data-stu-id="91273-188">The property name set by this attribute:</span></span>

* <span data-ttu-id="91273-189">Stosuje się w obu kierunkach dla serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-189">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="91273-190">Ma pierwszeństwo przed zasadami nazewnictwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="91273-190">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="91273-191">Użyj notacji CamelCase przypadku dla wszystkich nazw właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="91273-191">Use camel case for all JSON property names</span></span>

<span data-ttu-id="91273-192">Aby użyć notacji CamelCase przypadku dla wszystkich nazw właściwości JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-192">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="91273-193">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-193">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="91273-194">Zasady nazewnictwa właściwości przypadku notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="91273-194">The camel case property naming policy:</span></span>

* <span data-ttu-id="91273-195">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-195">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="91273-196">Jest zastępowany przez atrybuty `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="91273-196">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="91273-197">Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie notacji CamelCase wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="91273-197">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="91273-198">Użyj niestandardowych zasad nazewnictwa właściwości JSON</span><span class="sxs-lookup"><span data-stu-id="91273-198">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="91273-199">Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę pochodzącą z <xref:System.Text.Json.JsonNamingPolicy> i Zastąp metodę <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-199">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="91273-200">Następnie ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na wystąpienie klasy zasad nazewnictwa:</span><span class="sxs-lookup"><span data-stu-id="91273-200">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="91273-201">Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-201">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATUREC": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="91273-202">Zasady nazewnictwa właściwości JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-202">The JSON property naming policy:</span></span>

* <span data-ttu-id="91273-203">Dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-203">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="91273-204">Jest zastępowany przez atrybuty `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="91273-204">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="91273-205">Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest wielką literą.</span><span class="sxs-lookup"><span data-stu-id="91273-205">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="91273-206">Klucze słownika przypadku notacji CamelCase</span><span class="sxs-lookup"><span data-stu-id="91273-206">Camel case dictionary keys</span></span>

<span data-ttu-id="91273-207">Jeśli właściwość obiektu, który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>`, klucze `string` można przekonwertować na notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="91273-207">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="91273-208">W tym celu ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-208">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="91273-209">Serializacja obiektu przy użyciu słownika o nazwie `TemperatureRanges`, który ma pary klucz-wartość, `"ColdMinTemp", 20` i `"HotMinTemp", 40` spowoduje to wyjście JSON podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="91273-209">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="91273-210">Zasady nazewnictwa przypadków notacji CamelCase dla kluczy słownika mają zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-210">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="91273-211">W przypadku deserializacji słownika klucze będą zgodne z plikiem JSON nawet wtedy, gdy dla `DictionaryKeyPolicy`określono `JsonNamingPolicy.CamelCase`.</span><span class="sxs-lookup"><span data-stu-id="91273-211">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="91273-212">Wyliczenia jako ciągi</span><span class="sxs-lookup"><span data-stu-id="91273-212">Enums as strings</span></span>

<span data-ttu-id="91273-213">Domyślnie wyliczenia są serializowane jako liczby.</span><span class="sxs-lookup"><span data-stu-id="91273-213">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="91273-214">Aby serializować nazwy wyliczenia jako ciągi, użyj <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="91273-214">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="91273-215">Załóżmy na przykład, że trzeba serializować następujące klasy, które mają Wyliczenie:</span><span class="sxs-lookup"><span data-stu-id="91273-215">For example, suppose you need to serialize the following class that has an enum:</span></span>

```csharp
class WeatherForecastWithEnum
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public Summary Summary { get; set; }
}

public enum Summary
{
    Cold, Cool, Warm, Hot
}
```

<span data-ttu-id="91273-216">Jeśli podsumowanie jest `Hot`, domyślnie serializowany kod JSON ma wartość liczbową 3:</span><span class="sxs-lookup"><span data-stu-id="91273-216">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

<span data-ttu-id="91273-217">Następujący przykładowy kod serializować nazwy wyliczenia, a następnie konwertuje je na notacji CamelCase:</span><span class="sxs-lookup"><span data-stu-id="91273-217">The following sample code serializes the enum names instead, and converts them to camel case:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

<span data-ttu-id="91273-218">Wynikowy kod JSON wygląda podobnie do poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="91273-218">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="91273-219">Obsługa wyliczeń jako ciągów dotyczy również deserializacji, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-219">The support for enums as strings applies to deserialization also, as shown in the following example:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="91273-220">Wyklucz właściwości z serializacji</span><span class="sxs-lookup"><span data-stu-id="91273-220">Exclude properties from serialization</span></span>

<span data-ttu-id="91273-221">Domyślnie wszystkie właściwości publiczne są serializowane.</span><span class="sxs-lookup"><span data-stu-id="91273-221">By default, all public properties are serialized.</span></span> <span data-ttu-id="91273-222">Jeśli nie chcesz, aby niektóre z nich pojawiały się w danych wyjściowych JSON, masz kilka opcji.</span><span class="sxs-lookup"><span data-stu-id="91273-222">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="91273-223">W tej sekcji wyjaśniono, jak wykluczyć:</span><span class="sxs-lookup"><span data-stu-id="91273-223">This section explains how to exclude:</span></span>

* <span data-ttu-id="91273-224">Poszczególne właściwości</span><span class="sxs-lookup"><span data-stu-id="91273-224">Individual properties</span></span>
* <span data-ttu-id="91273-225">Wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="91273-225">All read-only properties</span></span>
* <span data-ttu-id="91273-226">Wszystkie właściwości o wartości null</span><span class="sxs-lookup"><span data-stu-id="91273-226">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="91273-227">Wyklucz pojedyncze właściwości</span><span class="sxs-lookup"><span data-stu-id="91273-227">Exclude individual properties</span></span>

<span data-ttu-id="91273-228">Aby zignorować poszczególne właściwości, Użyj atrybutu [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="91273-228">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="91273-229">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-229">Here's an example type to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonIgnore]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="91273-230">Wyklucz wszystkie właściwości tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="91273-230">Exclude all read-only properties</span></span>

<span data-ttu-id="91273-231">Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej.</span><span class="sxs-lookup"><span data-stu-id="91273-231">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="91273-232">Aby wykluczyć wszystkie właściwości tylko do odczytu, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-232">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="91273-233">Oto przykład typu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-233">Here's an example type to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public int WindSpeed { get; private set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="91273-234">Ta opcja ma zastosowanie tylko do serializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-234">This option applies only to serialization.</span></span> <span data-ttu-id="91273-235">Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane.</span><span class="sxs-lookup"><span data-stu-id="91273-235">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="91273-236">Wyklucz wszystkie właściwości wartości null</span><span class="sxs-lookup"><span data-stu-id="91273-236">Exclude all null value properties</span></span>

<span data-ttu-id="91273-237">Aby wykluczyć wszystkie właściwości wartości null, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na `true`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-237">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="91273-238">Oto przykład obiektu do serializacji i danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-238">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="91273-239">Właściwość</span><span class="sxs-lookup"><span data-stu-id="91273-239">Property</span></span> |<span data-ttu-id="91273-240">Wartość</span><span class="sxs-lookup"><span data-stu-id="91273-240">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="91273-241">Data</span><span class="sxs-lookup"><span data-stu-id="91273-241">Date</span></span>    | <span data-ttu-id="91273-242">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="91273-242">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="91273-243">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="91273-243">TemperatureC</span></span>| <span data-ttu-id="91273-244">6,25</span><span class="sxs-lookup"><span data-stu-id="91273-244">25</span></span> |
| <span data-ttu-id="91273-245">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="91273-245">Summary</span></span>| <span data-ttu-id="91273-246">wartość null</span><span class="sxs-lookup"><span data-stu-id="91273-246">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="91273-247">To ustawienie dotyczy serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-247">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="91273-248">Aby uzyskać informacje o jego wpływie na deserializacji, zobacz [Ignore null podczas deserializacji](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="91273-248">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="91273-249">Dostosuj kodowanie znaków</span><span class="sxs-lookup"><span data-stu-id="91273-249">Customize character encoding</span></span>

<span data-ttu-id="91273-250">Domyślnie serializator wyprowadza wszystkie znaki nienależące do zestawu znaków ASCII.</span><span class="sxs-lookup"><span data-stu-id="91273-250">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="91273-251">Oznacza to, że zastępuje je `\uxxxx` gdzie `xxxxx` jest kodem Unicode znaku.</span><span class="sxs-lookup"><span data-stu-id="91273-251">That is, it replaces them with `\uxxxx` where `xxxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="91273-252">Na przykład, jeśli właściwość `Summary` jest ustawiona na wartość cyrylicy жарко, obiekt `WeatherForecast` zostanie Zserializowany, jak pokazano w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-252">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="91273-253">Serializowanie zestawów znaków języka</span><span class="sxs-lookup"><span data-stu-id="91273-253">Serialize language character sets</span></span>

<span data-ttu-id="91273-254">Aby serializować zestawy znaków w jednym lub kilku językach, określ [zakresy Unicode](xref:System.Text.Unicode.UnicodeRanges) podczas tworzenia wystąpienia <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-254">To serialize the character set(s) of one or more languages, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(UnicodeRanges.Cyrillic, UnicodeRanges.GreekExtended)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="91273-255">Ten kod serializacji znaki cyrylicy i greckich.</span><span class="sxs-lookup"><span data-stu-id="91273-255">This code serializes Cyrillic and Greek characters.</span></span> <span data-ttu-id="91273-256">Znaki cyrylicy są wyświetlane w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-256">Cyrillic characters are shown in the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

<span data-ttu-id="91273-257">Aby określić wszystkie języki, użyj <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91273-257">To specify all languages, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="91273-258">Serializacja określonych znaków</span><span class="sxs-lookup"><span data-stu-id="91273-258">Serialize specific characters</span></span>

<span data-ttu-id="91273-259">Alternatywą jest określenie pojedynczych znaków, które mają być dozwolone, bez konieczności ucieczki.</span><span class="sxs-lookup"><span data-stu-id="91273-259">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="91273-260">Poniższy przykład serializacji tylko dwa pierwsze znaki жарко:</span><span class="sxs-lookup"><span data-stu-id="91273-260">The following example serializes only the first two characters of жарко:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var encoderSettings = new TextEncoderSettings();
encoderSettings.AllowCharacters('\u0436', '\u0430');
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(encoderSettings)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="91273-261">Oto przykład kodu JSON utworzonego przez poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="91273-261">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="91273-262">Serializować wszystkie znaki</span><span class="sxs-lookup"><span data-stu-id="91273-262">Serialize all characters</span></span>

<span data-ttu-id="91273-263">Aby zminimalizować liczbę ucieczki, można użyć <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-263">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
```

```csharp
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.UnsafeRelaxedJsonEscaping
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

> [!CAUTION]
> <span data-ttu-id="91273-264">W przeciwieństwie do domyślnego kodera, koder `UnsafeRelaxedJsonEscaping`:</span><span class="sxs-lookup"><span data-stu-id="91273-264">Unlike the default encoder, the `UnsafeRelaxedJsonEscaping` encoder:</span></span>
>
> * <span data-ttu-id="91273-265">Nie ucieczki znaków w języku HTML, takich jak `<`, `>`, `&`i `'`.</span><span class="sxs-lookup"><span data-stu-id="91273-265">Doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="91273-266">Nie oferuje żadnej dodatkowej ochrony przed atakami typu XSS lub ujawnienie informacji, takich jak te, które mogą wynikać z klienta i serwera bez zgody na *zestaw znaków*.</span><span class="sxs-lookup"><span data-stu-id="91273-266">Doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
> * <span data-ttu-id="91273-267">Jest bardziej ograniczająca niż domyślny koder, na którym znaki mogą być przekazywane przez niezmienione.</span><span class="sxs-lookup"><span data-stu-id="91273-267">Is more permissive than the default encoder on which characters are allowed to pass through unescaped.</span></span>
>
> <span data-ttu-id="91273-268">Używaj niebezpiecznego kodera tylko wtedy, gdy wiadomo, że klient będzie interpretować otrzymany ładunek jako zakodowany w formacie JSON UTF-8.</span><span class="sxs-lookup"><span data-stu-id="91273-268">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="91273-269">Można na przykład użyć go, jeśli serwer wysyła nagłówek odpowiedzi `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="91273-269">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="91273-270">Nigdy nie Zezwalaj na emitowanie nieprzetworzonych danych wyjściowych `UnsafeRelaxedJsonEscaping` do strony HTML lub `<script>` elementu.</span><span class="sxs-lookup"><span data-stu-id="91273-270">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="91273-271">Serializowanie właściwości klas pochodnych</span><span class="sxs-lookup"><span data-stu-id="91273-271">Serialize properties of derived classes</span></span>

<span data-ttu-id="91273-272">Serializacja polimorficzna nie jest obsługiwana w przypadku określenia w czasie kompilacji typu, który ma być serializowany.</span><span class="sxs-lookup"><span data-stu-id="91273-272">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="91273-273">Załóżmy na przykład, że masz klasę `WeatherForecast` i klasę pochodną `WeatherForecastWithWind`:</span><span class="sxs-lookup"><span data-stu-id="91273-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
class WeatherForecastWithWind : WeatherForecast
{
    public int WindSpeed { get; set; }
}
```

<span data-ttu-id="91273-274">I Załóżmy, że argument typu metody `Serialize` w czasie kompilacji jest `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="91273-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="91273-275">W tym scenariuszu Właściwość `WindSpeed` nie jest serializowana, nawet jeśli obiekt `weatherForecast` jest w rzeczywistości obiektem `WeatherForecastWithWind`.</span><span class="sxs-lookup"><span data-stu-id="91273-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="91273-276">Tylko właściwości klasy bazowej są serializowane:</span><span class="sxs-lookup"><span data-stu-id="91273-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="91273-277">Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="91273-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="91273-278">Aby serializować właściwości typu pochodnego, należy użyć jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="91273-278">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="91273-279">Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A>, które pozwala określić typ w czasie wykonywania:</span><span class="sxs-lookup"><span data-stu-id="91273-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="91273-280">Zadeklaruj obiekt do serializacji jako `object`.</span><span class="sxs-lookup"><span data-stu-id="91273-280">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="91273-281">W poprzednim przykładowym scenariuszu oba podejścia powodują, że właściwość `WindSpeed` ma zostać uwzględniona w danych wyjściowych JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="91273-282">Aby uzyskać informacje na temat deserializacji polimorficznej, zobacz [Obsługa deserializacji polimorficznej](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="91273-282">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="91273-283">Zezwalaj na komentarze i końcowe przecinki</span><span class="sxs-lookup"><span data-stu-id="91273-283">Allow comments and trailing commas</span></span>

<span data-ttu-id="91273-284">Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON.</span><span class="sxs-lookup"><span data-stu-id="91273-284">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="91273-285">Aby zezwolić na komentarze w formacie JSON, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="91273-285">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="91273-286">I aby zezwolić na końcowe przecinki, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="91273-286">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="91273-287">Poniższy przykład pokazuje, jak:</span><span class="sxs-lookup"><span data-stu-id="91273-287">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="91273-288">Oto przykładowy kod JSON z komentarzami i końcowym przecinkiem:</span><span class="sxs-lookup"><span data-stu-id="91273-288">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="91273-289">Dopasowanie właściwości bez uwzględniania wielkości liter</span><span class="sxs-lookup"><span data-stu-id="91273-289">Case-insensitive property matching</span></span>

<span data-ttu-id="91273-290">Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="91273-290">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="91273-291">Aby zmienić to zachowanie, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="91273-291">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="91273-292">Oto przykład JSON z nazwami właściwości przypadku notacji CamelCase.</span><span class="sxs-lookup"><span data-stu-id="91273-292">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="91273-293">Można ją zdeserializować do następującego typu, który ma nazwy właściwości przypadku języka Pascal.</span><span class="sxs-lookup"><span data-stu-id="91273-293">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
}
```

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="91273-294">Obsługa przepełnienia kodu JSON</span><span class="sxs-lookup"><span data-stu-id="91273-294">Handle overflow JSON</span></span>

<span data-ttu-id="91273-295">Podczas deserializacji można odbierać dane w formacie JSON, które nie są reprezentowane przez właściwości typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="91273-295">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="91273-296">Załóżmy na przykład, że typ docelowy to:</span><span class="sxs-lookup"><span data-stu-id="91273-296">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="91273-297">I kod JSON do deserializacji jest następujący:</span><span class="sxs-lookup"><span data-stu-id="91273-297">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
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

<span data-ttu-id="91273-298">W przypadku deserializacji kodu JSON pokazanego w pokazanym typie właściwości `DatesAvailable` i `SummaryWords` mają wartość Nowhere i są tracone.</span><span class="sxs-lookup"><span data-stu-id="91273-298">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="91273-299">Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="91273-299">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonExtensionData]
    public Dictionary<string, object> ExtensionData { get; set; }
}
```

<span data-ttu-id="91273-300">Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie przykładowym dodatkowe dane staną się parami klucz-wartość właściwości `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="91273-300">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="91273-301">Właściwość</span><span class="sxs-lookup"><span data-stu-id="91273-301">Property</span></span> |<span data-ttu-id="91273-302">Wartość</span><span class="sxs-lookup"><span data-stu-id="91273-302">Value</span></span>  |<span data-ttu-id="91273-303">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91273-303">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="91273-304">Data</span><span class="sxs-lookup"><span data-stu-id="91273-304">Date</span></span>    | <span data-ttu-id="91273-305">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="91273-305">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="91273-306">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="91273-306">TemperatureC</span></span>| <span data-ttu-id="91273-307">0</span><span class="sxs-lookup"><span data-stu-id="91273-307">0</span></span> | <span data-ttu-id="91273-308">Niezgodność z wielkością liter (`temperatureC` w formacie JSON), więc właściwość nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="91273-308">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="91273-309">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="91273-309">Summary</span></span> | <span data-ttu-id="91273-310">Ręczne</span><span class="sxs-lookup"><span data-stu-id="91273-310">Hot</span></span> ||
| <span data-ttu-id="91273-311">ExtensionData —</span><span class="sxs-lookup"><span data-stu-id="91273-311">ExtensionData</span></span> | <span data-ttu-id="91273-312">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="91273-312">temperatureC: 25</span></span> |<span data-ttu-id="91273-313">Ponieważ przypadek nie jest zgodny, ta właściwość JSON jest dodatkową i jest parą klucz-wartość w słowniku.</span><span class="sxs-lookup"><span data-stu-id="91273-313">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="91273-314">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="91273-314">DatesAvailable:</span></span><br>  <span data-ttu-id="91273-315">8/1/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="91273-315">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="91273-316">8/2/2019 12:00:00 AM – 07:00</span><span class="sxs-lookup"><span data-stu-id="91273-316">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="91273-317">Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="91273-317">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="91273-318">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="91273-318">SummaryWords:</span></span><br><span data-ttu-id="91273-319">Ochłodzenia</span><span class="sxs-lookup"><span data-stu-id="91273-319">Cool</span></span><br><span data-ttu-id="91273-320">Wiatr</span><span class="sxs-lookup"><span data-stu-id="91273-320">Windy</span></span><br><span data-ttu-id="91273-321">Humid</span><span class="sxs-lookup"><span data-stu-id="91273-321">Humid</span></span> |<span data-ttu-id="91273-322">Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="91273-322">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="91273-323">Gdy obiekt docelowy jest serializowany, pary wartości klucza danych rozszerzenia stają się właściwościami JSON tak samo jak w przychodzących danych JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-323">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 0,
  "Summary": "Hot",
  "temperatureC": 25,
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

<span data-ttu-id="91273-324">Zauważ, że nazwa właściwości `ExtensionData` nie występuje w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="91273-324">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="91273-325">Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.</span><span class="sxs-lookup"><span data-stu-id="91273-325">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="91273-326">Ignoruj wartość null podczas deserializacji</span><span class="sxs-lookup"><span data-stu-id="91273-326">Ignore null when deserializing</span></span>

<span data-ttu-id="91273-327">Domyślnie, jeśli właściwość w formacie JSON ma wartość null, odpowiadająca jej właściwość w obiekcie docelowym ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="91273-327">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="91273-328">W niektórych scenariuszach właściwość target może mieć wartość domyślną i nie ma potrzeby przesłonięcia wartości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="91273-328">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="91273-329">Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:</span><span class="sxs-lookup"><span data-stu-id="91273-329">For example, suppose the following code represents your target object:</span></span>

```csharp
class WeatherForecastWithDefault
{
    public WeatherForecastWithDefault()
    {
        Summary = "No summary";
    }
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="91273-330">Załóżmy, że następujący kod JSON jest deserializowany:</span><span class="sxs-lookup"><span data-stu-id="91273-330">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

<span data-ttu-id="91273-331">Po deserializacji właściwość `Summary` obiektu `WeatherForecastWithDefault` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="91273-331">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="91273-332">Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na `true`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="91273-332">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

<span data-ttu-id="91273-333">W przypadku tej opcji Właściwość `Summary` obiektu `WeatherForecastWithDefault` jest wartością domyślną "Brak podsumowania" po deserializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-333">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="91273-334">Wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="91273-334">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="91273-335">Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki.</span><span class="sxs-lookup"><span data-stu-id="91273-335">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="91273-336">Aby uzyskać więcej informacji, zobacz [problem związany z typami wartości niedopuszczających wartości null](https://github.com/dotnet/corefx/issues/40922) w repozytorium dotnet/corefx w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="91273-336">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="91273-337">Utf8JsonReader, Utf8JsonWriter i JsonDocument</span><span class="sxs-lookup"><span data-stu-id="91273-337">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="91273-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> jest wysoce wydajnym, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, Odczytaj z `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="91273-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="91273-339">`Utf8JsonReader` jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="91273-339">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="91273-340">Metoda <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> używa `Utf8JsonReader` w obszarze okładek.</span><span class="sxs-lookup"><span data-stu-id="91273-340">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="91273-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> to wysoce wydajny sposób pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy .NET, takich jak `String`, `Int32`i `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="91273-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="91273-342">Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="91273-342">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="91273-343">Metoda <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> używa `Utf8JsonWriter` w obszarze okładek.</span><span class="sxs-lookup"><span data-stu-id="91273-343">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="91273-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> zapewnia możliwość tworzenia Document Object Model tylko do odczytu (DOM) przy użyciu `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="91273-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="91273-345">DOM zapewnia losowy dostęp do danych w ładunku JSON.</span><span class="sxs-lookup"><span data-stu-id="91273-345">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="91273-346">Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem typu <xref:System.Text.Json.JsonElement>.</span><span class="sxs-lookup"><span data-stu-id="91273-346">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="91273-347">`JsonElement` zapewnia moduł wyliczający tablic i obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET.</span><span class="sxs-lookup"><span data-stu-id="91273-347">The `JsonElement` provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="91273-348">`JsonDocument` uwidacznia Właściwość <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="91273-348">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="91273-349">W poniższych sekcjach pokazano, jak używać tych narzędzi do odczytywania i pisania danych JSON.</span><span class="sxs-lookup"><span data-stu-id="91273-349">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="91273-350">Korzystanie z JsonDocument do uzyskiwania dostępu do danych</span><span class="sxs-lookup"><span data-stu-id="91273-350">Use JsonDocument for access to data</span></span>

<span data-ttu-id="91273-351">Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.JsonDocument> na potrzeby losowego dostępu do danych:</span><span class="sxs-lookup"><span data-stu-id="91273-351">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data:</span></span>

```csharp
double sum = 0;
int count = 0;

using (JsonDocument document = JsonDocument.Parse(jsonString))
{
    JsonElement root = document.RootElement;
    JsonElement studentsElement = root.GetProperty("Students");
    foreach (JsonElement student in studentsElement.EnumerateArray())
    {
        if (student.TryGetProperty("Grade", out JsonElement gradeElement))
        {
            sum += gradeElement.GetDouble();
        }
        else
        {
            sum += 70;
        }
        count++;
    }
}

double average = sum / count;
Console.WriteLine($"Average grade: {average}");
```

<span data-ttu-id="91273-352">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="91273-352">The preceding code:</span></span>

* <span data-ttu-id="91273-353">Przyjęto, że kod JSON do analizy znajduje się w ciągu o nazwie `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="91273-353">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="91273-354">Oblicza średnią ocenę dla obiektów w tablicy `Students`, która ma właściwość `Grade`.</span><span class="sxs-lookup"><span data-stu-id="91273-354">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="91273-355">Przypisuje domyślną ocenę 70 dla studentów, którzy nie posiadają klasy.</span><span class="sxs-lookup"><span data-stu-id="91273-355">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="91273-356">Zlicza uczniów przez zwiększenie zmiennej `count` przy każdej iteracji.</span><span class="sxs-lookup"><span data-stu-id="91273-356">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="91273-357">Alternatywą jest wywołanie <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:</span><span class="sxs-lookup"><span data-stu-id="91273-357">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:</span></span>

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

<span data-ttu-id="91273-358">Oto przykład pliku JSON, który jest przetwarzany przez ten kod:</span><span class="sxs-lookup"><span data-stu-id="91273-358">Here's an example of the JSON that this code processes:</span></span>

```json
{
  "Class Name": "Science",
  "Teacher's Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="91273-359">Użyj JsonDocument, aby zapisać kod JSON</span><span class="sxs-lookup"><span data-stu-id="91273-359">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="91273-360">Poniższy przykład pokazuje, jak napisać kod JSON z <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="91273-360">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);

var writerOptions = new JsonWriterOptions { Indented = true };
var documentOptions = new JsonDocumentOptions { CommentHandling = JsonCommentHandling.Skip };

using (FileStream fs = File.Create(outputFileName))
using (var writer = new Utf8JsonWriter(fs, options: writerOptions))
using (JsonDocument document = JsonDocument.Parse(jsonString, documentOptions))
{
    JsonElement root = document.RootElement;

    if (root.ValueKind == JsonValueKind.Object)
    {
        writer.WriteStartObject();
    }
    else
    {
        return;
    }

    foreach (JsonProperty property in root.EnumerateObject())
    {
        property.WriteTo(writer);
    }

    writer.WriteEndObject();

    writer.Flush();
}
```

<span data-ttu-id="91273-361">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="91273-361">The preceding code:</span></span>

* <span data-ttu-id="91273-362">Odczytuje plik JSON, ładuje dane do `JsonDocument`i zapisuje sformatowany plik JSON w formacie.</span><span class="sxs-lookup"><span data-stu-id="91273-362">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="91273-363">Używa <xref:System.Text.Json.JsonDocumentOptions>, aby określić, że komentarze w wejściowym formacie JSON są dozwolone, ale ignorowane.</span><span class="sxs-lookup"><span data-stu-id="91273-363">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="91273-364">Po zakończeniu wywołuje <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> w składniku zapisywania.</span><span class="sxs-lookup"><span data-stu-id="91273-364">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="91273-365">Alternatywą jest umożliwienie składnika zapisywania AutoFlush, gdy zostanie on usunięty.</span><span class="sxs-lookup"><span data-stu-id="91273-365">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="91273-366">Oto przykład danych wejściowych JSON do przetworzenia przez przykładowy kod:</span><span class="sxs-lookup"><span data-stu-id="91273-366">Here's an example of JSON input to be processed by the example code:</span></span>

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

<span data-ttu-id="91273-367">Wynikiem są następujące niedrukowane dane wyjściowe JSON:</span><span class="sxs-lookup"><span data-stu-id="91273-367">The result is the following pretty-printed JSON output:</span></span>

```json
{
  "Class Name": "Science",
  "Teacher\u0027s Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="91273-368">Użyj Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="91273-368">Use Utf8JsonWriter</span></span>

<span data-ttu-id="91273-369">Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.Utf8JsonWriter>:</span><span class="sxs-lookup"><span data-stu-id="91273-369">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

```csharp
var options = new JsonWriterOptions
{
    Indented = true
};

using (var stream = new MemoryStream())
{
    using (var writer = new Utf8JsonWriter(stream, options))
    {
        writer.WriteStartObject();
        writer.WriteString("date", DateTimeOffset.UtcNow);
        writer.WriteNumber("temp", 42);
        writer.WriteEndObject();
    }

    string json = Encoding.UTF8.GetString(stream.ToArray());
    Console.WriteLine(json);
}
```

## <a name="use-utf8jsonreader"></a><span data-ttu-id="91273-370">Użyj Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="91273-370">Use Utf8JsonReader</span></span>

<span data-ttu-id="91273-371">Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.Utf8JsonReader>:</span><span class="sxs-lookup"><span data-stu-id="91273-371">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

```csharp
var options = new JsonReaderOptions
{
    AllowTrailingCommas = true,
    CommentHandling = JsonCommentHandling.Skip
};
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, options);

while (reader.Read())
{
    Console.Write(reader.TokenType);

    switch (reader.TokenType)
    {
        case JsonTokenType.PropertyName:
        case JsonTokenType.String:
            {
                string text = reader.GetString();
                Console.Write(" ");
                Console.Write(text);
                break;
            }

        case JsonTokenType.Number:
            {
                int value = reader.GetInt32();
                Console.Write(" ");
                Console.Write(value);
                break;
            }

            // Other token types elided for brevity
    }

    Console.WriteLine();
}
```

<span data-ttu-id="91273-372">Poprzedni kod założono, że zmienna `jsonUtf8` jest tablicą bajtów, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="91273-372">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="91273-373">Filtrowanie danych za pomocą Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="91273-373">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="91273-374">Poniższy przykład pokazuje, jak odczytywać plik synchronicznie i wyszukiwać wartość:</span><span class="sxs-lookup"><span data-stu-id="91273-374">The following example shows how to read a file synchronously and search for a value:</span></span>

```csharp
class Program
{
    private static readonly byte[] s_nameUtf8 = Encoding.UTF8.GetBytes("name");
    private static readonly byte[] s_universityUtf8 = Encoding.UTF8.GetBytes("University");

    private static void ReaderFromFileSync(string fileName)
    {
         string jsonString = File.ReadAllText(fileName);
         ReadOnlySpan<byte> jsonReadOnlySpan = Encoding.UTF8.GetBytes(jsonString);

        int count = 0;
        int total = 0;

        var json = new Utf8JsonReader(jsonReadOnlySpan, isFinalBlock: true, state: default);

        while (json.Read())
        {
            JsonTokenType tokenType = json.TokenType;

            switch (tokenType)
            {
                case JsonTokenType.StartObject:
                    total++;
                    break;
                case JsonTokenType.PropertyName:
                    if (json.ValueSpan.SequenceEqual(s_nameUtf8))
                    {
                        bool result = json.Read();

                        Debug.Assert(result);  // Assume valid JSON
                        Debug.Assert(json.TokenType == JsonTokenType.String);   // Assume known, valid JSON schema

                        if (json.ValueSpan.EndsWith(s_universityUtf8))
                        {
                            count++;
                        }
                    }
                    break;
            }
        }
        Console.WriteLine($"{count} out of {total} have names that end with 'University'");
    }
}
```

<span data-ttu-id="91273-375">Poprzedni kod:</span><span class="sxs-lookup"><span data-stu-id="91273-375">The preceding code:</span></span>

* <span data-ttu-id="91273-376">Przyjęto założenie, że plik jest zakodowany jako UTF-16 i transkoduje go do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="91273-376">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="91273-377">Plik zakodowany jako UTF-8 można odczytać bezpośrednio w `ReadOnlySpan<byte>`, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="91273-377">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="91273-378">Przyjęto, że kod JSON zawiera tablicę obiektów, a każdy obiekt może zawierać właściwość "name" typu String.</span><span class="sxs-lookup"><span data-stu-id="91273-378">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="91273-379">Zlicza obiekty i `name` wartości właściwości, które kończą się na Uniwersytecie.</span><span class="sxs-lookup"><span data-stu-id="91273-379">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="91273-380">Oto przykład JSON, który może odczytać poprzedzający kod.</span><span class="sxs-lookup"><span data-stu-id="91273-380">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="91273-381">Otrzymany komunikat podsumowujący to "2 z 4 mają nazwy kończące się na" University ":</span><span class="sxs-lookup"><span data-stu-id="91273-381">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

```json
[
  {
    "web_pages": [ "https://contoso.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contoso.edu" ],
    "name": "Contoso Community College"
  },
  {
    "web_pages": [ "http://fabrikam.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikam.edu" ],
    "name": "Fabrikam Community College"
  },
  {
    "web_pages": [ "http://www.contosouniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contosouniversity.edu" ],
    "name": "Contoso University"
  },
  {
    "web_pages": [ "http://www.fabrikamuniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikamuniversity.edu" ],
    "name": "Fabrikam University"
  }
]
```

## <a name="additional-resources"></a><span data-ttu-id="91273-382">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="91273-382">Additional resources</span></span>

* [<span data-ttu-id="91273-383">System. Text. JSON — Omówienie</span><span class="sxs-lookup"><span data-stu-id="91273-383">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="91273-384">Dokumentacja interfejsu API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="91273-384">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="91273-385">Zapisuj niestandardowe konwertery dla elementu System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="91273-385">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="91273-386">Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="91273-386">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
