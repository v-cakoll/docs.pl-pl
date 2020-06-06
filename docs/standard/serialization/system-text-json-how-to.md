---
title: Jak serializować i deserializować kod JSON przy użyciu języka C# — .NET
description: W tym artykule pokazano, jak używać System.Text.Json przestrzeni nazw do serializacji i deserializacji z JSON w programie .NET. Zawiera przykładowy kod.
ms.date: 05/13/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 7ad2721f12c5d14b61b35ecf7696ff0d6a6f27da
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289515"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>Jak serializować i deserializować (Marshaling and unmarshaling) JSON w programie .NET

W tym artykule pokazano, jak używać <xref:System.Text.Json> przestrzeni nazw do serializacji i deserializacji do i z JavaScript Object Notation (JSON). W przypadku przenoszenia istniejącego kodu z programu `Newtonsoft.Json` zapoznaj się z tematem [jak `System.Text.Json` przeprowadzić migrację do programu ](system-text-json-migrate-from-newtonsoft-how-to.md).

Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).

Większość przykładowych kodów serializacji <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> do `true` "DB-Print" w formacie JSON (z wcięciem i białym znakiem). Do użycia w środowisku produkcyjnym zwykle przyjmuje się wartość domyślną `false` dla tego ustawienia.

Przykłady kodu odnoszą się do następującej klasy i wariantów:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>Przestrzenie nazw

<xref:System.Text.Json>Przestrzeń nazw zawiera wszystkie punkty wejścia i typy główne. <xref:System.Text.Json.Serialization>Przestrzeń nazw zawiera atrybuty i interfejsy API dla zaawansowanych scenariuszy i dostosowań specyficznych dla serializacji i deserializacji. Przykłady kodu przedstawione w tym artykule wymagają `using` dyrektyw dla jednej lub obu tych przestrzeni nazw:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atrybuty z <xref:System.Runtime.Serialization> przestrzeni nazw nie są obecnie obsługiwane w programie `System.Text.Json` .

## <a name="how-to-write-net-objects-to-json-serialize"></a>Pisanie obiektów .NET w formacie JSON (Serializacja)

Aby zapisać dane JSON do ciągu lub do pliku, wywołaj <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> metodę.

Poniższy przykład tworzy kod JSON jako ciąg:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

Poniższy przykład używa kodu synchronicznego do utworzenia pliku JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

W poniższym przykładzie jest tworzony plik JSON przy użyciu kodu asynchronicznego:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Powyższe przykłady używają wnioskowania typu dla serializowanego typu. Przeciążenie `Serialize()` przyjmuje parametr typu ogólnego:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Przykład serializacji

Oto przykładowa Klasa, która zawiera kolekcje i zagnieżdżoną klasę:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

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

Aby serializować do UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> metodę:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<xref:System.Text.Json.JsonSerializer.Serialize%2A>Dostępne jest również Przeciążenie, które trwa <xref:System.Text.Json.Utf8JsonWriter> .

Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach. Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).

## <a name="serialization-behavior"></a>Zachowanie serializacji

* Domyślnie wszystkie właściwości publiczne są serializowane. Można [określić właściwości do wykluczenia](#exclude-properties-from-serialization).
* [Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem języka HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Domyślnie JSON jest zminimalizowanego. Można tu [wydrukować kod JSON](#serialize-to-formatted-json).
* Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET. Można [dostosować wielkość liter w nazwach JSON](#customize-json-names-and-values).
* Wykryto odwołania cykliczne i zostały zgłoszone wyjątki.
* Obecnie pola są wykluczone.

Obsługiwane typy to:

* Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.
* Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tablice jednowymiarowe i nieregularne ( `ArrayName[][]` ).
* `Dictionary<string,TValue>`gdzie `TValue` is to `object` , `JsonElement` lub poco.
* Kolekcje z następujących przestrzeni nazw.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Można [zaimplementować niestandardowe konwertery](system-text-json-converters-how-to.md) w celu obsługi dodatkowych typów lub zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Jak odczytywać dane JSON do obiektów .NET (deserializacji)

Aby zdeserializować z ciągu lub pliku, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> metodę.

Poniższy przykład odczytuje dane JSON z ciągu i tworzy wystąpienie `WeatherForecast` klasy pokazanej wcześniej dla [przykładu serializacji](#serialization-example):

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Aby zdeserializować z pliku przy użyciu kodu synchronicznego, Odczytaj plik do ciągu, jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Aby zdeserializować z pliku przy użyciu kodu asynchronicznego, wywołaj <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> metodę:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>Deserializacja z UTF-8

Aby zdeserializować z UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Przeciążenie, które pobiera `Utf8JsonReader` lub a `ReadOnlySpan<byte>` , jak pokazano w poniższych przykładach. W przykładach założono, że kod JSON znajduje się w tablicy bajtów o nazwie jsonUtf8Bytes.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Zachowanie deserializacji

* Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter. Można [określić wielkość liter](#case-insensitive-property-matching).
* Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.
* Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.
* Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana.
* Domyślnie wyliczenia są obsługiwane jako liczby. [Nazwy wyliczenia można serializować jako ciągi](#enums-as-strings).
* Pola nie są obsługiwane.
* Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON. Można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas).
* [Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.

[Konwertery niestandardowe można zaimplementować](system-text-json-converters-how-to.md) w celu zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.

## <a name="serialize-to-formatted-json"></a>Serializacja do sformatowanego pliku JSON

Aby całkiem wydrukować dane wyjściowe JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Oto przykład typu do serializacji i całkiem wydrukowanych danych wyjściowych JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

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

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

Aby użyć notacji CamelCase przypadku wszystkich nazw właściwości JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` tak, jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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
* Jest zastępowany przez `[JsonPropertyName]` atrybuty. Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest notacji CamelCase.

### <a name="use-a-custom-json-property-naming-policy"></a>Użyj niestandardowych zasad nazewnictwa właściwości JSON

Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę, która pochodzi od <xref:System.Text.Json.JsonNamingPolicy> i przesłania <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> metodę, jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

Następnie ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> Właściwość na wystąpienie klasy zasad nazewnictwa:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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
* Jest zastępowany przez `[JsonPropertyName]` atrybuty. Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest wielką literą.

### <a name="camel-case-dictionary-keys"></a>Klucze słownika przypadku notacji CamelCase

Jeśli właściwość obiektu, który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>` , `string` klucze mogą być konwertowane na notacji CamelCase przypadku. W tym celu ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase` , jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

Serializacja obiektu ze słownikiem o nazwie `TemperatureRanges` , który ma pary klucz-wartość `"ColdMinTemp", 20` i `"HotMinTemp", 40` spowodowałaby wyjście JSON podobne do poniższego przykładu:

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

Zasady nazewnictwa przypadków notacji CamelCase dla kluczy słownika mają zastosowanie tylko do serializacji. W przypadku deserializacji słownika klucze będą zgodne z plikiem JSON nawet w przypadku określenia `JsonNamingPolicy.CamelCase` dla `DictionaryKeyPolicy` .

### <a name="enums-as-strings"></a>Wyliczenia jako ciągi

Domyślnie wyliczenia są serializowane jako liczby. Aby serializować nazwy wyliczenia jako ciągi, użyj <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .

Załóżmy na przykład, że trzeba serializować następujące klasy, które mają Wyliczenie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Jeśli podsumowanie jest `Hot` , domyślnie serializowany kod JSON ma wartość liczbową 3:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

Następujący przykładowy kod serializować nazwy wyliczenia zamiast wartości liczbowych i konwertuje nazwy na notacji CamelCase:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

Wynikowy kod JSON wygląda podobnie do poniższego przykładu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Można również deserializować nazwy ciągów wyliczenia, jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>Wyklucz właściwości z serializacji

Domyślnie wszystkie właściwości publiczne są serializowane. Jeśli nie chcesz, aby niektóre z nich pojawiały się w danych wyjściowych JSON, masz kilka opcji. W tej sekcji wyjaśniono, jak wykluczyć:

* [Poszczególne właściwości](#exclude-individual-properties)
* [Wszystkie właściwości tylko do odczytu](#exclude-all-read-only-properties)
* [Wszystkie właściwości o wartości null](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>Wyklucz pojedyncze właściwości

Aby zignorować poszczególne właściwości, Użyj atrybutu [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Oto przykład typu do serializacji i danych wyjściowych JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>Wyklucz wszystkie właściwości tylko do odczytu

Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej. Aby wykluczyć wszystkie właściwości tylko do odczytu, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true` , jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Oto przykład typu do serializacji i danych wyjściowych JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Ta opcja ma zastosowanie tylko do serializacji. Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane.

### <a name="exclude-all-null-value-properties"></a>Wyklucz wszystkie właściwości wartości null

Aby wykluczyć wszystkie właściwości wartości null, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> Właściwość na `true` , jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Oto przykład obiektu do serializacji i danych wyjściowych JSON:

|Właściwość |Wartość  |
|---------|---------|
| Date    | 8/1/2019 12:00:00 AM – 07:00|
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

Domyślnie serializator wyprowadza wszystkie znaki nienależące do zestawu znaków ASCII.  Oznacza to, że zastępuje je, `\uxxxx` gdzie `xxxx` jest kodem Unicode znaku.  Na przykład, jeśli `Summary` Właściwość jest ustawiona na wartość cyrylicy жарко, `WeatherForecast` obiekt jest serializowany, jak pokazano w poniższym przykładzie:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Serializowanie zestawów znaków języka

Aby serializować zestawy znaków z co najmniej jednego języka bez ucieczki, określ [zakresy Unicode](xref:System.Text.Unicode.UnicodeRanges) podczas tworzenia wystąpienia <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Ten kod nie ma ucieczki znaków cyrylicy lub greckich. Jeśli `Summary` Właściwość jest ustawiona na wartość cyrylicy жарко, `WeatherForecast` obiekt jest serializowany, jak pokazano w poniższym przykładzie:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Aby serializować wszystkie zestawy językowe bez ucieczki, użyj <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .

### <a name="serialize-specific-characters"></a>Serializacja określonych znaków

Alternatywą jest określenie pojedynczych znaków, które mają być dozwolone, bez konieczności ucieczki. Poniższy przykład serializacji tylko dwa pierwsze znaki жарко:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Oto przykład kodu JSON utworzonego przez poprzedni kod:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Serializować wszystkie znaki

Aby zminimalizować liczbę ucieczki, można użyć <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> W porównaniu z domyślnym koderem `UnsafeRelaxedJsonEscaping` koder jest bardziej ograniczając, aby umożliwić przekazywanie znaków przez niezmieniony:
>
> * Nie ucieczk znaków w języku HTML, takich jak `<` , `>` , `&` , i `'` .
> * Nie oferuje żadnej dodatkowej ochrony przed atakami na ataki typu XSS lub ujawnienie informacji, takich jak te, które mogą wynikać z klienta i serwera bez zgody na *zestaw znaków*.
>
> Używaj niebezpiecznego kodera tylko wtedy, gdy wiadomo, że klient będzie interpretować otrzymany ładunek jako zakodowany w formacie JSON UTF-8. Można na przykład użyć go, jeśli serwer wysyła nagłówek odpowiedzi `Content-Type: application/json; charset=utf-8` . Nigdy nie Zezwalaj na `UnsafeRelaxedJsonEscaping` emitowanie nieprzetworzonych danych wyjściowych do strony HTML lub `<script>` elementu.

## <a name="serialize-properties-of-derived-classes"></a>Serializowanie właściwości klas pochodnych

Serializacja hierarchii typów polimorficznych nie jest obsługiwana. Na przykład, jeśli właściwość jest zdefiniowana jako interfejs lub Klasa abstrakcyjna, tylko właściwości zdefiniowane w interfejsie lub klasie abstrakcyjnej są serializowane, nawet jeśli typ środowiska uruchomieniowego ma dodatkowe właściwości. Wyjątki dotyczące tego zachowania zostały omówione w tej sekcji.

Załóżmy na przykład, że masz `WeatherForecast` klasę i klasę pochodną `WeatherForecastDerived` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

I Załóżmy, że argument typu `Serialize` metody w czasie kompilacji to `WeatherForecast` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

W tym scenariuszu `WindSpeed` Właściwość nie jest serializowana, nawet jeśli `weatherForecast` obiekt jest rzeczywiście `WeatherForecastDerived` obiektem. Tylko właściwości klasy bazowej są serializowane:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.

Aby serializować właściwości typu pochodnego w poprzednim przykładzie, należy użyć jednej z następujących metod:

* Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A> , które pozwala określić typ w czasie wykonywania:

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Zadeklaruj obiekt, który ma zostać Zserializowany jako `object` .

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

W poprzednim przykładowym scenariuszu oba podejścia powodują, że `WindSpeed` Właściwość powinna zostać uwzględniona w danych wyjściowych JSON:

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> Te podejścia zapewniają serializację polimorficzne tylko dla obiektu głównego, który ma być serializowany, a nie dla właściwości tego obiektu głównego.

Można uzyskać serializację polimorficzny dla obiektów niższego poziomu, jeśli zdefiniujesz je jako typ `object` . Na przykład załóżmy, `WeatherForecast` że Klasa ma właściwość o nazwie `PreviousForecast` , która może być zdefiniowana jako typ `WeatherForecast` lub `object` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

Jeśli `PreviousForecast` Właściwość zawiera wystąpienie `WeatherForecastDerived` :

* Dane wyjściowe JSON z serializacji `WeatherForecastWithPrevious` **nie obejmują** `WindSpeed` .
* Dane wyjściowe JSON z serializacji `WeatherForecastWithPreviousAsObject` **obejmują** `WindSpeed` .

Aby serializować `WeatherForecastWithPreviousAsObject` , nie jest konieczne wywołanie `Serialize<object>` lub `GetType` ponieważ obiekt główny nie jest tym, który może znajdować się w typie pochodnym. Poniższy przykład kodu nie wywołuje `Serialize<object>` lub `GetType` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

Powyższy kod poprawnie serializować `WeatherForecastWithPreviousAsObject` :

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

To samo podejście do definiowania właściwości jako `object` współdziałanie z interfejsami. Załóżmy, że masz następujący interfejs i implementacja, i chcesz serializować klasę o właściwościach zawierających wystąpienia implementacji:

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

Podczas serializacji wystąpienia elementu `Forecasts` , `Tuesday` wyświetlana `WindSpeed` jest tylko właściwość, ponieważ `Tuesday` jest zdefiniowana jako `object` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

Poniższy przykład pokazuje kod JSON, który wynika z poprzedniego kodu:

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

Aby uzyskać więcej informacji na temat **serializacji**polimorficznej i informacje o **deserializacji**, zobacz [Jak przeprowadzić migrację z Newtonsoft.Json do System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).

## <a name="allow-comments-and-trailing-commas"></a>Zezwalaj na komentarze i końcowe przecinki

Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON. Aby zezwolić na komentarze w formacie JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> Właściwość na `JsonCommentHandling.Skip` .
I aby zezwolić na końcowe przecinki, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> Właściwość na `true` . Poniższy przykład pokazuje, jak:

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Oto przykładowy kod JSON z komentarzami i końcowym przecinkiem:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Dopasowanie właściwości bez uwzględniania wielkości liter

Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego. Aby zmienić to zachowanie, ustaw opcję <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Oto przykład JSON z nazwami właściwości przypadku notacji CamelCase. Można ją zdeserializować do następującego typu, który ma nazwy właściwości przypadku języka Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Obsługa przepełnienia kodu JSON

Podczas deserializacji można odbierać dane w formacie JSON, które nie są reprezentowane przez właściwości typu docelowego. Załóżmy na przykład, że typ docelowy to:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

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

W przypadku deserializacji kodu JSON pokazanego w pokazanym typie, `DatesAvailable` `SummaryWords` właściwości i mają wartość Nowhere to go i są tracone. Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub `Dictionary<string,JsonElement>` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie próbkowania dodatkowe dane staną się parami klucz-wartość `ExtensionData` Właściwości:

|Właściwość |Wartość  |Uwagi  |
|---------|---------|---------|
| Date    | 8/1/2019 12:00:00 AM – 07:00||
| TemperatureCelsius| 0 | Niezgodność z rozróżnianiem wielkości liter ( `temperatureCelsius` w formacie JSON), więc właściwość nie jest ustawiona. |
| Podsumowanie | Gorąca ||
| ExtensionData — | temperatureCelsius: 25 |Ponieważ przypadek nie jest zgodny, ta właściwość JSON jest dodatkową i jest parą klucz-wartość w słowniku.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM – 07:00<br>8/2/2019 12:00:00 AM – 07:00 |Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.|
| |SummaryWords:<br>Chłodna<br>Wiatr<br>Humid |Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.|

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

Zauważ, że `ExtensionData` Nazwa właściwości nie pojawia się w formacie JSON. Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.

## <a name="ignore-null-when-deserializing"></a>Ignoruj wartość null podczas deserializacji

Domyślnie, jeśli właściwość w formacie JSON ma wartość null, odpowiadająca jej właściwość w obiekcie docelowym ma wartość null. W niektórych scenariuszach właściwość target może mieć wartość domyślną i nie ma potrzeby przesłonięcia wartości domyślnej.

Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Załóżmy, że następujący kod JSON jest deserializowany:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Po deserializacji `Summary` Właściwość `WeatherForecastWithDefault` obiektu ma wartość null.

Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> wartość `true` tak, jak pokazano w następującym przykładzie:

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

W przypadku tej opcji `Summary` Właściwość `WeatherForecastWithDefault` obiektu jest wartością domyślną "Brak podsumowania" po deserializacji.

Wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe. Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter i JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>jest wysoką wydajnością, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, Odczytaj z `ReadOnlySpan<byte>` lub `ReadOnlySequence<byte>` . `Utf8JsonReader`Jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji. <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>Metoda używa `Utf8JsonReader` w obszarze okładki.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>jest wysoce wydajnym sposobem pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy .NET, takich jak `String` , `Int32` , i `DateTime` . Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych. <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>Metoda używa `Utf8JsonWriter` w obszarze okładki.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>zapewnia możliwość tworzenia Document Object Model tylko do odczytu (DOM) za pomocą programu `Utf8JsonReader` . DOM zapewnia losowy dostęp do danych w ładunku JSON. Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typu. `JsonElement`Typ udostępnia moduł wyliczający tablic i obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET. `JsonDocument`uwidacznia <xref:System.Text.Json.JsonDocument.RootElement> Właściwość.

W poniższych sekcjach pokazano, jak używać tych narzędzi do odczytywania i pisania danych JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Korzystanie z JsonDocument do uzyskiwania dostępu do danych

Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.JsonDocument> klasy do losowego dostępu do danych w ciągu JSON:

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Powyższy kod ma następujące działanie:

* Przyjęto, że kod JSON do analizy jest w ciągu o nazwie `jsonString` .
* Oblicza średnią ocenę dla obiektów w `Students` tablicy, która ma `Grade` Właściwość.
* Przypisuje domyślną ocenę 70 dla studentów, którzy nie posiadają klasy.
* Zlicza uczniów przez zwiększenie `count` zmiennej przy każdej iteracji. Alternatywą jest wywołanie <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , jak pokazano w następującym przykładzie:

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Oto przykład pliku JSON, który jest przetwarzany przez ten kod:

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>Użyj JsonDocument, aby zapisać kod JSON

Poniższy przykład pokazuje, jak napisać kod JSON z <xref:System.Text.Json.JsonDocument> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Powyższy kod ma następujące działanie:

* Odczytuje plik JSON, ładuje dane do `JsonDocument` i zapisuje sformatowany plik JSON w formacie.
* Używa <xref:System.Text.Json.JsonDocumentOptions> do określenia, czy komentarze w wejściowym formacie JSON są dozwolone, ale ignorowane.
* Po zakończeniu wywołania <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> na składniku zapisywania. Alternatywą jest umożliwienie składnika zapisywania AutoFlush, gdy zostanie on usunięty.

Oto przykład danych wejściowych JSON do przetworzenia przez przykładowy kod:

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

Wynikiem są następujące niedrukowane dane wyjściowe JSON:

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Użyj Utf8JsonWriter

Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.Utf8JsonWriter> klasy:

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Użyj Utf8JsonReader

Poniższy przykład pokazuje, jak używać <xref:System.Text.Json.Utf8JsonReader> klasy:

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Poprzedni kod założono, że `jsonUtf8` zmienna jest tablicą bajtową, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrowanie danych za pomocą Utf8JsonReader

Poniższy przykład pokazuje, jak odczytywać plik synchronicznie i wyszukiwać wartość:

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

Powyższy kod ma następujące działanie:

* Przyjęto, że kod JSON zawiera tablicę obiektów, a każdy obiekt może zawierać właściwość "name" typu String.
* Zlicza obiekty i wartości właściwości "name", które kończą się znakiem "University".
* Przyjęto założenie, że plik jest zakodowany jako UTF-16 i transkoduje go do UTF-8. Plik zakodowany jako UTF-8 może być odczytywany bezpośrednio do programu `ReadOnlySpan<byte>` , przy użyciu następującego kodu:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  Jeśli plik zawiera znacznik kolejności bajtów UTF-8, usuń go przed przekazaniem bajtów do `Utf8JsonReader` , ponieważ czytnik oczekuje tekstu. W przeciwnym razie BOM jest traktowany jako nieprawidłowy kod JSON, a czytelnik zgłasza wyjątek.

Oto przykład JSON, który może odczytać poprzedzający kod. Otrzymany komunikat podsumowujący to "2 z 4 mają nazwy kończące się na" University ":

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a>Odczytaj ze strumienia przy użyciu Utf8JsonReader

W przypadku odczytywania dużego pliku (na przykład gigabajta lub więcej) można uniknąć konieczności załadowania całego pliku do pamięci jednocześnie. W tym scenariuszu można użyć <xref:System.IO.FileStream> .

W przypadku `Utf8JsonReader` odczytywania ze strumienia przy użyciu programu, obowiązują następujące reguły:

* Bufor zawierający częściowy ładunek JSON musi być co najmniej tak duży jak największy token JSON w tym samym czasie, aby czytnik mógł postępować dalej.
* Bufor musi być co najmniej tak duży jak największą sekwencję białych znaków w formacie JSON.
* Czytnik nie śledzi danych, które zostały odczytane, dopóki nie zostaną całkowicie odczytane dalej <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> w ładunku JSON. Tak więc, gdy bajty są pozostawione w buforze, należy ponownie przekazać je do czytnika. Możesz użyć, <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> Aby określić, ile bajtów pozostało.

Poniższy kod ilustruje sposób odczytywania ze strumienia. Przykład pokazuje <xref:System.IO.MemoryStream> . Podobny kod będzie działał z <xref:System.IO.FileStream> , z wyjątkiem sytuacji, gdy `FileStream` zawiera BOM w formacie UTF-8. W takim przypadku należy rozdzielić te trzy bajty z buforu przed przekazaniem pozostałych bajtów do `Utf8JsonReader` . W przeciwnym razie czytelnik zgłosi wyjątek, ponieważ BOM nie jest traktowany jako prawidłowa część JSON.

Przykładowy kod rozpoczyna się od buforu 4 KB i podwaja rozmiar buforu za każdym razem, gdy okaże się, że rozmiar nie jest wystarczająco duży, aby dopasować pełny token JSON, który jest wymagany, aby czytnik mógł postępować w ładunku JSON. Przykład JSON podany w fragmencie kodu wyzwala zwiększenie rozmiaru buforu tylko wtedy, gdy ustawisz bardzo mały początkowy rozmiar buforu, na przykład 10 bajtów. Jeśli ustawisz początkowy rozmiar buforu na 10, `Console.WriteLine` instrukcje ilustrują przyczynę i wpływ rozmiaru buforu. W początkowym rozmiarze bufora 4 KB cały przykładowy kod JSON jest pokazywany przez każdy z nich `Console.WriteLine` , a rozmiar buforu nigdy nie musi zostać zwiększony.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

W powyższym przykładzie nie określono limitu rozmiaru buforu. Jeśli rozmiar tokenu jest zbyt duży, kod może zakończyć się niepowodzeniem z <xref:System.OutOfMemoryException> wyjątkiem. Taka sytuacja może wystąpić, jeśli kod JSON zawiera token o rozmiarze około 1 GB lub więcej, ponieważ Podwajanie rozmiaru 1 GB spowoduje, że rozmiar jest zbyt duży, aby zmieścił się w `int32` buforze.

## <a name="additional-resources"></a>Zasoby dodatkowe

* [System.Text.JsonPodsumowanie](system-text-json-overview.md)
* [Jak pisać konwertery niestandardowe](system-text-json-converters-how-to.md)
* [Jak przeprowadzić migrację zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Obsługa DateTime i DateTimeOffset wSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonDokumentacja interfejsu API](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
