---
title: 'Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów'
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
ms.openlocfilehash: 94f12b4cc6cb35864fefbb3b5bb1378bec5e974c
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347566"
---
# <a name="how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters-visual-basic"></a><span data-ttu-id="45faf-102">Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45faf-102">How to: Overload a Procedure that Takes an Indefinite Number of Parameters (Visual Basic)</span></span>
<span data-ttu-id="45faf-103">Jeśli procedura zawiera parametr [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , nie można zdefiniować przeciążonej wersji pobierającej tablicę jednowymiarową dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="45faf-103">If a procedure has a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, you cannot define an overloaded version taking a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="45faf-104">Aby uzyskać więcej informacji, zobacz "niejawne przeciążenia dla parametru ParamArray" w artykule dotyczącym [przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="45faf-104">For more information, see "Implicit Overloads for a ParamArray Parameter" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
### <a name="to-overload-a-procedure-that-takes-a-variable-number-of-parameters"></a><span data-ttu-id="45faf-105">Aby przeciążyć procedurę, która przyjmuje zmienną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="45faf-105">To overload a procedure that takes a variable number of parameters</span></span>  
  
1. <span data-ttu-id="45faf-106">Należy upewnić się, że procedura i wywoływanie logiki kodu z przeciążonych wersji nie przekracza z `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="45faf-106">Ascertain that the procedure and calling code logic benefits from overloaded versions more than from a `ParamArray` parameter.</span></span> <span data-ttu-id="45faf-107">Zobacz sekcję "overloads and ParamArrays" w artykule dotyczącym [przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="45faf-107">See "Overloads and ParamArrays" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
2. <span data-ttu-id="45faf-108">Określ, które liczby podanych wartości mają być akceptowane przez procedurę w zmiennej części listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="45faf-108">Determine which numbers of supplied values the procedure should accept in the variable part of the parameter list.</span></span> <span data-ttu-id="45faf-109">Może to obejmować przypadek braku wartości i może uwzględniać wielkość liter pojedynczej tablicy jednowymiarowej.</span><span class="sxs-lookup"><span data-stu-id="45faf-109">This might include the case of no value, and it might include the case of a single one-dimensional array.</span></span>  
  
3. <span data-ttu-id="45faf-110">Dla każdej akceptowalnej liczby podanych wartości Napisz `Sub` lub instrukcję deklaracji `Function`, która definiuje odpowiednią listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="45faf-110">For each acceptable number of supplied values, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="45faf-111">Nie należy używać słowa kluczowego `Optional` ani `ParamArray` w tej przeciążonej wersji.</span><span class="sxs-lookup"><span data-stu-id="45faf-111">Do not use either the `Optional` or the `ParamArray` keyword in this overloaded version.</span></span>  
  
4. <span data-ttu-id="45faf-112">W każdej deklaracji poprzedź słowo kluczowe `Sub` lub `Function` za pomocą słowa kluczowego [overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="45faf-112">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
5. <span data-ttu-id="45faf-113">Po każdej deklaracji Napisz kod procedury, który powinien zostać wykonany, gdy wywoływany kod zawiera wartości odpowiadające tej deklaracji listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="45faf-113">Following each declaration, write the procedure code that should execute when the calling code supplies values corresponding to that declaration's parameter list.</span></span>  
  
6. <span data-ttu-id="45faf-114">W razie potrzeby Zakończ każdą procedurę z instrukcją `End Sub` lub `End Function`.</span><span class="sxs-lookup"><span data-stu-id="45faf-114">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45faf-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="45faf-115">Example</span></span>  
 <span data-ttu-id="45faf-116">Poniższy przykład pokazuje procedurę zdefiniowaną za pomocą parametru [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) , a następnie równoważnego zestawu przeciążonych procedur.</span><span class="sxs-lookup"><span data-stu-id="45faf-116">The following example shows a procedure defined with a [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md) parameter, and then an equivalent set of overloaded procedures.</span></span>  
  
 [!code-vb[VbVbcnProcedures#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#69)]  
  
 [!code-vb[VbVbcnProcedures#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#70)]  
  
 <span data-ttu-id="45faf-117">Nie można przeciążyć takiej procedury z listą parametrów, która przyjmuje jednowymiarową tablicę dla tablicy parametrów.</span><span class="sxs-lookup"><span data-stu-id="45faf-117">You cannot overload such a procedure with a parameter list that takes a one-dimensional array for the parameter array.</span></span> <span data-ttu-id="45faf-118">Można jednak użyć podpisów innych niejawnych przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="45faf-118">However, you can use the signatures of the other implicit overloads.</span></span> <span data-ttu-id="45faf-119">Ilustruje to następujące deklaracje.</span><span class="sxs-lookup"><span data-stu-id="45faf-119">The following declarations illustrate this.</span></span>  
  
 [!code-vb[VbVbcnProcedures#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#71)]  
  
 <span data-ttu-id="45faf-120">Kod w przeciążonych wersjach nie musi testować, czy kod wywołujący dostarczył jedną lub więcej wartości dla parametru `ParamArray`, czy tak, ile.</span><span class="sxs-lookup"><span data-stu-id="45faf-120">The code in the overloaded versions does not have to test whether the calling code supplied one or more values for the `ParamArray` parameter, or if so, how many.</span></span> <span data-ttu-id="45faf-121">Visual Basic przekazuje kontrolę do wersji zgodnej z listą argumentów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="45faf-121">Visual Basic passes control to the version matching the calling argument list.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="45faf-122">Skompilować kod</span><span class="sxs-lookup"><span data-stu-id="45faf-122">Compile the code</span></span>  
 <span data-ttu-id="45faf-123">Ponieważ procedura z parametrem `ParamArray` jest równoważna z zestawem przeciążonych wersji, nie można przeciążyć takiej procedury z listą parametrów odpowiadającą każdemu z tych niejawnych przeciążeń.</span><span class="sxs-lookup"><span data-stu-id="45faf-123">Because a procedure with a `ParamArray` parameter is equivalent to a set of overloaded versions, you cannot overload such a procedure with a parameter list corresponding to any of these implicit overloads.</span></span> <span data-ttu-id="45faf-124">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="45faf-124">For more information, see [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="45faf-125">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="45faf-125">.NET Framework Security</span></span>  
 <span data-ttu-id="45faf-126">Za każdym razem, gdy zajmujesz się tablicą, która może być nienieskończona, istnieje ryzyko, że zachodzi taka Wewnętrzna pojemność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45faf-126">Whenever you deal with an array which can be indefinitely large, there is a risk of overrunning some internal capacity of your application.</span></span> <span data-ttu-id="45faf-127">Jeśli zaakceptujesz tablicę parametrów, należy sprawdzić długość tablicy, do której przeszedł kod wywołujący, i wykonać odpowiednie czynności, jeśli jest zbyt duży dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="45faf-127">If you accept a parameter array, you should test for the length of the array the calling code passed to it, and take appropriate steps if it is too large for your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45faf-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45faf-128">See also</span></span>

- [<span data-ttu-id="45faf-129">Procedury</span><span class="sxs-lookup"><span data-stu-id="45faf-129">Procedures</span></span>](./index.md)
- [<span data-ttu-id="45faf-130">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="45faf-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="45faf-131">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="45faf-131">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="45faf-132">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="45faf-132">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="45faf-133">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="45faf-133">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="45faf-134">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="45faf-134">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="45faf-135">Instrukcje: definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="45faf-135">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="45faf-136">Instrukcje: wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="45faf-136">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="45faf-137">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="45faf-137">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="45faf-138">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="45faf-138">Overload Resolution</span></span>](./overload-resolution.md)
