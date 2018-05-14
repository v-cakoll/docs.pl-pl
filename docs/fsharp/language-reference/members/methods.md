---
title: Metody (F#)
description: 'Dowiedz się, jak metoda F # jest skojarzony z typem służą do ujawnia i implementuje funkcje i zachowanie obiektów i typów funkcji.'
ms.date: 05/16/2016
ms.openlocfilehash: 6e0b0789d97a9671425fb08c56c84ba1f66dfbe6
ms.sourcegitcommit: e5bb395ec86f536e114314184288f40a8c745e2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2018
---
# <a name="methods"></a>Metody

A *metody* to funkcja, która jest skojarzona z typem. W programowanie zorientowane obiektowo metody są używane ujawnia i wdrażanie funkcji oraz zachowanie obiektów i typów.


## <a name="syntax"></a>Składnia

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a>Uwagi
W poprzednich składni widać różne formy — metoda deklaracje i definicje. W treści metody dłużej podział wiersza następuje znak równości (=) i tworzone jest wcięcie całej treści.

Atrybuty można zastosować do dowolnego deklaracji metody. One poprzedzać składnia definicję metody i zazwyczaj są wyświetlane w osobnym wierszu. Aby uzyskać więcej informacji, zobacz [atrybutów](../attributes.md).

Można oznaczyć metody `inline`. Aby uzyskać informacje o `inline`, zobacz [funkcji śródwierszowych](../functions/inline-functions.md).

Inne niż wbudowane metody mogą być używane rekursywnie w ramach typu; nie istnieje potrzeba aby jawnie używać `rec` — słowo kluczowe.


## <a name="instance-methods"></a>Wystąpienie metody
Metody wystąpienia są deklarowane jako z `member` — słowo kluczowe i *własny identyfikator*, a następnie kropki (.) oraz nazwę metody i parametry. Podobnie jak w przypadku dla `let` powiązań, *listy parametrów* może być wzorcem. Zwykle to ująć metodę, której parametry w nawiasach w postaci spójnej kolekcji, czyli metody sposób są wyświetlane w języku F # tworzona w innych językach .NET Framework. Jednak rozwinięte formularza (rozdzielone spacjami parametry) jest również typowe i innymi wzorami są również obsługiwane.

Poniższy przykład przedstawia definicja oraz wykorzystanie metody wystąpienia nieabstrakcyjnej.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

Wewnątrz metody wystąpienia nie należy używać własnego identyfikatora do pola dostępu zdefiniowane za pomocą powiązania let. Użyć własnego identyfikatora podczas uzyskiwania dostępu do innych elementów członkowskich i właściwości.


## <a name="static-methods"></a>Metody statyczne
Słowo kluczowe `static` służy do określania, czy można wywołać metody bez wystąpienia i nie jest skojarzony z wystąpieniem obiektu. W przeciwnym razie metody to metody wystąpienia.

W przykładzie w następnej sekcji przedstawiono pola zadeklarowana z `let` — słowo kluczowe, właściwości elementów członkowskich zadeklarowanych za pomocą `member` — słowo kluczowe i metody statycznej zadeklarowana z `static` — słowo kluczowe.

Poniższy przykład przedstawia definicję i korzystanie z metod statycznych. Załóżmy, że te metody definicje znajdują się w `SomeType` klasy w poprzedniej sekcji.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjna i wirtualna
Słowo kluczowe `abstract` wskazuje metodę miejsca wysyłania wirtualnego i nie może mieć definicji klasy. A *miejsca wysyłania wirtualnego* jest odwołuje się do wpisu w tabeli obsługiwanej wewnętrznie funkcji używany w czasie wykonywania do odszukania funkcji wirtualnej zorientowane obiektowo typu. Mechanizm wysyłania wirtualnego jest mechanizm, który implementuje *polimorfizm*, ważna cecha programowanie zorientowane obiektowo. Klasa, która ma co najmniej jednej metody abstrakcyjnej bez definicji jest *klasy abstrakcyjnej*, co oznacza, że nie można utworzyć jego wystąpienia tej klasy. Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klas abstrakcyjnych](../abstract-classes.md).

Deklaracje metody abstrakcyjnej nie zawierają treści metody. Zamiast tego nazwę metody następuje dwukropkiem (:) i podpis typu metody. Podpis typu metody jest taka sama, jak te wyświetlane przez funkcję IntelliSense po zatrzymaniu wskaźnika myszy nad nazwę metody w Visual Studio edytorze kodu, z wyjątkiem bez nazwy parametrów. Typ podpisy są również wyświetlane przez interpretera fsi.exe, podczas pracy w trybie interakcyjnym. Podpis typu metody jest tworzony przez listę się typami parametrów, następuje typ zwracany przy użyciu odpowiednich separatora symboli. Rozwinięte parametry są oddzielone `->` i spójnej kolekcji parametry są oddzielone `*`. Zwracana wartość jest zawsze oddzielony od argumenty `->` symbolu. Nawiasy może służyć do grupowania złożonych parametrów, na przykład gdy typ funkcji jest parametrem, lub aby wskazać, kiedy Krotka jest traktowany jako jeden parametr, a nie dwa parametry.

Definicje domyślne metody abstrakcyjne mogą również dawać przez dodanie definicji klasy i przy użyciu `default` — słowo kluczowe, jak pokazano w bloku składni, w tym temacie. Metoda abstrakcyjna o definicję w tej samej klasy jest odpowiednikiem wirtualnej metody w innych językach .NET Framework. Określa, czy istnieje definicja `abstract` — słowo kluczowe tworzy nowe miejsce wysyłania w tabeli funkcji wirtualnych dla tej klasy.

Niezależnie od tego, czy klasa podstawowa implementuje jego metody abstrakcyjne klas pochodnych może dostarczyć implementacje metody abstrakcyjne. Aby zaimplementować metoda abstrakcyjna w klasie pochodnej, zdefiniuj metodę, która ma taką samą nazwę i podpis w klasie pochodnej, z wyjątkiem użycia `override` lub `default` — słowo kluczowe i podaj treści metody. Słowa kluczowe `override` i `default` oznacza dokładnie tak samo. Użyj `override` Jeśli nowa metoda zastępuje implementację klasy podstawowej; użyj `default` podczas tworzenia wdrożenia w tej samej klasy jako oryginalnej deklaracji abstrakcyjny. Nie używaj `abstract` — słowo kluczowe dla metody, która implementuje metodę, która została zadeklarowana jako abstrakcyjna w klasie podstawowej.

Poniższy przykład przedstawia metody abstrakcyjnej `Rotate` mający Domyślna implementacja odpowiednikiem metody wirtualnej .NET Framework.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Poniższy przykład przedstawia klasy pochodnej, która zastępuje metodę klasy podstawowej. W takim przypadku zastąpienie zmienia zachowanie tak, aby metody nie działają.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Metody przeciążane
Przeciążone metody są metody, które mają identyczne nazwy w danym typie, ale mają różne argumentów. W F # Argumenty opcjonalne są zazwyczaj używane zamiast przeciążonej metody. Jednak przeciążonej metody są dozwolone w języku, pod warunkiem, że argumenty są w postaci spójnej kolekcji, nie rozwinięte formularza.

## <a name="optional-arguments"></a>Argumenty opcjonalne

Począwszy od 4.1 F #, może także zawierać Argumenty opcjonalne, wartość domyślna parametru metody.  To, aby ułatwić współdziałanie z kodem C#.  Poniższy przykład przedstawia składnię:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Należy pamiętać, że wartość przekazana dla `DefaultParameterValue` musi być zgodny typ danych wejściowych.  W powyższym przykładzie jest `int`.  Próba przekazania wartość nie jest liczbą całkowitą w `DefaultParameterValue` spowoduje błąd kompilacji.

## <a name="example-properties-and-methods"></a>Przykład: Właściwości i metody
Poniższy przykład zawiera typ, który zawiera przykłady pola, prywatnej funkcji, właściwości i metody statycznej.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Zobacz też
[Elementy członkowskie](index.md)
