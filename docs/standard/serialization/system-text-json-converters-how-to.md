---
title: Jak pisać konwertery niestandardowe na potrzeby serializacji JSON — .NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: f72d2d83d701b20648140900d65c9098a8abb721
ms.sourcegitcommit: 5d769956a04b6d68484dd717077fabc191c21da5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76164063"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>Jak pisać konwertery niestandardowe na potrzeby serializacji JSON (kierowanie) w programie .NET

W tym artykule pokazano, jak utworzyć niestandardowe konwertery dla klas serializacji JSON, które są dostępne w przestrzeni nazw <xref:System.Text.Json>. Aby zapoznać się z wprowadzeniem do `System.Text.Json`, zobacz [jak serializować i deserializować kod JSON w programie .NET](system-text-json-how-to.md).

*Konwerter* jest klasą, która konwertuje obiekt lub wartość do i z formatu JSON. Przestrzeń nazw `System.Text.Json` zawiera wbudowane konwertery dla większości typów pierwotnych, które są mapowane na elementy pierwotne języka JavaScript. Możesz pisać niestandardowe konwertery:

* Aby zastąpić domyślne zachowanie konwertera wbudowanego. Na przykład możesz chcieć, aby wartości `DateTime` były reprezentowane w formacie mm/dd/rrrr zamiast domyślnego formatu ISO 8601-1:2019.
* Do obsługi niestandardowego typu wartości. Na przykład struktura `PhoneNumber`.

Możesz również napisać niestandardowe konwertery, aby dostosować lub zwiększyć `System.Text.Json` z funkcjami niezawartymi w bieżącej wersji. Poniższe scenariusze zostały omówione w dalszej części tego artykułu:

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

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a>Przykładowy konwerter wzorców fabryki

Poniższy kod przedstawia niestandardowy konwerter, który działa z `Dictionary<Enum,TValue>`. Kod jest zgodny ze wzorcem fabryki, ponieważ pierwszy parametr typu ogólnego to `Enum`, a drugi jest otwarty. Metoda `CanConvert` zwraca `true` tylko dla `Dictionary` z dwoma parametrami ogólnymi, z których pierwszy jest typem `Enum`. Wewnętrzny konwerter pobiera istniejący konwerter do obsługi dowolnego typu w czasie wykonywania dla `TValue`. 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Poprzedni kod jest taki sam jak w [słowniku pomocy technicznej z kluczem innym niż ciąg](#support-dictionary-with-non-string-key) w dalszej części tego artykułu.

## <a name="steps-to-follow-the-basic-pattern"></a>Kroki prowadzące do wzorca podstawowego

Poniższe kroki wyjaśniają, jak utworzyć konwerter, wykonując następujące czynności:

* Utwórz klasę, która pochodzi od <xref:System.Text.Json.Serialization.JsonConverter%601>, gdzie `T` jest typem, który ma być serializowany i deserializowany.
* Zastąp metodę `Read`, aby deserializować przychodzącego pliku JSON i przekonwertować go na `T`typu. Użyj <xref:System.Text.Json.Utf8JsonReader>, który jest przesyłany do metody, aby odczytać kod JSON.
* Zastąp metodę `Write`, aby serializować obiekt przychodzący typu `T`. Użyj <xref:System.Text.Json.Utf8JsonWriter>, który jest przesyłany do metody, aby zapisać kod JSON.
* Zastąp metodę `CanConvert` tylko w razie potrzeby. Domyślna implementacja zwraca `true`, gdy typ do przekonwertowania jest typu `T`. W związku z tym konwertery obsługujące tylko typ `T` nie muszą przesłaniać tej metody. Aby zapoznać się z przykładem konwertera, który musi przesłonić tę metodę, zobacz sekcję [deserializacji polimorficzną](#support-polymorphic-deserialization) w dalszej części tego artykułu.

Możesz odwołać się do [wbudowanego kodu źródłowego konwerterów](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) jako implementacji odwołań do pisania konwerterów niestandardowych.

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

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Jeśli zostanie wyświetlony komunikat (na przykład `throw new JsonException("Error occurred")`, wyjątek nadal udostępnia ścieżkę we właściwości <xref:System.Text.Json.JsonException.Path>.

## <a name="register-a-custom-converter"></a>Rejestrowanie niestandardowego konwertera

*Zarejestruj* konwerter niestandardowy, aby zastosować `Serialize` i `Deserialize` metody. Wybierz jedną z następujących metod:

* Dodaj wystąpienie klasy Converter do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.
* Zastosuj atrybut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) do właściwości, które wymagają konwertera niestandardowego.
* Zastosuj atrybut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) do klasy lub struktury, która reprezentuje niestandardowy typ wartości.

## <a name="registration-sample---converters-collection"></a>Przykład rejestracji — kolekcja konwerterów 

Oto przykład, który sprawia, że <xref:System.ComponentModel.DateTimeOffsetConverter> domyślny dla właściwości typu <xref:System.DateTimeOffset>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

Załóżmy, że Serializacja wystąpienia następującego typu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Oto przykład danych wyjściowych JSON, które pokazują, że użyto niestandardowego konwertera:

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Poniższy kod używa tego samego podejścia do deserializacji przy użyciu niestandardowego konwertera `DateTimeOffset`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a>Przykład rejestracji — [JsonConverter] na właściwości

Poniższy kod wybiera niestandardowy konwerter właściwości `Date`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

Kod do serializacji `WeatherForecastWithConverterAttribute` nie wymaga użycia `JsonSerializeOptions.Converters`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

Kod do deserializacji również nie wymaga użycia `Converters`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a>Przykład rejestracji — [JsonConverter] w typie

Oto kod, który tworzy strukturę i stosuje do niej atrybut `[JsonConverter]`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

Oto niestandardowy konwerter dla poprzedniej struktury:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

Atrybut `[JsonConvert]` w strukturze rejestruje niestandardowy konwerter jako domyślny dla właściwości typu `Temperature`. Konwerter jest automatycznie używany we właściwości `TemperatureCelsius` następującego typu podczas serializacji lub deserializacji:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a>Pierwszeństwo rejestracji konwertera

Podczas serializacji lub deserializacji konwerter jest wybierany dla każdego elementu JSON w następującej kolejności, na podstawie najwyższego priorytetu:

* `[JsonConverter]` zastosowana do właściwości.
* Konwerter dodany do kolekcji `Converters`.
* `[JsonConverter]` zastosowana do niestandardowego typu wartości lub POCO.

Jeśli wiele konwerterów niestandardowych dla typu są zarejestrowane w kolekcji `Converters`, zostanie użyty pierwszy konwerter zwracający wartość true dla `CanConvert`.

Wbudowany konwerter jest wybierany tylko wtedy, gdy nie zarejestrowano żadnego odpowiedniego konwertera niestandardowego.

## <a name="converter-samples-for-common-scenarios"></a>Przykłady konwerterów dla typowych scenariuszy

Poniższe sekcje zawierają przykłady konwerterów, które dotyczą niektórych typowych scenariuszy, które nie obsługują funkcji wbudowanych.

* [Deserializacja wywnioskowanych typów do właściwości obiektu](#deserialize-inferred-types-to-object-properties)
* [Obsługa słownika z kluczem niebędącym ciągiem](#support-dictionary-with-non-string-key)
* [Obsługa deserializacji polimorficzna](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a>Deserializacja wywnioskowanych typów do właściwości obiektu

Podczas deserializacji do właściwości typu `object`zostanie utworzony obiekt `JsonElement`. Przyczyną jest to, że Deserializator nie wie, jakie typy CLR należy utworzyć, i nie próbuje go odgadnąć. Na przykład, jeśli właściwość JSON ma wartość "true", Deserializator nie uzna, że wartość jest `Boolean`, a jeśli element ma "01/01/2019", Deserializator nie uzna, że jest to `DateTime`.

Wnioskowanie o typie może być niedokładne. Jeśli Deserializator analizuje numer JSON, który nie ma punktu dziesiętnego jako `long`, co może spowodować problemy poza zakresem, jeśli wartość została pierwotnie zserializowana jako `ulong` lub `BigInteger`. Analizowanie liczby, która ma przecinek dziesiętny jako `double` może stracić dokładnooć, jeśli liczba została pierwotnie zserializowana jako `decimal`.

W przypadku scenariuszy, które wymagają wnioskowania o typie, poniższy kod przedstawia niestandardowy konwerter dla `object` właściwości. Kod konwertuje:

* `true` i `false` do `Boolean`
* Liczby bez wartości dziesiętnej do `long`
* Liczby z liczbą dziesiętną do `double`
* Daty do `DateTime`
* Ciągi do `string`
* Wszystkie inne elementy do `JsonElement`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

Następujący kod rejestruje konwerter:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

Oto przykładowy typ z właściwościami `object`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

Poniższy przykład JSON do deserializacji zawiera wartości, które zostaną rozszeregowane jako `DateTime`, `long`i `string`:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Bez niestandardowego konwertera deserializacja umieszcza `JsonElement` w każdej właściwości.

[Folder testów jednostkowych](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) w przestrzeni nazw `System.Text.Json.Serialization` zawiera więcej przykładów niestandardowych konwerterów, które obsługują deserializacji do właściwości `object`.

### <a name="support-dictionary-with-non-string-key"></a>Obsługa słownika z kluczem niebędącym ciągiem

Wbudowana obsługa kolekcji słowników ma na celu `Dictionary<string, TValue>`. Oznacza to, że klucz musi być ciągiem. Aby zapewnić obsługę słownika z liczbą całkowitą lub innym typem jako klucz, wymagany jest konwerter niestandardowy.

Poniższy kod przedstawia niestandardowy konwerter, który działa z `Dictionary<Enum,TValue>`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Następujący kod rejestruje konwerter:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

Konwerter może serializować i deserializować Właściwość `TemperatureRanges` poniższej klasy, która używa następujących `Enum`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

Dane wyjściowe JSON z serializacji wyglądają podobnie jak w poniższym przykładzie:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

[Folder testy jednostkowe](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) w przestrzeni nazw `System.Text.Json.Serialization` zawiera więcej przykładów niestandardowych konwerterów, które obsługują słowniki niebędące ciągami.

### <a name="support-polymorphic-deserialization"></a>Obsługa deserializacji polimorficzna

Wbudowane funkcje zapewniają ograniczony zakres [serializacji polimorficznej](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ale nie obsługują deserializacji. Deserializacja wymaga konwertera niestandardowego.

Załóżmy na przykład, że masz `Person` abstrakcyjną klasę bazową z `Employee` i `Customer` klasami pochodnymi. Deserializacja polimorficzna oznacza, że w czasie projektowania można określić `Person` jako element docelowy deserializacji, a `Customer` i `Employee` obiektów w formacie JSON są prawidłowo deserializowane w czasie wykonywania. Podczas deserializacji należy znaleźć wskazówki, które identyfikują wymagany typ w kodzie JSON. Rodzaje dostępnych wskazówek różnią się w zależności od scenariusza. Na przykład może być dostępna właściwość rozróżniacza lub może zależeć od obecności lub braku określonej właściwości. Bieżąca wersja `System.Text.Json` nie udostępnia atrybutów, aby określić sposób obsługi scenariuszy deserializacji polimorficznych, dlatego wymagane są niestandardowe konwertery.

Poniższy kod przedstawia klasę bazową, dwie klasy pochodne i niestandardowy konwerter dla nich. Konwerter używa właściwości rozróżniacza do wykonywania deserializacji polimorficznej. Rozróżniacz typu nie znajduje się w definicjach klas, ale jest tworzony podczas serializacji i jest odczytywany podczas deserializacji.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

Następujący kod rejestruje konwerter:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

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

Kod konwertera w poprzednim przykładzie odczytuje i zapisuje każdą właściwość ręcznie. Alternatywą jest wywołanie `Deserialize` lub `Serialize` do wykonania niektórych zadań. Aby zapoznać się z przykładem, zobacz [ten StackOverflow post](https://stackoverflow.com/a/59744873/12509023).

## <a name="other-custom-converter-samples"></a>Inne przykłady konwerterów niestandardowych

[Migracja z Newtonsoft.Json do System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) artykułu zawiera dodatkowe przykłady konwerterów niestandardowych.

[Folder testy jednostkowe](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) w `System.Text.Json.Serialization` kodzie źródłowym zawiera inne niestandardowe przykłady konwerterów, takie jak:

* [Konwerter Int32, który konwertuje wartość null na wartość 0 podczas deserializacji](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [Konwerter Int32, który zezwala na wartości typu String i Number przy deserializacji](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [Konwerter wyliczenia](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [Listowy konwerter\<T > akceptujący dane zewnętrzne](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Długi konwerter [], który działa z rozdzielaną przecinkami listą liczb](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs) 

Jeśli musisz utworzyć konwerter, który modyfikuje zachowanie istniejącego wbudowanego konwertera, możesz uzyskać [kod źródłowy istniejącego konwertera](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) , który będzie używany jako punkt wyjścia do dostosowania.

## <a name="additional-resources"></a>Dodatkowe zasoby

* [Kod źródłowy wbudowanych konwerterów](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [Obsługa DateTime i DateTimeOffset w System.Text.Json](../datetime/system-text-json-support.md)
* [Przegląd System.Text.Json](system-text-json-overview.md)
* [Jak używać System.Text.Json](system-text-json-how-to.md)
* [Jak przeprowadzić migrację z Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Dokumentacja interfejsu API System.Text.Json](xref:System.Text.Json)
* [System.Text.Json. Dokumentacja interfejsu API serializacji](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
