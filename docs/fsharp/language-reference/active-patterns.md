---
title: Wzorce aktywne (F#)
description: Dowiedz się, jak zdefiniować nazwanych partycji, które należy podzielić dane wejściowe w języku programowania F# przy użyciu wzorców.
ms.date: 05/16/2016
ms.openlocfilehash: 4fb7d3e2b9c7e6f1c1ed9d64a47728c7f40017c8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "48838315"
---
# <a name="active-patterns"></a><span data-ttu-id="08525-103">Wzorce aktywne</span><span class="sxs-lookup"><span data-stu-id="08525-103">Active Patterns</span></span>

<span data-ttu-id="08525-104">*Wzorce aktywne* umożliwiają definiowanie nazwanych partycji, które należy podzielić dane wejściowe, dzięki czemu można używać tych nazw w wyrażeniu dopasowania, tak jak w przypadku złożenia dyskryminowanego do wzorca.</span><span class="sxs-lookup"><span data-stu-id="08525-104">*Active patterns* enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union.</span></span> <span data-ttu-id="08525-105">Wzorce aktywne służy do rozkładania danych w sposób dostosowany dla każdej partycji.</span><span class="sxs-lookup"><span data-stu-id="08525-105">You can use active patterns to decompose data in a customized manner for each partition.</span></span>

## <a name="syntax"></a><span data-ttu-id="08525-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="08525-106">Syntax</span></span>

```fsharp
// Complete active pattern definition.
let (|identifer1|identifier2|...|) [ arguments ] = expression
// Partial active pattern definition.
let (|identifier|_|) [ arguments ] = expression
```

## <a name="remarks"></a><span data-ttu-id="08525-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08525-107">Remarks</span></span>

<span data-ttu-id="08525-108">W poprzedniej składni identyfikatory są nazwy partycji danych wejściowych, który jest reprezentowany przez *argumenty*, lub innymi słowy, nazwy dla podzbiorów zbiór wszystkich wartości argumentów.</span><span class="sxs-lookup"><span data-stu-id="08525-108">In the previous syntax, the identifiers are names for partitions of the input data that is represented by *arguments*, or, in other words, names for subsets of the set of all values of the arguments.</span></span> <span data-ttu-id="08525-109">W definicji — aktywny wzorzec może być maksymalnie siedem partycji.</span><span class="sxs-lookup"><span data-stu-id="08525-109">There can be up to seven partitions in an active pattern definition.</span></span> <span data-ttu-id="08525-110">*Wyrażenie* opisuje formularza, w którym do rozkładania danych.</span><span class="sxs-lookup"><span data-stu-id="08525-110">The *expression* describes the form into which to decompose the data.</span></span> <span data-ttu-id="08525-111">Definicja — aktywny wzorzec można użyć do zdefiniowania reguł do określania, której partycji nazwanej wartości podanej jako argumenty należą do.</span><span class="sxs-lookup"><span data-stu-id="08525-111">You can use an active pattern definition to define the rules for determining which of the named partitions the values given as arguments belong to.</span></span> <span data-ttu-id="08525-112">(| I |) symbole są określane jako *klipy banany* i jest wywoływana funkcja utworzone przez tego typu powiązania let *active rozpoznawania*.</span><span class="sxs-lookup"><span data-stu-id="08525-112">The (| and |) symbols are referred to as *banana clips* and the function created by this type of let binding is called an *active recognizer*.</span></span>

<span data-ttu-id="08525-113">Na przykład należy wziąć pod uwagę następujące aktywny wzorzec z nieprawidłowym argumentem.</span><span class="sxs-lookup"><span data-stu-id="08525-113">As an example, consider the following active pattern with an argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5001.fs)]

<span data-ttu-id="08525-114">Aktywny wzorzec można użyć w wyrażeniu, jak w poniższym przykładzie dopasowania do wzorca.</span><span class="sxs-lookup"><span data-stu-id="08525-114">You can use the active pattern in a pattern matching expression, as in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5002.fs)]

<span data-ttu-id="08525-115">Dane wyjściowe tego programu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="08525-115">The output of this program is as follows:</span></span>

```
7 is odd
11 is odd
32 is even
```

<span data-ttu-id="08525-116">Innym zastosowaniem wzorców jest do rozkładania typy danych na wiele sposobów, na przykład w przypadku tych samych danych bazowych różne reprezentacje to możliwe.</span><span class="sxs-lookup"><span data-stu-id="08525-116">Another use of active patterns is to decompose data types in multiple ways, such as when the same underlying data has various possible representations.</span></span> <span data-ttu-id="08525-117">Na przykład `Color` obiekt może być rozłożone na reprezentację w postaci RGB lub reprezentację w postaci HSB.</span><span class="sxs-lookup"><span data-stu-id="08525-117">For example, a `Color` object could be decomposed into an RGB representation or an HSB representation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5003.fs)]

<span data-ttu-id="08525-118">Dane wyjściowe programu powyżej jest następująca:</span><span class="sxs-lookup"><span data-stu-id="08525-118">The output of the above program is as follows:</span></span>

```
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

<span data-ttu-id="08525-119">W połączeniu te dwa sposoby używania wzorców pozwalają na partycji i rozkładania danych do odpowiedniej postaci i wykonać odpowiednie obliczeń na odpowiednie dane w postaci najbardziej odpowiednim obliczeń.</span><span class="sxs-lookup"><span data-stu-id="08525-119">In combination, these two ways of using active patterns enable you to partition and decompose data into just the appropriate form and perform the appropriate computations on the appropriate data in the form most convenient for the computation.</span></span>

<span data-ttu-id="08525-120">Wyrażenia dopasowania wzorca wynikowe Włącz dane są zapisywane w wygodny sposób, który jest bardzo czytelny, znaczne uproszczenie złożonych tworzenia rozgałęzień i kod analizy danych.</span><span class="sxs-lookup"><span data-stu-id="08525-120">The resulting pattern matching expressions enable data to be written in a convenient way that is very readable, greatly simplifying potentially complex branching and data analysis code.</span></span>

## <a name="partial-active-patterns"></a><span data-ttu-id="08525-121">Wzorce aktywne częściowe</span><span class="sxs-lookup"><span data-stu-id="08525-121">Partial Active Patterns</span></span>

<span data-ttu-id="08525-122">Czasami musisz partycji tylko część obszaru danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="08525-122">Sometimes, you need to partition only part of the input space.</span></span> <span data-ttu-id="08525-123">W takim przypadku można zapisać zestawu częściowego wzorców, z nich odnosić się do niektórych danych wejściowych, ale nie można dopasować pozostałych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="08525-123">In that case, you write a set of partial patterns each of which match some inputs but fail to match other inputs.</span></span> <span data-ttu-id="08525-124">Aktywne wzorce, które nie zawsze daje wartość są nazywane *częściowe wzorców*; mają zwracanej wartości, która jest typem opcji.</span><span class="sxs-lookup"><span data-stu-id="08525-124">Active patterns that do not always produce a value are called *partial active patterns*; they have a return value that is an option type.</span></span> <span data-ttu-id="08525-125">Aby zdefiniować częściowe — aktywny wzorzec, należy użyć symbolu wieloznacznego (\_) na końcu listy wzorców wewnątrz klipów banany.</span><span class="sxs-lookup"><span data-stu-id="08525-125">To define a partial active pattern, you use a wildcard character (\_) at the end of the list of patterns inside the banana clips.</span></span> <span data-ttu-id="08525-126">Poniższy kod ilustruje sposób korzystania z częściowego — aktywny wzorzec.</span><span class="sxs-lookup"><span data-stu-id="08525-126">The following code illustrates the use of a partial active pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5004.fs)]

<span data-ttu-id="08525-127">Dane wyjściowe poprzedniego przykładu, jest następujący:</span><span class="sxs-lookup"><span data-stu-id="08525-127">The output of the previous example is as follows:</span></span>

```
1.100000 : Floating point
0 : Integer
0.000000 : Floating point
10 : Integer
Something else : Not matched.
```

<span data-ttu-id="08525-128">Korzystając z częściowego wzorców, czasami poszczególne opcje mogą być rozłączne lub wzajemnie się wykluczają, ale nie muszą być.</span><span class="sxs-lookup"><span data-stu-id="08525-128">When using partial active patterns, sometimes the individual choices can be disjoint or mutually exclusive, but they need not be.</span></span> <span data-ttu-id="08525-129">W poniższym przykładzie kwadrat wzorca i wzorzec modułu nie są rozłączne, ponieważ niektóre numery kwadratów i modułów, takich jak 64.</span><span class="sxs-lookup"><span data-stu-id="08525-129">In the following example, the pattern Square and the pattern Cube are not disjoint, because some numbers are both squares and cubes, such as 64.</span></span> <span data-ttu-id="08525-130">Następujący program drukowania wszystkich liczb całkowitych do 1000000, które są zarówno kwadratów i moduły.</span><span class="sxs-lookup"><span data-stu-id="08525-130">The following program prints out all integers up to 1000000 that are both squares and cubes.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5005.fs)]

<span data-ttu-id="08525-131">Dane wyjściowe wyglądają następująco:</span><span class="sxs-lookup"><span data-stu-id="08525-131">The output is as follows:</span></span>

```
1
64
729
4096
15625
46656
117649
262144
531441
1000000
```

## <a name="parameterized-active-patterns"></a><span data-ttu-id="08525-132">Wzorce aktywne sparametryzowane</span><span class="sxs-lookup"><span data-stu-id="08525-132">Parameterized Active Patterns</span></span>

<span data-ttu-id="08525-133">Wzorce aktywne zawsze uruchomić co najmniej jednego argumentu dla elementu są dopasowywane, ale potrwać dodatkowych argumentów, w tym przypadku nazwa *sparametryzowanego — aktywny wzorzec* ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="08525-133">Active patterns always take at least one argument for the item being matched, but they may take additional arguments as well, in which case the name *parameterized active pattern* applies.</span></span> <span data-ttu-id="08525-134">Dodatkowe argumenty zezwala na ogólny wzorzec można wyspecjalizować.</span><span class="sxs-lookup"><span data-stu-id="08525-134">Additional arguments allow a general pattern to be specialized.</span></span> <span data-ttu-id="08525-135">Na przykład wzorców, które używają wyrażeń regularnych do analizowania ciągów często zawierają wyrażenia regularnego jako dodatkowego parametru, zgodnie z poniższym kodem, który także używa częściowe — aktywny wzorzec `Integer` zdefiniowane w poprzednim przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="08525-135">For example, active patterns that use regular expressions to parse strings often include the regular expression as an extra parameter, as in the following code, which also uses the partial active pattern `Integer` defined in the previous code example.</span></span> <span data-ttu-id="08525-136">W tym przykładzie podane są ciągów, które używają wyrażeń regularnych dla różnych formatów daty, aby dostosować ogólny ParseRegex — aktywny wzorzec.</span><span class="sxs-lookup"><span data-stu-id="08525-136">In this example, strings that use regular expressions for various date formats are given to customize the general ParseRegex active pattern.</span></span> <span data-ttu-id="08525-137">Liczba całkowita — aktywny wzorzec służy do konwertowania ciągów dopasowane do liczb całkowitych, które mogą być przekazywane do konstruktora daty/godziny.</span><span class="sxs-lookup"><span data-stu-id="08525-137">The Integer active pattern is used to convert the matched strings into integers that can be passed to the DateTime constructor.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5006.fs)]

<span data-ttu-id="08525-138">Dane wyjściowe poprzedniego kodu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="08525-138">The output of the previous code is as follows:</span></span>

```
12/22/2008 12:00:00 AM 1/1/2009 12:00:00 AM 1/15/2008 12:00:00 AM 12/28/1995 12:00:00 AM
```

<span data-ttu-id="08525-139">Wzorce aktywne nie są ograniczone tylko do wyrażenia dopasowania do wzorca, można również użyć na let — powiązania.</span><span class="sxs-lookup"><span data-stu-id="08525-139">Active patterns are not restricted only to pattern matching expressions, you can also use them on let-bindings.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5007.fs)]

<span data-ttu-id="08525-140">Dane wyjściowe poprzedniego kodu jest następująca:</span><span class="sxs-lookup"><span data-stu-id="08525-140">The output of the previous code is as follows:</span></span>

```
Hello, random citizen!
Hello, George!
```

## <a name="see-also"></a><span data-ttu-id="08525-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="08525-141">See also</span></span>

- [<span data-ttu-id="08525-142">Dokumentacja języka F#</span><span class="sxs-lookup"><span data-stu-id="08525-142">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="08525-143">Wyrażenia dopasowania</span><span class="sxs-lookup"><span data-stu-id="08525-143">Match Expressions</span></span>](match-expressions.md)
