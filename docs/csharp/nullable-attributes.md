---
title: Uaktualnij interfejsy API dla typów odwołań dopuszczających wartości null z atrybutami, które definiują oczekiwania dla wartości zerowych
description: Dowiedz się, jak używać opisowych atrybutów AllowNull, DisallowNull, MaybeNull, NotNull i innych, aby w pełni opisać stan null interfejsów API.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 7142fe0566b1cc7373f5dc777c36443041114c4f
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204632"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizowanie bibliotek do używania typów referencyjnych dopuszczających wartości null i przekazywanie reguł dopuszczających wartość null do wywoływania

Dodanie [typów referencyjnych dopuszczających wartość null](nullable-references.md) oznacza, czy można zadeklarować, czy wartość `null` jest dozwolona, czy nieoczekiwana dla każdej zmiennej. Ponadto można zastosować wiele atrybutów: `AllowNull`, `DisallowNull`, `MaybeNull`, `NotNull`, `NotNullWhen`, `MaybeNullWhen`i `NotNullWhenNotNull`, aby całkowicie opisać Stany null argumentu i wartości zwracane. Zapewnia to doskonałe środowisko podczas pisania kodu. Otrzymasz ostrzeżenia, jeśli zmienna niedopuszczające wartości null może być ustawiona na `null`. Są wyświetlane ostrzeżenia, jeśli zmienna dopuszczająca wartość null nie jest sprawdzana przed usunięciem odwołania do niej. Aktualizowanie bibliotek może zająć trochę czasu, ale Payoffs. Więcej informacji udostępnianych kompilatorowi o tym, *kiedy* `null` wartość jest dozwolona lub zabroniona, będzie można uzyskać lepszych ostrzeżeń użytkowników interfejsu API. Zacznijmy od znanego przykładu. Wyobraź sobie, że biblioteka zawiera następujący interfejs API do pobrania ciągu zasobu:

```csharp
bool TryGetMessage(string key, out string message)
```

Poprzedni przykład jest zgodny ze znanym wzorcem `Try*` w programie .NET. Dla tego interfejsu API istnieją dwa argumenty odwołania: `key` i `message`. Ten interfejs API ma następujące reguły dotyczące wartości null tych argumentów:

- Obiekty wywołujące nie powinny przekazywać `null` jako argumentu dla `key`.
- Obiekty wywołujące mogą przekazać zmienną, której wartość jest `null` jako argument dla `message`.
- Jeśli metoda `TryGetMessage` zwraca `true`, wartość `message` nie jest równa null. Jeśli wartość zwracana jest `false,` wartość `message` (a jej stan null) ma wartość null.

Reguła dla `key` może być całkowicie wyrażona przez typ zmiennej: `key` powinna być typem referencyjnym, który nie dopuszcza wartości null. `message` parametr jest bardziej skomplikowany. Umożliwia `null` jako argument, ale gwarantuje, że po powodzeniu `out` argument nie ma wartości null. W tych scenariuszach potrzebujesz bogatszego słownictwa do opisywania oczekiwań.

Aktualizacja biblioteki na potrzeby odwołań do wartości null wymaga więcej niż `?` na niektórych zmiennych i nazwach typów. Powyższy przykład pokazuje, że należy przejrzeć interfejsy API i uwzględnić oczekiwania dla każdego argumentu wejściowego. Należy wziąć pod uwagę gwarancje wartości zwracanej oraz wszystkie `out` lub `ref` argumenty przy zwracaniu metody. Następnie Przekaż te reguły do kompilatora, a kompilator dostarczy ostrzeżenia, gdy wywołujący nie przestrzegają tych reguł.

To działanie jest czasochłonne. Zacznijmy od strategii, aby dowiedzieć się, jak Twoja biblioteka lub aplikacja doznała wartości null, a także zrównoważyć inne wymagania i elementy dostarczane. Zobaczysz, jak zrównoważyć bieżące programowanie, włączając typy referencyjne dopuszczające wartość null. Nauczysz się wyzwań dla definicji typów ogólnych. Dowiesz się, jak zastosować atrybuty do opisywania warunków wstępnych i postanowień dotyczących poszczególnych interfejsów API.

## <a name="choose-a-nullable-strategy"></a>Wybierz strategię dopuszczającą wartość null

Pierwszy wybór polega na tym, czy typy odwołań dopuszczające wartość null mają być domyślnie włączone czy wyłączone. Istnieją dwie strategie:

- Włącz typy referencyjne dopuszczające wartość null dla całego projektu i wyłącz je w kodzie, który nie jest gotowy.
- Włącz tylko typy referencyjne dopuszczające wartość null dla kodu, który jest oznaczony adnotacją dla typów referencyjnych dopuszczających wartość null.

Pierwsza strategia działa najlepiej, gdy dodajesz inne funkcje do biblioteki, gdy zaktualizujesz ją do typów referencyjnych dopuszczających wartość null. Cały nowy projekt ma świadomość dopuszczający wartość null. Gdy aktualizujesz istniejący kod, włączasz typy odwołań do wartości null w tych klasach.

Postępując zgodnie z pierwszą strategią, wykonaj następujące czynności:

1. Włącz Typy dopuszczające wartość null dla całego projektu, dodając `<Nullable>enable</Nullable>` element do plików *csproj* . 
1. Dodaj `#nullable disable` pragma do każdego pliku źródłowego w projekcie. 
1. Podczas pracy nad każdym plikiem Usuń pragmę i rozwiąż wszelkie ostrzeżenia.

Ta pierwsza strategia ma więcej zadań z góry, aby dodać pragmę do każdego pliku. Korzyść polega na tym, że każdy nowy plik kodu dodany do projektu będzie miał włączoną wartość null. Każda nowa służbowa będzie mieć świadomość wartości null; należy zaktualizować tylko istniejący kod.

Druga strategia działa lepiej, jeśli biblioteka jest ogólnie stabilna, a głównym celem rozwoju jest przyjęcie typów referencyjnych dopuszczających wartość null. W przypadku dodawania adnotacji do interfejsów API należy włączyć typy odwołań do wartości null. Po zakończeniu włączać dla całego projektu typy referencyjne dopuszczające wartość null.

Postępując zgodnie z tą drugą strategią, należy wykonać następujące czynności:

1. Dodaj `#nullable enable` pragma do pliku, który ma być dopuszczający wartość null.
1. Rozwiązywanie wszelkich ostrzeżeń.
1. Wykonaj te dwa pierwsze kroki, dopóki cała biblioteka nie doznała wartości null.
1. Włącz Typy dopuszczające wartość null dla całego projektu, dodając `<Nullable>enable</Nullable>` element do plików *csproj* . 
1. Usuń `#nullable enable` pragmy, ponieważ nie są już potrzebne.

Ta druga strategia ma mniej pracy z góry. Wadą jest to, że pierwsze zadanie podczas tworzenia nowego pliku to dodanie dyrektywy pragma i przekazanie jej do wartości null. Jeśli wszyscy deweloperzy w zespole zapomnili, nowy kod jest teraz w zaległości prac, aby umożliwić sobie dopełnienie kodu do wartości null.

Które z tych strategii są wybierane, zależy od tego, jak dużo aktywnego programowania odbywa się w projekcie. Im bardziej dojrzały i stabilny projekt, tym lepiej druga strategia. Im więcej funkcji jest opracowywanych, tym lepsza jest pierwsza strategia.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Czy ostrzeżenia o wartościach null wprowadzają istotne zmiany?

Przed włączeniem typów referencyjnych dopuszczających wartości null, zmienne są uznawane za *Oblivious dopuszczające wartość null*. Po włączeniu typów referencyjnych dopuszczających wartości null wszystkie te zmienne *nie dopuszczają wartości null*. Kompilator będzie wystawiał ostrzeżenia, jeśli te zmienne nie są zainicjowane do wartości innych niż null.

Inne prawdopodobnie Źródło ostrzeżeń ma zwracane wartości, gdy wartość nie została zainicjowana.

Pierwszym krokiem w przypadku rozwiązywania ostrzeżeń kompilatora jest użycie adnotacji `?` dla parametrów i zwracanych typów, aby wskazać, kiedy argumenty lub wartości zwracane mogą mieć wartość null. Gdy zmienne odwołania nie mogą mieć wartości null, oryginalna deklaracja jest poprawna. W takim przypadku cel nie tylko naprawi ostrzeżenia. Im bardziej istotny jest sposób, aby kompilator mógł zrozumieć zamiar dla potencjalnych wartości null. Podczas badania ostrzeżeń możesz przejść do następnej głównej decyzji dotyczącej biblioteki. Czy chcesz rozważyć modyfikowanie sygnatur interfejsów API, aby dokładniej komunikować swój projekt? Lepszym podpisem interfejsu API dla metody `TryGetMessage` przeanalizowanej wcześniej może być:

```csharp
string? TryGetMessage(string key);
```

Wartość zwracana wskazuje powodzenie lub niepowodzenie i przenosi wartość w przypadku znalezienia wartości. W wielu przypadkach zmiana sygnatur interfejsów API może poprawić sposób, w jaki komunikują się wartości null.

Jednak w przypadku bibliotek publicznych lub bibliotek z dużymi bazami użytkowników można preferować nie wprowadzać żadnych zmian sygnatury interfejsu API. W tych przypadkach i innych wspólnych wzorców można zastosować atrybuty, aby dokładniej zdefiniować, kiedy może być `null`argumentu lub wartości zwracanej. Bez względu na to, czy należy rozważyć zmianę powierzchni interfejsu API, prawdopodobnie okaże się, że tylko adnotacje typu nie są wystarczające do opisywania wartości `null` argumentów lub zwracanych wartości. W tych przypadkach można zastosować atrybuty, aby dokładniej opisać interfejs API. 

## <a name="attributes-extend-type-annotations"></a>Atrybuty rozszerzonego typu

Dodano kilka atrybutów w celu wyrażenia dodatkowych informacji o stanie null zmiennych. Wszystkie kod, który zapisano C# przed 8 wprowadzonymi typami odwołań dopuszczających wartości null, miał *wartość null Oblivious*. Oznacza to, że jakakolwiek zmienna typu referencyjnego może mieć wartość null, ale sprawdzanie wartości null nie jest wymagane. Gdy kod *dopuszcza wartość null*, te reguły zostaną zmienione. Typ referencyjny nigdy nie powinien być wartością `null`, a typy referencyjne dopuszczające wartość null muszą zostać sprawdzone względem `null` przed usunięciem odwołania.

Reguły interfejsów API mogą być bardziej skomplikowane, jak pokazano w scenariuszu interfejsu API `TryGetValue`. Wiele interfejsów API ma bardziej złożone reguły dla sytuacji, gdy zmienne mogą lub nie mogą być `null`. W takich przypadkach użyjesz jednego z następujących atrybutów, aby przedstawić te reguły:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy niedopuszczający wartości null może mieć wartość null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy dopuszczający wartość null nigdy nie powinien mieć wartości null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): wartość zwracana niedopuszczający wartości null może być równa null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): wartość zwracana do wartości null nigdy nie będzie równa null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy, który nie dopuszcza wartości null, może mieć wartość null, gdy metoda zwraca określoną wartość `bool`.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do wartości null nie będzie miał wartości null, gdy metoda zwróci określoną wartość `bool`.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): wartość zwracana nie ma wartości null, jeśli argument dla określonego parametru nie ma wartości null.

Powyższe opisy stanowią krótkie informacje o tym, co robi każdy atrybut. W poniższych sekcjach opisano zachowanie i ich znaczenie.

Dodanie tych atrybutów zapewnia kompilatorowi więcej informacji na temat reguł dla interfejsu API. Gdy Wywoływanie kodu jest kompilowane w kontekście włączonego wartości null, kompilator ostrzega wywoływania, gdy narusza te reguły. Te atrybuty nie umożliwiają wykonywania dodatkowych operacji sprawdzania w implementacji.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Określ warunki wstępne: `AllowNull` i `DisallowNull`

Należy rozważyć właściwość odczytu/zapisu, która nigdy nie zwraca `null`, ponieważ ma ona rozsądną wartość domyślną. Obiekty wywołujące przechodzą `null` do zestawu metod dostępu podczas ustawiania tej wartości domyślnej. Rozważmy na przykład system obsługi komunikatów, który prosi o podanie nazwy ekranu w pokoju rozmowy. Jeśli żaden nie jest podany, system generuje nazwę losową:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Gdy kompilujesz poprzedni kod w kontekście dopuszczającym wartość null, wszystko jest bardzo precyzyjne. Po włączeniu typów referencyjnych dopuszczających wartości null Właściwość `ScreenName` będzie niedostępna do wartości null. Jest to poprawne dla metody dostępu `get`: nigdy nie zwraca `null`. Obiekty wywołujące nie muszą sprawdzać zwracanej właściwości dla `null`. Ale teraz ustawienie właściwości na `null` generuje ostrzeżenie. Aby kontynuować obsługę tego typu kodu, Dodaj atrybut <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> do właściwości, jak pokazano w poniższym kodzie: 

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Może być konieczne dodanie dyrektywy `using` dla <xref:System.Diagnostics.CodeAnalysis>, aby użyć tego i innych atrybutów omówionych w tym artykule. Ten atrybut jest stosowany do właściwości, a nie metody dostępu `set`. Atrybut `AllowNull` określa *warunki wstępne*i ma zastosowanie tylko do danych wejściowych. Metoda dostępu `get` ma wartość zwracaną, ale nie ma argumentów wejściowych. W związku z tym, atrybut `AllowNull` ma zastosowanie tylko do `set` metody dostępu.

W poprzednim przykładzie pokazano, co należy szukać podczas dodawania atrybutu `AllowNull` w argumencie:

1. Ogólnym kontraktem tej zmiennej jest, że nie należy `null`, więc potrzebujesz typu referencyjnego, który nie dopuszcza wartości null.
1. Istnieją scenariusze dla zmiennej wejściowej, która ma być `null`, ale nie są one najczęstszym użyciem.

Najczęściej ten atrybut jest wymagany dla właściwości, `in`, `out`i `ref` argumentów. Atrybut `AllowNull` jest najlepszym wyborem, gdy zmienna jest zwykle inna niż null, ale musisz zezwolić na `null` jako warunek wstępny.

Kontrast zawierający scenariusze używania `DisallowNull`: ten atrybut służy do określenia, że zmienna wejściowa typu dopuszczającego wartość null nie powinna być `null`. Rozważmy właściwość, w której `null` jest wartością domyślną, ale klienci mogą ustawić tylko wartość różną od null. Rozważmy następujący kod:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Poprzedni kod jest najlepszym sposobem wyrażania projektu, że `ReviewComment` może być `null`, ale nie można go ustawić jako `null`. Gdy ten kod dopuszcza wartość null, można jawnie wyrazić ten pomysł do wywoływania przy użyciu <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>:

```csharp
[DisallowNull] 
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

W kontekście dopuszczającym wartość null metoda dostępu `ReviewComment` `get` może zwracać wartość domyślną `null`. Kompilator ostrzega o tym, że musi zostać sprawdzony przed dostępem. Ponadto ostrzega wywołujących, że mimo że może być `null`, obiekty wywołujące nie powinny jawnie ustawiać go do `null`. Atrybut `DisallowNull` określa również *warunek wstępny*, nie ma wpływu na `get` metodę dostępu. Należy wybrać użycie atrybutu `DisallowNull`, gdy zobaczysz następujące cechy:

1. Zmienna może być `null` w scenariuszach podstawowych, często podczas pierwszego wystąpienia.
1. Zmienna nie powinna być jawnie ustawiona na `null`.

Te sytuacje często występują w kodzie, który pierwotnie miał *wartość null Oblivious*. Może być to, że właściwości obiektu są ustawiane w dwóch odrębnych operacjach inicjalizacji. Niektóre właściwości mogą być ustawione tylko po zakończeniu pewnej asynchronicznej pracy.

Atrybuty `AllowNull` i `DisallowNull` umożliwiają określenie, że warunki wstępne dotyczące zmiennych mogą nie pasować do adnotacji dopuszczających wartości null w tych zmiennych. Zapewniają one więcej szczegółowych informacji o cechach interfejsu API. Te dodatkowe informacje ułatwiają wywoływanie interfejsu API. Należy pamiętać o określeniu warunków wstępnych przy użyciu następujących atrybutów:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy niedopuszczający wartości null może mieć wartość null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy dopuszczający wartość null nigdy nie powinien mieć wartości null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Określ warunki końcowe: `MaybeNull` i `NotNull`

Załóżmy, że masz metodę o następującej sygnaturze:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Prawdopodobnie Zapisano metodę podobną do tej, aby zwrócić `null`, gdy nie znaleziono poszukiwanej nazwy. `null` jasno wskazuje, że nie znaleziono rekordu. W tym przykładzie istnieje możliwość zmiany typu zwracanego z `Customer` na `Customer?`. Deklarowanie wartości zwracanej jako typ referencyjny dopuszczający wartość null Określa zamiar tego interfejsu API jasno. 

Z przyczyn objętych [definicjami ogólnymi i wartością null](#generic-definitions-and-nullability) ta technika nie działa z metodami ogólnymi. Może istnieć Metoda ogólna, która następuje po podobnym wzorcu:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Nie można określić, że wartość zwracana jest `T?`. Metoda zwraca `null`, gdy nie znaleziono poszukiwanego elementu. Ponieważ nie można zadeklarować typu zwracanego `T?`, należy dodać adnotację `MaybeNull` do zwracanej metody:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Poprzedni kod informuje wywołujących, że kontrakt implikuje typ niedopuszczający wartości null, ale zwracana wartość *może* być równa null.  Użyj atrybutu `MaybeNull`, gdy interfejs API powinien być typu niedopuszczający wartości null, zazwyczaj jest parametrem typu ogólnego, ale mogą występować wystąpienia, w których `null` zostałyby zwrócone.

Można również określić, że wartość zwracana lub `out` lub argument `ref` nie ma wartości null, mimo że typ jest typem dopuszczającym wartość null. Rozważmy metodę, która zapewnia, że tablica jest wystarczająco duża, aby pomieścić liczbę elementów. Jeśli argument wejściowy nie ma pojemności, procedura przydzieli nową tablicę i skopiuje do niej wszystkie istniejące elementy. Jeśli argument wejściowy jest `null`, procedura przydzieli nowy magazyn. W przypadku wystarczającej pojemności procedura nie wykonuje żadnych czynności:

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

Po włączeniu typów odwołań o wartości null, należy upewnić się, że poprzedni kod kompiluje bez ostrzeżeń. Gdy metoda zwraca, gwarantowany argument `storage` nie ma wartości null. Możliwe jest jednak, aby wywoływać `EnsureCapacity` z odwołaniem null. Można wprowadzić `storage` typu referencyjnego dopuszczającego wartość null i dodać `NotNull` po warunku do deklaracji parametru:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Poprzedni kod wyraża istniejący kontrakt bardzo jasno: obiekty wywołujące mogą przekazać zmienną z wartością `null`, ale wartość zwracana jest gwarantowana, aby nigdy nie była równa null. Atrybut `NotNull` jest najbardziej przydatny dla argumentów `ref` i `out`, w których `null` może być przekazane jako argument, ale ten argument ma gwarancję not null, gdy metoda zwraca.

Należy określić warunki końcowe bezwarunkowe, korzystając z następujących atrybutów:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): wartość zwracana niedopuszczający wartości null może być równa null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): wartość zwracana do wartości null nigdy nie będzie równa null.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Określ warunkowe warunki końcowe: `NotNullWhen`, `MaybeNullWhen`i `NotNullIfNotNull`

Najkorzystniej znasz metodę `string` <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>. Ta metoda zwraca `true`, gdy argument ma wartość null lub jest pustym ciągiem. Jest to forma sprawdzania wartości null: obiekty wywołujące nie muszą mieć wartości null — Sprawdź, czy metoda zwraca `false`. Aby określić metodę, taką jak ta, która dopuszcza wartość null, należy ustawić argument na typ dopuszczający wartość null i dodać atrybut `NotNullWhen`:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Informuje kompilator, że żaden kod, w którym wartość zwracana jest `false` nie musi być sprawdzona null. Dodanie atrybutu informuje o analizie statycznej kompilatora, który `IsNullOrEmpty` wykonuje wymagane sprawdzanie wartości null: gdy zwraca `false`, argument wejściowy nie jest `null`.

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

Metoda <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> zostanie umieszczona w adnotacji, jak pokazano powyżej dla programu .NET Core 3,0. W bazie kodu mogą znajdować się podobne metody, które sprawdzają stan obiektów dla wartości null. Kompilator nie rozpoznaje niestandardowych metod sprawdzania wartości null i należy samodzielnie dodać adnotacje. Po dodaniu atrybutu analiza statyczna kompilatora wie, kiedy sprawdzona zmienna ma wartość null.

Innym zastosowaniem tych atrybutów jest wzorzec `Try*`. Warunki końcowe dla zmiennych `ref` i `out` są przekazywane przez wartość zwracaną. Rozważmy tę metodę pokazaną wcześniej:

```csharp
bool TryGetMessage(string key, out string message)
```

Poprzednia metoda jest zgodna z typowym środowiskiem .NET idiom: wartość zwracana wskazuje, czy `message` została ustawiona na znalezioną wartość, lub jeśli nie zostanie znaleziony żaden komunikat do wartości domyślnej. Jeśli metoda zwraca `true`, wartość `message` nie jest równa null; w przeciwnym razie metoda ustawia `message` na null.

Można komunikować się z idiom przy użyciu atrybutu `NotNullWhen`. Podczas aktualizowania podpisu dla typów referencyjnych dopuszczających wartości null, należy `message` `string?` i dodać atrybut:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

W powyższym przykładzie wartość `message` jest znana od null, gdy `TryGetMessage` zwraca `true`. Należy dodać adnotacje do podobnych metod w bazie kodu w taki sam sposób: argumenty mogą być `null`i nie mieć wartości null, gdy metoda zwraca `true`.

Istnieje również jeden atrybut końcowy. Czasami stan null wartości zwracanej zależy od stanu zerowego co najmniej jednego argumentu wejściowego. Metody te zwracają wartość różną od null, gdy pewne argumenty wejściowe nie będą `null`. Aby poprawnie dodać adnotację do tych metod, Użyj atrybutu `NotNullIfNotNull`. Weź pod uwagę następującą metodę:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Jeśli argument `url` nie ma wartości null, dane wyjściowe nie `null`. Po włączeniu odwołań do wartości null ten podpis działa prawidłowo, pod warunkiem, że interfejs API nigdy nie akceptuje danych wejściowych o wartości null. Jeśli jednak dane wejściowe mogą mieć wartość null, wówczas wartość zwracana może być również wartością null. W związku z tym można zmienić sygnaturę na następujący kod:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

To również działa, ale często wymuszają wywoływania dodatkowych `null`. Kontrakt polega na tym, że wartość zwracana byłaby `null` tylko wtedy, gdy argument wejściowy `url` jest `null`. Aby można było wyrazić ten kontrakt, należy dodać adnotację do tej metody, jak pokazano w poniższym kodzie:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Wartość zwracana i argument mają adnotację z `?` wskazującą, że można `null`. Ten atrybut dokładniej objaśnia, że wartość zwracana nie będzie równa null, jeśli argument `url` nie jest `null`.

Należy określić warunkowe warunki końcowe przy użyciu następujących atrybutów:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy, który nie dopuszcza wartości null, może mieć wartość null, gdy metoda zwraca określoną wartość `bool`.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do wartości null nie będzie miał wartości null, gdy metoda zwróci określoną wartość `bool`.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): wartość zwracana nie ma wartości null, jeśli argument wejściowy dla określonego parametru nie ma wartości null.

## <a name="generic-definitions-and-nullability"></a>Definicje generyczne i wartości null

Poprawne powiadamianie o stanie null typów ogólnych i metod ogólnych wymaga szczególnej uwagi. Wynika to z faktu, że typ wartości null i typ referencyjny dopuszczający wartość null są zasadniczo różne. `int?` jest synonimem dla `Nullable<int>`, a `string?` jest `string` z atrybutem dodanym przez kompilator. W efekcie kompilator nie może wygenerować poprawnego kodu dla `T?` bez znajomości, czy `T` jest `class` lub `struct`. 

Nie oznacza to, że nie można użyć typu dopuszczającego wartości null (typu wartości lub typu referencyjnego) jako argumentu typu dla zamkniętego typu ogólnego. Zarówno `List<string?>`, jak i `List<int?>` są prawidłowymi wystąpieniami `List<T>`. 

Oznacza to, że nie można użyć `T?` w ogólnej klasie lub deklaracji metody bez ograniczeń. Na przykład <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> nie zostanie zmieniony na zwraca `T?`. Ograniczenie to można przezwyciężyć, dodając ograniczenie `struct` lub `class`. Z dowolnego z tych ograniczeń kompilator wie, jak generować kod dla `T` i `T?`.

Możesz chcieć ograniczyć typy używane dla argumentu typu ogólnego jako niedopuszczające wartości null. Można to zrobić przez dodanie ograniczenia `notnull` tego argumentu typu. Po zastosowaniu tego ograniczenia argument typu nie może być typem dopuszczającym wartość null.

## <a name="conclusions"></a>Wnioski

Dodanie typów referencyjnych dopuszczających wartość null zapewnia wstępne słownictwo do opisywania oczekiwań interfejsów API dla zmiennych, które mogą być `null`. Dodatkowe atrybuty zapewniają bogatszy słownictwo do opisania stanu wartości null zmiennych jako warunków wstępnych i warunki końcowe. Te atrybuty bardziej wyraźnie opisują oczekiwania i zapewniają lepszy komfort używania interfejsów API przez deweloperów.

Podczas aktualizowania bibliotek dla kontekstu dopuszczającego wartość null należy dodać te atrybuty, aby ułatwić użytkownikom interfejsów API poprawne użycie. Te atrybuty pomagają w pełni opisać stan null argumentów wejściowych i zwracanych wartości:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy niedopuszczający wartości null może mieć wartość null.
- [DisallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy dopuszczający wartość null nigdy nie powinien mieć wartości null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): wartość zwracana niedopuszczający wartości null może być równa null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): wartość zwracana do wartości null nigdy nie będzie równa null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy, który nie dopuszcza wartości null, może mieć wartość null, gdy metoda zwraca określoną wartość `bool`.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do wartości null nie będzie miał wartości null, gdy metoda zwróci określoną wartość `bool`.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): wartość zwracana nie ma wartości null, jeśli argument wejściowy dla określonego parametru nie ma wartości null.
