---
title: 'Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], indefinite number of parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: c7042de2-2422-4039-94e8-ac298896af69
ms.openlocfilehash: 026dd59db135e8b195ae014aaff5e3a6a7846fc7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651495"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="0c042-102">Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c042-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="0c042-103">Jeśli procedura ma [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, nie można zdefiniować przeciążonego wersji biorąc tablicą jednowymiarową dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="0c042-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="0c042-104">Aby uzyskać więcej informacji, zobacz "Niejawne Overloads dla parametru ParamArray" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0c042-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="0c042-105">Aby przeciążanie procedury wykorzystującej zmienną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="0c042-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="0c042-106">Upewnić się, że procedura i wywoływania kodu logiki korzyści z przeciążone wersje więcej niż `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="0c042-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="0c042-107">Zobacz "Przeciążenia i ParamArrays" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0c042-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="0c042-108">Ustal, które numery podane wartości procedura powinna obsługiwać w części zmiennej listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="0c042-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="0c042-109">Może to być case o wartości i może zawierać przypadku tablicą jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="0c042-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="0c042-110">Dla każdego dopuszczalne liczba podanych wartości zapisu `Sub` lub `Function` instrukcji deklaracji, który definiuje na odpowiedniej liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="0c042-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="0c042-111">Nie używaj albo `Optional` lub `ParamArray` — słowo kluczowe w tej wersji przeciążona.</span><span class="sxs-lookup"><span data-stu-id="0c042-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="0c042-112">W każdej deklaracji poprzedzać `Sub` lub `Function` — słowo kluczowe z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="0c042-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="0c042-113">Po każdej deklaracji pisania kodu procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza wartości odpowiadających listy parametrów tej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="0c042-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="0c042-114">Zakończenie każdej procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="0c042-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c042-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0c042-115">Example</span></span>  
 <span data-ttu-id="0c042-116">W poniższym przykładzie przedstawiono procedurę zdefiniowane z [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametr, a następnie równoważne zbiór procedury przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="0c042-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#70](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_2.vb)]  
  
 <span data-ttu-id="0c042-117">Nie można przeciążyć procedury z listą parametrów pobierającej tablicą jednowymiarową dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="0c042-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="0c042-118">Można jednak użyć podpisy niejawne przeładowania.</span><span class="sxs-lookup"><span data-stu-id="0c042-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="0c042-119">Następujące deklaracje ilustrację.</span><span class="sxs-lookup"><span data-stu-id="0c042-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters_3.vb)]  
  
 <span data-ttu-id="0c042-120">Kod w wersjach przeciążone nie ma do sprawdzenia, czy kod wywołujący dostarczonych wartości co najmniej jeden `ParamArray` parametr, lub jeśli tak, jak wiele.</span><span class="sxs-lookup"><span data-stu-id="0c042-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="0c042-121">Visual Basic przejmuje kontrolę wersji pasujących do wywoływania listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="0c042-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0c042-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0c042-122">Compiling the Code</span></span>  
 <span data-ttu-id="0c042-123">Ponieważ procedura o `ParamArray` parametru jest odpowiednikiem zestaw zastąpionej wersji, nie mogą przeciążać takiej procedury z listą parametrów odpowiadający żadnego z tych niejawne przeładowania.</span><span class="sxs-lookup"><span data-stu-id="0c042-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="0c042-124">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0c042-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="0c042-125">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="0c042-125">.NET Framework Security</span></span>  
 <span data-ttu-id="0c042-126">Zawsze, gdy praca z tablicy, która może być duży czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrzny wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c042-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="0c042-127">Akceptujesz tablicy parametrów, należy przetestować długości tablicy przekazywania kod wywołujący i podejmij odpowiednie kroki, jeśli jest ona za duża dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c042-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c042-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0c042-128">See Also</span></span>  
 [<span data-ttu-id="0c042-129">Procedury</span><span class="sxs-lookup"><span data-stu-id="0c042-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="0c042-130">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="0c042-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="0c042-131">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="0c042-131">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="0c042-132">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="0c042-132">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="0c042-133">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="0c042-133">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="0c042-134">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="0c042-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="0c042-135">Instrukcje: definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="0c042-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="0c042-136">Instrukcje: wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="0c042-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="0c042-137">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="0c042-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="0c042-138">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="0c042-138">Overload Resolution</span></span>](./overload-resolution.md)
