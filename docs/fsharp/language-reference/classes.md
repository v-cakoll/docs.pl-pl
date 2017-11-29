---
title: Klasy (F#)
description: "Dowiedz się, jak klas F # są typy, które reprezentują obiektów, które mogą mieć właściwości, metod i zdarzeń."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: d58679d5-7753-4b3b-a12f-6e9f00ed5ba3
ms.openlocfilehash: 2a73baba1f7c1b0d3bd09d22c9d6d9f0524daef3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
Klasy reprezentuje opis podstawowych typów obiektu .NET. Klasa jest koncepcji typu podstawowego, który obsługuje programowanie zorientowane obiektowo w języku F #.

W powyższej składni `type-name` jest dowolny poprawny identyfikator. `type-params` Opisano parametry opcjonalne typu ogólnego. Składa się z nazwy parametrów typu i ograniczenia ujęte w nawiasy (`<` i `>`). Aby uzyskać więcej informacji, zobacz [ogólne](generics/index.md) i [ograniczenia](generics/constraints.md). `parameter-list` Opisuje parametrami konstruktora. Pierwszy modyfikator dostępu odnoszą się do tego typu; Druga odnosi się do podstawowego konstruktora. W obu przypadkach wartość domyślna to `public`.

Określ klasę podstawową dla klasy przy użyciu `inherit` — słowo kluczowe. Należy podać argumentów konstruktora klasy podstawowej, w nawiasach.

Deklaruj pól lub wartości, które znajdują się lokalnie do klasy przy użyciu funkcji `let` powiązania i wykonaj ogólne zasady `let` powiązania. `do-bindings` Sekcja zawiera kod do wykonania po konstrukcji obiektów.

`member-list` Składa się z konstruktorów dodatkowe, wystąpienia i deklaracje metody statycznej deklaracji interfejsów, abstrakcyjny powiązania i deklaracje właściwości i zdarzenia. Te ustawienia zostały opisane w [członków](members/index.md).

`identifier` Używany z opcjonalnym `as` — słowo kluczowe nadaje nazwę zmiennej instancji lub własnego identyfikatora, którego można użyć do odwoływania się do wystąpienia typu w definicji typu. Aby uzyskać więcej informacji zobacz sekcję samoobsługowego identyfikatorów w dalszej części tego tematu.

Słowa kluczowe `class` i `end` oznakowanie początek i koniec definicji są opcjonalne.

Wzajemnie typy cyklicznego, do których są typy, które odwołują się do siebie, są połączone razem z `and` tak samo jak wzajemnie są funkcje rekursywne — słowo kluczowe. Na przykład zobacz sekcję wzajemnie rekursywne typów.


## <a name="constructors"></a>Konstruktorów
Konstruktor jest kod, który tworzy wystąpienie typu klasy. Konstruktory klas działają trochę inaczej w F # niż w innych językach .NET. W F # klasa, jest zawsze podstawowego konstruktora, którego argumenty zostały opisane w `parameter-list` następujący nazwa typu, a których treści składa się z `let` (i `let rec`) powiązania na początku deklaracji klasy i `do`powiązania, które należy wykonać. Argumenty konstruktora głównej znajdują się w zakresie w deklaracji klasy.

Możesz dodać dodatkowe konstruktorów przy użyciu `new` — słowo kluczowe, aby dodać element członkowski, w następujący sposób:

`new`(`argument-list`) = `constructor-body`

Treść konstruktora new należy wywołać konstruktora podstawowego, który został określony na początku deklaracji klasy.

Poniższy przykład ilustruje tę koncepcję. W poniższym kodzie `MyClass` ma dwa konstruktory, podstawowego konstruktora, który przyjmuje dwa argumenty i innego konstruktora, który nie przyjmuje żadnych argumentów.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2401.fs)]
    
## <a name="let-and-do-bindings"></a>Let i powiązania

`let` i `do` powiązania w definicji klasy tworzą treść konstruktora klasy podstawowej i w związku z tym są uruchamiane zawsze, gdy jest tworzone wystąpienie klasy. Jeśli `let` powiązania jest funkcją, a następnie jest on skompilowany do członka. Jeśli `let` powiązanie to wartość, która nie jest używany w żadnych funkcji lub elementu członkowskiego, a następnie jest on skompilowany w zmiennej, która jest lokalny dla konstruktora. W przeciwnym razie jest kompilowana do pola klasy. `do` Wyrażeń, które należy wykonać są kompilowane do podstawowego konstruktora i wykonywanie kodu inicjowania dla każdego wystąpienia. Ponieważ żadnych dodatkowych konstruktorów zawsze wywołać konstruktora podstawowego, `let` powiązania i `do` powiązania wykonać zawsze, niezależnie od tego, które jest nazywany konstruktora.

Pola, które zostały utworzone przy użyciu `let` powiązania są dostępne w ramach metod i właściwości klasy; jednak ich jest niedostępny z metody statyczne, nawet w przypadku statycznej metody przyjmują zmienna wystąpienia jako parametr. Nie były dostępne przy użyciu własnego identyfikatora, jeśli taka istnieje.


## <a name="self-identifiers"></a>Samoidentyfikatory

A *własnego identyfikatora* jest nazwą, która reprezentuje bieżącego wystąpienia. Podobne samoidentyfikatory `this` słów kluczowych w języku C# lub C++ lub `Me` w języku Visual Basic. Można zdefiniować własnego identyfikatora na dwa różne sposoby, w zależności od tego, czy ma własnego identyfikatora znajdował się w zakresie dla definicji klasy całego lub tylko dla poszczególnych metod.

Aby zdefiniować własnego identyfikatora dla całej klasy, należy użyć `as` — słowo kluczowe po nawiasów zamykających parametru konstruktora listę i określ nazwę identyfikatora.

Aby zdefiniować własnego identyfikatora dla tylko jednej metody, podaj własnego identyfikatora w deklaracji elementu członkowskiego, bezpośrednio przed nazwę metody i kropki (.) jako separatora.

Poniższy przykładowy kod przedstawia dwa sposoby tworzenia własnego identyfikatora. W pierwszym wierszu `as` — słowo kluczowe jest używane do definiowania własnego identyfikatora. W wierszu piątym identyfikator `this` służy do definiowania własnego identyfikatora, których zakres jest ograniczony do metody `PrintMessage`.

```fsharp
type MyClass2(dataIn) as self =
    let data = dataIn
    do
        self.PrintMessage()
    member this.PrintMessage() =
        printf "Creating MyClass2 with Data %d" data
```

W przeciwieństwie do innych języków .NET, można określić nazwę własnego identyfikatora jednak ma; użytkownik nie są ograniczone do nazw takich jak `self`, `Me`, lub `this`.

Własnego identyfikatora, który jest zadeklarowana z `as` — słowo kluczowe nie został zainicjowany dopiero po `let` powiązania są wykonywane. W związku z tym nie można używać w `let` powiązania. Można użyć własnego identyfikatora w `do` sekcji powiązania.


## <a name="generic-type-parameters"></a>Parametry typu ogólnego

Parametry typu ogólnego są określone w nawiasy (`<` i `>`), w postaci pojedynczego cudzysłowu następuje identyfikator. Wiele parametrów typu ogólnego są oddzielone przecinkami. Parametr typu ogólnego jest w zakresie całego zgłoszenia. Poniższy przykład kodu pokazuje, jak określić parametry typu ogólnego.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2403.fs)]

Gdy jest używany typ, są wywnioskować argumentów typu. W poniższym kodzie wnioskowany typ jest sekwencją spójnych kolekcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet24031.fs)]
    
## <a name="specifying-inheritance"></a>Określanie dziedziczenia

`inherit` Klauzuli identyfikuje bezpośredniej klasie podstawowej, jeśli istnieje. W języku F # jest dozwolony tylko jeden bezpośredniej klasie podstawowej. Interfejsy, które implementuje klasy nie są traktowane jako klasy podstawowe. Interfejsy zostały omówione w [interfejsów](Interfaces.md) tematu.

Dostępne metody i właściwości klasy podstawowej z klasy pochodnej przy użyciu słowa kluczowego języka `base` identyfikatorowi następuje znak kropki (.) i nazwa elementu członkowskiego.

Aby uzyskać więcej informacji, zobacz [dziedziczenia](inheritance.md).


## <a name="members-section"></a>Elementy członkowskie sekcji
W tej sekcji można zdefiniować statyczne lub wystąpienie metody, właściwości implementacje interfejsu, abstrakcyjne elementy członkowskie, deklaracje zdarzeń i dodatkowych konstruktorów. Pozwalają oraz czy powiązania nie może występować w tej sekcji. Ponieważ można dodawać członków do różnych typów F # oprócz klas, zostały omówione w innym temacie [członków](members/index.md).


## <a name="mutually-recursive-types"></a>Wzajemnie rekursywne typów
Po zdefiniowaniu typów odwołujące się do siebie nawzajem w sposób cykliczne można łączyć ze sobą definicje typów za pomocą `and` — słowo kluczowe. `and` Zastępuje — słowo kluczowe `type` — słowo kluczowe na wszystkich z wyjątkiem pierwsza definicja w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2404.fs)]

Dane wyjściowe znajduje się lista wszystkich plików w bieżącym katalogu.


## <a name="when-to-use-classes-unions-records-and-structures"></a>Kiedy używać klas, Unii, rekordów i struktury
Biorąc pod uwagę różne typy do wyboru, musisz mieć dobrą znajomość co każdego typu jest przeznaczona dla wybierz odpowiedni typ dla danej sytuacji. Klasy są przeznaczone do użytku w kontekście programowania, zorientowany obiektowo. Programowanie zorientowane obiektowo jest dominującą modelu, używany w aplikacjach, które są przeznaczone dla programu .NET Framework. Jeśli ściśle współpracować z programu .NET Framework lub inną biblioteką zorientowane obiektowo kodzie języka F #, a zwłaszcza, jeśli masz system zorientowane obiektowo typów, takich jak biblioteki interfejsu użytkownika związane z klasy są prawdopodobnie odpowiednie.

Jeśli użytkownik nie są ściśle współdziałanie z kodem zorientowane obiektowo lub pisania kodu, która jest niezależna i dlatego chronione z częste interakcji z kodem zorientowane obiektowo, należy rozważyć użycie rekordów i Suma rozłączna Unii. Jeden również myśl — limit czasu rozróżnianą Unię wraz z odpowiednią wzorzec dopasowany kodu, można często prostsze alternatywę do hierarchii obiektów. Aby uzyskać więcej informacji na temat rozłączne, zobacz [Suma rozłączna unie](discriminated-unions.md).

Rekordy zostały zaletą jest łatwiejsze niż w przypadku klasy, ale rekordy nie są odpowiednie wymagania typu przekracza, co można zrobić z ich uproszczenia. Rekordy są zasadniczo proste agreguje wartości, bez konstruktorów oddzielne, które może wykonywać akcje niestandardowe, bez ukryte pola i bez implementacji dziedziczenia lub interfejsu. Mimo że elementy członkowskie, takie jak właściwości i metod można dodać do rekordów do wykonania ich zachowanie bardziej złożonych, proste agregacji wartości są nadal pola przechowywane w rekordzie. Aby uzyskać więcej informacji na temat rekordów, zobacz [rekordów](records.md).

Struktury są także przydatne dla małych wartości zagregowanych danych, ale różnią się od klasy i rekordów są typy wartości .NET. Klasy i rekordów są typy referencyjne .NET. Semantyka typów wartości i typy referencyjne są różne, w tym typy wartości są przekazywane przez wartość. Oznacza to, że są one kopiowane bit bitu, gdy są one przekazywane jako parametr lub zwracane przez funkcję. Są one również przechowywane na stosie lub, jeśli są używane jako pole osadzony w obiekcie nadrzędnym zamiast przechowywane w ich własnych osobnych lokalizacji na stosie. W związku z tym struktury są odpowiednie dla często używanych danych, gdy obciążenie podczas uzyskiwania dostępu do sterty problem. Aby uzyskać więcej informacji na temat struktury, zobacz [struktury](structures.md).


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)

[Elementy członkowskie](members/index.md)

[Dziedziczenie](inheritance.md)

[Interfejsy](interfaces.md)

