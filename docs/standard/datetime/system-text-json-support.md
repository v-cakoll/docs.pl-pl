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
ms.openlocfilehash: 8198359e2c54c4ed098703fbcc070f7469b3362a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344653"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Obsługa elementów DateTime i DateTimeOffset w pliku System.Text.Json

Biblioteka system. Text. JSON analizuje i zapisuje <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości zgodnie z rozszerzonym profilem ISO 8601:-2019.
[Konwertery](xref:System.Text.Json.Serialization.JsonConverter%601) zapewniają obsługę niestandardową do serializacji i deserializacji za pomocą <xref:System.Text.Json.JsonSerializer>.
Obsługę niestandardową można również zaimplementować przy użyciu <xref:System.Text.Json.Utf8JsonReader> i <xref:System.Text.Json.Utf8JsonWriter>.

## <a name="support-for-the-iso-8601-12019-format"></a>Obsługa formatu ISO 8601-1:2019

Typy <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>i <xref:System.Text.Json.JsonElement> analizują i zapisują <xref:System.DateTime> i <xref:System.DateTimeOffset> reprezentacje tekstowe zgodnie z rozszerzonym profilem formatu ISO 8601-1:2019; na przykład 2019-07-26T16:59:57-05:00.

<xref:System.DateTime> i <xref:System.DateTimeOffset> dane można serializować przy użyciu <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Można je również zdeserializować przy użyciu <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Z opcjami domyślnymi dane wejściowe <xref:System.DateTime> i <xref:System.DateTimeOffset> reprezentacje tekstowe muszą być zgodne z profilem rozszerzonego ISO 8601-1:2019.
Próba deserializacji reprezentacji, które nie są zgodne z profilem, spowoduje, że <xref:System.Text.Json.JsonSerializer> zgłosić <xref:System.Text.Json.JsonException>:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<xref:System.Text.Json.JsonDocument> zapewnia strukturalny dostęp do zawartości ładunku JSON, w tym <xref:System.DateTime> i <xref:System.DateTimeOffset> reprezentacje. W poniższym przykładzie pokazano, jak w przypadku zbierania temperatury można obliczyć średnią temperaturę w poniedziałek:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Próba obliczenia średniej temperatury danego ładunku z niezgodnymi reprezentacjami <xref:System.DateTime> spowoduje, że <xref:System.Text.Json.JsonDocument> zgłosić <xref:System.FormatException>:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

<xref:System.Text.Json.Utf8JsonWriter> niższego poziomu zapisuje <xref:System.DateTime> i <xref:System.DateTimeOffset> dane:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader> analizuje <xref:System.DateTime> i <xref:System.DateTimeOffset> dane:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Próba odczytania niezgodnych formatów z <xref:System.Text.Json.Utf8JsonReader> spowoduje zgłoszenie <xref:System.FormatException>:

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Obsługa niestandardowych <xref:System.DateTime> i <xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Przy użyciu <xref:System.Text.Json.JsonSerializer>

Jeśli chcesz, aby serializator wykonywał niestandardowe analizy lub formatowanie, możesz zaimplementować [niestandardowe konwertery](xref:System.Text.Json.Serialization.JsonConverter%601).
Oto kilka przykładów:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Używanie `DateTime(Offset).Parse` i `DateTime(Offset).ToString`

Jeśli nie możesz określić formatów danych wejściowych <xref:System.DateTime> lub <xref:System.DateTimeOffset> reprezentacje tekstu, możesz użyć metody `DateTime(Offset).Parse` w logice odczytu konwertera. Umożliwia to korzystanie z programu. Rozległa pomoc techniczna w sieci na potrzeby analizowania różnych <xref:System.DateTime> i <xref:System.DateTimeOffset> formatów tekstu, w tym ciągów z niestandardem ISO 8601 i formatów ISO 8601, które nie są zgodne z rozszerzonym profilem ISO 8601-1:2019. Ta metoda jest znacznie mniej wydajna niż użycie natywnej implementacji serializatora.

Do serializacji można użyć metody `DateTime(Offset).ToString` w logice zapisu konwertera. Dzięki temu można pisać <xref:System.DateTime> i <xref:System.DateTimeOffset> wartości przy użyciu dowolnych [standardowych formatów daty i godziny](../base-types/standard-date-and-time-format-strings.md)oraz [niestandardowych formatów daty i godziny](../base-types/custom-date-and-time-format-strings.md).
Jest to również znacznie mniej wydajne niż użycie natywnej implementacji serializatora.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Podczas implementowania <xref:System.Text.Json.Serialization.JsonConverter%601>, a `T` jest <xref:System.DateTime>, parametr `typeToConvert` będzie zawsze `typeof(DateTime)`.
Parametr jest przydatny do obsługi przypadków polimorficznych i używania typów ogólnych do uzyskiwania `typeof(T)` w sposób efektywny.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Używanie <xref:System.Buffers.Text.Utf8Parser> i <xref:System.Buffers.Text.Utf8Formatter>

W logice konwertera można używać szybkich metod analizy i formatowania opartych na kodowaniu UTF-8, jeśli dane wejściowe <xref:System.DateTime> lub <xref:System.DateTimeOffset> są zgodne z jednym z ciągów "R", "l", "O" lub "G" [standardowego formatu daty i godziny](../base-types/standard-date-and-time-format-strings.md), lub chcesz pisać według jednego z tych formatów. Jest to znacznie szybsze niż używanie `DateTime(Offset).Parse` i `DateTime(Offset).ToString`.

W tym przykładzie przedstawiono niestandardowy konwerter, który serializować i deserializacji wartości <xref:System.DateTime> zgodnie z [formatem standardowym "R"](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> Standardowy format "R" będzie zawsze zawierać 29 znaków.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Używanie `DateTime(Offset).Parse` jako powrotu do analizy natywnej serializatora

Jeśli zwykle oczekujesz, że dane wejściowe <xref:System.DateTime> lub <xref:System.DateTimeOffset> są zgodne z rozszerzonym profilem ISO 8601-1:2019, możesz użyć natywnej logiki analizy serializatora. Można również zaimplementować mechanizm rezerwowy tylko w przypadku.
Ten przykład pokazuje, że po niepowodzeniu analizy <xref:System.DateTime> reprezentacji tekstowej przy użyciu <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, konwerter pomyślnie przeanalizuje dane przy użyciu <xref:System.DateTime.Parse(System.String)>.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Podczas pisania przy użyciu <xref:System.Text.Json.Utf8JsonWriter>

Jeśli chcesz napisać niestandardowy <xref:System.DateTime> lub <xref:System.DateTimeOffset> reprezentację tekstową za pomocą <xref:System.Text.Json.Utf8JsonWriter>, możesz sformatować swoją niestandardową reprezentację do <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`lub <xref:System.Text.Json.JsonEncodedText>, a następnie przekazać ją do odpowiedniej metody <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> lub <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType>.

Poniższy przykład pokazuje, jak <xref:System.DateTime> format niestandardowy można utworzyć za pomocą <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>, a następnie napisać przy użyciu metody <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)>:

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Podczas czytania przy użyciu <xref:System.Text.Json.Utf8JsonReader>

Jeśli chcesz odczytać niestandardowy <xref:System.DateTime> lub <xref:System.DateTimeOffset> reprezentację tekstową za pomocą <xref:System.Text.Json.Utf8JsonReader>, możesz pobrać wartość bieżącego tokenu JSON jako <xref:System.String> przy użyciu <xref:System.Text.Json.Utf8JsonReader.GetString>, a następnie przeanalizować wartość przy użyciu logiki niestandardowej.

Poniższy przykład pokazuje, jak można pobrać niestandardową reprezentację tekstu <xref:System.DateTimeOffset> przy użyciu <xref:System.Text.Json.Utf8JsonReader.GetString>, a następnie przeanalizować ją przy użyciu <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Profil rozszerzonego ISO 8601-1:2019 w pliku System. Text. JSON

### <a name="date-and-time-components"></a>Składniki daty i godziny

Profil rozszerzonego ISO 8601-1:2019 zaimplementowany w <xref:System.Text.Json> definiuje następujące składniki dla reprezentacji daty i godziny. Te składniki są używane do definiowania różnych poziomów szczegółowości, które są obsługiwane podczas analizowania i formatowania <xref:System.DateTime> i <xref:System.DateTimeOffset> reprezentacji.

| Składnik       | Format                      | Opis                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Rok            | „yyyy”                      | 0001-9999                                                                       |
| Month           | „MM”                        | 01-12                                                                           |
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
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([specyfikator formatu sortowania ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier)
    2. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF

4. "" Pełna Data "" t "godzina" ":" minuta "przesunięcie czasu" "
    1. "yyyy'-'MM'-'dd'T'HH": "mmZ"
    2. "yyyy'-'MM'-'dd'T'HH": "mm (" + "/"-") gg": "mm"

5. "Data i godzina"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SSS"
    2. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFFZ"
    3. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" + "/"-") gg": "mm"
    4. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF (' + '/'-') gg ': ' mm '

Jeśli istnieją ułamki dziesiętne dla sekund, musi zawierać co najmniej jedną cyfrę; `2019-07-26T00:00:00.` jest niedozwolony.
Gdy dozwolone są maksymalnie 16 cyfr ułamkowych, analizowane są tylko pierwsze siedem. Wszystko, co jest traktowane jako zero.
Na przykład `2019-07-26T00:00:00.1234567890` zostanie przeanalizowany, jeśli jest `2019-07-26T00:00:00.1234567`.
Jest to zgodne z implementacją <xref:System.DateTime>, która jest ograniczona do tego rozwiązania.

Sekundy przestępne nie są obsługiwane.

### <a name="support-for-formatting"></a>Obsługa formatowania

Następujące poziomy szczegółowości są zdefiniowane na potrzeby formatowania:

1. "" Pełna Data "" t "" częściowe czas ""
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" ([specyfikator formatu sortowania ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier)

        Służy do formatowania <xref:System.DateTime> bez ułamków sekund i bez informacji o przesunięciu.

    2. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF

        Służy do formatowania <xref:System.DateTime> za pomocą ułamków sekund, ale bez informacji o przesunięciu.

2. "Data i godzina"
    1. "yyyy'-'MM'-'dd'T'HH": "mm": "SSS"

        Służy do formatowania <xref:System.DateTime> bez ułamków sekund, ale z przesunięciem czasu UTC.

    2. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFFZ"

        Służy do formatowania <xref:System.DateTime> za pomocą ułamków sekund i przesunięcia czasu UTC.

    3. "yyyy'-'MM'-'dd'T'HH": "mm": "SS" + "/"-") gg": "mm"

        Służy do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> bez ułamków sekund, ale z przesunięciem lokalnym.

    4. "yyyy'-'MM'-'dd'T'HH": "mm": "SS". " FFFFFFF (' + '/'-') gg ': ' mm '

        Służy do formatowania <xref:System.DateTime> lub <xref:System.DateTimeOffset> za pomocą ułamków sekund i przesunięcia lokalnego.

Jeśli jest obecny, zapisywana jest maksymalnie 7 cyfr ułamkowych. Jest to zgodne z implementacją <xref:System.DateTime>, która jest ograniczona do tego rozwiązania.
