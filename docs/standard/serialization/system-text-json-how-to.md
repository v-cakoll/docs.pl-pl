---
title: Jak serializować kod JSON — .NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 8ccd7afe4abb928e7723aa740507774012fc85d1
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083109"
---
# <a name="how-to-serialize-json-in-net"></a>Jak serializować kod JSON w programie .NET

> [!IMPORTANT]
> Dokumentacja serializacji JSON jest w przygotowaniu. Ten artykuł nie obejmuje wszystkich scenariuszy. Aby uzyskać więcej informacji, należy zapoznać się z tematami [System. Text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) w repozytorium dotnet/corefx w witrynie GitHub, w szczególności z etykietą [JSON-funkcja-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).

W tym artykule pokazano, <xref:System.Text.Json> jak używać przestrzeni nazw do serializacji i deserializacji do i z JavaScript Object Notation (JSON). Instrukcje i przykładowy kod używają biblioteki bezpośrednio, a nie za pomocą struktury, takiej jak [ASP.NET Core](/aspnet/core/).

## <a name="namespaces"></a>Namespaces

<xref:System.Text.Json> Przestrzeń nazw zawiera wszystkie punkty wejścia i typy główne. <xref:System.Text.Json.Serialization> Przestrzeń nazw zawiera atrybuty i interfejsy API dla zaawansowanych scenariuszy i dostosowań specyficznych dla serializacji i deserializacji. W związku z tym przykłady kodu przedstawione w tym artykule wymagają jednej lub obu następujących `using` dyrektyw:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atrybuty z <xref:System.Runtime.Serialization> przestrzeni nazw nie są obecnie obsługiwane `System.Text.Json`w programie.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Pisanie obiektów .NET w formacie JSON (Serializacja)

Aby zapisać kod JSON w ciągu, wywołaj <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> metodę. Poniższy przykład używa przeciążenia z parametrem typu ogólnego:

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

Można pominąć parametr typu ogólnego i zamiast tego użyć ogólnego wnioskowania o typie:

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

Oto przykład typu do serializacji, który zawiera kolekcje i klasy zagnieżdżone:

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

Dane wyjściowe JSON domyślnie są zminimalizowanego: 

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

Przeciążenia można serializować <xref:System.IO.Stream>do. <xref:System.Text.Json.JsonSerializer.Serialize%2A> Asynchroniczne wersje `Stream` przeciążeń są dostępne.

### <a name="serialize-to-utf-8"></a>Serializacja do UTF-8

Aby serializować do UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> metodę:

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

Alternatywnie, <xref:System.Text.Json.JsonSerializer.Serialize%2A> Przeciążenie, które <xref:System.Text.Json.Utf8JsonWriter> trwa, jest dostępne.

Serializacja do UTF-8 jest szybsza o 5-10% niż przy użyciu metod opartych na ciągach. Różnica polega na tym, że bajty (w formacie UTF-8) nie muszą być konwertowane na ciągi (UTF-16).

## <a name="serialization-behavior"></a>Zachowanie serializacji

* Domyślnie wszystkie właściwości publiczne są serializowane. Można [określić właściwości do wykluczenia](#exclude-properties).
* [Domyślny koder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) wyprowadza znaki nienależące do zestawu znaków ASCII, znaki z uwzględnieniem kodu HTML w zakresie ASCII i znaków, które muszą zostać zmienione zgodnie z [specyfikacją JSON](https://tools.ietf.org/html/rfc8259#section-7).
* Domyślnie JSON jest zminimalizowanego. Można tu [wydrukować kod JSON](#serialize-to-formatted-json).
* Domyślnie wielkość liter w nazwach JSON jest zgodna z nazwami .NET. Można [dostosować wielkość liter w nazwach JSON](#customize-json-names).
* Wykryto odwołania cykliczne i zostały zgłoszone wyjątki. Aby uzyskać więcej informacji, zobacz [problem dotyczący odwołań cyklicznych](https://github.com/dotnet/corefx/issues/38579) w repozytorium dotnet/corefx w witrynie GitHub.
* Obecnie pola są wykluczone.

Obsługiwane typy to:

* Elementy podstawowe platformy .NET, które są mapowane na elementy podstawowe języka JavaScript, takie jak typy liczbowe, ciągi i wartości logiczne.
* Obiekty CLR zdefiniowane przez użytkownika [(POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tablice jednowymiarowe i nieregularne (`ArrayName[][]`).
* `Dictionary<string,TValue>`gdzie `TValue` is `object`to ,`JsonElement`lub poco.
* Kolekcje z następujących przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [problem związany z obsługą kolekcji](https://github.com/dotnet/corefx/issues/36643) w repozytorium dotnet/corefx w witrynie GitHub.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Jak odczytywać dane JSON do obiektów .NET (deserializacji)

Aby zdeserializować z ciągu, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> metodę, jak pokazano w następującym przykładzie:

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Aby zapoznać się z przykładem, zapoznaj się z sekcją [serializacji](#how-to-write-net-objects-to-json-serialize) . Obiekty JSON i .NET są takie same, ale kierunek jest odwrócony.

Przeciążenia programu <xref:System.Text.Json.JsonSerializer.Deserialize*> umożliwiają deserializacji `Stream`z.  Asynchroniczne wersje `Stream` przeciążeń są dostępne.

### <a name="deserialize-from-utf-8"></a>Deserializacja z UTF-8

Aby zdeserializować z UTF-8, wywołaj <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Przeciążenie, które `Utf8JsonReader` przyjmuje lub a `ReadOnlySpan<byte>`, jak pokazano w następujących przykładach:

```csharp
byte[] utf8Json;
//...
var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json;
//...
var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a>Zachowanie deserializacji

* Domyślnie w dopasowaniu nazw właściwości rozróżniana jest wielkość liter. Można [określić wielkość liter](#case-insensitive-property-matching).
* Jeśli kod JSON zawiera wartość właściwości tylko do odczytu, wartość jest ignorowana i nie jest zgłaszany żaden wyjątek.
* Deserializacja do typów referencyjnych bez bezparametrowego konstruktora nie jest obsługiwana.
* Deserializacja z niezmiennymi obiektami lub właściwościami tylko do odczytu nie jest obsługiwana. Aby uzyskać więcej informacji, zobacz [problem z obsługą usługi GitHub dla niemodyfikowalnych obiektów](https://github.com/dotnet/corefx/issues/38569) i [problem związany z obsługą właściwości tylko do odczytu](https://github.com/dotnet/corefx/issues/38163) w repozytorium dotnet/corefx w witrynie GitHub.
* Domyślnie wyliczenia są obsługiwane jako liczby.
* Pola nie są obsługiwane.
* Domyślnie komentarze lub końcowe przecinki w wyjątkach throw JSON. W razie konieczności można [zezwolić na komentarze i końcowe przecinki](#allow-comments-and-trailing-commas) .
* [Domyślna głębokość maksymalna](xref:System.Text.Json.JsonReaderOptions.MaxDepth) to 64.

## <a name="serialize-to-formatted-json"></a>Serializacja do sformatowanego pliku JSON

Aby całkiem wydrukować dane wyjściowe JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType>: `true`

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
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
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

## <a name="allow-comments-and-trailing-commas"></a>Zezwalaj na komentarze i końcowe przecinki

Domyślnie Komentarze i końcowe przecinki są niedozwolone w notacji JSON. Aby zezwolić na komentarze w formacie JSON, ustaw <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> właściwość na `JsonCommentHandling.Skip`. I aby zezwolić na końcowe przecinki, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> właściwość na `true`. Poniższy przykład pokazuje, jak:

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

## <a name="customize-json-names"></a>Dostosuj nazwy JSON

Domyślnie nazwy właściwości i klucze słownika nie są zmieniane w danych wyjściowych JSON, włącznie z wielkością liter. W tej sekcji wyjaśniono, jak:

* Dostosowywanie poszczególnych nazw właściwości
* Konwertuj wszystkie nazwy właściwości na notacji CamelCase przypadku
* Implementowanie zasad nazewnictwa właściwości niestandardowych
* Konwertuj klucze słownika na notacji CamelCase

Obecnie nie jest obsługiwane automatyczne konwertowanie tekstów stałych na notacji CamelCase przypadku. Aby uzyskać więcej informacji, zapoznaj się z tematem [problem związany z obsługą przypadku wyliczeniowego notacji CamelCase](https://github.com/dotnet/corefx/issues/37725) w repozytorium dotnet/corefx w witrynie GitHub.

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

Aby użyć notacji CamelCase przypadku wszystkich nazw właściwości JSON, ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase`tak, jak pokazano w następującym przykładzie:

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
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
  "Wind": 35
}
```

Zasady nazewnictwa właściwości przypadku notacji CamelCase:

* Dotyczy serializacji i deserializacji.
* Jest zastępowany `[JsonPropertyName]` przez atrybuty.

### <a name="use-a-custom-json-property-naming-policy"></a>Użyj niestandardowych zasad nazewnictwa właściwości JSON

Aby użyć niestandardowych zasad nazewnictwa właściwości JSON, Utwórz klasę, która pochodzi od <xref:System.Text.Json.JsonNamingPolicy> i <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> przesłania metodę, jak pokazano w następującym przykładzie:

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Następnie ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> właściwość na wystąpienie klasy zasad nazewnictwa:

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
* Jest zastępowany `[JsonPropertyName]` przez atrybuty.

### <a name="camel-case-dictionary-keys"></a>Klucze słownika przypadku notacji CamelCase

Jeśli właściwość obiektu `string` , który ma zostać Zserializowany, jest typu `Dictionary<string,TValue>`, klucze mogą być konwertowane na notacji CamelCase przypadku. W tym celu ustaw wartość <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase`, jak pokazano w następującym przykładzie:

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Oto przykład obiektu do serializacji i danych wyjściowych JSON:

|Właściwość |Wartość  |
|---------|---------|
| Data    | 8/1/2019 12:00:00 AM – 07:00|
| TemperatureC| 25 |
| Podsumowanie| ręczne|
| TemperatureRanges | Zimna, 20<br>Gorąca, 40|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "cold": 20,
    "hot": 40
  }
}
```

Zasady nazewnictwa przypadków notacji CamelCase mają zastosowanie tylko do serializacji.

## <a name="exclude-properties"></a>Właściwości wykluczenia

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

Aby wykluczyć wszystkie właściwości tylko <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> do odczytu, ustaw wartość na `true`, jak pokazano w następującym przykładzie:

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

Ta opcja ma zastosowanie tylko do serializacji. Podczas deserializacji właściwości tylko do odczytu są domyślnie ignorowane. Właściwość jest tylko do odczytu, jeśli zawiera publiczną metodę pobierającą, ale nie do publicznej metody ustawiającej.

### <a name="exclude-all-null-value-properties"></a>Wyklucz wszystkie właściwości wartości null

Aby wykluczyć wszystkie właściwości wartości null, należy ustawić <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> właściwość na `true`, jak pokazano w następującym przykładzie:

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
| TemperatureC| 25 |
| Podsumowanie| wartość null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

To ustawienie dotyczy serializacji i deserializacji. Podczas deserializacji wartości null w formacie JSON są ignorowane tylko wtedy, gdy są prawidłowe. Wartości null dla typów wartości, które nie dopuszczają wartości null, powodują wyjątki. Aby uzyskać więcej informacji, zobacz [problem związany z typami wartości niedopuszczających wartości null](https://github.com/dotnet/corefx/issues/40922) w repozytorium dotnet/corefx w witrynie GitHub.

## <a name="case-insensitive-property-matching"></a>Dopasowanie właściwości bez uwzględniania wielkości liter

Domyślnie deserializacja wyszukuje dopasowania nazw właściwości z uwzględnieniem wielkości liter między formatem JSON a właściwościami obiektu docelowego. Aby zmienić to zachowanie, ustaw <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> wartość na: `true`

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

## <a name="include-properties-of-derived-classes"></a>Dołącz właściwości klas pochodnych

Serializacja polimorficzna nie jest obsługiwana w przypadku określenia w czasie kompilacji typu, który ma być serializowany. Załóżmy na przykład, że masz `WeatherForecast` klasę i klasę `WeatherForecastWithWind`pochodną:

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

I Załóżmy, że typ przeszedł do, lub wywnioskowany przez, `Serialize` Metoda w czasie kompilacji to `WeatherForecast`:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

W tym scenariuszu `WindSpeed` właściwość nie jest serializowana, nawet `weatherForecast` Jeśli obiekt jest rzeczywiście `WeatherForecastWithWind` obiektem. Tylko właściwości klasy bazowej są serializowane:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Takie zachowanie ma na celu zapobieganie przypadkowemu narażeniu danych w pochodnym typie tworzonym przez środowisko uruchomieniowe.

Aby serializować właściwości typu pochodnego, należy użyć jednej z następujących metod:

* Wywołaj Przeciążenie <xref:System.Text.Json.JsonSerializer.Serialize%2A> , które pozwala określić typ w czasie wykonywania:

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* Zadeklaruj obiekt, który ma zostać `object`Zserializowany jako.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

W poprzednim przykładowym scenariuszu oba podejścia powodują `WindSpeed` , że właściwość powinna zostać uwzględniona w danych wyjściowych JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
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

W przypadku deserializacji kodu JSON pokazanego w pokazanym `SummaryWords` typie, właściwości i mają wartość `DatesAvailable` Nowhere to go i są tracone. Aby przechwycić dodatkowe dane, takie jak te właściwości, zastosuj atrybut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) do właściwości typu `Dictionary<string,object>` lub: `Dictionary<string,JsonElement>`

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

Podczas deserializacji kodu JSON pokazanego wcześniej w tym typie próbkowania dodatkowe dane staną się parami `ExtensionData` klucz-wartość właściwości:

|Właściwość |Wartość  |Uwagi  |
|---------|---------|---------|
| Data    | 8/1/2019 12:00:00 AM – 07:00||
| TemperatureC| 0 | Niezgodność z rozróżnianiem`temperatureC` wielkości liter (w formacie JSON), więc właściwość nie jest ustawiona. |
| Podsumowanie | ręczne ||
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

Zauważ, że `ExtensionData` nazwa właściwości nie pojawia się w formacie JSON. Takie zachowanie umożliwia wykonywanie operacji okrężnych przez kod JSON bez utraty jakichkolwiek dodatkowych danych, które w przeciwnym razie nie zostały odszeregowane.

## <a name="use-utf8jsonwriter-directly"></a>Używaj Utf8JsonWriter bezpośrednio

Poniższy przykład pokazuje, <xref:System.Text.Json.Utf8JsonWriter> jak używać klasy bezpośrednio.

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

## <a name="use-utf8jsonreader-directly"></a>Używaj Utf8JsonReader bezpośrednio

Poniższy przykład pokazuje, <xref:System.Text.Json.Utf8JsonReader> jak używać klasy bezpośrednio. W kodzie przyjęto, `jsonUtf8` że zmienna jest tablicą bajtów, która zawiera prawidłowy kod JSON zakodowany jako UTF-8.

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

## <a name="additional-resources"></a>Dodatkowe zasoby

* [System. Text. JSON — Omówienie](system-text-json-overview.md)
* [Dokumentacja interfejsu API System. Text. JSON](xref:System.Text.Json)
* [Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON](../datetime/system-text-json-support.md)
