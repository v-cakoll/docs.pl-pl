---
title: Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)
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
ms.openlocfilehash: bdaa0351e288b85a3e35818c0f53ef4d772932e5
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183870"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="57526-102">Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57526-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="57526-103">Gdy wywołujesz `Sub` lub `Function` procedury, można przekazać argumenty *według pozycji* — w kolejności, w jakiej są wyświetlane w definicji procedury — lub przekazać je *według nazwy*, bez uwzględniając pozycji.</span><span class="sxs-lookup"><span data-stu-id="57526-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="57526-104">Podczas przekazywania argumentu przez nazwę, należy określić argument deklarowana przez nazwę, a następnie dwukropek i znak równości (`:=`), a następnie wartość argumentu.</span><span class="sxs-lookup"><span data-stu-id="57526-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="57526-105">Możesz podać Argumenty nazwane w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="57526-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="57526-106">Na przykład następująca `Sub` procedury przyjmuje trzy argumenty:</span><span class="sxs-lookup"><span data-stu-id="57526-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 <span data-ttu-id="57526-107">Po wywołaniu tej procedury, można podać argumentów według pozycji według nazwy lub przy użyciu kombinacji obu.</span><span class="sxs-lookup"><span data-stu-id="57526-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="57526-108">Przekazywanie argumentów według pozycji</span><span class="sxs-lookup"><span data-stu-id="57526-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="57526-109">Możesz wywołać `Display` metody z argumentami przekazywane według pozycji i rozdzielone przecinkami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="57526-109">You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 <span data-ttu-id="57526-110">Jeżeli pominięto opcjonalny argument na liście argumentów pozycyjnych muszą przechowywać jej miejscu za pomocą przecinka.</span><span class="sxs-lookup"><span data-stu-id="57526-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="57526-111">Poniższy przykład wywołuje `Display` metody bez `age` argumentu:</span><span class="sxs-lookup"><span data-stu-id="57526-111">The following example calls the `Display` method without the `age` argument:</span></span>  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="57526-112">Przekazywanie argumentów według nazwy</span><span class="sxs-lookup"><span data-stu-id="57526-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="57526-113">Ewentualnie możesz wywołać `Display` argumenty przekazywane według nazwy, również rozdzielone przecinkami, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="57526-113">Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 <span data-ttu-id="57526-114">Przekazywanie argumentów według nazwy w ten sposób jest szczególnie przydatne w przypadku, gdy wywołujesz procedurę, która ma więcej niż jeden opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="57526-114">Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="57526-115">Jeśli podasz argumentów według nazwy, ma oznaczają brakujące argumenty pozycyjne przy użyciu następujących po sobie przecinków.</span><span class="sxs-lookup"><span data-stu-id="57526-115">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="57526-116">Przekazywanie argumentów według nazwy również ułatwia do śledzenia argumentów, które kończy się sukcesem i pomijanie te, które.</span><span class="sxs-lookup"><span data-stu-id="57526-116">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="57526-117">Mieszanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="57526-117">Mixing Arguments by Position and by Name</span></span>  

<span data-ttu-id="57526-118">Można podać argumentów według pozycji i według nazwy w wywołaniu samą procedurą, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="57526-118">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 <span data-ttu-id="57526-119">W powyższym przykładzie nie dodatkowy przecinek jest niezbędne do przechowywania miejsca pominięty `age` argumentu, ponieważ `birth` jest przekazywany przez nazwę.</span><span class="sxs-lookup"><span data-stu-id="57526-119">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
<span data-ttu-id="57526-120">W wersji programu Visual Basic przed 15.5 podczas podawania argumenty przez kombinację pozycji i nazwy, argumentów pozycyjnych muszą wszystkich umieszczone jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="57526-120">In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="57526-121">Gdy podasz argument według nazwy, wszelkie pozostałe argumenty muszą wszystkie być przekazywane według nazwy.</span><span class="sxs-lookup"><span data-stu-id="57526-121">Once you supply an argument by name, any remaining arguments must all be passed by name.</span></span>  <span data-ttu-id="57526-122">Na przykład, następujące wywołanie do `Display` metoda wyświetla błąd kompilatora [BC30241: Oczekiwano argumentu nazwanego](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="57526-122">For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

<span data-ttu-id="57526-123">Począwszy od wersji 15.5 programu Visual Basic, argumenty pozycyjne wykonać argumenty nazwane jeśli końcowa argumenty pozycyjne są w poprawnej pozycji.</span><span class="sxs-lookup"><span data-stu-id="57526-123">Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position.</span></span> <span data-ttu-id="57526-124">Jeśli skompilowany w wersji 15.5 programu Visual Basic, poprzednie wywołanie `Display` metoda pomyślnie wykonuje kompilację i już nie generuje błąd kompilatora [BC30241](../../../misc/bc30241.md).</span><span class="sxs-lookup"><span data-stu-id="57526-124">If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).</span></span>  

<span data-ttu-id="57526-125">Ta możliwość mieszanie i dopasowywanie argumentów nazwanych i pozycyjnych w dowolnej kolejności jest szczególnie przydatne, jeśli chcesz użyć nazwanego argumentu, aby zwiększyć czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="57526-125">This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable.</span></span> <span data-ttu-id="57526-126">Na przykład następująca `Person` konstruktora klasy wymaga dwóch argumentów typu `Person`, które mogą być `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="57526-126">For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.</span></span> 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

<span data-ttu-id="57526-127">Za pomocą mieszanego argumentów nazwanych i pozycyjnych, które ułatwia celem kod, usuń zaznaczenie, gdy wartość `father` i `mother` argumenty są `Nothing`:</span><span class="sxs-lookup"><span data-stu-id="57526-127">Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:</span></span>

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

<span data-ttu-id="57526-128">Aby skorzystać z argumentów pozycyjnych z argumentami nazwanego, należy dodać następujący element do projektu języka Visual Basic (\*.vbproj) pliku:</span><span class="sxs-lookup"><span data-stu-id="57526-128">To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:</span></span>

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="57526-129">Aby uzyskać więcej informacji, zobacz [ustawienie wersji języka Visual Basic](../../../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="57526-129">For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).</span></span>

## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="57526-130">Ograniczenia dotyczące podanie argumentów według nazwy</span><span class="sxs-lookup"><span data-stu-id="57526-130">Restrictions on Supplying Arguments by Name</span></span>  

<span data-ttu-id="57526-131">Nie można przekazywać argumentów według nazwy, aby uniknąć wpisywania wymaganych argumentów.</span><span class="sxs-lookup"><span data-stu-id="57526-131">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="57526-132">Można pominąć opcjonalne argumenty.</span><span class="sxs-lookup"><span data-stu-id="57526-132">You can omit only the optional arguments.</span></span>  
  
<span data-ttu-id="57526-133">Tablica parametrów nie można przekazać według nazwy.</span><span class="sxs-lookup"><span data-stu-id="57526-133">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="57526-134">Jest to spowodowane po wywołaniu procedury, podaj nieskończona liczba rozdzielonych przecinkami argumenty tablicą parametrów, a kompilator nie można skojarzyć więcej niż jeden argument nazwą jednego.</span><span class="sxs-lookup"><span data-stu-id="57526-134">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57526-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="57526-135">See Also</span></span>  
 [<span data-ttu-id="57526-136">Procedury</span><span class="sxs-lookup"><span data-stu-id="57526-136">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="57526-137">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="57526-137">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="57526-138">Instrukcje: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="57526-138">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="57526-139">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="57526-139">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="57526-140">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="57526-140">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="57526-141">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="57526-141">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="57526-142">Optional</span><span class="sxs-lookup"><span data-stu-id="57526-142">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="57526-143">ParamArray</span><span class="sxs-lookup"><span data-stu-id="57526-143">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
