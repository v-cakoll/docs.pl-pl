---
title: "Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)"
ms.custom: 
ms.date: 02/01/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13f5e5a8da6a899d4920a25b250ca88b2a21f559
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="fc18a-102">Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc18a-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="fc18a-103">Podczas wywoływania `Sub` lub `Function` procedury, można przekazywać argumenty *według położenia* — w kolejności, w jakiej występują w definicji procedury — lub można przekazać *według nazwy*, bez w odniesieniu do pozycji.</span><span class="sxs-lookup"><span data-stu-id="fc18a-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="fc18a-104">Jeśli argument według nazw, określ argument deklarowana przez nazwę dwukropek i znak równości (`:=`), a następnie wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="fc18a-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="fc18a-105">Możesz podać Argumenty nazwane w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="fc18a-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="fc18a-106">Na przykład następująca `Sub` procedury przyjmuje trzy argumenty:</span><span class="sxs-lookup"><span data-stu-id="fc18a-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 <span data-ttu-id="fc18a-107">Podczas wywoływania tej procedury, można podać argumentów według pozycji, według nazwy lub za pomocą ich kombinacjami.</span><span class="sxs-lookup"><span data-stu-id="fc18a-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="fc18a-108">Przekazywanie argumentów według pozycji</span><span class="sxs-lookup"><span data-stu-id="fc18a-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="fc18a-109">Możesz wywołać `Display` metody z argumentami przekazywane według pozycji i rozdzielonych przecinkami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fc18a-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 <span data-ttu-id="fc18a-110">W przypadku pominięcia opcjonalny argument w postaci listy argument pozycyjny, musi posiadać zamiast niej użyć przecinka.</span><span class="sxs-lookup"><span data-stu-id="fc18a-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="fc18a-111">Następujące przykładowe wywołania `Display` metody bez `age` argumentu:</span><span class="sxs-lookup"><span data-stu-id="fc18a-111">The following example calls the `Display` method without the `age` argument:</span></span>  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="fc18a-112">Przekazywanie argumentów według nazwy</span><span class="sxs-lookup"><span data-stu-id="fc18a-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="fc18a-113">Alternatywnie możesz wywołać `Display` argumentów przekazywane według nazw, również rozdzielonych przecinkami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fc18a-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 <span data-ttu-id="fc18a-114">Przekazywanie argumentów według nazwy w ten sposób jest szczególnie przydatna podczas wywoływania procedury, która ma więcej niż jeden argument opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="fc18a-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="fc18a-115">Należy podać argumenty według nazwy, nie trzeba używać przecinków kolejnych oznaczający brak argumenty pozycyjne.</span><span class="sxs-lookup"><span data-stu-id="fc18a-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="fc18a-116">Przekazywanie argumentów według nazwy również ułatwia do śledzenia argumenty, które są przekazywane i które pominięcie.</span><span class="sxs-lookup"><span data-stu-id="fc18a-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="fc18a-117">Mieszanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="fc18a-117">Mixing Arguments by Position and by Name</span></span>  

<span data-ttu-id="fc18a-118">Można podać argumenty zarówno według pozycji i według nazwy w wywołaniu procedury pojedynczego, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fc18a-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 <span data-ttu-id="fc18a-119">W powyższym przykładzie nie dodatkowy przecinek jest niezbędne do przechowywania miejsca pominięcia `age` argumentu, ponieważ `birth` jest przekazywana przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="fc18a-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
<span data-ttu-id="fc18a-120">W wersjach programu Visual Basic przed 15,5 cala gdy podać argumenty mieszaniną pozycji i nazwy, argumenty pozycyjne musi wszystkie znajdować na pierwszym.</span><span class="sxs-lookup"><span data-stu-id="fc18a-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="fc18a-121">Po podasz argument według nazwy, wszystkie pozostałe argumenty muszą wszystkie być przekazywane przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="fc18a-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="fc18a-122">Na przykład następujące wywołanie do `Display` metoda wyświetla błąd kompilatora [BC30241: nazwany argument, oczekiwano](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="fc18a-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

<span data-ttu-id="fc18a-123">Począwszy od programu Visual Basic 15,5 cala argumenty pozycyjne można wykonać nazwanych argumentów Jeśli końcowy argumenty pozycyjne są w poprawnej pozycji.</span><span class="sxs-lookup"><span data-stu-id="fc18a-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="fc18a-124">Jeśli skompilowany w obszarze 15,5 cala Visual Basic, poprzedniego wywołania `Display` metoda kompiluje pomyślnie i już nie generuje błąd kompilatora [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="fc18a-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>  

<span data-ttu-id="fc18a-125">Ta możliwość mieszać i dopasowywać argumentów nazwanych i pozycyjnych w dowolnej kolejności jest szczególnie przydatne, jeśli chcesz użyć nazwanego argumentu, aby zwiększyć czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="fc18a-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="fc18a-126">Na przykład następująca `Person` Konstruktor klasy wymaga dwóch argumentów typu `Person`, które mogą być `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fc18a-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span> 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

<span data-ttu-id="fc18a-127">Przy użyciu mieszanych argumentów nazwanych i pozycyjnych ułatwia celem kod wyczyścić, gdy wartość `father` i `mother` argumentów jest `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="fc18a-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

<span data-ttu-id="fc18a-128">Aby wykonać argumenty pozycyjne z argumentami nazwanymi, należy dodać następujący element do projekt programu Visual Basic (\*.vbproj) plików:</span><span class="sxs-lookup"><span data-stu-id="fc18a-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="fc18a-129">Ograniczenia dotyczące określenie argumentów według nazwy</span><span class="sxs-lookup"><span data-stu-id="fc18a-129">Restrictions on Supplying Arguments by Name</span></span>  

<span data-ttu-id="fc18a-130">Nie można przekazywać argumentów przez nazwę, aby uniknąć wprowadzenia wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="fc18a-130">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="fc18a-131">Można pominąć tylko argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="fc18a-131">You can omit only the optional arguments.</span></span>  
  
<span data-ttu-id="fc18a-132">Tablica parametrów nie można przekazać według nazwy.</span><span class="sxs-lookup"><span data-stu-id="fc18a-132">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="fc18a-133">To dlatego po wywołaniu procedury, podaj nieokreśloną liczbę rozdzielone przecinkami argumenty dla tablicy parametrów, a kompilator nie można skojarzyć więcej niż jeden argument pod jedną nazwą.</span><span class="sxs-lookup"><span data-stu-id="fc18a-133">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc18a-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc18a-134">See Also</span></span>  
 [<span data-ttu-id="fc18a-135">Procedury</span><span class="sxs-lookup"><span data-stu-id="fc18a-135">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="fc18a-136">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="fc18a-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="fc18a-137">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="fc18a-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="fc18a-138">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="fc18a-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="fc18a-139">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="fc18a-139">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="fc18a-140">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="fc18a-140">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="fc18a-141">Optional</span><span class="sxs-lookup"><span data-stu-id="fc18a-141">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="fc18a-142">ParamArray</span><span class="sxs-lookup"><span data-stu-id="fc18a-142">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
