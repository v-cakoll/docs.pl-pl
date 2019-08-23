---
title: Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON
description: Omówienie sposobu, w jaki typy DateTime i DateTimeOffset są obsługiwane w bibliotece system. Text. JSON.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 182694a3d2df02d5e2c709e33a02bd9fa7d20383
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69973192"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="f9209-103">Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="f9209-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="f9209-104">Biblioteka system. Text. JSON analizuje i zapisuje <xref:System.DateTime> dane oraz <xref:System.DateTimeOffset> wartości zgodnie z rozszerzonym profilem ISO 8601:-2019.</span><span class="sxs-lookup"><span data-stu-id="f9209-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="f9209-105">[Konwertery](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) zapewniają obsługę niestandardową do serializacji i deserializacji <xref:System.Text.Json.JsonSerializer>za pomocą.</span><span class="sxs-lookup"><span data-stu-id="f9209-105">[Converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="f9209-106">Obsługa formatu ISO 8601-1:2019</span><span class="sxs-lookup"><span data-stu-id="f9209-106">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="f9209-107"><xref:System.Text.Json.Utf8JsonReader> <xref:System.DateTimeOffset> <xref:System.DateTime> ,, ,I<xref:System.Text.Json.JsonElement> typy przeanalizują i zapisują reprezentacje, zgodnie z rozszerzonym profilem formatu ISO 8601-1:2019, na przykład 2019-07-26T16 <xref:System.Text.Json.Utf8JsonWriter> <xref:System.Text.Json.JsonSerializer> : 59:57-05:00.</span><span class="sxs-lookup"><span data-stu-id="f9209-107">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="f9209-108"><xref:System.DateTime>i <xref:System.DateTimeOffset> można serializować dane przy użyciu <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="f9209-108"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

<span data-ttu-id="f9209-109">Można je również zdeserializować przy użyciu <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="f9209-109">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

<span data-ttu-id="f9209-110">Z opcjami domyślnymi <xref:System.DateTime> reprezentacje wejściowe i <xref:System.DateTimeOffset> tekstowe muszą być zgodne z rozszerzonym profilem ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="f9209-110">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="f9209-111">Próba deserializacji reprezentacji, które nie są zgodne z profilem <xref:System.Text.Json.JsonSerializer> , spowoduje <xref:System.Text.Json.JsonException>wygenerowanie:</span><span class="sxs-lookup"><span data-stu-id="f9209-111">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

<span data-ttu-id="f9209-112">Zapewnia strukturalny dostęp do zawartości ładunku JSON, w tym <xref:System.DateTime> i <xref:System.DateTimeOffset> reprezentacje. <xref:System.Text.Json.JsonDocument></span><span class="sxs-lookup"><span data-stu-id="f9209-112">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="f9209-113">W poniższym przykładzie pokazano, jak w przypadku zbierania temperatury można obliczyć średnią temperaturę w poniedziałek:</span><span class="sxs-lookup"><span data-stu-id="f9209-113">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

<span data-ttu-id="f9209-114">Próba obliczenia średniej temperatury danego ładunku z niezgodnymi <xref:System.DateTime> reprezentacjami <xref:System.Text.Json.JsonDocument> spowoduje wygenerowanie <xref:System.FormatException>:</span><span class="sxs-lookup"><span data-stu-id="f9209-114">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

<span data-ttu-id="f9209-115">Zapisy <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> i daneniższegopoziomu:<xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="f9209-115">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<span data-ttu-id="f9209-116"><xref:System.Text.Json.Utf8JsonReader><xref:System.DateTime> analizowanie i<xref:System.DateTimeOffset> dane:</span><span class="sxs-lookup"><span data-stu-id="f9209-116"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

<span data-ttu-id="f9209-117">Próba odczytania niezgodnych formatów w programie <xref:System.Text.Json.Utf8JsonReader> spowoduje <xref:System.FormatException>wygenerowanie:</span><span class="sxs-lookup"><span data-stu-id="f9209-117">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="f9209-118">Obsługa niestandardowa <xref:System.DateTimeOffset> dla <xref:System.DateTime> i w<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="f9209-118">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset> in <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="f9209-119">Jeśli chcesz, aby serializator wykonywał niestandardowe analizy lub formatowanie, możesz zaimplementować [niestandardowe konwertery](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="f9209-119">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span></span>
<span data-ttu-id="f9209-120">Oto kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="f9209-120">Here are a few examples:</span></span>

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="f9209-121">Korzystanie `DateTime(Offset).Parse` z i`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="f9209-121">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="f9209-122">Jeśli nie możesz określić formatów reprezentacji danych wejściowych <xref:System.DateTime> lub <xref:System.DateTimeOffset> tekstowych `DateTime(Offset).Parse` , możesz użyć metody z logiki odczytu konwertera.</span><span class="sxs-lookup"><span data-stu-id="f9209-122">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="f9209-123">Umożliwia to korzystanie z programu. Rozległa pomoc techniczna w sieci na <xref:System.DateTime> potrzeby <xref:System.DateTimeOffset> analizowania różnych formatów i formatu tekstu, w tym ciągów z niestandardem ISO 8601 i formatów ISO 8601, które nie są zgodne z rozszerzonym profilem ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="f9209-123">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="f9209-124">Ta metoda jest znacznie mniej wydajna niż użycie natywnej implementacji serializatora.</span><span class="sxs-lookup"><span data-stu-id="f9209-124">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="f9209-125">Do serializacji można użyć `DateTime(Offset).ToString` metody z logiki zapisu konwertera.</span><span class="sxs-lookup"><span data-stu-id="f9209-125">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="f9209-126"><xref:System.DateTime> Pozwala to pisać <xref:System.DateTimeOffset> i wartości przy użyciu dowolnych [standardowych formatów daty i godziny](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)oraz [niestandardowych formatów daty i godziny](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span><span class="sxs-lookup"><span data-stu-id="f9209-126">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="f9209-127">Jest to również znacznie mniej wydajne niż użycie natywnej implementacji serializatora.</span><span class="sxs-lookup"><span data-stu-id="f9209-127">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="f9209-128">Podczas <xref:System.Text.Json.Serialization.JsonConverter%601>implementowania i `T` jest <xref:System.DateTime> parametr`typeToConvert` zawsze`typeof(DateTime)`będzie.</span><span class="sxs-lookup"><span data-stu-id="f9209-128">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="f9209-129">Parametr jest przydatny do obsługi przypadków polimorficznych i korzystania z typów ogólnych do `typeof(T)` uzyskania w sposób efektywny.</span><span class="sxs-lookup"><span data-stu-id="f9209-129">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="f9209-130">Korzystanie <xref:System.Buffers.Text.Utf8Parser> z i<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="f9209-130">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="f9209-131">W logice konwertera można używać szybkich metod analizy i formatowania opartych na kodowaniu UTF-8 <xref:System.DateTime> , <xref:System.DateTimeOffset> Jeśli prezentacje wejściowe lub tekstowe są zgodne z jednym z [ciągów standardowego formatu daty i godziny](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" lub "G" lub chcesz Zapisz zgodnie z jednym z tych formatów.</span><span class="sxs-lookup"><span data-stu-id="f9209-131">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format Strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="f9209-132">Jest to znacznie szybsze niż użycie `DateTime(Offset).Parse` i `DateTime(Offset).ToString`.</span><span class="sxs-lookup"><span data-stu-id="f9209-132">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="f9209-133">Ten przykład pokazuje niestandardowy konwerter, który serializować i deserializacji <xref:System.DateTime> wartości zgodnie z [formatem standardowym "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span><span class="sxs-lookup"><span data-stu-id="f9209-133">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="f9209-134">Standardowy format "R" będzie zawsze zawierać 29 znaków.</span><span class="sxs-lookup"><span data-stu-id="f9209-134">The "R" standard format will always be 29 characters long.</span></span>

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="f9209-135">Używanie `DateTime(Offset).Parse` jako rezerwy do analizy natywnej serializatora</span><span class="sxs-lookup"><span data-stu-id="f9209-135">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="f9209-136">Jeśli zazwyczaj oczekujesz, że <xref:System.DateTime> dane <xref:System.DateTimeOffset> wejściowe lub zgodne z rozszerzonym profilem ISO 8601-1:2019, możesz użyć natywnej logiki analizy serializatora.</span><span class="sxs-lookup"><span data-stu-id="f9209-136">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="f9209-137">Można również zaimplementować mechanizm rezerwowy tylko w przypadku.</span><span class="sxs-lookup"><span data-stu-id="f9209-137">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="f9209-138">Ten przykład pokazuje, że po niepowodzeniu analizy <xref:System.DateTime> reprezentacji tekstowej przy użyciu <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>konwertera pomyślnie przeanalizuje dane <xref:System.DateTime.Parse(System.String)>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="f9209-138">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="f9209-139">Profil rozszerzonego ISO 8601-1:2019 w pliku System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="f9209-139">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="f9209-140">Składniki daty i godziny</span><span class="sxs-lookup"><span data-stu-id="f9209-140">Date and time components</span></span>

<span data-ttu-id="f9209-141">Profil rozszerzonego ISO 8601-1:2019 zaimplementowany w <xref:System.Text.Json> programie definiuje następujące składniki dla reprezentacji daty i godziny.</span><span class="sxs-lookup"><span data-stu-id="f9209-141">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="f9209-142">Te składniki służą do definiowania różnych poziomów szczegółowości, które są obsługiwane podczas analizowania i <xref:System.DateTime> formatowania <xref:System.DateTimeOffset> i reprezentacji.</span><span class="sxs-lookup"><span data-stu-id="f9209-142">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="f9209-143">Składnik</span><span class="sxs-lookup"><span data-stu-id="f9209-143">Component</span></span>       | <span data-ttu-id="f9209-144">Format</span><span class="sxs-lookup"><span data-stu-id="f9209-144">Format</span></span>                      | <span data-ttu-id="f9209-145">Opis</span><span class="sxs-lookup"><span data-stu-id="f9209-145">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="f9209-146">Rok</span><span class="sxs-lookup"><span data-stu-id="f9209-146">Year</span></span>            | <span data-ttu-id="f9209-147">„yyyy”</span><span class="sxs-lookup"><span data-stu-id="f9209-147">"yyyy"</span></span>                      | <span data-ttu-id="f9209-148">0001-9999</span><span class="sxs-lookup"><span data-stu-id="f9209-148">0001-9999</span></span>                                                                       |
| <span data-ttu-id="f9209-149">Bieżącym</span><span class="sxs-lookup"><span data-stu-id="f9209-149">Month</span></span>           | <span data-ttu-id="f9209-150">„MM”</span><span class="sxs-lookup"><span data-stu-id="f9209-150">"MM"</span></span>                        | <span data-ttu-id="f9209-151">01-12</span><span class="sxs-lookup"><span data-stu-id="f9209-151">01-12</span></span>                                                                           |
| <span data-ttu-id="f9209-152">Dzień</span><span class="sxs-lookup"><span data-stu-id="f9209-152">Day</span></span>             | <span data-ttu-id="f9209-153">„dd”</span><span class="sxs-lookup"><span data-stu-id="f9209-153">"dd"</span></span>                        | <span data-ttu-id="f9209-154">01-28, 01-29, 01-30, 01-31 w oparciu o miesiąc/rok</span><span class="sxs-lookup"><span data-stu-id="f9209-154">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="f9209-155">Godzina</span><span class="sxs-lookup"><span data-stu-id="f9209-155">Hour</span></span>            | <span data-ttu-id="f9209-156">„HH”</span><span class="sxs-lookup"><span data-stu-id="f9209-156">"HH"</span></span>                        | <span data-ttu-id="f9209-157">00-23</span><span class="sxs-lookup"><span data-stu-id="f9209-157">00-23</span></span>                                                                           |
| <span data-ttu-id="f9209-158">Minuta</span><span class="sxs-lookup"><span data-stu-id="f9209-158">Minute</span></span>          | <span data-ttu-id="f9209-159">„mm”</span><span class="sxs-lookup"><span data-stu-id="f9209-159">"mm"</span></span>                        | <span data-ttu-id="f9209-160">00-59</span><span class="sxs-lookup"><span data-stu-id="f9209-160">00-59</span></span>                                                                           |
| <span data-ttu-id="f9209-161">Sekunda</span><span class="sxs-lookup"><span data-stu-id="f9209-161">Second</span></span>          | <span data-ttu-id="f9209-162">„ss”</span><span class="sxs-lookup"><span data-stu-id="f9209-162">"ss"</span></span>                        | <span data-ttu-id="f9209-163">00-59</span><span class="sxs-lookup"><span data-stu-id="f9209-163">00-59</span></span>                                                                           |
| <span data-ttu-id="f9209-164">Druga część</span><span class="sxs-lookup"><span data-stu-id="f9209-164">Second fraction</span></span> | <span data-ttu-id="f9209-165">„FFFFFFF”</span><span class="sxs-lookup"><span data-stu-id="f9209-165">"FFFFFFF"</span></span>                   | <span data-ttu-id="f9209-166">Co najmniej jedna cyfra, maksymalnie 16 cyfr</span><span class="sxs-lookup"><span data-stu-id="f9209-166">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="f9209-167">Przesunięcie czasu</span><span class="sxs-lookup"><span data-stu-id="f9209-167">Time offset</span></span>     | <span data-ttu-id="f9209-168">„K”</span><span class="sxs-lookup"><span data-stu-id="f9209-168">"K"</span></span>                         | <span data-ttu-id="f9209-169">"Z" lub "(" + "/"-") gg": "mm"</span><span class="sxs-lookup"><span data-stu-id="f9209-169">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="f9209-170">Czas częściowy</span><span class="sxs-lookup"><span data-stu-id="f9209-170">Partial time</span></span>    | <span data-ttu-id="f9209-171">"Gg": "mm": "SS [FFFFFFF]"</span><span class="sxs-lookup"><span data-stu-id="f9209-171">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="f9209-172">Czas bez informacji o przesunięciu czasu UTC</span><span class="sxs-lookup"><span data-stu-id="f9209-172">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="f9209-173">Pełna Data</span><span class="sxs-lookup"><span data-stu-id="f9209-173">Full date</span></span>       | <span data-ttu-id="f9209-174">"yyyy'-'MM'-'dd"</span><span class="sxs-lookup"><span data-stu-id="f9209-174">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="f9209-175">Data kalendarza</span><span class="sxs-lookup"><span data-stu-id="f9209-175">Calendar date</span></span>                                                                   |
| <span data-ttu-id="f9209-176">Pełny czas</span><span class="sxs-lookup"><span data-stu-id="f9209-176">Full time</span></span>       | <span data-ttu-id="f9209-177">"Częściowe time'K"</span><span class="sxs-lookup"><span data-stu-id="f9209-177">"'Partial time'K"</span></span>           | <span data-ttu-id="f9209-178">Czas UTC dnia lub lokalny dzień z przesunięciem czasu między czasem lokalnym i czasem UTC</span><span class="sxs-lookup"><span data-stu-id="f9209-178">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="f9209-179">Data i godzina</span><span class="sxs-lookup"><span data-stu-id="f9209-179">Date time</span></span>       | <span data-ttu-id="f9209-180">"" Pełna Data "t" "Pełny czas" "</span><span class="sxs-lookup"><span data-stu-id="f9209-180">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="f9209-181">Data i godzina kalendarzowa, np. 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="f9209-181">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="f9209-182">Obsługa analizy</span><span class="sxs-lookup"><span data-stu-id="f9209-182">Support for parsing</span></span>

<span data-ttu-id="f9209-183">Następujące poziomy szczegółowości są zdefiniowane do analizy:</span><span class="sxs-lookup"><span data-stu-id="f9209-183">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="f9209-184">"Pełna Data"</span><span class="sxs-lookup"><span data-stu-id="f9209-184">'Full date'</span></span>
    1. <span data-ttu-id="f9209-185">"yyyy'-'MM'-'dd"</span><span class="sxs-lookup"><span data-stu-id="f9209-185">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="f9209-186">"" Pełna Data "t" godzina "": "minuta" "</span><span class="sxs-lookup"><span data-stu-id="f9209-186">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="f9209-187">"yyyy'-'MM'-'dd'T'HH": "mm"</span><span class="sxs-lookup"><span data-stu-id="f9209-187">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="f9209-188">"" Pełna Data "" t "" częściowe czas ""</span><span class="sxs-lookup"><span data-stu-id="f9209-188">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="f9209-189">"yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([specyfikator formatu sortowania ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier)</span><span class="sxs-lookup"><span data-stu-id="f9209-189">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="f9209-190">"yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="f9209-190">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="f9209-191">"" Pełna Data "" t "godzina" ":" minuta "przesunięcie czasu" "</span><span class="sxs-lookup"><span data-stu-id="f9209-191">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="f9209-192">"yyyy'-'MM'-'dd'T'HH": "mmZ"</span><span class="sxs-lookup"><span data-stu-id="f9209-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="f9209-193">"yyyy'-'MM'-'dd'T'HH": "mm (" + "/"-") gg": "mm"</span><span class="sxs-lookup"><span data-stu-id="f9209-193">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="f9209-194">"Data i godzina"</span><span class="sxs-lookup"><span data-stu-id="f9209-194">'Date time'</span></span>
    1. <span data-ttu-id="f9209-195">"yyyy'-'MM'-'dd'T'HH": "mm": "SSS"</span><span class="sxs-lookup"><span data-stu-id="f9209-195">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="f9209-196">"yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="f9209-196">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="f9209-197">"yyyy'-'MM'-'dd'T'HH": "mm": "SS" + "/"-") gg": "mm"</span><span class="sxs-lookup"><span data-stu-id="f9209-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="f9209-198">"yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF (' + '/'-') gg ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="f9209-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="f9209-199">Jeśli istnieją ułamki dziesiętne dla sekund, musi zawierać co najmniej jedną cyfrę; `2019-07-26T00:00:00.` nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="f9209-199">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="f9209-200">Gdy dozwolone są maksymalnie 16 cyfr ułamkowych, analizowane są tylko pierwsze siedem.</span><span class="sxs-lookup"><span data-stu-id="f9209-200">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="f9209-201">Wszystko, co jest traktowane jako zero.</span><span class="sxs-lookup"><span data-stu-id="f9209-201">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="f9209-202">Na przykład program `2019-07-26T00:00:00.1234567890` zostanie przeanalizowany tak, jakby był. `2019-07-26T00:00:00.1234567`</span><span class="sxs-lookup"><span data-stu-id="f9209-202">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="f9209-203">Jest to tak, aby zachować zgodność <xref:System.DateTime> z implementacją, która jest ograniczona do tego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f9209-203">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="f9209-204">Sekundy przestępne nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9209-204">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="f9209-205">Obsługa formatowania</span><span class="sxs-lookup"><span data-stu-id="f9209-205">Support for formatting</span></span>

<span data-ttu-id="f9209-206">Następujące poziomy szczegółowości są zdefiniowane na potrzeby formatowania:</span><span class="sxs-lookup"><span data-stu-id="f9209-206">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="f9209-207">"" Pełna Data "" t "" częściowe czas ""</span><span class="sxs-lookup"><span data-stu-id="f9209-207">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="f9209-208">"yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([specyfikator formatu sortowania ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier)</span><span class="sxs-lookup"><span data-stu-id="f9209-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="f9209-209">Służy do formatowania <xref:System.DateTime> bez ułamków sekund i bez informacji o przesunięciu.</span><span class="sxs-lookup"><span data-stu-id="f9209-209">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="f9209-210">"yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="f9209-210">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="f9209-211">Służy do formatowania z <xref:System.DateTime> ułamkami sekund, ale bez informacji o przesunięciu.</span><span class="sxs-lookup"><span data-stu-id="f9209-211">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="f9209-212">"Data i godzina"</span><span class="sxs-lookup"><span data-stu-id="f9209-212">'Date time'</span></span>
    1. <span data-ttu-id="f9209-213">"yyyy'-'MM'-'dd'T'HH": "mm": "SSS"</span><span class="sxs-lookup"><span data-stu-id="f9209-213">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="f9209-214">Używane do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> bez ułamków sekund, ale z przesunięciem czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="f9209-214">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="f9209-215">"yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="f9209-215">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="f9209-216">Służy do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> z ułamkami sekund i przesunięciem czasu UTC.</span><span class="sxs-lookup"><span data-stu-id="f9209-216">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="f9209-217">"yyyy'-'MM'-'dd'T'HH": "mm": "SS" + "/"-") gg": "mm"</span><span class="sxs-lookup"><span data-stu-id="f9209-217">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="f9209-218">Używane do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> bez ułamków sekund, ale z przesunięciem lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f9209-218">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="f9209-219">"yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF (' + '/'-') gg ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="f9209-219">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="f9209-220">Służy do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> z ułamkami sekund i przesunięcia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="f9209-220">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>
