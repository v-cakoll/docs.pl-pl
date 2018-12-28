---
title: Metody
description: Dowiedz się, jak F# metoda jest funkcją skojarzony z typem, które są używane do udostępnienia i wdrażaniu funkcji i zachowanie obiektów i typy.
ms.date: 05/16/2016
ms.openlocfilehash: 03150cc67f79bfde58cf27e4a9d4dfa9e9ff3f55
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614028"
---
# <a name="methods"></a>Metody

A *metoda* jest funkcją, która jest skojarzona z typem. W programowanie zorientowane obiektowo metody są używane do udostępnienia i wdrażaniu funkcji i zachowanie obiektów i typy.

## <a name="syntax"></a>Składnia

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni można zobaczyć różne rodzaje definicje i deklaracje metody. W treści metod dłużej podział wiersza następuje znak równości (=) i tworzone jest wcięcie treści całej metody.

Atrybuty można zastosować do dowolnego deklaracji metody. One poprzedzać Składnia definicji metody i zazwyczaj są wyświetlane w osobnym wierszu. Aby uzyskać więcej informacji, zobacz [atrybuty](../attributes.md).

Można oznaczyć metody `inline`. Aby uzyskać informacje o `inline`, zobacz [funkcji śródwierszowych](../functions/inline-functions.md).

Inne niż wbudowane metody mogą być używane cyklicznie w ramach typu; nie trzeba jawnie użyć `rec` — słowo kluczowe.

## <a name="instance-methods"></a>Metody wystąpienia

Metody wystąpienia są uznane za pomocą `member` — słowo kluczowe i *własny identyfikator*, a następnie kropka (.) i nazwy metody i parametrów. Podobnie jak w przypadku dla `let` powiązań *listy parametrów* może być wzorca. Zazwyczaj należy ująć metoda parametry w nawiasach w formularzu krotki, czyli metody sposób są wyświetlane w F# gdy są one tworzone w innych językach .NET Framework. Rozwinięte formularza (rozdzielone spacjami parametry) jest również typowe i inne wzorce są również obsługiwane.

Poniższy przykład ilustruje definicja oraz wykorzystanie metody wystąpienia nieabstrakcyjnej.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

W ramach metody wystąpienia nie należy używać własny identyfikator do dostępu do pola zdefiniowane przy użyciu powiązania let. Użyj identyfikatora samodzielnie, podczas uzyskiwania dostępu do innych elementów członkowskich i właściwości.

## <a name="static-methods"></a>Metody statyczne

Słowo kluczowe `static` służy do określania, czy metoda może być wywołana bez wystąpienia i nie jest skojarzony z wystąpieniem obiektu. W przeciwnym razie przedstawiono metody wystąpienia.

W przykładzie w następnej sekcji przedstawiono zadeklarowane za pomocą pola `let` właściwości elementów członkowskich zadeklarowanych za pomocą słowa kluczowego, `member` — słowo kluczowe, a metoda statyczna zadeklarowana za pomocą `static` — słowo kluczowe.

Poniższy przykład ilustruje definicja oraz wykorzystanie metody statyczne. Przyjęto założenie, że te definicje metod znajdują się w `SomeType` klasy w poprzedniej sekcji.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjne i wirtualnych

Słowo kluczowe `abstract` wskazuje, że metoda ma miejsce wysyłania wirtualnego i nie może mieć definicji klasy. A *wysyłania wirtualnego miejsca* to wpis w obsługiwanej wewnętrznie tabeli funkcji używane w czasie wykonywania, aby wyszukać funkcji wirtualnej wywołuje typu zorientowane obiektowo. Mechanizm wysyłania wirtualnej to mechanizm, który implementuje *polimorfizm*, ważną funkcją programowanie zorientowane obiektowo. Jest klasą, która ma co najmniej jedną metodę abstrakcyjną bez definicji *abstrakcyjna klasa*, co oznacza, że nie można utworzyć jego wystąpienia tej klasy. Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [klasy abstrakcyjne](../abstract-classes.md).

Deklaracje metody abstrakcyjnej nie zawierają treści metody. Zamiast tego nazwę metody następuje dwukropek (:) i typ podpisu dla metody. Sygnatura typu metody jest taka sama, jak pokazano w przez funkcję IntelliSense po zatrzymaniu wskaźnika myszy nad nazwy metody w edytorze programu Visual Studio Code z wyjątkiem bez nazwy parametrów. Podpisy typu są również wyświetlane przez interpretera fsi.exe podczas pracy w interaktywnie. Sygnatura typu metody jest tworzony przez listę się typy parametrów, następuje zwracany typ, a symbole separatorów odpowiednie. Rozwinięte parametry są rozdzielane `->` i krotki parametry są rozdzielane `*`. Wartość zwracana zawsze jest oddzielony od argumentów przez `->` symboli. Nawiasów może służyć do grupowania złożonych parametrów, na przykład gdy typ funkcji jest parametr, lub, aby wskazać, kiedy krotki jest traktowany jako jeden parametr, a nie jako dwa parametry.

Definicje domyślne metody abstrakcyjne mogą również dawać przez dodanie definicji klasy i za pomocą `default` — słowo kluczowe, jak pokazano w bloku składni, w tym temacie. Metoda abstrakcyjna, który zawiera definicję w tej samej klasie jest odpowiednikiem wirtualnej metody w innych językach .NET Framework. Określa, czy definicja istnieje, `abstract` — słowo kluczowe tworzy nowe gniazdo wysyłania w tabeli funkcji wirtualnych dla tej klasy.

Niezależnie od tego, czy klasa bazowa implementuje jego metody abstrakcyjne klasach pochodnych można podać implementacji metody abstrakcyjne. Aby zaimplementować metodę abstrakcyjną w klasie pochodnej, należy zdefiniować metodę, która ma taką samą nazwę i podpis w klasie pochodnej, z wyjątkiem użycia `override` lub `default` — słowo kluczowe i podaj treści metody. Słowa kluczowe `override` i `default` oznacza dokładnie tak samo. Użyj `override` Jeśli nowa metoda zastępuje implementacji klasy podstawowej; użyj `default` podczas tworzenia implementacji w tej samej klasy jako abstrakcyjnej pierwotnej deklaracji. Nie używaj `abstract` — słowo kluczowe w metodzie, która implementuje metodę, która został zadeklarowany jako abstrakcyjny w klasie bazowej.

W poniższym przykładzie pokazano metodę abstrakcyjną `Rotate` zawierający implementacji domyślnej, odpowiednik metody wirtualnej .NET Framework.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Poniższy przykład ilustruje klasę pochodną, która zastępuje metodę klasy bazowej. W tym przypadku zastąpienie zmienia zachowanie, tak aby nie robi nic, metoda.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Przeciążone metody

Przeciążone metody są metody, które mają identyczne nazwy w danego typu, ale mają różnymi argumentami. W F#, argumenty opcjonalne są zwykle używane zamiast przeciążonych metod. Jednak przeciążone metody są dozwolone w języku, pod warunkiem, że argumenty znajdują się w formularzu krotki i nie rozwinięte formularza.

## <a name="optional-arguments"></a>Argumenty opcjonalne.

Począwszy od F# 4.1, mogą też istnieć Argumenty opcjonalne z wartością domyślną parametru za pomocą metod.  To, aby ułatwić współdziałanie z kodem C#.  Poniższy przykład pokazuje składnię:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Należy zauważyć, że wartość przekazywana w dla `DefaultParameterValue` musi odpowiadać typowi danych wejściowych.  W powyższym przykładzie jest `int`.  Próba przekazania wartości niebędące liczbami całkowitymi, do `DefaultParameterValue` mogłoby spowodować błąd kompilacji.

## <a name="example-properties-and-methods"></a>Przykład: Właściwości i metody

Poniższy przykład zawiera typ, który zawiera przykłady pola, prywatne funkcje, właściwości i metody statycznej.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)