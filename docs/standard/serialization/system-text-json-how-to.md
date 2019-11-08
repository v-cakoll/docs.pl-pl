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
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>Jak serializować i deserializować kod JSON w programie .NET

> [!IMPORTANT]
> Dokumentacja serializacji JSON jest w przygotowaniu. Ten artykuł nie obejmuje wszystkich scenariuszy. Aby uzyskać więcej informacji, należy zapoznać się z tematami [System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) w repozytorium dotnet/corefx w witrynie GitHub, w szczególności z etykietą [JSON-funkcja-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).

W tym artykule pokazano, jak używać przestrzeni nazw <xref:System.Text.Json> do serializacji i deserializacji do i z JavaScript Object Notation (JSON). Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).

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

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

Poniższy przykład używa kodu synchronicznego do utworzenia pliku JSON:

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

W poniższym przykładzie jest tworzony plik JSON przy użyciu kodu asynchronicznego:

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

Powyższe przykłady używają wnioskowania typu dla serializowanego typu. Przeciążenie `Serialize()` przyjmuje parametr typu ogólnego:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a>Przykład serializacji

Oto przykładowy typ zawierający kolekcje i klasy zagnieżdżone:

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

Dane wyjściowe JSON serializowania wystąpienia poprzedniego typu wyglądają podobnie jak w poniższym przykładzie. Dane wyjściowe JSON domyślnie są zminimalizowanego: 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

W poniższym przykładzie przedstawiono ten sam kod JSON, sformatowany (to jest całkiem wydruk z odstępami i wcięciami):

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

### <a name="serialize-to-utf-8"></a>Serializacja do UTF-8

Aby serializować do UTF-8, wywołaj metodę <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

Dostępne jest również Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A>, które pobiera <xref:System.Text.Json.Utf8JsonWriter>.

Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach. Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).

## <a name="serialization-behavior"></a>Zachowanie serializacji

* Domyślnie wszystkie właściwości publiczne są serializowane. Można [określić właściwości do wykluczenia](#exclude-properties-from-serialization).
* [Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem kodu HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON](https://tools.ietf.org/html/rfc8259#section-7).
* Domyślnie JSON jest zminimalizowanego. Można tu [wydrukować kod JSON](#serialize-to-formatted-json).
* Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET. Można [dostosować wielkość liter w nazwach JSON](#customize-json-names-and-values).
* Wykryto odwołania cykliczne i zostały zgłoszone wyjątki. Aby uzyskać więcej informacji, zobacz [problem dotyczący odwołań cyklicznych](https://github.com/dotnet/corefx/issues/38579) w repozytorium dotnet/corefx w witrynie GitHub.
* Obecnie pola są wykluczone.

Obsługiwane typy to:

* Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.
* Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tablice jednowymiarowe i nieregularne (`ArrayName[][]`).
* `Dictionary<string,TValue>` gdzie `TValue` jest `object`, `JsonElement` lub POCO.
* Kolekcje z następujących przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [problem związany z obsługą kolekcji](https://github.com/dotnet/corefx/issues/36643) w repozytorium dotnet/corefx w witrynie GitHub.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Można [zaimplementować niestandardowe konwertery](system-text-json-converters-how-to.md) do obsługi dodatkowych typów lub udostępniać funkcje, które nie są obsługiwane przez wbudowane konwertery.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Jak odczytywać dane JSON do obiektów .NET (deserializacji)

Aby zdeserializować z ciągu lub pliku, wywołaj metodę <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.

Poniższy przykład odczytuje kod JSON z ciągu:

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

Aby zdeserializować z pliku przy użyciu kodu synchronicznego, Odczytaj plik do ciągu, jak pokazano w następującym przykładzie:

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

Aby zdeserializować z pliku przy użyciu kodu asynchronicznego, wywołaj metodę <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

Przykładowy typ i odpowiedni kod JSON można znaleźć w sekcji [przykład serializacji](#serialization-example) .

### <a name="deserialize-from-utf-8"></a>Deserializacja z UTF-8

Aby zdeserializować z UTF-8, wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>, które pobiera `Utf8JsonReader` lub `ReadOnlySpan<byte>`, jak pokazano w poniższych przykładach. W przykładach założono, że kod JSON znajduje się w tablicy bajtów o nazwie jsonUtf8Bytes.

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a>Zachowanie deserializacji

* Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter. Można [określić wielkość liter](#case-insensitive-property-matching).
* Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.
* Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.
* Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana. Aby uzyskać więcej informacji, zobacz [problem z obsługą usługi GitHub dla niemodyfikowalnych obiektów](https://github.com/dotnet/corefx/issues/38569) i [problem związany z obsługą właściwości tylko do odczytu](https://github.com/dotnet/corefx/issues/38163) w repozytorium dotnet/corefx w witrynie GitHub.
* Domyślnie wyliczenia są obsługiwane jako liczby. [Nazwy wyliczenia można serializować jako ciągi](#enums-as-strings).
* Pola nie są obsługiwane.
* Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON. Można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas).
* [Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.

[Konwertery niestandardowe można zaimplementować](system-text-json-converters-how-to.md) w celu zapewnienia funkcjonalności, która nie jest obsługiwana przez wbudowane konwertery.

## <a name="serialize-to-formatted-json"></a>Serializacja do sformatowanego pliku JSON

Aby wydrukować dane wyjściowe JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Oto przykład typu do serializacji i całkiem wydrukowanych danych wyjściowych JSON:

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

## <a name="customize-json-names-and-values"></a>Dostosowywanie nazw i wartości JSON

Domyślnie nazwy właściwości i klucze słownika nie są zmieniane w danych wyjściowych JSON, włącznie z wielkością liter. Wartości wyliczeniowe są reprezentowane jako liczby. W tej sekcji wyjaśniono, jak:

* Dostosowywanie poszczególnych nazw właściwości
* Konwertuj wszystkie nazwy właściwości na notacji CamelCase przypadku
* Implementowanie zasad nazewnictwa właściwości niestandardowych
* Konwertuj klucze słownika na notacji CamelCase
* Konwertuj wyliczenia na ciągi i notacji CamelCase wielkość liter 

W przypadku innych scenariuszy, które wymagają specjalnej obsługi nazw i wartości właściwości JSON, można [zaimplementować konwertery niestandardowe](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Dostosowywanie poszczególnych nazw właściwości

Aby ustawić nazwę poszczególnych właściwości, Użyj atrybutu [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Oto przykład typu do serializacji i powstającego JSON:

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

Nazwa właściwości ustawiona przez ten atrybut:

* Stosuje się w obu kierunkach dla serializacji i deserializacji.
* Ma pierwszeństwo przed zasadami nazewnictwa właściwości.

### <a name="use-camel-case-for-all-json-property-names"></a>Użyj notacji CamelCase przypadku dla wszystkich nazw właściwości JSON

Aby użyć notacji CamelCase przypadku dla wszystkich nazw właściwości JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:

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

Zasady nazewnictwa właściwości przypadku notacji CamelCase:

* Dotyczy serializacji i deserializacji.
* Jest zastępowany przez atrybuty `[JsonPropertyName]`. Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie notacji CamelCase wielkości liter.

### <a name="use-a-custom-json-property-naming-policy"></a>Użyj niestandardowych zasad nazewnictwa właściwości JSON

Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę pochodzącą z <xref:System.Text.Json.JsonNamingPolicy> i Zastąp metodę <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, jak pokazano w następującym przykładzie:

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Następnie ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na wystąpienie klasy zasad nazewnictwa:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Oto przykładowa Klasa do serializacji i danych wyjściowych JSON:

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

Zasady nazewnictwa właściwości JSON:

* Dotyczy serializacji i deserializacji.
* Jest zastępowany przez atrybuty `[JsonPropertyName]`. Jest to dlatego, że nazwa właściwości JSON `Wind` w przykładzie nie jest wielką literą.

### <a name="camel-case-dictionary-keys"></a>Klucze słownika przypadku notacji CamelCase

Jeśli właściwość obiektu, który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>`, klucze `string` można przekonwertować na notacji CamelCase. W tym celu ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Serializacja obiektu przy użyciu słownika o nazwie `TemperatureRanges`, który ma pary klucz-wartość, `"ColdMinTemp", 20` i `"HotMinTemp", 40` spowoduje to wyjście JSON podobne do następującego przykładu:

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

Zasady nazewnictwa przypadków notacji CamelCase dla kluczy słownika mają zastosowanie tylko do serializacji. W przypadku deserializacji słownika klucze będą zgodne z plikiem JSON nawet wtedy, gdy dla `DictionaryKeyPolicy`określono `JsonNamingPolicy.CamelCase`.

### <a name="enums-as-strings"></a>Wyliczenia jako ciągi

Domyślnie wyliczenia są serializowane jako liczby. Aby serializować nazwy wyliczenia jako ciągi, użyj <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.

Załóżmy na przykład, że trzeba serializować następujące klasy, które mają Wyliczenie:

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

Jeśli podsumowanie jest `Hot`, domyślnie serializowany kod JSON ma wartość liczbową 3:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

Następujący przykładowy kod serializować nazwy wyliczenia, a następnie konwertuje je na notacji CamelCase:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

Wynikowy kod JSON wygląda podobnie do poniższego przykładu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

Obsługa wyliczeń jako ciągów dotyczy również deserializacji, jak pokazano w następującym przykładzie:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a>Wyklucz właściwości z serializacji

Domyślnie wszystkie właściwości publiczne są serializowane. Jeśli nie chcesz, aby niektóre z nich pojawiały się w danych wyjściowych JSON, masz kilka opcji. W tej sekcji wyjaśniono, jak wykluczyć:

* Poszczególne właściwości
* Wszystkie właściwości tylko do odczytu
* Wszystkie właściwości o wartości null 

### <a name="exclude-individual-properties"></a>Wyklucz pojedyncze właściwości

Aby zignorować poszczególne właściwości, Użyj atrybutu [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Oto przykład typu do serializacji i danych wyjściowych JSON:

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

### <a name="exclude-all-read-only-properties"></a>Wyklucz wszystkie właściwości tylko do odczytu

Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej. Aby wykluczyć wszystkie właściwości tylko do odczytu, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak pokazano w następującym przykładzie:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Oto przykład typu do serializacji i danych wyjściowych JSON:

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

Ta opcja ma zastosowanie tylko do serializacji. Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane.

### <a name="exclude-all-null-value-properties"></a>Wyklucz wszystkie właściwości wartości null

Aby wykluczyć wszystkie właściwości wartości null, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na `true`, jak pokazano w następującym przykładzie:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Oto przykład obiektu do serializacji i danych wyjściowych JSON:

|Właściwość |Wartość  |
|---------|---------|
| Data    | 8/1/2019 12:00:00 AM – 07:00|
| TemperatureC| 6,25 |
| Podsumowanie| wartość null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

To ustawienie dotyczy serializacji i deserializacji. Aby uzyskać informacje o jego wpływie na deserializacji, zobacz [Ignore null podczas deserializacji](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Dostosuj kodowanie znaków

Domyślnie serializator wyprowadza wszystkie znaki nienależące do zestawu znaków ASCII.  Oznacza to, że zastępuje je `\uxxxx` gdzie `xxxxx` jest kodem Unicode znaku.  Na przykład, jeśli właściwość `Summary` jest ustawiona na wartość cyrylicy жарко, obiekt `WeatherForecast` zostanie Zserializowany, jak pokazano w tym przykładzie:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Serializowanie zestawów znaków języka

Aby serializować zestawy znaków w jednym lub kilku językach, określ [zakresy Unicode](xref:System.Text.Unicode.UnicodeRanges) podczas tworzenia wystąpienia <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak pokazano w następującym przykładzie:

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

Ten kod serializacji znaki cyrylicy i greckich. Znaki cyrylicy są wyświetlane w następującym przykładzie:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

Aby określić wszystkie języki, użyj <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.

### <a name="serialize-specific-characters"></a>Serializacja określonych znaków

Alternatywą jest określenie pojedynczych znaków, które mają być dozwolone, bez konieczności ucieczki. Poniższy przykład serializacji tylko dwa pierwsze znaki жарко:

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

Oto przykład kodu JSON utworzonego przez poprzedni kod:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Serializować wszystkie znaki

Aby zminimalizować liczbę ucieczki, można użyć <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, jak pokazano w następującym przykładzie:

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
> W przeciwieństwie do domyślnego kodera, koder `UnsafeRelaxedJsonEscaping`:
>
> * Nie ucieczki znaków w języku HTML, takich jak `<`, `>`, `&`i `'`.
> * Nie oferuje żadnej dodatkowej ochrony przed atakami typu XSS lub ujawnienie informacji, takich jak te, które mogą wynikać z klienta i serwera bez zgody na *zestaw znaków*.
> * Jest bardziej ograniczająca niż domyślny koder, na którym znaki mogą być przekazywane przez niezmienione.
>
> Używaj niebezpiecznego kodera tylko wtedy, gdy wiadomo, że klient będzie interpretować otrzymany ładunek jako zakodowany w formacie JSON UTF-8. Można na przykład użyć go, jeśli serwer wysyła nagłówek odpowiedzi `Content-Type: application/json; charset=utf-8`. Nigdy nie Zezwalaj na emitowanie nieprzetworzonych danych wyjściowych `UnsafeRelaxedJsonEscaping` do strony HTML lub `<script>` elementu.

## <a name="serialize-properties-of-derived-classes"></a>Serializowanie właściwości klas pochodnych

Serializacja polimorficzna nie jest obsługiwana w przypadku określenia w czasie kompilacji typu, który ma być serializowany. Załóżmy na przykład, że masz klasę `WeatherForecast` i klasę pochodną `WeatherForecastWithWind`:

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

I Załóżmy, że argument typu metody `Serialize` w czasie kompilacji jest `WeatherForecast`:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

W tym scenariuszu Właściwość `WindSpeed` nie jest serializowana, nawet jeśli obiekt `weatherForecast` jest w rzeczywistości obiektem `WeatherForecastWithWind`. Tylko właściwości klasy bazowej są serializowane:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.

Aby serializować właściwości typu pochodnego, należy użyć jednej z następujących metod:

* Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A>, które pozwala określić typ w czasie wykonywania:

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* Zadeklaruj obiekt do serializacji jako `object`.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

W poprzednim przykładowym scenariuszu oba podejścia powodują, że właściwość `WindSpeed` ma zostać uwzględniona w danych wyjściowych JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

Aby uzyskać informacje na temat deserializacji polimorficznej, zobacz [Obsługa deserializacji polimorficznej](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

## <a name="allow-comments-and-trailing-commas"></a>Zezwalaj na komentarze i końcowe przecinki

Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON. Aby zezwolić na komentarze w formacie JSON, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na `JsonCommentHandling.Skip`. I aby zezwolić na końcowe przecinki, ustaw właściwość <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na `true`. Poniższy przykład pokazuje, jak:

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Oto przykładowy kod JSON z komentarzami i końcowym przecinkiem:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Dopasowanie właściwości bez uwzględniania wielkości liter

Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego. Aby zmienić to zachowanie, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

Oto przykład JSON z nazwami właściwości przypadku notacji CamelCase. Można ją zdeserializować do następującego typu, który ma nazwy właściwości przypadku języka Pascal.

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

## <a name="handle-overflow-json"></a>Obsługa przepełnienia kodu JSON

Podczas deserializacji można odbierać dane w formacie JSON, które nie są reprezentowane przez właściwości typu docelowego. Załóżmy na przykład, że typ docelowy to:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

I kod JSON do deserializacji jest następujący:

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

W przypadku deserializacji kodu JSON pokazanego w pokazanym typie właściwości `DatesAvailable` i `SummaryWords` mają wartość Nowhere i są tracone. Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub `Dictionary<string,JsonElement>`:

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

Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie przykładowym dodatkowe dane staną się parami klucz-wartość właściwości `ExtensionData`:

|Właściwość |Wartość  |Uwagi  |
|---------|---------|---------|
| Data    | 8/1/2019 12:00:00 AM – 07:00||
| TemperatureC| 0 | Niezgodność z wielkością liter (`temperatureC` w formacie JSON), więc właściwość nie jest ustawiona. |
| Podsumowanie | Ręczne ||
| ExtensionData — | temperatureC: 25 |Ponieważ przypadek nie jest zgodny, ta właściwość JSON jest dodatkową i jest parą klucz-wartość w słowniku.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 AM – 07:00<br>8/2/2019 12:00:00 AM – 07:00 |Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.|
| |SummaryWords:<br>Ochłodzenia<br>Wiatr<br>Humid |Dodatkowa Właściwość JSON zmieni się na parę klucz-wartość, z tablicą jako obiektem wartości.|

Gdy obiekt docelowy jest serializowany, pary wartości klucza danych rozszerzenia stają się właściwościami JSON tak samo jak w przychodzących danych JSON:

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

Zauważ, że nazwa właściwości `ExtensionData` nie występuje w formacie JSON. Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.

## <a name="ignore-null-when-deserializing"></a>Ignoruj wartość null podczas deserializacji

Domyślnie, jeśli właściwość w formacie JSON ma wartość null, odpowiadająca jej właściwość w obiekcie docelowym ma wartość null. W niektórych scenariuszach właściwość target może mieć wartość domyślną i nie ma potrzeby przesłonięcia wartości domyślnej.

Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:

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

Załóżmy, że następujący kod JSON jest deserializowany:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

Po deserializacji właściwość `Summary` obiektu `WeatherForecastWithDefault` ma wartość null.

Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na `true`, jak pokazano w następującym przykładzie:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

W przypadku tej opcji Właściwość `Summary` obiektu `WeatherForecastWithDefault` jest wartością domyślną "Brak podsumowania" po deserializacji.

Wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe. Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki. Aby uzyskać więcej informacji, zobacz [problem związany z typami wartości niedopuszczających wartości null](https://github.com/dotnet/corefx/issues/40922) w repozytorium dotnet/corefx w witrynie GitHub.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter i JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> jest wysoce wydajnym, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, Odczytaj z `ReadOnlySpan<byte>`. `Utf8JsonReader` jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji. Metoda <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> używa `Utf8JsonReader` w obszarze okładek.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> to wysoce wydajny sposób pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy .NET, takich jak `String`, `Int32`i `DateTime`. Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych. Metoda <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> używa `Utf8JsonWriter` w obszarze okładek.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> zapewnia możliwość tworzenia Document Object Model tylko do odczytu (DOM) przy użyciu `Utf8JsonReader`. DOM zapewnia losowy dostęp do danych w ładunku JSON. Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem typu <xref:System.Text.Json.JsonElement>. `JsonElement` zapewnia moduł wyliczający tablic i obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET. `JsonDocument` uwidacznia Właściwość <xref:System.Text.Json.JsonDocument.RootElement>.

W poniższych sekcjach pokazano, jak używać tych narzędzi do odczytywania i pisania danych JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Korzystanie z JsonDocument do uzyskiwania dostępu do danych

Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.JsonDocument> na potrzeby losowego dostępu do danych:

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

Poprzedni kod:

* Przyjęto, że kod JSON do analizy znajduje się w ciągu o nazwie `jsonString`.
* Oblicza średnią ocenę dla obiektów w tablicy `Students`, która ma właściwość `Grade`. 
* Przypisuje domyślną ocenę 70 dla studentów, którzy nie posiadają klasy.
* Zlicza uczniów przez zwiększenie zmiennej `count` przy każdej iteracji. Alternatywą jest wywołanie <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

Oto przykład pliku JSON, który jest przetwarzany przez ten kod:

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

## <a name="use-jsondocument-to-write-json"></a>Użyj JsonDocument, aby zapisać kod JSON

Poniższy przykład pokazuje, jak napisać kod JSON z <xref:System.Text.Json.JsonDocument>:

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

Poprzedni kod:

* Odczytuje plik JSON, ładuje dane do `JsonDocument`i zapisuje sformatowany plik JSON w formacie.
* Używa <xref:System.Text.Json.JsonDocumentOptions>, aby określić, że komentarze w wejściowym formacie JSON są dozwolone, ale ignorowane.
* Po zakończeniu wywołuje <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> w składniku zapisywania. Alternatywą jest umożliwienie składnika zapisywania AutoFlush, gdy zostanie on usunięty. 

Oto przykład danych wejściowych JSON do przetworzenia przez przykładowy kod:

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

Wynikiem są następujące niedrukowane dane wyjściowe JSON:

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

## <a name="use-utf8jsonwriter"></a>Użyj Utf8JsonWriter

Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.Utf8JsonWriter>:

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

## <a name="use-utf8jsonreader"></a>Użyj Utf8JsonReader

Poniższy przykład pokazuje, jak używać klasy <xref:System.Text.Json.Utf8JsonReader>:

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

Poprzedni kod założono, że zmienna `jsonUtf8` jest tablicą bajtów, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrowanie danych za pomocą Utf8JsonReader

Poniższy przykład pokazuje, jak odczytywać plik synchronicznie i wyszukiwać wartość:

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

Poprzedni kod:

* Przyjęto założenie, że plik jest zakodowany jako UTF-16 i transkoduje go do UTF-8. Plik zakodowany jako UTF-8 można odczytać bezpośrednio w `ReadOnlySpan<byte>`, używając następującego kodu:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* Przyjęto, że kod JSON zawiera tablicę obiektów, a każdy obiekt może zawierać właściwość "name" typu String.
* Zlicza obiekty i `name` wartości właściwości, które kończą się na Uniwersytecie.

Oto przykład JSON, który może odczytać poprzedzający kod. Otrzymany komunikat podsumowujący to "2 z 4 mają nazwy kończące się na" University ":

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

## <a name="additional-resources"></a>Dodatkowe zasoby

* [System. Text. JSON — Omówienie](system-text-json-overview.md)
* [Dokumentacja interfejsu API System. Text. JSON](xref:System.Text.Json)
* [Zapisuj niestandardowe konwertery dla elementu System. Text. JSON](system-text-json-converters-how-to.md)
* [Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON](../datetime/system-text-json-support.md)
