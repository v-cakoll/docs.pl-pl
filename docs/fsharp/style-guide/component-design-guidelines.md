---
title: F# — wytyczne dotyczące projektowania składników
description: 'Zapoznaj się z wytycznymi dotyczącymi pisania składników języka F # przeznaczonych do użycia przez innych wywołujących.'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209139"
---
# <a name="f-component-design-guidelines"></a>F# — wytyczne dotyczące projektowania składników

Ten dokument stanowi zestaw wytycznych dotyczących projektowania składników języka F # opartych na wytycznych dotyczących projektowania składnika F #, wersja 14, Microsoft Research i wersji, która była pierwotnie nadzorowana i obsługiwana przez program F # Software Foundation.

W tym dokumencie założono, że znasz programowanie w języku F #. Wiele poprowadzi Cię przez społeczność F # do swoich potrzeb i pomocnych informacji o różnych wersjach tego przewodnika.

## <a name="overview"></a>Omówienie

W tym dokumencie przedstawiono niektóre problemy związane z projektowaniem i kodowaniem składników w języku F #. Składnik może oznaczać jedną z następujących wartości:

* Warstwa w projekcie języka F #, która ma zewnętrznych odbiorców w tym projekcie.
* Biblioteka przeznaczona do użycia przez kod F # między granicami zestawu.
* Biblioteka przeznaczona do użycia przez dowolny język .NET między granicami zestawu.
* Biblioteka przeznaczona do dystrybucji za pośrednictwem repozytorium pakietów, takich jak [NuGet](https://nuget.org).

Techniki opisane w tym artykule mają zastosowanie do [pięciu zasad dobrego kodu języka F #](index.md#five-principles-of-good-f-code)i w ten sposób wykorzystują zarówno programowanie funkcjonalne, jak i obiektów.

Bez względu na metodologię, składnik i Projektant biblioteki mogą napotkać wiele praktycznych i prosaicych problemów podczas tworzenia interfejsu API, który jest najłatwiej do użycia przez deweloperów. Conscientious z zastosowaniem [wytycznych dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md) będzie można utworzyć spójny zestaw interfejsów API, które są przyjemne do użycia.

## <a name="general-guidelines"></a>Ogólne wskazówki

Istnieje kilka uniwersalnych wytycznych dotyczących bibliotek języka F #, niezależnie od zamierzonych odbiorców biblioteki.

### <a name="learn-the-net-library-design-guidelines"></a>Poznaj wskazówki dotyczące projektowania biblioteki .NET

Bez względu na rodzaj kodowania języka F # jest to cenna znajomość [wytycznych dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md). Większość innych programistów F # i .NET zna te wytyczne i oczekuje, że kod .NET będzie zgodny z nimi.

Wskazówki dotyczące projektowania biblioteki .NET zapewniają ogólne wskazówki dotyczące nazewnictwa, projektowania klas i interfejsów, projektowania elementów członkowskich (właściwości, metod, zdarzeń itp.) i innych, a które są użytecznym pierwszym punktem odniesienia dla różnych wytycznych projektowych.

### <a name="add-xml-documentation-comments-to-your-code"></a>Dodawanie komentarzy do dokumentacji XML do kodu

Dokumentacja XML w publicznych interfejsach API zapewnia, że użytkownicy mogą uzyskać wspaniałe funkcje IntelliSense i sekcji szybkich informacji podczas korzystania z tych typów i członków, a także włączyć tworzenie plików dokumentacji dla biblioteki. Zapoznaj się z [dokumentacją XML](../language-reference/xml-documentation.md) dotyczącą różnych tagów XML, które mogą być używane do dodatkowego adiustacji w komentarzach XMLDOC.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

Możesz użyć krótkich komentarzy XML ( `/// comment` ) lub standardowych komentarzy XML ( `///<summary>comment</summary>` ).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Rozważ użycie jawnych plików sygnatur (. FSI) dla stabilnych interfejsów API biblioteki i składników

Używanie jawnych plików sygnatur w bibliotece języka F # zawiera zwięzłe podsumowanie publicznego interfejsu API, co pomaga zapewnić pełną publiczną powierzchnię biblioteki i zapewnia czyste rozdzielenie między dokumentacją publiczną i wewnętrznymi szczegółami implementacji. Pliki sygnatur dodają tarcie do zmiany publicznego interfejsu API, co wymaga wprowadzenia zmian w plikach implementacji i sygnatur. W związku z tym pliki sygnatur powinny być zwykle wprowadzane tylko wtedy, gdy interfejs API stał się solidified i nie jest już zmieniany znacząco.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Zawsze należy stosować najlepsze rozwiązania dotyczące używania ciągów w programie .NET

Postępuj zgodnie z [najlepszymi rozwiązaniami dotyczącymi używania ciągów w wskazówkach platformy .NET](../../standard/base-types/best-practices-strings.md) . W szczególności zawsze jawnie *zamiarem kultury* w konwersji i porównywania ciągów (jeśli ma to zastosowanie).

## <a name="guidelines-for-f-facing-libraries"></a>Wskazówki dotyczące bibliotek przeznaczonych dla języka F #

W tej sekcji przedstawiono zalecenia dotyczące projektowania publicznych bibliotek języka F #. oznacza to, że biblioteki uwidaczniające publiczne interfejsy API przeznaczone do użycia przez deweloperów języka F #. Istnieją różne zalecenia dotyczące projektowania bibliotek mające zastosowanie w odróżnieniu od języka F #. W przypadku braku konkretnych zaleceń, które obserwują, wskazówki dotyczące projektowania biblioteki .NET są wskazówkami powrotu.

### <a name="naming-conventions"></a>Konwencje nazewnictwa

#### <a name="use-net-naming-and-capitalization-conventions"></a>Korzystanie z nazw platformy .NET i Konwencji kapitalizacji

W poniższej tabeli przedstawiono konwencje nazewnictwa i Konwencji kapitalizacji platformy .NET. Istnieją małe dodatki, które zawierają również konstrukcje języka F #.

| Konstrukcja | Sprawa | Część | Przykłady | Uwagi |
|-----------|------|------|----------|-------|
| Typy konkretne | PascalCase | Rzeczownik/przymiotnik | Lista, podwójna, złożona | Konkretne typy to struktury, klasy, wyliczenia, Delegaty, rekordy i złożenia. Chociaż nazwy typów są tradycyjnie małe litery w OCaml, język F # przyjął schemat nazewnictwa platformy .NET dla typów.
| biblioteki DLL           | PascalCase |                 | Fabrikam. Core. dll |  |
| Złożenie tagów     | PascalCase | Rzeczownik | Niektóre, Dodaj, sukces | Nie należy używać prefiksu w publicznych interfejsach API. Opcjonalnie użyj prefiksu w przypadku wewnętrznego, takiego jak`type Teams = TAlpha | TBeta | TDelta.` |
| Wydarzenie          | PascalCase | Czasownik | ValueChanged / ValueChanging |  |
| Wyjątki     | PascalCase |      | WebException | Nazwa powinna kończyć się znakiem "Exception". |
| Pole          | PascalCase | Rzeczownik | Bieżącaname  | |
| Typy interfejsów |  PascalCase | Rzeczownik/przymiotnik | IDisposable | Nazwa powinna zaczynać się od "I". |
| Metoda |  PascalCase |  Czasownik | ToString | |
| Przestrzeń nazw | PascalCase | | Microsoft. FSharp. Core | Zwykle używaj `<Organization>.<Technology>[.<Subnamespace>]` , chociaż Porzuć organizację, jeśli technologia jest niezależna od organizacji. |
| Parametry | camelCase | Rzeczownik |  typeName, Transform, Range | |
| Zezwalaj na wartości (wewnętrzne) | camelCase lub PascalCase | Rzeczownik/czasownik |  GetValue, myTable |
| Zezwalaj na wartości (zewnętrzne) | camelCase lub PascalCase | Rzeczownik/czasownik  | List. map, daty. dzisiaj | wartości, które są powiązane, często są publiczne, gdy obowiązują tradycyjne funkcjonalne wzorce projektowe. Jednak zazwyczaj należy używać PascalCase, gdy identyfikator może być używany z innych języków .NET. |
| Właściwość  | PascalCase  | Rzeczownik/przymiotnik  | IsEndOfFile, BackColor  | Ogólnie używane właściwości logiczne to i mogą być pozytywne, podobnie jak w IsEndOfFile, a nie IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Unikaj skrótów

Wskazówki dotyczące platformy .NET uniemożliwiają korzystanie z skrótów (na przykład "Użyj `OnButtonClick` zamiast `OnBtnClick` "). Standardowe skróty, takie jak `Async` dla "asynchroniczne", są dopuszczalne. Te wytyczne są czasami ignorowane w programowaniu funkcjonalnym; na przykład `List.iter` używa skrótu do iteracji. Z tego powodu skróty do programowania w języku F #-do-F # mają być ograniczone, ale mimo to nadal powinny być stosowane w projekcie składnika publicznego.

#### <a name="avoid-casing-name-collisions"></a>Unikaj kolizji nazw

Wskazówki dotyczące platformy .NET mówią, że nie można użyć samej obudowy, aby odróżnić kolizje nazw, ponieważ niektóre języki klienta (na przykład Visual Basic) nie uwzględniają wielkości liter.

#### <a name="use-acronyms-where-appropriate"></a>Używaj akronimów, tam gdzie to konieczne

Akronimy, takie jak XML, nie są skrótami i są szeroko stosowane w bibliotekach platformy .NET w postaci niewielkiej (XML). Należy używać tylko dobrze znanych, powszechnie rozpoznanych akronimów.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Użyj PascalCase dla ogólnych nazw parametrów

Użyj PascalCase dla ogólnych nazw parametrów w publicznych interfejsach API, w tym dla bibliotek przeznaczonych dla języka F #. W szczególności należy używać nazw, takich jak,, `T` `U` `T1` , `T2` dla dowolnych parametrów ogólnych, a kiedy konkretne nazwy mają sens, a następnie dla bibliotek przeznaczonych dla języka F # używają nazw takich jak `Key` , `Value` , `Arg` (ale nie na przykład `TKey` ).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Użyj PascalCase lub camelCase do publicznych funkcji i wartości w modułach języka F #

camelCase jest używany do funkcji publicznych, które są przeznaczone do użycia niekwalifikowanych (na przykład `invalidArg` ) i dla "standardowych funkcji kolekcji" (na przykład list. map). W obu tych przypadkach nazwy funkcji działają podobnie jak słowa kluczowe w języku.

### <a name="object-type-and-module-design"></a>Obiekt, typ i projekt modułu

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Używanie obszarów nazw lub modułów do przechowywania typów i modułów

Każdy plik F # w składniku powinien rozpoczynać się od deklaracji przestrzeni nazw lub deklaracji modułu.

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

Różnice między używaniem modułów i przestrzeni nazw do organizowania kodu na najwyższym poziomie są następujące:

* Przestrzenie nazw mogą obejmować wiele plików
* Przestrzenie nazw nie mogą zawierać funkcji języka F #, chyba że znajdują się w module wewnętrznym
* Kod dla danego modułu musi być zawarty w pojedynczym pliku
* Moduły najwyższego poziomu mogą zawierać funkcje języka F # bez potrzeby wewnętrznego modułu

Wybór między przestrzenią nazw najwyższego poziomu lub modułem ma wpływ na skompilowaną postać kodu i w efekcie będzie miał wpływ na widok z innych języków .NET, jeśli interfejs API zostanie ostatecznie użyty poza kodem F #.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Użyj metod i właściwości dla operacji wewnętrznych dla typów obiektów

Podczas pracy z obiektami najlepiej jest upewnić się, że funkcje możliwe do użycia są implementowane jako metody i właściwości tego typu.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

Większość funkcjonalności dla danego elementu członkowskiego nie musi być koniecznie zaimplementowana w tym elemencie członkowskim, ale może to być użyteczna część tej funkcji.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Użyj klas do hermetyzacji stanu modyfikowalnego

W języku F #, należy to zrobić tylko wtedy, gdy ten stan nie jest już hermetyzowany przez inną konstrukcję języka, taką jak zamknięcie, wyrażenie sekwencji lub asynchroniczne obliczanie.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Używanie interfejsów do grupowania powiązanych operacji

Użyj typów interfejsów do reprezentowania zestawu operacji. Jest to preferowane w przypadku innych opcji, takich jak krotki funkcji lub rekordów funkcji.

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

W preferencjach:

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

Interfejsy są pojęciami pierwszej klasy w programie .NET, których można użyć do osiągnięcia tego, co funktory zwykle. Ponadto mogą być używane do kodowania typów egzystencjalna w programie, które nie mogą być rejestrowane w programie.

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a>Używanie modułu do grupowania funkcji, które działają na kolekcjach

Podczas definiowania typu kolekcji należy rozważyć dostarczenie standardowego zestawu operacji takich jak `CollectionType.map` i `CollectionType.iter` ) dla nowych typów kolekcji.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Jeśli dołączysz taki moduł, postępuj zgodnie ze standardowymi konwencjami nazewnictwa dla funkcji znalezionych w FSharp. Core.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Używanie modułu do grupowania funkcji dla wspólnych, kanonicznych funkcji, szczególnie w bibliotekach matematycznych i DSL

Na przykład `Microsoft.FSharp.Core.Operators` jest automatycznie otwierana kolekcja funkcji najwyższego poziomu (takich jak `abs` i `sin` ) dostarczonych przez FSharp. Core. dll.

Podobnie Biblioteka statystyk może zawierać moduł z funkcjami `erf` i `erfc` , w których ten moduł został zaprojektowany do jawnego lub automatycznego otwierania.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Rozważ użycie RequireQualifiedAccess i starannie Zastosuj atrybuty AutoOpen

Dodanie `[<RequireQualifiedAccess>]` atrybutu do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów modułu wymagają jawnego kwalifikowanego dostępu. Na przykład `Microsoft.FSharp.Collections.List` moduł ma ten atrybut.

Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą powodować konflikt z nazwami w innych modułach. Wymaganie dostępu kwalifikowanego może znacznie zwiększyć długoterminową konserwację i możliwość rozwijania biblioteki.

Dodanie `[<AutoOpen>]` atrybutu do modułu oznacza, że moduł zostanie otwarty po otwarciu zawierającego ją przestrzeni nazw. Ten `[<AutoOpen>]` atrybut może być również stosowany do zestawu, aby wskazać moduł, który jest automatycznie otwierany, gdy następuje odwołanie do zestawu.

Na przykład biblioteka statystyk **MathsHeaven. statystyki** mogą zawierać `module MathsHeaven.Statistics.Operators` funkcje zawierające `erf` i `erfc` . Należy oznaczyć ten moduł jako `[<AutoOpen>]` . Oznacza to `open MathsHeaven.Statistics` również otwarcie tego modułu i przeniesienie nazw `erf` oraz `erfc` zakresu. Innym dobrym zastosowaniem `[<AutoOpen>]` jest dla modułów zawierających metody rozszerzające.

Nadmierne użycie `[<AutoOpen>]` potencjalnych klientów w zanieczyszczonych przestrzeniach nazw i atrybut powinien być używany z opieką. W przypadku określonych bibliotek w określonych domenach rozsądne użycie `[<AutoOpen>]` może prowadzić do lepszej użyteczności.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Należy rozważyć Definiowanie elementów członkowskich operatora w klasach, w których używane są dobrze znane operatory

Czasami klasy są używane do modelowania konstrukcji matematycznych, takich jak Vectors. W przypadku modelowania domeny ma dobrze znane operatory, Definiowanie ich jako elementów członkowskich wewnętrznych dla klasy jest pomocne.

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Te wskazówki odnoszą się do ogólnych wskazówek dotyczących platformy .NET dla tych typów. Jednak może być dodatkowo ważne w języku F #, ponieważ pozwala to na używanie tych typów w połączeniu z funkcjami i metodami języka F # z ograniczeniami elementu członkowskiego, takimi jak list. sumBy —.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Rozważ użycie Skompilowanname, aby podać. Przyjazna dla sieci nazwa dla innych użytkowników języka .NET

Czasami warto nazwać coś w jednym stylu dla odbiorców F # (takich jak statyczna składowa w małych przypadkach, tak jakby była funkcją powiązaną z modułem), ale mieć inny styl dla nazwy, gdy jest kompilowany do zestawu. Możesz użyć atrybutu, `[<CompiledName>]` Aby podać inny styl dla kodu języka F #, który korzysta z zestawu.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Korzystając z programu `[<CompiledName>]` , można używać konwencji nazewnictwa platformy .NET dla odbiorców nie należących do zestawu.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Użycie przeciążania metod dla funkcji Członkowskich, jeśli tak, zapewnia łatwiejszy interfejs API

Przeciążanie metod jest zaawansowanym narzędziem do uproszczenia interfejsu API, który może wymagać wykonania podobnej funkcjonalności, ale z różnymi opcjami lub argumentami.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

W języku F # jest to bardziej powszechne, aby przeciążać liczbę argumentów zamiast typów argumentów.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Ukryj reprezentacje typów rekordów i Unii, jeśli projekt tych typów prawdopodobnie zostanie rozbudowany

Unikaj ujawniania konkretnych reprezentacji obiektów. Na przykład konkretna reprezentacja <xref:System.DateTime> wartości nie jest ujawniana przez zewnętrzny, publiczny interfejs API projektu biblioteki .NET. W czasie wykonywania środowisko uruchomieniowe języka wspólnego zna zatwierdzoną implementację, która będzie używana w czasie wykonywania. Jednak skompilowany kod nie sam wybiera zależności w konkretną reprezentację.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Unikaj stosowania dziedziczenia implementacji dla rozszerzalności

W języku F #, dziedziczenie implementacji jest rzadko używane. Ponadto hierarchie dziedziczenia są często skomplikowane i trudne do zmiany po nadejściu nowych wymagań. Implementacja dziedziczenia nadal istnieje w języku F # w celu zapewnienia zgodności i rzadkich przypadków, gdy jest to najlepsze rozwiązanie problemu, ale w programach F # należy odszukać alternatywne techniki w przypadku projektowania pod kątem polimorfizmu, takiego jak implementacja interfejsu.

### <a name="function-and-member-signatures"></a>Sygnatury funkcji i elementów członkowskich

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Użyj krotek dla zwracanych wartości podczas zwracania niewielkiej liczby niepowiązanych wartości

Oto dobry przykład użycia krotki w zwracanym typie:

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

Dla zwracanych typów zawierających wiele składników lub, gdy składniki są powiązane z pojedynczą identyfikowaną jednostką, należy rozważyć użycie nazwanego typu zamiast spójnej kolekcji.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Używanie `Async<T>` do programowania asynchronicznego w granicach interfejsu API języka F #

Jeśli istnieje odpowiadająca operacja synchroniczna o nazwie, `Operation` która zwraca obiekt `T` , operacja asynchroniczna powinna mieć nazwę, `AsyncOperation` jeśli zwraca `Async<T>` lub `OperationAsync` zwraca `Task<T>` . W przypadku często używanych typów platformy .NET, które uwidaczniają metody Begin/End, należy rozważyć użycie `Async.FromBeginEnd` programu w celu zapisania metod rozszerzających jako elewacji, aby zapewnić asynchroniczny model programowania F # dla tych interfejsów API platformy .NET.

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a>Wyjątki

Zobacz [zarządzanie błędami](conventions.md#error-management) , aby dowiedzieć się, jak korzystać z wyjątków, wyników i opcji.

### <a name="extension-members"></a>Elementy członkowskie rozszerzenia

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Starannie stosuj elementy członkowskie rozszerzenia F # w składnikach języka F # do-F #

Elementy członkowskie rozszerzeń języka F # powinny być zwykle używane tylko w przypadku operacji, które są w zamknięciu operacji wewnętrznych skojarzonych z typem w większości trybów użytkowania. Typowym zastosowaniem jest zapewnienie interfejsów API, które są bardziej idiomatyczne do F # dla różnych typów .NET:

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

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Używaj Unii rozłącznych zamiast hierarchii klas dla danych o strukturze drzewa

Struktury podobne do drzewa są zdefiniowane cyklicznie. Jest to niewygodna z dziedziczeniem, ale elegancki z związkami rozłącznych.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Przedstawianie danych o podobnej do drzewa z związkami rozłącznych pozwala również uzyskać wyczerpujące korzyści ze dopasowania wzorców.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Użycie `[<RequireQualifiedAccess>]` na typach Unii, których nazwy przypadków nie są wystarczająco unikatowe

Możesz się odszukać w domenie, w której ta sama nazwa jest najlepszą nazwą dla różnych rzeczy, takich jak przypadki Unii rozłącznych. Można użyć `[<RequireQualifiedAccess>]` , aby rozróżnić nazwy przypadków, aby uniknąć wyzwalania błędów spowodowanych przez zapełnienie w zależności od kolejności `open` instrukcji

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Ukryj reprezentacje związków rozłącznych dla zgodnych z binarnych interfejsów API, jeśli projekt tych typów prawdopodobnie zostanie rozbudowany

Typy Unii polegają na formularzach dopasowania wzorców języka F #, aby uzyskać zwięzły model programowania. Jak wspomniano wcześniej, należy unikać ujawniania konkretnych reprezentacji danych, jeśli projekt tych typów prawdopodobnie zostanie rozbudowany.

Na przykład reprezentacja związku rozłącznych może być ukryta przy użyciu prywatnej lub wewnętrznej deklaracji lub przy użyciu pliku sygnatury.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Jeśli ujawniane są odróżnienia związków rozłącznych, może się okazać, że trudno jest wersja biblioteki bez przerywania kodu użytkownika. Zamiast tego należy rozważyć ujawnienie jednego lub kilku aktywnych wzorców, aby umożliwić Dopasowywanie wzorców do wartości typu.

Aktywne wzorce oferują alternatywny sposób udostępniania konsumentom F # z dopasowywaniem do wzorców, jednocześnie unikając bezpośredniego udostępniania typów Unii języka F #.

### <a name="inline-functions-and-member-constraints"></a>Funkcje wbudowane i ograniczenia elementu członkowskiego

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Definiowanie ogólnych algorytmów liczbowych przy użyciu funkcji wbudowanych z implikowanymi ograniczeniami składowych i statycznie rozwiązanymi typami ogólnymi

Ograniczenia arytmetyczne elementu członkowskiego i ograniczenia języka F # są standardowym programowaniem w języku F #. Rozważmy na przykład następujący kod:

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

Jest to odpowiednia funkcja dla publicznego interfejsu API w bibliotece matematycznej.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Unikaj używania ograniczeń składowych, aby symulować klasy typów i nazwy kaczki

Istnieje możliwość symulowania "kaczania tekstu" przy użyciu ograniczenia elementu członkowskiego F #. Jednakże elementy członkowskie, które korzystają z tego nie powinny być ogólnie używane w projektach bibliotek języka F #-to-F #. Wynika to z faktu, że projekty biblioteki oparte na nieznanym lub niestandardowym ograniczeniu niejawnym powodują, że kod użytkownika staje się nieelastyczny i powiązany z jednym określonym wzorcem struktury.

Ponadto istnieje dobry szansa, że w ten sposób duże użycie ograniczeń składowych może skutkować bardzo długim czasem kompilowania.

### <a name="operator-definitions"></a>Definicje operatorów

#### <a name="avoid-defining-custom-symbolic-operators"></a>Unikaj definiowania niestandardowych operatorów symbolicznych

Operatory niestandardowe są niezbędne w niektórych sytuacjach i są wysoce przydatnymi urządzeniami do zapisu w dużej treści kodu implementacji. W przypadku nowych użytkowników biblioteki nazwane funkcje są często łatwiejsze w użyciu. Ponadto niestandardowe operatory symboliczne mogą być trudne do udokumentowania, a użytkownicy są trudniejsze do wyszukania pomocy dotyczącej operatorów, ze względu na istniejące ograniczenia dotyczące środowiska IDE i aparatów wyszukiwania.

W związku z tym najlepszym rozwiązaniem jest opublikowanie funkcji jako nazwanych funkcji i członków, a dodatkowo uwidocznienie operatorów dla tej funkcji tylko wtedy, gdy korzyści z notacji są większe niż dokumentację i koszty poznawcze.

### <a name="units-of-measure"></a>Jednostki miary

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Starannie korzystaj z jednostek miary, aby zwiększyć bezpieczeństwo typu w kodzie języka F #

Dodatkowe informacje o wpisywaniu jednostek miary są wymazywane podczas wyświetlania przez inne języki .NET. Należy pamiętać, że składniki, narzędzia i odbicie w programie .NET zobaczą typy-San-Units. Na przykład użytkownicy w języku C# będą widzieć `float` zamiast `float<kg>` .

### <a name="type-abbreviations"></a>Skróty typów

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Starannie używaj skrótów typów do uproszczenia kodu F #

Składniki programu .NET, narzędzia i odbicie nie będą widziały skróconych nazw typów. Znaczące użycie skrótów typu może sprawiać, że domena jest bardziej złożona niż rzeczywiście, co może mylić konsumentów.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Należy unikać skrótów typów dla publicznych typów, których elementy członkowskie i właściwości powinny być w sposób niezależny od tych, które są dostępne w skrócie typu

W takim przypadku skrócony typ ujawnia zbyt dużo informacji o reprezentowaniu określonego typu. Zamiast tego Rozważ zapakowanie skrótu w typie klasy lub Unii rozłącznej o pojedynczej wielkości liter (lub, jeśli wydajność jest istotna, rozważ użycie typu struktury do zawijania skrótu).

Na przykład jest to skłonność do definiowania wielomap jako specjalnego przypadku mapy języka F #, na przykład:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Jednak logiczne operacje notacji kropek na tym typie nie są takie same jak operacje na mapie — na przykład jest to uzasadnione, aby mapowanie operatora wyszukiwania było możliwe. [Key] Zwróć pustą listę, jeśli klucz nie znajduje się w słowniku, zamiast podnieść wyjątek.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Wskazówki dotyczące bibliotek do użycia w innych językach .NET

Podczas projektowania bibliotek do użycia w innych językach .NET ważne jest, aby przestrzegać [wytycznych dotyczących projektowania biblioteki .NET](../../standard/design-guidelines/index.md). W tym dokumencie te biblioteki są oznaczone jako biblioteka platformy .NET w formacie Wanili, w przeciwieństwie do bibliotek języka F #, które korzystają z konstrukcji F # bez ograniczeń. Projektowanie bibliotek programu .NET w postaci wanilii oznacza zapewnienie przyjaznych i idiomatyczne interfejsów API spójnych z pozostałą częścią .NET Framework przez zminimalizowanie użycia konstrukcji specyficznych dla języka F # w publicznym interfejsie API. Zasady są wyjaśnione w poniższych sekcjach.

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Przestrzeń nazw i projekt typu (dla bibliotek używanych w innych językach .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Stosowanie konwencji nazewnictwa platformy .NET do publicznego interfejsu API składników

Należy zwrócić szczególną uwagę na używanie skróconych nazw oraz wytycznych dotyczących wielkości liter w programie .NET.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Używanie przestrzeni nazw, typów i elementów członkowskich jako podstawowej struktury organizacyjnej składników

Wszystkie pliki zawierające funkcje publiczne powinny rozpoczynać się od `namespace` deklaracji, a jedyne publiczne jednostki w przestrzeniach nazw powinny być typami. Nie używaj modułów języka F #.

Używanie modułów niepublicznych do przechowywania kodu implementacji, typów narzędzi i funkcji narzędziowych.

Typy statyczne powinny być preferowane dla modułów, ponieważ umożliwiają przyszłe ewolucję interfejsu API w celu korzystania z przeciążeń i innych koncepcji projektowania interfejsów API platformy .NET, które nie mogą być używane w modułach języka F #.

Na przykład zamiast następującego publicznego interfejsu API:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

Zamiast tego Rozważ:

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Użyj typów rekordów języka F # w interfejsie API .NET w usłudze Wanili, jeśli projekt typów nie zostanie rozbudowany

Typy rekordów języka F # kompilują się do prostej klasy .NET. Są one odpowiednie dla niektórych prostych, stabilnych typów w interfejsach API. Rozważ użycie `[<NoEquality>]` atrybutów i, `[<NoComparison>]` Aby pominąć automatyczne generowanie interfejsów. Unikaj również używania modyfikowalnych pól rekordów w interfejsie API .NET w formacie Wanili, ponieważ uwidaczniają one pole publiczne. Należy zawsze rozważyć, czy Klasa zapewni bardziej elastyczną opcję dla przyszłego rozwoju interfejsu API.

Na przykład poniższy kod F # ujawnia publiczny interfejs API dla użytkownika w języku C#:

F#:

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
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

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Ukryj reprezentację typów Unii języka F # w interfejsach API platformy .NET w usłudze Wanili

Typy Unii języka f # nie są często używane między granicami składników, nawet w przypadku kodowania F #-to-F #. Są one doskonałym urządzeniem implementacji używanym wewnętrznie w ramach składników i bibliotek.

Podczas projektowania interfejsu API .NET w sieci Wanili, rozważ ukrycie reprezentacji typu złożenia przy użyciu prywatnej deklaracji lub pliku sygnatury.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Można również rozszerzyć typy, które używają reprezentacji Union wewnętrznie z elementami członkowskimi, aby zapewnić odpowiednie. Interfejs API w sieci.

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Projektowanie graficznego interfejsu użytkownika i innych składników przy użyciu wzorców projektu struktury

Istnieje wiele różnych struktur dostępnych w ramach platformy .NET, takich jak WinForms, WPF i ASP.NET. Nazwy i konwencje projektowania dla każdego z nich powinny być używane, jeśli projektujesz składniki do użycia w tych strukturach. Na przykład w przypadku programowania WPF należy przyjąć wzorce projektowania WPF dla projektowanych klas. W przypadku modeli w programowaniu interfejsu użytkownika Użyj wzorców projektowych, takich jak zdarzenia i kolekcje oparte na powiadomieniach, takie jak te, które znajdują się w <xref:System.Collections.ObjectModel> .

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Projekt obiektu i elementu członkowskiego (dla bibliotek używanych z innych języków .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Korzystanie z atrybutu CLIEvent w celu udostępnienia zdarzeń platformy .NET

Konstrukcja a `DelegateEvent` z określonym typem delegata platformy .NET, który przyjmuje obiekt i `EventArgs` (zamiast `Event` , który właśnie używa `FSharpHandler` typu domyślnie), aby zdarzenia były publikowane w znany sposób w innych językach .NET.

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a>Uwidacznianie operacji asynchronicznych jako metod, które zwracają zadania .NET

Zadania są używane w programie .NET do reprezentowania aktywnych asynchronicznych obliczeń. Zadania są generalnie mniejsze niż obiekty języka F # `Async<T>` , ponieważ reprezentują "już wykonywane" zadania i nie mogą być tworzone razem w sposób, który wykonuje równoległą kompozycję lub które ukrywają propagacje sygnałów anulowania i innych parametrów kontekstowych.

Jednak pomimo tego, metody zwracające zadania są standardową reprezentacją programowania asynchronicznego w programie .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Często trzeba również zaakceptować jawny token anulowania:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Użyj typów delegatów platformy .NET zamiast typów funkcji języka F #

W tym miejscu "typy funkcji języka F #" oznaczają ", takie jak `int -> int` .

Zamiast tego:

```fsharp
member this.Transform(f: int->int) =
    ...
```

Wykonaj następujące czynności:

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

Typ funkcji języka F # jest wyświetlany w `class FSharpFunc<T,U>` innych językach .NET i jest mniej odpowiedni dla funkcji języka i narzędzi, które są zrozumiałe dla typów delegatów. Podczas tworzenia metody wyższej kolejności docelowej .NET Framework 3,5 lub nowszej, `System.Func` `System.Action` Delegaty i są odpowiednie interfejsy API do opublikowania, aby umożliwić deweloperom platformy .NET korzystanie z tych interfejsów API w sposób słaby. (W przypadku określania wartości docelowej .NET Framework 2,0 typy delegatów zdefiniowane przez system są bardziej ograniczone; Rozważ użycie wstępnie zdefiniowanych typów delegatów, takich jak `System.Converter<T,U>` lub Definiowanie określonego typu delegata).

Na stronie Przerzucanie delegatów platformy .NET nie są naturalne dla bibliotek mających dostęp do języka F # (zobacz następną sekcję w bibliotekach przeznaczonych dla języka F #). W związku z tym typową strategią implementacji podczas opracowywania metod wyższego rzędu dla bibliotek .NET w formacie Wanili jest utworzenie całej implementacji przy użyciu typów funkcji języka F #, a następnie Tworzenie publicznego interfejsu API za pomocą delegatów jako wąskie fasada korzystającego rzeczywistą implementację języka F #.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Użyj wzorca TryGetValue zamiast zwracać wartości opcji F # i Preferuj przeciążanie metody w celu pobierania wartości opcji F # jako argumentów

Typowe wzorce użycia dla typu opcji języka F # w interfejsach API są lepiej zaimplementowane w interfejsie API platformy .NET w usłudze Wanili przy użyciu standardowych technik projektowania platformy .NET. Zamiast zwracać wartość opcji F #, rozważ użycie typu zwracanego bool oraz parametru out, jak w wzorcu "TryGetValue". Zamiast przyjmować wartości opcji F # jako parametry, należy rozważyć użycie przeciążania metod lub opcjonalnych argumentów.

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Użyj typów interfejsu kolekcji platformy .NET IEnumerable \< T \> i IDictionary \< , wartość \> parametrów i zwracanych wartości

Unikaj używania konkretnych typów kolekcji, takich jak tablice .NET `T[]` , typy języka F # `list<T>` , `Map<Key,Value>` oraz `Set<T>` typy kolekcji konkretnych dla platformy .NET, takich jak `Dictionary<Key,Value>` . Wskazówki dotyczące projektowania biblioteki .NET mają dobre porady dotyczące sytuacji, w których należy używać różnych typów kolekcji, takich jak `IEnumerable<T>` . Niektóre zastosowania tablic ( `T[]` ) są dopuszczalne w pewnych okolicznościach, z przyczyn związanych z wydajnością. Należy zwrócić uwagę `seq<T>` na to, że jest to tylko alias F # dla `IEnumerable<T>` , i w ten sposób sekwencja jest często odpowiednim typem dla interfejsu API .NET.

Zamiast list języka F #:

```fsharp
member this.PrintNames(names: string list) =
    ...
```

Użyj sekwencji języka F #:

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Użyj typu jednostki jako jedynego typu danych wejściowych metody do zdefiniowania metody zero lub jako jedynego zwracanego typu, aby zdefiniować metodę void-Return

Unikaj innych użycia typu jednostki. Są one dobre:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

To nie jest właściwe:

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Sprawdź pod kątem wartości null w granicach interfejsu API .NET Wanili

Kod implementacji języka F # ma mniejszą liczbę wartości null, ze względu na niezmienne wzorce projektowe i ograniczenia dotyczące używania literałów o wartości null dla typów języka F #. Inne języki .NET często używają wartości null, co jest znacznie częściej. Z tego względu kod języka F #, który uwidacznia interfejs API platformy .NET, powinien sprawdzać parametry dla wartości null na granicy interfejsu API i uniemożliwiać przepływanie tych wartości do kodu implementacji języka F #. `isNull`Można użyć funkcji lub dopasowania do wzorca na `null` wzorcu.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Unikaj używania krotek jako wartości zwracanych

Zamiast tego, Preferuj zwraca nazwany typ przechowujący zagregowane dane lub korzystając z parametrów out, aby zwracać wiele wartości. Chociaż krotki i krotek struktury istnieją w programie .NET (łącznie z obsługą języka C# dla krotek struktury), najczęściej nie zapewniają idealnego i oczekiwanego interfejsu API dla deweloperów platformy .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Unikaj używania currying parametrów

Zamiast tego należy używać konwencji wywoływania platformy .NET `Method(arg1,arg2,…,argN)` .

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Porada: Jeśli projektujesz biblioteki do użytku z dowolnego języka .NET, nie ma znaczenia dla faktycznego wykonywania niektórych eksperymentalnych języków C# i Visual Basic, aby upewnić się, że biblioteki "działają bezpośrednio" w tych językach. Możesz również użyć narzędzi takich jak reflektor .NET i program Visual Studio Przeglądarka obiektów, aby upewnić się, że biblioteki i ich dokumentacja będą wyglądały zgodnie z oczekiwaniami dla deweloperów.

## <a name="appendix"></a>Dodatek

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Kompleksowy przykład projektowania kodu języka F # do użycia przez inne języki .NET

Rozważmy następujące klasy:

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

Wywnioskowany typ F # tej klasy jest następujący:

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

Przyjrzyjmy się, jak ten typ języka F # jest widoczny dla programisty przy użyciu innego języka platformy .NET. Na przykład przybliżona "sygnatura" w języku C# jest następująca:

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

Istnieją pewne ważne punkty, które należy zwrócić uwagę na to, w jaki sposób F # reprezentuje konstrukcje. Przykład:

* Metadane, takie jak nazwy argumentów, zostały zachowane.

* Metody języka F #, które przyjmują dwa argumenty, stają się metodami języka C#, które przyjmują dwa argumenty.

* Funkcje i listy stają się odwołaniami do odpowiednich typów w bibliotece języka F #.

Poniższy kod pokazuje, jak dostosować ten kod, aby wziąć pod uwagę te zagadnienia.

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

Wywnioskowany typ F # jest następujący:

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

Sygnatura języka C# jest teraz następująca:

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

Poprawki wykonane w celu przygotowania tego typu do użycia w ramach biblioteki programu .NET w formacie Wanili są następujące:

* Zmieniono kilka nazw: `Point1` , `n` ,, `l` i `f` stała `RadialPoint` się, `count` , `factor` , i `transform` , odpowiednio.

* Użyto typu zwracanego `seq<RadialPoint>` zamiast `RadialPoint list` przez zmianę konstrukcji listy przy użyciu `[ ... ]` do konstrukcji sekwencji przy użyciu `IEnumerable<RadialPoint>` .

* Użyto typu delegata platformy .NET `System.Func` zamiast typu funkcji języka F #.

Pozwala to na korzystanie z kodu w języku C#.
