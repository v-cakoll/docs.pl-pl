---
title: 'F # składnika wytyczne dotyczące projektowania'
description: 'Dowiedz się, zalecenia dotyczące pisania F # składników przeznaczonych do użytku przez inne obiekty wywołujące.'
ms.date: 05/14/2018
ms.openlocfilehash: 446cba0f810af9517b655ef5741ddf7a919676d5
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43488290"
---
# <a name="f-component-design-guidelines"></a>F # składnika wytyczne dotyczące projektowania

W tym dokumencie to zestaw składników wytycznych projektowych dla języka F # programowania, w oparciu F # składnika wytycznych projektowych, wersja 14, Microsoft Research oraz [inna wersja](https://fsharp.org/specs/component-design-guidelines/) pierwotnie nadzorowane i obsługiwane przez F # Software Foundation.

W tym dokumencie przyjęto założenie, że czytelnik zna programowanie F #. Wiele dzięki społeczność języka F # ich wkład i przydatne opinie na temat różnych wersji tego przewodnika.

## <a name="overview"></a>Omówienie

W tym dokumencie patrzy na niektórych problemów związanych z F # składnika projektowania i kodowania. Składnik może oznaczać jedną z następujących czynności:

* Warstwy w projekcie języka F #, zawierającej klientów zewnętrznych w ramach tego projektu.
* Biblioteka przeznaczone do użytku przez kod F # poza granicami zestawu.
* Biblioteka przeznaczonych do użycia za pomocą dowolnego języka platformy .NET poza granicami zestawu.
* Biblioteka przeznaczone do dystrybucji za pośrednictwem repozytorium pakietów, takich jak [NuGet](https://nuget.org).

Postępuj zgodnie z metod opisanych w tym artykule [pięć zasadami dobrej kodzie języka F #](index.md#five-principles-of-good-f-code), dlatego korzystanie z obu funkcjonalności i obiekt programowania zgodnie z potrzebami.

Niezależnie od tego, metodologii składników i biblioteki projektanta twarzy szereg problemów praktycznych i prosaic podczas próby jednostki interfejsu API, który jest najłatwiej jest używany przez deweloperów. Sumienia stosowania [wytyczne dotyczące projektowania biblioteki .NET](../../standard/design-guidelines/index.md) kierowania do tworzenia spójny zestaw interfejsów API, które są przyjemne korzystać.

## <a name="general-guidelines"></a>Ogólne wskazówki

Istnieje kilka universal wskazówki, które dotyczą bibliotek F #, niezależnie od odbiorców dla biblioteki.

### <a name="learn-the-net-library-design-guidelines"></a>Dowiedz się, wytyczne dotyczące projektowania w bibliotece platformy .NET

Niezależnie od rodzaju F # kodowania, którą wykonujesz, jest przydatna dla ma praktyczną wiedzę na temat [wytyczne dotyczące projektowania biblioteki .NET](../../standard/design-guidelines/index.md). Większość innych F # programistów .NET będzie należy zapoznać się z tymi wytycznymi i oczekują kodu platformy .NET, które są zgodne z nich.

Wytyczne dotyczące projektowania dla biblioteki .NET zapewniają ogólne wskazówki dotyczące nazewnictwa, projektowanie klas i interfejsów, projekt elementu członkowskiego (właściwości, metody, zdarzenia itp.) i inne i są przydatne, pierwszy punkt odniesienia dla różnych wskazówki dotyczące projektowania.

### <a name="add-xml-documentation-comments-to-your-code"></a>Dodaj komentarze dokumentacji XML w kodzie

Dokumentacja XML w publicznych interfejsach API upewnij się, że użytkownicy będą mogli uzyskać doskonałe Intellisense i szybkich informacji podczas tych typów i elementów członkowskich i Włącz tworzenie dokumentacji plików biblioteki. Zobacz [dokumentacji XML](../language-reference/xml-documentation.md) o różne tagi xml, które mogą służyć do dodatkową marżę w ramach xmldoc komentarzy.

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

Możesz użyć albo komentarze XML krótka (`/// comment`), lub standardowych komentarzy XML (`///<summary>comment</summary>`).

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a>Należy wziąć pod uwagę przy użyciu plików jawne podpisu (.fsi) dla biblioteki stabilny, jak i składnika interfejsów API

Za pomocą jawnego podpisów plików w bibliotece F # zawiera zwięzły podsumowanie publicznego interfejsu API, który zarówno pomaga zapewnić, że możesz znać powierzchni publicznej biblioteki, a także umożliwia czystą separacji między publiczną dokumentację i wewnętrzne Szczegóły implementacji. Należy pamiętać, pliki podpisów dodać zajmowania się do zmiany publicznego interfejsu API, wymagając od zmian w plikach implementacji i podpis. W rezultacie plików sygnatur zwykle tylko należy wprowadzić po stają się zestalone interfejsu API oraz nie jest już oczekuje się znacznie zmieniać.

### <a name="always-follow-best-practices-for-using-strings-in-net"></a>Zawsze stosować najlepsze rozwiązania dotyczące używania ciągów w programie .NET

Postępuj zgodnie z [najlepsze rozwiązania dotyczące Using Strings in .NET](../../standard/base-types/best-practices-strings.md) wskazówki. W szczególności należy zawsze jawnie określać *kultury intencji* konwersji i porównanie ciągów (jeśli dotyczy).

## <a name="guidelines-for-f-facing-libraries"></a>Wytyczne dotyczące języka F #-połączonego z biblioteki

W tej sekcji przedstawiono zalecenia dotyczące tworzenia publicznego F #-połączonego z biblioteki; oznacza to, że biblioteki udostępnia publiczne interfejsy API, które są przeznaczone do użycia przez deweloperów F #. Istnieją różne zalecenia dotyczące projektowania biblioteki dotyczy w szczególności F #. W przypadku braku szczegółowe zalecenia, które należy wykonać wytyczne dotyczące projektowania dla biblioteki .NET są wskazówki rezerwowego.

### <a name="naming-conventions"></a>Konwencje nazewnictwa

#### <a name="use-net-naming-and-capitalization-conventions"></a>Użyj platformy .NET konwencji nazewnictwa i wielkości liter

Poniższa tabela jest zgodna z konwencjami nazewnictwa i wielkości liter, platformy .NET. Istnieją małe dodatki, aby obejmować konstrukcje F #.

| Konstrukcja | przypadek | Część | Przykłady | Uwagi |
|-----------|------|------|----------|-------|
| Typów konkretnych | PascalCase | Rzeczownik / przymiotników | Lista, Double, złożone | Konkretne typy są struktur, klas, wyliczeń, delegatów, rekordy i Unii. Chociaż nazwy typów są zazwyczaj pisane małymi literami w OCaml, F # przyjęła schemat nazewnictwa platformy .NET dla typów.
| biblioteki DLL           | PascalCase |                 | Fabrikam.Core.dll |  |
| Tagi Unii     | PascalCase | Rzeczownik | Niektóre z nich, Dodaj sukces | Nie używaj prefiksu w publicznych interfejsów API. Opcjonalnie użyj prefiksu, gdy wewnętrznych, takich jak "" wpisz zespołów = TAlpha | TBeta | TDelta. "" |
| Zdarzenie          | PascalCase | zlecenia | ValueChanged / ValueChanging |  |
| Wyjątki     | PascalCase |      | Klasa WebException | Nazwa powinna kończyć "Wyjątki". |
| Pole          | PascalCase | Rzeczownik | CurrentName  | |
| Typy interfejsów |  PascalCase | Rzeczownik / przymiotników | Interfejs IDisposable | Nazwa powinna rozpoczynać "I". |
| Metoda |  PascalCase |  zlecenia | ToString | |
| Przestrzeń nazw | PascalCase | | Microsoft.FSharp.Core | Na ogół używają `<Organization>.<Technology>[.<Subnamespace>]`, mimo że Porzuć organizacji, jeśli ta technologia jest niezależny od organizacji. |
| Parametry | camelCase | Rzeczownik |  Element typeName, przekształcania, zakresu | |
| Pozwól wartości (wewnętrzny) | camelCase lub PascalCase | Rzeczownik / zlecenia |  getValue, myTable |
| Pozwól wartości (zewnętrzne) | camelCase lub PascalCase | Rzeczownik/zlecenia  | List.map, Dates.Today | wartości powiązanym umożliwiają często są publiczne, gdy następujące wzorce projektowe funkcjonalności tradycyjnych. Jednak zazwyczaj użyć PascalCase identyfikator może być używana z innymi językami .NET. |
| Właściwość  | PascalCase  | Rzeczownik / przymiotników  | IsEndOfFile, kolor tła  | Operatory logiczne ogólnie użycie jest i może i powinno być twierdząca, tak jak IsEndOfFile, nie IsNotEndOfFile.

#### <a name="avoid-abbreviations"></a>Unikaj skrótów

Wskazówki .NET zniechęcać do używania skrótów (na przykład "Użyj `OnButtonClick` zamiast `OnBtnClick`"). Skrótów, takich jak `Async` dla "Asynchroniczne" są tolerowane. Ta wytyczna czasami jest ignorowany dla programowania funkcjonalności. na przykład `List.iter` używa skrót "iteracji". Z tego powodu, za pomocą skrótów zwykle tolerowane większym stopniu w języku F #-do-programowanie F #, ale nadal jest ogólnie należy unikać w projekcie składnik publiczny.

#### <a name="avoid-casing-name-collisions"></a>Należy unikać wielkość liter Kolizje nazw

Wskazówki .NET Załóżmy, że wielkość liter samodzielnie nie można użyć do odróżniania konfliktów nazw, ponieważ niektóre języki klienta (na przykład Visual Basic) jest rozróżniana wielkość liter.

#### <a name="use-acronyms-where-appropriate"></a>Użyj akronimów, gdzie jest to odpowiednie

Akronimów, takich jak XML nie są skróty i są powszechnie używane w bibliotekach .NET w postaci małymi (Xml). Tylko należy używać dobrze znanej i dobrze znana akronimów.

#### <a name="use-pascalcase-for-generic-parameter-names"></a>Użyj PascalCase dla nazw parametrów ogólnych

Na użytek PascalCase nazwy parametru ogólnego w publicznych interfejsów API, w tym w języku F #-połączonego z biblioteki. W szczególności należy używać nazw takich jak `T`, `U`, `T1`, `T2` dla dowolnych parametrów ogólnych, a gdy konkretne nazwy sensu, następnie w języku F #-bibliotek umożliwiający dostęp do Internetu Użyj nazwy, takie jak `Key`, `Value`, `Arg`(ale nie na przykład `TKey`).

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a>Na użytek PascalCase lub camelCase funkcji publicznych i wartości w modułach F #

camelCase służy do funkcji publicznych, które są przeznaczone do służyć niekwalifikowana (na przykład `invalidArg`) i "standardowe kolekcji funkcji" (na przykład List.map). W obu tych przypadkach nazwy funkcji działają podobnie jak słowa kluczowe w języku.

### <a name="object-type-and-module-design"></a>Obiekt, typ i moduł projektu

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a>Użyj przestrzeni nazw lub modułów, aby zawierać modułów i typów

Każdy plik F # w składniku powinien zaczynać się od deklaracji przestrzeni nazw lub deklaracja modułu.

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

* Przestrzenie nazw może obejmować wiele plików
* Przestrzenie nazw nie może zawierać funkcji F #, chyba że są one w moduł wewnętrzny
* Kod dla każdego danego modułu muszą znajdować się w jednym pliku
* Moduły najwyższego poziomu może zawierać funkcji F # bez konieczności moduł wewnętrzny

Wybór między przestrzeń nazw najwyższego poziomu lub moduł ma wpływ na formularzu skompilowanego kodu i związku z tym wpływają na widok z innymi językami .NET należy interfejsu API po pewnym czasie być używane poza kodzie języka F #.

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a>Użyj metody i właściwości dla operacji wewnętrznej do typów obiektów

Praca z obiektami, najlepiej upewnij się, że w użyciu jest implementowana jako metody i właściwości tego typu.

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

Większość funkcji dla danego elementu członkowskiego nie muszą zawsze zaimplementowana w tym elemencie członkowskim, ale powinien być w użyciu część tej funkcji.

#### <a name="use-classes-to-encapsulate-mutable-state"></a>Używanie klas do hermetyzacji modyfikowalnego stanu

W języku F # tylko musi to której odbywać, że stan nie jest już zamknięte przez innej konstrukcji języka, takich jak zamknięcie, wyrażenia sekwencji lub asynchroniczne obliczenie.

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a>Użyj interfejsów do grupowania działań związanych z

Typy interfejsów umożliwia reprezentuje zestaw operacji. To jest preferowana względem innych opcji, takie jak krotek funkcji lub rekordy funkcji.

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

Najwyższej jakości koncepcje na platformie .NET, którego można użyć do osiągnięcia, jakie Funktory będzie zwykle zapewniają są interfejsy. Ponadto może być używany do kodowania typów egzystencjalna do tego programu, który rejestruje funkcji nie może.

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a>Używaj modułu TPM funkcje grupy, które działają w kolekcjach

Podczas definiowania typem kolekcji, należy wziąć pod uwagę zapewnienie standardowy zestaw operacji, takich jak `CollectionType.map` i `CollectionType.iter`) dla nowych typów kolekcji.

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

Jeśli takie modułu, należy wykonać standardowe konwencje nazewnictwa dla funkcje dostępne w elemencie FSharp.Core.

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a>Używaj modułu TPM funkcje grupy do wspólnego, kanonicznej funkcji, szczególnie w przypadku matematyczne i biblioteki DSL

Na przykład `Microsoft.FSharp.Core.Operators` automatycznie otwierane zbiór funkcji najwyższego poziomu (np. `abs` i `sin`) dostarczonych przez FSharp.Core.dll.

Podobnie, biblioteka statystyki może obejmować modułu za pomocą funkcji `erf` i `erfc`, w którym ten moduł służy do można jawnie lub automatycznie otworzyć.

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a>Należy rozważyć użycie RequireQualifiedAccess i dokładnie Zastosuj AutoOpen — atrybuty

Dodawanie `[<RequireQualifiedAccess>]` atrybut do modułu wskazuje, że moduł nie może być otwarty i że odwołania do elementów moduł wymaga jawnego kwalifikowana dostępu. Na przykład `Microsoft.FSharp.Collections.List` moduł ma tego atrybutu.

Jest to przydatne, gdy funkcje i wartości w module mają nazwy, które mogą powodować konflikt z nazwami w innych modułach. Wymagające dostępu kwalifikowana może znacznie zwiększyć długoterminowe łatwość konserwacji i evolvability biblioteki.

Dodawanie `[<AutoOpen>]` atrybutu do modułu oznacza, że moduł zostanie otwarty po otwarciu zawierającej przestrzeni nazw. `[<AutoOpen>]` Atrybut ma również zastosowanie do zestawu, aby wskazać, moduł, który jest automatycznie otwierana, gdy odwołuje się do zestawu.

Na przykład, biblioteka statystyki **MathsHeaven.Statistics** może zawierać `module MathsHeaven.Statistics.Operators` zawierająca funkcje `erf` i `erfc`. Można oznaczyć ten moduł jako `[<AutoOpen>]`. Oznacza to, że `open MathsHeaven.Statistics` również spowoduje to otwarcie tego modułu i przenieść nazwy `erf` i `erfc` do zakresu. Użycie innego dobre `[<AutoOpen>]` dla modułów zawierających metody rozszerzenia.

Nadużywać z `[<AutoOpen>]` prowadzi do zanieczyszczonych przestrzenie nazw i atrybutu powinna być stosowana z rozwagą. Dla określonych bibliotek w określonych domenach, korzystać z `[<AutoOpen>]` może prowadzić do lepszego użyteczność.

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a>Należy rozważyć Definiowanie operatora członków w klasach, gdzie jest odpowiednia przy użyciu dobrze znanych operatorów

Czasami klasy służą do modelowania konstrukcje matematyczne, takie jak wektory. Kiedy domeny są modelowane ma dobrze znanym użytkownikom, definiując je jako elementy członkowskie wewnętrzne klasy jest pomocne.

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

Niniejsze wskazówki odpowiada ogólne wskazówki .NET dotyczące tych typów. Jednak może być dodatkowo ważne w F # kodowania, ponieważ pozwala ono tych typów, które ma być używany w połączeniu z F # funkcje i metody z ograniczeniami elementu członkowskiego, takie jak List.sumBy.

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a>Należy rozważyć użycie compiledname — w celu zapewnienia. NET — przyjazna nazwa dla innych klientów języka .NET

Czasami możesz chcieć nazw coś w jednym stylu dla konsumentów F # (takich jak statyczny element członkowski w małe litery, tak aby pojawił tak, jakby była to funkcja powiązane z modułu), ale mają różne style dla nazwy, gdy jest ona kompilowana do zestawu. Możesz użyć `[<CompiledName>]` atrybutu, aby zapewnić innego stylu dla kodu innego niż F #, korzystanie z zestawu.

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

Za pomocą `[<CompiledName>]`, można użyć konwencji nazewnictwa platformy .NET, innego niż F # w konsumentach napisanych zestawu.

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a>Użyj przeciążenie metody do funkcji elementu członkowskiego, jeśli w ten sposób zapewnia prostszy interfejs API

Przeciążenie metody jest zaawansowanym narzędziem internetowym upraszczającym interfejsu API, który może być konieczne wykonanie podobne funkcje, ale z różnych opcji lub argumentów.

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

W języku F # jest bardziej powszechne, aby można było przeciążyć na liczbę argumentów, a nie typy argumentów.

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a>Ukryj liczbami w postaci rekordu i typy Unii, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji

Unikaj ujawniania konkretnych reprezentacje obiektów. Na przykład konkretny reprezentacja <xref:System.DateTime> wartości nie została ujawniona przez zewnętrzny, publiczny interfejs API projektu biblioteki .NET. W czasie wykonywania środowisko uruchomieniowe języka wspólnego wie, implementacja zatwierdzone, używanym w całym wykonywania. Jednak kod skompilowany nie sam przejmą zależności od konkretnych reprezentacji.

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a>Unikaj stosowania dziedziczenia implementacji rozszerzalności

W języku F # jest rzadko używana implementacja dziedziczenia. Ponadto hierarchii dziedziczenia najczęściej złożonej i trudnej można zmienić po nadejściu nowych wymagań. Implementacja dziedziczenia nadal istnieje w języku F # dla zgodności i rzadkich przypadkach, gdy jest to najlepsze rozwiązanie problemu, ale techniki alternatywnego należy dążyć w swoich programach F # podczas projektowania dla polimorfizmu, takich jak implementacji interfejsu.

### <a name="function-and-member-signatures"></a>Sygnatury funkcji i elementów członkowskich

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a>Używaj krotek dla wartości zwracanych, gdy zwracany jest niewielka liczba wielu niepowiązanych wartości

W tym miejscu jest dobrym przykładem korzystania z krotki w typ zwracany:

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

Zwracane typy zawierające wiele składników lub w przypadku, gdy składniki są powiązane z pojedynczą jednostkę do zidentyfikowania, należy rozważyć użycie typu nazwanego zamiast spójnej kolekcji.

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a>Użyj `Async<T>` dla programowania asynchronicznego na granicach interfejsu API języka F #

Jeśli jest odpowiednia Operacja synchroniczna, o nazwie `Operation` zwracającego `T`, powinien zostać nazwany operacji asynchronicznej, a następnie `AsyncOperation` Jeśli zwróci ona `Async<T>` lub `OperationAsync` Jeśli zwróci ona `Task<T>`. Dla często używanych typów .NET, które ujawniają początek/koniec metody, należy wziąć pod uwagę przy użyciu `Async.FromBeginEnd` do zapisania metody rozszerzenia jako fasada zapewnienie F # asynchronicznego modelu programowania do tych interfejsów API platformy .NET.

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

Zobacz [zarządzanie błędami](conventions.md#error-management) Aby dowiedzieć się więcej na temat właściwego użycia, wyjątków, wyniki i opcje.

### <a name="extension-members"></a>Elementy członkowskie rozszerzeń

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a>Dokładnie zastosować F # elementy członkowskie rozszerzeń w języku F #-do-F # składników

Elementy członkowskie rozszerzeń F # powinien ogólnie można używać tylko dla operacji, które znajdują się w zamknięcia wewnętrzne operacje skojarzone z typem w większości jej trybów użytkowania. Jeden z najczęściej używanych jest zapewnienie interfejsów API, które są bardziej idiomatyczną do F # dla różnych typów .NET:

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

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a>Na użytek dyskryminowanych związków zamiast hierarchii klas strukturze drzewa danych

Struktury drzewa są rekursywnie zdefiniowane. Jest niewygodna za pomocą dziedziczenia, ale elegancki za pomocą sumy rozłączne.

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

Efektywna reprezentacja danych drzewa za pomocą sumy rozłączne umożliwia również korzystać z kompletności w dopasowywania do wzorca.

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a>Użyj `[<RequireQualifiedAccess>]` na typy Unii, w których wielkość nazwy nie są wystarczająco unikatowe

Może się okazać się w domenie, gdzie takiej samej nazwie jest najlepszą nazwę dla różnych rzeczy, takich jak przypadków Unii rozłącznej. Możesz użyć `[<RequireQualifiedAccess>]` do rozróżniania wielkości liter nazwy w celu uniknięcia wyzwalania błędy myląca ze względu na przesłanianie zależne od kolejność `open` instrukcji

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a>Ukryj reprezentacje sumy rozłączne binarne zgodnych interfejsów API, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji

Typy Unii korzystają ze F # dopasowania do wzorca formularzy zwięzłą modelu programowania. Jak wspomniano wcześniej, należy unikać, odsłaniając reprezentacje konkretnych danych, jeśli projekt tych typów jest prawdopodobnie podlegać ewolucji.

Na przykład, reprezentacja złożenia dyskryminowanego mogą być ukrywane przy użyciu deklarację prywatne lub wewnętrzne lub przy użyciu pliku podpisu.

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

Jeśli sumy rozłączne są ujawnione masowe, może okazać się trudne do wersji biblioteki bez przerywania kod użytkownika. Zamiast tego należy wziąć pod uwagę przedstawiania co najmniej jeden wzorce aktywne, aby umożliwić dopasowywanie wzorców względem wartości tego typu.

Wzorce aktywne zapewniają alternatywny sposób zapewnienie konsumentów F # za pomocą wzorca dopasowania unikając bezpośrednio udostępnianie typów złożenia F #.

### <a name="inline-functions-and-member-constraints"></a>Funkcje śródwierszowe i ograniczeniami elementu członkowskiego

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a>Zdefiniuj ogólnego algorytmy numeryczne, za pomocą wbudowanych funkcji z ograniczeniami elementu członkowskiego domniemane i statycznie rozwiązany typów ogólnych

Ograniczenia Członkowskie arytmetyczne i ograniczenia porównania F # są standardowe rozwiązanie dla programowania w języku F #. Na przykład rozważmy następujący kod:

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

Typ tej funkcji jest następująca:

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

To jest odpowiednia funkcja publicznego interfejsu API w bibliotekę funkcji matematycznych.

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a>Unikaj korzystania z ograniczeniami elementu członkowskiego symulacji klasy typów i wpisując kaczka

Istnieje możliwość zasymulować "kacze, wpisując" przy użyciu języka F # ograniczeniami elementu członkowskiego. Jednak elementy członkowskie, które należy użyć tego ogólne nie należy używać w języku F #-do-projekty biblioteki F #. Jest tak, ponieważ projekty biblioteki, na podstawie nieznaną lub niestandardową niejawne ograniczeń, które mogą spowodować, że kod użytkownika do stają się sztywny i wiązanej wzorcem jednej określonej struktury.

Ponadto jest dobrym pomysłem, która intensywnie korzysta z ograniczeniami elementu członkowskiego w ten sposób może spowodować czasy kompilacji bardzo długi.

### <a name="operator-definitions"></a>Definicje — operator

#### <a name="avoid-defining-custom-symbolic-operators"></a>Unikaj definiowania niestandardowych operatorów symboliczne

Operatory niestandardowe są niezbędne w niektórych sytuacjach i są bardzo przydatne notational urządzeń znajdujących się w dużej części kodu realizacji. Nowi użytkownicy biblioteki nazwane funkcje są często łatwiejsze w użyciu. Ponadto niestandardowych operatorów symboliczne może być trudne do dokumentu, a użytkownicy znaleźć trudniej uzyskać pomoc dotyczącą operatorów, ze względu na ograniczenia istniejącego w IDE i wyszukiwania aparaty wyszukiwania.

W rezultacie warto publikować własne funkcje jako nazwane funkcje i elementy członkowskie, a dodatkowo ujawnić operatory dla tej funkcji, tylko wtedy, gdy przeważają korzyści notational, dokumentacji i cognitive koszt oni.

### <a name="units-of-measure"></a>Jednostki miary

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a>Dokładnie użycia jednostek miary bezpieczeństwo typów dodanych w kodzie języka F #

Dodatkowe informacje Pisownia jednostki miary są usuwane w przypadku widocznej z innymi językami .NET. Należy pamiętać, że składniki .NET, narzędzia i odbicia będą widzieć typy sieci SAN, jednostek. Na przykład C# będą widzieli `float` zamiast `float<kg>`.

### <a name="type-abbreviations"></a>Skróty typów

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a>Dokładnie uprościć kod F # za pomocą skróty typów

Składniki .NET, narzędzia i odbicia nie będą widzieć skrócone nazwy dla typów. Znaczne wykorzystanie skróty typów można również ustawić domenę pojawiają się faktycznie jest bardziej złożone niż, który może mylić konsumentów.

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a>Unikaj skrótów typu dla typów publicznych, na których elementy członkowskie i właściwości powinny różnić się wewnętrznie do tych, które są dostępne wobec typu jest skracana

W tym przypadku typ jest skrócona, co spowoduje wyświetlenie zbyt dużo o reprezentujący rzeczywisty typ zostały zdefiniowane. Zamiast tego należy wziąć pod uwagę zawijania — skrót typu klasy lub pojedynczym przypadku złożenia dyskryminowanego (lub, jeśli wydajność ma podstawowe, należy wziąć pod uwagę przy użyciu typu struktury do opakowania skrót).

Na przykład jest kuszące do definiowania wielu map w szczególnych przypadkach F # mapy, na przykład:

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

Jednak operacje logiczne notacji z kropką dla tego typu nie są takie same, jak operacje na mapie — na przykład, jest uzasadnione, że operator wyszukiwania mapy. Zwróć [klucza] pusta lista, jeśli klucz nie znajduje się w słowniku, zamiast zgłaszania wyjątku.

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a>Wytyczne dotyczące biblioteki do użycia z innymi językami .NET

Podczas projektowania biblioteki do użycia z innymi językami .NET, należy stosować się do [wytyczne dotyczące projektowania biblioteki .NET](../../standard/design-guidelines/index.md). W tym dokumencie biblioteki te są oznaczone jako podstawowego bibliotek .NET, w przeciwieństwie do F #-połączonego z bibliotek, które używają F # tworzy bez ograniczeń. Projektowanie wanilii bibliotek .NET oznacza, że zapewnienie znanego i idiomatyczną interfejsów API zgodne z pozostałą częścią programu .NET Framework, minimalizując użycie języka F #-określonych konstrukcje w publicznym interfejsie API. Zasady zostały wyjaśnione w poniższych sekcjach.

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a>Namespace i typu projektu (w przypadku biblioteki do użycia z innymi językami .NET)

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a>Zastosuj konwencji nazewnictwa platformy .NET do publicznego interfejsu API składniki

Należy zwrócić szczególną uwagę na użycie skrócone nazwy i wytyczne dotyczące użycia wielkich liter .NET.

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a>Użyj przestrzeni nazw, typów i elementów członkowskich jako podstawowej struktury organizacyjnej składników

Wszystkie pliki zawierające publiczny funkcji powinna zaczynać się od `namespace` deklaracji i tylko jednostki publicznymi w przestrzeniach nazw powinny być typów. Nie należy używać modułów F #.

Użyj modułach niepubliczna zawierającą kod implementacji, typy narzędzia i funkcje narzędziowe.

Typy statyczne powinny mieć pierwszeństwo modułów, ponieważ umożliwiają one pod kątem przyszłego rozwoju interfejsu API do użycia przeciążania operacji i innych interfejsu API platformy .NET zagadnienia dotyczące projektowania, które nie mogą być używane w modułach F #.

Na przykład, zamiast następujące publicznego interfejsu API:

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

Rozważ zamiast tego:

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a>Używać typów rekordów F # w vanilla interfejsów API platformy .NET, jeśli projekt typy nie będą ewoluować

Typy rekordów F # kompilacji do prostych klasy .NET. Są one odpowiednie dla niektóre typy proste i stabilne interfejsy API. Należy rozważyć użycie `[<NoEquality>]` i `[<NoComparison>]` atrybutów, które mają pominąć automatyczne generowanie interfejsów. Należy też unikać stosowania pól rekordu mutable w vanilla interfejsów API platformy .NET jako tych ujawnia pole publiczne. Zawsze należy rozważyć, czy klasa zapewni bardziej elastycznych opcji pod kątem przyszłego rozwoju interfejsu API.

Na przykład poniższy kod F # ujawnia publiczny interfejs API użytkownika języka C#:

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

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a>Ukryj reprezentacja typów F # Unii w vanilla interfejsów API platformy .NET

Typy Unii F # nie są powszechnie używane przez granice składnika, nawet w przypadku F #-do-F # kodowania. Są one urządzenia doskonałą implementacji, gdy jest używana wewnętrznie w ramach składniki i biblioteki.

Podczas projektowania vanilla interfejsu API platformy .NET, należy wziąć pod uwagę ukrywanie reprezentacja typu złożenia przy użyciu prywatnego deklaracji lub plik podpisu.

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

Może także rozszerzyć typy, które umożliwia reprezentację złożenia wewnętrznie z elementami członkowskimi zapewniają odpowiednią. Interfejs API skierowaną do sieci.

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a>Projekt graficzny interfejs użytkownika i inne składniki, korzystania z wzorców projektowania Framework

Brak dostępnych wiele różnych platform w ramach platformy .NET, takich jak WinForms, WPF i programu ASP.NET. Konwencje nazewnictwa i projektowania dla każdego należy używać w przypadku projektowania składniki do użycia w tych platform. Na przykład dla programowania WPF, należy przyjąć WPF wzorców projektowych dla klas, które projektowania. W przypadku modeli w programowaniu interfejsu użytkownika, użyj wzorce projektowe, takich jak zdarzenia i kolekcje oparte na powiadomienie, takich jak znaleźć w <xref:System.Collections.ObjectModel>.

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a>Projektowanie obiektów i elementów członkowskich (w przypadku biblioteki do użycia z innymi językami .NET)

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a>Umożliwia udostępnianie zdarzeń .NET clievent — atrybut

Konstruowania `DelegateEvent` przy użyciu określonej platformy .NET należy przekazać typ, który przyjmuje obiekt i `EventArgs` (zamiast `Event`, który używa `FSharpHandler` typu domyślnie), aby zdarzenia są publikowane w dobrze znana metoda innymi językami .NET.

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

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a>Uwidacznianie operacji asynchronicznych jako metody, które zwracają zadania platformy .NET

Zadania są używane na platformie .NET do reprezentowania aktywnego asynchronicznych obliczeń. Zadania są ogólnie rzecz biorąc, mniej składu niż F # `Async<T>` obiektów, ponieważ reprezentuje zadania "już wykonuje", a nie może być ze sobą w sposób, które wykonują równolegle kompozycji, lub który ukryć propagacji anulowania sygnały i innych Parametry kontekstowe.

Jednak mimo to metody, które zwracają zadania są standardowa reprezentacja programowanie asynchroniczne na platformie .NET.

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

Często obejmuje także do akceptowania tokenu anulowania jawne:

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a>Użyj typów obiektów delegowanych .NET zamiast typów F # — funkcja

W tym miejscu "typów F # funkcja" oznacza "strzałkę" typów, takich jak `int -> int`.

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

Typu funkcji F # jest wyświetlany jako `class FSharpFunc<T,U>` do innych języków platformy .NET jest mniej odpowiednia dla funkcji języka i narzędzi, które zrozumieć typy delegatów. Podczas tworzenia metody wyższego rzędu przeznaczone dla .NET Framework 3.5 lub nowszego, `System.Func` i `System.Action` obiekty delegowane są odpowiednie interfejsy API w celu publikowania umożliwia deweloperom platformy .NET do korzystania z tych interfejsów API w sposób prostego. (Podczas określania wartości docelowej platformy .NET Framework 2.0, typy zdefiniowane przez system delegatów są bardziej ograniczone; należy wziąć pod uwagę przy użyciu wstępnie zdefiniowanego delegata typy, takie jak `System.Converter<T,U>` lub definiujący typ określonego obiektu delegowanego.)

Po drugiej stronie delegatów .NET nie są fizyczną w języku F #-połączonego z biblioteki (zobacz następną sekcję F #-połączonego z bibliotekami). W wyniku typowych strategii wdrażania podczas tworzenia metody wyższego rzędu do wanilii bibliotek .NET jest tworzyć wszystkie wdrożenia za pomocą funkcji typów F #, a następnie utwórz publiczny interfejs API przy użyciu delegatów jako fasada alokowania elastycznego na jego podstawie rzeczywistej F # Implementacja.

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a>Użyj wzorca TryGetValue zamiast zwracać wartości opcji F # i wolisz przeciążenie metody do uwzględnienia wartości opcji F # jako argumenty

Typowe wzorce użycia typu opcji F # w interfejsach API są lepsze zaimplementowane w vanilla techniki projektowania interfejsów API platformy .NET przy użyciu platformy .NET standard. Zamiast zwracać wartość opcji F #, należy wziąć pod uwagę przy użyciu zwracanego typu wartość logiczna, a także parametru wyjściowego tak jak wzorzec "TryGetValue". I zamiast wartości opcji F # jako parametry, należy wziąć pod uwagę przy użyciu przeciążenie metody lub argumenty opcjonalne.

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a>Korzystając z platformy .NET kolekcji typów IEnumerable\<T\> i IDictionary\<klucz, wartość\> dla parametrów i zwracanych wartości

Należy unikać użycia kolekcji konkretnych typów, takich jak tablice platformy .NET `T[]`, typów F # `list<T>`, `Map<Key,Value>` i `Set<T>`, i typy kolekcji konkretny .NET, takie jak `Dictionary<Key,Value>`. Wytyczne dotyczące projektowania dla biblioteki .NET mają dobrej porad dotyczących kiedy należy używać różnych typów kolekcji, takich jak `IEnumerable<T>`. Użyj tablic (`T[]`) jest dopuszczalna w pewnych okolicznościach, na podstawie wydajności. Należy pamiętać, że szczególnie `seq<T>` jest po prostu języka F # alias dla `IEnumerable<T>`, i dlatego seq jest często odpowiednich typów vanilla interfejsu API platformy .NET.

Zamiast list języka F #:

```fsharp
member this.PrintNames(names : string list) =
    ...
```

Sekwencje F #:

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a>Użyj tego typu jednostki jako jedyny typ danych wejściowych metody do definiowania metody zero argument lub jako tylko zwraca typ, aby zdefiniować metodę zwracającą typ void

Należy unikać inne zastosowania tego typu jednostki. Są one dobrym:

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

To jest nieprawidłowy:

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a>Sprawdzanie pod kątem wartości null wanilii granice interfejsu API platformy .NET

Kod implementacji F # zwykle mają mniejszą liczbę wartości null, ze względu na wzorce projektowe niezmienne i ograniczenia związane z użyciem literały null dla typów F #. Innymi językami .NET często używają wartości null jako wartość znacznie częściej. W związku z tym kodzie języka F #, który jest uwidaczniany vanilla interfejsu API platformy .NET należy sprawdzić parametry o wartości null na granicy interfejsu API i te wartości uniemożliwiają otrzymywanych przez lepszy kod implementacji F #. `isNull` Funkcji lub dopasowania do wzorca w `null` wzorca można użyć.

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a>Unikaj korzystania z krotek jako wartości zwracane

Zamiast tego wolisz, zwracająca Typ nazwany, rezerwowanie zagregowane dane lub korzystanie z parametrów out zwracanie wielu wartości. Mimo że krotek struktur i kolekcje objęte .NET (w tym obsługa języka C# dla krotek struktur), będą w większości przypadków nie zapewniają idealne i oczekiwanego interfejsu API dla deweloperów platformy .NET.

#### <a name="avoid-the-use-of-currying-of-parameters"></a>Unikaj stosowania currying parametrów

Zamiast tego należy użyć konwencji wywoływania .NET ``Method(arg1,arg2,…,argN)``.

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

Porada: Jeśli projektujesz biblioteki do użycia z dowolnego języka platformy .NET, występuje nie zastąpi faktycznie wykonywania niektórych eksperymentalne języka C# i Visual Basic programowania do upewnij się, że bibliotek "działania po prawej" z tych języków. Narzędzia takie jak reflektor .NET i przeglądarki obiektów usługi Visual Studio umożliwia również upewnić się, że bibliotek i ich dokumentację są wyświetlane zgodnie z oczekiwaniami dla deweloperów.

## <a name="appendix"></a>Dodatek

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a>Przykład end-to-end projektowania kodzie języka F # do użytku przez innymi językami .NET

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

Wnioskowany Typ F # tej klasy jest następująca:

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

Spójrzmy na sposób wyświetlania tego typu F # do programisty, użycie innego języka .NET. Na przykład przybliżony języka C# "podpis" jest w następujący sposób:

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

Istnieją pewne ważne punkty, które informacja dotycząca jak F # reprezentuje konstrukcje w tym miejscu. Na przykład:

* Metadane, takie jak nazwy argumentów została zachowana.

* F # metod, które przyjmują dwa argumenty stają się języka C# metod, które przyjmują dwa argumenty.

* Funkcje i listy stają się odwołania do odpowiadające typy w bibliotece programu F #.

Poniższy kod pokazuje, jak dostosować ten kod w celu uwzględnienia tych rzeczy.

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

Wnioskowany Typ F # kodu jest następująca:

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

* Skorygowane kilka nazw: `Point1`, `n`, `l`, i `f` stało się `RadialPoint`, `count`, `factor`, i `transform`, odpowiednio.

* Zwracany typ używany `seq<RadialPoint>` zamiast `RadialPoint list` , zmieniając konstruowania listy przy użyciu `[ ... ]` do konstruowania sekwencji za pomocą `IEnumerable<RadialPoint>`.

* Używany typ delegata .NET `System.Func` zamiast typu funkcji F #.

Dzięki temu znacznie wrażeń korzystanie w kodzie języka C#.
