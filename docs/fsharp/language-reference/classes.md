---
title: Klasy
description: Dowiedz F# się, w jaki sposób klasy są typami reprezentującymi obiekty, które mogą mieć właściwości, metody i zdarzenia.
ms.date: 05/16/2016
ms.openlocfilehash: 5c012d028bc1f89e3e9f5969b3461faab9aad3a0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630442"
---
# <a name="classes"></a>Klasy

*Klasy* są typami reprezentującymi obiekty, które mogą mieć właściwości, metody i zdarzenia.

## <a name="syntax"></a>Składnia

```fsharp
// Class definition:
type [access-modifier] type-name [type-params] [access-modifier] ( parameter-list ) [ as identifier ] =
[ class ]
[ inherit base-type-name(base-constructor-args) ]
[ let-bindings ]
[ do-bindings ]
member-list
...
[ end ]
// Mutually recursive class definitions:
type [access-modifier] type-name1 ...
and [access-modifier] type-name2 ...
...
```

## <a name="remarks"></a>Uwagi

Klasy reprezentują podstawowy opis typów obiektów .NET; Klasa jest koncepcją typu podstawowego, która obsługuje programowanie zorientowane obiektowo w F#.

W powyższej składni, `type-name` jest dowolnym prawidłowym identyfikatorem. `type-params` Opisuje opcjonalne parametry typu ogólnego. Składa się z nazw parametrów typu i ograniczeń ujętych w nawiasy `>`kątowe (`<` i). Aby uzyskać więcej informacji, zobacz [typy ogólne](./generics/index.md) i [ograniczenia](./generics/constraints.md). `parameter-list` Opisuje parametry konstruktora. Pierwszy modyfikator dostępu dotyczy typu; sekunda odnosi się do głównego konstruktora. W obu przypadkach wartość domyślna to `public`.

Należy określić klasę bazową dla klasy za pomocą `inherit` słowa kluczowego. W nawiasach należy podać argumenty dla konstruktora klasy bazowej.

Deklaruj pola lub wartości funkcji, które są lokalne dla klasy przy użyciu `let` powiązań, i musisz przestrzegać ogólnych `let` reguł powiązań. `do-bindings` Sekcja zawiera kod, który ma być wykonywany podczas konstruowania obiektu.

`member-list` Składa się z dodatkowych konstruktorów, wystąpień i deklaracji metody statycznej, deklaracji interfejsu, powiązań abstrakcyjnych oraz deklaracji właściwości i zdarzenia. Są one opisane w obszarze [Członkowie](./members/index.md).

Funkcja, która jest używana ze słowem kluczowym Optional `as` , zawiera nazwę zmiennej wystąpienia lub samego identyfikatora, która może być używana w definicji typu do odwoływania się do wystąpienia typu. `identifier` Aby uzyskać więcej informacji, zobacz sekcję Identyfikatory własne w dalszej części tego tematu.

Słowa kluczowe `class` i `end` oznaczenie początku i końca definicji są opcjonalne.

Wzajemnie cykliczne typy, które są, które są wzajemnie odwołują się, są `and` sprzężone ze słowem kluczowym, tak jak funkcje wzajemnie cykliczne. Aby zapoznać się z przykładem, zobacz sekcję wzajemnie cykliczne typy.

## <a name="constructors"></a>Konstruktorów

Konstruktor to kod, który tworzy wystąpienie typu klasy. Konstruktory dla klas działają nieco inaczej F# niż w innych językach .NET. W F# klasie jest zawsze konstruktorem podstawowym, którego argumenty są opisane w `parameter-list` , która następuje po nazwie typu i którego `let` treść składa się z powiązań (i `let rec`) na początku deklaracji klasy i `do` powiązania, które obserwują. Argumenty konstruktora podstawowego znajdują się w zakresie w całej deklaracji klasy.

Można dodać więcej konstruktorów za pomocą `new` słowa kluczowego, aby dodać element członkowski w następujący sposób:

`new`(`argument-list`) = `constructor-body`

Treść nowego konstruktora musi wywoływać konstruktora podstawowego, który jest określony w górnej części deklaracji klasy.

Poniższy przykład ilustruje tę koncepcję. W poniższym kodzie, `MyClass` ma dwa konstruktory, Konstruktor podstawowy, który przyjmuje dwa argumenty i inny Konstruktor, który nie przyjmuje argumentów.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>Powiązania let i do

Powiązania `let` i`do` w definicji klasy tworzą treść konstruktora klasy podstawowej i dlatego są uruchamiane za każdym razem, gdy tworzone jest wystąpienie klasy. `let` Jeśli powiązanie jest funkcją, zostanie ona skompilowana do elementu członkowskiego. `let` Jeśli powiązanie jest wartością, która nie jest używana w żadnej funkcji lub składowej, jest skompilowana do zmiennej, która jest lokalna dla konstruktora. W przeciwnym razie jest kompilowany do pola klasy. `do` Wyrażenia, które obserwują, są kompilowane do konstruktora podstawowego i wykonywanie kodu inicjacji dla każdego wystąpienia. Ponieważ wszystkie dodatkowe konstruktory zawsze wywołują konstruktora podstawowego, `let` powiązania i `do` powiązania zawsze są wykonywane niezależnie od tego, który Konstruktor jest wywoływany.

Do pól tworzonych przez `let` powiązania można uzyskać dostęp w metodach i właściwościach klasy, jednak nie są one dostępne z metod statycznych, nawet jeśli metody statyczne przyjmują zmienną wystąpienia jako parametr. Nie można uzyskać do nich dostępu za pomocą identyfikatora własnego (jeśli taki istnieje).

## <a name="self-identifiers"></a>Identyfikatory własne

Samodzielny *Identyfikator* to nazwa, która reprezentuje bieżące wystąpienie. `this` Identyfikatory własne przypominają słowo kluczowe w C# lub C++ lub `Me` w Visual Basic. Można zdefiniować własny identyfikator na dwa różne sposoby, w zależności od tego, czy identyfikator samodzielny ma być w zakresie dla całej definicji klasy, czy tylko dla pojedynczej metody.

Aby zdefiniować samodzielny identyfikator dla całej klasy, użyj `as` słowa kluczowego po nawiasach zamykających listy parametrów konstruktora i podaj nazwę identyfikatora.

Aby zdefiniować samodzielny identyfikator dla tylko jednej metody, należy podać własny identyfikator w deklaracji elementu członkowskiego, tuż przed nazwą metody i kropką (.) jako separatorem.

Poniższy przykład kodu ilustruje dwa sposoby tworzenia identyfikatorów samodzielnych. W pierwszym wierszu `as` słowo kluczowe jest używane do definiowania własnego identyfikatora. W piątym wierszu identyfikator `this` jest używany do definiowania samego identyfikatora, którego zakres jest ograniczony do metody. `PrintMessage`

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

W przeciwieństwie do innych języków .NET, można nazwać swój identyfikator własny. nie są ograniczone do nazw takich jak `self`, `Me`, lub `this`.

Sam identyfikator, który jest zadeklarowany za `as` pomocą słowa kluczowego, nie został `let` zainicjowany do momentu wykonania powiązań. W związku z tym nie można jej używać `let` w powiązaniach. Możesz użyć własnego identyfikatora w `do` sekcji powiązania.

## <a name="generic-type-parameters"></a>Parametry typu ogólnego

Parametry typu ogólnego są określane w nawiasach kątowych `>`(`<` i) w postaci pojedynczego cudzysłowu, po którym następuje identyfikator. Wiele parametrów typu ogólnego jest oddzielonych przecinkami. Parametr typu ogólnego jest w zakresie w całej deklaracji. Poniższy przykład kodu pokazuje, jak określić parametry typu ogólnego.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Argumenty typu są wywnioskowane, gdy typ jest używany. W poniższym kodzie typ wnioskowany jest sekwencją krotek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Określanie dziedziczenia

`inherit` Klauzula identyfikuje bezpośrednią klasę bazową, jeśli istnieje. W F#programie dozwolona jest tylko jedna bezpośrednia klasa bazowa. Interfejsy implementowane przez klasę nie są uważane za klasy bazowe. Interfejsy zostały omówione w temacie [interfejsy](Interfaces.md) .

Można uzyskać dostęp do metod i właściwości klasy podstawowej z klasy pochodnej przy użyciu słowa kluczowego `base` Language jako identyfikatora, po którym następuje kropka (.) i nazwa elementu członkowskiego.

Aby uzyskać więcej informacji, [](inheritance.md)Zobacz dziedziczenie.

## <a name="members-section"></a>Sekcja członkowie

Można definiować metody statyczne lub wystąpienia, właściwości, implementacje interfejsów, abstrakcyjne elementy członkowskie, deklaracje zdarzeń i dodatkowe konstruktory w tej sekcji. W tej sekcji nie można wyświetlać powiązań let i do. Ponieważ elementy członkowskie mogą być dodawane do różnych F# typów Oprócz klas, są one omówione w osobnych tematach, elementach [członkowskich](./members/index.md).

## <a name="mutually-recursive-types"></a>Wzajemnie cykliczne typy

W przypadku definiowania typów, które odwołują się do siebie w sposób cykliczny, można ciągować razem definicje typu `and` za pomocą słowa kluczowego. `and` Słowo kluczowe `type` zastępuje słowo kluczowe dla wszystkich oprócz pierwszej definicji w następujący sposób.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Dane wyjściowe to lista wszystkich plików w bieżącym katalogu.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Kiedy używać klas, Unii, rekordów i struktur

Uwzględniając różne typy do wyboru, należy dobrze zrozumieć, co każdy typ jest przeznaczony do wyboru w celu wybrania odpowiedniego typu dla konkretnej sytuacji. Klasy są przeznaczone do użycia w kontekstach programowania zorientowanego obiektowo. Programowanie zorientowane obiektowo to dominujący model używany w aplikacjach, które są napisywane dla .NET Framework. Jeśli F# kod musi ściśle współpracować z .NET Framework lub inną biblioteką zorientowaną obiektowo, a zwłaszcza w przypadku, gdy konieczne jest przeciągnięcie z systemu typu zorientowanego obiektowo, takiego jak biblioteka UI, klasy są prawdopodobnie odpowiednie.

Jeśli nie prowadzisz ścisłej współpracy z kodem zorientowanym obiektowo lub jeśli piszesz kod, który jest niezależny i dlatego jest chroniony przed częste interakcje z kodem zorientowanym obiektowo, należy rozważyć użycie rekordów i Unii rozłącznych. Pojedyncza, dobrze przemyślana Unia, wraz z odpowiednim kodem zgodnym z wzorcem, może być często używana jako uproszczona alternatywa dla hierarchii obiektów. Aby uzyskać więcej informacji na temat związków rozłącznych, zobacz [związki](discriminated-unions.md)rozłączne.

Rekordy mają zalety uproszczenia niż klasy, ale rekordy nie są odpowiednie, gdy wymagania typu wykraczają poza to, co można osiągnąć przy użyciu prostoty. Rekordy są zasadniczo prostymi agregacjami wartości bez oddzielnych konstruktorów, które mogą wykonywać niestandardowe akcje, bez ukrytych pól i bez dziedziczenia lub implementacji interfejsów. Mimo że elementy członkowskie, takie jak właściwości i metody, można dodać do rekordów, aby zachować zachowanie bardziej złożone, pola przechowywane w rekordzie nadal są prostą agregacją wartości. Aby uzyskać więcej informacji o rekordach, zobacz [rekordy](records.md).

Struktury są również przydatne w przypadku małych zagregowanych danych, ale różnią się od klas i rekordów, które są typami wartości .NET. Klasy i rekordy są typami odwołań platformy .NET. Semantyka typów wartości i typów referencyjnych różni się w zależności od wartości. Oznacza to, że są one kopiowane bit dla bitu, gdy są przesyłane jako parametr lub zwracane z funkcji. Są one również przechowywane na stosie lub, jeśli są używane jako pola osadzone w obiekcie nadrzędnym, a nie przechowywane we własnej osobnej lokalizacji na stercie. W związku z tym struktury są odpowiednie dla często używanych danych, gdy narzuty dostępu do sterty jest problemem. Aby uzyskać więcej informacji na temat struktur, zobacz [struktury](structures.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Elementy członkowskie](./members/index.md)
- [Dziedziczenie](inheritance.md)
- [Interfejsy](interfaces.md)
