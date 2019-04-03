---
title: 'Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)'
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
ms.openlocfilehash: bae420e88a74fbe3f7e8ad3592133fdcaf191029
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839000"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="7687a-102">Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7687a-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="7687a-103">Jeśli procedura ma [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru nie można zdefiniować przeciążoną wersją, biorąc Jednowymiarowa tablica dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="7687a-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="7687a-104">Aby uzyskać więcej informacji, zobacz "Niejawne przeciążenia dla parametru ParamArray" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7687a-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="7687a-105">Aby przeciążanie procedury, która przyjmuje zmienną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="7687a-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1.  <span data-ttu-id="7687a-106">Upewnić się, że procedury i wywoływać metodę kod logiki korzyści z przeciążone wersje ponad `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="7687a-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="7687a-107">Zobacz "Przeciążenia i ParamArrays" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7687a-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2.  <span data-ttu-id="7687a-108">Ustal, które numery podane wartości procedura powinna obsługiwać w części zmiennej listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="7687a-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="7687a-109">Może to obejmować przypadku żadnej wartości i może zawierać przypadku pojedynczą tablicę jednowymiarową.</span><span class="sxs-lookup"><span data-stu-id="7687a-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3.  <span data-ttu-id="7687a-110">Dla każdego dopuszczalna liczba podanych wartości zapisu `Sub` lub `Function` instrukcji deklaracji, która definiuje odpowiednie listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="7687a-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="7687a-111">Nie używaj albo `Optional` lub `ParamArray` — słowo kluczowe w tej wersji przeciążona.</span><span class="sxs-lookup"><span data-stu-id="7687a-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4.  <span data-ttu-id="7687a-112">W każdym zgłoszeniu, należy poprzedzić `Sub` lub `Function` — słowo kluczowe z [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="7687a-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5.  <span data-ttu-id="7687a-113">Po każdym zgłoszeniu należy napisać kod procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza wartości odpowiadające liście parametrów tej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="7687a-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6.  <span data-ttu-id="7687a-114">Zakończenie każdej procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="7687a-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7687a-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="7687a-115">Example</span></span>  
 <span data-ttu-id="7687a-116">W poniższym przykładzie pokazano zdefiniowane za pomocą procedury [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parametru, a następnie zbiór równoważny, procedur przeciążona.</span><span class="sxs-lookup"><span data-stu-id="7687a-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="7687a-117">Nie można przeciążyć procedury z listą parametrów, który przyjmuje tablicę jednowymiarową dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="7687a-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="7687a-118">Można jednak użyć podpisy niejawne przeładowania.</span><span class="sxs-lookup"><span data-stu-id="7687a-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="7687a-119">Następujące deklaracje pokazują to.</span><span class="sxs-lookup"><span data-stu-id="7687a-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="7687a-120">Kod w przeciążone wersje nie trzeba sprawdzić, czy kod wywołujący podano jeden lub więcej wartości dla `ParamArray` parametr, lub jeśli tak, jak wiele.</span><span class="sxs-lookup"><span data-stu-id="7687a-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="7687a-121">Visual Basic przekazuje sterowanie do wersji pasujących do wywoływania listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="7687a-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7687a-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7687a-122">Compiling the Code</span></span>  
 <span data-ttu-id="7687a-123">Ponieważ procedury z `ParamArray` parametr jest równoważny z zestawem przeciążone wersje, nie mogą przeciążać takiej procedury z dowolnego z tych niejawne przeładowania odpowiadający listą parametrów.</span><span class="sxs-lookup"><span data-stu-id="7687a-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="7687a-124">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7687a-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7687a-125">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7687a-125">.NET Framework Security</span></span>  
 <span data-ttu-id="7687a-126">Zawsze, gdy użytkownik poradzić sobie z tablicy, które mogą być duże przez czas nieokreślony, istnieje ryzyko przekroczenia niektórych wewnętrznych wydajności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7687a-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="7687a-127">Jeśli akceptujesz tablicy parametrów, należy sprawdzić długość tablicy przekazany kod wywołujący i podejmie stosowne działania, jeśli jest zbyt duży dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7687a-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7687a-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7687a-128">See also</span></span>

- [<span data-ttu-id="7687a-129">Procedury</span><span class="sxs-lookup"><span data-stu-id="7687a-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7687a-130">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="7687a-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7687a-131">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="7687a-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="7687a-132">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="7687a-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="7687a-133">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="7687a-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="7687a-134">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="7687a-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="7687a-135">Instrukcje: Definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="7687a-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="7687a-136">Instrukcje: Wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="7687a-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="7687a-137">Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="7687a-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="7687a-138">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="7687a-138">Overload Resolution</span></span>](./overload-resolution.md)
