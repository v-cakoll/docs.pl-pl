---
title: Wzorce aktywne
description: Dowiedz się, jak używać aktywnych wzorców do definiowania nazwanych partycji, które dzielą dane wejściowe w języku F# programowania.
ms.date: 05/16/2016
ms.openlocfilehash: f5ed4a8600cba10d23d01628aba6ca07e543c586
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425094"
---
# <a name="active-patterns"></a><span data-ttu-id="b7e67-103">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="b7e67-103">Active Patterns</span></span>

<span data-ttu-id="b7e67-104">*Aktywne wzorce* umożliwiają zdefiniowanie nazwanych partycji, które dzielą dane wejściowe, dzięki czemu można używać tych nazw w wyrażeniu dopasowania wzorca tak samo jak w przypadku Unii rozłącznych.</span><span class="sxs-lookup"><span data-stu-id="b7e67-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="b7e67-105">Przy użyciu aktywnych wzorców można rozkładać dane w dostosowany sposób dla każdej partycji.</span><span class="sxs-lookup"><span data-stu-id="b7e67-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7e67-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="b7e67-106">Syntax</span></span>

```fsharp
// Active pattern of one choice.
let (|identifier|) [arguments] valueToMatch= expression

// Active Pattern with multiple choices.
// Uses a FSharp.Core.Choice<_,...,_> based on the number of case names. In F#, the limitation n <= 7 applies.
let (|identifer1|identifier2|...|) valueToMatch = expression

// Partial active pattern definition.
// Uses a FSharp.Core.option<_> to represent if the type is satisfied at the call site.
let (|identifier|_|) [arguments ] valueToMatch = expression
```

## <a name="remarks"></a><span data-ttu-id="b7e67-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7e67-107">Remarks</span></span>

<span data-ttu-id="b7e67-108">W poprzedniej składni identyfikatory są nazwami dla partycji danych wejściowych, które są reprezentowane przez *argumenty*lub, innymi słowy, nazwy podzestawów zestawu wszystkich wartości argumentów.</span><span class="sxs-lookup"><span data-stu-id="b7e67-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="b7e67-109">W definicji aktywnego wzorca może istnieć maksymalnie siedem partycji.</span><span class="sxs-lookup"><span data-stu-id="b7e67-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="b7e67-110">*Wyrażenie* opisuje formularz, w którym mają zostać rozdzielone dane.</span><span class="sxs-lookup"><span data-stu-id="b7e67-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="b7e67-111">Możesz użyć aktywnej definicji wzorca, aby zdefiniować reguły określania, które z nazwanych partycji są wartościami podaną jako argumenty należą do.</span><span class="sxs-lookup"><span data-stu-id="b7e67-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="b7e67-112">Symbole (| i |) są określane jako *klipy bananów* , a funkcja utworzona przez ten typ powiązania Let jest nazywana *aktywnym aparatem rozpoznawania*.</span><span class="sxs-lookup"><span data-stu-id="b7e67-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="b7e67-113">Na przykład rozważmy następujący Aktywny wzorzec z argumentem.</span><span class="sxs-lookup"><span data-stu-id="b7e67-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="b7e67-114">Możesz użyć aktywnego wzorca w wyrażeniu dopasowania do wzorca, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b7e67-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="b7e67-115">Dane wyjściowe tego programu są następujące:</span><span class="sxs-lookup"><span data-stu-id="b7e67-115">The output of this program is as follows:</span></span>

```console
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="b7e67-116">Innym sposobem użycia aktywnych wzorców jest rozkład typów danych na wiele sposobów, na przykład wtedy, gdy te same dane podstawowe mają różne możliwe reprezentacje.</span><span class="sxs-lookup"><span data-stu-id="b7e67-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="b7e67-117">Na przykład obiekt `Color` może zostać rozłożony na reprezentację RGB lub reprezentację HSB.</span><span class="sxs-lookup"><span data-stu-id="b7e67-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="b7e67-118">Dane wyjściowe powyższego programu są następujące:</span><span class="sxs-lookup"><span data-stu-id="b7e67-118">The output of the above program is as follows:</span></span>

```console
Red
 Red: 255 Green: 0 Blue: 0
 Hue: 360.000000 Saturation: 1.000000 Brightness: 0.500000
Black
 Red: 0 Green: 0 Blue: 0
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.000000
White
 Red: 255 Green: 255 Blue: 255
 Hue: 0.000000 Saturation: 0.000000 Brightness: 1.000000
Gray
 Red: 128 Green: 128 Blue: 128
 Hue: 0.000000 Saturation: 0.000000 Brightness: 0.501961
BlanchedAlmond
 Red: 255 Green: 235 Blue: 205
 Hue: 36.000000 Saturation: 1.000000 Brightness: 0.901961
```

<span data-ttu-id="b7e67-119">W połączeniu te dwa sposoby używania aktywnych wzorców umożliwiają partycjonowanie i rozdzielenie danych na odpowiedni formularz i wykonanie odpowiednich obliczeń na odpowiednich danych w formularzu najbardziej wygodnym do obliczenia.</span><span class="sxs-lookup"><span data-stu-id="b7e67-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="b7e67-120">Wyrażenia zgodne z wzorcem umożliwiają zapisywanie danych w wygodny sposób, który jest bardzo czytelny, co znacznie upraszcza tworzenie rozgałęzień i kodu analizy danych.</span><span class="sxs-lookup"><span data-stu-id="b7e67-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="b7e67-121">Częściowe aktywne wzorce</span><span class="sxs-lookup"><span data-stu-id="b7e67-121">Partial Active Patterns</span></span>

<span data-ttu-id="b7e67-122">Czasami należy podzielić tylko część przestrzeni wejściowej.</span><span class="sxs-lookup"><span data-stu-id="b7e67-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="b7e67-123">W takim przypadku należy napisać zestaw częściowych wzorców, z których każdy jest zgodny z niektórymi danymi wejściowymi, ale nie może dopasować innych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="b7e67-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="b7e67-124">Aktywne wzorce, które nie zawsze generują wartość, są nazywane *częściowymi wzorcami aktywnymi*; mają one wartość zwracaną, która jest typem opcji.</span><span class="sxs-lookup"><span data-stu-id="b7e67-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="b7e67-125">Aby zdefiniować częściowy Aktywny wzorzec, należy użyć symbolu wieloznacznego (\_) na końcu listy wzorców wewnątrz klipów bananów.</span><span class="sxs-lookup"><span data-stu-id="b7e67-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="b7e67-126">Poniższy kod ilustruje użycie części aktywnego wzorca.</span><span class="sxs-lookup"><span data-stu-id="b7e67-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="b7e67-127">W poprzednim przykładzie przedstawiono dane wyjściowe poniższego przykładu:</span><span class="sxs-lookup"><span data-stu-id="b7e67-127">The output of the previous example is as follows:</span></span>

```console
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="b7e67-128">W przypadku używania częściowych aktywnych wzorców czasami poszczególne opcje mogą być rozłączne lub wykluczane wzajemnie, ale nie muszą być.</span><span class="sxs-lookup"><span data-stu-id="b7e67-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="b7e67-129">W poniższym przykładzie, kwadrat wzorca i moduł wzorca nie są rozłączane, ponieważ niektóre liczby są kwadratami i modułami, takimi jak 64.</span><span class="sxs-lookup"><span data-stu-id="b7e67-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="b7e67-130">Poniższy program używa wzorca i do łączenia wzorców kwadratowych i sześcianu.</span><span class="sxs-lookup"><span data-stu-id="b7e67-130">The following program uses the AND pattern to combine the Square and Cube patterns.</span></span> <span data-ttu-id="b7e67-131">Drukuje wszystkie liczby całkowite o wartości do 1000, które są zarówno kwadratami, jak i modułami, a także tymi, które są tylko modułami.</span><span class="sxs-lookup"><span data-stu-id="b7e67-131">It print out all integers up to 1000 that are both squares and cubes, as well as those which are only cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="b7e67-132">Dane wyjściowe są następujące:</span><span class="sxs-lookup"><span data-stu-id="b7e67-132">The output is as follows:</span></span>

```console
1 is a cube and a square
8 is a cube
27 is a cube
64 is a cube and a square
125 is a cube
216 is a cube
343 is a cube
512 is a cube
729 is a cube and a square
1000 is a cube
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="b7e67-133">Sparametryzowane aktywne wzorce</span><span class="sxs-lookup"><span data-stu-id="b7e67-133">Parameterized Active Patterns</span></span>

<span data-ttu-id="b7e67-134">Aktywne wzorce zawsze przyjmują co najmniej jeden argument dla elementu, który jest dopasowywany, ale mogą również przyjmować dodatkowe argumenty, w tym przypadku ma zastosowanie nazwa *sparametryzowanego wzorca* .</span><span class="sxs-lookup"><span data-stu-id="b7e67-134">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="b7e67-135">Dodatkowe argumenty umożliwiają użycie ogólnego wzorca.</span><span class="sxs-lookup"><span data-stu-id="b7e67-135">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="b7e67-136">Na przykład aktywne wzorce używające wyrażeń regularnych do analizowania ciągów często zawierają wyrażenie regularne jako dodatkowy parametr, jak w poniższym kodzie, który używa również części aktywnego wzorca `Integer` zdefiniowanej w poprzednim przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="b7e67-136">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="b7e67-137">W tym przykładzie ciągi, które używają wyrażeń regularnych dla różnych formatów daty, są przyznawane w celu dostosowania ogólnego wzorca ParseRegex.</span><span class="sxs-lookup"><span data-stu-id="b7e67-137">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="b7e67-138">Aktywny wzorzec w liczbie całkowitej służy do konwertowania dopasowanych ciągów do liczb całkowitych, które mogą być przesyłane do konstruktora DateTime.</span><span class="sxs-lookup"><span data-stu-id="b7e67-138">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="b7e67-139">Dane wyjściowe poprzedniego kodu są następujące:</span><span class="sxs-lookup"><span data-stu-id="b7e67-139">The output of the previous code is as follows:</span></span>

```console
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="b7e67-140">Aktywne wzorce nie są ograniczone tylko do wyrażeń dopasowania wzorca, ale można ich używać również na potrzeby powiązań.</span><span class="sxs-lookup"><span data-stu-id="b7e67-140">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="b7e67-141">Dane wyjściowe poprzedniego kodu są następujące:</span><span class="sxs-lookup"><span data-stu-id="b7e67-141">The output of the previous code is as follows:</span></span>

```console
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="b7e67-142">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b7e67-142">See also</span></span>

- [<span data-ttu-id="b7e67-143">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="b7e67-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="b7e67-144">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="b7e67-144">Match Expressions</span></span>](match-expressions.md)
