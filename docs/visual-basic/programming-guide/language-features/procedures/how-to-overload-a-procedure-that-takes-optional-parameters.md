---
title: "Porady: przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], parameters
- procedure overloading [Visual Basic], optional parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
ms.assetid: 825f9d56-4cde-43fd-993a-b9171717e2eb
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4a863944d4f9ab265aab52578fbb704ca376de5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="629c9-102">Porady: przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="629c9-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="629c9-103">Jeśli procedura ma co najmniej jeden [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) parametrów, nie można zdefiniować przeciążonego wersji zgodne z żadnym z jego niejawne przeładowania.</span><span class="sxs-lookup"><span data-stu-id="629c9-103">If a procedure has one or more [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="629c9-104">Aby uzyskać więcej informacji, zobacz "Niejawne Overloads dla parametrów" w [zagadnienia dotyczące przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="629c9-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="629c9-105">Jeden opcjonalny parametr</span><span class="sxs-lookup"><span data-stu-id="629c9-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="629c9-106">Do procedury, która przyjmuje jeden parametr opcjonalny przeciążenia</span><span class="sxs-lookup"><span data-stu-id="629c9-106">To overload a procedure that takes one optional parameter</span></span>  
  
1.  <span data-ttu-id="629c9-107">Zapis `Sub` lub `Function` instrukcji deklaracji, która zawiera parametr opcjonalny na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="629c9-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="629c9-108">Nie używaj `Optional` — słowo kluczowe w tej wersji przeciążona.</span><span class="sxs-lookup"><span data-stu-id="629c9-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2.  <span data-ttu-id="629c9-109">Należy poprzedzić `Sub` lub `Function` — słowo kluczowe z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="629c9-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3.  <span data-ttu-id="629c9-110">Pisanie kodu procedury, który powinien zostać wykonany, gdy kod wywołujący dostarcza opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="629c9-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4.  <span data-ttu-id="629c9-111">Zakończenie procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="629c9-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5.  <span data-ttu-id="629c9-112">Zapis drugi instrukcji deklaracji, która jest taka sama jak pierwszej deklaracji z tą różnicą, że nie ma parametr opcjonalny na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="629c9-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6.  <span data-ttu-id="629c9-113">Pisanie kodu procedury, który powinien zostać wykonany, gdy kod wywołujący nie dostarcza opcjonalny argument.</span><span class="sxs-lookup"><span data-stu-id="629c9-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="629c9-114">Zakończenie procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="629c9-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="629c9-115">W poniższym przykładzie przedstawiono procedurę zdefiniowane za pomocą opcjonalnego parametru równoważne zbiór dwie procedury przeciążenia, a na końcu przykłady zarówno nieprawidłowy prawidłowy zastąpionej wersji i.</span><span class="sxs-lookup"><span data-stu-id="629c9-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_1.vb)]  
  
     [!code-vb[VbVbcnProcedures#60](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_2.vb)]  
  
     [!code-vb[VbVbcnProcedures#61](./codesnippet/VisualBasic/how-to-overload-a-procedure-that-takes-optional-parameters_3.vb)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="629c9-116">Wiele następujące parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="629c9-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="629c9-117">Procedury z więcej niż jeden parametr opcjonalny potrzebne są zwykle więcej niż dwie wersje przeciążona.</span><span class="sxs-lookup"><span data-stu-id="629c9-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="629c9-118">Na przykład jeśli istnieją dwie opcjonalne parametry i kod wywołujący może dostarczyć lub Pomiń nich niezależnie od innych, należy cztery przeciążone wersji narzędzia, dla każdej możliwej kombinacji podanych argumentów.</span><span class="sxs-lookup"><span data-stu-id="629c9-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="629c9-119">Jak zwiększa liczbę następujące parametry opcjonalne, zwiększa złożoności logowania.</span><span class="sxs-lookup"><span data-stu-id="629c9-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="629c9-120">Chyba, że niektóre kombinacje podanych argumentów nie są dozwolone, N następujące parametry opcjonalne mają być 2 ^ N przeciążony wersji.</span><span class="sxs-lookup"><span data-stu-id="629c9-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="629c9-121">W zależności od charakteru procedura może się okazać, że jasności logiki uzasadnia dodatkowy wysiłek zdefiniowania zastąpionej wersji.</span><span class="sxs-lookup"><span data-stu-id="629c9-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="629c9-122">Aby przeciążanie procedury wykorzystującej więcej niż jeden parametr opcjonalny</span><span class="sxs-lookup"><span data-stu-id="629c9-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1.  <span data-ttu-id="629c9-123">Określ kombinacje podane argumenty opcjonalne są akceptowane przez logikę procedury.</span><span class="sxs-lookup"><span data-stu-id="629c9-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="629c9-124">Kombinację niedopuszczalne mogą wystąpić, jeśli jeden parametr opcjonalny jest zależna od innej.</span><span class="sxs-lookup"><span data-stu-id="629c9-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="629c9-125">Na przykład jeden parametr akceptuje współmałżonka nazwę i inny akceptuje współmałżonka wieku, kombinacja argumentów dostarczanie wiek, ale bez określenia nazwy jest nie do przyjęcia.</span><span class="sxs-lookup"><span data-stu-id="629c9-125">For example, if one parameter accepts a spouse's name and another accepts the spouse's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2.  <span data-ttu-id="629c9-126">Dla każdej kombinacji dopuszczalne podanych argumentów opcjonalnych zapisu `Sub` lub `Function` instrukcji deklaracji, który definiuje na odpowiedniej liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="629c9-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="629c9-127">Nie używaj `Optional` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="629c9-127">Do not use the `Optional` keyword.</span></span>  
  
3.  <span data-ttu-id="629c9-128">W każdej deklaracji poprzedzać `Sub` lub `Function` — słowo kluczowe z [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="629c9-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4.  <span data-ttu-id="629c9-129">Po każdej deklaracji pisania kodu procedury, który powinien zostać wykonany po kod wywołujący dostarcza odpowiadającego tej deklaracji listy parametrów listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="629c9-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5.  <span data-ttu-id="629c9-130">Zakończenie każdej procedury z `End Sub` lub `End Function` oświadczenie zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="629c9-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="629c9-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="629c9-131">See Also</span></span>  
 [<span data-ttu-id="629c9-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="629c9-132">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="629c9-133">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="629c9-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="629c9-134">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="629c9-134">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="629c9-135">Tablice parametrów</span><span class="sxs-lookup"><span data-stu-id="629c9-135">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="629c9-136">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="629c9-136">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="629c9-137">Procedury rozwiązywania problemów</span><span class="sxs-lookup"><span data-stu-id="629c9-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)  
 [<span data-ttu-id="629c9-138">Porady: Definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="629c9-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="629c9-139">Porady: wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="629c9-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="629c9-140">Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="629c9-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="629c9-141">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="629c9-141">Overload Resolution</span></span>](./overload-resolution.md)
