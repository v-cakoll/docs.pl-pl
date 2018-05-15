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
ms.openlocfilehash: e1768d0ac03cb6730c4337d7476ae163e75adfd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="d8a27-102">Zagadnienia dotyczące przeciążania procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8a27-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="d8a27-103">Przeciążanie procedury, należy używać innej *podpisu* dla każdej wersji przeciążona.</span><span class="sxs-lookup"><span data-stu-id="d8a27-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="d8a27-104">Zwykle oznacza to, że każda wersja należy określić inną listą parametrów.</span><span class="sxs-lookup"><span data-stu-id="d8a27-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="d8a27-105">Aby uzyskać więcej informacji, zobacz "Inny podpis" w [przeciążanie procedury](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="d8a27-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="d8a27-106">Można przeciążać `Function` procedury z `Sub` procedury i na odwrót, pod warunkiem mają różnych podpisów.</span><span class="sxs-lookup"><span data-stu-id="d8a27-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="d8a27-107">Dwa przeciążenia nie różnią się tylko jedna ma wartość zwracaną, a drugi nie.</span><span class="sxs-lookup"><span data-stu-id="d8a27-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="d8a27-108">Można przeciążać właściwości tak samo przeciążanie procedury i z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="d8a27-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="d8a27-109">Jednak nie mogą przeciążać procedury z właściwością lub na odwrót.</span><span class="sxs-lookup"><span data-stu-id="d8a27-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="d8a27-110">Alternatywy dla wersji przeciążone</span><span class="sxs-lookup"><span data-stu-id="d8a27-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="d8a27-111">Czasami masz alternatywy dla przeciążonej wersje, zwłaszcza w przypadku obecności argumentów jest opcjonalny, lub ich numer zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d8a27-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="d8a27-112">Należy pamiętać, że argumenty opcjonalne nie są zawsze obsługiwane przez wszystkie języki, a tablice parametrów są ograniczone do języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d8a27-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="d8a27-113">Jeśli piszesz procedury, która może być wywoływana z kodu napisanego w jednym z kilku różnych języków przeciążony oferta wersji największą elastyczność.</span><span class="sxs-lookup"><span data-stu-id="d8a27-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="d8a27-114">Przeciążenia i argumentów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="d8a27-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="d8a27-115">Kod wywołujący może opcjonalnie podaj lub pominąć jeden lub więcej argumentów, można zdefiniować wiele wersji przeciążone lub opcjonalne parametry.</span><span class="sxs-lookup"><span data-stu-id="d8a27-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="d8a27-116">Kiedy należy używać przeciążonej wersji</span><span class="sxs-lookup"><span data-stu-id="d8a27-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="d8a27-117">Można rozważyć możliwość definiowania serii zastąpionej wersji w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="d8a27-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="d8a27-118">Logikę w kodzie procedury znacznie różni się w zależności od tego, czy kod wywołujący dostarcza opcjonalny argument lub nie.</span><span class="sxs-lookup"><span data-stu-id="d8a27-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
-   <span data-ttu-id="d8a27-119">Kod procedury niezawodnie nie może sprawdzić, czy kod wywołujący udostępnił opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="d8a27-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="d8a27-120">Jest to możliwe, na przykład, jeśli nie jest domyślna wartość, która nie kandydatem kod wywołujący nie należy się spodziewać umożliwiają określanie wartości.</span><span class="sxs-lookup"><span data-stu-id="d8a27-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="d8a27-121">Kiedy należy używać następujące parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="d8a27-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="d8a27-122">Można wybrać co najmniej jeden parametr opcjonalny w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="d8a27-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
-   <span data-ttu-id="d8a27-123">Tylko niezbędne czynności podczas kod wywołujący nie dostarcza opcjonalny argument jest ustawić parametr na wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="d8a27-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="d8a27-124">W takim przypadku kod procedura może być mniej skomplikowane, w przypadku definiowania jednej wersji co najmniej jednym `Optional` parametrów.</span><span class="sxs-lookup"><span data-stu-id="d8a27-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="d8a27-125">Aby uzyskać więcej informacji, zobacz [następujące parametry opcjonalne](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="d8a27-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="d8a27-126">Przeciążenia i ParamArrays</span><span class="sxs-lookup"><span data-stu-id="d8a27-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="d8a27-127">Gdy kod wywołujący może przekazać zmienna liczba argumentów, można zdefiniować wiele wersji przeciążone lub użyj tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="d8a27-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="d8a27-128">Kiedy należy używać przeciążonej wersji</span><span class="sxs-lookup"><span data-stu-id="d8a27-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="d8a27-129">Można rozważyć możliwość definiowania serii zastąpionej wersji w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="d8a27-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
-   <span data-ttu-id="d8a27-130">Wiadomo, że kod wywołujący nigdy nie przekazuje więcej niż małej liczby wartości do tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="d8a27-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
-   <span data-ttu-id="d8a27-131">Logikę w kodzie procedury znacznie różni się w zależności od tego, ile wartości przekazuje kod wywołujący.</span><span class="sxs-lookup"><span data-stu-id="d8a27-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
-   <span data-ttu-id="d8a27-132">Kod wywołujący może przekazać wartości różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="d8a27-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="d8a27-133">Kiedy należy używać tablicy parametrów</span><span class="sxs-lookup"><span data-stu-id="d8a27-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="d8a27-134">Czy można lepiej obsłużone przez `ParamArray` parametru w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="d8a27-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
-   <span data-ttu-id="d8a27-135">Nie jest możliwe do prognozowania wartości ile kod wywołujący może przekazać do tablicy parametrów i może być wiele.</span><span class="sxs-lookup"><span data-stu-id="d8a27-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
-   <span data-ttu-id="d8a27-136">Logika procedury pozwala na przechodzenie przez wszystkie wartości przekazuje kodu wywołującego, wykonywanie zasadniczo tej samej operacji w każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="d8a27-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="d8a27-137">Aby uzyskać więcej informacji, zobacz [tablice parametrów](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="d8a27-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="d8a27-138">Niejawne przeładowania dla następujące parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="d8a27-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="d8a27-139">Procedury z [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametru jest odpowiednikiem dwie procedury przeciążenia, jeden z opcjonalnym parametrem i drugi bez niego.</span><span class="sxs-lookup"><span data-stu-id="d8a27-139">A procedure with an [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="d8a27-140">Nie można przeciążyć takiej procedury z listą parametrów odpowiadający jednego z tych.</span><span class="sxs-lookup"><span data-stu-id="d8a27-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="d8a27-141">Następujące deklaracje ilustrację.</span><span class="sxs-lookup"><span data-stu-id="d8a27-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](./codesnippet/VisualBasic/considerations-in-overloading-procedures_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/considerations-in-overloading-procedures_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/considerations-in-overloading-procedures_3.vb)]  
  
 <span data-ttu-id="d8a27-142">Procedury z więcej niż jeden parametr opcjonalny jest zestaw niejawne przeładowania przez logikę, podobnie jak w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d8a27-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="d8a27-143">Niejawne przeładowania dla parametru ParamArray</span><span class="sxs-lookup"><span data-stu-id="d8a27-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="d8a27-144">Kompilator uwzględnia procedury z [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru nieograniczoną liczbę przeciążenia, różniące się od siebie co kod wywołujący przekazuje do tablicy parametrów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d8a27-144">The compiler considers a procedure with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
-   <span data-ttu-id="d8a27-145">Przeciążeniami dla gdy kod wywołujący nie dostarcza argument `ParamArray`</span><span class="sxs-lookup"><span data-stu-id="d8a27-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
-   <span data-ttu-id="d8a27-146">Przeciążeniami dla podczas wywoływania kodu dostarcza Jednowymiarowa tablica `ParamArray` typ elementu</span><span class="sxs-lookup"><span data-stu-id="d8a27-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
-   <span data-ttu-id="d8a27-147">Dla każdego dodatnią liczbą całkowitą, jeden przeciążenia dla gdy kod wywołujący dostarcza tej liczby argumentów, każdy z `ParamArray` typ elementu</span><span class="sxs-lookup"><span data-stu-id="d8a27-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="d8a27-148">Następujące deklaracje ilustrują te niejawne przeładowania.</span><span class="sxs-lookup"><span data-stu-id="d8a27-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](./codesnippet/VisualBasic/considerations-in-overloading-procedures_4.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/considerations-in-overloading-procedures_5.vb)]  
  
 <span data-ttu-id="d8a27-149">Nie można przeciążyć procedury z listą parametrów pobierającej tablicą jednowymiarową dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="d8a27-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="d8a27-150">Można jednak użyć podpisy niejawne przeładowania.</span><span class="sxs-lookup"><span data-stu-id="d8a27-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="d8a27-151">Następujące deklaracje ilustrację.</span><span class="sxs-lookup"><span data-stu-id="d8a27-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/considerations-in-overloading-procedures_6.vb)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="d8a27-152">Alternatywą wobec przeładowanie programowanie Nietypowane</span><span class="sxs-lookup"><span data-stu-id="d8a27-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="d8a27-153">Jeśli chcesz zezwolić kod wywołujący do przekazania do parametru różne typy danych, alternatywne podejście jest nietypowane.</span><span class="sxs-lookup"><span data-stu-id="d8a27-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="d8a27-154">Można ustawić typ sprawdzania przełącznik `Off` przy użyciu jednej [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) lub [/optionstrict —](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d8a27-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) or the [/optionstrict](../../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="d8a27-155">Następnie trzeba zadeklarować typ danych parametru.</span><span class="sxs-lookup"><span data-stu-id="d8a27-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="d8a27-156">Jednak ta metoda ma następujące wady w porównaniu do przeciążania:</span><span class="sxs-lookup"><span data-stu-id="d8a27-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
-   <span data-ttu-id="d8a27-157">Programowanie nietypowane tworzy mniej wydajne wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="d8a27-157">Typeless programming produces less efficient execution code.</span></span>  
  
-   <span data-ttu-id="d8a27-158">Dla każdego typu danych oszacowano, przekazywany jest przetestowanie procedury.</span><span class="sxs-lookup"><span data-stu-id="d8a27-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
-   <span data-ttu-id="d8a27-159">Kompilator nie może sygnał wystąpił błąd, jeśli kod wywołujący przekazuje procedura obsługuje tylko typ danych.</span><span class="sxs-lookup"><span data-stu-id="d8a27-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a27-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8a27-160">See Also</span></span>  
 [<span data-ttu-id="d8a27-161">Procedury</span><span class="sxs-lookup"><span data-stu-id="d8a27-161">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="d8a27-162">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="d8a27-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d8a27-163">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="d8a27-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="d8a27-164">Instrukcje: definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="d8a27-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="d8a27-165">Instrukcje: wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="d8a27-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="d8a27-166">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="d8a27-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="d8a27-167">Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów</span><span class="sxs-lookup"><span data-stu-id="d8a27-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="d8a27-168">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="d8a27-168">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="d8a27-169">Overloads</span><span class="sxs-lookup"><span data-stu-id="d8a27-169">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
