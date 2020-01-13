---
title: Migrowanie z Newtonsoft. JSON do System. Text. JSON-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 8b3ffc885691264548a19f694d159ce07aba7550
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904685"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Jak przeprowadzić migrację z Newtonsoft. JSON do System. Text. JSON

W tym artykule pokazano, jak przeprowadzić migrację z [Newtonsoft. JSON](https://www.newtonsoft.com/json) do <xref:System.Text.Json>.

 `System.Text.Json` koncentruje się głównie na wydajności, zabezpieczeniach i zgodności ze standardami. Ma pewne kluczowe różnice w zachowaniu domyślnym i nie ma wpływu na funkcję z `Newtonsoft.Json`. W przypadku niektórych scenariuszy `System.Text.Json` nie ma wbudowanych funkcji, ale istnieją zalecane obejścia tego problemu. W przypadku innych scenariuszy obejścia są niepraktyczne. Jeśli aplikacja zależy od brakującej funkcji, rozważ [zgłoszenie problemu](https://github.com/dotnet/runtime/issues/new) , aby dowiedzieć się, czy można dodać wsparcie dla danego scenariusza.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

W większości tego artykułu zawarto informacje dotyczące korzystania z interfejsu API <xref:System.Text.Json.JsonSerializer>, ale zawiera on również wskazówki dotyczące sposobu korzystania z <xref:System.Text.Json.JsonDocument> (która reprezentuje typy Document Object Model lub DOM), <xref:System.Text.Json.Utf8JsonReader>i <xref:System.Text.Json.Utf8JsonWriter>. Artykuł jest podzielony na sekcje w następującej kolejności:

* [Różnice dotyczące **domyślnego** zachowania JsonSerializer w porównaniu do Newtonsoft. JSON](#differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson)
* [Scenariusze korzystające z JsonSerializer, które wymagają obejścia](#scenarios-using-jsonserializer-that-require-workarounds)
* [Scenariusze, które nie są obecnie obsługiwane przez JsonSerializer](#scenarios-that-jsonserializer-currently-doesnt-support)
* [JsonDocument i Jsonelement w porównaniu do JToken (np. JObject, JArray)](#jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray)
* [Utf8JsonReader w porównaniu do JsonTextReader](#utf8jsonreader-compared-to-jsontextreader)
* [Utf8JsonWriter w porównaniu do JsonTextWriter](#utf8jsonwriter-compared-to-jsontextwriter)

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Różnice dotyczące domyślnego zachowania JsonSerializer w porównaniu do Newtonsoft. JSON

<xref:System.Text.Json> jest domyślnie rygorystyczne i pozwala uniknąć wszelkich odgadnąć lub interpretacji w imieniu wywołującego, podkreślając deterministyczne zachowanie. Biblioteka jest celowo zaprojektowana w taki sposób, aby uzyskać wydajność i bezpieczeństwo. Domyślnie `Newtonsoft.Json` jest elastyczny. Ta podstawowa różnica w projekcie jest zbyt wiele z poniższych konkretnych różnic w domyślnym zachowaniu.

### <a name="case-insensitive-deserialization"></a>Deserializacja bez uwzględniania wielkości liter 

Podczas deserializacji `Newtonsoft.Json` domyślnie dopasowywania nazw właściwości bez uwzględniania wielkości liter. W <xref:System.Text.Json> domyślnym rozróżniana jest wielkość liter, co zapewnia lepszą wydajność, ponieważ jest to dokładne dopasowanie. Aby uzyskać informacje o sposobie dopasowywania wielkości liter, zobacz dopasowanie do [wielkości](system-text-json-how-to.md#case-insensitive-property-matching)liter.

Jeśli używasz `System.Text.Json` pośrednio przy użyciu ASP.NET Core, nie musisz nic robić, aby uzyskać zachowanie takie jak `Newtonsoft.Json`. ASP.NET Core określa ustawienia [nazw właściwości notacji CamelCase](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) i bez uwzględniania wielkości liter, gdy używa `System.Text.Json`.

### <a name="comments"></a>Komentarze

Podczas deserializacji `Newtonsoft.Json` domyślnie ignoruje komentarze w formacie JSON. Domyślnie <xref:System.Text.Json> ma zgłosić wyjątki dla komentarzy, ponieważ Specyfikacja [RFC 8259](https://tools.ietf.org/html/rfc8259) nie zawiera ich. Aby uzyskać informacje o sposobach zezwalania na komentarze, zobacz [Zezwalanie na komentarze i końcowe przecinki](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Końcowe przecinki

Podczas deserializacji `Newtonsoft.Json` domyślnie ignoruje końcowe przecinki. Ignoruje także kilka końcowych przecinków (na przykład `[{"Color":"Red"},{"Color":"Green"},,]`). Domyślnie <xref:System.Text.Json> ma zgłosić wyjątki dla końcowych przecinków, ponieważ Specyfikacja [RFC 8259](https://tools.ietf.org/html/rfc8259) nie zezwala. Aby uzyskać informacje na temat sposobu ich akceptowania `System.Text.Json`, zobacz [Zezwalanie na komentarze i końcowe przecinki](system-text-json-how-to.md#allow-comments-and-trailing-commas). Nie ma możliwości zezwalania na wielokrotne końcowe przecinki.

### <a name="json-strings-property-names-and-string-values"></a>Ciągi JSON (nazwy właściwości i wartości ciągów)

Podczas deserializacji `Newtonsoft.Json` akceptuje nazwy właściwości ujęte w podwójne cudzysłowy, apostrofy lub bez cudzysłowu. Akceptuje wartości ciągów ujęte w cudzysłów lub pojedyncze cudzysłowy. Na przykład `Newtonsoft.Json` akceptuje następujący kod JSON:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json` akceptuje tylko nazwy właściwości i wartości ciągu w podwójnych cudzysłowach, ponieważ ten format jest wymagany przez specyfikację [RFC 8259](https://tools.ietf.org/html/rfc8259) i jest jedynym formatem uważanym za prawidłowy kod JSON.

Wartość zawarta w pojedynczym cudzysłowie powoduje, że element [jsonexception](xref:System.Text.Json.JsonException) z następującym komunikatem:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Wartości niebędące ciągami dla właściwości ciągu

`Newtonsoft.Json` akceptuje wartości niebędące ciągami, takie jak liczba lub literały `true` i `false`, dla deserializacji do właściwości typu String. Oto przykład kodu JSON, który `Newtonsoft.Json` pomyślnie deserializacji do następującej klasy:

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json` nie deserializacji wartości niebędących ciągami na właściwości ciągu. Odebrana wartość niebędąca ciągiem dla pola ciągu powoduje wyrażenie [jsonexception](xref:System.Text.Json.JsonException) z następującym komunikatem:

```
The JSON value could not be converted to System.String.
```

### <a name="converter-registration-precedence"></a>Pierwszeństwo rejestracji konwertera

Priorytet rejestracji `Newtonsoft.Json` dla konwerterów niestandardowych jest następujący:

* Atrybut właściwości
* Atrybut typu
* Kolekcja [konwerterów](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)

Ta kolejność oznacza, że konwerter niestandardowy w kolekcji `Converters` jest zastępowany przez konwerter zarejestrowany przez zastosowanie atrybutu na poziomie typu. Obie te rejestracje są zastępowane przez atrybut na poziomie właściwości.

Pierwszeństwo rejestracji <xref:System.Text.Json> dla konwerterów niestandardowych jest inne:

* Atrybut właściwości
* Kolekcja <xref:System.Text.Json.JsonSerializerOptions.Converters>
* Atrybut typu

Różnica polega na tym, że konwerter niestandardowy w kolekcji `Converters` przesłania atrybut na poziomie typu. Zamierzone jest zamierzenie, aby zmiany w czasie wykonywania zastępowały opcje czasu projektowania. Nie ma możliwości zmiany pierwszeństwa.

Aby uzyskać więcej informacji na temat rejestrowania niestandardowego konwertera, zobacz [Rejestrowanie niestandardowego konwertera](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="character-escaping"></a>Znak ucieczki

Podczas serializacji `Newtonsoft.Json` jest relatywnie ograniczając, aby zezwalać na znaki, bez ucieczki. Oznacza to, że nie zastępuje ich `\uxxxx`, gdzie `xxxx` jest punktem kodu znaku. Tam, gdzie wykonuje te zmiany, robi to, emitując `\` przed znakiem (na przykład `"` zostanie `\"`). <xref:System.Text.Json> domyślnie uzupełnia więcej znaków, aby zapewnić ochronę przed ochroną przed wieloma lokacjami (XSS) lub ataki z ujawnianiem informacji, a tym samym przy użyciu sekwencji składającej się z sześciu znaków. `System.Text.Json` domyślnie wyprowadza wszystkie znaki inne niż ASCII, więc nie trzeba wykonywać żadnych czynności, jeśli używasz `StringEscapeHandling.EscapeNonAscii` w `Newtonsoft.Json`. `System.Text.Json` również domyślnie wyprowadza znaki z uwzględnieniem kodu HTML. Aby dowiedzieć się, jak zastąpić domyślne zachowanie `System.Text.Json`, zobacz [Dostosowywanie kodowania znaków](system-text-json-how-to.md#customize-character-encoding).

### <a name="deserialization-of-object-properties"></a>Deserializacja właściwości obiektu

Gdy `Newtonsoft.Json` deserializacji do `object` właściwości w POCOs lub w słownikach typu `Dictionary<string, object>`,:

* Wnioskuje typ wartości pierwotnych w ładunku JSON (innym niż `null`) i zwraca przechowywane `string`, `long`, `double`, `boolean`lub `DateTime` jako obiekt opakowany. *Wartości pierwotne* to pojedyncze wartości JSON, takie jak numer JSON, ciąg, `true`, `false`lub `null`.
* Zwraca `JObject` lub `JArray` dla wartości złożonych w ładunku JSON. *Wartości złożone* to kolekcje par klucz-wartość JSON w nawiasach klamrowych (`{}`) lub listy wartości w nawiasach kwadratowych (`[]`). Właściwości i wartości w nawiasach klamrowych mogą mieć dodatkowe właściwości lub wartości.
* Zwraca odwołanie o wartości null, gdy ładunek ma `null`y literał JSON.

<xref:System.Text.Json> przechowuje `JsonElement` w ramce dla wartości pierwotnych i złożonych w ramach właściwości `System.Object` lub wartości słownika. Jednak traktuje `null` tak samo jak `Newtonsoft.Json` i zwraca odwołanie o wartości null, gdy ładunek ma `null` w nim literał JSON.

Aby zaimplementować wnioskowanie o właściwościach `object`, Utwórz konwerter jak przykład w temacie [How to Write Custom Converters](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).

### <a name="maximum-depth"></a>Maksymalna głębokość

`Newtonsoft.Json` domyślnie nie ma maksymalnego limitu głębokości. W przypadku <xref:System.Text.Json> istnieje domyślny limit 64 i można go skonfigurować przez ustawienie <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>.

### <a name="stack-type-handling"></a>Obsługa typów stosu

W <xref:System.Text.Json>kolejność zawartości stosu jest odwrócona, gdy jest serializowana. To zachowanie dotyczy następujących typów i typów i zdefiniowanych przez użytkownika rodzajów, które pochodzą od nich:

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

Konwerter niestandardowy można zaimplementować, aby zachować zawartość stosu w tej samej kolejności.

### <a name="omit-null-value-properties"></a>Pomiń właściwości o wartości null

`Newtonsoft.Json` ma ustawienie globalne, które powoduje, że właściwości null wartości mają być wykluczone z serializacji: [NullValueHandling. ignore](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_NullValueHandling.htm). Odpowiadająca opcja w <xref:System.Text.Json> jest <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues%2A>.

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Scenariusze korzystające z JsonSerializer, które wymagają obejścia

Następujące scenariusze nie są obsługiwane przez wbudowaną funkcję, ale dla obejść jest dostępny przykładowy kod. Większość obejść wymaga zaimplementowania [konwerterów niestandardowych](system-text-json-converters-how-to.md).

### <a name="specify-date-format"></a>Określ format daty

`Newtonsoft.Json` oferuje kilka sposobów, aby kontrolować sposób serializacji i deserializacji właściwości typów `DateTime` i `DateTimeOffset`:

* Ustawienie `DateTimeZoneHandling` może służyć do serializacji wszystkich wartości `DateTime` jako daty UTC.
* Ustawienia `DateFormatString` i konwerterów `DateTime` mogą służyć do dostosowywania formatu ciągów daty.

W <xref:System.Text.Json>jedynym formatem, który ma wbudowaną obsługę, jest ISO 8601-1:2019, ponieważ jest on powszechnie przyjęty, niejednoznaczny i umożliwia precyzyjne przekazanie rundy. Aby użyć innego formatu, Utwórz konwerter niestandardowy. Aby uzyskać więcej informacji, zobacz [Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON](../datetime/system-text-json-support.md).

### <a name="quoted-numbers"></a>Liczby ujęte w cudzysłów

`Newtonsoft.Json` może serializować lub deserializować liczby reprezentowane przez ciągi JSON (ujęte w cudzysłowy). Na przykład może akceptować: `{"DegreesCelsius":"23"}`, a nie `{"DegreesCelsius":23}`. Aby włączyć to zachowanie w <xref:System.Text.Json>, zaimplementuj niestandardowy konwerter, jak w poniższym przykładzie. Konwerter obsługuje właściwości zdefiniowane jako `long`:

* Serializować je jako ciągi JSON. 
* Akceptuje liczby i cyfry JSON w cudzysłowie podczas deserializacji.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Zarejestrowanie tego konwertera niestandardowego przy [użyciu atrybutu](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) dla poszczególnych właściwości `long` lub poprzez [dodanie konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters>.

### <a name="dictionary-with-non-string-key"></a>Słownik z kluczem niebędącym ciągiem

`Newtonsoft.Json` obsługuje kolekcje typu `Dictionary<TKey, TValue>`. Wbudowana obsługa kolekcji słowników w <xref:System.Text.Json> jest ograniczona do `Dictionary<string, TValue>`. Oznacza to, że klucz musi być ciągiem.

Aby zapewnić obsługę słownika z liczbą całkowitą lub innym typem jako klucz, Utwórz konwerter jak przykład w temacie [How to Write Custom Converters](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).

### <a name="polymorphic-serialization"></a>Serializacja polimorficzna

`Newtonsoft.Json` automatycznie wykonuje serializacji polimorficznej. Aby uzyskać informacje o ograniczonych możliwościach serializacji polimorficznej <xref:System.Text.Json>, zobacz [Serializowanie właściwości klas pochodnych](system-text-json-how-to.md#serialize-properties-of-derived-classes).

Opisane obejście ma na celu zdefiniowanie właściwości, które mogą zawierać klasy pochodne jako typ `object`. Jeśli to nie jest możliwe, kolejną opcją jest utworzenie konwertera z metodą `Write` dla całej hierarchii typów dziedziczenia, na przykład w przypadku [pisania konwerterów niestandardowych](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="polymorphic-deserialization"></a>Deserializacja polimorficzna

`Newtonsoft.Json` ma ustawienie `TypeNameHandling`, które dodaje metadane nazwy typu do JSON podczas serializacji. Używa metadanych podczas deserializacji w celu wykonania deserializacji polimorficznej. <xref:System.Text.Json> może wykonywać ograniczony zakres [serializacji polimorficznej](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ale nie deserializacji polimorficznej.

Aby obsłużyć deserializacja polimorficzna, Utwórz konwerter, taki jak przykład, w [jaki sposób pisać konwertery niestandardowe](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="required-properties"></a>Wymagane właściwości

Podczas deserializacji <xref:System.Text.Json> nie zgłasza wyjątku, jeśli żadna wartość nie zostanie odebrana w formacie JSON dla jednej z właściwości typu docelowego. Na przykład jeśli masz klasę `WeatherForecast`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Następujący kod JSON jest deserializowany bez błędu:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

Aby deserializacja nie powiodła się, jeśli w kodzie JSON nie ma właściwości `Date`, zaimplementuj konwerter niestandardowy. Następujący przykładowy kod konwertera zgłasza wyjątek, jeśli właściwość `Date` nie jest ustawiona po zakończeniu deserializacji:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

Zarejestrowanie tego konwertera niestandardowego przy [użyciu atrybutu klasy poco](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) lub poprzez [dodanie konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters>.

W przypadku przestrzegania tego wzorca nie należy przechodzić do obiektu options podczas rekursywnego wywoływania <xref:System.Text.Json.JsonSerializer.Serialize%2A> lub <xref:System.Text.Json.JsonSerializer.Deserialize%2A>. Obiekt Options zawiera kolekcję <xref:System.Text.Json.JsonSerializerOptions.Converters%2A>. Jeśli przekażesz go do `Serialize` lub `Deserialize`, konwerter niestandardowy wywołuje się do siebie, tworząc nieskończoną pętlę, która powoduje wyjątek przepełnienia stosu. Jeśli opcje domyślne nie są możliwe, Utwórz nowe wystąpienie opcji z ustawieniami, które są potrzebne. Takie podejście będzie powolne, ponieważ każde nowe wystąpienie pamięci podręcznej jest niezależne.

Poprzedni kod konwertera to uproszczony przykład. Dodatkowa logika powinna być wymagana, jeśli trzeba obsługiwać atrybuty (takie jak [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) lub różne opcje (takie jak kodery niestandardowe). Ponadto przykładowy kod nie obsługuje właściwości, dla których ustawiono wartość domyślną w konstruktorze. To podejście nie różni się między następującymi scenariuszami:

* Brak właściwości w kodzie JSON.
* Właściwość typu niedopuszczający wartości null jest obecna w notacji JSON, ale wartość jest wartością domyślną dla tego typu, np. zero dla `int`.
* Właściwość dla typu dopuszczającego wartość null jest obecna w notacji JSON, ale wartość jest równa null.

### <a name="deserialize-null-to-non-nullable-type"></a>Deserializacja wartości null na typ niedopuszczający wartości null 

`Newtonsoft.Json` nie zgłasza wyjątku w następującym scenariuszu:

* `NullValueHandling` jest ustawiony na `Ignore`i
* Podczas deserializacji kod JSON zawiera wartość null dla typu, który nie dopuszcza wartości null.

W tym samym scenariuszu <xref:System.Text.Json> generuje wyjątek. (Odpowiednie ustawienie obsługi wartości null to <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>.)

Jeśli jesteś własnym typem docelowym, najlepszym obejściem jest to, że właściwość w pytaniu nie dopuszcza wartości null (na przykład zmiana `int` na `int?`).

Innym obejściem jest tworzenie konwertera dla typu, takiego jak Poniższy przykład, który obsługuje wartości null dla typów `DateTimeOffset`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Zarejestrowanie tego konwertera niestandardowego przy [użyciu atrybutu właściwości](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) lub przez [dodanie konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters>.

**Uwaga:** Poprzedni konwerter **obsługuje wartości null inaczej** niż `Newtonsoft.Json` dla POCOs, które określają wartości domyślne. Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Załóżmy, że następujący kod JSON jest deserializowany przy użyciu poprzedniego konwertera:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Po deserializacji właściwość `Date` ma 1/1/0001 (`default(DateTimeOffset)`), oznacza to, że wartość ustawiona w konstruktorze jest zastępowana. Mając te same POCO i kod JSON, `Newtonsoft.Json` deserializacji spowodowałaby pozostawienie 1/1/2001 we właściwości `Date`.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Deserializacja do niemodyfikowalnych klas i struktur

`Newtonsoft.Json` może deserializować do niemodyfikowalnych klas i struktur, ponieważ może używać konstruktorów z parametrami. <xref:System.Text.Json> obsługuje tylko publiczne konstruktory bez parametrów. Jako obejście można wywołać konstruktora z parametrami w niestandardowym konwerterze.

Oto niezmienna struktura z wieloma parametrami konstruktora:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

A oto konwerter, który serializować i deserializacji tej struktury:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Zarejestruj ten konwerter niestandardowy, [dodając konwerter](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters>.

Aby zapoznać się z przykładem podobnego konwertera, który obsługuje otwarte właściwości ogólne, zobacz [wbudowany konwerter par klucz-wartość](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Określ Konstruktor do użycia

Atrybut `[JsonConstructor]` `Newtonsoft.Json` pozwala określić Konstruktor, który ma być wywoływany podczas deserializacji do POCO. <xref:System.Text.Json> obsługuje tylko konstruktory bez parametrów. Jako obejście można wywołać każdy Konstruktor, którego potrzebujesz w niestandardowym konwerterze. Zobacz przykład dla [deserializacji do niemodyfikowalnych klas i struktur](#deserialize-to-immutable-classes-and-structs).

### <a name="conditionally-ignore-a-property"></a>Warunkowo Ignoruj Właściwość

`Newtonsoft.Json` ma kilka sposobów, aby warunkowo ignorować właściwość podczas serializacji lub deserializacji:

* `DefaultContractResolver` umożliwia wybranie właściwości, które mają zostać dołączone lub wykluczone w oparciu o dowolne kryteria. 
* Ustawienia `NullValueHandling` i `DefaultValueHandling` na `JsonSerializerSettings` pozwalają określić, że wszystkie właściwości null-value lub wartość domyślna wartości powinny być ignorowane.
* Ustawienia `NullValueHandling` i `DefaultValueHandling` w atrybucie `[JsonProperty]` umożliwiają określanie poszczególnych właściwości, które mają być ignorowane, gdy wartość jest równa null lub wartości domyślnej.

<xref:System.Text.Json> oferuje następujące sposoby pomijania właściwości podczas serializacji:

* Atrybut [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) właściwości powoduje pominięcie właściwości z poziomu JSON podczas serializacji.
* Opcja globalna [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) umożliwia wykluczenie wszystkich właściwości o wartości null.
* Opcja globalna [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) umożliwia wykluczenie wszystkich właściwości tylko do odczytu.

Te opcje **nie** pozwalają:

* Zignoruj wszystkie właściwości, które mają wartość domyślną dla tego typu.
* Ignoruj wybrane właściwości, które mają wartość domyślną dla tego typu.
* Ignoruj wybrane właściwości, jeśli ich wartość jest równa null.
* Ignoruj wybrane właściwości na podstawie arbitralnych kryteriów ocenionych w czasie wykonywania. 

W przypadku tej funkcji można napisać konwerter niestandardowy. Oto przykład POCO i niestandardowy konwerter dla niego, który ilustruje następujące podejście:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Konwerter powoduje pominięcie właściwości `Summary` z serializacji, jeśli jej wartość jest równa null, pusty ciąg lub "N/A". 

Zarejestrowanie tego konwertera niestandardowego przy [użyciu atrybutu klasy](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) lub przez [dodanie konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters>.

Takie podejście wymaga dodatkowej logiki, jeśli:

* POCO zawiera złożone właściwości.
* Musisz obsługiwać atrybuty, takie jak `[JsonIgnore]` lub opcje, takie jak kodery niestandardowe.

### <a name="callbacks"></a>Wywołania zwrotne

`Newtonsoft.Json` umożliwia wykonywanie kodu niestandardowego w kilku punktach w procesie serializacji lub deserializacji:

* OnDeserializing (przy rozpoczynaniu deserializacji obiektu)
* Onserializacja (po zakończeniu deserializacji obiektu)
* Onserializacja (gdy zaczynasz serializować obiekt)
* Onserialed (po zakończeniu serializacji obiektu)

W <xref:System.Text.Json>można symulować wywołania zwrotne, pisząc konwertery niestandardowe. W poniższym przykładzie przedstawiono niestandardowy konwerter dla POCO. Konwerter zawiera kod, który wyświetla komunikat w każdym punkcie, który odpowiada `Newtonsoft.Json` wywołanie zwrotne.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Zarejestrowanie tego konwertera niestandardowego przy [użyciu atrybutu klasy](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) lub przez [dodanie konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters>.

Jeśli używasz niestandardowego konwertera, który następuje po powyższym przykładzie:

* Kod `OnDeserializing` nie ma dostępu do nowego wystąpienia POCO. Aby manipulować nowym wystąpieniem POCO na początku deserializacji, Umieść ten kod w konstruktorze POCO.
* Nie przekazuj w obiekcie Options podczas rekursywnego wywoływania `Serialize` lub `Deserialize`. Obiekt Options zawiera kolekcję `Converters`. Jeśli przekażesz go do `Serialize` lub `Deserialize`, zostanie użyty konwerter, dzięki czemu nieskończona pętla powoduje wyjątek przepełnienia stosu.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Scenariusze, które nie są obecnie obsługiwane przez JsonSerializer

Obejścia są możliwe w następujących scenariuszach, ale niektóre z nich byłyby stosunkowo trudne do zaimplementowania. Ten artykuł nie zawiera przykładów kodu dla tych scenariuszy.

Nie jest to pełna lista funkcji `Newtonsoft.Json`, które nie mają odpowiedników w `System.Text.Json`. Lista zawiera wiele scenariuszy, które zostały zażądane w przypadku problemów z usługą [GitHub](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) lub wpisów [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) .

Jeśli zaimplementowano obejście dla jednego z tych scenariuszy i można udostępnić kod, zaznacz przycisk "**Ta strona**" w dolnej części strony. Powoduje to utworzenie problemu usługi GitHub i dodanie go do problemów, które są wyświetlane w dolnej części strony.

### <a name="types-without-built-in-support"></a>Typy bez wbudowanej obsługi

<xref:System.Text.Json> nie zapewnia wbudowanego wsparcia dla następujących typów:

* <xref:System.Data.DataTable> i powiązane typy
* F#typy, takie jak [związki](../../fsharp/language-reference/discriminated-unions.md)rozłączne, [typy rekordów](../../fsharp/language-reference/records.md)i [anonimowe typy rekordów](../../fsharp/language-reference/anonymous-records.md).
* Typy kolekcji w przestrzeni nazw <xref:System.Collections.Specialized>
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple> i powiązane typy ogólne

Konwertery niestandardowe można zaimplementować dla typów, które nie mają wbudowanej obsługi.

### <a name="public-and-non-public-fields"></a>Pola publiczne i niepubliczne

`Newtonsoft.Json` może serializować i deserializować pola oraz właściwości. <xref:System.Text.Json> działa tylko z właściwościami publicznymi. Te funkcje mogą zapewniać konwertery niestandardowe.

### <a name="internal-and-private-property-setters-and-getters"></a>Metody i metody pobierające właściwości wewnętrznych i prywatnych

`Newtonsoft.Json` może używać prywatnych i wewnętrznych metod ustawiających właściwości i metody pobierającej za pośrednictwem atrybutu `JsonProperty`. <xref:System.Text.Json> obsługuje tylko publiczne metody ustawiające. Te funkcje mogą zapewniać konwertery niestandardowe.

### <a name="preserve-object-references-and-handle-loops"></a>Zachowaj odwołania do obiektów i pętle obsługi

Domyślnie `Newtonsoft.Json` serializacji według wartości. Na przykład jeśli obiekt zawiera dwie właściwości, które zawierają odwołanie do tego samego obiektu `Person`, wartości właściwości tego obiektu `Person` są zduplikowane w kodzie JSON.

`Newtonsoft.Json` ma `PreserveReferencesHandling` ustawienia `JsonSerializerSettings`, które umożliwiają serializację przez odwołanie:

* Metadane identyfikatora są dodawane do pliku JSON utworzonego dla pierwszego obiektu `Person`.
* KOD JSON tworzony dla drugiego obiektu `Person` zawiera odwołanie do tego identyfikatora zamiast wartości właściwości.

`Newtonsoft.Json` ma także `ReferenceLoopHandling` ustawienie, które umożliwia ignorowanie odwołań cyklicznych zamiast zgłaszania wyjątku.

<xref:System.Text.Json> obsługuje serializacji tylko przez wartość i zgłasza wyjątek dla odwołań cyklicznych.

### <a name="systemruntimeserialization-attributes"></a>Atrybuty System. Runtime. Serialization

<xref:System.Text.Json> nie obsługuje atrybutów z przestrzeni nazw `System.Runtime.Serialization`, takich jak `DataMemberAttribute` i `IgnoreDataMemberAttribute`.

### <a name="octal-numbers"></a>Liczby ósemkowe

`Newtonsoft.Json` traktuje liczby z zerem wiodącym jako liczba ósemkowa. <xref:System.Text.Json> nie zezwala na zera wiodące, ponieważ Specyfikacja [RFC 8259](https://tools.ietf.org/html/rfc8259) nie zezwala.

### <a name="populate-existing-objects"></a>Wypełnij istniejące obiekty

Metoda `JsonConvert.PopulateObject` w `Newtonsoft.Json` deserializacji dokumentu JSON do istniejącego wystąpienia klasy, zamiast tworzyć nowe wystąpienie. <xref:System.Text.Json> zawsze tworzy nowe wystąpienie typu docelowego przy użyciu domyślnego publicznego konstruktora bez parametrów. Konwertery niestandardowe mogą zdeserializować do istniejącego wystąpienia.

### <a name="reuse-rather-than-replace-properties"></a>Użyj ponownie zamiast właściwości Zamień

Ustawienie `ObjectCreationHandling` `Newtonsoft.Json` pozwala określić, że obiekty w właściwości powinny być ponownie używane, a nie zastąpione podczas deserializacji. <xref:System.Text.Json> zawsze zastępuje obiekty we właściwościach.  Te funkcje mogą zapewniać konwertery niestandardowe.

### <a name="add-to-collections-without-setters"></a>Dodaj do kolekcji bez metod ustawiających

Podczas deserializacji `Newtonsoft.Json` dodaje obiekty do kolekcji, nawet jeśli właściwość nie ma metody ustawiającej. <xref:System.Text.Json> ignoruje właściwości, które nie mają metod ustawiających. Te funkcje mogą zapewniać konwertery niestandardowe.

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json` można skonfigurować do zgłaszania wyjątków podczas deserializacji, jeśli dane JSON zawierają właściwości, których brakuje w typie docelowym. <xref:System.Text.Json> ignoruje dodatkowe właściwości w formacie JSON, z wyjątkiem sytuacji, gdy jest używany [atrybut [JsonExtensionData]](system-text-json-how-to.md#handle-overflow-json). Nie istnieje obejście dla brakującej funkcji członkowskiej.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json` umożliwia debugowanie przy użyciu `TraceWriter` do wyświetlania dzienników generowanych przez serializacji lub deserializacji. <xref:System.Text.Json> nie wykonuje rejestrowania.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument i Jsonelement w porównaniu do JToken (np. JObject, JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> umożliwia analizowanie i kompilowanie Document Object Model (DOM) **tylko do odczytu** z istniejących ładunków JSON. DOM zapewnia losowy dostęp do danych w ładunku JSON. Do elementów JSON, które tworzą ładunek, można uzyskać dostęp za pośrednictwem typu <xref:System.Text.Json.JsonElement>. Typ `JsonElement` udostępnia interfejsy API do konwersji tekstu JSON na popularne typy .NET. `JsonDocument` uwidacznia Właściwość <xref:System.Text.Json.JsonDocument.RootElement>.

### <a name="jsondocument-is-idisposable"></a>JsonDocument jest interfejs IDisposable

`JsonDocument` kompiluje widok danych w pamięci w buforze puli. W związku z tym, w przeciwieństwie do `JObject` lub `JArray` z `Newtonsoft.Json`, typ `JsonDocument` implementuje `IDisposable` i musi być używany wewnątrz bloku using. 

Zwróć `JsonDocument` z interfejsu API, jeśli chcesz przenieść własność okresu istnienia i usunąć odpowiedzialność do obiektu wywołującego. W większości przypadków nie jest to konieczne. Jeśli obiekt wywołujący musi współdziałać z całym dokumentem JSON, zwróć <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonDocument.RootElement%2A>, który jest <xref:System.Text.Json.JsonElement>. Jeśli obiekt wywołujący musi pracować z określonym elementem w dokumencie JSON, zwróć <xref:System.Text.Json.JsonElement.Clone%2A> tego <xref:System.Text.Json.JsonElement>. Jeśli powrócisz `RootElement` lub element podrzędny bezpośrednio bez tworzenia `Clone`, obiekt wywołujący nie będzie w stanie uzyskać dostępu do zwróconej `JsonElement` po usunięciu `JsonDocument`, do którego należy.

Oto przykład, który wymaga wprowadzenia `Clone`:

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());
   
    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

Poprzedni kod oczekuje `JsonElement`, który zawiera właściwość `fileName`. Otwiera plik JSON i tworzy `JsonDocument`. Metoda zakłada, że obiekt wywołujący chce współpracować z całym dokumentem, dlatego zwraca `Clone` `RootElement`. 

Jeśli zostanie wyświetlony `JsonElement` i zwróci element podrzędny, nie trzeba zwracać `Clone` elementu podrzędnego. Obiekt wywołujący jest odpowiedzialny za utrzymanie aktywności `JsonDocument`, do której należy `JsonElement` zakończono. Na przykład:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument jest tylko do odczytu

<xref:System.Text.Json> DOM nie może dodawać, usuwać ani modyfikować elementów JSON. Ta metoda została zaprojektowana w taki sposób, aby zwiększyć wydajność i zmniejszyć alokacje do analizy wspólnych rozmiarów ładunków JSON (czyli < 1 MB). Jeśli w scenariuszu obecnie jest używany modyfikowalny DOM, jedno z następujących obejść może być wykonalne:

* Aby skompilować `JsonDocument` od podstaw (to oznacza, że bez przekazywania istniejącego ładunku JSON do metody `Parse`), Napisz tekst JSON przy użyciu `Utf8JsonWriter` i Przeanalizuj dane wyjściowe z tego, aby utworzyć nowy `JsonDocument`.
* Aby zmodyfikować istniejące `JsonDocument`, należy użyć go do zapisania tekstu JSON, wprowadzenia zmian podczas pisania i przeanalizowania danych wyjściowych, aby utworzyć nowe `JsonDocument`.
* Aby scalić istniejące dokumenty JSON, równoważne `JObject.Merge` lub `JContainer.Merge` interfejsów API z `Newtonsoft.Json`, zobacz [ten problem](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)w serwisie GitHub.

### <a name="jsonelement-is-a-union-struct"></a>Jsonelement jest strukturą Union

`JsonDocument` uwidacznia `RootElement` jako właściwość typu <xref:System.Text.Json.JsonElement>, która jest Unią, typ struktury, która obejmuje dowolny element JSON. `Newtonsoft.Json` używa dedykowanych typów hierarchicznych, takich jak `JObject`,`JArray`, `JToken`i tak dalej. `JsonElement` to elementy, które można wyszukać i wyliczyć, i można użyć `JsonElement` do zmaterializowania elementów JSON do typów .NET.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Jak wyszukiwać element JsonDocument i Jsonelement dla elementów podrzędnych

Wyszukuje tokeny JSON przy użyciu `JObject` lub `JArray` z `Newtonsoft.Json` jest stosunkowo szybka, ponieważ są wyszukiwaniemi w słowniku. Zgodnie z porównaniem program wyszukuje `JsonElement` wymagające wyszukania właściwości i dlatego jest stosunkowo wolny (na przykład przy użyciu `TryGetProperty`). <xref:System.Text.Json> zaprojektowano w celu zminimalizowania początkowego czasu analizy zamiast czasu wyszukiwania. W związku z tym należy stosować następujące podejścia do optymalizowania wydajności podczas wyszukiwania za pomocą obiektu `JsonDocument`:

* Użyj wbudowanych modułów wyliczających (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> i <xref:System.Text.Json.JsonElement.EnumerateObject%2A>), zamiast tworzyć własne indeksowania lub pętle.
* Nie wykonuj wyszukiwania sekwencyjnego na całej `JsonDocument` za pośrednictwem każdej właściwości przy użyciu `RootElement`. Zamiast tego należy szukać obiektów zagnieżdżonych JSON w oparciu o znaną strukturę danych JSON. Na przykład jeśli szukasz właściwości `Grade` w obiektach `Student`, pętla przez `Student` obiektów i Pobierz wartość `Grade` dla każdego, zamiast przeszukiwać wszystkie `JsonElement` obiekty, szukając `Grade` właściwości. Wykonanie tych czynności spowoduje niepotrzebne przekazanie tych samych danych.

Aby uzyskać przykład kodu, zobacz [Korzystanie z JsonDocument w celu uzyskania dostępu do danych](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader w porównaniu do JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> jest wysoce wydajnym, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, Odczytaj z [ReadOnlySpan\<bajt >](xref:System.ReadOnlySpan%601) lub [ReadOnlySequence\<bajt >](xref:System.Buffers.ReadOnlySequence%601). `Utf8JsonReader` jest typem niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji.

W poniższych sekcjach opisano zalecane wzorce programowania do korzystania z `Utf8JsonReader`.

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader jest strukturą ref

Ponieważ typ `Utf8JsonReader` jest *strukturą ref*, ma [pewne ograniczenia](../../csharp/language-reference/keywords/ref.md#ref-struct-types). Na przykład nie można go zapisać jako pola w klasie lub strukturze innej niż struktura ref. Aby osiągnąć wysoką wydajność, ten typ musi być `ref struct`, ponieważ musi buforować wejściowe [ReadOnlySpan\<bajt >](xref:System.ReadOnlySpan%601), który sam jest strukturą ref. Ponadto ten typ jest modyfikowalny, ponieważ zawiera stan. W związku z tym **Przekaż go przez odwołanie** , a nie przez wartość. Przekazanie go przez wartość spowoduje skopiowanie struktury i zmiana stanu nie będzie widoczna dla obiektu wywołującego. Różni się to od `Newtonsoft.Json`, ponieważ `Newtonsoft.Json` `JsonTextReader` jest klasą. Aby uzyskać więcej informacji o sposobach korzystania z struktur ref, zobacz [Zapisywanie bezpiecznego i C# wydajnego kodu](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>Odczytaj tekst UTF-8

Aby osiągnąć najlepszą możliwą wydajność przy użyciu `Utf8JsonReader`, Odczytaj ładunki JSON już zakodowane jako tekst UTF-8, a nie jako ciągi UTF-16. Aby zapoznać się z przykładem kodu, zobacz [filtrowanie danych za pomocą Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Odczytaj przy użyciu strumienia lub PipeReader

`Utf8JsonReader` obsługuje odczytywanie z zakodowanego w formacie UTF-8 [ReadOnlySpan\<bajt >](xref:System.ReadOnlySpan%601) lub [ReadOnlySequence\<bajt >](xref:System.Buffers.ReadOnlySequence%601) (który jest wynikiem odczytu z <xref:System.IO.Pipelines.PipeReader>).

W przypadku odczytu synchronicznego można odczytać ładunek JSON do końca strumienia w tablicy bajtów i przekazać go do czytnika. Do odczytywania z ciągu (zakodowanego jako UTF-16) Wywołaj <xref:System.Text.Encoding.UTF8>.<xref:System.Text.Encoding.GetBytes%2A> Aby najpierw transkodowanie ciąg do tablicy bajtów zakodowanych w formacie UTF-8. Następnie Przekaż go do `Utf8JsonReader`. 

Ponieważ `Utf8JsonReader` traktuje dane wejściowe jako tekst JSON, znacznik kolejności bajtów UTF-8 jest uznawany za nieprawidłowy kod JSON. Obiekt wywołujący musi odfiltrować to wyjście przed przekazaniem danych do czytnika.

Aby zapoznać się z przykładami kodu, zobacz [use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Odczytaj z ReadOnlySequence wiele segmentów

Jeśli dane wejściowe JSON to [ReadOnlySpan\<bajt >](xref:System.ReadOnlySpan%601), do każdego elementu JSON można uzyskać dostęp z właściwości `ValueSpan` w czytniku podczas przechodzenia przez pętlę odczytu. Jeśli jednak dane wejściowe to [ReadOnlySequence\<bajty >](xref:System.Buffers.ReadOnlySequence%601) (który jest wynikiem odczytu z <xref:System.IO.Pipelines.PipeReader>), niektóre elementy JSON mogą obsłużyć wiele segmentów obiektu `ReadOnlySequence<byte>`. Te elementy byłyby niedostępne z <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> w ciągłym bloku pamięci. Zamiast tego, jeśli masz `ReadOnlySequence<byte>` jako dane wejściowe, sondowanie właściwości <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> w czytniku, aby ustalić, jak uzyskać dostęp do bieżącego elementu JSON. Oto zalecany wzorzec:

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>Użyj ValueTextEquals do wyszukiwania nazw właściwości

Nie używaj <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> do przeszukiwania bajtów po bajcie, wywołując <xref:System.MemoryExtensions.SequenceEqual%2A> do wyszukiwania nazw właściwości. Wywołaj <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> zamiast tego, ponieważ ta metoda nie ma żadnych znaków, które są wyprowadzane w formacie JSON. Oto przykład, który pokazuje, jak wyszukiwać właściwość o nazwie "name":

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Odczytywanie wartości null w typach wartości null

`Newtonsoft.Json` udostępnia interfejsy API, które zwracają <xref:System.Nullable%601>, takie jak `ReadAsBoolean`, które obsługują `Null` `TokenType` przez zwrócenie `bool?`. Wbudowane interfejsy API `System.Text.Json` zwracają tylko typy wartości niedopuszczające wartości null. Na przykład <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> zwraca `bool`. Zgłasza wyjątek, jeśli odnajdzie `Null` w formacie JSON. W poniższych przykładach pokazano dwa sposoby obsługi wartości null, jeden przez zwrócenie typu wartości null i jednego przez zwrócenie wartości domyślnej:

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>Wiele elementów docelowych

Jeśli musisz nadal używać `Newtonsoft.Json` dla pewnych platform docelowych, możesz wybrać wiele implementacji i mieć dwie implementacje. Nie jest to jednak proste i wymagało pewnego `#ifdefs` i duplikowania źródła. Jednym ze sposobów udostępniania możliwie największej ilości kodu jest utworzenie otoki `ref struct` wokół `Utf8JsonReader` i `Newtonsoft.Json` `JsonTextReader`. Ta otoka umożliwia ujednolicenie obszaru powierzchni publicznej podczas izolowania różnic behawioralnych. Dzięki temu można izolować zmiany w odniesieniu do konstrukcji typu wraz z przekazywaniem nowego typu dookoła przez odwołanie. Jest to wzorzec, [który jest następujący](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) :

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter w porównaniu do JsonTextWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> to wysoce wydajny sposób pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów platformy .NET, takich jak `String`, `Int32`i `DateTime`. Składnik zapisywania jest typu niskiego poziomu, który może służyć do tworzenia serializatorów niestandardowych.

W poniższych sekcjach opisano zalecane wzorce programowania do korzystania z `Utf8JsonWriter`.

### <a name="write-with-utf-8-text"></a>Napisz z tekstem UTF-8

Aby osiągnąć najlepszą możliwą wydajność przy użyciu `Utf8JsonWriter`, Zapisz ładunki JSON już zakodowane jako tekst UTF-8, a nie jako ciągi UTF-16. Użyj <xref:System.Text.Json.JsonEncodedText>, aby buforować i wstępnie kodować znane nazwy i wartości właściwości ciągów jako elementy statyczne i przekazać je do składnika zapisywania zamiast używać literałów ciągów w formacie UTF-16. Jest to szybsze niż buforowanie i korzysta z tablic bajtowych UTF-8.

Takie podejście działa również, jeśli trzeba wykonać niestandardowe ucieczki. `System.Text.Json` nie pozwala na wyłączenie ucieczki podczas pisania ciągu. Można jednak przekazać własne <xref:System.Text.Encodings.Web.JavaScriptEncoder> niestandardowe jako opcję składnika zapisywania lub utworzyć własne `JsonEncodedText`, które używają `JavascriptEncoder` do wykonywania ucieczki, a następnie napisać `JsonEncodedText` zamiast ciągu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodowania znaków](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Zapisz nieprzetworzone wartości

Metoda `Newtonsoft.Json` `WriteRawValue` zapisuje nieprzetworzony kod JSON, w którym oczekiwana jest wartość. <xref:System.Text.Json> nie ma bezpośredniego odpowiednika, ale jest to obejście, które gwarantuje, że jest zapisany tylko prawidłowy kod JSON:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Dostosowywanie ucieczki znaków

Ustawienie [StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) `JsonTextWriter` oferuje opcje ucieczki wszystkich znaków spoza zestawu ASCII **lub** znaków HTML. Domyślnie `Utf8JsonWriter` wyprowadza wszystkie znaki inne niż ASCII **i** html. To anulowanie jest wykonywane w celu zapewnienia bezpieczeństwa ze względu na ochronę. Aby określić inne zasady ucieczki, Utwórz <xref:System.Text.Encodings.Web.JavaScriptEncoder> i ustaw <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodowania znaków](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>Dostosuj format JSON

`JsonTextWriter` obejmuje następujące ustawienia, dla których `Utf8JsonWriter` nie ma odpowiednika:

* [Wcięcia](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) — określa liczbę znaków do wcięcia. `Utf8JsonWriter` zawsze wykonuje wcięcie z 2 znakami.
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) — określa znak do użycia w przypadku wcięcia.  `Utf8JsonWriter` zawsze używa białych znaków.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) — określa znak, który ma być używany do otaczania wartości ciągu.  `Utf8JsonWriter` zawsze używa podwójnych cudzysłowów.
* [Quote](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) -określa, czy należy ująć nazwy właściwości z cudzysłowami.  `Utf8JsonWriter` zawsze ujmuje je w cudzysłowy.

Nie istnieją obejścia, które pozwolą dostosować kod JSON utworzony przez `Utf8JsonWriter` w taki sposób.

### <a name="write-null-values"></a>Zapisz wartości null

Aby zapisać wartości null przy użyciu `Utf8JsonWriter`, wywołaj:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> zapisać pary klucz-wartość z wartością null jako wartością.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> zapisać wartości null jako elementu tablicy JSON.

Dla właściwości String, jeśli ciąg ma wartość null, <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> i <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> są równoważne `WriteNull` i `WriteNullValue`.

### <a name="write-timespan-uri-or-char-values"></a>Zapis wartości TimeSpan, URI lub char

`JsonTextWriter` zapewnia `WriteValue` metod dla wartości [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [URI](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)i [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) . `Utf8JsonWriter` nie ma równoważnych metod. Zamiast tego sformatuj te wartości jako ciągi (przez wywołanie `ToString()`, na przykład) i wywołań <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>.

### <a name="multi-targeting"></a>Wiele elementów docelowych

Jeśli musisz nadal używać `Newtonsoft.Json` dla pewnych platform docelowych, możesz wybrać wiele implementacji i mieć dwie implementacje. Nie jest to jednak proste i wymagało pewnego `#ifdefs` i duplikowania źródła. Jednym ze sposobów udostępniania możliwie największej ilości kodu jest utworzenie otoki wokół `Utf8JsonWriter` i `Newtonsoft` `JsonTextWriter`. Ta otoka umożliwia ujednolicenie obszaru powierzchni publicznej podczas izolowania różnic behawioralnych. Dzięki temu można izolować zmiany głównie do konstrukcji typu. Biblioteka [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) :

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Dodatkowe zasoby

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System. Text. JSON — Omówienie](system-text-json-overview.md)
* [Jak używać metody System. Text. JSON](system-text-json-how-to.md)
* [Jak pisać konwertery niestandardowe](system-text-json-converters-how-to.md)
* [Obsługa DateTime i DateTimeOffset w pliku System. Text. JSON](../datetime/system-text-json-support.md)
* [Dokumentacja interfejsu API System. Text. JSON](xref:System.Text.Json)
* [Dokumentacja interfejsu API System. Text. JSON. Serialization](xref:System.Text.Json.Serialization)
