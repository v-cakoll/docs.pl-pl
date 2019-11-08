---
title: Jak pisać konwertery niestandardowe na potrzeby serializacji JSON — .NET
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741893"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a>Jak napisać niestandardowe konwertery dla serializacji JSON w programie .NET

W tym artykule pokazano, jak utworzyć niestandardowe konwertery dla klas serializacji JSON, które są dostępne w przestrzeni nazw <xref:System.Text.Json>. Aby zapoznać się z wprowadzeniem do `System.Text.Json`, zobacz [jak serializować i deserializować kod JSON w programie .NET](system-text-json-how-to.md).

*Konwerter* jest klasą, która konwertuje obiekt lub wartość do i z formatu JSON. Przestrzeń nazw `System.Text.Json` zawiera wbudowane konwertery dla większości typów pierwotnych, które są mapowane na elementy pierwotne języka JavaScript. Możesz pisać niestandardowe konwertery:

* Aby zastąpić domyślne zachowanie konwertera wbudowanego. Na przykład możesz chcieć, aby wartości `DateTime` były reprezentowane w formacie mm/dd/rrrr zamiast domyślnego formatu ISO 8601-1:2019.
* Do obsługi niestandardowego typu wartości. Na przykład struktura `PhoneNumber`.

Możesz również napisać niestandardowe konwertery, aby zwiększyć `System.Text.Json` z funkcjami niezawartymi w bieżącej wersji. Poniższe scenariusze zostały omówione w dalszej części tego artykułu:

* [Deserializacja wywnioskowanych typów do właściwości obiektu](#deserialize-inferred-types-to-object-properties).
* [Obsługa słownika z kluczem niebędącym ciągiem](#support-dictionary-with-non-string-key).
* [Obsługa deserializacji polimorficznej](#support-polymorphic-deserialization).

## <a name="custom-converter-patterns"></a>Wzorce niestandardowego konwertera

Istnieją dwa wzorce do tworzenia niestandardowego konwertera: wzorzec podstawowy i wzorzec fabryki. Wzorzec fabryki jest przeznaczony dla konwerterów, które obsługują typ `Enum` lub otwierają typy ogólne. Wzorzec podstawowy dotyczy typów ogólnych nieogólnych i zamkniętych.  Na przykład konwertery dla następujących typów wymagają wzorca fabryki:

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

Niektóre przykłady typów, które mogą być obsługiwane przez wzorzec Basic, obejmują:

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

Wzorzec podstawowy tworzy klasę, która może obsługiwać jeden typ. Wzorzec fabryki tworzy klasę, która określa w czasie wykonywania, który określony typ jest wymagany i dynamicznie tworzy odpowiedni konwerter.

## <a name="sample-basic-converter"></a>Przykładowy konwerter podstawowy

Poniższy przykład to konwerter, który zastąpi domyślną serializację dla istniejącego typu danych. Konwerter używa formatu mm/dd/rrrr do `DateTimeOffset` właściwości.

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a>Przykładowy konwerter wzorców fabryki

Poniższy kod przedstawia niestandardowy konwerter, który działa z `Dictionary<Enum,TValue>`. Kod jest zgodny ze wzorcem fabryki, ponieważ pierwszy parametr typu ogólnego to `Enum`, a drugi jest otwarty. Metoda `CanConvert` zwraca `true` tylko dla `Dictionary` z dwoma parametrami ogólnymi, z których pierwszy jest typem `Enum`. Wewnętrzny konwerter pobiera istniejący konwerter do obsługi dowolnego typu w czasie wykonywania dla `TValue`. 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

Poprzedni kod jest taki sam jak w [słowniku pomocy technicznej z kluczem innym niż ciąg](#support-dictionary-with-non-string-key) w dalszej części tego artykułu.

## <a name="steps-to-follow-the-basic-pattern"></a>Kroki prowadzące do wzorca podstawowego

Poniższe kroki wyjaśniają, jak utworzyć konwerter, wykonując następujące czynności:

* Utwórz klasę, która pochodzi od <xref:System.Text.Json.Serialization.JsonConverter%601>, gdzie `T` jest typem, który ma być serializowany i deserializowany.
* Zastąp metodę `Read`, aby deserializować przychodzącego pliku JSON i przekonwertować go na `T`typu. Użyj <xref:System.Text.Json.Utf8JsonReader>, który jest przesyłany do metody, aby odczytać kod JSON.
* Zastąp metodę `Write`, aby serializować obiekt przychodzący typu `T`. Użyj <xref:System.Text.Json.Utf8JsonWriter>, który jest przesyłany do metody, aby zapisać kod JSON.
* Zastąp metodę `CanConvert` tylko w razie potrzeby. Domyślna implementacja zwraca `true`, gdy typ do przekonwertowania jest typu `T`. W związku z tym konwertery obsługujące tylko typ `T` nie muszą przesłaniać tej metody. Aby zapoznać się z przykładem konwertera, który musi przesłonić tę metodę, zobacz sekcję [deserializacji polimorficzną](#support-polymorphic-deserialization) w dalszej części tego artykułu.

Możesz odwołać się do [wbudowanego kodu źródłowego konwerterów](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) jako implementacji odwołań do pisania konwerterów niestandardowych.

## <a name="steps-to-follow-the-factory-pattern"></a>Kroki prowadzące do wzorca fabryki

Poniższe kroki wyjaśniają, jak utworzyć konwerter, postępując zgodnie z wzorcem fabryki:

* Utwórz klasę pochodzącą z <xref:System.Text.Json.Serialization.JsonConverterFactory>.
* Zastąp metodę `CanConvert`, aby zwracał wartość true, gdy typ do przekonwertowania jest taki, który może obsłużyć konwerter. Na przykład, jeśli konwerter jest przeznaczony dla `List<T>` może obsłużyć tylko `List<int>`, `List<string>`i `List<DateTime>`. 
* Zastąp metodę `CreateConverter`, aby zwracała wystąpienie klasy konwertera, która będzie obsługiwała typ do konwersji, który jest dostarczany w czasie wykonywania.
* Utwórz klasę konwertera, którą tworzy instancja metody `CreateConverter`. 

Wzorzec fabryki jest wymagany do otwierania typów ogólnych, ponieważ kod do konwersji obiektu na i z ciągu nie jest taki sam dla wszystkich typów. Konwerter dla otwartego typu ogólnego (na przykład`List<T>`) musi utworzyć konwerter dla zamkniętego typu ogólnego (na przykład`List<DateTime>`) w tle. Kod musi być zapisany, aby obsługiwał każdy zamknięty typ ogólny, który może obsłużyć konwerter.

Typ `Enum` jest podobny do otwartego typu ogólnego: konwerter dla `Enum` musi utworzyć konwerter dla konkretnej `Enum``WeekdaysEnum`(na przykład) w tle. 

## <a name="error-handling"></a>Obsługa błędów

Jeśli musisz zgłosić wyjątek w kodzie obsługi błędu, rozważ przegenerowanie <xref:System.Text.Json.JsonException> bez komunikatu. Ten typ wyjątku powoduje automatyczne utworzenie komunikatu zawierającego ścieżkę do części JSON, która spowodowała błąd. Na przykład instrukcja `throw new JsonException();` generuje komunikat o błędzie, jak w poniższym przykładzie:

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Jeśli zostanie wyświetlony komunikat (na przykład `throw new JsonException("Error occurred)`, wyjątek nadal udostępnia ścieżkę we właściwości <xref:System.Text.Json.JsonException.Path>.

## <a name="register-a-custom-converter"></a>Rejestrowanie niestandardowego konwertera

*Zarejestruj* konwerter niestandardowy, aby zastosować `Serialize` i `Deserialize` metody. Wybierz jedną z następujących metod:

* Dodaj wystąpienie klasy Converter do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.
* Zastosuj atrybut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) do właściwości, które wymagają konwertera niestandardowego.
* Zastosuj atrybut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) do klasy lub struktury, która reprezentuje niestandardowy typ wartości.

## <a name="registration-sample---converters-collection"></a>Przykład rejestracji — kolekcja konwerterów 

Oto przykład, który sprawia, że `ExampleDateTimeOffsetConverter` domyślny dla właściwości typu `DateTimeOffset`:

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

Załóżmy, że serializowany został następujący typ:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

Oto przykład danych wyjściowych JSON, które pokazują, że użyto niestandardowego konwertera:

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Poniższy kod używa tego samego podejścia do deserializacji przy użyciu niestandardowego konwertera `DateTimeOffset`:

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a>Przykład rejestracji — [JsonConverter] na właściwości

Poniższy kod wybiera niestandardowy konwerter właściwości `Date`:

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

Kod do serializacji i deserializacji `WeatherForecastWithConverter` nie wymaga użycia `JsonSerializeOptions.Converters`:

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a>Przykład rejestracji — [JsonConverter] w typie

Oto kod, który tworzy strukturę i stosuje do niej atrybut `[JsonConverter]`:

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

Oto niestandardowy konwerter dla poprzedniej struktury:

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

Atrybut `[JsonConvert]` w strukturze rejestruje niestandardowy konwerter jako domyślny dla właściwości typu `Temperature`. Konwerter jest automatycznie używany we właściwości `TemperatureC` następującego typu podczas serializacji lub deserializacji:

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a>Pierwszeństwo rejestracji konwertera

Podczas serializacji lub deserializacji konwerter jest wybierany dla każdego elementu JSON w następującej kolejności, na podstawie najwyższego priorytetu:

* `[JsonConverter]` zastosowana do właściwości.
* Konwerter dodany do kolekcji `Converters`.
* `[JsonConverter]` zastosowana do niestandardowego typu wartości lub POCO.

Jeśli wiele konwerterów niestandardowych dla typu są zarejestrowane w kolekcji `Converters`, zostanie użyty pierwszy konwerter zwracający wartość true dla `CanConvert`.

Wbudowany konwerter jest wybierany tylko wtedy, gdy nie zarejestrowano żadnego odpowiedniego konwertera niestandardowego.

## <a name="converter-samples-for-common-scenarios"></a>Przykłady konwerterów dla typowych scenariuszy

Poniższe sekcje zawierają przykłady konwerterów, które dotyczą niektórych typowych scenariuszy, które nie obsługują funkcji wbudowanych.

### <a name="deserialize-inferred-types-to-object-properties"></a>Deserializacja wywnioskowanych typów do właściwości obiektu

Podczas deserializacji do właściwości typu `Object`zostanie utworzony obiekt `JsonElement`. Przyczyną jest to, że Deserializator nie wie, jakie typy CLR należy utworzyć, i nie próbuje go odgadnąć. Na przykład, jeśli właściwość JSON ma wartość "true", Deserializator nie uzna, że wartość jest `Boolean`, a jeśli element ma "01/01/2019", Deserializator nie uzna, że jest to `DateTime`.

Wnioskowanie o typie może być niedokładne. Jeśli Deserializator analizuje numer JSON, który nie ma punktu dziesiętnego jako `long`, co może spowodować problemy poza zakresem, jeśli wartość została pierwotnie zserializowana jako `ulong` lub `BigInteger`. Analizowanie liczby, która ma przecinek dziesiętny jako `double` może stracić dokładnooć, jeśli liczba została pierwotnie zserializowana jako `decimal`.

W przypadku scenariuszy, które wymagają wnioskowania o typie, poniższy kod przedstawia niestandardowy konwerter dla `Object` właściwości. Kod konwertuje:

* `true` i `false` do `Boolean`
* Liczby do `long` lub `double`
* Daty do `DateTime`
* Ciągi do `string`
* Wszystkie inne elementy do `JsonElement`

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

Następujący kod rejestruje konwerter:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

Oto przykładowy typ z właściwością Object:

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

Poniższy przykład JSON do deserializacji zawiera wartości, które zostaną rozszeregowane jako `DateTime`, `long`i `string`:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

Bez niestandardowego konwertera deserializacja umieszcza `JsonElement` w każdej właściwości.

[Folder testów jednostkowych](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) w przestrzeni nazw `System.Text.Json.Serialization` zawiera więcej przykładów niestandardowych konwerterów, które obsługują deserializacji do właściwości obiektu.

### <a name="support-dictionary-with-non-string-key"></a>Obsługa słownika z kluczem niebędącym ciągiem

Wbudowana obsługa kolekcji słowników ma na celu `Dictionary<string, TValue>`. Oznacza to, że klucz musi być ciągiem. Aby zapewnić obsługę słownika z liczbą całkowitą lub innym typem jako klucz, wymagany jest konwerter niestandardowy.

Poniższy kod przedstawia niestandardowy konwerter, który działa z `Dictionary<Enum,TValue>`:

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

Następujący kod rejestruje konwerter:

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

Konwerter może serializować i deserializować Właściwość `TemperatureRanges` poniższej klasy, która używa następujących `Enum`:

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

Dane wyjściowe JSON z serializacji wyglądają podobnie jak w poniższym przykładzie:

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

[Folder testy jednostkowe](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) w przestrzeni nazw `System.Text.Json.Serialization` zawiera więcej przykładów niestandardowych konwerterów, które obsługują słowniki niebędące ciągami.

### <a name="support-polymorphic-deserialization"></a>Obsługa deserializacji polimorficzna

[Serializacja polimorficzna](system-text-json-how-to.md#serialize-properties-of-derived-classes) nie wymaga konwertera niestandardowego, ale deserializacja wymaga konwertera niestandardowego.

Załóżmy na przykład, że masz `Person` abstrakcyjną klasę bazową z `Employee` i `Customer` klasami pochodnymi. Deserializacja polimorficzna oznacza, że w czasie projektowania można określić `Person` jako element docelowy deserializacji, a `Customer` i `Employee` obiektów w formacie JSON są prawidłowo deserializowane w czasie wykonywania. Podczas deserializacji należy znaleźć wskazówki, które identyfikują wymagany typ w kodzie JSON. Rodzaje dostępnych wskazówek różnią się w zależności od scenariusza. Na przykład może być dostępna właściwość rozróżniacza lub może zależeć od obecności lub braku określonej właściwości. Bieżąca wersja `System.Text.Json` nie udostępnia atrybutów, aby określić sposób obsługi scenariuszy deserializacji polimorficznych, dlatego wymagane są niestandardowe konwertery.

Poniższy kod przedstawia klasę bazową, dwie klasy pochodne i niestandardowy konwerter dla nich. Konwerter używa właściwości rozróżniacza do wykonywania deserializacji polimorficznej. Rozróżniacz typu nie znajduje się w definicjach klas, ale jest tworzony podczas serializacji i jest odczytywany podczas deserializacji.

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

Następujący kod rejestruje konwerter:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

Konwerter może deserializować kod JSON, który został utworzony przy użyciu tego samego konwertera do serializacji, na przykład:

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

## <a name="other-custom-converter-samples"></a>Inne przykłady konwerterów niestandardowych

[Folder testy jednostkowe](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) w `System.Text.Json.Serialization` kodzie źródłowym zawiera inne niestandardowe przykłady konwerterów, takie jak:

* konwerter `Int32`, który konwertuje wartość null na wartość 0 podczas deserializacji
* konwerter `Int32`, który zezwala na wartości typu String i Number przy deserializacji
* konwerter `Enum`
* konwerter `List<T>`, który akceptuje dane zewnętrzne
* konwerter `Long[]`, który współpracuje z listą liczb rozdzielanych przecinkami 

## <a name="additional-resources"></a>Dodatkowe zasoby

* [System. Text. JSON — Omówienie](system-text-json-overview.md)
* [Dokumentacja interfejsu API System. Text. JSON](xref:System.Text.Json)
* [Jak używać metody System. Text. JSON](system-text-json-how-to.md)
* [Kod źródłowy wbudowanych konwerterów](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* Problemy z usługą GitHub dotyczące niestandardowych konwerterów dla `System.Text.Json`
  * [36639 wprowadzenie niestandardowych konwerterów](https://github.com/dotnet/corefx/issues/36639)
  * [38713 informacje o deserializacji do obiektu](https://github.com/dotnet/corefx/issues/38713)
  * [40120 dotyczące słowników kluczy niebędących ciągami](https://github.com/dotnet/corefx/issues/40120)
  * [37787 informacje o deserializacji polimorficznej](https://github.com/dotnet/corefx/issues/37787)
