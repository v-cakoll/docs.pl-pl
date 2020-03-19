---
title: Metody
description: Dowiedz się, jak Metoda F# jest funkcją skojarzoną z typem, które są używane do uwidaczniania i implementowania funkcji i zachowania obiektów i typów.
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400212"
---
# <a name="methods"></a>Metody

*Metoda* jest funkcją skojarzoną z typem. W programowaniu obiektowym metody są używane do uwidaczniania i implementowania funkcji i zachowania obiektów i typów.

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

W poprzedniej składni można zobaczyć różne formy deklaracji metod i definicji. W obiektach metody dłuższej podział wiersza następuje po znaku równości (=), a cała treść metody jest wcięta.

Atrybuty mogą być stosowane do dowolnej deklaracji metody. Poprzedzają one składnię definicji metody i są zwykle wyświetlane w osobnym wierszu. Aby uzyskać więcej informacji, zobacz [Atrybuty](../attributes.md).

Metody mogą być `inline`oznaczone . Aby uzyskać `inline`informacje na temat , zobacz [Funkcje inline](../functions/inline-functions.md).

Metody niewinna mogą być używane cyklicznie w obrębie typu; nie ma potrzeby jawnego `rec` używania słowa kluczowego.

## <a name="instance-methods"></a>Metody wystąpień

Metody wystąpienia są deklarowane za pomocą słowa kluczowego `member` i *samoidentyfikatora,* po którym następuje kropka (.) oraz nazwa i parametry metody. Jak w przypadku `let` powiązań, *lista parametrów* może być wzorcem. Zazwyczaj należy ująć parametry metody w nawiasy w formularzu krotki, który jest sposób metody są wyświetlane w F#, gdy są one tworzone w innych językach .NET Framework. Jednak forma curried (parametry oddzielone spacjami) jest również powszechna, a inne wzorce są również obsługiwane.

W poniższym przykładzie przedstawiono definicję i użycie metody wystąpienia nieabstrakcyjnego.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

W ramach metody wystąpienia nie należy używać identyfikatora siebie, aby uzyskać dostęp do pól zdefiniowanych przy użyciu let powiązania. Użyj identyfikatora siebie podczas uzyskiwania dostępu do innych elementów członkowskich i właściwości.

## <a name="static-methods"></a>Metody statyczne

Słowo `static` kluczowe służy do określenia, że metoda może być wywoływana bez wystąpienia i nie jest skojarzony z wystąpieniem obiektu. W przeciwnym razie metody są metody wystąpienia.

W przykładzie w następnej sekcji `let` przedstawiono pola zadeklarowane `member` za pomocą słowa kluczowego, `static` członków właściwości zadeklarowanych za pomocą słowa kluczowego i metodę statyczną zadeklarowaną za pomocą słowa kluczowego.

Poniższy przykład ilustruje definicję i stosowanie metod statycznych. Załóżmy, że te `SomeType` definicje metod znajdują się w klasie w poprzedniej sekcji.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a>Metody abstrakcyjne i wirtualne

Słowo `abstract` kluczowe wskazuje, że metoda ma gniazdo wirtualnej wysyłki i może nie mieć definicji w klasie. Gniazdo *wirtualnej wysyłki* jest wpisem w wewnętrznie obsługiwanej tabeli funkcji, która jest używana w czasie wykonywania do wyszukiwania wywołań funkcji wirtualnych w typie obiektowym. Mechanizm wirtualnej wysyłki to mechanizm, który implementuje *polimorfizm*, ważną cechę programowania obiektowego. Klasa, która ma co najmniej jedną metodę abstrakcyjną bez definicji jest *klasą abstrakcyjną,* co oznacza, że nie można utworzyć żadnych wystąpień tej klasy. Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klasy abstrakcyjne](../abstract-classes.md).

Deklaracje metody abstrakcyjne nie zawierają treści metody. Zamiast tego po nazwie metody następuje dwukropek (:) i podpis typu dla metody. Podpis typu metody jest taka sama jak pokazana przez IntelliSense po wstrzymaniu wskaźnika myszy nad nazwą metody w Edytorze kodu programu Visual Studio, z wyjątkiem bez nazw parametrów. Podpisy typów są również wyświetlane przez interpretera fsi.exe, gdy pracujesz interaktywnie. Podpis typu metody jest tworzony przez listę typów parametrów, a następnie typu zwracanego, z odpowiednimi symbolami separatora. Parametry curried są `->` oddzielone, a parametry krotki są oddzielone . `*` Zwracana wartość jest zawsze oddzielona `->` od argumentów symbolem. Nawiasy mogą służyć do grupowania złożonych parametrów, takich jak, gdy typ funkcji jest parametrem, lub do wskazania, kiedy krotka jest traktowana jako pojedynczy parametr, a nie jako dwa parametry.

Można również podać metody abstrakcyjne domyślne definicje, dodając definicję do klasy i przy użyciu słowa kluczowego, `default` jak pokazano w bloku składni w tym temacie. Metoda abstrakcyjna, która ma definicję w tej samej klasie jest odpowiednikiem metody wirtualnej w innych językach .NET Framework. Niezależnie od tego, czy `abstract` istnieje definicja, słowo kluczowe tworzy nowe gniazdo wysyłki w tabeli funkcji wirtualnych dla klasy.

Niezależnie od tego, czy klasa podstawowa implementuje swoje metody abstrakcyjne, klasy pochodne może zapewnić implementacje metod abstrakcyjnych. Aby zaimplementować metodę abstrakcyjną w klasie pochodnej, należy zdefiniować metodę, która ma `override` taką `default` samą nazwę i podpis w klasie pochodnej, z wyjątkiem użycia lub słowa kluczowego i podać treść metody. Słowa kluczowe `override` `default` i oznaczają dokładnie to samo. Użyj, `override` jeśli nowa metoda zastępuje implementację klasy podstawowej; użyj `default` podczas tworzenia implementacji w tej samej klasie, co oryginalna deklaracja abstrakcyjna. Nie należy `abstract` używać słowa kluczowego na metodę, która implementuje metodę, która została zadeklarowana jako abstrakcyjna w klasie podstawowej.

W poniższym przykładzie przedstawiono `Rotate` metodę abstrakcyjną, która ma implementację domyślną, odpowiednik metody wirtualnej .NET Framework.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

W poniższym przykładzie przedstawiono klasę pochodną, która zastępuje metodę klasy podstawowej. W takim przypadku zastąpienie zmienia zachowanie tak, aby metoda nic nie robi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a>Metody przeciążone

Przeciążone metody są metody, które mają identyczne nazwy w danym typu, ale które mają różne argumenty. W F#, opcjonalne argumenty są zwykle używane zamiast przeciążonych metod. Jednak przeciążone metody są dozwolone w języku, pod warunkiem, że argumenty są w formie krotki, a nie curried formie.

## <a name="optional-arguments"></a>Argumenty opcjonalne

Począwszy od F# 4.1, można również mieć opcjonalne argumenty z wartością parametru domyślnego w metodach.  Ma to ułatwić współdziałanie z kodem Języka C#.  W poniższym przykładzie przedstawiono składnię:

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

Należy zauważyć, że `DefaultParameterValue` wartość przekazywana dla musi odpowiadać typowi wejściowemu.  W powyższej próbce `int`jest to .  Próba przekazania wartości niecałkowitej do `DefaultParameterValue` spowodowałoby błąd kompilacji.

## <a name="example-properties-and-methods"></a>Przykład: Właściwości i metody

Poniższy przykład zawiera typ, który zawiera przykłady pól, funkcje prywatne, właściwości i metodę statyczną.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a>Zobacz też

- [Elementy członkowskie](index.md)
