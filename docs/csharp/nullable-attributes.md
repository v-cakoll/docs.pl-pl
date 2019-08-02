---
title: Uaktualnij interfejsy API z atrybutami, aby zdefiniować oczekiwania o wartości null
description: W tym artykule wyjaśniono motywacje i techniki umożliwiające dodawanie opisowych atrybutów do opisu stanu wartości null argumentów oraz zwracanie wartości z interfejsów API
ms.date: 07/31/2019
ms.openlocfilehash: 9a5eded385d5eac7a493a36876557cadf083afad
ms.sourcegitcommit: 8c6426a3d2adff5fbcbe1fed0f28eda718c15351
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68733435"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizowanie bibliotek do używania typów referencyjnych dopuszczających wartości null i przekazywanie reguł dopuszczających wartość null do wywoływania.

Dodanie [typów referencyjnych dopuszczających wartość null](nullable-references.md) oznacza, czy można zadeklarować, czy `null` wartość jest dozwolona, czy nieoczekiwana dla każdej zmiennej. Zapewnia to doskonałe środowisko podczas pisania kodu. Są wyświetlane ostrzeżenia, jeśli zmienna niedopuszczający wartości null może być `null`ustawiona na wartość. Są wyświetlane ostrzeżenia, jeśli zmienna dopuszczająca wartość null nie jest sprawdzana przed usunięciem odwołania do niej. Aktualizowanie bibliotek może zająć trochę czasu, ale Payoffs. Więcej informacji udostępnianych kompilatorowi o tym, *kiedy* `null` wartość jest dozwolona lub zabroniona, użytkownicy otrzymają lepszych ostrzeżeń dotyczących interfejsu API. Zacznijmy od znanego przykładu. Wyobraź sobie, że biblioteka zawiera następujący interfejs API do pobrania ciągu zasobu:

```csharp
bool TryGetMessage(string key, out string message)
```

Poprzedni przykład jest zgodny ze znajomym `Try*` wzorcem w programie .NET. Istnieją dwa argumenty odwołania dla tego interfejsu API: `key` `message` i parametru. Ten interfejs API ma następujące reguły dotyczące wartości null tych argumentów:

- Obiekty wywołujące nie `null` powinny być przekazywane jako `key`argument dla elementu.
- Obiekty wywołujące mogą przekazywać zmienną, której `null` wartość jest argumentem `message`dla.
- Jeśli metoda zwraca `true`, wartość `message` nie jest równa null. `TryGetMessage` Jeśli wartość zwracana jest `false,` `message` wartością parametru (i jego stan zerowy) ma wartość null.

Reguła dla `key` może być całkowicie wyrażona przez typ zmiennej: `key` powinien być typem referencyjnym, który nie dopuszcza wartości null. `message` Parametr jest bardziej skomplikowany. Umożliwia `null` jako argument, ale gwarantuje, że w przypadku powodzenia ten `out` argument nie ma wartości null. W tych scenariuszach potrzebujesz bogatszego słownictwa do opisywania oczekiwań.

Aktualizacja biblioteki dla odwołań do wartości null wymaga więcej niż `?` przestawianie niektórych zmiennych i nazw typów. Powyższy przykład pokazuje, że należy przejrzeć interfejsy API i uwzględnić oczekiwania dla każdego argumentu wejściowego. Należy wziąć pod uwagę gwarancje wartości zwracanej, `out` a `ref` także wszystkie lub argumenty dla zwracanej metody. Następnie Przekaż te reguły do kompilatora, a kompilator dostarczy ostrzeżenia, gdy wywołujący nie przestrzegają tych reguł.

To działanie jest czasochłonne. Zacznijmy od strategii, aby dowiedzieć się, jak Twoja biblioteka lub aplikacja doznała wartości null, a także zrównoważyć inne wymagania i elementy dostarczane. Zobaczysz, jak zrównoważyć bieżące programowanie, włączając typy referencyjne dopuszczające wartość null. Nauczysz się wyzwań dla definicji typów ogólnych. Dowiesz się, jak zastosować atrybuty do opisywania warunków wstępnych i postanowień dotyczących poszczególnych interfejsów API.

## <a name="choose-a-nullable-strategy"></a>Wybierz strategię dopuszczającą wartość null

Pierwszy wybór polega na tym, czy typy odwołań dopuszczające wartość null mają być domyślnie włączone czy wyłączone. Istnieją dwie strategie:

- Włącz typy referencyjne dopuszczające wartość null dla całego projektu i wyłącz je w kodzie, który nie jest gotowy.
- Włącz tylko typy referencyjne dopuszczające wartość null dla kodu, który jest oznaczony adnotacją dla typów referencyjnych dopuszczających wartość null.

Pierwsza strategia działa najlepiej, gdy dodajesz inne funkcje do biblioteki, gdy zaktualizujesz ją do typów referencyjnych dopuszczających wartość null. Cały nowy projekt ma świadomość dopuszczający wartość null. Gdy aktualizujesz istniejący kod, włączasz typy odwołań do wartości null w tych klasach.

Postępując zgodnie z pierwszą strategią, wykonaj następujące czynności:

1. Włącz Typy dopuszczające wartość null dla całego projektu przez `<Nullable>enable</Nullable>` dodanie elementu do plików *csproj* . 
1. `#nullable disable` Dodaj pragmę do każdego pliku źródłowego w projekcie. 
1. Podczas pracy nad każdym plikiem Usuń pragmę i rozwiąż wszelkie ostrzeżenia.

Ta pierwsza strategia ma więcej zadań z góry, aby dodać pragmę do każdego pliku. Korzyść polega na tym, że każdy nowy plik kodu dodany do projektu będzie miał włączoną wartość null. Każda nowa służbowa będzie mieć świadomość wartości null; należy zaktualizować tylko istniejący kod.

Druga strategia działa lepiej, jeśli biblioteka jest ogólnie stabilna, a głównym celem rozwoju jest przyjęcie typów referencyjnych dopuszczających wartość null. W przypadku dodawania adnotacji do interfejsów API należy włączyć typy odwołań do wartości null. Po zakończeniu włączać dla całego projektu typy referencyjne dopuszczające wartość null.

Postępując zgodnie z tą drugą strategią, należy wykonać następujące czynności:

1. `#nullable enable` Dodaj pragmę do pliku, dla którego chcesz wprowadzić wartość null.
1. Rozwiązywanie wszelkich ostrzeżeń.
1. Wykonaj te dwa pierwsze kroki, dopóki cała biblioteka nie doznała wartości null.
1. Włącz Typy dopuszczające wartość null dla całego projektu przez `<Nullable>enable</Nullable>` dodanie elementu do plików *csproj* . 
1. `#nullable enable` Usuń dyrektywy pragma, ponieważ nie są już potrzebne.

Ta druga strategia ma mniej pracy z góry. Wadą jest to, że pierwsze zadanie podczas tworzenia nowego pliku to dodanie dyrektywy pragma i przekazanie jej do wartości null. Jeśli wszyscy deweloperzy w zespole zapomnili, nowy kod jest teraz w zaległości prac, aby umożliwić sobie dopełnienie kodu do wartości null.

Które z tych strategii są wybierane, zależy od tego, jak dużo aktywnego programowania odbywa się w projekcie. Im bardziej dojrzały i stabilny projekt, tym lepiej druga strategia. Im więcej funkcji jest opracowywanych, tym lepsza jest pierwsza strategia.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Czy ostrzeżenia o wartościach null wprowadzają istotne zmiany?

Przed włączeniem typów referencyjnych dopuszczających wartości null, zmienne są uznawane za *Oblivious dopuszczające wartość null*. Po włączeniu typów referencyjnych dopuszczających wartości null wszystkie te zmienne *nie dopuszczają wartości null*. Kompilator będzie wystawiał ostrzeżenia, jeśli te zmienne nie są zainicjowane do wartości innych niż null.

Inne prawdopodobnie Źródło ostrzeżeń ma zwracane wartości, gdy wartość nie została zainicjowana.

Pierwszym krokiem w rozwiązywaniu ostrzeżeń kompilatora jest użycie `?` adnotacji dla parametrów i zwracanych typów, aby wskazać, kiedy argumenty lub wartości zwracane mogą mieć wartość null. Gdy zmienne odwołania nie mogą mieć wartości null, oryginalna deklaracja jest poprawna. W takim przypadku cel nie tylko naprawi ostrzeżenia. Im bardziej istotny jest sposób, aby kompilator mógł zrozumieć zamiar dla potencjalnych wartości null. Podczas badania ostrzeżeń możesz przejść do następnej głównej decyzji dotyczącej biblioteki. Czy chcesz rozważyć modyfikowanie sygnatur interfejsów API, aby dokładniej komunikować swój projekt? Lepszym podpisem interfejsu API `TryGetMessage` dla metody analizowanej wcześniej mogą być:


```csharp
string? TryGetMessage(string key);
```

Wartość zwracana wskazuje powodzenie lub niepowodzenie i przenosi wartość w przypadku znalezienia wartości. W wielu przypadkach zmiana sygnatur interfejsów API może poprawić sposób, w jaki komunikują się wartości null.

Jednak w przypadku bibliotek publicznych lub bibliotek z dużymi bazami użytkowników można preferować nie wprowadzać żadnych zmian sygnatury interfejsu API. W tych przypadkach i innych wspólnych wzorców można zastosować atrybuty, aby dokładniej zdefiniować, kiedy może być `null`argument lub wartość zwracana. Bez względu na to, czy można zmienić powierzchnię interfejsu API, prawdopodobnie okaże się, że tylko adnotacje typu nie są `null` wystarczające do opisywania wartości argumentów lub zwracanych wartości. W tych przypadkach można zastosować atrybuty, aby dokładniej opisać interfejs API. 

## <a name="attributes-extend-type-annotations"></a>Atrybuty rozszerzonego typu

Dodano kilka atrybutów w celu wyrażenia dodatkowych informacji o stanie null zmiennych. Wszystkie kod, który zapisano C# przed 8 wprowadzonymi typami odwołań dopuszczających wartości null, miał *wartość null Oblivious*. Oznacza to, że jakakolwiek zmienna typu referencyjnego może mieć wartość null, ale sprawdzanie wartości null nie jest wymagane. Gdy kod *dopuszcza wartość null*, te reguły zostaną zmienione. Typy odwołań nigdy nie powinny być `null` wartościami, a typy referencyjne dopuszczające wartość null `null` muszą zostać sprawdzone przed usunięciem odwołania.

Reguły interfejsów API mogą być `TryGetValue` bardziej skomplikowane, jak pokazano w scenariuszu interfejsu API. Wiele interfejsów API ma bardziej złożone reguły dla sytuacji, gdy zmienne mogą być `null`lub niemożliwe. W takich przypadkach użyjesz jednego z następujących atrybutów, aby przedstawić te reguły:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Niedopuszczający wartości null argument wejściowy może mieć wartość null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy dopuszczający wartość null nigdy nie powinien mieć wartości null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana niedopuszczający wartości null może być zerowa.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Wartość zwracana do wartości null nigdy nie będzie równa null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument, który nie `out` dopuszcza `ref` wartości null lub, może mieć wartość null, gdy wartość zwracana spełnia warunek.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Wartość dopuszczająca `out` wartość null lub `ref` argument nie może mieć wartości null, jeśli zwracaną wartością jest warunek.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Wartość zwracana nie ma wartości null, jeśli argument wejściowy dla określonego parametru nie ma wartości null.

Powyższe opisy stanowią krótkie informacje o tym, co robi każdy atrybut. W poniższych sekcjach opisano zachowanie i ich znaczenie.

Dodanie tych atrybutów zapewnia kompilatorowi więcej informacji na temat reguł dla interfejsu API. Gdy Wywoływanie kodu jest kompilowane w kontekście włączonego wartości null, kompilator ostrzega wywoływania, gdy narusza te reguły. Te atrybuty nie umożliwiają wykonywania dodatkowych operacji sprawdzania w implementacji.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Określ warunki wstępne: `AllowNull` i`DisallowNull`

Rozważ użycie właściwości do odczytu/zapisu, która `null` nigdy nie zwraca, ponieważ ma ona rozsądną wartość domyślną. Obiekty wywołujące `null` przejdą do zestawu metod dostępu podczas ustawiania tej wartości domyślnej. Rozważmy na przykład system obsługi komunikatów, który prosi o podanie nazwy ekranu w pokoju rozmowy. Jeśli żaden nie jest podany, system generuje nazwę losową:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Gdy kompilujesz poprzedni kod w kontekście dopuszczającym wartość null, wszystko jest bardzo precyzyjne. Po włączeniu typów referencyjnych dopuszczających wartość `ScreenName` null, właściwość ta będzie odwołaniem niedopuszczanym do wartości null. Jest to poprawne dla `get` metody dostępu: nigdy nie zwraca. `null` Obiekty wywołujące nie muszą sprawdzać zwracanej właściwości `null`dla elementu. Ale teraz ustawienie właściwości w celu `null` wygenerowania ostrzeżenia. Aby kontynuować obsługę tego typu kodu, Dodaj <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> atrybut do właściwości, jak pokazano w poniższym kodzie: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Może być konieczne dodanie `using` <xref:System.Diagnostics.CodeAnalysis> dyrektywy do programu w celu użycia tego i innych atrybutów omówionych w tym artykule. Ten atrybut jest stosowany do właściwości, a nie do `set` metody dostępu. Atrybut określa *warunki wstępne*i ma zastosowanie tylko do danych wejściowych. `AllowNull` `get` Metoda dostępu ma wartość zwracaną, ale nie ma argumentów wejściowych. W związku z tym `set` atrybutmazastosowanietylkodometodydostępu.`AllowNull`

W poprzednim przykładzie pokazano, co należy szukać podczas dodawania `AllowNull` atrybutu do argumentu:

1. Ogólną umową dla tej zmiennej jest to, że nie `null`powinna ona być, więc potrzebujesz typu referencyjnego, który nie dopuszcza wartości null.
1. Istnieją scenariusze dla zmiennej `null`wejściowej, chociaż nie są one najczęstszym użyciem.

Najczęściej ten atrybut jest potrzebny dla właściwości, `in` `out`, i `ref` argumentów. Ten `AllowNull` atrybut jest najlepszym wyborem, gdy zmienna jest zwykle inna niż null, ale musisz zezwolić `null` jako warunek wstępny.

Przeciwieństwo do użycia `DisallowNull`: Ten atrybut służy do określenia, że zmienna wejściowa typu dopuszczającego wartość null `null`nie powinna być. Rozważmy właściwość, `null` gdzie jest wartością domyślną, ale klienci mogą ustawić ją tylko na wartość różną od null. Rozważmy następujący kod:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Poprzedni kod jest najlepszym sposobem, aby wyrazić projekt, który `ReviewComment` może być `null`, ale nie może być ustawiony na `null`. Gdy ten kod dopuszcza wartość null, można jawnie wyrazić takie koncepcje dla wywołujących przy użyciu <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

W kontekście `ReviewComment` `null`dopuszczającym wartość null metodadostępumożezwrócićwartośćdomyślną.`get` Kompilator ostrzega o tym, że musi zostać sprawdzony przed dostępem. Ponadto ostrzega wywołujących, że mimo że może się `null`to zdarzyć, obiekty wywołujące nie powinny jawnie ustawiać. `null` Atrybut określa również *warunek wstępny*, nie ma wpływu na `get` metodę dostępu. `DisallowNull` Należy wybrać, `DisallowNull` aby użyć atrybutu podczas przestrzegania następujących cech:

1. Zmienna może być `null` w scenariuszach podstawowych, często podczas pierwszego wystąpienia.
1. Zmienna nie powinna być jawnie ustawiona na `null`wartość.

Te sytuacje często występują w kodzie, który pierwotnie miał *wartość null Oblivious*. Może być to, że właściwości obiektu są ustawiane w dwóch odrębnych operacjach inicjalizacji. Niektóre właściwości mogą być ustawione tylko po zakończeniu pewnej asynchronicznej pracy.

Atrybuty `AllowNull` i`DisallowNull` umożliwiają określenie, że warunki wstępne dla zmiennych mogą nie pasować do adnotacji dopuszczających wartości null w tych zmiennych. Zapewniają one więcej szczegółowych informacji o cechach interfejsu API. Te dodatkowe informacje ułatwiają wywoływanie interfejsu API. Należy pamiętać o określeniu warunków wstępnych przy użyciu następujących atrybutów:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Niedopuszczający wartości null argument wejściowy może mieć wartość null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy dopuszczający wartość null nigdy nie powinien mieć wartości null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Określ warunki końcowe: `MaybeNull` i`NotNull`

Załóżmy, że masz metodę o następującej sygnaturze:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Prawdopodobnie Zapisano metodę podobną do tej, aby zwracała `null` się, gdy nie znaleziono nazwy. `null` Jasno wskazuje, że rekord nie został znaleziony. W tym przykładzie można zmienić typ zwracany z `Customer` na. `Customer?` Deklarowanie wartości zwracanej jako typ referencyjny dopuszczający wartość null Określa zamiar tego interfejsu API jasno. 

Z przyczyn objętych [definicjami ogólnymi i wartością null](#generic-definitions-and-nullability) ta technika nie działa z metodami ogólnymi. Może istnieć Metoda ogólna, która następuje po podobnym wzorcu:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Nie można określić, że wartość zwracana to `T?`. Metoda zwraca `null` , gdy nie znaleziono szukanego elementu. Ponieważ nie można zadeklarować `T?` zwracanego typu, należy `MaybeNull` dodać adnotację do zwracanej metody:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Poprzedni kod informuje wywołujących, że kontrakt implikuje typ niedopuszczający wartości null, ale zwracana wartość *może* być równa null.  Użyj atrybutu, gdy interfejs API powinien być typu niedopuszczający wartości null, zazwyczaj parametru typu ogólnego, ale mogą występować wystąpienia, w `null` których zostałyby zwrócone. `MaybeNull`

Można również określić, że wartość zwracana lub `out` argument or `ref` nie mają wartości null, mimo że typ jest typem dopuszczającym wartość null. Rozważmy metodę, która zapewnia, że tablica jest wystarczająco duża, aby pomieścić liczbę elementów. Jeśli argument wejściowy nie ma pojemności, procedura przydzieli nową tablicę i skopiuje do niej wszystkie istniejące elementy. Jeśli argumentem wejściowym `null`jest, procedura przydzieli nowy magazyn. W przypadku wystarczającej pojemności procedura nie wykonuje żadnych czynności:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Tę procedurę można wywołać w następujący sposób:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Po włączeniu typów odwołań o wartości null, należy upewnić się, że poprzedni kod kompiluje bez ostrzeżeń. Gdy metoda zwraca, `storage` argument ma gwarantowaną wartość nie równą null. Jednak jest to możliwe do wywołania `EnsureCapacity` z odwołaniem o wartości null. Można wprowadzić `storage` typ referencyjny dopuszczający wartość null i `NotNull` dodać warunek post do deklaracji parametru:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Powyższy kod odzwierciedla istniejący kontrakt bardzo jasno: Obiekty wywołujące mogą przekazać zmienną o `null` wartości, ale wartość zwracana jest gwarantowana, aby nigdy nie była równa null. Ten `NotNull` atrybut jest najbardziej przydatny `ref` dla `out` argumentów i `null` , gdzie mogą być przekazane jako argument, ale ten argument jest gwarantowany, że nie ma wartości null, gdy metoda zwraca.

Należy określić warunki końcowe bezwarunkowe, korzystając z następujących atrybutów:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana niedopuszczający wartości null może być zerowa.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Wartość zwracana do wartości null nigdy nie będzie równa null.

## <a name="specify-conditional-post-conditions-notnullwhen-and-maybenullwhen"></a>Określ warunkowe warunki końcowe: `NotNullWhen` i`MaybeNullWhen`

Najkorzystniej znasz `string` metodę <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>. Ta metoda zwraca `true` , gdy argument nie ma wartości null i nie jest pustym ciągiem. Jest to forma sprawdzenia wartości null: Obiekty wywołujące nie muszą mieć wartości null — Sprawdź argument, jeśli metoda `false`zwraca wartość. Aby zapewnić metodę, taką jak ta, która dopuszcza wartość null, należy ustawić argument na typ dopuszczający wartość null `NotNullWhen` i dodać atrybut:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Informuje kompilator, że żaden kod, w którym nie jest `false` wymagana wartość zwracana, nie może mieć wartości null. Dodanie atrybutu informuje analizę statyczną kompilatora, która `IsNullOrEmpty` wykonuje niezbędne sprawdzanie wartości null: gdy zwraca `false`, argument wejściowy nie `null`jest.

```csharp
string? userInput = GetUserInput();
if (!(string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

<xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> Metoda zostanie umieszczona w adnotacji, jak pokazano powyżej dla programu .NET Core 3,0. W bazie kodu mogą znajdować się podobne metody, które sprawdzają stan obiektów dla wartości null. Kompilator nie rozpoznaje niestandardowych metod sprawdzania wartości null i należy samodzielnie dodać adnotacje. Po dodaniu atrybutu analiza statyczna kompilatora wie, kiedy sprawdzona zmienna ma wartość null.

Innym zastosowaniem dla tych atrybutów jest `Try*` wzorzec. Warunki końcowe dla `ref` i `out` zmienne są przekazywane przez wartość zwracaną. Rozważmy tę metodę pokazaną wcześniej:

```csharp
bool TryGetMessage(string key, out string message)
```

Poprzednia metoda jest zgodna z typowym środowiskiem .NET idiom: `message` wartość zwracana wskazuje, czy została ustawiona na znalezioną wartość, czy nie zostanie znaleziony komunikat do wartości domyślnej. Jeśli metoda zwraca `true`, `message` wartość nie jest równa null; w przeciwnym razie metoda jest `message` ustawiana na wartość null.

Można komunikować się z idiom przy użyciu `NotNullWhen` atrybutu. W przypadku aktualizowania sygnatury dla typów referencyjnych dopuszczających `message` wartość `string?` null wprowadź i Dodaj atrybut:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

W poprzednim przykładzie wartość jest znana od `message` null, gdy `TryGetMessage` zwraca `true`. Należy dodać adnotacje do podobnych metod w bazie kodu w taki sam sposób: argumenty mogą być `null`i nie mieć wartości null, gdy metoda zwraca. `true`

Istnieje również jeden atrybut końcowy. Czasami stan null wartości zwracanej zależy od stanu zerowego co najmniej jednego argumentu wejściowego. Metody te zwracają wartość różną od null, gdy nie `null`ma określonych argumentów wejściowych. Aby poprawnie dodać adnotację do tych metod, należy `NotNullIfNotNull` użyć atrybutu. Weź pod uwagę następującą metodę:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Jeśli argument nie ma wartości null, dane wyjściowe `null`nie są. `url` Po włączeniu odwołań do wartości null ten podpis działa prawidłowo, pod warunkiem, że interfejs API nigdy nie akceptuje danych wejściowych o wartości null. Jeśli jednak dane wejściowe mogą mieć wartość null, wówczas wartość zwracana może być również wartością null. W związku z tym można zmienić sygnaturę na następujący kod:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

To również działa, ale często zmusza wywołujących do wdrożenia dodatkowych `null` kontroli. Kontrakt jest, że wartość `null` zwracana będzie tylko wtedy, gdy argument `url` wejściowy to `null`. Aby można było wyrazić ten kontrakt, należy dodać adnotację do tej metody, jak pokazano w poniższym kodzie:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Zwracana wartość i argument mają adnotację ze `?` wskazaniem, że może to być. `null` Ten atrybut dokładniej objaśnia, że wartość zwracana nie będzie zerowa, gdy `url` argument nie jest. `null`

Należy określić warunkowe warunki końcowe przy użyciu następujących atrybutów:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument, który nie `out` dopuszcza `ref` wartości null lub, może mieć wartość null, gdy wartość zwracana spełnia warunek.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Wartość dopuszczająca `out` wartość null lub `ref` argument nie może mieć wartości null, jeśli zwracaną wartością jest warunek.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Wartość zwracana nie ma wartości null, jeśli argument wejściowy dla określonego parametru nie ma wartości null.

## <a name="generic-definitions-and-nullability"></a>Definicje generyczne i wartości null

Poprawne powiadamianie o stanie null typów ogólnych i metod ogólnych wymaga szczególnej uwagi. Wynika to z faktu, że typ wartości null i typ referencyjny dopuszczający wartość null są zasadniczo różne. Jest `int?` synonimem `Nullable<int>`dla, `string?` w którym jest `string` atrybut dodany przez kompilator. Wynika to z tego, że kompilator nie może wygenerować poprawnego kodu `T?` dla programu bez znajomości `struct`if `T` `class` lub. 

Nie oznacza to, że nie można użyć typu dopuszczającego wartości null (typu wartości lub typu referencyjnego) jako argumentu typu dla zamkniętego typu ogólnego. Oba `List<string?>` i `List<int?>` sąprawidłowymi`List<T>`wystąpieniami. 

Oznacza to, że nie można użyć `T?` w deklaracji klasy generycznej ani metody bez ograniczeń. Na przykład <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> nie zostanie zmieniony na Return `T?`. Ograniczenie to można przezwyciężyć, dodając `struct` ograniczenie `class` or. W przypadku każdego z tych ograniczeń kompilator wie, jak generować kod dla obu `T` i. `T?`

Możesz chcieć ograniczyć typy używane dla argumentu typu ogólnego jako niedopuszczające wartości null. Można to zrobić, dodając `notnull` ograniczenie dla tego argumentu typu. Po zastosowaniu tego ograniczenia argument typu nie może być typem dopuszczającym wartość null.

## <a name="conclusions"></a>Wnioski

Dodanie typów referencyjnych dopuszczających wartość null zapewnia wstępne słownictwo do opisywania oczekiwań interfejsów API `null`dla zmiennych, które mogą być. Dodatkowe atrybuty zapewniają bogatszy słownictwo do opisania stanu wartości null zmiennych jako warunków wstępnych i warunki końcowe. Te atrybuty bardziej wyraźnie opisują oczekiwania i zapewniają lepszy komfort używania interfejsów API przez deweloperów.

Podczas aktualizowania bibliotek dla kontekstu dopuszczającego wartość null należy dodać te atrybuty, aby ułatwić użytkownikom interfejsów API poprawne użycie. Te atrybuty pomagają w pełni opisać stan null argumentów wejściowych i zwracanych wartości:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Niedopuszczający wartości null argument wejściowy może mieć wartość null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy dopuszczający wartość null nigdy nie powinien mieć wartości null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana niedopuszczający wartości null może być zerowa.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Wartość zwracana do wartości null nigdy nie będzie równa null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument, który nie `out` dopuszcza `ref` wartości null lub, może mieć wartość null, gdy wartość zwracana spełnia warunek.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Wartość dopuszczająca `out` wartość null lub `ref` argument nie może mieć wartości null, jeśli zwracaną wartością jest warunek.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Wartość zwracana nie ma wartości null, jeśli argument wejściowy dla określonego parametru nie ma wartości null.
