---
title: 'Porady: przeciążanie procedury wykorzystującej parametry opcjonalne'
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
ms.openlocfilehash: 9ae6818b1e03ccd00ed554e98690e02ffa45de99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387845"
---
# <a name="how-to-overload-a-procedure-that-takes-optional-parameters-visual-basic"></a><span data-ttu-id="7d3c5-102">Porady: przeciążanie procedury wykorzystującej parametry opcjonalne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d3c5-102">How to: Overload a Procedure that Takes Optional Parameters (Visual Basic)</span></span>
<span data-ttu-id="7d3c5-103">Jeśli procedura zawiera co najmniej jeden parametr [opcjonalny](../../../language-reference/modifiers/optional.md) , nie można zdefiniować przeciążonej wersji zgodnej z żadnym z jego niejawnego przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-103">If a procedure has one or more [Optional](../../../language-reference/modifiers/optional.md) parameters, you cannot define an overloaded version matching any of its implicit overloads.</span></span> <span data-ttu-id="7d3c5-104">Aby uzyskać więcej informacji, zobacz "niejawne przeciążenia dla parametrów opcjonalnych" w [kwestiach dotyczących przeciążania procedur](./considerations-in-overloading-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7d3c5-104">For more information, see "Implicit Overloads for Optional Parameters" in [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md).</span></span>  
  
## <a name="one-optional-parameter"></a><span data-ttu-id="7d3c5-105">Jeden opcjonalny parametr</span><span class="sxs-lookup"><span data-stu-id="7d3c5-105">One Optional Parameter</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-one-optional-parameter"></a><span data-ttu-id="7d3c5-106">Aby przeciążyć procedurę, która przyjmuje jeden parametr opcjonalny</span><span class="sxs-lookup"><span data-stu-id="7d3c5-106">To overload a procedure that takes one optional parameter</span></span>  
  
1. <span data-ttu-id="7d3c5-107">Napisz `Sub` instrukcję lub `Function` deklaracji, która zawiera opcjonalny parametr na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-107">Write a `Sub` or `Function` declaration statement that includes the optional parameter in the parameter list.</span></span> <span data-ttu-id="7d3c5-108">Nie należy używać `Optional` słowa kluczowego w tej przeciążonej wersji.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-108">Do not use the `Optional` keyword in this overloaded version.</span></span>  
  
2. <span data-ttu-id="7d3c5-109">Poprzedź `Sub` słowo kluczowe or `Function` za pomocą słowa kluczowego [overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="7d3c5-109">Precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
3. <span data-ttu-id="7d3c5-110">Napisz kod procedury, który powinien zostać wykonany, gdy wywoływany kod dostarcza opcjonalnego argumentu.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-110">Write the procedure code that should execute when the calling code supplies the optional argument.</span></span>  
  
4. <span data-ttu-id="7d3c5-111">Zakończ procedurę z `End Sub` `End Function` instrukcją lub, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-111">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
5. <span data-ttu-id="7d3c5-112">Napisz drugą instrukcję deklaracji, która jest identyczna z pierwszą deklaracją, z tą różnicą, że nie zawiera parametru opcjonalnego na liście parametrów.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-112">Write a second declaration statement that is identical to the first declaration except that it does not include the optional parameter in the parameter list.</span></span>  
  
6. <span data-ttu-id="7d3c5-113">Napisz kod procedury, który powinien zostać wykonany, gdy wywołujący kod nie poda opcjonalnego argumentu.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-113">Write the procedure code that should execute when the calling code does not supply the optional argument.</span></span> <span data-ttu-id="7d3c5-114">Zakończ procedurę z `End Sub` `End Function` instrukcją lub, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-114">Terminate the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
     <span data-ttu-id="7d3c5-115">Poniższy przykład pokazuje procedurę zdefiniowaną za pomocą opcjonalnego parametru, równoważnego zestawu dwóch przeciążonych procedur, a wreszcie przykłady zarówno dla nieprawidłowych, jak i prawidłowych wersji przeciążonych.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-115">The following example shows a procedure defined with an optional parameter,  an equivalent set of two overloaded procedures, and finally examples of both invalid and valid overloaded versions.</span></span>  
  
     [!code-vb[VbVbcnProcedures#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#59)]  
  
     [!code-vb[VbVbcnProcedures#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#60)]  
  
     [!code-vb[VbVbcnProcedures#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#61)]  
  
## <a name="multiple-optional-parameters"></a><span data-ttu-id="7d3c5-116">Wiele parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="7d3c5-116">Multiple Optional Parameters</span></span>  
 <span data-ttu-id="7d3c5-117">W przypadku procedury z więcej niż jednym opcjonalnym parametrem zwykle wymagane są więcej niż dwie przeciążone wersje.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-117">For a procedure with more than one optional parameter, you normally need more than two overloaded versions.</span></span> <span data-ttu-id="7d3c5-118">Na przykład jeśli istnieją dwa parametry opcjonalne, a kod wywołujący może dostarczyć lub pominąć każdy z nich niezależnie, potrzebne są cztery przeciążone wersje, jeden dla każdej możliwej kombinacji dostarczonych argumentów.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-118">For example, if there are two optional parameters, and the calling code can supply or omit each one independently of the other, you need four overloaded versions, one for each possible combination of supplied arguments.</span></span>  
  
 <span data-ttu-id="7d3c5-119">Wraz ze wzrostem liczby parametrów opcjonalnych zwiększa się złożoność przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-119">As the number of optional parameters increases, the complexity of the overloading increases.</span></span> <span data-ttu-id="7d3c5-120">Jeśli niektóre kombinacje podanych argumentów nie są akceptowalne, dla N opcjonalnych parametrów wymagane są 2 ^ N przeciążone wersje.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-120">Unless some combinations of supplied arguments are not acceptable, for N optional parameters you need 2 ^ N overloaded versions.</span></span> <span data-ttu-id="7d3c5-121">W zależności od charakteru procedury, może się okazać, że przejrzystość logiki usprawiedliwia dodatkowy nakład pracy w celu zdefiniowania wszystkich przeciążonych wersji.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-121">Depending on the nature of the procedure, you might find that the clarity of logic justifies the extra effort of defining all the overloaded versions.</span></span>  
  
#### <a name="to-overload-a-procedure-that-takes-more-than-one-optional-parameter"></a><span data-ttu-id="7d3c5-122">Aby przeciążyć procedurę, która przyjmuje więcej niż jeden parametr opcjonalny</span><span class="sxs-lookup"><span data-stu-id="7d3c5-122">To overload a procedure that takes more than one optional parameter</span></span>  
  
1. <span data-ttu-id="7d3c5-123">Ustal, które kombinacje podanych argumentów opcjonalnych są akceptowalne dla logiki procedury.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-123">Determine which combinations of supplied optional arguments are acceptable to the logic of the procedure.</span></span> <span data-ttu-id="7d3c5-124">Nieakceptowalna kombinacja może wystąpić, jeśli jeden opcjonalny parametr zależy od innego.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-124">An unacceptable combination might arise if one optional parameter depends on another.</span></span> <span data-ttu-id="7d3c5-125">Na przykład jeśli jeden parametr akceptuje nazwisko osoby i inny akceptuje wiek osoby, kombinację argumentów dostarczających wiek, ale pomijając nazwę, nie można jej zaakceptować.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-125">For example, if one parameter accepts a person's name and another accepts the person's age, a combination of arguments supplying the age but omitting the name is unacceptable.</span></span>  
  
2. <span data-ttu-id="7d3c5-126">Dla każdej akceptowalnej kombinacji podanych argumentów opcjonalnych Napisz `Sub` `Function` instrukcję lub deklarację, która definiuje odpowiednią listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-126">For each acceptable combination of supplied optional arguments, write a `Sub` or `Function` declaration statement that defines the corresponding parameter list.</span></span> <span data-ttu-id="7d3c5-127">Nie należy używać `Optional` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-127">Do not use the `Optional` keyword.</span></span>  
  
3. <span data-ttu-id="7d3c5-128">W każdej deklaracji poprzedź słowo kluczowe `Sub` or słowa `Function` kluczowego [overloads](../../../language-reference/modifiers/overloads.md) .</span><span class="sxs-lookup"><span data-stu-id="7d3c5-128">In each declaration, precede the `Sub` or `Function` keyword with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span>  
  
4. <span data-ttu-id="7d3c5-129">Po każdej deklaracji Napisz kod procedury, który powinien zostać wykonany, gdy wywołujący kod dostarcza listę argumentów odpowiadającą tej deklaracji listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-129">Following each declaration, write the procedure code that should execute when the calling code supplies an argument list corresponding to that declaration's parameter list.</span></span>  
  
5. <span data-ttu-id="7d3c5-130">Przerwij każdą procedurę za pomocą `End Sub` instrukcji lub w `End Function` zależności od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="7d3c5-130">Terminate each procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d3c5-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d3c5-131">See also</span></span>

- [<span data-ttu-id="7d3c5-132">Procedury</span><span class="sxs-lookup"><span data-stu-id="7d3c5-132">Procedures</span></span>](./index.md)
- [<span data-ttu-id="7d3c5-133">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="7d3c5-133">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7d3c5-134">Parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="7d3c5-134">Optional Parameters</span></span>](./optional-parameters.md)
- [<span data-ttu-id="7d3c5-135">Parameter — Tablice</span><span class="sxs-lookup"><span data-stu-id="7d3c5-135">Parameter Arrays</span></span>](./parameter-arrays.md)
- [<span data-ttu-id="7d3c5-136">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="7d3c5-136">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="7d3c5-137">Rozwiązywanie problemów z procedurami</span><span class="sxs-lookup"><span data-stu-id="7d3c5-137">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="7d3c5-138">Instrukcje: definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="7d3c5-138">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="7d3c5-139">Instrukcje: wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="7d3c5-139">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="7d3c5-140">Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="7d3c5-140">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="7d3c5-141">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="7d3c5-141">Overload Resolution</span></span>](./overload-resolution.md)
