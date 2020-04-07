---
title: Uaktualnianie interfejsów API dla typów odwołań z wartościami nullable z atrybutami definiuujającym oczekiwania dotyczące wartości null
description: Naucz się używać atrybutów opisowych AllowNull, DisallowNull, MaybeNull, NotNull i innych, aby w pełni opisać stan zerowy interfejsów API.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: 5d7a864ba1b66ad6b4ae7b0391d170a29147c537
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805843"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizowanie bibliotek w celu używania typów odwołań z regułami zbędnymi wartościami null i przekazywanie reguł nullable wywołującym

Dodanie [typów odwołań nullable](nullable-references.md) oznacza, że `null` można zadeklarować, czy wartość jest dozwolona lub oczekiwana dla każdej zmiennej. Ponadto można zastosować liczbę atrybutów: `AllowNull` `DisallowNull`, `MaybeNull` `NotNull`, `NotNullWhen` `MaybeNullWhen`, `NotNullIfNotNull` , , i całkowicie opisać null stany argumentów i zwracanych wartości. Zapewnia to wspaniałe doświadczenie podczas pisania kodu. Otrzymasz ostrzeżenia, jeśli zmienna nienastępna null może być ustawiona na `null`. Otrzymasz ostrzeżenia, jeśli zmienna nullable nie jest zaznaczona zerem przed wyłuskaniem go. Aktualizowanie bibliotek może zająć trochę czasu, ale wypłaty są tego warte. Im więcej informacji, które podasz `null` kompilatorowi o *tym, kiedy* wartość jest dozwolona lub zabroniona, otrzymają lepsze ostrzeżenia, które otrzymają użytkownicy interfejsu API. Zacznijmy od znanego przykładu. Wyobraź sobie, że biblioteka ma następujący interfejs API do pobierania ciągu zasobu:

```csharp
bool TryGetMessage(string key, out string message)
```

W poprzednim przykładzie `Try*` następuje znane wzorzec w .NET. Istnieją dwa argumenty odwołania dla `key` tego `message` interfejsu API: i parametr. Ten interfejs API ma następujące reguły odnoszące się do nieważności tych argumentów:

- Dzwoniący nie powinni `null` przechodzić `key`jako argument dla .
- Osoby dzwoniące mogą przekazać `null` zmienną, `message`której wartość jest argumentem dla .
- Jeśli `TryGetMessage` metoda `true`zwraca , `message` wartość nie jest null. Jeśli zwracana `false,` wartość jest `message` wartością (a jej stan zerowy) jest null.

Reguła `key` dla może być całkowicie wyrażona `key` przez typ zmiennej: powinien być typem odwołania nienastępnego. Parametr `message` jest bardziej złożony. Pozwala `null` jako argument, ale gwarantuje, że `out` na sukces, że argument nie jest null. W przypadku tych scenariuszy potrzebujesz bogatszego słownictwa, aby opisać oczekiwania.

Aktualizowanie biblioteki dla odwołań nullable wymaga `?` więcej niż posypywanie na niektóre zmienne i nazwy typów. W poprzednim przykładzie pokazano, że należy zbadać interfejsy API i należy wziąć pod uwagę oczekiwania dla każdego argumentu wejściowego. Należy wziąć pod uwagę gwarancje `out` dla `ref` wartości zwracanej i wszelkie lub argumenty po powrocie metody. Następnie komunikować te reguły do kompilatora, a kompilator zapewni ostrzeżenia, gdy wywołania nie są zgodne z tymi regułami.

Ta praca wymaga czasu. Zacznijmy od strategii, aby biblioteka lub aplikacja nullable-aware, przy jednoczesnym równoważeniu innych wymagań i ujednolików. Zobaczysz, jak zrównoważyć bieżące gonie, umożliwiając typy odwołań powodujących wartość null. Poznasz wyzwania dotyczące definicji typów ogólnych. Nauczysz się stosować atrybuty do opisywania warunków wstępnych i postowych w poszczególnych interfejsach API.

## <a name="choose-a-strategy-for-nullable-reference-types"></a>Wybieranie strategii dla typów odwołań z dopuszczaniem do wartości null

Pierwszym wyborem jest to, czy typy odwołań nullable powinny być domyślnie włączone lub wyłączone. Masz dwie strategie:

- Włącz typy odwołań nullable dla całego projektu i wyłącz go w kodzie, który nie jest gotowy.
- Włącz tylko typy odwołań z nullable dla kodu, który został o astowany dla typów odwołań zdatnymi do wartości null.

Pierwsza strategia działa najlepiej podczas dodawania innych funkcji do biblioteki podczas aktualizowania go dla typów odwołań, których można anulować. Wszystkie nowe rozwoju jest nullable świadomość. Podczas aktualizowania istniejącego kodu, można włączyć nullable typy odwołań w tych klasach.

Zgodnie z tą pierwszą strategią wykonaj następujące czynności:

1. Włącz typy odwołań nullable dla `<Nullable>enable</Nullable>` całego projektu, dodając element do plików *csproj.*
1. Dodaj `#nullable disable` pragmę do każdego pliku źródłowego w projekcie.
1. Podczas pracy nad każdym plikiem usuń pragmę i zaaminuj wszelkie ostrzeżenia.

Ta pierwsza strategia ma więcej pracy z góry, aby dodać pragmy do każdego pliku. Zaletą jest to, że każdy nowy plik kodu dodany do projektu będzie nullable włączone. Wszelkie nowe prace będą nieważne świadomość; tylko istniejący kod musi zostać zaktualizowany.

Druga strategia działa lepiej, jeśli biblioteka jest ogólnie stabilna, a głównym celem rozwoju jest przyjęcie typów odwołań do nullable. Typy odwołań z których można wyłączyć z wartościami null, podczas dodawać adnotacje do interfejsów API. Po zakończeniu można włączyć typy odwołań nullable dla całego projektu.

Zgodnie z tą drugą strategią wykonujesz następujące czynności:

1. Dodaj `#nullable enable` pragmę do pliku, który chcesz zgłosić do null.
1. Usuń wszelkie ostrzeżenia.
1. Kontynuuj te dwa pierwsze kroki, dopóki nie dowiesz się, że cała biblioteka jest nieuprawniona.
1. Włącz typy nullable dla całego `<Nullable>enable</Nullable>` projektu, dodając element do plików *csproj.*
1. Usuń `#nullable enable` pragmy, ponieważ nie są już potrzebne.

Ta druga strategia ma mniej pracy z góry. Kompromisem jest to, że pierwszym zadaniem podczas tworzenia nowego pliku jest dodanie pragmy i uczynienie go nullable aware. Jeśli deweloperzy w zespole zapomnieć, że nowy kod jest teraz w zaległości pracy, aby wszystkie kodu nullable świadomość.

Która z tych strategii zostanie wybrasza, zależy od tego, jak bardzo aktywny rozwój odbywa się w twoim projekcie. Im bardziej dojrzały i stabilny projekt, tym lepsza druga strategia. Im więcej funkcji jest opracowywanych, tym lepsza jest pierwsza strategia.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Czy ostrzeżenia o unieważnianiu powinny powodować zmiany w przerwaniu?

Przed włączeniem typów odwołań do wartości null, zmienne są uważane za *nullable oblivious*. Po włączeniu typów odwołań zable null, wszystkie te zmienne są *niemożna null .* Kompilator wyda ostrzeżenia, jeśli te zmienne nie są inicjowane do wartości innych niż null.

Innym prawdopodobnym źródłem ostrzeżeń są zwracane wartości, gdy wartość nie została zainicjowana.

Pierwszym krokiem w adresowaniu ostrzeżeń `?` kompilatora jest użycie adnotacji na typy parametrów i zwracać, aby wskazać, kiedy argumenty lub zwraca wartości mogą być null. Gdy zmienne odwołania nie może być null, oryginalna deklaracja jest poprawna. Jak to zrobić, Twoim celem nie jest tylko naprawić ostrzeżenia. Ważniejszym celem jest, aby kompilator zrozumieć intencji dla potencjalnych wartości null. Podczas badania ostrzeżeń, można osiągnąć następną ważną decyzję dla biblioteki. Czy chcesz rozważyć zmodyfikowanie podpisów interfejsu API, aby lepiej komunikować intencje projektu? Lepszy podpis interfejsu `TryGetMessage` API dla metody badanej wcześniej może być:

```csharp
string? TryGetMessage(string key);
```

Zwracana wartość wskazuje sukces lub niepowodzenie i przenosi wartość, jeśli wartość została znaleziona. W wielu przypadkach zmiana podpisów interfejsu API może poprawić sposób przekazywania wartości null.

Jednak w przypadku bibliotek publicznych lub bibliotek z dużymi bazami użytkowników może wolisz nie wprowadzać żadnych zmian podpisu interfejsu API. W tych przypadkach i innych typowych wzorcach można zastosować atrybuty, aby jaśniej `null`zdefiniować, kiedy argument lub wartość zwracana może być . Niezależnie od tego, czy rozważasz zmianę powierzchni interfejsu API, prawdopodobnie okaże się, że `null` same adnotacje typu nie są wystarczające do opisywania wartości argumentów lub zwracanych wartości. W tych przypadkach można zastosować atrybuty, aby jaśniej opisać interfejs API.

## <a name="attributes-extend-type-annotations"></a>Atrybuty rozszerzają adnotacje typów

Dodano kilka atrybutów, aby wyrazić dodatkowe informacje o stanie null zmiennych. Cały kod, który napisałeś przed C# 8 wprowadzone nullable typy odwołań był *null oblivious*. Oznacza to, że każda zmienna typu odwołania może mieć wartość null, ale nie są wymagane kontrole wartości null. Gdy kod jest *nullable aware*, te reguły zmienić. Typy odwołań `null` nigdy nie powinny być wartością, `null` a typy odwołań do wartości null muszą być sprawdzane przed odwołaniem.

Reguły interfejsów API są prawdopodobnie bardziej skomplikowane, `TryGetValue` jak widać w scenariuszu interfejsu API. Wiele interfejsów API ma bardziej złożone reguły, gdy zmienne mogą lub nie mogą być `null`. W takich przypadkach do wyrażenia tych reguł użyjesz jednego z następujących atrybutów:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy nienastępny do wartości null może mieć wartość null.
- [NieuprawnionyNull:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Nullable argument wejściowy nigdy nie powinien być null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana bez wartości null może być wartość null.
- [NotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)Nullable wartość zwracana nigdy nie będzie null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy nienastępny do wartości `bool` null może mieć wartość null, gdy metoda zwraca określoną wartość.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do null nie będzie `bool` null, gdy metoda zwraca określoną wartość.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Zwracana wartość nie jest zerowa, jeśli argument dla określonego parametru nie jest null.

Powyższe opisy są szybkie odwołanie do tego, co każdy atrybut nie. W każdej poniższej sekcji opisano zachowanie i znaczenie dokładniej.

Dodanie tych atrybutów daje kompilatorowi więcej informacji na temat reguł dla interfejsu API. Podczas wywoływania kodu jest kompilowany w kontekście z obsługą nullable włączone, kompilator będzie ostrzegać wywoływaczy, gdy naruszają te reguły. Te atrybuty nie umożliwiają dodatkowych kontroli implementacji.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Określ warunki wstępne: `AllowNull` i`DisallowNull`

Należy wziąć pod uwagę właściwość odczytu/zapisu, która nigdy nie zwraca, `null` ponieważ ma rozsądną wartość domyślną. Wywołujący `null` przechodzą do zestawu akcesora podczas ustawiania go do tej wartości domyślnej. Rozważmy na przykład system obsługi wiadomości, który prosi o nazwę ekranu w pokoju rozmów. Jeśli nie podano, system generuje losową nazwę:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Podczas kompilowania poprzedniego kodu w kontekście nullable nieświadomy, wszystko jest w porządku. Po włączeniu typów odwołań `ScreenName` nullable, właściwość staje się odwołanie nie nullable. To jest poprawne `get` dla akcesora: nigdy nie zwraca `null`. Dzwoniący nie muszą sprawdzać zwracane `null`właściwość dla . Ale teraz ustawienie `null` właściwości, aby wygenerować ostrzeżenie. Aby nadal obsługiwać ten typ kodu, <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> należy dodać atrybut do właściwości, jak pokazano w poniższym kodzie:

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Może być konieczne `using` dodanie <xref:System.Diagnostics.CodeAnalysis> dyrektywy, aby użyć tego i innych atrybutów omówionych w tym artykule. Atrybut jest stosowany do właściwości, a `set` nie akcesora. Atrybut `AllowNull` określa *warunki wstępne*i ma zastosowanie tylko do danych wejściowych. Akcesor `get` ma wartość zwracaną, ale nie ma argumentów wejściowych. W związku `AllowNull` z tym atrybut dotyczy `set` tylko akcesora.

W poprzednim przykładzie pokazano, na co `AllowNull` zwrócić uwagę podczas dodawania atrybutu w argurze:

1. Ogólna umowa dla tej zmiennej jest, że nie powinno być `null`, więc chcesz typu odwołania nie nullable.
1. Istnieją scenariusze dla zmiennej `null`wejściowej, które mają być, choć nie są one najczęściej użycia.

Najczęściej ten atrybut jest potrzebny dla właściwości `in`lub `out`, `ref` i argumentów. Atrybut `AllowNull` jest najlepszym wyborem, gdy zmienna jest zazwyczaj nie null, ale należy zezwolić `null` jako warunek wstępny.

Kontrast, który ze `DisallowNull`scenariuszami użycia: Ten atrybut służy do określania, że zmienną `null`wejściową typu odwołania z dopuszczalną wartością null nie powinna być . Należy wziąć `null` pod uwagę właściwość, gdzie jest wartością domyślną, ale klienci mogą tylko ustawić ją na wartość nietrwałą. Spójrzmy na poniższy kod:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Powyższy kod jest najlepszym sposobem wyrażenia projektu, który `ReviewComment` może być, `null`ale `null`nie można ustawić na . Gdy ten kod jest nullable pamiętać, można wyrazić tę <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>koncepcję jaśniej do rozmówców za pomocą:

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

W kontekście `ReviewComment` `get` możliwego do anulowania akcesor może zwrócić wartość domyślną `null`programu . Kompilator ostrzega, że należy sprawdzić przed dostępem. Co więcej, ostrzega dzwoniących, że nawet `null`jeśli może to być , `null`dzwoniący nie powinni wyraźnie ustawić go na . Atrybut `DisallowNull` określa również *warunek wstępny*, nie wpływa `get` na akcesor. Należy użyć atrybutu, `DisallowNull` gdy obserwujesz następujące cechy dotyczące:

1. Zmienna może `null` znajdować się w podstawowych scenariuszach, często podczas pierwszego wystąpienia.
1. Zmienna nie powinna być jawnie ustawiona na `null`.

Te sytuacje są powszechne w kodzie, który pierwotnie *null oblivious*. Może się okazać, że właściwości obiektu są ustawione w dwóch różnych operacji inicjowania. Może się okazać, że niektóre właściwości są ustawiane tylko po zakończeniu niektórych prac asynchronicznych.

`AllowNull` Atrybuty `DisallowNull` i umożliwiają określenie, że warunki wstępne dla zmiennych mogą nie odpowiadać adnotacjami nullable dla tych zmiennych. Zapewniają one więcej szczegółów na temat cech interfejsu API. Te dodatkowe informacje pomagają wywołującym poprawnie używać interfejsu API. Pamiętaj, że określono warunki wstępne przy użyciu następujących atrybutów:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy nienastępny do wartości null może mieć wartość null.
- [NieuprawnionyNull:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Nullable argument wejściowy nigdy nie powinien być null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Określ warunki `MaybeNull` post: i`NotNull`

Załóżmy, że masz metodę z następującym podpisem:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Prawdopodobnie napisałeś taką metodę, aby `null` powrócić, gdy poszukiwana nazwa nie została znaleziona. Wyraźnie `null` wskazuje, że rekord nie został znaleziony. W tym przykładzie prawdopodobnie zmienisz typ `Customer` `Customer?`zwracany z na . Deklarowanie wartości zwracanej jako typu odwołania powodującego wartość null określa intencję tego interfejsu API.

Z przyczyn objętych [definicjami rodzajowymi i niemożnością użycia](#generic-definitions-and-nullability) ta technika nie działa z metodami ogólnymi. Może być metoda rodzajowa, która następuje podobny wzorzec:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Nie można określić, że `T?`zwracana jest wartość . Metoda zwraca, `null` gdy nie znaleziono poszukiwanego elementu. Ponieważ nie można zadeklarować typu zwracanego, `T?` należy dodać `MaybeNull` adnotację do zwracania metody:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Powyższy kod informuje wywołujących, że umowa implikuje typ nienależyte do null, ale wartość *zwracana może* być rzeczywiście null.  Użyj `MaybeNull` atrybutu, gdy interfejs API powinien być typem nienastępnym do wartości null, `null` zazwyczaj parametrem typu ogólnego, ale mogą występować wystąpienia, w których zostaną zwrócone.

Można również określić, że `out` wartość `ref` zwracana lub argument lub nie jest null, nawet jeśli typ jest typem odwołania z dopuszczalną wartością null. Należy wziąć pod uwagę metodę, która zapewnia tablicy jest wystarczająco duży, aby pomieścić wiele elementów. Jeśli argument wejściowy nie ma pojemności, procedura będzie przydzielić nową tablicę i skopiować wszystkie istniejące elementy do niego. Jeśli argument input `null`jest , procedura będzie przydzielić nowy magazyn. Jeśli istnieje wystarczająca pojemność, procedura nie robi nic:

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

Po włączeniu typów odwołań null, chcesz upewnić się, że poprzedni kod kompiluje się bez ostrzeżeń. Gdy metoda zwraca, `storage` argument jest gwarantowane nie null. Jednak jest dopuszczalne, `EnsureCapacity` aby wywołać z odwołaniem null. Można wprowadzić `storage` typ odwołania z dopuszczalną `NotNull` wartością null i dodać warunek post do deklaracji parametrów:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Powyższy kod wyraża istniejącą umowę bardzo wyraźnie: wywołujący mogą `null` przekazać zmienną z wartością, ale wartość zwracana jest gwarantowana, że nigdy nie będzie null. Atrybut `NotNull` jest najbardziej przydatne `ref` `out` dla `null` i argumenty, gdzie mogą być przekazywane jako argument, ale ten argument jest gwarantowane nie jest null, gdy zwraca metodę.

Bezwarunkowe warunki postwarunkowe można określić przy użyciu następujących atrybutów:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana bez wartości null może być wartość null.
- [NotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)Nullable wartość zwracana nigdy nie będzie null.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Określ warunkowe warunki `NotNullWhen` `MaybeNullWhen`post:, , i`NotNullIfNotNull`

Prawdopodobnie znasz `string` metodę <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>. Ta metoda `true` zwraca, gdy argument ma wartość null lub pusty ciąg. Jest to forma sprawdzania wartości null: osoby dzwoniące nie muszą sprawdzać wartości `false`null, jeśli metoda zwraca . Aby metoda taka jak ta nullable świadomość, należy ustawić argument do typu `NotNullWhen` odwołania nullable i dodać atrybut:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Informuje kompilator, że każdy kod, `false` w którym jest wartość zwracana, nie musi być sprawdzany z wartością null. Dodanie atrybutu informuje analizę statyczną kompilatora, `IsNullOrEmpty` która wykonuje niezbędne sprawdzanie wartości `false`null: po `null`powrocie argument input nie jest .

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

Metoda <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> zostanie oznaczona jako pokazano powyżej dla .NET Core 3.0. Może mieć podobne metody w bazie kodu, które sprawdzają stan obiektów dla wartości null. Kompilator nie rozpoznaje niestandardowych metod sprawdzania wartości null i musisz samodzielnie dodać adnotacje. Po dodaniu atrybutu, analiza statyczna kompilatora wie, kiedy testowana zmienna została sprawdzona wartość null.

Innym zastosowaniem `Try*` dla tych atrybutów jest wzorzec. Warunki powarunkowe `ref` `out` i zmienne są przekazywane za pośrednictwem wartości zwracanej. Należy wziąć pod uwagę tę metodę pokazano wcześniej:

```csharp
bool TryGetMessage(string key, out string message)
```

Poprzednia metoda jest zgodna z typowym idiomem `message` .NET: zwracana wartość wskazuje, czy została ustawiona na znalezioną wartość lub, jeśli nie zostanie znaleziony żaden komunikat, do wartości domyślnej. Jeśli metoda `true`zwraca , `message` wartość nie jest null; w przeciwnym razie `message` metoda ustawia wartość null.

Można przekazać, że idiom przy użyciu atrybutu. `NotNullWhen` Podczas aktualizowania podpisu dla typów `message` odwołań, których można unieważnić, należy wykonać `string?` i dodać atrybut:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

W poprzednim przykładzie wartość `message` jest znana jako nie `TryGetMessage` `true`null podczas zwraca . Podobne metody w bazie kodu należy dodawać adnotacje w `null`taki sam sposób: argumenty mogą `true`być i są znane jako nie null, gdy metoda zwraca .

Istnieje jeden atrybut końcowy, który może być również potrzebny. Czasami stan zerowy wartości zwracanej zależy od stanu zerowego jednego lub więcej argumentów wejściowych. Metody te zwracają wartość nie null, gdy pewne `null`argumenty wejściowe nie są . Aby poprawnie dodawać adnotacje `NotNullIfNotNull` do tych metod, należy użyć atrybutu. Należy wziąć pod uwagę następującą metodę:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Jeśli `url` argument nie jest null, dane `null`wyjściowe nie jest . Po włączeniu odwołań nullable, że podpis działa poprawnie, pod warunkiem, że interfejs API nigdy nie akceptuje null danych wejściowych. Jednak jeśli dane wejściowe może być null, a następnie zwraca wartość może być również null. W związku z tym można zmienić podpis na następujący kod:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

To również działa, ale często zmusza `null` dzwoniących do wdrożenia dodatkowych kontroli. Umowa jest taka, że `null` wartość zwracana `url` będzie `null`tylko wtedy, gdy argument wejściowy jest . Aby wyrazić tę umowę, należy opisać tę metodę, jak pokazano w poniższym kodzie:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Wartość zwracana i argument zostały oś `?` tym adnotacje ze `null`wskazaniem, że albo może być . Atrybut dalej wyjaśnia, że wartość zwracana nie będzie `url` null, `null`gdy argument nie jest .

Warunkowe warunki postconditions przy użyciu tych atrybutów:

- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy nienastępny do wartości `bool` null może mieć wartość null, gdy metoda zwraca określoną wartość.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do null nie będzie `bool` null, gdy metoda zwraca określoną wartość.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Zwracana wartość nie jest zerowa, jeśli argument wejściowy dla określonego parametru nie jest null.

## <a name="generic-definitions-and-nullability"></a>Definicje ogólne i możliwość niemożności

Prawidłowe komunikowanie stanu null typów ogólnych i metod ogólnych wymaga szczególnej ostrożności. Wynika to z faktu, że typ wartości nullable i typ odwołania nullable są zasadniczo różne. An `int?` jest synonimem `Nullable<int>`, `string?` mając `string` na uwadze, że jest z atrybutem dodanym przez kompilator. Wynik jest, że kompilator nie może `T?` wygenerować poprawny kod bez wiedząc, czy `T` jest `class` lub . `struct`

Nie oznacza to, że nie można użyć typu nullable (typ wartości lub typ odwołania) jako argumentu typu dla zamkniętego typu ogólnego. Oba `List<string?>` `List<int?>` i są prawidłowe `List<T>`wystąpienia .

Oznacza to, że nie można `T?` używać w deklaracji klasy lub metody rodzajowej bez ograniczeń. Na przykład <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> nie zostanie zmieniona, aby powrócić `T?`. Można przezwyciężyć to ograniczenie, `struct` dodając `class` albo ograniczenia. Z jednym z tych ograniczeń, kompilator wie, `T` jak `T?`wygenerować kod dla obu i .

Można ograniczyć typy używane dla argumentu typu ogólnego, aby były typami nienastępulnymi wartością null. Można to zrobić, `notnull` dodając ograniczenie do tego argumentu typu. Po zastosowaniu tego ograniczenia argument typu nie może być typem do null.

## <a name="conclusions"></a>Wnioski

Dodawanie typów odwołań do wartości nullable zapewnia początkowe słownictwo opisujące `null`oczekiwania interfejsów API dla zmiennych, które mogą być . Dodatkowe atrybuty zapewniają bogatsze słownictwo do opisania stanu null zmiennych jako warunków wstępnych i postconditions. Te atrybuty jaśniej opisują twoje oczekiwania i zapewniają lepsze środowisko dla deweloperów korzystających z interfejsów API.

Podczas aktualizowania bibliotek dla kontekstu możliwego do podenia, dodaj te atrybuty, aby poprowadzić użytkowników interfejsów API do prawidłowego użycia. Te atrybuty pomagają w pełni opisać zerowy stan argumentów wejściowych i zwracać wartości:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy nienastępny do wartości null może mieć wartość null.
- [NieuprawnionyNull:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Nullable argument wejściowy nigdy nie powinien być null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana bez wartości null może być wartość null.
- [NotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)Nullable wartość zwracana nigdy nie będzie null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy nienastępny do wartości `bool` null może mieć wartość null, gdy metoda zwraca określoną wartość.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do null nie będzie `bool` null, gdy metoda zwraca określoną wartość.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Zwracana wartość nie jest zerowa, jeśli argument wejściowy dla określonego parametru nie jest null.
