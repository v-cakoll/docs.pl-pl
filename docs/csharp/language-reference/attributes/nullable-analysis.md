---
title: 'Atrybuty zastrzeżone języka C#: nullowa analiza statyczna'
ms.date: 04/14/2020
description: Te atrybuty są interpretowane przez kompilator, aby zapewnić lepszą analizę statyczną dla typów odwołań nullable i non-null.
ms.openlocfilehash: 0315d78db7517541efe578d8675c0f2fe45f5aea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389864"
---
# <a name="reserved-attributes-contribute-to-the-compilers-null-state-static-analysis"></a>Atrybuty zastrzeżone przyczyniają się do analizy statycznej stanu zerowego kompilatora

W kontekście nullable kompilator wykonuje statyczną analizę kodu w celu określenia stanu null wszystkich zmiennych typu odwołania:

- *nie null*: Analiza statyczna ustaliła, że zmienna jest przypisana do wartości innej niż null.
- *może null*: Analiza statyczna nie może ustalić, że zmiennej jest przypisana wartość niekrajowa.

Można zastosować szereg atrybutów, które dostarczają informacji do kompilatora o semantyki interfejsów API. Te informacje pomagają kompilatorowi wykonać analizę statyczną i określić, kiedy zmienna nie jest null. Ten artykuł zawiera krótki opis każdego z tych atrybutów i jak z nich korzystać. Wszystkie przykłady zakładają C# 8.0 lub nowsze, a kod jest w kontekście nullable.

Zacznijmy od znanego przykładu. Wyobraź sobie, że biblioteka ma następujący interfejs API do pobierania ciągu zasobu:

```csharp
bool TryGetMessage(string key, out string message)
```

W poprzednim przykładzie `Try*` następuje znane wzorzec w .NET. Istnieją dwa argumenty odwołania dla `key` tego `message` interfejsu API: i parametr. Ten interfejs API ma następujące reguły odnoszące się do nieważności tych argumentów:

- Dzwoniący nie powinni `null` przechodzić `key`jako argument dla .
- Osoby dzwoniące mogą przekazać `null` zmienną, `message`której wartość jest argumentem dla .
- Jeśli `TryGetMessage` metoda `true`zwraca , `message` wartość nie jest null. Jeśli zwracana `false,` wartość jest `message` wartością (a jej stan zerowy) jest null.

Reguła `key` dla może być wyrażona `key` przez typ zmiennej: powinien być typem odwołania nienastępującym wartość null. Parametr `message` jest bardziej złożony. Pozwala `null` jako argument, ale gwarantuje, że `out` na sukces, że argument nie jest null. W przypadku tych scenariuszy potrzebujesz bogatszego słownictwa, aby opisać oczekiwania.

Dodano kilka atrybutów, aby wyrazić dodatkowe informacje o stanie null zmiennych. Cały kod, który napisałeś przed C# 8 wprowadzone nullable typy odwołań był *null oblivious*. Oznacza to, że każda zmienna typu odwołania może mieć wartość null, ale nie są wymagane kontrole wartości null. Gdy kod jest *nullable aware*, te reguły zmienić. Typy odwołań `null` nigdy nie powinny być wartością, `null` a typy odwołań do wartości null muszą być sprawdzane przed odwołaniem.

Reguły interfejsów API są prawdopodobnie bardziej skomplikowane, `TryGetValue` jak widać w scenariuszu interfejsu API. Wiele interfejsów API ma bardziej złożone reguły, gdy zmienne mogą lub nie mogą być `null`. W takich przypadkach do wyrażenia tych reguł użyjesz jednego z następujących atrybutów:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy nienastępny do wartości null może mieć wartość null.
- [NieuprawnionyNull:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Nullable argument wejściowy nigdy nie powinien być null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana bez wartości null może być wartość null.
- [NotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)Nullable wartość zwracana nigdy nie będzie null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy nienastępny do wartości `bool` null może mieć wartość null, gdy metoda zwraca określoną wartość.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do null nie będzie `bool` null, gdy metoda zwraca określoną wartość.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Zwracana wartość nie jest zerowa, jeśli argument dla określonego parametru nie jest null.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Metoda nigdy nie zwraca. Innymi słowy zawsze zgłasza wyjątek.
- [DoesNotReturnIf:](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute)Ta metoda nigdy nie `bool` zwraca, jeśli skojarzony parametr ma określoną wartość.

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

W kontekście `ReviewComment` `get` możliwego do anulowania akcesor może zwrócić wartość domyślną `null`programu . Kompilator ostrzega, że należy sprawdzić przed dostępem. Co więcej, ostrzega dzwoniących, że nawet `null`jeśli może to być , `null`dzwoniący nie powinni wyraźnie ustawić go na . Atrybut `DisallowNull` określa również *warunek wstępny*, nie wpływa `get` na akcesor. Atrybutu `DisallowNull` należy używać, gdy obserwujesz następujące cechy dotyczące:

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

Z przyczyn objętych [definicjami rodzajowymi i niemożnością użycia](../../nullable-attributes.md#generic-definitions-and-nullability) ta technika nie działa z metodami ogólnymi. Może być metoda rodzajowa, która następuje podobny wzorzec:

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

Powyższy kod wyraźnie wyraża istniejącą umowę: wywołujący mogą `null` przekazać zmienną z wartością, ale wartość zwracana jest gwarantowana, aby nigdy nie była null. Atrybut `NotNull` jest najbardziej przydatne `ref` `out` dla `null` i argumenty, gdzie mogą być przekazywane jako argument, ale ten argument jest gwarantowane nie jest null, gdy zwraca metodę.

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

## <a name="verify-unreachable-code"></a>Weryfikowanie nieosiągalnego kodu

Niektóre metody, zazwyczaj pomocników wyjątków lub innych metod narzędzia, zawsze zakończyć, zgłaszając wyjątek. Lub pomocnika może zgłosić wyjątek na podstawie wartości argumentu logicznego.

W pierwszym przypadku można dodać `DoesNotReturn` atrybut do deklaracji metody. Kompilator pomaga na trzy sposoby. Najpierw kompilator generuje ostrzeżenie, jeśli istnieje ścieżka, w której metoda może zakończyć działanie bez zgłaszania wyjątku. Po drugie kompilator oznacza dowolny kod po wywołaniu tej metody `catch` jako *nieosiągalny*, dopóki nie zostanie napotkana odpowiednia klauzula. Po trzecie, nieosiągalny kod nie wpłynie na żadne stany null. Należy wziąć pod uwagę tę metodę:

```csharp
[DoesNotReturn]
private void FailFast()
{
   throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   if (!isInitialized)
      FailFast();

   // unreachable code:
   this.field = containedField;
}
```

W drugim przypadku należy `DoesNotReturnIf` dodać atrybut do parametru logicznego metody. Poprzedni przykład można zmodyfikować w następujący sposób:

```csharp
private void FailFast([DoesNotReturnIf(false)]bool isValid)
{
   if (!isValid)
       throw new InvalidOperationException();
}

public void SetState(object containedField)
{
   FailFast(isInitialized);

   // unreachable code when "isInitialized" is false:
   this.field = containedField;
}
```

## <a name="summary"></a>Podsumowanie

Dodawanie typów odwołań do wartości nullable zapewnia początkowe słownictwo opisujące `null`oczekiwania interfejsów API dla zmiennych, które mogą być . Dodatkowe atrybuty zapewniają bogatsze słownictwo do opisania stanu null zmiennych jako warunków wstępnych i postconditions. Te atrybuty jaśniej opisują twoje oczekiwania i zapewniają lepsze środowisko dla deweloperów korzystających z interfejsów API.

Podczas aktualizowania bibliotek dla kontekstu możliwego do podenia, dodaj te atrybuty, aby poprowadzić użytkowników interfejsów API do prawidłowego użycia. Te atrybuty pomagają w pełni opisać zerowy stan argumentów wejściowych i zwracać wartości:

- [AllowNull](xref:System.Diagnostics.CodeAnalysis.AllowNullAttribute): Argument wejściowy nienastępny do wartości null może mieć wartość null.
- [NieuprawnionyNull:](xref:System.Diagnostics.CodeAnalysis.DisallowNullAttribute)Nullable argument wejściowy nigdy nie powinien być null.
- [MaybeNull](xref:System.Diagnostics.CodeAnalysis.MaybeNullAttribute): Wartość zwracana bez wartości null może być wartość null.
- [NotNull:](xref:System.Diagnostics.CodeAnalysis.NotNullAttribute)Nullable wartość zwracana nigdy nie będzie null.
- [MaybeNullWhen](xref:System.Diagnostics.CodeAnalysis.MaybeNullWhenAttribute): Argument wejściowy nienastępny do wartości `bool` null może mieć wartość null, gdy metoda zwraca określoną wartość.
- [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute): Argument wejściowy do null nie będzie `bool` null, gdy metoda zwraca określoną wartość.
- [NotNullIfNotNull](xref:System.Diagnostics.CodeAnalysis.NotNullIfNotNullAttribute): Zwracana wartość nie jest zerowa, jeśli argument wejściowy dla określonego parametru nie jest null.
- [DoesNotReturn](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnAttribute): Metoda nigdy nie zwraca. Innymi słowy zawsze zgłasza wyjątek.
- [DoesNotReturnIf:](xref:System.Diagnostics.CodeAnalysis.DoesNotReturnIfAttribute)Ta metoda nigdy nie `bool` zwraca, jeśli skojarzony parametr ma określoną wartość.
