---
title: Zagadnienia dotyczące przeciążania procedur (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures [Visual Basic], ParamArray arguments
- ParamArray keyword [Visual Basic], parameter arrays
- ParamArray keyword [Visual Basic], arguments and signatures
- function overloading [Visual Basic], implicit overloads for ParamArray
- ParamArray keyword [Visual Basic], signatures
- Visual Basic code, procedures
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], overloading
- parameters [Visual Basic], lists
- function overloading [Visual Basic], typeless programming
- typeless programming
- function overloading [Visual Basic], restrictions
- arguments [Visual Basic], optional
- optional arguments [Visual Basic], overloading
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- parameter arrays [Visual Basic], overloading arguments
- Visual Basic code, parameter lists
- procedure overloading [Visual Basic], considerations
- Option Explicit statement [Visual Basic]
- restrictions [Visual Basic], overloading procedures
- procedures [Visual Basic], parameter lists
ms.assetid: a2001248-10d0-42c5-b0ce-eeedc987319f
ms.openlocfilehash: 8dfee8a8678fb00fcded4b7da57c3b200ef64d69
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979544"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="90850-102">Zagadnienia dotyczące przeciążania procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90850-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="90850-103">Możesz przeciążanie procedury, należy użyć innego *podpisu* dla każdej wersji przeciążona.</span><span class="sxs-lookup"><span data-stu-id="90850-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="90850-104">Zwykle oznacza to, że każda wersja należy określić inną listą parametrów.</span><span class="sxs-lookup"><span data-stu-id="90850-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="90850-105">Aby uzyskać więcej informacji, zobacz "Inny podpis" w [przeciążanie procedury](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="90850-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="90850-106">Możesz doprowadzić do przeciążenia `Function` procedury z `Sub` procedury i na odwrót, pod warunkiem mają różnych podpisów.</span><span class="sxs-lookup"><span data-stu-id="90850-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="90850-107">Dwa przeciążenia nie różnią się tylko jeden z nich nie zwraca wartości, a drugi nie.</span><span class="sxs-lookup"><span data-stu-id="90850-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="90850-108">Możesz doprowadzić do przeciążenia właściwości taki sam sposób, przeciążanie procedury i z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="90850-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="90850-109">Jednak nie mogą przeciążać procedury z właściwością lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="90850-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="90850-110">Alternatywy dla przeciążone wersje</span><span class="sxs-lookup"><span data-stu-id="90850-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="90850-111">Czasami masz alternatyw przeciążone wersje, zwłaszcza w przypadku obecności argumentów jest opcjonalne, lub ich liczba jest zmienna.</span><span class="sxs-lookup"><span data-stu-id="90850-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="90850-112">Należy pamiętać, że opcjonalne argumenty nie są zawsze obsługiwane przez wszystkie języki i tablice parametrów są ograniczone do języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="90850-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="90850-113">Jeśli piszesz procedury, która może być wywoływana z kodu napisanego w dowolnym z kilku różnych języków, przeciążone wersje oferty największą elastyczność.</span><span class="sxs-lookup"><span data-stu-id="90850-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="90850-114">Przeciążenia i argumenty opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="90850-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="90850-115">Gdy kod wywołujący może opcjonalnie podaj lub Pomiń jeden lub więcej argumentów, można zdefiniować wiele przeciążone wersje, lub korzystanie z parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="90850-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="90850-116">Kiedy należy używać przeciążone wersje</span><span class="sxs-lookup"><span data-stu-id="90850-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="90850-117">Można rozważyć Definiowanie szereg przeciążone wersje w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="90850-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="90850-118">Logiki w kodzie procedury różni się znacznie w zależności od tego, czy kod wywołujący dostarcza opcjonalny argument, czy nie.</span><span class="sxs-lookup"><span data-stu-id="90850-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="90850-119">Kod procedury niezawodne nie można sprawdzić, czy kod wywołujący udostępnił opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="90850-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="90850-120">Jest to możliwe, na przykład, jeśli ma nie kandydatem dla domyślną wartość, która kod wywołujący nie należy się spodziewać umożliwiają określanie wartości.</span><span class="sxs-lookup"><span data-stu-id="90850-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="90850-121">Kiedy należy używać parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="90850-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="90850-122">Można wybrać co najmniej jeden parametr opcjonalny w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="90850-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="90850-123">Tylko niezbędne czynności podczas wywoływania kodu nie dostarcza opcjonalny argument jest ustawić parametr na wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="90850-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="90850-124">W takiej sytuacji kod procedury może być mniej skomplikowany, jeśli zdefiniujesz z co najmniej jedną wersję `Optional` parametrów.</span><span class="sxs-lookup"><span data-stu-id="90850-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="90850-125">Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="90850-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="90850-126">Przeciążenia i ParamArrays</span><span class="sxs-lookup"><span data-stu-id="90850-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="90850-127">Gdy kod wywołujący może przekazać zmienną liczbę argumentów, można zdefiniować wiele przeciążone wersje, lub użyj tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="90850-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="90850-128">Kiedy należy używać przeciążone wersje</span><span class="sxs-lookup"><span data-stu-id="90850-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="90850-129">Można rozważyć Definiowanie szereg przeciążone wersje w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="90850-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="90850-130">Wiesz, że kod wywołujący nigdy nie przekazuje ponad niewielka liczba wartości do tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="90850-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="90850-131">Logiki w kodzie procedura jest znacząco różne w zależności od tego, jak wiele wartości, które przekazuje kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="90850-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="90850-132">Kod wywołujący można przekazać wartości różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="90850-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="90850-133">Kiedy należy używać tablicy parametrów</span><span class="sxs-lookup"><span data-stu-id="90850-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="90850-134">Sięganie po `ParamArray` parametru w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="90850-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="90850-135">Nie jesteś w stanie przewidzieć liczbę wartości, kod wywołujący można przekazać do tablicy parametrów i może być duża liczba.</span><span class="sxs-lookup"><span data-stu-id="90850-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="90850-136">Logika procedury pozwala na przechodzenie przez wszystkie wartości, które przekazuje kodu wywołującego, wykonywanie zasadniczo tej samej operacji na każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="90850-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="90850-137">Aby uzyskać więcej informacji, zobacz [Parameter — tablice](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="90850-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="90850-138">Niejawne przeładowania dla parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="90850-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="90850-139">Procedury z [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametr jest równoważny dwóch procedur przeciążona, jeden z opcjonalnym parametrem i jedną bez niego.</span><span class="sxs-lookup"><span data-stu-id="90850-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="90850-140">Nie mogą przeciążać takiej procedury z listą parametrów odpowiadający jedną z tych wersji.</span><span class="sxs-lookup"><span data-stu-id="90850-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="90850-141">Następujące deklaracje pokazują to.</span><span class="sxs-lookup"><span data-stu-id="90850-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="90850-142">Procedury z więcej niż jeden parametr opcjonalny istnieje zestaw niejawne przeładowania, dotarły przez logikę, podobnie jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="90850-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="90850-143">Niejawne przeładowania dla ParamArray parametru</span><span class="sxs-lookup"><span data-stu-id="90850-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="90850-144">Kompilator traktuje procedury z [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru, aby mieć nieograniczoną liczbę przeciążeń, różniące się od siebie nawzajem co kod wywołujący przekazuje do tablicy parametrów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="90850-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="90850-145">Gdy kod wywołujący nie podać argument do jednego przeciążenia `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="90850-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="90850-146">Gdy kod wywołujący dostarcza Jednowymiarowa tablica jednego przeciążenia `ParamArray` typ elementu</span><span class="sxs-lookup"><span data-stu-id="90850-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="90850-147">Dla każdego dodatnią liczbą całkowitą jednego przeciążenia dla gdy kod wywołujący dostarcza tę liczbę argumentów, każdy z `ParamArray` typ elementu</span><span class="sxs-lookup"><span data-stu-id="90850-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="90850-148">Następujące deklaracje pokazują te niejawne przeładowania.</span><span class="sxs-lookup"><span data-stu-id="90850-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="90850-149">Nie można przeciążyć procedury z listą parametrów, który przyjmuje tablicę jednowymiarową dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="90850-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="90850-150">Można jednak użyć podpisy niejawne przeładowania.</span><span class="sxs-lookup"><span data-stu-id="90850-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="90850-151">Następujące deklaracje pokazują to.</span><span class="sxs-lookup"><span data-stu-id="90850-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="90850-152">Programowanie nietypowane jako alternatywę do przeciążania</span><span class="sxs-lookup"><span data-stu-id="90850-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="90850-153">Jeśli chcesz zezwolić na kod wywołujący, aby przekazać różne typy danych do parametru alternatywnym podejściem jest programowanie nietypowane.</span><span class="sxs-lookup"><span data-stu-id="90850-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="90850-154">Można ustawić typ sprawdzania przełącznik `Off` z oboma [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) lub [/optionstrict —](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="90850-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="90850-155">Następnie trzeba zadeklarować typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="90850-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="90850-156">Jednak to podejście ma następujące wady w porównaniu do przeciążania:</span><span class="sxs-lookup"><span data-stu-id="90850-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="90850-157">Programowanie nietypowane generuje kod, mniej wydajne wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="90850-157">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="90850-158">Procedury należy przetestować dla każdego typu danych, które przewiduje, przekazywana.</span><span class="sxs-lookup"><span data-stu-id="90850-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="90850-159">Kompilator nie zasygnalizować błąd, jeśli kod wywołujący przekazuje typ danych, który nie obsługuje procedury.</span><span class="sxs-lookup"><span data-stu-id="90850-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90850-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90850-160">See also</span></span>
- [<span data-ttu-id="90850-161">Procedury</span><span class="sxs-lookup"><span data-stu-id="90850-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="90850-162">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="90850-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="90850-163">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="90850-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="90850-164">Instrukcje: Definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="90850-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="90850-165">Instrukcje: Wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="90850-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="90850-166">Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="90850-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="90850-167">Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="90850-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="90850-168">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="90850-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="90850-169">Overloads</span><span class="sxs-lookup"><span data-stu-id="90850-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
