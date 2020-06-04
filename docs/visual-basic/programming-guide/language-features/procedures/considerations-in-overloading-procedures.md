---
title: Zagadnienia dotyczące przeciążania procedur
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
ms.openlocfilehash: c4075c87df8b9daa56ca1d35e0d6661598895fdc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403372"
---
# <a name="considerations-in-overloading-procedures-visual-basic"></a><span data-ttu-id="f232c-102">Zagadnienia dotyczące przeciążania procedur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f232c-102">Considerations in Overloading Procedures (Visual Basic)</span></span>
<span data-ttu-id="f232c-103">W przypadku przeciążenia procedury należy użyć innej *sygnatury* dla każdej przeciążonej wersji.</span><span class="sxs-lookup"><span data-stu-id="f232c-103">When you overload a procedure, you must use a different *signature* for each overloaded version.</span></span> <span data-ttu-id="f232c-104">Zazwyczaj oznacza to, że każda wersja musi określać inną listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="f232c-104">This usually means each version must specify a different parameter list.</span></span> <span data-ttu-id="f232c-105">Aby uzyskać więcej informacji, zobacz "różne sygnatury" podczas [przeciążania procedur](./procedure-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="f232c-105">For more information, see "Different Signature" in [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
 <span data-ttu-id="f232c-106">Można przeciążyć `Function` procedurę za pomocą `Sub` procedury i na odwrót, pod warunkiem, że mają różne sygnatury.</span><span class="sxs-lookup"><span data-stu-id="f232c-106">You can overload a `Function` procedure with a `Sub` procedure, and vice versa, provided they have different signatures.</span></span> <span data-ttu-id="f232c-107">Dwa przeciążenia nie mogą się różnić tylko w tym, że ma wartość zwracaną, a druga nie.</span><span class="sxs-lookup"><span data-stu-id="f232c-107">Two overloads cannot differ only in that one has a return value and the other does not.</span></span>  
  
 <span data-ttu-id="f232c-108">Można przeciążać Właściwość tak samo jak w przypadku przeciążenia procedury i z tymi samymi ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="f232c-108">You can overload a property the same way you overload a procedure, and with the same restrictions.</span></span> <span data-ttu-id="f232c-109">Nie można jednak przeciążać procedury z właściwością lub odwrotnie.</span><span class="sxs-lookup"><span data-stu-id="f232c-109">However, you cannot overload a procedure with a property, or vice versa.</span></span>  
  
## <a name="alternatives-to-overloaded-versions"></a><span data-ttu-id="f232c-110">Alternatywy dla przeciążonych wersji</span><span class="sxs-lookup"><span data-stu-id="f232c-110">Alternatives to Overloaded Versions</span></span>  
 <span data-ttu-id="f232c-111">Czasami istnieją alternatywy dla przeciążonych wersji, szczególnie gdy obecność argumentów jest opcjonalna lub ich liczba jest zmienna.</span><span class="sxs-lookup"><span data-stu-id="f232c-111">You sometimes have alternatives to overloaded versions, particularly when the presence of arguments is optional or their number is variable.</span></span>  
  
 <span data-ttu-id="f232c-112">Należy pamiętać, że argumenty opcjonalne nie są koniecznie obsługiwane przez wszystkie języki, a tablice parametrów są ograniczone do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f232c-112">Keep in mind that optional arguments are not necessarily supported by all languages, and parameter arrays are limited to Visual Basic.</span></span> <span data-ttu-id="f232c-113">Jeśli piszesz procedurę, która prawdopodobnie zostanie wywołana z kodu napisanego w jednym z kilku różnych języków, przeciążone wersje zapewniają największą elastyczność.</span><span class="sxs-lookup"><span data-stu-id="f232c-113">If you are writing a procedure that is likely to be called from code written in any of several different languages, overloaded versions offer the greatest flexibility.</span></span>  
  
### <a name="overloads-and-optional-arguments"></a><span data-ttu-id="f232c-114">Przeciążenia i opcjonalne argumenty</span><span class="sxs-lookup"><span data-stu-id="f232c-114">Overloads and Optional Arguments</span></span>  
 <span data-ttu-id="f232c-115">Gdy wywoływany kod może opcjonalnie dostarczyć lub pominąć jeden lub więcej argumentów, można zdefiniować wiele przeciążonych wersji lub użyć parametrów opcjonalnych.</span><span class="sxs-lookup"><span data-stu-id="f232c-115">When the calling code can optionally supply or omit one or more arguments, you can define multiple overloaded versions or use optional parameters.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="f232c-116">Kiedy używać przeciążonych wersji</span><span class="sxs-lookup"><span data-stu-id="f232c-116">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="f232c-117">Można rozważyć zdefiniowanie szeregu przeciążonych wersji w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="f232c-117">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="f232c-118">Logika w kodzie procedury jest znacznie inna w zależności od tego, czy wywoływany kod dostarcza opcjonalny argument, czy nie.</span><span class="sxs-lookup"><span data-stu-id="f232c-118">The logic in the procedure code is significantly different depending on whether the calling code supplies an optional argument or not.</span></span>  
  
- <span data-ttu-id="f232c-119">Kod procedury nie może niezawodnie sprawdzić, czy wywoływany kod dostarczył opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="f232c-119">The procedure code cannot reliably test whether the calling code has supplied an optional argument.</span></span> <span data-ttu-id="f232c-120">Dotyczy to na przykład sytuacji, gdy nie istnieje możliwy kandydat dla wartości domyślnej, która nie może zostać dostarczona do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f232c-120">This is the case, for example, if there is no possible candidate for a default value that the calling code could not be expected to supply.</span></span>  
  
#### <a name="when-to-use-optional-parameters"></a><span data-ttu-id="f232c-121">Kiedy należy używać parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="f232c-121">When to Use Optional Parameters</span></span>  
 <span data-ttu-id="f232c-122">W następujących przypadkach może być preferowany co najmniej jeden parametr opcjonalny:</span><span class="sxs-lookup"><span data-stu-id="f232c-122">You might prefer one or more optional parameters in the following cases:</span></span>  
  
- <span data-ttu-id="f232c-123">Jedyną wymaganą akcją, gdy wywoływany kod nie dostarcza opcjonalnego argumentu, jest ustawienie wartości domyślnej dla parametru.</span><span class="sxs-lookup"><span data-stu-id="f232c-123">The only required action when the calling code does not supply an optional argument is to set the parameter to a default value.</span></span> <span data-ttu-id="f232c-124">W takim przypadku kod procedury może być mniej skomplikowany w przypadku zdefiniowania jednej wersji z co najmniej jednym `Optional` parametrem.</span><span class="sxs-lookup"><span data-stu-id="f232c-124">In such a case, the procedure code can be less complicated if you define a single version with one or more `Optional` parameters.</span></span>  
  
 <span data-ttu-id="f232c-125">Aby uzyskać więcej informacji, zobacz [Parametry opcjonalne](./optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f232c-125">For more information, see [Optional Parameters](./optional-parameters.md).</span></span>  
  
### <a name="overloads-and-paramarrays"></a><span data-ttu-id="f232c-126">Przeciążenia i ParamArray</span><span class="sxs-lookup"><span data-stu-id="f232c-126">Overloads and ParamArrays</span></span>  
 <span data-ttu-id="f232c-127">Gdy wywoływany kod może przekazać zmienną liczbę argumentów, można zdefiniować wiele przeciążonych wersji lub użyć tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="f232c-127">When the calling code can pass a variable number of arguments, you can define multiple overloaded versions or use a parameter array.</span></span>  
  
#### <a name="when-to-use-overloaded-versions"></a><span data-ttu-id="f232c-128">Kiedy używać przeciążonych wersji</span><span class="sxs-lookup"><span data-stu-id="f232c-128">When to Use Overloaded Versions</span></span>  
 <span data-ttu-id="f232c-129">Można rozważyć zdefiniowanie szeregu przeciążonych wersji w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="f232c-129">You can consider defining a series of overloaded versions in the following cases:</span></span>  
  
- <span data-ttu-id="f232c-130">Wiadomo, że wywoływany kod nigdy nie przekazuje więcej niż niewielką liczbę wartości do tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="f232c-130">You know that the calling code never passes more than a small number of values to the parameter array.</span></span>  
  
- <span data-ttu-id="f232c-131">Logika w kodzie procedury jest znacznie inna w zależności od liczby wartości przekazywanych przez wywoływany kod.</span><span class="sxs-lookup"><span data-stu-id="f232c-131">The logic in the procedure code is significantly different depending on how many values the calling code passes.</span></span>  
  
- <span data-ttu-id="f232c-132">Kod wywołujący może przekazywać wartości różnych typów danych.</span><span class="sxs-lookup"><span data-stu-id="f232c-132">The calling code can pass values of different data types.</span></span>  
  
#### <a name="when-to-use-a-parameter-array"></a><span data-ttu-id="f232c-133">Kiedy używać tablicy parametrów</span><span class="sxs-lookup"><span data-stu-id="f232c-133">When to Use a Parameter Array</span></span>  
 <span data-ttu-id="f232c-134">Są one lepiej obsługiwane przez `ParamArray` parametr w następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="f232c-134">You are better served by a `ParamArray` parameter in the following cases:</span></span>  
  
- <span data-ttu-id="f232c-135">Nie można przewidzieć, ile wartości kod wywołujący może być przekazywany do tablicy parametrów i może być dużą liczbą.</span><span class="sxs-lookup"><span data-stu-id="f232c-135">You are not able to predict how many values the calling code can pass to the parameter array, and it could be a large number.</span></span>  
  
- <span data-ttu-id="f232c-136">Logika procedury polega na przeprowadzeniu iteracji przez wszystkie wartości, które wywołuje wywoływany kod, wykonując zasadniczo te same operacje na każdej wartości.</span><span class="sxs-lookup"><span data-stu-id="f232c-136">The procedure logic lends itself to iterating through all the values the calling code passes, performing essentially the same operations on every value.</span></span>  
  
 <span data-ttu-id="f232c-137">Aby uzyskać więcej informacji, zobacz [tablice parametrów](./parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="f232c-137">For more information, see [Parameter Arrays](./parameter-arrays.md).</span></span>  
  
## <a name="implicit-overloads-for-optional-parameters"></a><span data-ttu-id="f232c-138">Niejawne przeciążenia dla parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="f232c-138">Implicit Overloads for Optional Parameters</span></span>  
 <span data-ttu-id="f232c-139">Procedura z [opcjonalnym](../../../language-reference/modifiers/optional.md) parametrem jest równoznaczna z dwoma przeciążonymi procedurami, jedną z opcjonalnym parametrem i bez niej.</span><span class="sxs-lookup"><span data-stu-id="f232c-139">A procedure with an [Optional](../../../language-reference/modifiers/optional.md) parameter is equivalent to two overloaded procedures, one with the optional parameter and one without it.</span></span> <span data-ttu-id="f232c-140">Nie można przeciążyć takiej procedury z listą parametrów odpowiadającą którejkolwiek z nich.</span><span class="sxs-lookup"><span data-stu-id="f232c-140">You cannot overload such a procedure with a parameter list corresponding to either of these.</span></span> <span data-ttu-id="f232c-141">Ilustruje to następujące deklaracje.</span><span class="sxs-lookup"><span data-stu-id="f232c-141">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#58)]  
  
 [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
 [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
 <span data-ttu-id="f232c-142">W przypadku procedury z więcej niż jednym opcjonalnym parametrem istnieje zestaw niejawnych przeciążeń, które zostały dostarczone przez logikę podobną do tego w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f232c-142">For a procedure with more than one optional parameter, there is a set of implicit overloads, arrived at by logic similar to that in the preceding example.</span></span>  
  
## <a name="implicit-overloads-for-a-paramarray-parameter"></a><span data-ttu-id="f232c-143">Niejawne przeciążenia dla parametru ParamArray</span><span class="sxs-lookup"><span data-stu-id="f232c-143">Implicit Overloads for a ParamArray Parameter</span></span>  
 <span data-ttu-id="f232c-144">Kompilator traktuje procedurę z parametrem [ParamArray](../../../language-reference/modifiers/paramarray.md) w celu uzyskania nieskończonej liczby przeciążeń, które różnią się od siebie w wyniku wywołania kodu do tablicy parametrów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f232c-144">The compiler considers a procedure with a [ParamArray](../../../language-reference/modifiers/paramarray.md) parameter to have an infinite number of overloads, differing from each other in what the calling code passes to the parameter array, as follows:</span></span>  
  
- <span data-ttu-id="f232c-145">Jedno Przeciążenie, gdy wywołujący kod nie dostarcza argumentu do`ParamArray`</span><span class="sxs-lookup"><span data-stu-id="f232c-145">One overload for when the calling code does not supply an argument to the `ParamArray`</span></span>  
  
- <span data-ttu-id="f232c-146">Jedno Przeciążenie, gdy wywołujący kod dostarcza tablicę jednowymiarową `ParamArray` typu elementu</span><span class="sxs-lookup"><span data-stu-id="f232c-146">One overload for when the calling code supplies a one-dimensional array of the `ParamArray` element type</span></span>  
  
- <span data-ttu-id="f232c-147">Dla każdej dodatniej liczby całkowitej jedno Przeciążenie, gdy wywołujący kod dostarcza tę liczbę argumentów, każdy `ParamArray` Typ elementu</span><span class="sxs-lookup"><span data-stu-id="f232c-147">For every positive integer, one overload for when the calling code supplies that number of arguments, each of the `ParamArray` element type</span></span>  
  
 <span data-ttu-id="f232c-148">Następujące deklaracje ilustrują te niejawne przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="f232c-148">The following declarations illustrate these implicit overloads.</span></span>  
  
 [!code-vb[VbVbcnProcedures#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#68)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="f232c-149">Nie można przeciążyć takiej procedury z listą parametrów, która przyjmuje jednowymiarową tablicę dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="f232c-149">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="f232c-150">Można jednak użyć podpisów innych niejawnych przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="f232c-150">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="f232c-151">Ilustruje to następujące deklaracje.</span><span class="sxs-lookup"><span data-stu-id="f232c-151">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
## <a name="typeless-programming-as-an-alternative-to-overloading"></a><span data-ttu-id="f232c-152">Programowanie beztypu jako alternatywa dla przeciążenia</span><span class="sxs-lookup"><span data-stu-id="f232c-152">Typeless Programming as an Alternative to Overloading</span></span>  
 <span data-ttu-id="f232c-153">Jeśli chcesz zezwolić, aby kod wywołujący przekaże różne typy danych do parametru, podejście alternatywne to programowanie bez typu.</span><span class="sxs-lookup"><span data-stu-id="f232c-153">If you want to allow the calling code to pass different data types to a parameter, an alternative approach is typeless programming.</span></span> <span data-ttu-id="f232c-154">Można ustawić przełącznik sprawdzania typu `Off` z opcją [Strict](../../../language-reference/statements/option-strict-statement.md) lub Option [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f232c-154">You can set the type checking switch to `Off` with either the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) or the [-optionstrict](../../../reference/command-line-compiler/optionstrict.md) compiler option.</span></span> <span data-ttu-id="f232c-155">Następnie nie trzeba deklarować typu danych parametru.</span><span class="sxs-lookup"><span data-stu-id="f232c-155">Then you do not have to declare the parameter's data type.</span></span> <span data-ttu-id="f232c-156">Jednak takie podejście ma następujące wady w porównaniu z przeciążeniem:</span><span class="sxs-lookup"><span data-stu-id="f232c-156">However, this approach has the following disadvantages compared to overloading:</span></span>  
  
- <span data-ttu-id="f232c-157">Programowanie bez typu generuje mniej wydajny kod wykonania.</span><span class="sxs-lookup"><span data-stu-id="f232c-157">Typeless programming produces less efficient execution code.</span></span>  
  
- <span data-ttu-id="f232c-158">Procedura musi testować dla każdego typu danych, który przewiduje przekazanie.</span><span class="sxs-lookup"><span data-stu-id="f232c-158">The procedure must test for every data type it anticipates being passed.</span></span>  
  
- <span data-ttu-id="f232c-159">Kompilator nie może sygnalizować błędu, Jeśli wywołujący kod przekaże typ danych, których procedura nie obsługuje.</span><span class="sxs-lookup"><span data-stu-id="f232c-159">The compiler cannot signal an error if the calling code passes a data type that the procedure does not support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f232c-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f232c-160">See also</span></span>

- [<span data-ttu-id="f232c-161">Procedury</span><span class="sxs-lookup"><span data-stu-id="f232c-161">Procedures</span></span>](./index.md)
- [<span data-ttu-id="f232c-162">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="f232c-162">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f232c-163">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="f232c-163">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="f232c-164">Instrukcje: definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="f232c-164">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="f232c-165">Instrukcje: wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="f232c-165">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="f232c-166">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="f232c-166">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="f232c-167">Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="f232c-167">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="f232c-168">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="f232c-168">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="f232c-169">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="f232c-169">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
