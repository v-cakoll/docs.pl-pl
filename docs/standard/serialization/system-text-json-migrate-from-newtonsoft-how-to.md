---
title: Migrowanie Newtonsoft.Json System.Text.Json z do - .NET
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 0828a5654171df39230055215903d3a49690155d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739242"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Jak przeprowadzić migrację z Newtonsoft.Json do System.Text.Json

W tym artykule pokazano, jak przeprowadzić <xref:System.Text.Json>migrację z [pliku Newtonsoft.Json](https://www.newtonsoft.com/json) do .

Obszar `System.Text.Json` nazw udostępnia funkcje serializacji i deserializacji z notacji obiektu JavaScript (JSON). Biblioteka `System.Text.Json` jest uwzględniona w udostępnionej ramach [.NET Core 3.0.](https://aka.ms/netcore3download) W przypadku innych platform docelowych należy zainstalować pakiet [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet. Pakiet obsługuje:

* Wersje .NET Standard 2.0 i nowsze
* .NET Framework 4.7.2 i nowsze wersje
* .NET Core 2.0, 2.1 i 2.2

`System.Text.Json`koncentruje się przede wszystkim na wydajności, bezpieczeństwie i zgodności z normami. Ma kilka kluczowych różnic w zachowaniu domyślnym i nie `Newtonsoft.Json`ma na celu parytetu funkcji z . W niektórych `System.Text.Json` scenariuszach nie ma wbudowanych funkcji, ale istnieją zalecane obejścia. W przypadku innych scenariuszy obejścia są niepraktyczne. Jeśli aplikacja zależy od brakującej funkcji, należy rozważyć [zgłoszenie problemu,](https://github.com/dotnet/runtime/issues/new) aby dowiedzieć się, czy można dodać obsługę scenariusza.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

Większość tego artykułu dotyczy sposobu <xref:System.Text.Json.JsonSerializer> korzystania z interfejsu API, ale zawiera <xref:System.Text.Json.JsonDocument> również wskazówki dotyczące używania <xref:System.Text.Json.Utf8JsonReader>(który reprezentuje model obiektu dokumentu lub dom) i <xref:System.Text.Json.Utf8JsonWriter> typów.

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Tabela różnic między Newtonsoft.Json i System.Text.Json

W poniższej `Newtonsoft.Json` tabeli wymieniono operacje i `System.Text.Json` ich odpowiedniki. Odpowiedniki dzielą się na następujące kategorie:

* Obsługiwane przez wbudowane funkcje. Uzyskanie podobnego `System.Text.Json` zachowania może wymagać użycia atrybutu lub opcji globalnej.
* Nie jest obsługiwane, obejście jest możliwe. Obejścia są [niestandardowe konwertery,](system-text-json-converters-how-to.md)które mogą `Newtonsoft.Json` nie zapewnić pełną parzystość z funkcją. W przypadku niektórych z nich przykładowy kod jest podany jako przykłady. Jeśli korzystasz z `Newtonsoft.Json` tych funkcji, migracja będzie wymagać modyfikacji modeli obiektów platformy .NET lub innych zmian kodu.
* Nie jest obsługiwane, obejście nie jest praktyczne ani możliwe. Jeśli korzystasz z `Newtonsoft.Json` tych funkcji, migracja nie będzie możliwa bez istotnych zmian.

| Funkcja Newtonsoft.Json                               | System.Text.Json odpowiednik |
|-------------------------------------------------------|-----------------------------|
| Deserializacja bez uwzględniania wielkości liter domyślnie           | ✔️ [PropertyNameCaseInsensitive ustawienie globalne](#case-insensitive-deserialization) |
| Nazwy nieruchomości w przypadku wielbłąda                             | ✔️ [PropertyNamingPolicy ustawienie globalne](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| Minimaling postaci                            | ✔️ [Ścisła ucieczka postaci, konfigurowalna](#minimal-character-escaping) |
| `NullValueHandling.Ignore`ustawienie globalne             | ✔️ [IgnoreNullWuje opcję globalną](system-text-json-how-to.md#exclude-all-null-value-properties) |
| Zezwalaj na komentarze                                        | ✔️ [ReadCommentRowanie globalne](#comments) |
| Zezwalaj na końcowe przecinki                                 | ✔️ [Ustawienie globalne AllowTrailingCommas](#trailing-commas) |
| Rejestracja konwertera niestandardowego                         | ✔️ Kolejność [pierwszeństwa różni się](#converter-registration-precedence) |
| Brak domyślnej maksymalnej głębokości                           | ✔️ [Domyślna maksymalna głębokość 64, konfigurowalna](#maximum-depth) |
| Obsługa szerokiego zakresu typów                    | ⚠️[Niektóre typy wymagają konwerterów niestandardowych](#types-without-built-in-support) |
| Deserializacji ciągów jako liczb                        | ⚠️[Nie obsługiwane, obejście, przykład](#quoted-numbers) |
| Deserialize `Dictionary` z kluczem bez ciągu          | ⚠️[Nie obsługiwane, obejście, przykład](#dictionary-with-non-string-key) |
| Serializacja polimorficzna                             | ⚠️[Nie obsługiwane, obejście, przykład](#polymorphic-serialization) |
| Polimorficzna deserializacja                           | ⚠️[Nie obsługiwane, obejście, przykład](#polymorphic-deserialization) |
| Deserialize wywnioskować typ do `object` właściwości      | ⚠️[Nie obsługiwane, obejście, przykład](#deserialization-of-object-properties) |
| Deserialize JSON `null` literal do typów wartości nienastępalnych | ⚠️[Nie obsługiwane, obejście, przykład](#deserialize-null-to-non-nullable-type) |
| Deserialize do niezmiennych klas i struktur          | ⚠️[Nie obsługiwane, obejście, przykład](#deserialize-to-immutable-classes-and-structs) |
| Atrybut `[JsonConstructor]`                         | ⚠️[Nie obsługiwane, obejście, przykład](#specify-constructor-to-use) |
| `Required`ustawienie `[JsonProperty]` atrybutu        | ⚠️[Nie obsługiwane, obejście, przykład](#required-properties) |
| `NullValueHandling`ustawienie `[JsonProperty]` atrybutu | ⚠️[Nie obsługiwane, obejście, przykład](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`ustawienie `[JsonProperty]` atrybutu | ⚠️[Nie obsługiwane, obejście, przykład](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`ustawienie globalne                 | ⚠️[Nie obsługiwane, obejście, przykład](#conditionally-ignore-a-property) |
| `DefaultContractResolver`aby wykluczyć właściwości       | ⚠️[Nie obsługiwane, obejście, przykład](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` ustawienia   | ⚠️[Nie obsługiwane, obejście, przykład](#specify-date-format) |
| Wywołania zwrotne                                             | ⚠️[Nie obsługiwane, obejście, przykład](#callbacks) |
| Wsparcie dla pól publicznych i niepublicznych              | ⚠️[Nie obsługiwane, obejście](#public-and-non-public-fields) |
| Wsparcie dla wewnętrznych i prywatnych podmioty ustawiane i podmioty | ⚠️[Nie obsługiwane, obejście](#internal-and-private-property-setters-and-getters) |
| Metoda `JsonConvert.PopulateObject`                   | ⚠️[Nie obsługiwane, obejście](#populate-existing-objects) |
| `ObjectCreationHandling`ustawienie globalne               | ⚠️[Nie obsługiwane, obejście](#reuse-rather-than-replace-properties) |
| Dodawanie do kolekcji bez ustawianych                    | ⚠️[Nie obsługiwane, obejście](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`ustawienie globalne           | ❌[Nie obsługiwane](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`ustawienie globalne                | ❌[Nie obsługiwane](#preserve-object-references-and-handle-loops) |
| Obsługa `System.Runtime.Serialization` atrybutów | ❌[Nie obsługiwane](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`ustawienie globalne                | ❌[Nie obsługiwane](#missingmemberhandling) |
| Zezwalaj na nazwy właściwości bez cudzysłowów                   | ❌[Nie obsługiwane](#json-strings-property-names-and-string-values) |
| Zezwalaj na pojedyncze cudzysłowy wokół wartości ciągu              | ❌[Nie obsługiwane](#json-strings-property-names-and-string-values) |
| Zezwalaj na niestrumniczne wartości JSON dla właściwości ciągu    | ❌[Nie obsługiwane](#non-string-values-for-string-properties) |

Nie jest to wyczerpująca `Newtonsoft.Json` lista funkcji. Lista zawiera wiele scenariuszy, które zostały wymagane w [gitHub problemy](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) lub [stackoverflow](https://stackoverflow.com/questions/tagged/system.text.json) stanowisk. Jeśli zaimplementujesz obejście jednego ze scenariuszy wymienionych w tym miejscu, który obecnie nie ma przykładowego kodu, a jeśli chcesz udostępnić rozwiązanie, wybierz **tę stronę** w sekcji **Opinie** u dołu tej strony. To tworzy problem w tej dokumentacji GitHub repozytorium i wyświetla go w sekcji **Opinie** na tej stronie też.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Różnice w domyślnym zachowaniu JsonSerializer w porównaniu do Newtonsoft.Json

<xref:System.Text.Json>jest domyślnie ścisły i unika zgadywania lub interpretacji w imieniu osoby dzwoniącej, podkreślając deterministyczne zachowanie. Biblioteka została celowo zaprojektowana w ten sposób pod kątem wydajności i zabezpieczeń. `Newtonsoft.Json`jest elastyczna domyślnie. Ta podstawowa różnica w projekcie jest za wiele z następujących określonych różnic w zachowaniu domyślnym.

### <a name="case-insensitive-deserialization"></a>Deserializacja bez uwzględniania wielkości liter

Podczas deserializacji `Newtonsoft.Json` domyślnie jest zgodna nazwa właściwości bez uwzględniania wielkości liter. Wartość <xref:System.Text.Json> domyślna jest rozróżniana wielkość liter, co daje lepszą wydajność, ponieważ robi dokładne dopasowanie. Aby uzyskać informacje dotyczące dopasowywania bez uwzględniania wielkości liter, zobacz [Dopasowanie właściwości bez uwzględniania](system-text-json-how-to.md#case-insensitive-property-matching)wielkości liter .

Jeśli korzystasz `System.Text.Json` pośrednio za pomocą ASP.NET Core, nie musisz nic robić, aby `Newtonsoft.Json`uzyskać zachowanie, takie jak . ASP.NET Core określa ustawienia nazw [właściwości wielkości wielbłąda](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) i dopasowania bez uwzględniania `System.Text.Json`wielkości liter podczas używania .

### <a name="minimal-character-escaping"></a>Minimaling postaci

Podczas serializacji, `Newtonsoft.Json` jest stosunkowo permisywne o przepuszczanie znaków bez ucieczki ich. Oznacza to, że nie zastępuje `\uxxxx` `xxxx` ich, gdzie jest punkt kodu znaku. Tam, gdzie się im unika, robi `\` to, emitując `"` przed `\"`znakiem (na przykład staje się ). <xref:System.Text.Json>domyślnie uniknie większej liczby znaków, aby zapewnić ochronę przed skryptami krzyżowymi (XSS) lub atakami ujawniającymi informacje i robi to za pomocą sekwencji sześciu znaków. `System.Text.Json`domyślnie uniknie wszystkich znaków innych niż ASCII, więc nie musisz `StringEscapeHandling.EscapeNonAscii` nic `Newtonsoft.Json`robić, jeśli używasz w pliku . `System.Text.Json`domyślnie unika również znaków wrażliwych na kod HTML. Aby uzyskać informacje dotyczące zastępowania `System.Text.Json` zachowania domyślnego, zobacz [Dostosowywanie kodowania znaków](system-text-json-how-to.md#customize-character-encoding).

### <a name="comments"></a>Komentarze

Podczas deserializacji `Newtonsoft.Json` domyślnie ignoruje komentarze w JSON. Domyślnie <xref:System.Text.Json> jest zgłaszanie wyjątków dla komentarzy, ponieważ specyfikacja [RFC 8259](https://tools.ietf.org/html/rfc8259) nie zawiera ich. Aby uzyskać informacje o tym, jak zezwolić na komentarze, zobacz [Zezwalanie na komentarze i końcowe przecinki](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Końcowe przecinki

Podczas deserializacji `Newtonsoft.Json` domyślnie ignoruje końcowe przecinki. Ignoruje również wiele przecinków końcowych `[{"Color":"Red"},{"Color":"Green"},,]`(na przykład). Domyślnie <xref:System.Text.Json> jest zgłaszanie wyjątków dla końcowych przecinków, ponieważ specyfikacja [RFC 8259](https://tools.ietf.org/html/rfc8259) nie zezwala na nie. Aby uzyskać informacje `System.Text.Json` o tym, jak je zaakceptować, zobacz [Zezwalaj na komentarze i końcowe przecinki](system-text-json-how-to.md#allow-comments-and-trailing-commas). Nie ma sposobu, aby zezwolić na wiele końcowych przecinków.

### <a name="converter-registration-precedence"></a>Pierwszeństwo rejestracji konwertera

Pierwszeństwo `Newtonsoft.Json` rejestracji dla konwerterów niestandardowych jest następujące:

* Atrybut właściwości
* Atrybut typu
* [Kolekcja Konwerterów](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)

Ta kolejność oznacza, że konwerter niestandardowy w `Converters` kolekcji jest zastępowany przez konwerter, który jest zarejestrowany przez zastosowanie atrybutu na poziomie typu. Obie te rejestracje są zastępowane przez atrybut na poziomie właściwości.

Pierwszeństwo <xref:System.Text.Json> rejestracji dla konwerterów niestandardowych jest inny:

* Atrybut właściwości
* <xref:System.Text.Json.JsonSerializerOptions.Converters>Kolekcji
* Atrybut typu

Różnica polega na tym, że `Converters` konwerter niestandardowy w kolekcji zastępuje atrybut na poziomie typu. Intencją tej kolejności pierwszeństwa jest wprowadzenie zmian w czasie wykonywania zastąpić wybór czasu projektowania. Nie ma sposobu, aby zmienić pierwszeństwo.

Aby uzyskać więcej informacji na temat rejestracji konwertera [niestandardowego, zobacz Rejestrowanie konwertera niestandardowego](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="maximum-depth"></a>Maksymalna głębokość

`Newtonsoft.Json`domyślnie nie ma maksymalnego limitu głębokości. Dla <xref:System.Text.Json> istnieje domyślny limit 64, i to jest <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>konfigurowalne przez ustawienie .

### <a name="json-strings-property-names-and-string-values"></a>Ciągi JSON (nazwy właściwości i wartości ciągów)

Podczas deserializacji `Newtonsoft.Json` akceptuje nazwy właściwości otoczone cudzysłowami podwójnymi, pojedynczymi cudzysłowami lub bez cudzysłowów. Akceptuje wartości ciągu otoczone cudzysłowami lub pojedynczymi cudzysłowami. Na przykład `Newtonsoft.Json` akceptuje następujące JSON:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`akceptuje tylko nazwy właściwości i wartości ciągów w cudzysłowach, ponieważ ten format jest wymagany przez specyfikację [RFC 8259](https://tools.ietf.org/html/rfc8259) i jest jedynym formatem uważanym za prawidłowy JSON.

Wartość ujęta w pojedyncze cudzysłowy powoduje [JsonException](xref:System.Text.Json.JsonException) z następującym komunikatem:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Wartości niebędące ciągami dla właściwości ciągu

`Newtonsoft.Json`akceptuje wartości niebędące ciągami, takie jak liczba `true` `false`lub literały i , dla deserializacji do właściwości ciągu typu. Oto przykład JSON, który `Newtonsoft.Json` pomyślnie deserializes do następującej klasy:

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

`System.Text.Json`nie deserializacji wartości innych niż ciąg do właściwości ciągu. Wartość niebędąca ciągiem odebrana dla pola ciągu powoduje [powstanie JsonException](xref:System.Text.Json.JsonException) z następującym komunikatem:

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Scenariusze przy użyciu JsonSerializer, które wymagają obejścia

Następujące scenariusze nie są obsługiwane przez wbudowane funkcje, ale obejścia są możliwe. Obejścia są [niestandardowe konwertery,](system-text-json-converters-how-to.md)które mogą `Newtonsoft.Json` nie zapewnić pełną parzystość z funkcją. W przypadku niektórych z nich przykładowy kod jest podany jako przykłady. Jeśli korzystasz z `Newtonsoft.Json` tych funkcji, migracja będzie wymagać modyfikacji modeli obiektów platformy .NET lub innych zmian kodu.

### <a name="types-without-built-in-support"></a>Typy bez wbudowanej obsługi

<xref:System.Text.Json>nie zapewnia wbudowanej obsługi dla następujących typów:

* <xref:System.Data.DataTable>i powiązane typy
* Typy F#, takie jak [dyskryminowane związki,](../../fsharp/language-reference/discriminated-unions.md) [typy rekordów](../../fsharp/language-reference/records.md)i [typy rekordów anonimowych.](../../fsharp/language-reference/anonymous-records.md)
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>i powiązane z nimi typy rodzajowe

Konwertery niestandardowe mogą być implementowane dla typów, które nie mają wbudowanej obsługi.

### <a name="quoted-numbers"></a>Liczby podane w cycie

`Newtonsoft.Json`można serializować lub deserialize numery reprezentowane przez ciągi JSON (otoczony cudzysłowami). Na przykład może zaakceptować: `{"DegreesCelsius":"23"}` `{"DegreesCelsius":23}`zamiast . Aby włączyć to <xref:System.Text.Json>zachowanie w programie , należy zaimplementować konwertera niestandardowego, jak w poniższym przykładzie. Konwerter obsługuje właściwości zdefiniowane jako: `long`

* Serializuje je jako ciągi JSON.
* Akceptuje liczby JSON i liczby w cudzysłowie podczas deserializacji.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Zarejestruj ten konwerter niestandardowy przy `long` użyciu [atrybutu](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) dla poszczególnych <xref:System.Text.Json.JsonSerializerOptions.Converters> właściwości lub przez dodanie [konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekcji.

### <a name="dictionary-with-non-string-key"></a>Słownik z kluczem bez ciągu

`Newtonsoft.Json`obsługuje kolekcje `Dictionary<TKey, TValue>`typu . Wbudowana obsługa kolekcji słowników <xref:System.Text.Json> jest ograniczona `Dictionary<string, TValue>`do . Oznacza to, że klucz musi być ciągiem.

Aby obsługiwać słownik z liczeniem lub innym typem jako kluczem, utwórz konwerter, taki jak przykład w [jak pisać konwertery niestandardowe](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).

### <a name="polymorphic-serialization"></a>Serializacja polimorficzna

`Newtonsoft.Json`automatycznie wykonuje serializację polimorficzną. Aby uzyskać informacje na temat ograniczonych możliwości <xref:System.Text.Json>serializacji polimorficznej , zobacz [Serialize właściwości klas pochodnych](system-text-json-how-to.md#serialize-properties-of-derived-classes).

Opisane obejście ma na celu zdefiniowanie właściwości, które mogą `object`zawierać klasy pochodne jako typ . Jeśli nie jest to możliwe, inną opcją jest `Write` utworzenie konwertera z metodą dla całej hierarchii typów dziedziczenia, jak w przykładzie [Jak napisać konwertery niestandardowe](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="polymorphic-deserialization"></a>Polimorficzna deserializacja

`Newtonsoft.Json`ma `TypeNameHandling` ustawienie, które dodaje metadane nazwy typu do JSON podczas serializacji. Używa metadanych podczas deserializacji do wielomorficznej deserializacji. <xref:System.Text.Json>może wykonywać ograniczony zakres [serializacji polimorficznej,](system-text-json-how-to.md#serialize-properties-of-derived-classes) ale nie polimorficznej deserializacji.

Aby obsługiwać polimorficzną deserializację, utwórz konwerter, taki jak przykład w [jak pisać konwertery niestandardowe](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="deserialization-of-object-properties"></a>Deserializacja właściwości obiektu

Gdy `Newtonsoft.Json` deserializes <xref:System.Object>do , to:

* Wywnioskować typ wartości pierwotnych w ładunku `null`JSON (inne `string` `long`niż `double` `boolean`) `DateTime` i zwraca przechowywane , , , lub jako obiekt w pudełku. *Wartości pierwotne* to pojedyncze wartości JSON, takie `true`jak `false`liczba `null`JSON, ciąg, , lub .
* Zwraca `JObject` wartości `JArray` złożone lub dla złożonych w ładunku JSON. *Złożone wartości* to kolekcje par klucz-wartość JSON`{}`w nawiasach klamrowych`[]`( ) lub listy wartości w nawiasach ( ). Właściwości i wartości w nawiasach klamrowych lub nawiasów mogą mieć dodatkowe właściwości lub wartości.
* Zwraca odwołanie null, gdy ładunek ma literał `null` JSON.

<xref:System.Text.Json>przechowuje w `JsonElement` pudełku zarówno wartości pierwotne, jak <xref:System.Object>i złożone, gdy deserializing do , na przykład:

* Właściwość. `object`
* Wartość `object` słownika.
* Wartość `object` tablicy.
* Korzeń `object`.

Jednak `System.Text.Json` traktuje `null` tak samo `Newtonsoft.Json` jak i zwraca odwołanie null, `null` gdy ładunek ma literał JSON w nim.

Aby zaimplementować wnioskowanie o typie dla `object` właściwości, należy utworzyć konwerter, taki jak przykład w jak napisać [konwertery niestandardowe](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).

### <a name="deserialize-null-to-non-nullable-type"></a>Deserialize typu null do nienastępu

`Newtonsoft.Json`nie zgłasza wyjątek w następującym scenariuszu:

* `NullValueHandling`jest ustawiona na `Ignore`, i
* Podczas deserializacji JSON zawiera wartość null dla typu wartości nienastępulnej.

W tym samym <xref:System.Text.Json> scenariuszu zgłasza wyjątek. (Odpowiednie ustawienie obsługi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>null to .)

Jeśli jesteś właścicielem typu docelowego, najlepszym rozwiązaniem jest uczynienie danej właściwości nieważnośćą (na przykład zmień `int` na `int?`).

Innym rozwiązaniem jest, aby konwerter dla typu, takich jak poniższy `DateTimeOffset` przykład, który obsługuje wartości null dla typów:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Zarejestruj ten konwerter niestandardowy [przy użyciu atrybutu we właściwości](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) lub przez dodanie [konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> do kolekcji.

**Uwaga:** Poprzedni konwerter **obsługuje wartości null** `Newtonsoft.Json` inaczej niż w przypadku POCO, które określają wartości domyślne. Załóżmy na przykład, że następujący kod reprezentuje obiekt docelowy:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

I załóżmy, że następujące JSON jest deserialized przy użyciu poprzedniego konwertera:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Po deserializacji `Date` właściwość ma 1/1/0001 (`default(DateTimeOffset)`), oznacza to, że wartość ustawiona w konstruktorze jest zastępowany. Biorąc pod uwagę te same `Newtonsoft.Json` POCO i JSON, deserializacji pozostawi 1/1/2001 w `Date` nieruchomości.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Deserialize do niezmiennych klas i struktur

`Newtonsoft.Json`można deserialize do niezmienne klasy i struktury, ponieważ można użyć konstruktorów, które mają parametry. <xref:System.Text.Json>obsługuje tylko publiczne konstruktory bez parametrów. Jako obejście można wywołać konstruktora z parametrami w konwerterze niestandardowym.

Oto niezmienna struktura z wieloma parametrami konstruktora:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

A oto konwerter, który serializuje i deserializuje tę strukturę:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Zarejestruj ten niestandardowy konwerter, <xref:System.Text.Json.JsonSerializerOptions.Converters> [dodając konwerter](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekcji.

Na przykład podobny konwerter obsługujący otwarte właściwości ogólne można znaleźć [w wbudowanym konwerterze par klucz-wartość](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Określ konstruktora do użycia

Atrybut `Newtonsoft.Json` `[JsonConstructor]` umożliwia określenie, który konstruktor do wywołania podczas deserializacji do POCO. <xref:System.Text.Json>obsługuje tylko konstruktory bez parametrów. Aby obejść ten problem, można wywołać konstruktora, który jest potrzebny w konwerterze niestandardowym. Zobacz przykład [Deserialize do niezmiennych klas i struktur](#deserialize-to-immutable-classes-and-structs).

### <a name="required-properties"></a>Wymagane właściwości

W `Newtonsoft.Json`programie należy określić, że `Required` właściwość `[JsonProperty]` jest wymagana przez ustawienie atrybutu. `Newtonsoft.Json`zgłasza wyjątek, jeśli nie zostanie odebrana żadna wartość w JSON dla właściwości oznaczonej jako wymagana.

<xref:System.Text.Json>nie zgłasza wyjątek, jeśli nie zostanie odebrana żadna wartość dla jednej z właściwości typu docelowego. Na przykład, jeśli `WeatherForecast` masz klasę:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Następujący JSON jest deserializowane bez błędu:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

Aby deserializacji zakończyć `Date` się niepowodzeniem, jeśli żadna właściwość nie znajduje się w JSON, zaimplementuj konwerter niestandardowy. Następujący przykładowy kod konwertera `Date` zgłasza wyjątek, jeśli właściwość nie jest ustawiona po zakończeniu deserializacji:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

Zarejestruj ten konwerter niestandardowy [przy użyciu atrybutu w klasie POCO](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) lub przez [dodanie konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> do kolekcji.

Jeśli zastosujesz się do tego wzorca, nie należy przechodzić w obiekcie opcji podczas cyklicznego wywoływania <xref:System.Text.Json.JsonSerializer.Serialize%2A> lub <xref:System.Text.Json.JsonSerializer.Deserialize%2A>. Obiekt options zawiera <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> kolekcję. Jeśli przekażesz `Serialize` go `Deserialize`do lub , konwerter niestandardowy wywołuje do siebie, co nieskończona pętla, która powoduje wyjątek przepełnienia stosu. Jeśli opcje domyślne nie są możliwe, utwórz nowe wystąpienie opcji z potrzebnymi ustawieniami. Takie podejście będzie powolne, ponieważ każde nowe wystąpienie buforuje się niezależnie.

Poprzedni kod konwertera jest przykładem uproszczonym. Dodatkowa logika będzie wymagana, jeśli trzeba obsługiwać atrybuty (takie jak [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) lub różnych opcji (takich jak niestandardowe kodery). Ponadto przykładowy kod nie obsługuje właściwości, dla których wartość domyślna jest ustawiona w konstruktorze. I to podejście nie rozróżnia następujących scenariuszy:

* Brakuje właściwości z JSON.
* Właściwość dla typu nienastępnego do wartości null jest obecna w JSON, ale wartość `int`jest wartością domyślną dla typu, taką jak zero dla .
* Właściwość dla typu wartości możliwej do wartości null jest obecna w JSON, ale wartość jest null.

### <a name="conditionally-ignore-a-property"></a>Warunkowe zignorowanie właściwości

`Newtonsoft.Json`ma kilka sposobów warunkowego zignorowania właściwości podczas serializacji lub deserializacji:

* `DefaultContractResolver`umożliwia wybranie właściwości do uwzględnienia lub wykluczenia na podstawie dowolnych kryteriów.
* Ustawienia `NullValueHandling` `DefaultValueHandling` i `JsonSerializerSettings` ustawienia na pozwalają określić, że wszystkie właściwości wartości null lub wartości domyślnej powinny być ignorowane.
* Ustawienia `NullValueHandling` `DefaultValueHandling` i ustawienia `[JsonProperty]` atrybutu umożliwiają określenie poszczególnych właściwości, które powinny być ignorowane po ustawieniu wartości null lub wartości domyślnej.

<xref:System.Text.Json>zapewnia następujące sposoby pominięcia właściwości podczas serializacji:

* [Atrybut [JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) we właściwości powoduje, że właściwość ma zostać pominięta z JSON podczas serializacji.
* [Opcja ignoruj.ullValues](system-text-json-how-to.md#exclude-all-null-value-properties) umożliwia wykluczenie wszystkich właściwości o wartości null.
* Opcja globalna [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) umożliwia wykluczenie wszystkich właściwości tylko do odczytu.

Te opcje **nie** pozwalają:

* Zignoruj wszystkie właściwości, które mają wartość domyślną dla tego typu.
* Ignoruj wybrane właściwości, które mają wartość domyślną dla tego typu.
* Ignoruj wybrane właściwości, jeśli ich wartość jest zerowa.
* Ignoruj wybrane właściwości na podstawie dowolnych kryteriów ocenianych w czasie wykonywania.

Dla tej funkcji można napisać konwerter niestandardowy. Oto przykładowy POCO i konwerter niestandardowy dla niego, który ilustruje to podejście:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Konwerter powoduje, że `Summary` właściwość ma zostać pominięta w serializacji, jeśli jej wartość jest null, pusty ciąg lub "N/A".

Zarejestruj ten konwerter niestandardowy [przy użyciu atrybutu w klasie](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) lub przez dodanie [konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> do kolekcji.

Takie podejście wymaga dodatkowej logiki, jeśli:

* Poco zawiera właściwości złożone.
* Należy obsługiwać atrybuty, takie jak `[JsonIgnore]` lub opcje, takie jak kodery niestandardowe.

### <a name="specify-date-format"></a>Określ format daty

`Newtonsoft.Json`zawiera kilka sposobów kontrolowania, `DateTime` jak `DateTimeOffset` właściwości i typy są serializowane i deserializowane:

* Ustawienie `DateTimeZoneHandling` może służyć do serializacji wszystkich `DateTime` wartości jako dat UTC.
* Ustawienia `DateFormatString` i `DateTime` konwertery mogą służyć do dostosowywania formatu ciągów daty.

W <xref:System.Text.Json>, jedynym formacie, który ma wbudowaną obsługę jest ISO 8601-1:2019, ponieważ jest powszechnie przyjęty, jednoznaczny i dokładnie wykonuje podróże w obie strony. Aby użyć dowolnego innego formatu, utwórz konwerter niestandardowy. Aby uzyskać więcej informacji, zobacz [DateTime i DateTimeOffset pomocy technicznej w System.Text.Json](../datetime/system-text-json-support.md).

### <a name="callbacks"></a>Wywołania zwrotne

`Newtonsoft.Json`umożliwia wykonanie kodu niestandardowego w kilku punktach procesu serializacji lub deserializacji:

* OnDeserializing (gdy zaczyna się deserializacji obiektu)
* OnDeserialized (po zakończeniu deserializacji obiektu)
* OnSerializing (gdy zaczyna się serializować obiekt)
* OnSerialized (po zakończeniu serializacji obiektu)

W <xref:System.Text.Json>, można symulować wywołania zwrotne, pisząc konwerter niestandardowy. W poniższym przykładzie przedstawiono konwerter niestandardowy dla poco. Konwerter zawiera kod, który wyświetla komunikat w `Newtonsoft.Json` każdym punkcie, który odpowiada wywołaniu zwrotnym.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Zarejestruj ten konwerter niestandardowy [przy użyciu atrybutu w klasie](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) lub przez dodanie [konwertera](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> do kolekcji.

Jeśli używasz konwertera niestandardowego, który następuje po poprzedniej próbce:

* Kod `OnDeserializing` nie ma dostępu do nowego wystąpienia POCO. Aby manipulować nowym wystąpieniem POCO na początku deserializacji, umieść ten kod w konstruktorze POCO.
* Nie przekazuj w obiekcie opcji podczas `Serialize` cyklicznego wywoływania lub `Deserialize`. Obiekt options zawiera `Converters` kolekcję. Jeśli przekażesz `Serialize` go `Deserialize`do lub , konwerter będzie używany, co nieskończona pętla, która powoduje wyjątek przepełnienia stosu.

### <a name="public-and-non-public-fields"></a>Pola publiczne i niepubliczne

`Newtonsoft.Json`można serializować i deserializacji pól, jak również właściwości. <xref:System.Text.Json>działa tylko z właściwościami publicznymi. Konwertery niestandardowe mogą zapewnić tę funkcję.

### <a name="internal-and-private-property-setters-and-getters"></a>Podmioty ustalane i podmioty ustalane przez podmioty ustalane we wewnętrznego i prywatnego

`Newtonsoft.Json`można użyć prywatnych i wewnętrznych ustawiaczów `JsonProperty` właściwości i getters za pośrednictwem atrybutu. <xref:System.Text.Json>obsługuje tylko ustawiaczów publicznych. Konwertery niestandardowe mogą zapewnić tę funkcję.

### <a name="populate-existing-objects"></a>Wypełnianie istniejących obiektów

Metoda `JsonConvert.PopulateObject` w `Newtonsoft.Json` deserializes dokumentu JSON do istniejącego wystąpienia klasy, zamiast tworzenia nowego wystąpienia. <xref:System.Text.Json>zawsze tworzy nowe wystąpienie typu docelowego przy użyciu domyślnego konstruktora bez parametrów publicznych. Konwertery niestandardowe można deserializacji do istniejącego wystąpienia.

### <a name="reuse-rather-than-replace-properties"></a>Ponowne użycie zamiast zastępowania właściwości

Ustawienie `Newtonsoft.Json` `ObjectCreationHandling` pozwala określić, że obiekty we właściwościach powinny być ponownie używane, a nie zastępowane podczas deserializacji. <xref:System.Text.Json>zawsze zastępuje obiekty we właściwościach.  Konwertery niestandardowe mogą zapewnić tę funkcję.

### <a name="add-to-collections-without-setters"></a>Dodawanie do kolekcji bez ustawianych

Podczas deserializacji `Newtonsoft.Json` dodaje obiekty do kolekcji, nawet jeśli właściwość nie ma setter. <xref:System.Text.Json>ignoruje właściwości, które nie mają ustawiaczów. Konwertery niestandardowe mogą zapewnić tę funkcję.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Scenariusze, których obecnie nie obsługuje firma JsonSerializer

W następujących scenariuszach obejścia nie są praktyczne ani możliwe. Jeśli korzystasz z `Newtonsoft.Json` tych funkcji, migracja nie będzie możliwa bez istotnych zmian.

### <a name="preserve-object-references-and-handle-loops"></a>Zachowywanie odwołań do obiektów i pętli uchwytów

Domyślnie `Newtonsoft.Json` serializuje według wartości. Na przykład jeśli obiekt zawiera dwie właściwości, które `Person` zawierają odwołanie do `Person` tego samego obiektu, wartości właściwości tego obiektu są duplikowane w JSON.

`Newtonsoft.Json`ma `PreserveReferencesHandling` ustawienie, `JsonSerializerSettings` które pozwala serializować przez odwołanie:

* Metadane identyfikatora są dodawane do JSON utworzone dla pierwszego `Person` obiektu.
* JSON, który jest tworzony `Person` dla drugiego obiektu zawiera odwołanie do tego identyfikatora zamiast wartości właściwości.

`Newtonsoft.Json`również ma `ReferenceLoopHandling` ustawienie, które pozwala ignorować odwołania cykliczne, a nie zgłaszać wyjątek.

<xref:System.Text.Json>obsługuje tylko serializacji według wartości i zgłasza wyjątek dla odwołań cyklicznych.

### <a name="systemruntimeserialization-attributes"></a>Atrybuty system.Runtime.Serialization

<xref:System.Text.Json>nie obsługuje atrybutów `System.Runtime.Serialization` z obszaru nazw, takich jak `DataMemberAttribute` i `IgnoreDataMemberAttribute`.

### <a name="octal-numbers"></a>Liczby ósemki

`Newtonsoft.Json`traktuje liczby z zerem wiodącym jako liczby ósemki. <xref:System.Text.Json>nie zezwala na zer wiodących, ponieważ specyfikacja [RFC 8259](https://tools.ietf.org/html/rfc8259) nie zezwala na nie.

### <a name="missingmemberhandling"></a>BrakeczłonekHandling

`Newtonsoft.Json`można skonfigurować do zgłaszania wyjątków podczas deserializacji, jeśli JSON zawiera właściwości, których brakuje w typie docelowym. <xref:System.Text.Json>ignoruje dodatkowe właściwości w JSON, z wyjątkiem sytuacji, gdy używasz [atrybutu [JsonExtensionData].](system-text-json-how-to.md#handle-overflow-json) Nie ma obejścia funkcji brakującego elementu członkowskiego.

### <a name="tracewriter"></a>TraceWriter (TraceWriter)

`Newtonsoft.Json`umożliwia debugowanie przy `TraceWriter` użyciu do wyświetlania dzienników, które są generowane przez serializacji lub deserializacji. <xref:System.Text.Json>nie robi rejestrowania.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument i JsonElement w porównaniu do JToken (jak JObject, JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>zapewnia możliwość analizowania i tworzenia modelu obiektowego dokumentu tylko do **odczytu** (DOM) z istniejących ładunków JSON. Dom zapewnia losowy dostęp do danych w ładunku JSON. Elementy JSON, które tworzą ładunek można uzyskać <xref:System.Text.Json.JsonElement> za pośrednictwem typu. Ten `JsonElement` typ udostępnia interfejsy API do konwertowania tekstu JSON na typowe typy .NET. `JsonDocument`udostępnia <xref:System.Text.Json.JsonDocument.RootElement> właściwość.

### <a name="jsondocument-is-idisposable"></a>JsonDocument jest IDisposable

`JsonDocument`tworzy widok w pamięci danych do buforu puli. W związku `JObject` z `JArray` `Newtonsoft.Json`tym, `JsonDocument` w `IDisposable` przeciwieństwie do lub z , typ implementuje i musi być używany wewnątrz using bloku.

Tylko zwrócić `JsonDocument` z interfejsu API, jeśli chcesz przenieść własność życia i zbywać odpowiedzialność do obiektu wywołującego. W większości scenariuszy nie jest to konieczne. Jeśli wywołujący musi pracować z całym dokumentem <xref:System.Text.Json.JsonElement.Clone%2A> JSON, zwróć program <xref:System.Text.Json.JsonDocument.RootElement%2A>, który jest <xref:System.Text.Json.JsonElement>. Jeśli wywołujący musi pracować z określonym elementem w dokumencie <xref:System.Text.Json.JsonElement>JSON, zwróć ten <xref:System.Text.Json.JsonElement.Clone%2A> element . Jeśli zwrócisz `RootElement` lub podelement bezpośrednio bez `Clone`dokonywania , obiekt wywołujący nie `JsonElement` będzie `JsonDocument` mógł uzyskać dostępu do zwróconego po tym, jak jest on właścicielem.

Oto przykład, który wymaga: `Clone`

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

Poprzedni kod oczekuje, `JsonElement` że zawiera `fileName` właściwość. Otwiera plik JSON i `JsonDocument`tworzy plik . Metoda zakłada, że wywołujący chce pracować z całym dokumentem, `Clone` więc `RootElement`zwraca .

Jeśli otrzymasz `JsonElement` i zwracasz podelement, nie jest konieczne `Clone` zwracanie elementu podrzędnego. Wywołujący jest odpowiedzialny za `JsonDocument` utrzymanie przy życiu, że przekazywane w `JsonElement` należy do. Przykład:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument jest tylko do odczytu

Dom <xref:System.Text.Json> nie można dodać, usunąć lub zmodyfikować elementów JSON. Został zaprojektowany w ten sposób pod kątem wydajności i zmniejszenia alokacji do analizowania typowych rozmiarów ładunku JSON (czyli < 1 MB). Jeśli scenariusz używa obecnie modyfikowalnej witryny DOM, możliwe jest zastosowanie jednego z następujących rozwiązań:

* Aby `JsonDocument` zbudować od podstaw (to znaczy, bez przekazywania `Parse` w istniejącej ładowności `Utf8JsonWriter` JSON do metody), należy napisać `JsonDocument`tekst JSON za pomocą i przeanalizować dane wyjściowe z tego, aby utworzyć nowy .
* Aby zmodyfikować `JsonDocument`istniejący program , należy go używać do pisania tekstu JSON, wprowadzania `JsonDocument`zmian podczas pisania i analizowanie danych wyjściowych z tego, aby wprowadzić nowy plik .
* Aby scalić istniejące dokumenty `JObject.Merge` JSON, równoważne interfejsom API lub `JContainer.Merge` interfejsom API z `Newtonsoft.Json`, zobacz ten problem z [githubem](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).

### <a name="jsonelement-is-a-union-struct"></a>JsonElement jest strukturą unii

`JsonDocument`udostępnia `RootElement` jako właściwość typu <xref:System.Text.Json.JsonElement>, który jest union, struct typu, który obejmuje dowolny element JSON. `Newtonsoft.Json`używa dedykowanych typów `JObject`hierarchicznych, takich jak ,`JArray` `JToken`, i tak dalej. `JsonElement`jest to, co można wyszukiwać i wyliczać nad i można użyć `JsonElement` do materializacji JSON elementów w .NET typów.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Jak wyszukiwać JsonDocument i JsonElement pod elementami

Wyszukiwanie tokenów JSON `JObject` `JArray` przy `Newtonsoft.Json` użyciu lub z wydają się być stosunkowo szybkie, ponieważ są one wyszukiwania w niektórych słowników. Dla porównania, `JsonElement` wyszukiwanie na wymagają sekwencyjnego wyszukiwania właściwości, a zatem `TryGetProperty`jest stosunkowo powolny (na przykład podczas korzystania ). <xref:System.Text.Json>ma na celu zminimalizowanie początkowego czasu analizy, a nie czasu odnośnika. W związku z tym należy użyć następujących metod, `JsonDocument` aby zoptymalizować wydajność podczas przeszukiwania obiektu:

* Użyj wbudowanych wyliczników (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> <xref:System.Text.Json.JsonElement.EnumerateObject%2A>i ) zamiast robić własne indeksowanie lub pętle.
* Nie rób sekwencyjnego wyszukiwania `JsonDocument` w całości za `RootElement`pomocą każdej usługi za pomocą . Zamiast tego wyszukaj zagnieżdżone obiekty JSON na podstawie znanej struktury danych JSON. Na przykład jeśli szukasz `Grade` właściwości w `Student` obiektach, pętli `Student` przez obiekty i `Grade` uzyskać wartość dla każdego, zamiast przeszukiwania wszystkich `JsonElement` obiektów w poszukiwaniu `Grade` właściwości. Wykonanie tego ostatniego spowoduje niepotrzebne przekazywanie tych samych danych.

Przykładowy kod można znaleźć w programie [JsonDocument w celu uzyskania dostępu do danych](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader w porównaniu do JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>jest wysokowydajnym, niskowydyskowym czytnikiem tylko do przodu dla zakodowanego tekstu JSON UTF-8, odczytanym z [bajtu ReadOnlySpan\<>](xref:System.ReadOnlySpan%601) lub [bajtem ReadOnlySequence\<>](xref:System.Buffers.ReadOnlySequence%601). Jest `Utf8JsonReader` typu niskiego poziomu, który może służyć do tworzenia analizatorów niestandardowych i deserializatorów.

W poniższych sekcjach wyjaśniono `Utf8JsonReader`zalecane wzorce programowania do korzystania .

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader jest ref struct

Ponieważ `Utf8JsonReader` typ jest *ref struct,* ma [pewne ograniczenia](../../csharp/language-reference/builtin-types/struct.md#ref-struct). Na przykład nie można go przechowywać jako pola w klasie lub struktury innych niż struktury ref. Aby osiągnąć wysoką wydajność, `ref struct` ten typ musi być, ponieważ musi buforować wejście [ReadOnlySpan\<bajt>](xref:System.ReadOnlySpan%601), który sam jest ref struct. Ponadto ten typ jest modyfikowalna, ponieważ posiada stan. W związku z tym **przekazać go przez ref,** a nie przez wartość. Przekazywanie go przez wartość spowodowałoby kopię struktury i zmiany stanu nie będą widoczne dla wywołującego. To różni `Newtonsoft.Json` się `Newtonsoft.Json` `JsonTextReader` od tego, że jest klasą. Aby uzyskać więcej informacji na temat korzystania z struktury ref, zobacz [Pisanie bezpiecznego i wydajnego kodu C#.](../../csharp/write-safe-efficient-code.md)

### <a name="read-utf-8-text"></a>Przeczytaj tekst UTF-8

Aby osiągnąć najlepszą możliwą wydajność podczas korzystania z `Utf8JsonReader`, odczytaj ładunki JSON już zakodowane jako tekst UTF-8, a nie jako ciągi UTF-16. Przykładowy kod można znaleźć [w filtrowaniu danych przy użyciu czytnika Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Odczyt za pomocą strumienia lub pipereadera

Obsługuje `Utf8JsonReader` odczyt z utf-8 zakodowany [bajt\<ReadOnlySpan>](xref:System.ReadOnlySpan%601) lub [ReadOnlySequence\<bajt>](xref:System.Buffers.ReadOnlySequence%601) (co jest wynikiem odczytu z ). <xref:System.IO.Pipelines.PipeReader>

W celu odczytu synchronicznego można odczytać ładunek JSON do końca strumienia do tablicy bajtów i przekazać go do czytnika. Do odczytu z ciągu (który jest zakodowany jako <xref:System.Text.Encoding.UTF8>UTF-16), wywołanie .<xref:System.Text.Encoding.GetBytes%2A> , aby najpierw przekodować ciąg do tablicy bajtów zakodowanych w u. UTF-8. Następnie przekazać, `Utf8JsonReader`że do .

Ponieważ `Utf8JsonReader` dane wejściowe są tekstem JSON, znacznik kolejności bajtów UTF-8 (BOM) jest uważany za nieprawidłowy JSON. Wywołujący musi odfiltrować, zanim przekazuje dane do czytnika.

Przykłady kodu można znaleźć [w uwerna Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Czytaj z wielosegmentową readonlySequence

Jeśli wejście JSON jest [>bajt\<ReadOnlySpan, ](xref:System.ReadOnlySpan%601)każdy element JSON można uzyskać z `ValueSpan` właściwości na czytniku podczas przechodzenia przez pętlę odczytu. Jeśli jednak dane wejściowe są [>bajtów\<ReadOnlySequence](xref:System.Buffers.ReadOnlySequence%601) (co jest wynikiem odczytu z a), <xref:System.IO.Pipelines.PipeReader>niektóre `ReadOnlySequence<byte>` elementy JSON mogą oddzielać wiele segmentów obiektu. Te elementy nie będą <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> dostępne z w ciągłym bloku pamięci. Zamiast tego, gdy masz wielosegment `ReadOnlySequence<byte>` jako <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> dane wejściowe, sonduj właściwość na czytniku, aby dowiedzieć się, jak uzyskać dostęp do bieżącego elementu JSON. Oto zalecany wzór:

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

### <a name="use-valuetextequals-for-property-name-lookups"></a>Używanie wartości ValueTextEquals dla odnośów nazw właściwości

Nie używaj <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> do porównywania bajtów po bajcie, wywołując <xref:System.MemoryExtensions.SequenceEqual%2A> wyszukiwania nazw właściwości. Zamiast <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> tego wywołaj, ponieważ ta metoda odchudza wszystkie znaki, które są zmienione w JSON. Oto przykład, który pokazuje, jak wyszukać właściwość o nazwie "name":

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Odczyt wartości null do typów wartości nullable

`Newtonsoft.Json`zapewnia interfejsy API, <xref:System.Nullable%601>które `ReadAsBoolean`zwracają , `Null` `TokenType` takie jak , `bool?`który obsługuje dla Ciebie, zwracając . Wbudowane `System.Text.Json` interfejsy API zwracają tylko typy wartości nienastępne wartości null. Na przykład <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> zwraca `bool`plik . Zgłasza wyjątek, jeśli `Null` znajdzie w JSON. Poniższe przykłady pokazują dwa sposoby obsługi wartości null, jeden przez zwrócenie typu wartości nullable i jeden przez zwrócenie wartości domyślnej:

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

### <a name="multi-targeting"></a>Kierowanie wielokrotne

Jeśli musisz nadal używać `Newtonsoft.Json` dla niektórych struktur docelowych, można multi-target i mieć dwie implementacje. Jednak nie jest to trywialne i wymagałoby pewnego `#ifdefs` powielania źródeł. Jednym ze sposobów udostępniania jak najwięcej kodu, jak `Utf8JsonReader` `Newtonsoft.Json` `JsonTextReader`to możliwe jest utworzenie `ref struct` otoki wokół i . Ta otoka ujednoliciłaby powierzchnię publiczną, jednocześnie izolując różnice behawioralne. Dzięki temu można wyizolować zmiany głównie do konstrukcji typu, wraz z przekazywania nowego typu wokół przez odniesienie. Jest to wzorzec, który [microsoft.extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) biblioteki następujące:

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter w porównaniu do JsonTextWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>jest wysokowydajnym sposobem zapisu tekstu JSON zakodowanego w `String`uIW UTF-8 z typowych typów .NET, takich jak , `Int32`i `DateTime`. Moduł zapisujący jest typu niskiego poziomu, który może służyć do tworzenia niestandardowych serializatorów.

W poniższych sekcjach wyjaśniono `Utf8JsonWriter`zalecane wzorce programowania do korzystania .

### <a name="write-with-utf-8-text"></a>Pisanie za pomocą tekstu UTF-8

Aby osiągnąć najlepszą możliwą wydajność podczas korzystania z `Utf8JsonWriter`, zapisu ładunków JSON już zakodowane jako tekst UTF-8, a nie jako ciągi UTF-16. Służy <xref:System.Text.Json.JsonEncodedText> do buforowania i wstępnego kodowania znanych nazw właściwości ciągu i wartości jako wartości statycznych i przekazywania ich do modułu zapisującego, zamiast używania literałów ciągu UTF-16. Jest to szybsze niż buforowanie i używanie tablic bajtowych UTF-8.

Takie podejście działa również, jeśli trzeba zrobić niestandardowe ucieczki. `System.Text.Json`nie pozwala wyłączyć ucieczki podczas pisania ciągu. Jednak można przekazać we własnym <xref:System.Text.Encodings.Web.JavaScriptEncoder> zwyczaju jako opcja do modułu zapisującego lub utworzyć własne, `JsonEncodedText` który używa do `JavascriptEncoder` ucieczki, a następnie napisać `JsonEncodedText` zamiast ciągu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodowania znaków](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Zapis wartości nieprzetworzonych

Metoda `Newtonsoft.Json` `WriteRawValue` zapisuje nieprzetworzone JSON, gdzie oczekiwana jest wartość. <xref:System.Text.Json>nie ma bezpośredniego odpowiednika, ale oto obejście, które zapewnia, że tylko prawidłowy JSON jest zapisywany:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Dostosowywanie ucieczki postaci

[StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) ustawienie `JsonTextWriter` oferuje opcje ucieczki wszystkich znaków innych niż ASCII **lub** znaków HTML. Domyślnie `Utf8JsonWriter` wyuje wszystkie znaki inne niż ASCII **i** HTML. To ucieczka odbywa się ze względów bezpieczeństwa obrony w głębi. Aby określić inną zasadę <xref:System.Text.Encodings.Web.JavaScriptEncoder> ucieczki, utwórz i ustaw plik <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>. Aby uzyskać więcej informacji, zobacz [Dostosowywanie kodowania znaków](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>Dostosowywanie formatu JSON

`JsonTextWriter`zawiera następujące ustawienia, `Utf8JsonWriter` dla których nie ma odpowiednika:

* [Wcięcie](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) — określa liczbę znaków do wcięcie. `Utf8JsonWriter`zawsze wykonuje wcięcie dwuznakowe.
* [WcięcieChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) — określa znak, który ma być używany do wcięci.  `Utf8JsonWriter`zawsze używa odstępów.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) - Określa znak, który ma być używany do otaczania wartości ciągów.  `Utf8JsonWriter`zawsze używa podwójnych cudzysłowów.
* [QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) - Określa, czy nazwy właściwości mają być otoczone cudzysłowami.  `Utf8JsonWriter`zawsze otacza je cytatami.

Nie ma żadnych obejść, które pozwoli ci dostosować `Utf8JsonWriter` JSON produkowane przez w ten sposób.

### <a name="write-null-values"></a>Zapis wartości null

Aby zapisać wartości `Utf8JsonWriter`null za pomocą , wywołaj:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>, aby zapisać parę klucz-wartość z wartością null jako wartość.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>aby zapisać null jako element tablicy JSON.

Dla właściwości string, jeśli ciąg <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> ma <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> wartość `WriteNull` null `WriteNullValue`i są równoważne i .

### <a name="write-timespan-uri-or-char-values"></a>Zapis wartości Timespan, Uri lub char

`JsonTextWriter`udostępnia `WriteValue` metody dla [timespan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)i [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) wartości. `Utf8JsonWriter`nie ma równoważnych metod. Zamiast tego sformatować te wartości `ToString()`jako ciągi <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>(na przykład wywołując) i wywołać .

### <a name="multi-targeting"></a>Kierowanie wielokrotne

Jeśli musisz nadal używać `Newtonsoft.Json` dla niektórych struktur docelowych, można multi-target i mieć dwie implementacje. Jednak nie jest to trywialne i wymagałoby pewnego `#ifdefs` powielania źródeł. Jednym ze sposobów udostępniania jak najwięcej kodu, jak `Utf8JsonWriter` `Newtonsoft` `JsonTextWriter`to możliwe jest utworzenie otoki wokół i . Ta otoka ujednoliciłaby powierzchnię publiczną, jednocześnie izolując różnice behawioralne. Pozwala to wyizolować zmiany głównie do konstrukcji typu. [Biblioteka microsoft.extensions.dependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) jest następująca:

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Dodatkowe zasoby

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.JsonPrzegląd](system-text-json-overview.md)
* [Jak używaćSystem.Text.Json](system-text-json-how-to.md)
* [Jak pisać konwertery niestandardowe](system-text-json-converters-how-to.md)
* [Pomoc techniczna datetime i datetimeoffset wSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonOdwołanie do interfejsu API](xref:System.Text.Json)
* [System.Text.Json. Odwołanie do interfejsu API serializacji](xref:System.Text.Json.Serialization)
