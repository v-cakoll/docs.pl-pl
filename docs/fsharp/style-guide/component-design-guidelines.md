---
title: 'F # składnika zaleceń dotyczących projektowania'
description: 'Dowiedz się wskazówki dotyczące pisania F # składniki przeznaczone do użytku przez inne obiekty wywołujące.'
ms.date: 05/14/2018
ms.openlocfilehash: 7859baac76be01b2cfbdc8602b6cc417cfe5106f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="f-component-design-guidelines"></a>F # składnika zaleceń dotyczących projektowania

Ten dokument jest zestaw zaleceń dotyczących projektowania składnika w F # programowania, na podstawie F # składnika projektu wytycznych, wersja 14, Microsoft Research i [inna wersja](https://fsharp.org/specs/component-design-guidelines/) pierwotnie wyselekcjonowanych i obsługiwanego przez Foundation oprogramowania F #.

Tym dokumencie przyjęto założenie, że znasz programowania w języku F #. Wiele dzięki użyciu społeczności F # dla ich wkład i opinie pomocne w różnych wersjach tego przewodnika.

## <a name="overview"></a>Omówienie

Ten dokument wygląda na kilka zagadnień dotyczących projektowania składnika F # i kodowania. Składnik może oznaczać jedną z następujących czynności:

* Warstwa w projekcie F # z zewnętrznego konsumentów w ramach tego projektu.
* Biblioteka przeznaczonych do użycia w kodzie języka F # poza granicami zestawu.
* Biblioteka przeznaczonych do użycia za pomocą dowolnego języka .NET poza granicami zestawu.
* Biblioteki przeznaczone do dystrybucji za pośrednictwem z repozytorium pakietów, takie jak [NuGet](https://nuget.org).

Postępuj zgodnie z metod opisanych w tym artykule [pięć zasadami dobrej kodzie języka F #](index.md#five-principles-of-good-f-code)i w związku z tym korzystania zarówno funkcjonalności i obiekt programowania zależnie od potrzeb.

Niezależnie od metody Projektant składnika i biblioteki skierowany liczba praktycznych i prosaic problemy podczas próby jednostki interfejsu API, który jest łatwo używany przez deweloperów. Stosowanie sumienia [zaleceń dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md) kierowania kierunku tworzenia spójny zestaw interfejsów API, które są przyjemne korzystać.

## <a name="general-guidelines"></a>Ogólne wskazówki

Istnieje kilka uniwersalnych wskazówki, które dotyczą F # bibliotek, niezależnie od określonej grupy odbiorców w bibliotece.

### <a name="learn-the-net-library-design-guidelines"></a>Dowiedz się więcej zaleceń dotyczących projektowania biblioteki .NET

Niezależnie od rodzaju F # kodowania operacji jest przydatna dla mieć praktyczną wiedzę o [zaleceń dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md). Większość innych F # programistów platformy .NET zostanie należy zapoznać się z tymi wytycznymi i oczekują kodu platformy .NET, które są zgodne z nich.

Wytyczne dotyczące projektowania biblioteki .NET zawierają ogólne wskazówki dotyczące nazewnictwa, projektowanie klasy i interfejsy, elementu członkowskiego projektu (właściwości, metody, zdarzenia, itp.) i inne, a są przydatne, pierwszy punkt odniesienia dla różnych wskazówki dotyczące projektowania.

### <a name="add-xml-documentation-comments-to-your-code"></a>Dodaj komentarze dokumentacji XML w kodzie

Plik dokumentacji XML w publicznych interfejsach API upewnij się, że użytkownicy mogą uzyskać doskonałe Intellisense i skrócone informacje podczas plików przy użyciu tych typów i członków i Włącz tworzenie dokumentacji dla biblioteki. Zobacz [dokumentacji XML](../language-reference/xml-documentation.md) o różnych tagi xml, które mogą być używane dla dodatkowych znacznika w xmldoc komentarze.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

Można użyć albo komentarze XML Krótka forma (`/// comment`), lub standardowy komentarze XML (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Rozważ użycie jawnego podpisów (.fsi) bibliotekę stabilny i składników interfejsów API

Przy użyciu jawnych podpisów plików w bibliotece języka F # zawiera zwięzły podsumowanie publiczny interfejs API, których można mieć pewność, że należy znać publicznej powierzchni biblioteki, a także zapewnia czyste rozdzielenie między dokumentacji publicznych oraz wewnętrznych Szczegóły implementacji. Należy pamiętać, że pliki sygnatur dodać tarcia na zmieniające się publiczny interfejs API, wymagając od zmian wprowadzanych w plikach wykonania i podpis. W związku z tym pliki sygnatur zwykle tylko należy wprowadzić po interfejs API stają się zestalone i nie powinien zmienić znacznie.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Zawsze należy stosować najlepsze rozwiązania dotyczące używania ciągów w .NET

Postępuj zgodnie z [najlepsze rozwiązania dotyczące przy użyciu ciągów w .NET](../../standard/base-types/best-practices-strings.md) wskazówki. W szczególności zawsze jawnie określać *kultury zamiar* konwersji i porównywania ciągów (jeśli dotyczy).

## <a name="guidelines-for-f-facing-libraries"></a>Wytyczne dotyczące F #-ukierunkowane bibliotek

W tej sekcji przedstawiono zalecenia dotyczące tworzenia publicznego F #-ukierunkowane biblioteki; oznacza to, bibliotek udostępnia publiczne interfejsy API, które mają być używane przez deweloperów w F #. Istnieją różne projektu biblioteki zaleceń dotyczy w szczególności F #. W przypadku braku konkretnych zaleceń, które należy wykonać zaleceń dotyczących projektowania biblioteki .NET są wskazówki rezerwowego.

### <a name="naming-conventions"></a>Konwencje nazewnictwa

#### <a name="use-net-naming-and-capitalization-conventions"></a>Użyj .NET konwencji nazewnictwa i wielkości liter

Poniższa tabela jest zgodna z konwencjami .NET nazewnictwa i wielkość liter. Brak małych dodatki do również obejmować konstrukcje F #.

| Konstrukcja | Case | Część | Przykłady | Uwagi |
|-----------|------|------|----------|-------|
| Typów konkretnych | PascalCase | Rzeczownik / przymiotników | Lista, Double, złożone | Konkretne typy są struktury, klas, wyliczeń, delegatów, rekordów i Unii. Chociaż nazwy typów są tradycyjnie małe litery w OCaml, F # przyjęła schemat nazewnictwa .NET dla typów.
| biblioteki DLL           | PascalCase |                 | Fabrikam.Core.dll |  |
| Tagi Unii     | PascalCase | rzeczownik | Niektóre, Dodaj Powodzenie | Nie używaj prefiksu w publicznych interfejsach API. Opcjonalnie użyj prefiksu, gdy wewnętrznych, takich jak ''' wpisz zespoły = TAlpha | TBeta | TDelta. "" |
| Zdarzenie          | PascalCase | Zlecenie | ValueChanged / ValueChanging |  |
| Wyjątki     | PascalCase |      | WebException | Nazwa powinna kończyć się "Wyjątków". |
| Pole          | PascalCase | rzeczownik | CurrentName  | |
| Typy interfejsów |  PascalCase | Rzeczownik / przymiotników | Interfejs IDisposable | Nazwa powinna zaczynać się znakiem "I". |
| Metoda |  PascalCase |  Zlecenie | ToString | |
| Przestrzeń nazw | PascalCase | | Microsoft.fsharp.Core — | Na ogół służy `<Organization>.<Technology>[.<Subnamespace>]`, mimo że Porzuć organizacji, jeśli ta technologia jest niezależna od organizacji. |
| Parametry | (camelcase) | rzeczownik |  właściwość typeName, transform, zakres | |
| Let wartości (wewnętrzny) | (camelcase) lub PascalCase | Rzeczownik / zlecenie |  getValue, myTable |
| Let wartości (zewnętrzne) | (camelcase) lub PascalCase | Rzeczownik/zlecenie  | List.map, Dates.Today | Let granica wartości często są publiczne, po wzorce projektowe funkcjonalności tradycyjnych. Jednak na ogół służy PascalCase podczas identyfikator można używać z innymi językami .NET. |
| Właściwość  | PascalCase  | Rzeczownik / przymiotników  | IsEndOfFile, BackColor  | Operatory logiczne ogólnie użycie jest i może i powinno być potwierdzającego, tak jak IsEndOfFile, nie IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Unikaj skrótów

Wytyczne .NET nadal stosować skróty (na przykład "Użyj `OnButtonClick` zamiast `OnBtnClick`"). Skrótów, takich jak `Async` są dopuszczalne dla "Asynchronous". Niniejsze wytyczne czasami jest ignorowany dla funkcjonalności programowania. na przykład `List.iter` używa skrót "iteracyjne". Z tego powodu przy użyciu skróty zwykle następować do lepszej w języku F #-do-F # — programowanie, ale nadal ogólnie należy unikać w projekcie składnik publiczny.

#### <a name="avoid-casing-name-collisions"></a>Unikaj wielkość liter konflikty nazw

Wytyczne .NET powiedzieć, że wielkość liter samodzielnie nie można użyć do odróżniania konflikty nazw, ponieważ niektóre języki klienta (na przykład Visual Basic) jest rozróżniana wielkość liter.

#### <a name="use-acronyms-where-appropriate"></a>Użyj akronimów, gdzie jest to odpowiednie

Skrótów, takich jak XML nie są skróty i są powszechnie używane w bibliotekach .NET w postaci małymi (Xml). Tylko akronimów dobrze znane, powszechnie rozpoznanym powinien być używany.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Użyj PascalCase dla nazw parametrów ogólnych

Należy używać PascalCase nazw parametru ogólnego w publicznych interfejsach API, w tym w F #-ukierunkowane bibliotek. W szczególności, użyj nazwy, jak `T`, `U`, `T1`, `T2` dla dowolnego parametry ogólne i gdy konkretne nazwy sensu, następnie w F #-nazwy, jak używać dostępnych bibliotek `Key`, `Value`, `Arg`(ale nie na przykład `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Użyj PascalCase lub (camelcase) dla funkcji publicznych i wartości w modułach F #

(camelcase) służy do publicznego funkcje, które są przeznaczone do użycia niekwalifikowane (na przykład `invalidArg`), a "kolekcji standardowych funkcji" (na przykład List.map). W obu przypadkach nazwy funkcji znacznie działać tak jak słów kluczowych w języku.

### <a name="object-type-and-module-design"></a>Obiekt, typ i modułu projektu

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Zawiera modułów i typów za pomocą przestrzeni nazw lub modułów

Każdy plik F # w składniku powinien zaczynać się od deklaracji przestrzeni nazw lub deklaracji modułu.

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

lub

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

Różnice między organizowanie kodu na najwyższym poziomie za pomocą modułów i przestrzenie nazw są następujące:

* Przestrzenie nazw może obejmować wiele plików
* Przestrzenie nazw nie może zawierać funkcje F #, chyba że są one modułu wewnętrzny
* Kod dla dowolnego podanego modułu musi być zawarty w jednym pliku
* Moduły najwyższego poziomu może zawierać funkcje F # bez konieczności moduł wewnętrzny

Wybór między najwyższego poziomu przestrzeni nazw lub modułu ma wpływ na formularzu skompilowanego kodu i w związku z tym będzie miało wpływ na widoku z innymi językami .NET należy interfejsu API ostatecznie używane poza kodzie języka F #.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Użyj metody i właściwości dla operacji wewnętrznej do typów obiektów

Praca z obiektami, najlepiej upewnij się, że funkcje eksploatacyjny zostały zaimplementowane jako metody i właściwości tego typu.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

Zbiorczego funkcji dla danego elementu członkowskiego nie muszą zawsze zaimplementowana w tym elemencie członkowskim, ale powinien być element eksploatacyjny te funkcje.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Umożliwia Hermetyzowanie modyfikowalną stan klasy

W języku F # to tylko trzeba zrobić, gdzie czy stanu nie jest już zamknięte przez inny konstrukcji języka, takie jak zamknięcia, wyrażenie sekwencji lub obliczeń asynchronicznych.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Użyj interfejsów do grupy działań związanych z

Typy interfejsów umożliwia reprezentują zestaw operacji. Jest to preferowana względem inne opcje, takie jak krotek, funkcji lub rekordy funkcji.

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

W preference do:

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

Interfejsy są najwyższej jakości pojęcia związane z .NET, który służy do osiągnięcia co Funktorów pozwoli zwykle uzyskać. Ponadto może być używany do kodowania typów egzystencjalna do tego programu, który rejestruje funkcji nie może.

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>Używaj modułu TPM na funkcje grupy, które działają w kolekcjach

Podczas definiowania typem kolekcji, należy wziąć pod uwagę zapewnienie standardowy zestaw operacji, takich jak `CollectionType.map` i `CollectionType.iter`) dla nowych typów kolekcji.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Jeśli takie modułu, wykonaj standardowe konwencje nazewnictwa dla funkcji systemu plikiem FSharp.Core.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Używaj modułu TPM do funkcji grupy do typowych funkcji kanonicznej, szczególnie w matematyczne i bibliotek DSL

Na przykład `Microsoft.FSharp.Core.Operators` automatycznie otwarte zbiór funkcji najwyższego poziomu (takich jak `abs` i `sin`) podany w pliku FSharp.Core.dll.

Podobnie, biblioteka statystyki może obejmować modułu z funkcjami `erf` i `erfc`, gdy ten moduł jest może być jawnie lub automatycznie otwarte.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Należy rozważyć użycie RequireQualifiedAccess i ostrożnie stosować atrybutów AutoOpen

Dodawanie `[<RequireQualifiedAccess>]` modułu dla atrybutu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu, wymaga jawnego kwalifikowana dostępu. Na przykład `Microsoft.FSharp.Collections.List` moduł ma tego atrybutu.

Jest to przydatne, gdy wartości w module i funkcje mają nazwy, które mogą powodować konflikt z nazwami w innych modułach. Wymagających dostępu kwalifikowaną może znacznie zwiększyć długoterminowej utrzymanie i evolvability biblioteki.

Dodawanie `[<AutoOpen>]` modułu dla atrybutu oznacza, że moduł zostanie otwarty po otwarciu zawierającego przestrzeni nazw. `[<AutoOpen>]` Atrybutu może być również stosowany do zestawu, aby wskazać moduł, który jest automatycznie otwierane w momencie odwołuje się do zestawu.

Na przykład biblioteki statystyki **MathsHeaven.Statistics** może zawierać `module MathsHeaven.Statistics.Operators` zawierający funkcje `erf` i `erfc`. Jest uzasadnione oznaczyć ten moduł jako `[<AutoOpen>]`. Oznacza to, że `open MathsHeaven.Statistics` będzie także otworzyć ten moduł i przełączyć nazwy `erf` i `erfc` do zakresu. Użycie innego dobrego `[<AutoOpen>]` dla modułów zawierających metody rozszerzenia.

Nadużywać z `[<AutoOpen>]` potencjalnych klientów zanieczyszczonych przestrzeni nazw i atrybutu należy używać ostrożnie. Dla biblioteki określonej w określonych domenach, korzystać z `[<AutoOpen>]` może prowadzić do lepszego użyteczność.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Rozważ zdefiniowanie operatora elementów członkowskich w klasach, gdzie jest odpowiednia przy użyciu operatorów dobrze znanego

Czasami klas są używane do modelu matematyczne konstrukcje, takich jak wektory. Jeśli domeny modelowanego dobrze znane operatory, definiując je jako członków do klasy wewnętrznej jest przydatne.

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

W tych wskazówkach odpowiada ogólne wskazówki .NET dla tych typów. Jednak może być również ważne w F # kodowania, ponieważ dzięki temu te typy do użycia w połączeniu z F # funkcje i metody ograniczenia elementu członkowskiego, takich jak list.sumby —.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Należy rozważyć użycie compiledname — w celu dostarczenia. NET-przyjazna nazwa dla innych użytkowników języka .NET

Czasami warto nazw coś w jednym stylu dla konsumentów F # (takich jak statyczny element członkowski w małe litery, tak że pojawi się tak, jakby była funkcja powiązane z modułu), ale ma inny styl dla nazwy, gdy jest on skompilowany w zestawie. Można użyć `[<CompiledName>]` atrybut do zapewnienia innego stylu z systemem innym niż kodzie języka F # korzystających z zestawu.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Przy użyciu `[<CompiledName>]`, można użyć .NET konwencje nazewnictwa dla klientów z systemem innym niż język F # zestawu.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Użyj przeciążenie metody dla funkcji członkowskiej, jeśli ten sposób zapewnia prostszy interfejsu API

Przeciążenie metody jest zaawansowanym narzędziem do uproszczenia interfejs API, który może być konieczne wykonanie podobne funkcje, ale z różnymi opcjami lub argumentów.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

W F # jest najczęściej do przeciążenia na liczbę argumentów niż typy argumentów.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Ukryj reprezentacje rekordu i typami Unii, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji

Unikaj ujawniania konkretnych reprezentacje obiektów. Na przykład konkretnych reprezentacja <xref:System.DateTime> wartości nie została ujawniona przez zewnętrznych, publiczny interfejs API .NET projektu biblioteki. Środowisko uruchomieniowe języka wspólnego w czasie wykonywania, wie, zatwierdzone implementację, która będzie używana w wykonywania. Jednak skompilowanego kodu nie sam wybierz zależności dotyczące konkretnych reprezentacji.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Unikaj stosowania dziedziczenia implementacji rozszerzalności

W języku F # jest rzadko używana implementacja dziedziczenia. Ponadto hierarchii dziedziczenia mają złożonej i trudnej można zmienić w momencie nadejścia nowych wymagań w zakresie. Implementacja dziedziczenia nadal istnieje w języku F # dla zgodności i rzadkich przypadkach, gdy to najlepsze rozwiązanie problemu, ale alternatywnych metod należy dążyć w programach F # podczas projektowania polimorfizm, takich jak implementacji interfejsu.

### <a name="function-and-member-signatures"></a>Funkcja i element członkowski podpisów

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Użyj spójnych kolekcji dla wartości zwracanych, gdy zwracany jest niewielka liczba wielu niepowiązanych wartości

Oto przykład przy użyciu spójnych kolekcji w zwracanego typu:

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

Dla zwracanych typów zawierający wiele składników lub składniki programu są związane z pojedynczej do zidentyfikowania jednostki, należy rozważyć użycie typu o nazwie zamiast spójnych kolekcji.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Użyj `Async<T>` programowania asynchronicznego na granicach interfejsu API F #

Jeśli istnieje odpowiadająca mu Operacja synchroniczna o nazwie `Operation` zwracającą `T`, a następnie powinno być nazwanym operacji asynchronicznej `AsyncOperation` Jeśli zwróci ona `Async<T>` lub `OperationAsync` Jeśli zwróci ona `Task<T>`. Często używanych typów .NET, które udostępniają metody Begin/End, warto rozważyć użycie `Async.FromBeginEnd` do zapisania metody rozszerzenia jako fasad zapewnienie F # async modelu programowania do tych interfejsów API architektury .NET.

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Wyjątki

Wyjątki są wyjątkowych w .NET; oznacza to, że ich nie powinien wystąpić często w czasie wykonywania. Gdy tak robią, informacje, które zawierają jest przydatna. Wyjątki są podstawowe pojęcia pierwszej klasie .NET; Dlatego IT, następuje, które odpowiednią aplikację wyjątki należy używać jako części projektu interfejsu składnika.

#### <a name="follow-the-net-guidelines-for-exceptions"></a>Postępuj zgodnie z wytycznymi .NET dla wyjątków

[Zaleceń dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/exceptions.md) podać znakomity stosowania wyjątków w kontekście programowania .NET wszystkie. Niektóre z tych wskazówek są następujące:

* Nie używaj wyjątki przepływu sterowania. Mimo że ta metoda jest często używane w językach takich jak OCaml, jest podatne błędów i może być mało wydajne na platformie .NET. Zamiast tego należy wziąć pod uwagę zwracanie `None` wartość do wskazania błędu, który jest wystąpieniem wspólnych lub oczekiwanego opcji.

* Następnie należy udokumentować wyjątki zgłaszane przez składniki, gdy używana jest funkcja niepoprawnie.

* Jeśli to możliwe, należy stosować istniejących wyjątków z przestrzeni nazw systemu. Unikaj <xref:System.ApplicationException>, ale.

* Nie zgłaszają <xref:System.Exception> kiedy zostanie escape, aby kod użytkownika. Dotyczy to również unikając stosowania `failwith`, `failwithf`, które są przydatne funkcje, użyj skrypty i kod opracowywane, ale powinna zostać usunięta z biblioteki kodzie języka F # na rzecz zgłaszanie więcej określony typ wyjątku.

* Użyj `nullArg`, `invalidArg`, i `invalidOp` jako mechanizm throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, i <xref:System.InvalidOperationException> w odpowiednim przypadku.

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a>Rozważ użycie wartości opcji dla typy zwracane, gdy błąd nie jest kodem scenariusza

Podejście .NET do wyjątków jest, czy powinien być "wyjątkowych;" oznacza to, że ich powinna występować stosunkowo rzadko. Jednak niektóre operacje (np. wyszukiwanie tabeli) może się nie powieść często. Wartości opcji F # są doskonałym sposobem reprezentują typy zwracane występujące w tych operacji. Te operacje tradycyjnie rozpoczyna się od prefiksu nazwy "try":

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a>Elementy członkowskie rozszerzeń

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Dokładnie zastosować F # elementy członkowskie rozszerzeń w języku F #-do-F # składniki

Elementy członkowskie rozszerzeń F # powinien zwykle można używać tylko dla operacji, które znajdują się w zamknięcia wewnętrzne operacje związane z typem w większości jej trybów użycia. Jeden użycia ma na celu dostarczenie interfejsów API, które są bardziej idiomatyczne do F # dla różnych typów .NET:

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a>Typy Unii

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Użyj rozłączne zamiast klasy hierarchie strukturze drzewa danych

Struktury drzewa są zdefiniowane cyklicznie. Jest to nieodpowiednich z dziedziczenia, ale elegancki z Suma rozłączna Unii.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Reprezentacja drzewa danych z unie Suma rozłączna — umożliwia również korzystać z kompletności w dopasowywania do wzorca.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Użyj `[<RequireQualifiedAccess>]` złożenia typów, których nazwy nie są wystarczająco unikatowe

Może się okazać się w domenie, gdzie tej samej nazwie jest nazwą najlepsze dla różnych rzeczy, takich jak przypadków Unii Suma rozłączna. Można użyć `[<RequireQualifiedAccess>]` do odróżnienia nazwy, aby uniknąć wyzwalania błędy myląca ze względu na przesłanianie zależne kolejność `open` — instrukcje

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Ukryj reprezentacje rozłączne dla binarnego zgodne interfejsów API, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji

Typy Unii jest zależne od F # dopasowywanie do wzorca formularze zwięzły modelu programowania. Jak wspomniano wcześniej, należy unikać ujawniania danych konkretne oświadczenia, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji.

Na przykład reprezentację rozróżnianą Unię mogą być ukryte za pomocą deklaracji prywatny lub wewnętrzny lub przy użyciu pliku podpisu.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Jeśli przyrostu ujawnieniem rozłączne, może być trudne do wersji biblioteki bez przerywania kodu użytkownika. Zamiast tego należy wziąć pod uwagę ujawniania co najmniej jeden aktywne wzorce umożliwiające wzorzec dopasowany wartości tego typu.

Wzorce aktywne Podaj inny sposób udostępnić F # konsumentów wzorzec dopasowany unikając bezpośrednio udostępnianie typów złożenia języka F #.

### <a name="inline-functions-and-member-constraints"></a>Wbudowane funkcje i ograniczenia elementu członkowskiego

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Zdefiniuj ogólnego algorytmów liczbowych za pomocą funkcji śródwierszowych ograniczenia elementu członkowskiego domyślnych i statycznie rozwiązywane typów ogólnych

Ograniczenia elementu członkowskiego arytmetyczne i F # porównania ograniczenia są standardowe rozwiązanie dla programowania w języku F #. Rozważmy na przykład następujący kod:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

Typ tej funkcji jest następujący:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

Jest to funkcja odpowiednie dla publiczny interfejs API w bibliotece matematycznych.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Należy unikać używania ograniczenia elementu członkowskiego do symulowania typu klasy i wpisując kaczka

Można symulować "kacze, wpisując" za pomocą ograniczenia elementu członkowskiego F #. Jednak elementów członkowskich, które należy użyć tego ogólne nie stosuje się w języku F #-do-biblioteki projektów F #. Jest tak, ponieważ na podstawie nieznane lub niestandardową ograniczeń niejawne projektów biblioteki mogą spowodować sztywne i wiązanej do jednej konkretnej framework wzorzec staną się kodu użytkownika.

Ponadto istnieje szansa, że intensywnie korzysta z ograniczenia elementu członkowskiego w ten sposób może spowodować kompilacji bardzo dużo czasu.

### <a name="operator-definitions"></a>Definicje — operator

#### <a name="avoid-defining-custom-symbolic-operators"></a>Unikaj definiowania niestandardowych symboliczne operatory

Operatory niestandardowe są niezbędne w niektórych sytuacjach i są bardzo przydatne notational urządzeniami w ramach dużą porcję kod implementacji. Dla nowych użytkowników biblioteki funkcji o nazwie często są łatwiejsze w użyciu. Ponadto niestandardowych operatory symboliczne może być trudne do dokumentu, a użytkownicy uważają trudniej uzyskać pomoc dotyczącą operatorów, ze względu na ograniczenia istniejącego w IDE i wyszukiwania aparaty wyszukiwania.

W związku z tym najlepiej publikowanie z funkcji jako nazwane funkcje i elementy członkowskie, a ponadto ujawnia operatory dla tej funkcji tylko wtedy, gdy przeważają korzyści notational dokumentacji i kognitywnych koszt o ich.

### <a name="units-of-measure"></a>Jednostki miary

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Starannie Użyj jednostki miary dla typów dodanych bezpieczeństwa w kodzie języka F #

Dodatkowe informacje pisania jednostki miary wymazaniu widzianego innymi językami .NET. Należy pamiętać, że składniki platformy .NET, narzędzia i odbicie Zobacz typy sieci SAN jednostki. Na przykład C# będą widzieli `float` zamiast `float<kg>`.

### <a name="type-abbreviations"></a>Skróty typów

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Starannie użyć skróty typów, aby uprościć kodzie języka F #

Składniki platformy .NET, narzędzia i odbicie nie będą widzieć skróconej nazwy dla typów. Skróty typów znaczne użycie można również ustawić domeny są wyświetlane faktycznie jest bardziej złożone niż, które można mylić konsumentów.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Unikaj skrótów typu typy publiczne, których elementy członkowskie i właściwości powinny być bardzo różni się od tych, które są dostępne w skracanym typie

W takim przypadku skracanym typie ujawnia zbyt dużo o reprezentację rzeczywisty typ jest zdefiniowany. Zamiast tego należy wziąć pod uwagę zawijania skrót typu klasy lub jeden przypadek Unii rozłącznych (lub, gdy wydajność jest niezbędne, należy rozważyć użycie typu struct opakowywać skrót).

Na przykład jest kuszące do definiowania wielu mapy w szczególnych przypadkach F # mapy, na przykład:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Jednak operacje logiczne kropkowego w tym typie nie są takie same operacje na mapie — na przykład, jest uzasadnione, że operator wyszukiwania mapy. Pusta lista, jeśli klucz nie ma w słowniku zamiast generowanie wyjątków [klucza] powrotu.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Wytyczne dotyczące biblioteki do użycia z innymi językami .NET

Podczas projektowania biblioteki do użycia z innymi językami .NET, ważne jest, aby stosować się do [zaleceń dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md). W tym dokumencie biblioteki te są oznaczone jako podstawowego bibliotek .NET, a nie F #-ukierunkowane bibliotek, które używają F # konstruuje bez ograniczeń. Projektowanie podstawowego bibliotek .NET oznacza zapewnienie znanego i idiomatyczne interfejsów API zgodne z pozostałą częścią programu .NET Framework, minimalizując użycie języka F #-konstrukcje określonych w publiczny interfejs API. W poniższych sekcjach opisano reguły.

### <a name="namespace-and-type-sesign-for-libraries-for-use-from-other-net-languages"></a>Namespace i Type sesign (dla biblioteki do użycia z innymi językami .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Dotyczą konwencje nazewnictwa .NET publiczny interfejs API składników

Należy zwrócić szczególną uwagę na użycie skróconej nazwy i wskazówkami dotyczącymi .NET wielkość liter.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Użyj przestrzeni nazw, typy i składniki jako podstawowy struktura organizacyjna składników

Wszystkie pliki zawierające publiczny funkcji powinny rozpoczynać się od `namespace` deklaracji i tylko jednostek publicznych w przestrzeniach nazw powinny być typów. Nie należy używać modułów F #.

Użyj niepublicznych modułów do przechowywania w kodzie, typy narzędzi i funkcji narzędzia.

Statyczne typy powinny mieć pierwszeństwo modułów, jak pozwalają one na przyszłe zmiany interfejsu API do używania przeciążania i innych interfejs API .NET zagadnienia dotyczące projektowania, które nie mogą być używane w modułach F #.

Na przykład zamiast następujące publiczny interfejs API:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

Zamiast tego rozważ:

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Użyć typy rekordów F # w waniliowe interfejsów API architektury .NET, jeśli projekt typów nie będą rozwijać

Typy rekordów F # kompilacji do prostą klasę platformy .NET. Są to odpowiednie dla niektórych typów prostych, stabilna w interfejsów API. Należy rozważyć użycie `[<NoEquality>]` i `[<NoComparison>]` atrybuty do pomijania automatyczne generowanie interfejsów. Również unikać pola rekordu modyfikowalną waniliowe interfejsów API architektury .NET jako te ujawnia pole publiczne. Zawsze należy rozważyć, czy klasa zapewni bardziej elastycznych opcji dla przyszłego rozwoju interfejsu API.

Na przykład następujący kod F # przedstawia publiczny interfejs API do konsumenta C#:

F #:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

C#:

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Ukryj reprezentację typów F # Unii w waniliowe interfejsów API architektury .NET

Typy Unii języka F # nie są powszechnie stosowane poza granicami składnika, nawet w przypadku F #-do-F # kodowania. Są one urządzenia znakomity wykonania, gdy używana wewnętrznie w składniki i biblioteki.

Podczas projektowania waniliowe interfejs API .NET, należy wziąć pod uwagę ukrywanie reprezentacja typu union za pomocą deklaracji prywatnych lub plik podpisu.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Może również rozszerzyć typów, które używają reprezentację Unii z elementami członkowskimi zapewnienie do żądanej wewnętrznie. Interfejs API udostępnianych w sieci.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Projekt graficznego interfejsu użytkownika i inne składniki przy użyciu wzorce projektowe platformy

Wiele różnych platform są dostępne w ramach platformy .NET, takie jak WinForms, WPF i platformy ASP.NET. Konwencje nazewnictwa i projektu dla każdego powinien być używany w przypadku projektowania składniki do użycia w tych platform. Na przykład dla WPF programowania, przyjmuje WPF wzorce projektowe dla klasy, z którymi projektowania. Dla modeli w programowaniu interfejsu użytkownika, użyj wzorce projektowe, takich jak zdarzenia i kolekcje oparte na powiadomienie, takich jak znaleźć w <xref:System.Collections.ObjectModel>.

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Projekt obiektu i element członkowski (dla biblioteki do użycia z innymi językami .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Umożliwia ujawnia zdarzenia platformy .NET w clievent — atrybut

Utworzyć `DelegateEvent` z określonych .NET przekazać typ, który pobiera obiekt i `EventArgs` (zamiast `Event`, który używa `FSharpHandler` typu domyślnie), aby zdarzenia są publikowane w taki sposób zapoznać się z innymi językami .NET.

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Udostępnianie operacji asynchronicznych jako metody zwracające zadania .NET

Zadania są używane w środowisku .NET do reprezentowania active obliczeń asynchronicznych. Zadania są zwykle składu mniej niż F # `Async<T>` obiektów, ponieważ reprezentuje zadania "już wykonuje" i nie może być jednocześnie który równoległych utworzenia lub który Ukryj propagacji sygnały anulowania oraz innych Parametry kontekstowe.

Mimo to, metody zwracające zadania są standardowe reprezentację programowanie asynchroniczne na platformie .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Często będą również chcesz zaakceptować token anulowania explicit:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Użyj typów delegata .NET zamiast funkcji typów F #

W tym miejscu "typów F # funkcja" oznacza "strzałka" typy, takich jak `int -> int`.

Zamiast tego:

```fsharp
member this.Transform(f:int->int) =
    ...
```

wykonaj następujące czynności:

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

Typ funkcji języka F # jest wyświetlany jako `class FSharpFunc<T,U>` do innych języków .NET i mniej odpowiedni język funkcji i narzędzi które zrozumieć typy delegatów. Podczas tworzenia metody wyższego rzędu przeznaczonych dla platformy .NET Framework 3.5 lub nowszego, `System.Func` i `System.Action` delegatów są prawa interfejsów API do publikowania umożliwiają deweloperom korzystać z tych interfejsów API w sposób niskim tarcia .NET. (Jeśli systemem docelowym jest środowisko .NET Framework 2.0, typy zdefiniowane w systemie delegata są bardziej ograniczone; Rozważ użycie typów delegatów wstępnie zdefiniowane, takich jak `System.Converter<T,U>` lub określenie typu określonego delegata.)

Na stronie Przerzucanie .NET delegatów nie są fizycznych w F # — ukierunkowane bibliotek (zobacz następną sekcję w F #-ukierunkowane bibliotek). W związku z tym wspólnej strategii wdrażania, podczas tworzenia metody wyższego rzędu do bibliotek .NET podstawowego ma tworzyć wszystkie wdrożenia przy użyciu funkcji typów F #, a następnie utwórz publiczny interfejs API, używanie delegatów jako alokowania fasad nad rzeczywiste F # Implementacja.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Użyj wzorca TryGetValue zamiast zwracać wartości opcji F # i preferowane jest przeciążenie metody do uwzględnienia wartości opcji F # jako argumenty

Lepsze są typowe wzorce użycia dla typu opcji F # w interfejsów API zaimplementowano w waniliowe techniki projektowania interfejsów API platformy .NET przy użyciu platformy .NET standard. Zamiast zwracać wartość opcji F #, należy rozważyć użycie zwracany typ bool plus parametru wyjściowego tak jak wzorzec "TryGetValue". I zamiast przyjmowania wartości opcji F # jako parametry, należy rozważyć użycie przeciążenie metody lub argumenty opcjonalne.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Użyj interfejsu kolekcji .NET typy IEnumerable\<T\> i IDictionary\<klucza, wartość\> dla parametrów i zwracanych wartości

Unikaj używania kolekcji konkretnych typów, takich jak .NET tablice `T[]`, typów F # `list<T>`, `Map<Key,Value>` i `Set<T>`, oraz konkretnych kolekcji .NET typów, takie jak `Dictionary<Key,Value>`. Wytyczne dotyczące projektowania biblioteki .NET mają dobrej porad dotyczących kiedy należy używać różnych typów kolekcji, takie jak `IEnumerable<T>`. Niektóre korzystanie z tablic (`T[]`) jest akceptowany w pewnych okolicznościach, na podstawie wydajności. Należy pamiętać, że szczególnie `seq<T>` jest po prostu F # alias dla `IEnumerable<T>`, i w związku z tym seq jest często odpowiedniego typu dla waniliowe interfejsu API platformy .NET.

Zamiast tego języka F # zawiera następujące informacje:

```fsharp
member this.PrintNames(names : string list) =
    ...
```

Użyj sekwencji F #:

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Użyj tego typu jednostki tylko typ danych wejściowych metody można zdefiniować metody zero argumentu lub jako jedynym zwracany typ celu zdefiniowania metody zwracające typ void

Unikaj innych celów tego typu jednostki. Są to dobry:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

To jest nieprawidłowy:

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Sprawdź, czy wartości null na podstawowego granice interfejs API .NET

F # w kodzie zwykle ma mniejszą liczbę wartości null z powodu wzorce projektowe niezmienne i ograniczenia użytkowania literałów wartości null dla typów F #. Innymi językami .NET jest często używane jako wartości null częściej. W związku z tym F # kod, który jest ujawniany przez waniliowe interfejs API .NET należy Sprawdź parametry dla wartości null na granicy interfejsu API i uniemożliwić te wartości głębiej otrzymywanych kod implementacji F #. `isNull` Funkcji lub dopasowania wzorca w `null` użyciem wzorca.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Unikaj używania krotek jako wartości zwracane

Zamiast tego preferowane zwracających Typ nazwany, zawierający dane zagregowane lub za pomocą parametrów out zwraca wiele wartości. Istnieje spójne kolekcje i struktury spójnych kolekcji w programie .NET (co obejmuje obsługę języka C# dla struktury krotek) one najczęściej nie zapewnia interfejsu API idealne i oczekiwany dla deweloperów platformy .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Unikaj używania currying parametrów

Zamiast tego należy użyć .NET konwencji wywoływania ``Method(arg1,arg2,…,argN)``.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Porada: Jeśli projektujesz biblioteki do użycia z dowolnego języka .NET, to nie ma nie zastąpi faktycznie wykonywania niektórych eksperymentalne C# i Visual Basic programowania upewnij się, że bibliotek "działanie po prawej" z tych języków. Aby upewnić się, że biblioteki i ich dokumentacji są wyświetlane zgodnie z oczekiwaniami do deweloperów umożliwia także narzędzi, takich jak .NET reflektora i przeglądarki obiektów Visual Studio.

## <a name="appendix"></a>Dodatek

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Przykład end-to-end projektowania kodzie języka F # do użytku przez innych języków .NET

Należy wziąć pod uwagę następujące klasy:

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

Wnioskowany Typ F # tej klasy jest następujący:

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

Spójrzmy na sposób wyświetlania tego typu F # do programisty, przy użyciu innego języka .NET. Na przykład przybliżonej C# "podpisu" wygląda następująco:

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Istnieje kilka ważnych kwestii do uwagi dotyczące sposobu F # reprezentuje konstrukcje tutaj. Na przykład:

* Metadane, takie jak nazwy argumentów została zachowana.

* F # metod, które przyjmują dwóch argumentów stają się C# metod, które przyjmują dwóch argumentów.

* Funkcje i list stają się odwołania do odpowiednie typy w bibliotece języka F #.

Poniższy kod przedstawia sposób Dostosuj ten kod, aby uwzględnić te czynności.

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

Wnioskowany Typ F # kodu jest następujący:

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

Podpis C# jest teraz w następujący sposób:

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

Poprawki wprowadzone do przygotowania tego typu do użycia jako część podstawowego biblioteki .NET są następujące:

* Dostosowana kilka nazw: `Point1`, `n`, `l`, i `f` stał się `RadialPoint`, `count`, `factor`, i `transform`odpowiednio.

* Używany typ zwracany `seq<RadialPoint>` zamiast `RadialPoint list` zmieniając konstruowania listy przy użyciu `[ ... ]` je przy użyciu konstrukcji sekwencji `IEnumerable<RadialPoint>`.

* Używany typ delegata .NET `System.Func` zamiast typem funkcji języka F #.

Dzięki temu można znacznie wrażeń zużyje w kodzie języka C#.
