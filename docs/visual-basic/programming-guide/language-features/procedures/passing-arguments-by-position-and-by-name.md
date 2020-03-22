---
title: Przekazywanie argumentów według pozycji i według nazwy
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400856"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="c96d4-102">Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c96d4-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>

<span data-ttu-id="c96d4-103">Podczas wywoływania `Sub` `Function` lub procedury, można przekazać argumenty *według pozycji* — w kolejności, w jakiej pojawiają się one w definicji procedury — lub można przekazać je *po imieniu*, bez względu na pozycję.</span><span class="sxs-lookup"><span data-stu-id="c96d4-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>

<span data-ttu-id="c96d4-104">Podczas przekazywania argumentu według nazwy, należy określić zadeklarowaną nazwę argumentu, po której następuje dwukropek i znak równości (`:=`), a następnie wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="c96d4-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="c96d4-105">Nazwane argumenty można podać w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c96d4-105">You can supply named arguments in any order.</span></span>

<span data-ttu-id="c96d4-106">Na przykład w `Sub` poniższej procedurze wybierze trzy argumenty:</span><span class="sxs-lookup"><span data-stu-id="c96d4-106">For example, the following `Sub` procedure takes three arguments:</span></span>

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

<span data-ttu-id="c96d4-107">Podczas wywoływania tej procedury, można podać argumenty według pozycji, według nazwy lub przy użyciu mieszaniny obu.</span><span class="sxs-lookup"><span data-stu-id="c96d4-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>

## <a name="passing-arguments-by-position"></a><span data-ttu-id="c96d4-108">Przekazywanie argumentów według pozycji</span><span class="sxs-lookup"><span data-stu-id="c96d4-108">Passing Arguments by Position</span></span>

<span data-ttu-id="c96d4-109">Metodę można `Display` wywołać z jej argumentami przekazywanymi przez położenie i rozdzielanymi przecinkami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c96d4-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

<span data-ttu-id="c96d4-110">Jeśli pominięto opcjonalny argument na liście argumentów pozycyjnych, musisz utrzymać jego miejsce przecinkiem.</span><span class="sxs-lookup"><span data-stu-id="c96d4-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="c96d4-111">Poniższy przykład `Display` wywołuje metodę `age` bez argumentu:</span><span class="sxs-lookup"><span data-stu-id="c96d4-111">The following example calls the `Display` method without the `age` argument:</span></span>

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a><span data-ttu-id="c96d4-112">Przekazywanie argumentów według nazwy</span><span class="sxs-lookup"><span data-stu-id="c96d4-112">Passing Arguments by Name</span></span>

<span data-ttu-id="c96d4-113">Alternatywnie można wywołać `Display` z argumentami przekazanymi przez nazwę, również rozdzielone przecinkami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c96d4-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

<span data-ttu-id="c96d4-114">Przekazywanie argumentów według nazwy w ten sposób jest szczególnie przydatne podczas wywoływania procedury, która ma więcej niż jeden opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="c96d4-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="c96d4-115">Jeśli podajesz argumenty według nazwy, nie trzeba używać kolejnych przecinków do oznaczania brakujących argumentów pozycyjnych.</span><span class="sxs-lookup"><span data-stu-id="c96d4-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="c96d4-116">Przekazywanie argumentów według nazwy ułatwia również śledzenie, które argumenty przechodzisz, a które pomijasz.</span><span class="sxs-lookup"><span data-stu-id="c96d4-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>

## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="c96d4-117">Mieszanie argumentów według pozycji i nazwy</span><span class="sxs-lookup"><span data-stu-id="c96d4-117">Mixing Arguments by Position and by Name</span></span>

<span data-ttu-id="c96d4-118">Argumenty można podawać zarówno według pozycji, jak i według nazwy w wywołaniu pojedynczej procedury, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c96d4-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

<span data-ttu-id="c96d4-119">W poprzednim przykładzie nie jest konieczne dodatkowe przecinek do `age` przechowywania miejsca `birth` pominiętego argumentu, ponieważ jest przekazywana przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="c96d4-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>

<span data-ttu-id="c96d4-120">W wersjach języka Visual Basic przed 15.5, podczas pokazywanie argumentów przez mieszaninę pozycji i nazwy, argumenty pozycyjne muszą być na pierwszym miejscu.</span><span class="sxs-lookup"><span data-stu-id="c96d4-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="c96d4-121">Po podaniu argumentu według nazwy wszystkie pozostałe argumenty muszą być przekazywane według nazwy.</span><span class="sxs-lookup"><span data-stu-id="c96d4-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="c96d4-122">Na przykład następujące wywołanie `Display` metody wyświetla błąd kompilatora [BC30241: Oczekiwany argument nazwany.](../../../misc/bc30241.md)</span><span class="sxs-lookup"><span data-stu-id="c96d4-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

<span data-ttu-id="c96d4-123">Począwszy od języka Visual Basic 15.5, argumenty pozycyjne mogą być zgodne z nazwanymi argumentami, jeśli końcowe argumenty pozycyjne znajdują się we właściwej pozycji.</span><span class="sxs-lookup"><span data-stu-id="c96d4-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="c96d4-124">Jeśli skompilowane w języku Visual Basic 15.5, poprzednie wywołanie `Display` metody kompiluje się pomyślnie i nie generuje już błąd kompilatora [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="c96d4-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>

<span data-ttu-id="c96d4-125">Ta możliwość mieszania i dopasowywania argumentów nazwanych i pozycyjnych w dowolnej kolejności jest szczególnie przydatna, gdy chcesz użyć nazwanego argumentu, aby kod był bardziej czytelny.</span><span class="sxs-lookup"><span data-stu-id="c96d4-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="c96d4-126">Na przykład konstruktor następującej `Person` klasy `Person`wymaga dwóch argumentów `Nothing`typu , z których oba mogą być .</span><span class="sxs-lookup"><span data-stu-id="c96d4-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

<span data-ttu-id="c96d4-127">Za pomocą mieszanych nazwanych i pozycyjnych argumentów pomaga `father` `mother` uczynić `Nothing`intencję kodu jasne, gdy wartość i argumenty jest:</span><span class="sxs-lookup"><span data-stu-id="c96d4-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

<span data-ttu-id="c96d4-128">Aby śledzić argumenty pozycyjne z nazwanymi argumentami, należy\*dodać następujący element do pliku projektu języka Visual Basic ( .vbproj):</span><span class="sxs-lookup"><span data-stu-id="c96d4-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="c96d4-129">Aby uzyskać więcej informacji, zobacz [ustawianie wersji językowej języka Visual Basic](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="c96d4-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="c96d4-130">Ograniczenia dotyczące dostarczania argumentów według nazwy</span><span class="sxs-lookup"><span data-stu-id="c96d4-130">Restrictions on Supplying Arguments by Name</span></span>

<span data-ttu-id="c96d4-131">Nie można przekazać argumentów według nazwy, aby uniknąć wprowadzania wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="c96d4-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="c96d4-132">Można pominąć tylko opcjonalne argumenty.</span><span class="sxs-lookup"><span data-stu-id="c96d4-132">You can omit only the optional arguments.</span></span>

<span data-ttu-id="c96d4-133">Nie można przekazać tablicy parametrów według nazwy.</span><span class="sxs-lookup"><span data-stu-id="c96d4-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="c96d4-134">Dzieje się tak, ponieważ podczas wywoływania procedury, należy podać nieokreśloną liczbę argumentów oddzielonych przecinkami dla tablicy parametrów, a kompilator nie może skojarzyć więcej niż jeden argument z jedną nazwą.</span><span class="sxs-lookup"><span data-stu-id="c96d4-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>

## <a name="see-also"></a><span data-ttu-id="c96d4-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c96d4-135">See also</span></span>

- [<span data-ttu-id="c96d4-136">Procedury</span><span class="sxs-lookup"><span data-stu-id="c96d4-136">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c96d4-137">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="c96d4-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c96d4-138">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="c96d4-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="c96d4-139">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="c96d4-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c96d4-140">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="c96d4-140">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="c96d4-141">Parameter — Tablice</span><span class="sxs-lookup"><span data-stu-id="c96d4-141">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="c96d4-142">Opcjonalne</span><span class="sxs-lookup"><span data-stu-id="c96d4-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)
- [<span data-ttu-id="c96d4-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="c96d4-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
