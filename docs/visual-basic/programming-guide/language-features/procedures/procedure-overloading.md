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
ms.openlocfilehash: 0d1f2c4d8c88922659b3d91ed41d5e760e6e5233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653917"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="758a1-102">Przeciążanie procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="758a1-102">Procedure Overloading (Visual Basic)</span></span>
<span data-ttu-id="758a1-103">*Przeciążanie* procedury oznacza Definiowanie wielu wersji przy użyciu tej samej nazwie, ale listy różnych parametrów.</span><span class="sxs-lookup"><span data-stu-id="758a1-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="758a1-104">Przeciążanie służy do definiowania kilka wersji blisko związane procedury bez konieczności odróżnić je według nazwy.</span><span class="sxs-lookup"><span data-stu-id="758a1-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="758a1-105">W tym celu zróżnicowanie listy parametrów.</span><span class="sxs-lookup"><span data-stu-id="758a1-105">You do this by varying the parameter list.</span></span>  
  
## <a name="overloading-rules"></a><span data-ttu-id="758a1-106">Przeciążanie reguły</span><span class="sxs-lookup"><span data-stu-id="758a1-106">Overloading Rules</span></span>  
 <span data-ttu-id="758a1-107">Przeciążanie procedury, mają zastosowanie następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="758a1-107">When you overload a procedure, the following rules apply:</span></span>  
  
-   <span data-ttu-id="758a1-108">**Tej samej nazwy**.</span><span class="sxs-lookup"><span data-stu-id="758a1-108">**Same Name**.</span></span> <span data-ttu-id="758a1-109">Każdej zastąpionej wersji należy użyć tej samej nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="758a1-109">Each overloaded version must use the same procedure name.</span></span>  
  
-   <span data-ttu-id="758a1-110">**Inny podpis**.</span><span class="sxs-lookup"><span data-stu-id="758a1-110">**Different Signature**.</span></span> <span data-ttu-id="758a1-111">Każda wersja przeciążone musi różnić się od innych wersji przeciążone w co najmniej jeden z następujących aspektach:</span><span class="sxs-lookup"><span data-stu-id="758a1-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>  
  
    -   <span data-ttu-id="758a1-112">Liczba parametrów</span><span class="sxs-lookup"><span data-stu-id="758a1-112">Number of parameters</span></span>  
  
    -   <span data-ttu-id="758a1-113">Kolejność parametrów</span><span class="sxs-lookup"><span data-stu-id="758a1-113">Order of the parameters</span></span>  
  
    -   <span data-ttu-id="758a1-114">Typy danych parametrów</span><span class="sxs-lookup"><span data-stu-id="758a1-114">Data types of the parameters</span></span>  
  
    -   <span data-ttu-id="758a1-115">Liczba parametrów typu (dla procedury ogólny)</span><span class="sxs-lookup"><span data-stu-id="758a1-115">Number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="758a1-116">Zwracany typ (tylko dla operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="758a1-116">Return type (only for a conversion operator)</span></span>  
  
     <span data-ttu-id="758a1-117">Wraz z nazwą procedury poprzednie elementy są nazywane *podpisu* procedury.</span><span class="sxs-lookup"><span data-stu-id="758a1-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="758a1-118">Po wywołaniu procedury przeciążenia kompilator używa podpis do sprawdzenia, czy wywołanie poprawnie odpowiada definicji.</span><span class="sxs-lookup"><span data-stu-id="758a1-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>  
  
-   <span data-ttu-id="758a1-119">**Elementy nie jest częścią podpisu**.</span><span class="sxs-lookup"><span data-stu-id="758a1-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="758a1-120">Procedury nie mogą przeciążać bez zróżnicowanie podpisu.</span><span class="sxs-lookup"><span data-stu-id="758a1-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="758a1-121">W szczególności nie mogą przeciążać procedury przez zróżnicowanie tylko jeden lub więcej z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="758a1-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>  
  
    -   <span data-ttu-id="758a1-122">Słowa kluczowe modyfikator procedury, takich jak `Public`, `Shared`, i `Static`</span><span class="sxs-lookup"><span data-stu-id="758a1-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>  
  
    -   <span data-ttu-id="758a1-123">Parametr lub typ nazwy parametrów</span><span class="sxs-lookup"><span data-stu-id="758a1-123">Parameter or type parameter names</span></span>  
  
    -   <span data-ttu-id="758a1-124">Ograniczenia parametru typu (dla procedury ogólny)</span><span class="sxs-lookup"><span data-stu-id="758a1-124">Type parameter constraints (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="758a1-125">Słowa kluczowe modyfikator parametrów, takich jak `ByRef` i `Optional`</span><span class="sxs-lookup"><span data-stu-id="758a1-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>  
  
    -   <span data-ttu-id="758a1-126">Określa, czy wartość jest zwracana</span><span class="sxs-lookup"><span data-stu-id="758a1-126">Whether it returns a value</span></span>  
  
    -   <span data-ttu-id="758a1-127">Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="758a1-127">The data type of the return value (except for a conversion operator)</span></span>  
  
     <span data-ttu-id="758a1-128">Elementy na liście powyżej nie są częścią podpisu.</span><span class="sxs-lookup"><span data-stu-id="758a1-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="758a1-129">Mimo że nie można użyć ich do rozróżniania zastąpionej wersji, można je różnią przeciążone wersje, które są właściwie zróżnicowane przez ich podpisów.</span><span class="sxs-lookup"><span data-stu-id="758a1-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>  
  
-   <span data-ttu-id="758a1-130">**Późnym wiązaniem argumenty**.</span><span class="sxs-lookup"><span data-stu-id="758a1-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="758a1-131">Jeśli zamierzasz przekazać późne zmiennej obiektu związanego z wersją przeciążona, należy zadeklarować jako odpowiedni parametr <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="758a1-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>  
  
## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="758a1-132">Wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="758a1-132">Multiple Versions of a Procedure</span></span>  
 <span data-ttu-id="758a1-133">Załóżmy, że pisania `Sub` procedury można opublikować transakcji przed Saldo klienta i ma być możliwe do odwoływania się do klienta według nazwy lub numeru konta.</span><span class="sxs-lookup"><span data-stu-id="758a1-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="758a1-134">Aby to umożliwić, możesz zdefiniować dwa różne `Sub` procedur, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="758a1-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a><span data-ttu-id="758a1-135">Wersje przeciążone</span><span class="sxs-lookup"><span data-stu-id="758a1-135">Overloaded Versions</span></span>  
 <span data-ttu-id="758a1-136">Alternatywą jest nazwa jednej procedury przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="758a1-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="758a1-137">Można użyć [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) — słowo kluczowe, aby zdefiniować wersji procedury na wszystkich listach parametrem w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="758a1-137">You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a><span data-ttu-id="758a1-138">Dodatkowe przeciążenia</span><span class="sxs-lookup"><span data-stu-id="758a1-138">Additional Overloads</span></span>  
 <span data-ttu-id="758a1-139">Jeśli chcesz także zaakceptować kwota transakcji, albo `Decimal` lub `Single`, można dodatkowo przeciążenia `post` do obsługi tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="758a1-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="758a1-140">Jeśli tak, to nie wszystkie przeciążenia w poprzednim przykładzie należałoby cztery `Sub` procedur, wszystkie o takiej samej nazwie, ale z czterech różnych podpisów.</span><span class="sxs-lookup"><span data-stu-id="758a1-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>  
  
## <a name="advantages-of-overloading"></a><span data-ttu-id="758a1-141">Korzyści wynikające z przeciążenia</span><span class="sxs-lookup"><span data-stu-id="758a1-141">Advantages of Overloading</span></span>  
 <span data-ttu-id="758a1-142">Zaletą przeciążanie procedury jest elastyczność wywołania.</span><span class="sxs-lookup"><span data-stu-id="758a1-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="758a1-143">Do użycia `post` procedury zadeklarowany w poprzednim przykładzie kodu wywołującego, można uzyskać identyfikator klienta jako `String` lub `Integer`, a następnie wywołaj tę samą procedurę w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="758a1-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="758a1-144">Poniższy przykład przedstawia to:</span><span class="sxs-lookup"><span data-stu-id="758a1-144">The following example illustrates this:</span></span>  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="758a1-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="758a1-145">See Also</span></span>  
 [<span data-ttu-id="758a1-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="758a1-146">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="758a1-147">Instrukcje: definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="758a1-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)  
 [<span data-ttu-id="758a1-148">Instrukcje: wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="758a1-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)  
 [<span data-ttu-id="758a1-149">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="758a1-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [<span data-ttu-id="758a1-150">Instrukcje: przeciążanie procedury korzystającej z nieokreślonej liczby parametrów</span><span class="sxs-lookup"><span data-stu-id="758a1-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [<span data-ttu-id="758a1-151">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="758a1-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)  
 [<span data-ttu-id="758a1-152">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="758a1-152">Overload Resolution</span></span>](./overload-resolution.md)  
 [<span data-ttu-id="758a1-153">Overloads</span><span class="sxs-lookup"><span data-stu-id="758a1-153">Overloads</span></span>](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [<span data-ttu-id="758a1-154">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="758a1-154">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
