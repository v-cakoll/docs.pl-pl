---
title: Metody
description: Dowiedz się F# , jak metoda jest funkcją skojarzoną z typem, który służy do uwidaczniania i implementowania funkcji i zachowań obiektów i typów.
ms.date: 05/16/2016
ms.openlocfilehash: 13503690a59ace13dacba93b6fce9ea3240c5cc2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627439"
---
# <a name="methods"></a>Metody

*Metoda* jest funkcją, która jest skojarzona z typem. W programowaniu zorientowanym na obiekty metody są używane do ujawniania i implementowania funkcji i zachowań obiektów i typów.

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

W poprzedniej składni, można zobaczyć różne formy deklaracji i definicji metod. W większej liczbie metod, podział wiersza następuje po znaku równości (=), a cała treść metody jest wcięty.

Atrybuty mogą być stosowane do dowolnej deklaracji metody. Poprzedzają one składnię definicji metody i są zwykle wyświetlane w osobnym wierszu. Aby uzyskać więcej informacji, zobacz [atrybuty](../attributes.md).

Metody mogą być oznaczone `inline`. Aby uzyskać informacje `inline`na temat, zobacz [funkcje wbudowane](../functions/inline-functions.md).

Metody inne niż śródwierszowe mogą być używane rekursywnie w obrębie typu; nie ma potrzeby jawnego używania `rec` słowa kluczowego.

## <a name="instance-methods"></a>Metody wystąpień

Metody wystąpień są zadeklarowane za `member` pomocą słowa kluczowego i samodzielnego *identyfikatora*, po którym następuje kropka (.) oraz nazwa metody i parametry. Podobnie jak w przypadku `let` powiązań, *Lista parametrów* może być wzorcem. Zwykle parametry metody są umieszczane w nawiasach w postaci spójnej kolekcji, która jest sposobem, w F# jaki metody są wyświetlane, gdy są tworzone w innych językach .NET Framework. Jednak formularz rozwinięte (parametry oddzielone spacjami) jest również powszechny, a także inne wzorce są obsługiwane.

Poniższy przykład ilustruje definicję i użycie nieabstrakcyjnej metody wystąpienia.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

W ramach metod wystąpień nie należy używać samego identyfikatora do uzyskiwania dostępu do pól zdefiniowanych przy użyciu let bindings. Użyj własnego identyfikatora podczas uzyskiwania dostępu do innych członków i właściwości.

## <a name="static-methods"></a>Metody statyczne

Słowo kluczowe `static` jest używane do określania, że metoda może być wywoływana bez wystąpienia i nie jest skojarzona z wystąpieniem obiektu. W przeciwnym razie metody są metodami wystąpień.

W przykładzie w następnej sekcji przedstawiono pola zadeklarowane za pomocą `let` słowa kluczowego, członków właściwości zadeklarowanych `member` za pomocą słowa kluczowego i `static` statycznej metody zadeklarowanej za pomocą słowa kluczowego.

Poniższy przykład ilustruje definicję i użycie metod statycznych. Załóżmy, że te definicje metod znajdują `SomeType` się w klasie w poprzedniej sekcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjne i wirtualne

Słowo kluczowe `abstract` wskazuje, że metoda ma wirtualne gniazdo wysyłkowe i może nie mieć definicji w klasie. *Wirtualne miejsce wysyłki* to wpis w wewnętrznie obsługiwanej tabeli funkcji, który jest używany w czasie wykonywania do wyszukiwania wywołań funkcji wirtualnych w typie zorientowanym obiektowo. Mechanizm wysyłania wirtualnego jest mechanizmem, który implementuje *polimorfizm*, ważną funkcję programowania zorientowanego na obiekt. Klasa, która ma co najmniej jedną metodę abstrakcyjną bez definicji, jest *klasą abstrakcyjną*, co oznacza, że nie można tworzyć wystąpień tej klasy. Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klasy abstrakcyjne](../abstract-classes.md).

Deklaracje metody abstrakcyjnej nie zawierają treści metody. Zamiast tego, nazwa metody następuje dwukropek (:) i podpis typu dla metody. Sygnatura typu metody jest taka sama jak pokazana przez funkcję IntelliSense po zatrzymaniu wskaźnika myszy nad nazwą metody w edytorze Visual Studio Code, z wyjątkiem nazw parametrów. Sygnatury typów są również wyświetlane przez interpreter, FSI. exe, gdy pracujesz interaktywnie. Podpis typu metody jest tworzony przez wystawienie typów parametrów, po których następuje zwracany typ, z odpowiednimi symbolami separatora. Parametry rozwinięte są rozdzielone `->` , a parametry krotki są rozdzielone przez. `*` Wartość zwracana jest zawsze oddzielona od argumentów przez `->` symbol. Nawiasy mogą służyć do grupowania parametrów złożonych, takich jak, gdy typ funkcji jest parametrem lub aby wskazać, kiedy Krotka jest traktowana jako pojedynczy parametr, a nie jako dwa parametry.

Można również nadać abstrakcyjnym metodom definicje domyślne przez dodanie definicji do klasy i użycie `default` słowa kluczowego, jak pokazano w bloku składni w tym temacie. Metoda abstrakcyjna, która ma definicję w tej samej klasie, jest równoważna z metodą wirtualną w innych językach .NET Framework. Niezależnie od tego `abstract` , czy definicja istnieje, słowo kluczowe tworzy nowe miejsce wysyłki w tabeli funkcji wirtualnych dla klasy.

Niezależnie od tego, czy klasa bazowa implementuje metody abstrakcyjne, klasy pochodne mogą dostarczać implementacje metod abstrakcyjnych. Aby zaimplementować metodę abstrakcyjną w klasie pochodnej, zdefiniuj metodę, która ma taką samą nazwę i podpis w klasie pochodnej, z wyjątkiem użycia `override` słowa kluczowego or `default` i podaj treść metody. Słowa kluczowe `override` i `default` oznaczają dokładnie te same rzeczy. Użyj `override` , jeśli nowa metoda przesłania implementację klasy bazowej; Użyj `default` , gdy tworzysz implementację w tej samej klasie co oryginalna deklaracja abstrakcyjna. Nie należy używać `abstract` słowa kluczowego na metodzie implementującej metodę, która została zadeklarowana jako abstract w klasie bazowej.

Poniższy przykład ilustruje metodę `Rotate` abstrakcyjną, która ma implementację domyślną, równoważnej metody wirtualnej .NET Framework.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

Poniższy przykład ilustruje klasę pochodną, która zastępuje metodę klasy bazowej. W takim przypadku zastąpienie zmieni zachowanie, tak aby Metoda niczego nie robi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Przeciążone metody

Przeciążone metody to metody, które mają identyczne nazwy w danym typie, ale które mają różne argumenty. W F#programie argumenty opcjonalne są zwykle używane zamiast przeciążonych metod. Jednak przeciążone metody są dozwolone w języku, pod warunkiem, że argumenty są w postaci krotki, nie rozwinięte form.

## <a name="optional-arguments"></a>Argumenty opcjonalne

Począwszy od F# 4,1, można także mieć opcjonalne argumenty z domyślną wartością parametru w metodach.  W ten sposób można ułatwić współdziałanie C# z kodem.  Poniższy przykład ilustruje składnię:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Należy zauważyć, że wartość przeniesiona `DefaultParameterValue` dla elementu musi być zgodna z typem danych wejściowych.  W powyższym przykładzie jest `int`to.  Próba przekazania wartości `DefaultParameterValue` innej niż całkowita spowoduje błąd kompilacji.

## <a name="example-properties-and-methods"></a>Przykład: Właściwości i metody

Poniższy przykład zawiera typ, który ma przykłady pól, funkcji prywatnych, właściwości i metody statycznej.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
