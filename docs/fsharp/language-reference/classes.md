---
title: Klasy (F#)
description: 'Dowiedz się, jak klas F # są typy, które reprezentują obiektów, które mogą mieć właściwości, metod i zdarzeń.'
ms.date: 05/16/2016
ms.openlocfilehash: 71cd713d192d28565e879b79b2fc9e0530e5f841
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47401358"
---
# <a name="classes"></a>Klasy

*Klasy* są typy, które reprezentują obiektów, które mogą mieć właściwości, metod i zdarzeń.

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

Klasy reprezentują opis podstawowych typów obiektów .NET; Klasa jest pojęciem typu podstawowego, który obsługuje programowanie zorientowane obiektowo w F #.

W poprzedniej składni `type-name` jest dowolnym prawidłowym identyfikatorem. `type-params` Opisano parametry opcjonalne typu ogólnego. Składa się z nazwy parametrów typu i ograniczenia, ujęte w nawiasy (`<` i `>`). Aby uzyskać więcej informacji, zobacz [ogólne](generics/index.md) i [ograniczenia](generics/constraints.md). `parameter-list` Opisano parametry konstruktora. Pierwszy modyfikator dostępu odnoszą się do typu; druga dotyczy tylko podstawowy Konstruktor. W obu przypadkach wartość domyślna to `public`.

Należy określić klasę bazową dla klasy za pomocą `inherit` — słowo kluczowe. Musisz podać argumenty w nawiasach dla konstruktora klasy bazowej.

Deklaruj pól lub wartości, które są lokalne w klasie za pomocą funkcji `let` powiązania, na które należy wykonać ogólne reguły dotyczące `let` powiązania. `do-bindings` Sekcja zawiera kod do wykonania po konstrukcji obiektu.

`member-list` Składa się z konstruktorów dodatkowe, wystąpienia i deklaracje metody statyczne, deklaracji interfejsu, abstrakcyjna powiązania i deklaracje właściwości i zdarzenia. Te ustawienia zostały opisane w [członków](members/index.md).

`identifier` Używanego z opcjonalnym `as` — słowo kluczowe umożliwia nadanie nazwy zmiennej wystąpienia lub własny identyfikator, który może służyć w definicji typu do odwoływania się do wystąpienia typu. Aby uzyskać więcej informacji zobacz sekcję Self identyfikatorów w dalszej części tego tematu.

Słowa kluczowe `class` i `end` oznakowanie początek i koniec definicji są opcjonalne.

Wzajemnie typów cyklicznych, które są typów odwołujących się do siebie nawzajem, są połączone razem z `and` — słowo kluczowe tak, ponieważ wzajemnie funkcji rekursywnych. Aby uzyskać przykład zobacz sekcję wzajemnie typów cyklicznych.

## <a name="constructors"></a>Konstruktorów

Konstruktor jest kod, który tworzy wystąpienie typu klasy. Konstruktory dla klas działają trochę inaczej w języku F # niż w innych językach .NET. W F # klasy, jest zawsze konstruktora podstawowego, w której argumenty są opisane w `parameter-list` występujący na nazwę typu, a których treść składa się z `let` (i `let rec`) powiązania na początku deklaracji klasy `do`powiązania, które należy wykonać. Argumenty konstruktora podstawowego znajdują się w zakresie deklaracji klasy.

Możesz dodać dodatkowe konstruktory przy użyciu `new` — słowo kluczowe do dodania elementu członkowskiego, w następujący sposób:

`new`(`argument-list`) = `constructor-body`

Treść nowego konstruktora musi zostać wywołany podstawowy Konstruktor, który jest określony na początku deklaracji klasy.

Poniższy przykład ilustruje tę koncepcję. W poniższym kodzie `MyClass` ma dwa konstruktory, podstawowy Konstruktor, który przyjmuje dwa argumenty i innego konstruktora, który nie przyjmuje żadnych argumentów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]

## <a name="let-and-do-bindings"></a>Let, a powiązania

`let` i `do` powiązania w definicji klasy tworzą treść konstruktora klasy podstawowej i dlatego są one uruchamiane zawsze, gdy tworzone jest wystąpienie klasy. Jeśli `let` powiązania jest funkcją, a następnie jest kompilowany do elementu członkowskiego. Jeśli `let` powiązanie to wartość, która nie jest używany w żadnych funkcji lub elementu członkowskiego, a następnie jest kompilowany do zmiennej, która jest lokalny dla konstruktora. W przeciwnym razie jest kompilowana do pola klasy. `do` Wyrażeń, które należy wykonać są kompilowane do konstruktora podstawowego i wykonywania kodu inicjowania dla każdego wystąpienia. Ponieważ żadnych dodatkowych konstruktorów zawsze wywołanie konstruktora podstawowego, `let` powiązania i `do` powiązania wykonania zawsze, niezależnie od tego, które wywoływany jest Konstruktor.

Pola, które są tworzone przez `let` powiązania są dostępne w ramach metod i właściwości klasy; jednak nie będą dostępne z metody statyczne, nawet w przypadku statycznej metody przyjmują zmienną instance jako parametr. Nie będą dostępne za pomocą własny identyfikator, jeśli taka istnieje.

## <a name="self-identifiers"></a>Samoidentyfikatory

A *własny identyfikator* jest nazwą, która reprezentuje bieżącego wystąpienia. Samoidentyfikatory przypominają `this` — słowo kluczowe w języku C# lub C++ lub `Me` w języku Visual Basic. Można zdefiniować własny identyfikator na dwa różne sposoby, w zależności od tego, czy ma własny identyfikator, aby się mieścić w zakresie dla definicji całą klasę lub tylko dla poszczególnych metod.

Aby zdefiniować własny identyfikator dla całej klasy, należy użyć `as` — słowo kluczowe po nawiasów zamykających parametru konstruktora listy, a następnie podaj nazwę identyfikatora.

Aby zdefiniować własny identyfikator tylko jedną metodę, Podaj własny identyfikator w deklaracji elementu członkowskiego, tuż przed nazwy metody i kropki (.) jako separatora.

Poniższy przykładowy kod przedstawia dwa sposoby, aby utworzyć własny identyfikator. W pierwszym wierszu `as` — słowo kluczowe jest używane do definiowania własny identyfikator. W wierszu piątym identyfikator `this` służy do definiowania własny identyfikator, których zakres jest ograniczony do metody `PrintMessage`.

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

Inaczej niż w innych językach .NET, możesz nazwać własny identyfikator jednak ma; nie jest ograniczona do nazw takich jak `self`, `Me`, lub `this`.

Własny identyfikator, który jest zadeklarowana za pomocą `as` — słowo kluczowe nie jest zainicjowany aż po `let` powiązania są wykonywane. W związku z tym, nie można używać w `let` powiązania. Można użyć własny identyfikator w `do` sekcję wiązania.

## <a name="generic-type-parameters"></a>Parametry typu ogólnego

Parametry typu ogólnego są określone w nawiasy ostre (`<` i `>`), w postaci pojedynczy znak cudzysłowu, a następnie identyfikatora. Wiele parametrów typu ogólnego są oddzielone przecinkami. Parametr typu ogólnego znajduje się w zakresie deklaracji. Poniższy przykład kodu pokazuje sposób określania parametrów typu genetycznego.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Argumenty typu są wnioskowane, gdy typ jest używany. W poniższym kodzie wnioskowany typ to sekwencja krotek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]

## <a name="specifying-inheritance"></a>Określanie dziedziczenia

`inherit` Klauzula identyfikuje bezpośrednie klasy bazowej, jeśli taka istnieje. W języku F # jest dozwolony tylko jedną bezpośrednią klasą bazową. Interfejsy, które implementuje klasa nie są uwzględniane klas bazowych. Interfejsy są omówione w [interfejsów](Interfaces.md) tematu.

Dostępne metody i właściwości klasy bazowej z klasy pochodnej za pomocą słowa kluczowego języka `base` jako identyfikator, a następnie kropka (.) i nazwę elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [dziedziczenia](inheritance.md).

## <a name="members-section"></a>Sekcja elementy członkowskie

W tej sekcji można zdefiniować statyczne lub metody wystąpienia, właściwości, implementacje interfejsu, abstrakcyjne składowe, deklaracji zdarzeń i dodatkowych konstruktorów. Let, a następnie wykonaj wiązania nie może występować w tej sekcji. Ponieważ elementy Członkowskie mogą być dodawane do różnych typów F # oprócz klas, zostały omówione w osobnych tematach [członków](members/index.md).

## <a name="mutually-recursive-types"></a>Wzajemnie typów cyklicznych

Podczas definiowania typów odwołujące się do siebie nawzajem w sposób cykliczne, możesz łączyć ze sobą definicje typów przy użyciu `and` — słowo kluczowe. `and` Zastępuje słowo kluczowe `type` — słowo kluczowe na wszystkie z wyjątkiem pierwszej definicji, w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Dane wyjściowe znajduje się lista wszystkich plików w bieżącym katalogu.

## <a name="when-to-use-classes-unions-records-and-structures"></a>Kiedy należy używać klas, Unii, rekordy i struktury

Biorąc pod uwagę różne typy do wyboru, musisz dysponować dobrą znajomością programu co każdy typ jest przeznaczona dla wybrać odpowiedni typ w konkretnej sytuacji. Klasy są przeznaczone do użytku w kontekstach programowania obiektowego. Programowanie zorientowane obiektowo jest dominującym paradygmat, używany w aplikacjach, które zostały napisane dla platformy .NET Framework. Jeśli kod F # jest bliska współpraca z .NET Framework lub innej biblioteki zorientowane obiektowo, a zwłaszcza, jeśli zajdzie potrzeba rozszerzyć system zorientowane obiektowo typów, takich jak biblioteka interfejsów użytkownika, klasy są prawdopodobnie odpowiednie.

Czy można nie są ściśle współdziałanie z kodem zorientowane obiektowo, czy piszesz kod, który jest niezależna i w związku z tym chronione przed interakcja z kodem zorientowane obiektowo, należy wziąć pod uwagę przy użyciu rekordów i związków wyróżniających. Jeden dobrze myślenia — limit czasu złożenia dyskryminowanego, wraz z odpowiednią wzorzec dopasowywania kodu, często może służyć jako prostszej alternatywy hierarchii obiektów. Aby uzyskać więcej informacji na temat sumy rozłączne zobacz [sumy rozłączne](discriminated-unions.md).

Rekordy mają zaletą jest prostsze niż klasy, ale rekordy nie są odpowiednie wymagania typu przekracza, co można zrobić z ich prostotę. Rekordy są zasadniczo prostych wartości zagregowanych wartości bez oddzielne konstruktorów, które mogą wykonywać akcje niestandardowe, bez ukrytych pól i bez implementacji dziedziczenie lub interfejs. Chociaż składowych, takich jak właściwości i metody mogą być dodawane do rekordów się bardziej złożone ich zachowania, pola, przechowywane w rekordzie są nadal prostych agregacji wartości. Aby uzyskać więcej informacji na temat rekordów, zobacz [rekordów](records.md).

Struktury są także przydatne dla małej wartości zagregowanych danych, ale różnią się one z klas i dokumentów, ponieważ są typami wartości platformy .NET. Klasy i rekordy są typami odwołań platformy .NET. Semantyka typów wartości i typami odwołania są różne, w tym typy wartości są przekazywane przez wartość. Oznacza to, że są one kopiowane bit bitu, gdy są one przekazane jako parametr lub zwracany przez funkcję. One są także przechowywane w stosie lub, jeśli są one używane jako pole osadzone wewnątrz obiektu nadrzędnego, a nie przechowywany w ich własnych oddzielnej lokalizacji na stosie. W związku z tym struktur są odpowiednie dla rzadziej używanych danych, gdy obciążenie uzyskiwania dostępu do stosu problem. Aby uzyskać więcej informacji na temat struktur, zobacz [struktury](structures.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Elementy członkowskie](members/index.md)
- [Dziedziczenie](inheritance.md)
- [Interfejsy](interfaces.md)
