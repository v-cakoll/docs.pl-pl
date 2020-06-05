---
title: Przeciążanie procedury
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
ms.openlocfilehash: f8accc74fbdd9b1d8cf9bc3d8f6ddd26f73452b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363879"
---
# <a name="procedure-overloading-visual-basic"></a><span data-ttu-id="64e4e-102">Przeciążanie procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64e4e-102">Procedure Overloading (Visual Basic)</span></span>

<span data-ttu-id="64e4e-103">*Przeciążanie* procedury oznacza zdefiniowanie jej w wielu wersjach przy użyciu takiej samej nazwy, ale innych list parametrów.</span><span class="sxs-lookup"><span data-stu-id="64e4e-103">*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists.</span></span> <span data-ttu-id="64e4e-104">Przeciążanie polega na zdefiniowaniu kilku ściśle powiązanych wersji procedury bez konieczności odróżnienia ich według nazwy.</span><span class="sxs-lookup"><span data-stu-id="64e4e-104">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span> <span data-ttu-id="64e4e-105">Można to zrobić, zmieniając listę parametrów.</span><span class="sxs-lookup"><span data-stu-id="64e4e-105">You do this by varying the parameter list.</span></span>

## <a name="overloading-rules"></a><span data-ttu-id="64e4e-106">Reguły przeciążania</span><span class="sxs-lookup"><span data-stu-id="64e4e-106">Overloading Rules</span></span>

<span data-ttu-id="64e4e-107">W przypadku przeciążenia procedury stosowane są następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="64e4e-107">When you overload a procedure, the following rules apply:</span></span>

- <span data-ttu-id="64e4e-108">**Ta sama nazwa**.</span><span class="sxs-lookup"><span data-stu-id="64e4e-108">**Same Name**.</span></span> <span data-ttu-id="64e4e-109">Każda przeciążona wersja musi używać tej samej nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="64e4e-109">Each overloaded version must use the same procedure name.</span></span>

- <span data-ttu-id="64e4e-110">**Inny podpis**.</span><span class="sxs-lookup"><span data-stu-id="64e4e-110">**Different Signature**.</span></span> <span data-ttu-id="64e4e-111">Każda przeciążona wersja musi różnić się od wszystkich innych przeciążonych wersji w co najmniej jednej z następujących kwestii:</span><span class="sxs-lookup"><span data-stu-id="64e4e-111">Each overloaded version must differ from all other overloaded versions in at least one of the following respects:</span></span>

  - <span data-ttu-id="64e4e-112">Liczba parametrów</span><span class="sxs-lookup"><span data-stu-id="64e4e-112">Number of parameters</span></span>

  - <span data-ttu-id="64e4e-113">Kolejność parametrów</span><span class="sxs-lookup"><span data-stu-id="64e4e-113">Order of the parameters</span></span>

  - <span data-ttu-id="64e4e-114">Typy danych parametrów</span><span class="sxs-lookup"><span data-stu-id="64e4e-114">Data types of the parameters</span></span>

  - <span data-ttu-id="64e4e-115">Liczba parametrów typu (dla procedury ogólnej)</span><span class="sxs-lookup"><span data-stu-id="64e4e-115">Number of type parameters (for a generic procedure)</span></span>

  - <span data-ttu-id="64e4e-116">Zwracany typ (tylko dla operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="64e4e-116">Return type (only for a conversion operator)</span></span>

  <span data-ttu-id="64e4e-117">Wraz z nazwą procedury, poprzednie elementy są zbiorczo nazywane *podpisem* procedury.</span><span class="sxs-lookup"><span data-stu-id="64e4e-117">Together with the procedure name, the preceding items are collectively called the *signature* of the procedure.</span></span> <span data-ttu-id="64e4e-118">Gdy wywołujesz przeciążoną procedurę, kompilator używa podpisu, aby sprawdzić, czy wywołanie jest prawidłowo zgodne z definicją.</span><span class="sxs-lookup"><span data-stu-id="64e4e-118">When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.</span></span>

- <span data-ttu-id="64e4e-119">**Elementy nie są częścią podpisu**.</span><span class="sxs-lookup"><span data-stu-id="64e4e-119">**Items Not Part of Signature**.</span></span> <span data-ttu-id="64e4e-120">Nie można przeciążać procedury bez różnicowania podpisu.</span><span class="sxs-lookup"><span data-stu-id="64e4e-120">You cannot overload a procedure without varying the signature.</span></span> <span data-ttu-id="64e4e-121">W szczególności nie można przeciążać procedury, zmieniając tylko jeden lub więcej z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="64e4e-121">In particular, you cannot overload a procedure by varying only one or more of the following items:</span></span>

  - <span data-ttu-id="64e4e-122">Słowa kluczowe modyfikatora procedury, takie jak `Public` , `Shared` , i`Static`</span><span class="sxs-lookup"><span data-stu-id="64e4e-122">Procedure modifier keywords, such as `Public`, `Shared`, and `Static`</span></span>

  - <span data-ttu-id="64e4e-123">Nazwy parametrów lub parametrów typu</span><span class="sxs-lookup"><span data-stu-id="64e4e-123">Parameter or type parameter names</span></span>

  - <span data-ttu-id="64e4e-124">Ograniczenia parametru typu (dla procedury ogólnej)</span><span class="sxs-lookup"><span data-stu-id="64e4e-124">Type parameter constraints (for a generic procedure)</span></span>

  - <span data-ttu-id="64e4e-125">Słowa kluczowe modyfikatora parametru, takie jak `ByRef` i`Optional`</span><span class="sxs-lookup"><span data-stu-id="64e4e-125">Parameter modifier keywords, such as `ByRef` and `Optional`</span></span>

  - <span data-ttu-id="64e4e-126">Czy zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="64e4e-126">Whether it returns a value</span></span>

  - <span data-ttu-id="64e4e-127">Typ danych wartości zwracanej (z wyjątkiem operatora konwersji)</span><span class="sxs-lookup"><span data-stu-id="64e4e-127">The data type of the return value (except for a conversion operator)</span></span>

  <span data-ttu-id="64e4e-128">Elementy z powyższej listy nie są częścią podpisu.</span><span class="sxs-lookup"><span data-stu-id="64e4e-128">The items in the preceding list are not part of the signature.</span></span> <span data-ttu-id="64e4e-129">Chociaż nie można ich używać do rozróżniania przeciążonych wersji, można różnicować je między przeciążonymi wersjami, które są poprawnie różnicowane według ich sygnatur.</span><span class="sxs-lookup"><span data-stu-id="64e4e-129">Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.</span></span>

- <span data-ttu-id="64e4e-130">**Argumenty z późnym wiązaniem**.</span><span class="sxs-lookup"><span data-stu-id="64e4e-130">**Late-Bound Arguments**.</span></span> <span data-ttu-id="64e4e-131">Jeśli zamierzasz przekazać zmienną obiektu z późnym wiązaniem do przeciążonej wersji, musisz zadeklarować odpowiedni parametr jako <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="64e4e-131">If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.</span></span>

## <a name="multiple-versions-of-a-procedure"></a><span data-ttu-id="64e4e-132">Wiele wersji procedury</span><span class="sxs-lookup"><span data-stu-id="64e4e-132">Multiple Versions of a Procedure</span></span>

<span data-ttu-id="64e4e-133">Załóżmy, że piszesz `Sub` procedurę w celu opublikowania transakcji w oparciu o saldo klienta i chcesz mieć możliwość odwoływania się do klienta według nazwy lub numeru konta.</span><span class="sxs-lookup"><span data-stu-id="64e4e-133">Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number.</span></span> <span data-ttu-id="64e4e-134">Aby to umożliwić, można zdefiniować dwie różne `Sub` procedury, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="64e4e-134">To accommodate this, you can define two different `Sub` procedures, as in the following example:</span></span>

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a><span data-ttu-id="64e4e-135">Przeciążone wersje</span><span class="sxs-lookup"><span data-stu-id="64e4e-135">Overloaded Versions</span></span>

<span data-ttu-id="64e4e-136">Alternatywą jest przeciążanie pojedynczej nazwy procedury.</span><span class="sxs-lookup"><span data-stu-id="64e4e-136">An alternative is to overload a single procedure name.</span></span> <span data-ttu-id="64e4e-137">Możesz użyć słowa kluczowego [overloads](../../../language-reference/modifiers/overloads.md) , aby zdefiniować wersję procedury dla każdej listy parametrów w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="64e4e-137">You can use the [Overloads](../../../language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:</span></span>

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a><span data-ttu-id="64e4e-138">Dodatkowe przeciążenia</span><span class="sxs-lookup"><span data-stu-id="64e4e-138">Additional Overloads</span></span>

<span data-ttu-id="64e4e-139">Jeśli chcesz również zaakceptować kwotę transakcji w `Decimal` lub `Single` , możesz dodatkowo przeciążyć, `post` Aby zezwolić na tę odmianę.</span><span class="sxs-lookup"><span data-stu-id="64e4e-139">If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation.</span></span> <span data-ttu-id="64e4e-140">Jeśli przeciążenia zostały wykonane w poprzednim przykładzie, będziesz mieć cztery `Sub` procedury, wszystkie o tej samej nazwie, ale z czterema różnymi podpisami.</span><span class="sxs-lookup"><span data-stu-id="64e4e-140">If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.</span></span>

## <a name="advantages-of-overloading"></a><span data-ttu-id="64e4e-141">Zalety przeciążenia</span><span class="sxs-lookup"><span data-stu-id="64e4e-141">Advantages of Overloading</span></span>

<span data-ttu-id="64e4e-142">Zaletą przeładowania procedury jest elastyczność wywołania.</span><span class="sxs-lookup"><span data-stu-id="64e4e-142">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="64e4e-143">Aby użyć `post` procedury zadeklarowanej w poprzednim przykładzie, kod wywołujący może uzyskać identyfikację klienta jako `String` albo a `Integer` , a następnie wywołać tę samą procedurę w obu przypadkach.</span><span class="sxs-lookup"><span data-stu-id="64e4e-143">To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case.</span></span> <span data-ttu-id="64e4e-144">Zostało to przedstawione w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="64e4e-144">The following example illustrates this:</span></span>

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a><span data-ttu-id="64e4e-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64e4e-145">See also</span></span>

- [<span data-ttu-id="64e4e-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="64e4e-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="64e4e-147">Instrukcje: definiowanie wielu wersji procedury</span><span class="sxs-lookup"><span data-stu-id="64e4e-147">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="64e4e-148">Instrukcje: wywoływanie procedury przeciążenia</span><span class="sxs-lookup"><span data-stu-id="64e4e-148">How to: Call an Overloaded Procedure</span></span>](./how-to-call-an-overloaded-procedure.md)
- [<span data-ttu-id="64e4e-149">Instrukcje: przeciążanie procedury korzystającej z parametrów opcjonalnych</span><span class="sxs-lookup"><span data-stu-id="64e4e-149">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="64e4e-150">Porady: przeciążanie procedury wykorzystującej nieokreśloną liczbę parametrów</span><span class="sxs-lookup"><span data-stu-id="64e4e-150">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="64e4e-151">Zagadnienia dotyczące przeciążania procedur</span><span class="sxs-lookup"><span data-stu-id="64e4e-151">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="64e4e-152">Rozpoznanie przeciążenia</span><span class="sxs-lookup"><span data-stu-id="64e4e-152">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="64e4e-153">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="64e4e-153">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="64e4e-154">Typy ogólne w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64e4e-154">Generic Types in Visual Basic</span></span>](../data-types/generic-types.md)
