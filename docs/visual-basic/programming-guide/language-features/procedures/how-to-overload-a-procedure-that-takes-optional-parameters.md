---
title: 'Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
ms.openlocfilehash: 58c52a7d73efbd96d772dd85d6bf2c9084fb1241
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320234"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="407ff-102">Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="407ff-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="407ff-103">Jeśli procedura ma co najmniej jeden [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametrów, nie można zdefiniować przeciążoną wersją, dowolny z jej przeciążeń niejawne dopasowania.</span><span class="sxs-lookup"><span data-stu-id="407ff-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="407ff-104">Aby uzyskać więcej informacji, zobacz "Niejawne przeciążenia dla opcjonalne parametry" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="407ff-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="407ff-105">Jeden parametr opcjonalny</span><span class="sxs-lookup"><span data-stu-id="407ff-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="407ff-106">Aby przeciążanie procedury, która przyjmuje jeden parametr opcjonalny</span><span class="sxs-lookup"><span data-stu-id="407ff-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="407ff-107">Zapis `Sub` lub `Function` instrukcji deklaracji, która zawiera parametr opcjonalny na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="407ff-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="407ff-108">Nie używaj `Optional` — słowo kluczowe w tej wersji przeciążona.</span><span class="sxs-lookup"><span data-stu-id="407ff-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="407ff-109">Należy poprzedzić `Sub` lub `Function` — słowo kluczowe z [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="407ff-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="407ff-110">Napisz kod procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="407ff-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="407ff-111">Zakończenie procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="407ff-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="407ff-112">Napisz drugiej instrukcji deklaracji, która jest taka sama jak pierwszej deklaracji, z tą różnicą, że nie ma opcjonalnego parametru na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="407ff-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="407ff-113">Napisz kod procedury, który powinien zostać wykonany, gdy kod wywołujący nie dostarcza opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="407ff-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="407ff-114">Zakończenie procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="407ff-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="407ff-115">Poniższy przykład pokazuje zdefiniowane z opcjonalnym parametrem, równoważne zbiór dwie procedury przeciążone, a na końcu przykłady nieprawidłowych i prawidłowe przeciążone wersje procedury.</span><span class="sxs-lookup"><span data-stu-id="407ff-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="407ff-116">Wiele parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="407ff-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="407ff-117">Procedury z więcej niż jeden parametr opcjonalny zwykle wymaga więcej niż dwie przeciążone wersje.</span><span class="sxs-lookup"><span data-stu-id="407ff-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="407ff-118">Na przykład jeśli istnieją dwa parametry opcjonalne, a kod wywołujący może dostarczyć lub Pomiń każdej z nich niezależnie od innych, należy cztery przeciążone wersje: jeden dla każdej możliwej kombinacji podanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="407ff-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="407ff-119">W miarę zwiększania liczby parametrów opcjonalnych zwiększa złożonością przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="407ff-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="407ff-120">Chyba że niektóre kombinacje przekazanych argumentów nie są dozwolone, następujące parametry opcjonalne N na potrzeby należy 2 ^ N przeciążone wersje.</span><span class="sxs-lookup"><span data-stu-id="407ff-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="407ff-121">W zależności od charakteru procedura może się okazać, że w celu uściślenia logiki uzasadnia dodatkowego wysiłku definiowania przeciążone wersje.</span><span class="sxs-lookup"><span data-stu-id="407ff-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="407ff-122">Aby przeciążanie procedury wykorzystującej więcej niż jeden parametr opcjonalny</span><span class="sxs-lookup"><span data-stu-id="407ff-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="407ff-123">Ustal, kombinacje podane argumenty opcjonalne są akceptowane przez logikę procedury.</span><span class="sxs-lookup"><span data-stu-id="407ff-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="407ff-124">Można zaakceptować połączenie może wystąpić, jeśli jeden parametr opcjonalny jest zależny od innego.</span><span class="sxs-lookup"><span data-stu-id="407ff-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="407ff-125">Na przykład jeden parametr akceptuje współmałżonka nazwę i inny akceptuje współmałżonka wiek, kombinacja argumentów, podając wiek, ale pomijając nazwę jest nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="407ff-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="407ff-126">Dla każdej kombinacji dopuszczalne podanych argumentów opcjonalnych zapisu `Sub` lub `Function` instrukcji deklaracji, która definiuje odpowiednie listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="407ff-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="407ff-127">Nie używaj `Optional` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="407ff-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="407ff-128">W każdym zgłoszeniu, należy poprzedzić `Sub` lub `Function` — słowo kluczowe z [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="407ff-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="407ff-129">Po każdym zgłoszeniu należy napisać kod procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza listy argumentów odpowiadający tej deklaracji listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="407ff-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="407ff-130">Zakończenie każdej procedury z `End Sub` lub `End Function` instrukcji zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="407ff-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407ff-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="407ff-131">See also</span></span>

- [<span data-ttu-id="407ff-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="407ff-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="407ff-133">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="407ff-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="407ff-134">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="407ff-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="407ff-135">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="407ff-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="407ff-136">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="407ff-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="407ff-137">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="407ff-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="407ff-138">Instrukcje: Definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="407ff-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="407ff-139">Instrukcje: Wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="407ff-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="407ff-140">Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="407ff-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="407ff-141">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="407ff-141">Overload Resolution</span></span>](./overload-resolution.md)
