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
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>Jak serializować i deserializować kod JSON w programie .NET

W tym artykule pokazano, jak używać przestrzeni nazw <xref:System.Text.Json> do serializacji i deserializacji do i z JavaScript Object Notation (JSON).

Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).

Większość przykładowych kodów serializacji <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType>, aby `true` do "DB-Print" pliku JSON (z wcięciem i białym znakiem). Do użycia w środowisku produkcyjnym zwykle przyjmuje się wartość domyślną `false` dla tego ustawienia.

## <a name="namespaces"></a>Namespaces

Przestrzeń nazw <xref:System.Text.Json> zawiera wszystkie punkty wejścia i typy główne. Przestrzeń nazw <xref:System.Text.Json.Serialization> zawiera atrybuty i interfejsy API dla zaawansowanych scenariuszy i dostosowań specyficznych dla serializacji i deserializacji. Przykłady kodu przedstawione w tym artykule wymagają `using` dyrektyw dla jednej lub obu tych przestrzeni nazw:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atrybuty z przestrzeni nazw <xref:System.Runtime.Serialization> nie są obecnie obsługiwane w `System.Text.Json`.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Pisanie obiektów .NET w formacie JSON (Serializacja)

Aby zapisać dane JSON do ciągu lub do pliku, wywołaj metodę <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.

Poniższy przykład tworzy kod JSON jako ciąg:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

Poniższy przykład używa kodu synchronicznego do utworzenia pliku JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

W poniższym przykładzie jest tworzony plik JSON przy użyciu kodu asynchronicznego:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Powyższe przykłady używają wnioskowania typu dla serializowanego typu. Przeciążenie `Serialize()` przyjmuje parametr typu ogólnego:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Przykład serializacji

Oto przykładowa Klasa, która zawiera kolekcje i zagnieżdżoną klasę:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

Dane wyjściowe JSON serializowania wystąpienia poprzedniego typu wyglądają podobnie jak w poniższym przykładzie. Dane wyjściowe JSON domyślnie są zminimalizowanego: 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

W poniższym przykładzie przedstawiono ten sam kod JSON, sformatowany (to jest całkiem wydruk z odstępami i wcięciami):

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

### <a name="serialize-to-utf-8"></a>Serializacja do UTF-8

Aby serializować do UTF-8, wywołaj metodę <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

Dostępne jest również Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A>, które pobiera <xref:System.Text.Json.Utf8JsonWriter>.

Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach. Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).

## <a name="serialization-behavior"></a>Zachowanie serializacji

* Domyślnie wszystkie właściwości publiczne są serializowane. Można [określić właściwości do wykluczenia](#exclude-properties-from-serialization).
* [Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem języka HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Domyślnie JSON jest zminimalizowanego. Można tu [wydrukować kod JSON](#serialize-to-formatted-json).
* Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET. Można [dostosować wielkość liter w nazwach JSON](#customize-json-names-and-values).
* Wykryto odwołania cykliczne i zostały zgłoszone wyjątki. Aby uzyskać więcej informacji, zobacz [problem 38579 dotyczący odwołań cyklicznych](https://github.com/dotnet/corefx/issues/38579) w repozytorium dotnet/corefx w witrynie GitHub.
* Obecnie pola są wykluczone.

Obsługiwane typy to:

* Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.
* Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tablice jednowymiarowe i nieregularne (`ArrayName[][]`).
* `Dictionary<string,TValue>`, gdzie `TValue` jest `object`, `JsonElement`lub POCO.
* Kolekcje z następujących przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [problem związany z obsługą kolekcji](https://github.com/dotnet/corefx/issues/36643) w repozytorium dotnet/corefx w witrynie GitHub.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Można [zaimplementować niestandardowe konwertery](system-text-json-converters-how-to.md) w celu obsługi dodatkowych typów lub zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Jak odczytywać dane JSON do obiektów .NET (deserializacji)

Aby zdeserializować z ciągu lub pliku, wywołaj metodę <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.

Poniższy przykład odczytuje dane JSON z ciągu i tworzy wystąpienie klasy `WeatherForecast` pokazanej wcześniej dla [przykładu serializacji](#serialization-example):

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Aby zdeserializować z pliku przy użyciu kodu synchronicznego, Odczytaj plik do ciągu, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Aby zdeserializować z pliku przy użyciu kodu asynchronicznego, wywołaj metodę <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>Deserializacja z UTF-8

Aby zdeserializować z UTF-8, wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>, które pobiera `Utf8JsonReader` lub `ReadOnlySpan<byte>`, jak pokazano w poniższych przykładach. W przykładach założono, że kod JSON znajduje się w tablicy bajtów o nazwie jsonUtf8Bytes.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Zachowanie deserializacji

* Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter. Można [określić wielkość liter](#case-insensitive-property-matching).
* Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.
* Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.
* Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana. Aby uzyskać więcej informacji, zobacz artykuł [dotyczący usługi GitHub 38569 w przypadku niemodyfikowalnej obsługi obiektów](https://github.com/dotnet/corefx/issues/38569) i [problem 38163 w przypadku obsługi właściwości tylko do odczytu](https://github.com/dotnet/corefx/issues/38163) w repozytorium dotnet/corefx w witrynie GitHub.
* Domyślnie wyliczenia są obsługiwane jako liczby. [Nazwy wyliczenia można serializować jako ciągi](#enums-as-strings).
* Pola nie są obsługiwane.
* Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON. Można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas).
* [Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.

[Konwertery niestandardowe można zaimplementować](system-text-json-converters-how-to.md) w celu zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.

## <a name="serialize-to-formatted-json"></a>Serializacja do sformatowanego pliku JSON

Aby wydrukować dane wyjściowe JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Oto przykład typu do serializacji i całkiem wydrukowanych danych wyjściowych JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a>Dostosowywanie nazw i wartości JSON

Domyślnie nazwy właściwości i klucze słownika nie są zmieniane w danych wyjściowych JSON, włącznie z wielkością liter. Wartości wyliczeniowe są reprezentowane jako liczby. W tej sekcji wyjaśniono, jak:

* [Dostosowywanie poszczególnych nazw właściwości](#customize-individual-property-names)
* [Konwertuj wszystkie nazwy właściwości na notacji CamelCase przypadku](#use-camel-case-for-all-json-property-names)
* [Implementowanie zasad nazewnictwa właściwości niestandardowych](#use-a-custom-json-property-naming-policy)
* [Konwertuj klucze słownika na notacji CamelCase](#camel-case-dictionary-keys)
* [Konwertuj wyliczenia na ciągi i notacji CamelCase wielkość liter](#enums-as-strings) 

W przypadku innych scenariuszy, które wymagają specjalnej obsługi nazw i wartości właściwości JSON, można [zaimplementować konwertery niestandardowe](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Dostosowywanie poszczególnych nazw właściwości

Aby ustawić nazwę poszczególnych właściwości, Użyj atrybutu [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Oto przykład typu do serializacji i powstającego JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

Nazwa właściwości ustawiona przez ten atrybut:

* Stosuje się w obu kierunkach dla serializacji i deserializacji.
* Ma pierwszeństwo przed zasadami nazewnictwa właściwości.

### <a name="use-camel-case-for-all-json-property-names"></a>Użyj notacji CamelCase przypadku dla wszystkich nazw właściwości JSON

Aby użyć notacji CamelCase przypadku dla wszystkich nazw właściwości JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

Zasady nazewnictwa właściwości przypadku notacji CamelCase:

* Dotyczy serializacji i deserializacji.
* Jest zastępowany przez atrybuty `[JsonPropertyName]`. Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie notacji CamelCase wielkości liter.

### <a name="use-a-custom-json-property-naming-policy"></a>Użyj niestandardowych zasad nazewnictwa właściwości JSON

Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę pochodzącą z <xref:System.Text.Json.JsonNamingPolicy> i Zastąp metodę <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

Następnie ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na wystąpienie klasy zasad nazewnictwa:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

Zasady nazewnictwa właściwości JSON:

* Dotyczy serializacji i deserializacji.
* Jest zastępowany przez atrybuty `[JsonPropertyName]`. Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest wielką literą.

### <a name="camel-case-dictionary-keys"></a>Klucze słownika przypadku notacji CamelCase

Jeśli właściwość obiektu, który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>`, klucze `string` można przekonwertować na notacji CamelCase. W tym celu ustaw <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

Serializacja obiektu przy użyciu słownika o nazwie `TemperatureRanges`, który ma pary klucz-wartość, `"ColdMinTemp", 20` i `"HotMinTemp", 40` spowoduje to wyjście JSON podobne do następującego przykładu:

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

Zasady nazewnictwa przypadków notacji CamelCase dla kluczy słownika mają zastosowanie tylko do serializacji. W przypadku deserializacji słownika klucze będą zgodne z plikiem JSON nawet wtedy, gdy dla `DictionaryKeyPolicy`określono `JsonNamingPolicy.CamelCase`.

### <a name="enums-as-strings"></a>Wyliczenia jako ciągi

Domyślnie wyliczenia są serializowane jako liczby. Aby serializować nazwy wyliczenia jako ciągi, użyj <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.

Załóżmy na przykład, że trzeba serializować następujące klasy, które mają Wyliczenie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Jeśli podsumowanie jest `Hot`, domyślnie serializowany kod JSON ma wartość liczbową 3:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

Następujący przykładowy kod serializować nazwy wyliczenia zamiast wartości liczbowych i konwertuje nazwy na notacji CamelCase:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

Wynikowy kod JSON wygląda podobnie do poniższego przykładu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Można również deserializować nazwy ciągów wyliczenia, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>Wyklucz właściwości z serializacji

Domyślnie wszystkie właściwości publiczne są serializowane. Jeśli nie chcesz, aby niektóre z nich pojawiały się w danych wyjściowych JSON, masz kilka opcji. W tej sekcji wyjaśniono, jak wykluczyć:

* [Poszczególne właściwości](#exclude-individual-properties)
* [Wszystkie właściwości tylko do odczytu](#exclude-all-read-only-properties)
* [Wszystkie właściwości o wartości null](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>Wyklucz pojedyncze właściwości

Aby zignorować poszczególne właściwości, Użyj atrybutu [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Oto przykład typu do serializacji i danych wyjściowych JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>Wyklucz wszystkie właściwości tylko do odczytu

Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej. Aby wykluczyć wszystkie właściwości tylko do odczytu, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Oto przykład typu do serializacji i danych wyjściowych JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Ta opcja ma zastosowanie tylko do serializacji. Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane.

### <a name="exclude-all-null-value-properties"></a>Wyklucz wszystkie właściwości wartości null

Aby wykluczyć wszystkie właściwości wartości null, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na `true`, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Oto przykład obiektu do serializacji i danych wyjściowych JSON:

|Właściwość |Wartość  |
|---------|---------|
| Data    | 8/1/2019 12:00:00 AM – 07:00|
| TemperatureCelsius| 25 |
| Podsumowanie| wartość null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

To ustawienie dotyczy serializacji i deserializacji. Aby uzyskać informacje o jego wpływie na deserializacji, zobacz [Ignore null podczas deserializacji](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Dostosuj kodowanie znaków

Domyślnie serializator wyprowadza wszystkie znaki nienależące do zestawu znaków ASCII.  Oznacza to, że zastępuje je `\uxxxx` gdzie `xxxx` jest kodem Unicode znaku.  Na przykład, jeśli właściwość `Summary` jest ustawiona na wartość cyrylicy жарко, obiekt `WeatherForecast` zostanie Zserializowany, jak pokazano w tym przykładzie:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Serializowanie zestawów znaków języka

Aby serializować zestawy znaków z co najmniej jednego języka bez ucieczki, określ [zakresy Unicode](xref:System.Text.Unicode.UnicodeRanges) podczas tworzenia wystąpienia <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Ten kod nie ma ucieczki znaków cyrylicy lub greckich. Jeśli właściwość `Summary` jest ustawiona na wartość cyrylicy жарко, obiekt `WeatherForecast` zostanie Zserializowany, jak pokazano w tym przykładzie:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Aby serializować wszystkie zestawy językowe bez ucieczki, użyj <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.

### <a name="serialize-specific-characters"></a>Serializacja określonych znaków

Alternatywą jest określenie pojedynczych znaków, które mają być dozwolone, bez konieczności ucieczki. Poniższy przykład serializacji tylko dwa pierwsze znaki жарко:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Oto przykład kodu JSON utworzonego przez poprzedni kod:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Serializować wszystkie znaki

Aby zminimalizować liczbę ucieczki, można użyć <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> W porównaniu z domyślnym koderem, koder `UnsafeRelaxedJsonEscaping` jest bardziej ograniczając, aby umożliwić Przechodzenie znaków przez niezmieniony:
>
> * Nie wpływa to na znaki w języku HTML, takie jak `<`, `>`, `&`i `'`.
> * Nie oferuje żadnej dodatkowej ochrony przed atakami na ataki typu XSS lub ujawnienie informacji, takich jak te, które mogą wynikać z klienta i serwera bez zgody na *zestaw znaków*.
>
> Używaj niebezpiecznego kodera tylko wtedy, gdy wiadomo, że klient będzie interpretować otrzymany ładunek jako zakodowany w formacie JSON UTF-8. Można na przykład użyć go, jeśli serwer wysyła nagłówek odpowiedzi `Content-Type: application/json; charset=utf-8`. Nigdy nie Zezwalaj na emitowanie nieprzetworzonych danych wyjściowych `UnsafeRelaxedJsonEscaping` do strony HTML lub `<script>` elementu.

## <a name="serialize-properties-of-derived-classes"></a>Serializowanie właściwości klas pochodnych

Serializacja polimorficzna nie jest obsługiwana w przypadku określenia w czasie kompilacji typu, który ma być serializowany. Załóżmy na przykład, że masz klasę `WeatherForecast` i klasę pochodną `WeatherForecastWithWind`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

I Załóżmy, że argument typu metody `Serialize` w czasie kompilacji jest `WeatherForecast`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

W tym scenariuszu Właściwość `WindSpeed` nie jest serializowana, nawet jeśli obiekt `weatherForecast` jest w rzeczywistości obiektem `WeatherForecastWithWind`. Tylko właściwości klasy bazowej są serializowane:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.

Aby serializować właściwości typu pochodnego, należy użyć jednej z następujących metod:

* Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A>, które pozwala określić typ w czasie wykonywania:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Zadeklaruj obiekt do serializacji jako `object`.

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

W poprzednim przykładowym scenariuszu oba podejścia powodują, że właściwość `WindSpeed` ma zostać uwzględniona w danych wyjściowych JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

Aby uzyskać informacje na temat deserializacji polimorficznej, zobacz [Obsługa deserializacji polimorficznej](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

## <a name="allow-comments-and-trailing-commas"></a>Zezwalaj na komentarze i końcowe przecinki

Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON. Aby zezwolić na komentarze w formacie JSON, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na `JsonCommentHandling.Skip`.
I aby zezwolić na końcowe przecinki, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na `true`. Poniższy przykład pokazuje, jak:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Oto przykładowy kod JSON z komentarzami i końcowym przecinkiem:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Dopasowanie właściwości bez uwzględniania wielkości liter

Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego. Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Oto przykład JSON z nazwami właściwości przypadku notacji CamelCase. Można ją zdeserializować do następującego typu, który ma nazwy właściwości przypadku języka Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Obsługa przepełnienia kodu JSON

Podczas deserializacji można odbierać dane w formacie JSON, które nie są reprezentowane przez właściwości typu docelowego. Załóżmy na przykład, że typ docelowy to:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

I kod JSON do deserializacji jest następujący:

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

W przypadku deserializacji kodu JSON pokazanego w pokazanym typie właściwości `DatesAvailable` i `SummaryWords` mają wartość Nowhere i są tracone. Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub `Dictionary<string,JsonElement>`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie przykładowym dodatkowe dane staną się parami klucz-wartość właściwości `ExtensionData`:

|Właściwość |Wartość  |Uwagi  |
|---------|---------|---------|
| Data    | 8/1/2019 12:00:00 AM – 07:00||
| TemperatureCelsius| 0 | Niezgodność z wielkością liter (`temperatureCelsius` w formacie JSON), więc właściwość nie jest ustawiona. |
| Podsumowanie | Ręczne ||
| ExtensionData — | temperatureCelsius: 25 |Ponieważ przypadek nie jest zgodny, ta właściwość JSON jest dodatkową i jest parą klucz-wartość w słowniku.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM – 07:00<br>8/2/2019 12:00:00 AM – 07:00 |Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.|
| |SummaryWords:<br>Ochłodzenia<br>Wiatr<br>Humid |Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.|

Gdy obiekt docelowy jest serializowany, pary wartości klucza danych rozszerzenia stają się właściwościami JSON tak samo jak w przychodzących danych JSON:

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

Zauważ, że nazwa właściwości `ExtensionData` nie jest wyświetlana w formacie JSON. Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.

## <a name="ignore-null-when-deserializing"></a>Ignoruj wartość null podczas deserializacji

Domyślnie, jeśli właściwość w formacie JSON ma wartość null, odpowiadająca jej właściwość w obiekcie docelowym ma wartość null. W niektórych scenariuszach właściwość target może mieć wartość domyślną i nie ma potrzeby przesłonięcia wartości domyślnej.

Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Załóżmy, że następujący kod JSON jest deserializowany:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Po deserializacji właściwość `Summary` obiektu `WeatherForecastWithDefault` ma wartość null.

Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na `true`, jak pokazano w następującym przykładzie:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

W przypadku tej opcji Właściwość `Summary` obiektu `WeatherForecastWithDefault` jest wartością domyślną "Brak podsumowania" po deserializacji.

Wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe. Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki. Aby uzyskać więcej informacji, zobacz artykuł [dotyczący problemu 40922 w przypadku typów wartości niedopuszczających wartości null](https://github.com/dotnet/corefx/issues/40922) w repozytorium dotnet/corefx w witrynie GitHub.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter i JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> jest wysoce wydajnym, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, Odczytaj z `ReadOnlySpan<byte>`. `Utf8JsonReader` jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji. Metoda <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> używa `Utf8JsonReader` w obszarze okładek.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> to wysoce wydajny sposób pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy .NET, takich jak `String`, `Int32`i `DateTime`. Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych. Metoda <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> używa `Utf8JsonWriter` w obszarze okładek.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> zapewnia możliwość tworzenia Document Object Model tylko do odczytu (DOM) przy użyciu `Utf8JsonReader`. DOM zapewnia losowy dostęp do danych w ładunku JSON. Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem typu <xref:System.Text.Json.JsonElement>. Typ `JsonElement` zapewnia moduł wyliczający tablic i obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET. `JsonDocument` uwidacznia Właściwość <xref:System.Text.Json.JsonDocument.RootElement>.

W poniższych sekcjach pokazano, jak używać tych narzędzi do odczytywania i pisania danych JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Korzystanie z JsonDocument do uzyskiwania dostępu do danych

Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.JsonDocument> do losowego dostępu do danych w ciągu JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Powyższy kod:

* Przyjęto, że kod JSON do analizy znajduje się w ciągu o nazwie `jsonString`.
* Oblicza średnią ocenę dla obiektów w tablicy `Students`, która ma właściwość `Grade`. 
* Przypisuje domyślną ocenę 70 dla studentów, którzy nie posiadają klasy.
* Zlicza uczniów przez zwiększenie zmiennej `count` przy każdej iteracji. Alternatywą jest wywołanie <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, jak pokazano w następującym przykładzie:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Oto przykład pliku JSON, który jest przetwarzany przez ten kod:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>Użyj JsonDocument, aby zapisać kod JSON

Poniższy przykład pokazuje, jak napisać kod JSON z <xref:System.Text.Json.JsonDocument>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Powyższy kod:

* Odczytuje plik JSON, ładuje dane do `JsonDocument`i zapisuje sformatowany plik JSON w formacie.
* Używa <xref:System.Text.Json.JsonDocumentOptions>, aby określić, że komentarze w wejściowym formacie JSON są dozwolone, ale ignorowane.
* Po zakończeniu wywołuje <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> w składniku zapisywania. Alternatywą jest umożliwienie składnika zapisywania AutoFlush, gdy zostanie on usunięty. 

Oto przykład danych wejściowych JSON do przetworzenia przez przykładowy kod:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

Wynikiem są następujące niedrukowane dane wyjściowe JSON:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Użyj Utf8JsonWriter

Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.Utf8JsonWriter>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Użyj Utf8JsonReader

Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.Utf8JsonReader>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Poprzedni kod założono, że zmienna `jsonUtf8` jest tablicą bajtów, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrowanie danych za pomocą Utf8JsonReader

Poniższy przykład pokazuje, jak odczytywać plik synchronicznie i wyszukiwać wartość:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

Powyższy kod:

* Przyjęto założenie, że plik jest zakodowany jako UTF-16 i transkoduje go do UTF-8. Plik zakodowany jako UTF-8 można odczytać bezpośrednio w `ReadOnlySpan<byte>`, używając następującego kodu:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* Przyjęto, że kod JSON zawiera tablicę obiektów, a każdy obiekt może zawierać właściwość "name" typu String.
* Zlicza obiekty i `name` wartości właściwości, które kończą się na Uniwersytecie.

Oto przykład JSON, który może odczytać poprzedzający kod. Otrzymany komunikat podsumowujący to "2 z 4 mają nazwy kończące się na" University ":

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a>Dodatkowe zasoby

* [System. Text. JSON — Omówienie](system-text-json-overview.md)
* [Dokumentacja interfejsu API System. Text. JSON](xref:System.Text.Json)
* [Zapisuj niestandardowe konwertery dla elementu System. Text. JSON](system-text-json-converters-how-to.md)
* [Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON](../datetime/system-text-json-support.md)
* [Problemy z usługą GitHub w repozytorium dotnet/corefx z etykietą JSON-funkcja-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc) 
