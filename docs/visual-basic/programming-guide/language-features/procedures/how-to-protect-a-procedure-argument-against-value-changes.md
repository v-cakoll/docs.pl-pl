---
title: "Porady: chronienie argumentu procedury przed zmianami wartości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7975cbbc38c39223a4af5c87ac6bb090be548f2d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a><span data-ttu-id="a8c16-102">Porady: chronienie argumentu procedury przed zmianami wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8c16-102">How to: Protect a Procedure Argument Against Value Changes (Visual Basic)</span></span>
<span data-ttu-id="a8c16-103">Jeśli procedura deklaruje jako parametru [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] daje kodu procedury bezpośrednie odwołanie do elementu programistycznego bazowy argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a8c16-103">If a procedure declares a parameter as [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gives the procedure code a direct reference to the programming element underlying the argument in the calling code.</span></span> <span data-ttu-id="a8c16-104">Pozwala to na procedurę, aby zmienić wartość bazowy argumentu w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a8c16-104">This permits the procedure to change the value underlying the argument in the calling code.</span></span> <span data-ttu-id="a8c16-105">W niektórych przypadkach kod wywołujący może być przydatna ochrona przed tej zmiany.</span><span class="sxs-lookup"><span data-stu-id="a8c16-105">In some cases the calling code might want to protect against such a change.</span></span>  
  
 <span data-ttu-id="a8c16-106">Zawsze chronić argumentu z zmiany przez zadeklarowanie odpowiadającego mu parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) w procedurze.</span><span class="sxs-lookup"><span data-stu-id="a8c16-106">You can always protect an argument from change by declaring the corresponding parameter [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) in the procedure.</span></span> <span data-ttu-id="a8c16-107">Jeśli chcesz mieć możliwość zmiany podany argument w niektórych przypadkach, ale nie można zadeklarować go `ByRef` i pozwolić, aby określić mechanizm przekazywania w każdym wywołaniu kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="a8c16-107">If you want to be able to change a given argument in some cases but not others, you can declare it `ByRef` and let the calling code determine the passing mechanism in each call.</span></span> <span data-ttu-id="a8c16-108">Jest to możliwe dzięki otaczającej odpowiadającego mu argumentu w nawiasach przekazywany przez wartość lub nie należy ująć w nawias przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="a8c16-108">It does this by enclosing the corresponding argument in parentheses to pass it by value, or not enclosing it in parentheses to pass it by reference.</span></span> <span data-ttu-id="a8c16-109">Aby uzyskać więcej informacji, zobacz [porady: Wymuszanie przekazywania argumentu przez wartość](./how-to-force-an-argument-to-be-passed-by-value.md).</span><span class="sxs-lookup"><span data-stu-id="a8c16-109">For more information, see [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8c16-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8c16-110">Example</span></span>  
 <span data-ttu-id="a8c16-111">W poniższym przykładzie przedstawiono dwie procedury, które podejmują zmienną tablicową i które działają na swoich elementów.</span><span class="sxs-lookup"><span data-stu-id="a8c16-111">The following example shows two procedures that take an array variable and operate on its elements.</span></span> <span data-ttu-id="a8c16-112">`increase` Procedury po prostu dodaje je do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="a8c16-112">The `increase` procedure simply adds one to each element.</span></span> <span data-ttu-id="a8c16-113">`replace` Procedury przypisuje nową macierz do parametru `a()` , a następnie dodaje je do każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="a8c16-113">The `replace` procedure assigns a new array to the parameter `a()` and then adds one to each element.</span></span> <span data-ttu-id="a8c16-114">Jednak ponowne przypisanie nie ma wpływu na podstawowe zmiennej tablicy w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a8c16-114">However, the reassignment does not affect the underlying array variable in the calling code.</span></span>  
  
 [!code-vb[VbVbcnProcedures#35](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#38](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_2.vb)]  
  
 [!code-vb[VbVbcnProcedures#37](./codesnippet/VisualBasic/how-to-protect-a-procedure-argument-against-value-changes_3.vb)]  
  
 <span data-ttu-id="a8c16-115">Pierwszy `MsgBox` wywołać Wyświetla "po increase(n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="a8c16-115">The first `MsgBox` call displays "After increase(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="a8c16-116">Ponieważ tablicy `n` jest typem referencyjnym `replace` można zmienić jej członków, nawet jeśli jest mechanizm przekazywania `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="a8c16-116">Because the array `n` is a reference type, `replace` can change its members, even though the passing mechanism is `ByVal`.</span></span>  
  
 <span data-ttu-id="a8c16-117">Drugi `MsgBox` wywołać Wyświetla "po replace(n): 11, 21, 31, 41".</span><span class="sxs-lookup"><span data-stu-id="a8c16-117">The second `MsgBox` call displays "After replace(n): 11, 21, 31, 41".</span></span> <span data-ttu-id="a8c16-118">Ponieważ `n` jest przekazywany `ByVal`, `replace` nie można zmodyfikować zmienną `n` w wywoływanym kodzie przez przypisanie nowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="a8c16-118">Because `n` is passed `ByVal`, `replace` cannot modify the variable `n` in the calling code by assigning a new array to it.</span></span> <span data-ttu-id="a8c16-119">Gdy `replace` tworzy nowe wystąpienie tablicy `k` i przypisuje go do zmiennej lokalnej `a`, tym samym odwołanie do `n` przekazany przez wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="a8c16-119">When `replace` creates the new array instance `k` and assigns it to the local variable `a`, it loses the reference to `n` passed in by the calling code.</span></span> <span data-ttu-id="a8c16-120">Podczas zmiany jego elementów członkowskich `a`, lokalnej tablicy `k` dotyczy.</span><span class="sxs-lookup"><span data-stu-id="a8c16-120">When it changes the members of `a`, only the local array `k` is affected.</span></span> <span data-ttu-id="a8c16-121">W związku z tym `replace` nie zwiększa się wartości w tablicy `n` w wywoływanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a8c16-121">Therefore, `replace` does not increment the values of array `n` in the calling code.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a8c16-122">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a8c16-122">Compiling the Code</span></span>  
 <span data-ttu-id="a8c16-123">Domyślnie [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ma argument jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="a8c16-123">The default in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] is to pass arguments by value.</span></span> <span data-ttu-id="a8c16-124">Jednak jest dobre rozwiązanie to dołączenie albo programowania [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) — słowo kluczowe z każdym zadeklarowany parametr.</span><span class="sxs-lookup"><span data-stu-id="a8c16-124">However, it is good programming practice to include either the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword with every declared parameter.</span></span> <span data-ttu-id="a8c16-125">Ułatwia to kodu do odczytu.</span><span class="sxs-lookup"><span data-stu-id="a8c16-125">This makes your code easier to read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c16-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8c16-126">See Also</span></span>  
 [<span data-ttu-id="a8c16-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="a8c16-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="a8c16-128">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="a8c16-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="a8c16-129">Porady: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="a8c16-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="a8c16-130">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="a8c16-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="a8c16-131">Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="a8c16-131">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)  
 [<span data-ttu-id="a8c16-132">Różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="a8c16-132">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="a8c16-133">Porady: Zmienianie wartości argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="a8c16-133">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="a8c16-134">Porady: Wymuszanie przekazywania argumentu przez wartość</span><span class="sxs-lookup"><span data-stu-id="a8c16-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="a8c16-135">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="a8c16-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="a8c16-136">Typy wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="a8c16-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
