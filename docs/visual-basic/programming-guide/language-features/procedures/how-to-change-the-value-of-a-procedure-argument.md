---
title: 'Instrukcje: Zmień wartość argumentu procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: 096bc6adfa7a8c95674d235f0112d23f7a45caf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672295"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a><span data-ttu-id="80f67-102">Instrukcje: Zmień wartość argumentu procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80f67-102">How to: Change the Value of a Procedure Argument (Visual Basic)</span></span>
<span data-ttu-id="80f67-103">Po wywołaniu procedury, każdy argument, który podasz odnosi się do jednego z parametrów zdefiniowanych w procedurze.</span><span class="sxs-lookup"><span data-stu-id="80f67-103">When you call a procedure, each argument you supply corresponds to one of the parameters defined in the procedure.</span></span> <span data-ttu-id="80f67-104">W niektórych przypadkach kod procedury można zmienić wartości bazowe argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80f67-104">In some cases, the procedure code can change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="80f67-105">W innych przypadkach procedura może zmienić tylko w swojej lokalnej kopii argumentu.</span><span class="sxs-lookup"><span data-stu-id="80f67-105">In other cases, the procedure can change only its local copy of an argument.</span></span>  
  
 <span data-ttu-id="80f67-106">Po wywołaniu procedury, Visual Basic sprawia, że lokalna kopia każdego argumentu, który jest przekazywany [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="80f67-106">When you call the procedure, Visual Basic makes a local copy of every argument that is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="80f67-107">Każdy argument przekazany [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic, zawiera kod procedury bezpośrednie odwołanie do elementu programistycznego, bazowy argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80f67-107">For each argument passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), Visual Basic gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span>  
  
 <span data-ttu-id="80f67-108">Jeśli element podstawowy kod wywołujący jest elementem można modyfikować, a argument jest przekazywany `ByRef`, kod procedury użyć odwołanie bezpośrednie tak, aby zmienić wartości elementu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80f67-108">If the underlying element in the calling code is a modifiable element and the argument is passed `ByRef`, the procedure code can use the direct reference to change the element's value in the calling code.</span></span>  
  
## <a name="changing-the-underlying-value"></a><span data-ttu-id="80f67-109">Zmiana wartości podstawowej</span><span class="sxs-lookup"><span data-stu-id="80f67-109">Changing the Underlying Value</span></span>  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a><span data-ttu-id="80f67-110">Aby zmienić podstawowej wartości argumentu w wywoływanym kodzie procedury</span><span class="sxs-lookup"><span data-stu-id="80f67-110">To change the underlying value of a procedure argument in the calling code</span></span>  
  
1.  <span data-ttu-id="80f67-111">W deklaracji procedury, należy określić [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) parametru odpowiadającego atrybutowi argument.</span><span class="sxs-lookup"><span data-stu-id="80f67-111">In the procedure declaration, specify [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) for the parameter corresponding to the argument.</span></span>  
  
2.  <span data-ttu-id="80f67-112">W wywoływanym kodzie należy przekazać można modyfikować elementu programistycznego jako argument.</span><span class="sxs-lookup"><span data-stu-id="80f67-112">In the calling code, pass a modifiable programming element as the argument.</span></span>  
  
3.  <span data-ttu-id="80f67-113">W wywoływanym kodzie nie należy umieszczać argument w nawiasach na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="80f67-113">In the calling code, do not enclose the argument in parentheses in the argument list.</span></span>  
  
4.  <span data-ttu-id="80f67-114">W kodzie procedury należy użyć nazwy parametru do przypisania wartości do elementu bazowego w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80f67-114">In the procedure code, use the parameter name to assign a value to the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="80f67-115">Zobacz przykład dalej na dół demonstracyjne.</span><span class="sxs-lookup"><span data-stu-id="80f67-115">See the example further down for a demonstration.</span></span>  
  
## <a name="changing-local-copies"></a><span data-ttu-id="80f67-116">Zmiana kopiami lokalnymi</span><span class="sxs-lookup"><span data-stu-id="80f67-116">Changing Local Copies</span></span>  
 <span data-ttu-id="80f67-117">Jeśli element podstawowy kod wywołujący jest elementem niemodyfikowalnymi lub jeśli argument jest przekazywany `ByVal`, procedury nie można zmienić jego wartość w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80f67-117">If the underlying element in the calling code is a nonmodifiable element, or if the argument is passed `ByVal`, the procedure cannot change its value in the calling code.</span></span> <span data-ttu-id="80f67-118">Procedurę można zmieniać swojej lokalnej kopii takich argumentu.</span><span class="sxs-lookup"><span data-stu-id="80f67-118">However, the procedure can change its local copy of such an argument.</span></span>  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a><span data-ttu-id="80f67-119">Aby zmienić kopię argumentu procedury w kodzie procedury</span><span class="sxs-lookup"><span data-stu-id="80f67-119">To change the copy of a procedure argument in the procedure code</span></span>  
  
1.  <span data-ttu-id="80f67-120">W deklaracji procedury, należy określić [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) parametru odpowiadającego atrybutowi argument.</span><span class="sxs-lookup"><span data-stu-id="80f67-120">In the procedure declaration, specify [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) for the parameter corresponding to the argument.</span></span>  
  
     <span data-ttu-id="80f67-121">—lub—</span><span class="sxs-lookup"><span data-stu-id="80f67-121">-or-</span></span>  
  
     <span data-ttu-id="80f67-122">W wywoływanym kodzie należy ująć argument w nawiasach na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="80f67-122">In the calling code, enclose the argument in parentheses in the argument list.</span></span> <span data-ttu-id="80f67-123">Zmusza to Visual Basic do przekazywania argumentu przez wartość, nawet wtedy, gdy odpowiedni parametr określa `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="80f67-123">This forces Visual Basic to pass the argument by value, even if the corresponding parameter specifies `ByRef`.</span></span>  
  
2.  <span data-ttu-id="80f67-124">W kodzie procedury należy użyć nazwy parametru do przypisania wartości do lokalnej kopi argumentu.</span><span class="sxs-lookup"><span data-stu-id="80f67-124">In the procedure code, use the parameter name to assign a value to the local copy of the argument.</span></span> <span data-ttu-id="80f67-125">Podstawową wartość w kod wywołujący nie jest zmieniany.</span><span class="sxs-lookup"><span data-stu-id="80f67-125">The underlying value in the calling code is not changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80f67-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="80f67-126">Example</span></span>  
 <span data-ttu-id="80f67-127">Poniższy przykład przedstawia dwie procedury używające zmiennej tablicy i działać na jego elementach.</span><span class="sxs-lookup"><span data-stu-id="80f67-127">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="80f67-128">`increase` Procedura dodaje po prostu jednym do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="80f67-128">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="80f67-129">`replace` Procedury przypisuje nową tablicę z parametrem `a()` , a następnie dodaje je do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="80f67-129">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#36](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-change-the-value-of-a-procedure-argument_3.vb)]  
  
 <span data-ttu-id="80f67-130">Pierwszy `MsgBox` wywołać Wyświetla "po increase(n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="80f67-130">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="80f67-131">Ponieważ tablicy `n` jest typem referencyjnym `replace` można zmienić jej członków, nawet jeśli jest mechanizm przekazywania `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="80f67-131">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="80f67-132">Drugi `MsgBox` wywołać Wyświetla "po replace(n): 101, 201, 301".</span><span class="sxs-lookup"><span data-stu-id="80f67-132">The second `MsgBox` call displays "After replace(n): 101, 201, 301".</span></span> <span data-ttu-id="80f67-133">Ponieważ `n` jest przekazywany `ByRef`, `replace` można zmodyfikować zmienną `n` w wywoływanym kodzie i przypisać nową tablicę do niego.</span><span class="sxs-lookup"><span data-stu-id="80f67-133">Because `n` is passed `ByRef`, `replace` can modify the variable `n` in the calling code and assign a new array to it.</span></span> <span data-ttu-id="80f67-134">Ponieważ `n` jest typem referencyjnym `replace` można również zmienić jej członków.</span><span class="sxs-lookup"><span data-stu-id="80f67-134">Because `n` is a reference type, `replace` can also change its members.</span></span>  
  
 <span data-ttu-id="80f67-135">Aby uniemożliwić procedurę modyfikowania zmiennej w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="80f67-135">You can prevent the procedure from modifying the variable itself in the calling code.</span></span> <span data-ttu-id="80f67-136">Zobacz [jak: Chronienie argumentu procedury przed zmianami wartości](./how-to-protect-a-procedure-argument-against-value-changes.md).</span><span class="sxs-lookup"><span data-stu-id="80f67-136">See [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80f67-137">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80f67-137">Compiling the Code</span></span>  
 <span data-ttu-id="80f67-138">Jeśli zmienna jest przekazywane przez odwołanie, musisz użyć `ByRef` — słowo kluczowe, aby określić, ten mechanizm.</span><span class="sxs-lookup"><span data-stu-id="80f67-138">When you pass a variable by reference, you must use the `ByRef` keyword to specify this mechanism.</span></span>  
  
 <span data-ttu-id="80f67-139">Domyślnie w języku Visual Basic nie jest przekazywanie argumentów według wartości.</span><span class="sxs-lookup"><span data-stu-id="80f67-139">The default in Visual Basic is to pass arguments by value.</span></span> <span data-ttu-id="80f67-140">Jednak dobrą praktyką, aby uwzględnić albo programowania jest [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr.</span><span class="sxs-lookup"><span data-stu-id="80f67-140">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="80f67-141">Dzięki temu można łatwiej odczytać kodu.</span><span class="sxs-lookup"><span data-stu-id="80f67-141">This makes your code easier to read.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="80f67-142">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="80f67-142">.NET Framework Security</span></span>  
 <span data-ttu-id="80f67-143">Z zezwoleniem na procedury zmienić wartość argumentu w wywoływanym kodzie bazowego zawsze to potencjalne zagrożenie.</span><span class="sxs-lookup"><span data-stu-id="80f67-143">There is always a potential risk in allowing a procedure to change the value underlying an argument in the calling code.</span></span> <span data-ttu-id="80f67-144">Upewnij się, że oczekiwane tę wartość można zmienić i przygotowywane do sprawdzania poprawności, przed jego użyciem.</span><span class="sxs-lookup"><span data-stu-id="80f67-144">Make sure you expect this value to be changed, and be prepared to check it for validity before using it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80f67-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="80f67-145">See also</span></span>
- [<span data-ttu-id="80f67-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="80f67-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="80f67-147">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="80f67-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="80f67-148">Instrukcje: Przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="80f67-148">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="80f67-149">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="80f67-149">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="80f67-150">Różnice między argumentami modyfikowalnymi i niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="80f67-150">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="80f67-151">Różnice między przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="80f67-151">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [<span data-ttu-id="80f67-152">Instrukcje: Chronienie argumentu procedury przed zmianami wartości</span><span class="sxs-lookup"><span data-stu-id="80f67-152">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="80f67-153">Instrukcje: Wymuszanie być przekazywany przez wartość argumentu</span><span class="sxs-lookup"><span data-stu-id="80f67-153">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="80f67-154">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="80f67-154">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="80f67-155">Typy wartości i odwołań</span><span class="sxs-lookup"><span data-stu-id="80f67-155">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
