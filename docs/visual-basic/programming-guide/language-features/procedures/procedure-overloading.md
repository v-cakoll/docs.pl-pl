---
title: Przeciążanie procedury (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 4d90b81049197fbbf4a767b17399d3e9c80be0f7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975475"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="242d2-102">Przeciążanie procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="242d2-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="242d2-103">*Przeciążanie* procedury oznacza zdefiniowaniem go w wielu wersjach, przy użyciu takiej samej nazwie, ale listy różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="242d2-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="242d2-104">Przeciążanie ma na celu zdefiniować kilka wersji ściśle powiązanych procedury bez konieczności odróżnić je według nazwy.</span><span class="sxs-lookup"><span data-stu-id="242d2-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="242d2-105">Można to zrobić przez zróżnicowanie listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="242d2-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="242d2-106">Przeciążanie reguły</span><span class="sxs-lookup"><span data-stu-id="242d2-106">Overloading Rules</span></span>  
 <span data-ttu-id="242d2-107">Po użytkownik przeciążanie procedury, obowiązują następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="242d2-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="242d2-108">**Tej samej nazwie**.</span><span class="sxs-lookup"><span data-stu-id="242d2-108">**Same Name**.</span></span> <span data-ttu-id="242d2-109">Każda przeciążona wersja należy użyć tej samej nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="242d2-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="242d2-110">**Inny podpis**.</span><span class="sxs-lookup"><span data-stu-id="242d2-110">**Different Signature**.</span></span> <span data-ttu-id="242d2-111">Każda wersja przeciążona muszą różnić się od wszystkich innych przeciążone wersje w co najmniej jeden z następujących aspektach:</span><span class="sxs-lookup"><span data-stu-id="242d2-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="242d2-112">Liczba parametrów</span><span class="sxs-lookup"><span data-stu-id="242d2-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="242d2-113">Kolejność parametrów</span><span class="sxs-lookup"><span data-stu-id="242d2-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="242d2-114">Typy danych parametrów</span><span class="sxs-lookup"><span data-stu-id="242d2-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="242d2-115">Liczba parametrów typu (w przypadku ogólnych procedura)</span><span class="sxs-lookup"><span data-stu-id="242d2-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="242d2-116">Zwracany typ (tylko dla operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="242d2-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="242d2-117">Wraz z nazwą procedury poprzednie elementy są nazywane *podpisu* procedury.</span><span class="sxs-lookup"><span data-stu-id="242d2-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="242d2-118">Po wywołaniu procedury przeciążenia, kompilator używa sygnatury do sprawdzenia, czy wywołanie odpowiada poprawnie definicji.</span><span class="sxs-lookup"><span data-stu-id="242d2-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="242d2-119">**Elementy nie jest częścią podpisu**.</span><span class="sxs-lookup"><span data-stu-id="242d2-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="242d2-120">Procedury nie mogą przeciążać bez zróżnicowanie podpis.</span><span class="sxs-lookup"><span data-stu-id="242d2-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="242d2-121">W szczególności nie mogą przeciążać procedury przez zróżnicowanie tylko jeden lub więcej z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="242d2-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="242d2-122">Słowa kluczowe modyfikator procedury, takich jak `Public`, `Shared`, i `Static`</span><span class="sxs-lookup"><span data-stu-id="242d2-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="242d2-123">Parametr lub typ nazwy parametrów</span><span class="sxs-lookup"><span data-stu-id="242d2-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="242d2-124">Ograniczenia parametru typu (w przypadku ogólnych procedura)</span><span class="sxs-lookup"><span data-stu-id="242d2-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="242d2-125">Słowa kluczowe modyfikator parametrów, takich jak `ByRef` i `Optional`</span><span class="sxs-lookup"><span data-stu-id="242d2-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="242d2-126">Czy wartość jest zwracana</span><span class="sxs-lookup"><span data-stu-id="242d2-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="242d2-127">Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="242d2-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="242d2-128">Elementy na powyższej liście nie są częścią podpis.</span><span class="sxs-lookup"><span data-stu-id="242d2-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="242d2-129">Mimo że nie można ich użyć do rozróżnienia między przeciążone wersje, można je różnią przeciążone wersje, które są właściwie zróżnicowane według ich podpisy.</span><span class="sxs-lookup"><span data-stu-id="242d2-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="242d2-130">**Z późnym wiązaniem argumenty**.</span><span class="sxs-lookup"><span data-stu-id="242d2-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="242d2-131">Jeśli zamierzasz przekazać późno zmiennej powiązany obiekt do przeciążoną wersją, należy zadeklarować odpowiedni parametr jako <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="242d2-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="242d2-132">Wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="242d2-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="242d2-133">Załóżmy, że piszesz `Sub` procedury, aby transakcję przed saldo odbiorcy, a ma być dostępna do odwoływania się do klienta, według nazwy lub numer konta.</span><span class="sxs-lookup"><span data-stu-id="242d2-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="242d2-134">Aby to umożliwić, należy zdefiniować dwa różne `Sub` procedury jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="242d2-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="242d2-135">Przeciążone wersje</span><span class="sxs-lookup"><span data-stu-id="242d2-135">Overloaded Versions</span></span>  
 <span data-ttu-id="242d2-136">Alternatywą jest nazwa jednej procedury przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="242d2-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="242d2-137">Możesz użyć [przeciążenia](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe, aby zdefiniować wersję procedurę dla każdej listy parametrów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="242d2-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="242d2-138">Dodatkowe przeciążenia</span><span class="sxs-lookup"><span data-stu-id="242d2-138">Additional Overloads</span></span>  
 <span data-ttu-id="242d2-139">Jeśli chcesz również zaakceptować ilości transakcji, albo `Decimal` lub `Single`, można dodatkowo przeciążenia `post` umożliwia dla tej odmiany.</span><span class="sxs-lookup"><span data-stu-id="242d2-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="242d2-140">Jeśli tak, to nie do poszczególnych przeciążeń w poprzednim przykładzie należałoby cztery `Sub` procedury, wszystkie o takiej samej nazwie, ale z czterech różnych podpisów.</span><span class="sxs-lookup"><span data-stu-id="242d2-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="242d2-141">Korzyści wynikające z przeciążenia</span><span class="sxs-lookup"><span data-stu-id="242d2-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="242d2-142">Zaletą przeciążanie procedury trwa elastyczność wywołania.</span><span class="sxs-lookup"><span data-stu-id="242d2-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="242d2-143">Do użycia `post` procedury zadeklarowane w poprzednim przykładzie, kod wywołujący można uzyskać identyfikator klienta jako `String` lub `Integer`, a następnie wywołać tę samą procedurę w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="242d2-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="242d2-144">Ilustruje to poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="242d2-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="242d2-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="242d2-145">See also</span></span>
- [<span data-ttu-id="242d2-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="242d2-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="242d2-147">Instrukcje: Definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="242d2-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="242d2-148">Instrukcje: Wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="242d2-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="242d2-149">Instrukcje: Przeciążanie procedury wykorzystującej parametry opcjonalne</span><span class="sxs-lookup"><span data-stu-id="242d2-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="242d2-150">Instrukcje: Przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="242d2-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="242d2-151">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="242d2-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="242d2-152">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="242d2-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="242d2-153">Overloads</span><span class="sxs-lookup"><span data-stu-id="242d2-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [<span data-ttu-id="242d2-154">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="242d2-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
