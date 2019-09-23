---
title: Obsługa elementów DateTime i DateTimeOffset w pliku System.Text.Json
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
ms.openlocfilehash: 000a6b6dc892e65b50ae413ab3cb95d2a73ef0ef
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182572"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Obsługa elementów DateTime i DateTimeOffset w pliku System.Text.Json

Biblioteka system. Text. JSON analizuje i zapisuje <xref:System.DateTime> dane oraz <xref:System.DateTimeOffset> wartości zgodnie z rozszerzonym profilem ISO 8601:-2019.
[Konwertery](xref:System.Text.Json.Serialization.JsonConverter%601) zapewniają obsługę niestandardową do serializacji i deserializacji <xref:System.Text.Json.JsonSerializer>za pomocą.
Obsługę niestandardową można również zaimplementować przy <xref:System.Text.Json.Utf8JsonReader> użyciu <xref:System.Text.Json.Utf8JsonWriter>i.

## <a name="support-for-the-iso-8601-12019-format"></a>Obsługa formatu ISO 8601-1:2019

<xref:System.Text.Json.Utf8JsonReader> <xref:System.DateTimeOffset> <xref:System.DateTime> ,, ,I<xref:System.Text.Json.JsonElement> typy przeanalizują i zapisują reprezentacje, zgodnie z rozszerzonym profilem formatu ISO 8601-1:2019, na przykład 2019-07-26T16 <xref:System.Text.Json.Utf8JsonWriter> <xref:System.Text.Json.JsonSerializer> : 59:57-05:00.

<xref:System.DateTime>i <xref:System.DateTimeOffset> można serializować dane przy użyciu <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Można je również zdeserializować przy użyciu <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Z opcjami domyślnymi <xref:System.DateTime> reprezentacje wejściowe i <xref:System.DateTimeOffset> tekstowe muszą być zgodne z rozszerzonym profilem ISO 8601-1:2019.
Próba deserializacji reprezentacji, które nie są zgodne z profilem <xref:System.Text.Json.JsonSerializer> , spowoduje <xref:System.Text.Json.JsonException>wygenerowanie:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

Zapewnia strukturalny dostęp do zawartości ładunku JSON, w tym <xref:System.DateTime> i <xref:System.DateTimeOffset> reprezentacje. <xref:System.Text.Json.JsonDocument> W poniższym przykładzie pokazano, jak w przypadku zbierania temperatury można obliczyć średnią temperaturę w poniedziałek:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Próba obliczenia średniej temperatury danego ładunku z niezgodnymi <xref:System.DateTime> reprezentacjami <xref:System.Text.Json.JsonDocument> spowoduje wygenerowanie <xref:System.FormatException>:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

Zapisy <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> i daneniższegopoziomu:<xref:System.DateTimeOffset>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader><xref:System.DateTime> analizowanie i<xref:System.DateTimeOffset> dane:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Próba odczytania niezgodnych formatów w programie <xref:System.Text.Json.Utf8JsonReader> spowoduje <xref:System.FormatException>wygenerowanie:

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Obsługa niestandardowa dla programu <xref:System.DateTime> i<xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>W przypadku korzystania z<xref:System.Text.Json.JsonSerializer>

Jeśli chcesz, aby serializator wykonywał niestandardowe analizy lub formatowanie, możesz zaimplementować [niestandardowe konwertery](xref:System.Text.Json.Serialization.JsonConverter%601).
Oto kilka przykładów:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Korzystanie `DateTime(Offset).Parse` z i`DateTime(Offset).ToString`

Jeśli nie możesz określić formatów reprezentacji danych wejściowych <xref:System.DateTime> lub <xref:System.DateTimeOffset> tekstowych `DateTime(Offset).Parse` , możesz użyć metody z logiki odczytu konwertera. Umożliwia to korzystanie z programu. Rozległa pomoc techniczna w sieci na <xref:System.DateTime> potrzeby <xref:System.DateTimeOffset> analizowania różnych formatów i formatu tekstu, w tym ciągów z niestandardem ISO 8601 i formatów ISO 8601, które nie są zgodne z rozszerzonym profilem ISO 8601-1:2019. Ta metoda jest znacznie mniej wydajna niż użycie natywnej implementacji serializatora.

Do serializacji można użyć `DateTime(Offset).ToString` metody z logiki zapisu konwertera. <xref:System.DateTime> Pozwala to pisać <xref:System.DateTimeOffset> i wartości przy użyciu dowolnych [standardowych formatów daty i godziny](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)oraz [niestandardowych formatów daty i godziny](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).
Jest to również znacznie mniej wydajne niż użycie natywnej implementacji serializatora.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Podczas <xref:System.Text.Json.Serialization.JsonConverter%601>implementowania i `T` jest <xref:System.DateTime> parametr`typeToConvert` zawsze`typeof(DateTime)`będzie.
Parametr jest przydatny do obsługi przypadków polimorficznych i korzystania z typów ogólnych do `typeof(T)` uzyskania w sposób efektywny.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Korzystanie <xref:System.Buffers.Text.Utf8Parser> z i<xref:System.Buffers.Text.Utf8Formatter>

W logice konwertera można używać szybkich metod analizy i formatowania opartych na kodowaniu UTF-8 <xref:System.DateTime> , <xref:System.DateTimeOffset> Jeśli prezentacje wejściowe lub tekstowe są zgodne z jednym z [ciągów standardowego formatu daty i godziny](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" lub "G" lub chcesz Zapisz zgodnie z jednym z tych formatów. Jest to znacznie szybsze niż użycie `DateTime(Offset).Parse` i `DateTime(Offset).ToString`.

Ten przykład pokazuje niestandardowy konwerter, który serializować i deserializacji <xref:System.DateTime> wartości zgodnie z [formatem standardowym "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> Standardowy format "R" będzie zawsze zawierać 29 znaków.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Używanie `DateTime(Offset).Parse` jako rezerwy do analizy natywnej serializatora

Jeśli zazwyczaj oczekujesz, że <xref:System.DateTime> dane <xref:System.DateTimeOffset> wejściowe lub zgodne z rozszerzonym profilem ISO 8601-1:2019, możesz użyć natywnej logiki analizy serializatora. Można również zaimplementować mechanizm rezerwowy tylko w przypadku.
Ten przykład pokazuje, że po niepowodzeniu analizy <xref:System.DateTime> reprezentacji tekstowej przy użyciu <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>konwertera pomyślnie przeanalizuje dane <xref:System.DateTime.Parse(System.String)>przy użyciu.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Podczas pisania przy użyciu<xref:System.Text.Json.Utf8JsonWriter>

<xref:System.DateTime> Jeśli chcesz napisać niestandardową lub <xref:System.DateTimeOffset> tekstową reprezentację za pomocą <xref:System.Text.Json.Utf8JsonWriter>, możesz `ReadOnlySpan<Char>`sformatować swoją niestandardową reprezentację do <xref:System.String>, `ReadOnlySpan<Byte>`,, lub <xref:System.Text.Json.JsonEncodedText>, przekazać ją do odpowiedniego [Utf8JsonWriter. WriteStringValue](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0) lub [Utf8JsonWriter. WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0) .

Poniższy przykład pokazuje <xref:System.DateTime> ,jak<xref:System.DateTime.ToString(System.String,System.IFormatProvider)>format niestandardowy można utworzyć za pomocą, a następnie napisać przy użyciu metody:<xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)>

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Podczas czytania z<xref:System.Text.Json.Utf8JsonReader>

Jeśli <xref:System.DateTime> chcesz odczytać niestandardową lub <xref:System.DateTimeOffset> tekstową reprezentację z <xref:System.Text.Json.Utf8JsonReader>, możesz pobrać <xref:System.String> wartość bieżącego tokenu JSON jako użycie <xref:System.Text.Json.Utf8JsonReader.GetString>, a następnie przeanalizować wartość przy użyciu logiki niestandardowej.

Poniższy przykład pokazuje, jak można pobrać <xref:System.DateTimeOffset> niestandardową reprezentację <xref:System.Text.Json.Utf8JsonReader.GetString>tekstową przy użyciu, <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>a następnie przeanalizować ją przy użyciu:

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Profil rozszerzonego ISO 8601-1:2019 w pliku System. Text. JSON

### <a name="date-and-time-components"></a>Składniki daty i godziny

Profil rozszerzonego ISO 8601-1:2019 zaimplementowany w <xref:System.Text.Json> programie definiuje następujące składniki dla reprezentacji daty i godziny. Te składniki służą do definiowania różnych poziomów szczegółowości, które są obsługiwane podczas analizowania i <xref:System.DateTime> formatowania <xref:System.DateTimeOffset> i reprezentacji.

| Składnik       | Format                      | Opis                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Rok            | „yyyy”                      | 0001-9999                                                                       |
| Bieżącym           | „MM”                        | 01-12                                                                           |
| Dzień             | „dd”                        | 01-28, 01-29, 01-30, 01-31 w oparciu o miesiąc/rok                                  |
| Godzina            | „HH”                        | 00-23                                                                           |
| Minuta          | „mm”                        | 00-59                                                                           |
| Sekunda          | „ss”                        | 00-59                                                                           |
| Druga część | „FFFFFFF”                   | Co najmniej jedna cyfra, maksymalnie 16 cyfr                                      |
| Przesunięcie czasu     | „K”                         | "Z" lub "(" + "/"-") gg": "mm"                                                |
| Czas częściowy    | "Gg": "mm": "SS [FFFFFFF]"     | Czas bez informacji o przesunięciu czasu UTC                                             |
| Pełna Data       | "yyyy'-'MM'-'dd"            | Data kalendarza                                                                   |
| Pełny czas       | "Częściowe time'K"           | Czas UTC dnia lub lokalny dzień z przesunięciem czasu między czasem lokalnym i czasem UTC |
| Data i godzina       | "" Pełna Data "t" "Pełny czas" " | Data i godzina kalendarzowa, np. 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>Obsługa analizy

Następujące poziomy szczegółowości są zdefiniowane do analizy:

1. "Pełna Data"
    1. "yyyy'-'MM'-'dd"

2. "" Pełna Data "t" godzina "": "minuta" "
    1. "yyyy'-'MM'-'dd'T'HH": "mm"

3. "" Pełna Data "" t "" częściowe czas ""
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([specyfikator formatu sortowania ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier)
    2. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF

4. "" Pełna Data "" t "godzina" ":" minuta "przesunięcie czasu" "
    1. "yyyy'-'MM'-'dd'T'HH": "mmZ"
    2. "yyyy'-'MM'-'dd'T'HH": "mm (" + "/"-") gg": "mm"

5. "Data i godzina"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SSS"
    2. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFFZ"
    3. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" + "/"-") gg": "mm"
    4. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF (' + '/'-') gg ': ' mm '

Jeśli istnieją ułamki dziesiętne dla sekund, musi zawierać co najmniej jedną cyfrę; `2019-07-26T00:00:00.` nie jest dozwolone.
Gdy dozwolone są maksymalnie 16 cyfr ułamkowych, analizowane są tylko pierwsze siedem. Wszystko, co jest traktowane jako zero.
Na przykład program `2019-07-26T00:00:00.1234567890` zostanie przeanalizowany tak, jakby był. `2019-07-26T00:00:00.1234567`
Jest to tak, aby zachować zgodność <xref:System.DateTime> z implementacją, która jest ograniczona do tego rozwiązania.

Sekundy przestępne nie są obsługiwane.

### <a name="support-for-formatting"></a>Obsługa formatowania

Następujące poziomy szczegółowości są zdefiniowane na potrzeby formatowania:

1. "" Pełna Data "" t "" częściowe czas ""
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([specyfikator formatu sortowania ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier)

        Służy do formatowania <xref:System.DateTime> bez ułamków sekund i bez informacji o przesunięciu.

    2. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF

        Służy do formatowania z <xref:System.DateTime> ułamkami sekund, ale bez informacji o przesunięciu.

2. "Data i godzina"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SSS"

        Używane do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> bez ułamków sekund, ale z przesunięciem czasu UTC.

    2. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFFZ"

        Służy do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> z ułamkami sekund i przesunięciem czasu UTC.

    3. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" + "/"-") gg": "mm"

        Używane do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> bez ułamków sekund, ale z przesunięciem lokalnym.

    4. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF (' + '/'-') gg ': ' mm '

        Służy do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> z ułamkami sekund i przesunięcia lokalnego.

Jeśli jest obecny, zapisywana jest maksymalnie 7 cyfr ułamkowych. Jest to zgodne z <xref:System.DateTime> implementacją, która jest ograniczona do tego rozwiązania.
