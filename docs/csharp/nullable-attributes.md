---
title: Uaktualnianie interfejsów API dla typów odwołań z wartościami null z atrybutami definiującymi oczekiwania dotyczące wartości null
description: Dowiedz się, aby użyć atrybutów opisowych AllowNull, DisallowNull, MaybeNull, NotNull i więcej, aby w pełni opisać stan zerowy interfejsów API.
ms.technology: csharp-null-safety
ms.date: 07/31/2019
ms.openlocfilehash: a4b1f851bcbe27dd4884d45eb6d1209ab54271d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79170363"
---
# <a name="update-libraries-to-use-nullable-reference-types-and-communicate-nullable-rules-to-callers"></a>Aktualizowanie bibliotek w celu używania typów odwołań z możliwością null i przekazywania reguł nullable do wywoływania

Dodanie [typów odwołań nullable](nullable-references.md) oznacza, że `null` można zadeklarować, czy wartość jest dozwolona lub oczekiwana dla każdej zmiennej. Ponadto można zastosować szereg `AllowNull`atrybutów: , `DisallowNull` `MaybeNull`, `NotNull` `NotNullWhen`, `MaybeNullWhen`, `NotNullWhenNotNull` , i całkowicie opisać stany null argumentu i wartości zwracanych. Zapewnia to wspaniałe doświadczenie podczas pisania kodu. Otrzymujesz ostrzeżenia, jeśli zmienna niepodlegająca `null`null może być ustawiona na . Otrzymasz ostrzeżenia, jeśli zmienna nullable nie jest sprawdzana wartości null przed wyłusk iem. Aktualizacja bibliotek może zająć trochę czasu, ale wypłaty są tego warte. Im więcej informacji podasz kompilatorowi o *tym, kiedy* `null` wartość jest dozwolona lub zabroniona, tym lepsze ostrzeżenia użytkownicy interfejsu API otrzymają. Zacznijmy od znajomego przykładu. Wyobraź sobie, że biblioteka ma następujący interfejs API do pobrania ciągu zasobu:

```csharp
bool TryGetMessage(string key, out string message)
```

W poprzednim przykładzie następuje `Try*` znany wzorzec w .NET. Istnieją dwa argumenty odniesienia dla `key` tego `message` interfejsu API: i parametr. Ten interfejs API ma następujące reguły odnoszące się do nieważności tych argumentów:

- Obiekty wywołujące nie `null` powinny przechodzić jako argument dla `key`.
- Obiekty wywołujące mogą przekazać `null` zmienną, `message`której wartość jest argumentem dla .
- Jeśli `TryGetMessage` metoda `true`zwraca, wartość `message` nie jest null. Jeśli wartość zwracana `false,` jest `message` wartością (i jej stan null) jest null.

Reguła `key` dla może być całkowicie wyrażona `key` przez typ zmiennej: powinien być typem odwołania niepodlegającym null. Parametr `message` jest bardziej złożony. Pozwala `null` jako argument, ale gwarantuje, że `out` na sukces, że argument nie jest null. W przypadku tych scenariuszy potrzebujesz bogatszego słownictwa, aby opisać oczekiwania.

Aktualizowanie biblioteki dla odwołań nullwymaga więcej `?` niż pokropienie na niektórych zmiennych i nazw typów. W poprzednim przykładzie pokazano, że należy zbadać interfejsy API i rozważyć swoje oczekiwania dla każdego argumentu wejściowego. Należy wziąć pod uwagę gwarancje `out` dla `ref` wartości zwracanej i wszelkie lub argumenty na powrót metody. Następnie przekaż te reguły do kompilatora, a kompilator zapewni ostrzeżenia, gdy obiekty wywołujące nie przestrzegają tych reguł.

Ta praca wymaga czasu. Zacznijmy od strategii, aby biblioteki lub aplikacji nullable-aware, przy jednoczesnym równoważeniu innych wymagań i rezultatów. Zobaczysz, jak zrównoważyć bieżącego rozwoju, umożliwiając nullable typy odwołań. Nauczysz się wyzwań związanych z definicjami typów ogólnych. Dowiesz się, aby zastosować atrybuty do opisania warunków przed i po na poszczególnych interfejsów API.

## <a name="choose-a-nullable-strategy"></a>Wybierz strategię unieważnialną

Pierwszym wyborem jest, czy typy odwołań null powinny być domyślnie włączone lub wyłączone. Masz dwie strategie:

- Włącz typy odwołań z możliwością null dla całego projektu i wyłącz go w kodzie, który nie jest gotowy.
- Włącz tylko typy odwołań null able dla kodu, który został odany adnotatorem dla typów odwołań nullable.

Pierwsza strategia działa najlepiej podczas dodawania innych funkcji do biblioteki podczas aktualizowania jej dla typów odwołań z możliwością null. Wszystkie nowe programistycznych jest nullable świadomość. Podczas aktualizowania istniejącego kodu można włączyć typy odwołań nullable w tych klasach.

Po tej pierwszej strategii, należy wykonać następujące czynności:

1. Włącz typy nullable dla całego `<Nullable>enable</Nullable>` projektu, dodając element do plików *csproj.*
1. Dodaj `#nullable disable` pragma do każdego pliku źródłowego w projekcie.
1. Podczas pracy nad każdym plikiem usuń pragmę i zajmij się ostrzeżeniami.

Ta pierwsza strategia ma więcej pracy z góry, aby dodać pragma do każdego pliku. Zaletą jest to, że każdy nowy plik kodu dodany do projektu będzie możliwy do zwyżek. Każda nowa praca będzie nullable świadomość; tylko istniejący kod musi zostać zaktualizowany.

Druga strategia działa lepiej, jeśli biblioteka jest ogólnie stabilna, a głównym celem rozwoju jest przyjęcie typów odwołań z możliwością null. Można włączyć typy odwołań nullable jak adnotować interfejsy API. Po zakończeniu można włączyć typy odwołań nullable dla całego projektu.

Po tej drugiej strategii można wykonać następujące czynności:

1. Dodaj `#nullable enable` pragma do pliku, który ma być świadomy wartości null.
1. Zajmij się ostrzeżeniami.
1. Kontynuuj te pierwsze dwa kroki, aż cała biblioteka będzie świadoma wartości null.
1. Włącz typy nullable dla całego `<Nullable>enable</Nullable>` projektu, dodając element do plików *csproj.*
1. Usuń `#nullable enable` pragmy, ponieważ nie są już potrzebne.

Ta druga strategia ma mniej pracy z góry. Kompromis jest, że pierwsze zadanie podczas tworzenia nowego pliku jest dodanie pragma i uczynić go nullable świadomość. Jeśli deweloperzy w zespole zapomnieć, że nowy kod jest teraz w zaległości pracy, aby wszystkie kodu nullable świadomość.

To, którą z tych strategii wybierzesz, zależy od tego, ile aktywnego rozwoju ma miejsce w twoim projekcie. Im bardziej dojrzały i stabilny projekt, tym lepsza jest druga strategia. Im więcej funkcji jest opracowywanych, tym lepsza jest pierwsza strategia.

## <a name="should-nullable-warnings-introduce-breaking-changes"></a>Czy ostrzeżenia nullable wprowadzić zmiany krytyczne?

Przed włączeniu typów odwołań nullable, zmienne są uważane za *nullable oblivious*. Po włączeniu typów odwołań nullable wszystkie te zmienne są *nienullable*. Kompilator będzie wydawać ostrzeżenia, jeśli te zmienne nie są inicjowane do wartości innych niż null.

Innym prawdopodobnym źródłem ostrzeżeń jest zwracanie wartości, gdy wartość nie została zainicjowana.

Pierwszym krokiem w rozwiązywaniu ostrzeżenia kompilatora jest użycie `?` adnotacji na typy parametrów i zwracania, aby wskazać, kiedy argumenty lub wartości zwracane mogą być null. Gdy zmienne odniesienia nie mogą być null, oryginalna deklaracja jest poprawna. W ten sposób Twoim celem nie jest tylko naprawianie ostrzeżeń. Ważniejszym celem jest, aby kompilator zrozumieć zamiar potencjalnych wartości null. Podczas badania ostrzeżeń można dojść do następnej ważnej decyzji dla swojej biblioteki. Czy chcesz rozważyć zmodyfikowanie podpisów interfejsu API, aby wyraźniej komunikować zamiar projektu? Lepszy podpis interfejsu API dla `TryGetMessage` metody badanej wcześniej może być:

```csharp
string? TryGetMessage(string key);
```

Wartość zwracana wskazuje sukces lub niepowodzenie i przenosi wartość, jeśli wartość została znaleziona. W wielu przypadkach zmiana podpisów interfejsu API może poprawić sposób komunikowania wartości null.

Jednak w przypadku bibliotek publicznych lub bibliotek z dużymi bazami użytkowników może wolisz nie wprowadzać żadnych zmian podpisu interfejsu API. W tych przypadkach i innych typowych wzorców można zastosować atrybuty do bardziej `null`jasnego zdefiniowania, kiedy może być argument lub wartość zwracana . Niezależnie od tego, czy rozważysz zmianę powierzchni interfejsu API, prawdopodobnie okaże się, że `null` same adnotacje typu nie są wystarczające do opisywania wartości argumentów lub zwracanych wartości. W takich przypadkach można zastosować atrybuty do bardziej wyraźnie opisać interfejs API.

## <a name="attributes-extend-type-annotations"></a>Atrybuty rozszerzają adnotacje typów

Dodano kilka atrybutów, aby wyrazić dodatkowe informacje o stanie zeru zmiennych. Cały kod, który napisałeś przed wprowadzeniem c# 8 typów odwołań nullable był *null oblivious*. Oznacza to, że każda zmienna typu odwołania może mieć wartość null, ale kontrole wartości null nie są wymagane. Gdy kod jest *nullable świadomość,* te reguły zmienić. Typy odwołań nigdy `null` nie powinny być wartością, a `null` typy odwołań o wartości null muszą być sprawdzane przed wyłuskiem.

Reguły dla interfejsów API są prawdopodobnie bardziej `TryGetValue` skomplikowane, jak widać w scenariuszu interfejsu API. Wiele interfejsów API ma bardziej złożone reguły, gdy `null`zmienne mogą lub nie mogą być . W takich przypadkach do wyrażenia tych reguł należy użyć jednego z następujących atrybutów:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy niepodlegający null może mieć wartość null.
- [NiedzallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy nullnie powinien nigdy nie być null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana niepodlegająca null może być null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Wartość zwracana null nigdy nie będzie null.
- [MaybeNullWhen:](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)Argument wejściowy niepodlegający null może mieć wartość null, gdy metoda zwraca określoną `bool` wartość.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy z wartością null nie będzie `bool` null, gdy metoda zwraca określoną wartość.
- [NotNullIfNotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)Wartość zwracana nie jest null, jeśli argument dla określonego parametru nie jest null.

Powyższe opisy są szybkie odwołanie do tego, co każdy atrybut robi. W każdej z poniższych sekcji opisano zachowanie i znaczenie dokładniej.

Dodawanie tych atrybutów daje kompilatorowi więcej informacji o regułach dla interfejsu API. Podczas wywoływania kodu jest kompilowany w kontekście z włączoną wartością null, kompilator ostrzega wywoływania, gdy naruszają te reguły. Te atrybuty nie umożliwiają dodatkowych kontroli implementacji.

## <a name="specify-preconditions-allownull-and-disallownull"></a>Określ warunki `AllowNull` wstępne: i`DisallowNull`

Należy wziąć pod uwagę read/write właściwości, która nigdy nie zwraca, `null` ponieważ ma rozsądną wartość domyślną. Obiekty wywołujące przechodzą `null` do set akcesor podczas ustawiania go do tej wartości domyślnej. Rozważmy na przykład system obsługi wiadomości, który prosi o nazwę ekranu w pokoju rozmów. Jeśli nie podano, system generuje losową nazwę:

```csharp
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName;
```

Podczas kompilowania poprzedniego kodu w kontekście nullable nieświadomych, wszystko jest w porządku. Po włączeniu typów odwołań `ScreenName` nullable właściwość staje się odwołanie niedopuszczające wartości null. To jest poprawne `get` dla akcesora: nigdy nie zwraca `null`. Obiekty wywołujące nie muszą sprawdzać zwróconej właściwości dla `null`pliku . Ale teraz ustawienie `null` właściwości generuje ostrzeżenie. Aby kontynuować obsługę tego typu kodu, <xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute?displayProperty=nameWithType> należy dodać atrybut do właściwości, jak pokazano w następującym kodzie:

```csharp
[AllowNull]
public string ScreenName
{
   get => screenName;
   set => screenName = value ?? GenerateRandomScreenName();
}
private string screenName = GenerateRandomScreenName();
```

Może być konieczne `using` dodanie <xref:System.Diagnostics.CodeAnalysis> dyrektywy do użycia tego i innych atrybutów omówione w tym artykule. Atrybut jest stosowany do właściwości, `set` a nie akcesor. Atrybut `AllowNull` określa *warunki wstępne*i ma zastosowanie tylko do danych wejściowych. Akcesor `get` ma wartość zwracaną, ale nie ma argumentów wejściowych. W związku `AllowNull` z tym atrybut `set` dotyczy tylko akcesor.

W poprzednim przykładzie pokazano, czego szukać `AllowNull` podczas dodawania atrybutu na argument:

1. Ogólny kontrakt dla tej zmiennej jest, `null`że nie powinno być , więc chcesz niedopuszczający wartości null typu odwołania.
1. Istnieją scenariusze zmiennej wejściowej `null`być , choć nie są one najczęściej używane.

Najczęściej ten atrybut jest potrzebny do właściwości `in` `out`lub `ref` , i argumentów. Atrybut `AllowNull` jest najlepszym wyborem, gdy zmienna jest zazwyczaj non-null, ale należy zezwolić `null` jako warunek wstępny.

Kontrast, że ze `DisallowNull`scenariuszami do korzystania : Należy użyć tego atrybutu, aby `null`określić, że zmienna wejściowa typu nullnie powinny być . Należy wziąć `null` pod uwagę właściwość, gdzie jest wartością domyślną, ale klienci mogą ustawić go tylko na wartość nienull. Spójrzmy na poniższy kod:

```csharp
public string ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string _comment;
```

Poprzedni kod jest najlepszym sposobem, aby wyrazić swój projekt, że `ReviewComment` może być `null`, ale nie można ustawić . `null` Gdy ten kod jest nullable świadomość, można wyrazić <xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute?displayProperty=nameWithType>tę koncepcję jaśniej do wywoływania za pomocą :

```csharp
[DisallowNull]
public string? ReviewComment
{
    get => _comment;
    set => _comment = value ?? throw new ArgumentNullException(nameof(value), "Cannot set to null");
}
string? _comment;
```

W kontekście nullable `ReviewComment` `get` akcesor może `null`zwrócić wartość domyślną . Kompilator ostrzega, że musi być sprawdzony przed dostępem. Ponadto ostrzega dzwoniących, że nawet jeśli `null`może to być , dzwoniący `null`nie powinny jawnie ustawić go . Atrybut `DisallowNull` określa również *warunek wstępny*, nie `get` ma wpływu na akcesor. Należy wybrać, aby `DisallowNull` użyć atrybutu, gdy zaobserwujesz te cechy dotyczące:

1. Zmienna może `null` być w podstawowych scenariuszach, często po pierwszym uprzedzeniu.
1. Zmienna nie powinna być jawnie ustawiona na `null`.

Sytuacje te są powszechne w kodzie, który pierwotnie był *null oblivious*. Może się okazać, że właściwości obiektu są ustawione w dwóch odrębnych operacjach inicjowania. Może się okazać, że niektóre właściwości są ustawiane dopiero po zakończeniu niektórych prac asynchronicznych.

`AllowNull` Atrybuty `DisallowNull` i umożliwiają określenie, że warunki wstępne zmiennych mogą nie odpowiadać adnotacjom wartości null dla tych zmiennych. Zapewniają one więcej szczegółów na temat właściwości interfejsu API. Te dodatkowe informacje ułatwiają wywołującym poprawnie korzystać z interfejsu API. Pamiętaj, że określasz warunki wstępne przy użyciu następujących atrybutów:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy niepodlegający null może mieć wartość null.
- [NiedzallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy nullnie powinien nigdy nie być null.

## <a name="specify-post-conditions-maybenull-and-notnull"></a>Określ warunki `MaybeNull` post: i`NotNull`

Załóżmy, że masz metodę z następującym podpisem:

```csharp
public Customer FindCustomer(string lastName, string firstName)
```

Prawdopodobnie napisałeś taką metodę, aby `null` powrócić, gdy szukana nazwa nie została znaleziona. Wyraźnie `null` wskazuje, że rekord nie został znaleziony. W tym przykładzie prawdopodobnie zmienisz typ `Customer` `Customer?`zwracany z na . Deklarowanie wartości zwracanej jako typu odwołania z możliwością null wyraźnie określa intencję tego interfejsu API.

Z powodów [objętych ogólnymi definicjami i nullability](#generic-definitions-and-nullability) tej techniki nie działa z metod ogólnych. Możesz mieć metodę rodzajową, która następuje podobny wzorzec:

```csharp
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Nie można określić, że zwracana wartość jest `T?`. Metoda zwraca, `null` gdy nie znaleziono poszukiwanego elementu. Ponieważ nie można zadeklarować typu zwracanego, `T?` należy dodać `MaybeNull` adnotację do zwracanej metody:

```csharp
[return: MaybeNull]
public T Find<T>(IEnumerable<T> sequence, Func<T, bool> match)
```

Poprzedni kod informuje obiekty wywołujące, że umowa oznacza typ niepodlegający null, ale wartość zwracana *może* faktycznie być null.  Użyj `MaybeNull` atrybutu, gdy interfejs API powinien być typem niepodlegającym null, zazwyczaj parametrem typu ogólnego, ale mogą istnieć wystąpienia, w których `null` będą zwracane.

Można również określić, że wartość `out` `ref` zwracana lub lub argument nie jest null, nawet jeśli typ jest typem null. Należy wziąć pod uwagę metodę, która zapewnia tablicy jest wystarczająco duży, aby pomieścić wiele elementów. Jeśli argument wejściowy nie ma pojemności, rutynowych przydzieli nową tablicę i skopiować wszystkie istniejące elementy do niego. Jeśli argument wejściowy `null`jest , rutynowych przydzieli nowy magazyn. Jeśli jest wystarczająca pojemność, procedura nic nie robi:

```csharp
public void EnsureCapacity<T>(ref T[] storage, int size)
```

Tę procedurę można nazwać następującą:

```csharp
// messages has the default value (null) when EnsureCapacity is called:
EnsureCapacity<string>(ref messages, 10);
// messages is not null.
EnsureCapacity<string>(messages, 50);
```

Po włączeniu typów odwołań null, chcesz upewnić się, że poprzedni kod kompiluje bez ostrzeżenia. Gdy metoda zwraca, `storage` argument jest gwarantowane, aby nie był null. Jednak dopuszczalne jest wywołanie `EnsureCapacity` z odwołaniem zerowym. Można wprowadzić `storage` typ odwołania z wartością `NotNull` null i dodać warunek post do deklaracji parametru:

```csharp
public void EnsureCapacity<T>([NotNull]ref T[]? storage, int size)
```

Poprzedni kod wyraża istniejący kontrakt bardzo wyraźnie: Obiekty wywołujące `null` można przekazać zmienną z wartością, ale wartość zwracana jest gwarantowana, że nigdy nie będzie null. Atrybut `NotNull` jest najbardziej `ref` przydatne `out` dla `null` i argumenty, gdzie mogą być przekazywane jako argument, ale ten argument jest gwarantowane, aby nie być null, gdy metoda zwraca.

Bezwarunkowe warunki posty można określić przy użyciu następujących atrybutów:

- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana niepodlegająca null może być null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Wartość zwracana null nigdy nie będzie null.

## <a name="specify-conditional-post-conditions-notnullwhen-maybenullwhen-and-notnullifnotnull"></a>Określanie warunkowych `NotNullWhen` `MaybeNullWhen`warunków postojowych: , , i`NotNullIfNotNull`

Prawdopodobnie znasz `string` tę metodę <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType>. Ta metoda `true` zwraca, gdy argument ma wartość null lub pusty ciąg. Jest to forma null-check: Obiekty wywołujące nie trzeba null-check argument, jeśli metoda zwraca `false`. Aby metoda taka jak ta znawartość nullable, należy ustawić argument na `NotNullWhen` typ nullable i dodać atrybut:

```csharp
bool IsNullOrEmpty([NotNullWhen(false)]string? value);
```

Informuje kompilator, że każdy kod, w którym wartość zwracana jest `false` nie musi być sprawdzane wartości null. Dodanie atrybutu informuje o analizie statycznej `IsNullOrEmpty` kompilatora, która wykonuje `false`niezbędne sprawdzanie `null`null: po powrocie, argument wejściowy nie jest .

```csharp
string? userInput = GetUserInput();
if (!string.IsNullOrEmpty(userInput))
{
   int messageLength = userInput.Length; // no null check needed.
}
// null check needed on userInput here.
```

Metoda <xref:System.String.IsNullOrEmpty(System.String)?DisplayProperty=nameWithType> zostanie omówiona w sposób pokazany powyżej dla .NET Core 3.0. W bazie kodu mogą znajdować się podobne metody sprawdzania stanu obiektów pod kątem wartości null. Kompilator nie rozpoznaje niestandardowych metod sprawdzania wartości null i należy samodzielnie dodać adnotacje. Po dodaniu atrybutu analiza statyczna kompilatora wie, kiedy przetestowana zmienna została sprawdzona wartości null.

Innym zastosowaniem dla tych `Try*` atrybutów jest wzorzec. Postconditions for `ref` `out` i zmienne są przekazywane za pośrednictwem wartości zwracanej. Należy wziąć pod uwagę tę metodę pokazano wcześniej:

```csharp
bool TryGetMessage(string key, out string message)
```

Powyższa metoda jest zgodna z typowym idiomem `message` .NET: wartość zwracana wskazuje, czy została ustawiona na znalezioną wartość lub, jeśli nie zostanie znaleziony żaden komunikat, na wartość domyślną. Jeśli metoda `true`zwraca, wartość `message` nie jest null; w przeciwnym razie `message` metoda ustawia wartość null.

Można komunikować się, że `NotNullWhen` idiom za pomocą atrybutu. Podczas aktualizowania podpisu dla typów `message` odwołań podlegających wartości null należy dodać `string?` i dodać atrybut:

```csharp
bool TryGetMessage(string key, [NotNullWhen(true)] out string? message)
```

W poprzednim przykładzie wartość `message` jest znana jako nie `TryGetMessage` null `true`po zwrocie . Podobne metody należy dodać do adnotowania w bazie kodu w `null`ten sam sposób: argumenty mogą `true`być , i są znane jako nie null, gdy metoda zwraca .

Jest jeszcze jeden końcowy atrybut, którego możesz potrzebować. Czasami stan zerowy wartości zwracanej zależy od stanu zerowego jednego lub więcej argumentów wejściowych. Te metody zwróci wartość nienull, gdy niektóre argumenty wejściowe nie `null`są . Aby poprawnie adnotować te metody, `NotNullIfNotNull` należy użyć tego atrybutu. Należy wziąć pod uwagę następującą metodę:

```csharp
string GetTopLevelDomainFromFullUrl(string url);
```

Jeśli `url` argument nie jest null, dane `null`wyjściowe nie jest . Po włączeniu odwołań nullable, że podpis działa poprawnie, pod warunkiem, że interfejs API nigdy nie akceptuje null danych wejściowych. Jednak jeśli dane wejściowe mogą być null, a następnie wartość zwracana może być również null. W związku z tym można zmienić podpis na następujący kod:

```csharp
string? GetTopLevelDomainFromFullUrl(string? url);
```

To również działa, ale często zmusza `null` dzwoniących do wdrożenia dodatkowych kontroli. Kontrakt jest, że wartość `null` zwracana będzie `url` tylko `null`wtedy, gdy argument wejściowy jest . Aby wyrazić tę umowę, należy opatrzyć tą metodą, jak pokazano w następującym kodzie:

```csharp
[return: NotNullIfNotNull("url")]
string? GetTopLevelDomainFromFullUrl(string? url);
```

Wartość zwracana i argument zostały oznaczyć `?` z oskazaniami, `null`że może być . Atrybut wyjaśnia ponadto, że wartość zwracana nie będzie `url` null, `null`gdy argument nie jest .

Warunki postów warunkowych można określić przy użyciu następujących atrybutów:

- [MaybeNullWhen:](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)Argument wejściowy niepodlegający null może mieć wartość null, gdy metoda zwraca określoną `bool` wartość.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy z wartością null nie będzie `bool` null, gdy metoda zwraca określoną wartość.
- [NotNullIfNotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)Wartość zwracana nie jest null, jeśli argument wejściowy dla określonego parametru nie jest null.

## <a name="generic-definitions-and-nullability"></a>Ogólne definicje i nieważność

Poprawne komunikowanie stanu zerowego typów ogólnych i metod ogólnych wymaga szczególnej ostrożności. Wynika to z faktu, że typ wartości nullable i typ odwołania nullable są zasadniczo różne. An `int?` jest synonimem `Nullable<int>`dla , `string?` `string` podczas gdy jest z atrybutem dodanym przez kompilator. Wynik jest, że kompilator nie `T?` można wygenerować poprawny kod bez wiedząc, czy `T` jest `class` `struct`lub .

Nie oznacza to, że nie można użyć typu nullable (typu wartości lub typu odwołania) jako argumenttypu dla zamkniętego typu ogólnego. Oba `List<string?>` `List<int?>` i są ważne wystąpienia `List<T>`.

Co to znaczy, że nie `T?` można używać w klasie ogólnej lub deklaracji metody bez ograniczeń. Na przykład <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable%7B%60%600%7D)?displayProperty=nameWithType> nie zostaną zmienione, `T?`aby powrócić . Można przezwyciężyć to ograniczenie, `struct` dodając `class` lub ograniczenie. Z jednym z tych ograniczeń kompilator `T` wie, jak wygenerować kod dla obu i `T?`.

Można ograniczyć typy używane dla argumentu typu ogólnego jako typy niepodlegające wartości null. Można to zrobić, `notnull` dodając ograniczenie dla tego argumentu typu. Po zastosowaniu tego ograniczenia argument typu nie może być typem wartości null.

## <a name="conclusions"></a>Wnioski

Dodanie typów odwołań z możliwością null zapewnia początkowe słownictwo opisujące `null`oczekiwania interfejsów API dla zmiennych, które mogą być . Dodatkowe atrybuty zapewniają bogatsze słownictwo do opisania stanu zerowego zmiennych jako warunków wstępnych i warunków postconditions. Te atrybuty wyraźniej opisują twoje oczekiwania i zapewniają lepsze środowisko dla deweloperów korzystających z interfejsów API.

Podczas aktualizowania bibliotek dla kontekstu nullable, dodaj te atrybuty, aby poprowadzić użytkowników interfejsów API do prawidłowego użycia. Te atrybuty pomagają w pełni opisać stan null argumentów wejściowych i wartości zwracanych:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy niepodlegający null może mieć wartość null.
- [NiedzallowNull](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute): Argument wejściowy nullnie powinien nigdy nie być null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana niepodlegająca null może być null.
- [NotNull](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute): Wartość zwracana null nigdy nie będzie null.
- [MaybeNullWhen:](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute)Argument wejściowy niepodlegający null może mieć wartość null, gdy metoda zwraca określoną `bool` wartość.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy z wartością null nie będzie `bool` null, gdy metoda zwraca określoną wartość.
- [NotNullIfNotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute)Wartość zwracana nie jest null, jeśli argument wejściowy dla określonego parametru nie jest null.
