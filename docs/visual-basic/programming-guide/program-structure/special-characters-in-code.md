---
title: Znaki specjalne w Code (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 11c5ef9ad41fc2362d9ba4f2cb5eb5b63a9ca31c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="85e5a-102">Znaki specjalne w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="85e5a-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="85e5a-103">Czasami trzeba użyć znaków specjalnych w kodzie, oznacza to, znaki, które nie są alfabetycznej lub liczbowe.</span><span class="sxs-lookup"><span data-stu-id="85e5a-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="85e5a-104">Interpunkcja i znaki specjalne w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] różnych zastosowań z organizowanie tekst programu do określenia zadań, które wykonuje kompilatora lub skompilowany program ma zestaw znaków.</span><span class="sxs-lookup"><span data-stu-id="85e5a-104">The punctuation and special characters in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="85e5a-105">Nie należy określać operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="85e5a-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="85e5a-106">Nawiasów</span><span class="sxs-lookup"><span data-stu-id="85e5a-106">Parentheses</span></span>  
 <span data-ttu-id="85e5a-107">Użyj nawiasów w przypadku zdefiniowania procedury, takich jak `Sub` lub `Function`.</span><span class="sxs-lookup"><span data-stu-id="85e5a-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="85e5a-108">Wszystkie listy argumentów procedury należy ująć w nawias.</span><span class="sxs-lookup"><span data-stu-id="85e5a-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="85e5a-109">Również Użyj nawiasów wprowadzenia zmienne lub argumenty w grupy logiczne, szczególnie w celu zastąpienia domyślna kolejność pierwszeństwa operatora w wyrażenie złożone.</span><span class="sxs-lookup"><span data-stu-id="85e5a-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="85e5a-110">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="85e5a-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 <span data-ttu-id="85e5a-111">Po realizacji poprzedniego kodu, wartość `d` 8.225 i wartość `e` to 3.</span><span class="sxs-lookup"><span data-stu-id="85e5a-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="85e5a-112">Obliczanie `d` korzysta z domyślnego pierwszeństwo `/` za pośrednictwem `+` i stanowi odpowiednik `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="85e5a-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="85e5a-113">Nawiasy w obliczaniu `e` zastąpić domyślny priorytet.</span><span class="sxs-lookup"><span data-stu-id="85e5a-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="85e5a-114">Separatorach</span><span class="sxs-lookup"><span data-stu-id="85e5a-114">Separators</span></span>  
 <span data-ttu-id="85e5a-115">Separatory czy ich nazwy sugeruje: oddzielają fragmentów kodu.</span><span class="sxs-lookup"><span data-stu-id="85e5a-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="85e5a-116">W [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], znak separatora jest dwukropkiem (`:`).</span><span class="sxs-lookup"><span data-stu-id="85e5a-116">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], the separator character is the colon (`:`).</span></span> <span data-ttu-id="85e5a-117">Użyj separatorów, jeśli chcesz dołączyć wiele instrukcji w jednym wierszu, a nie oddzielnych wierszach.</span><span class="sxs-lookup"><span data-stu-id="85e5a-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="85e5a-118">To pozwala zaoszczędzić miejsce i poprawia czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="85e5a-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="85e5a-119">W poniższym przykładzie przedstawiono trzy instrukcje oddzielone dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="85e5a-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 <span data-ttu-id="85e5a-120">Aby uzyskać więcej informacji, zobacz [porady: podział i łączenie instrukcji w Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="85e5a-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="85e5a-121">Dwukropkiem (`:`) znaków również służy do identyfikowania etykiety instrukcji.</span><span class="sxs-lookup"><span data-stu-id="85e5a-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="85e5a-122">Aby uzyskać więcej informacji, zobacz [porady: Etykieta instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="85e5a-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="85e5a-123">Połączenie (konkatenacja)</span><span class="sxs-lookup"><span data-stu-id="85e5a-123">Concatenation</span></span>  
 <span data-ttu-id="85e5a-124">Użyj `&` operator *łączenia*, lub łączący ciągów.</span><span class="sxs-lookup"><span data-stu-id="85e5a-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="85e5a-125">Nie należy mylić jej z `+` operatora, który dodaje wartości liczbowych.</span><span class="sxs-lookup"><span data-stu-id="85e5a-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="85e5a-126">Jeśli używasz `+` operator do połączenia, gdy działają na wartości liczbowe można uzyskać niepoprawnych wyników.</span><span class="sxs-lookup"><span data-stu-id="85e5a-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="85e5a-127">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="85e5a-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 <span data-ttu-id="85e5a-128">Po realizacji poprzedniego kodu, wartość `resultA` jest 21.01 i wartość `resultB` jest "10.0111".</span><span class="sxs-lookup"><span data-stu-id="85e5a-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="85e5a-129">Operatory dostępu do elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="85e5a-129">Member Access Operators</span></span>  
 <span data-ttu-id="85e5a-130">Aby uzyskać dostęp do elementu członkowskiego typu, należy użyć kropki (.) (`.`) lub wykrzyknika (`!`) operatora pomiędzy nazwą typu i nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="85e5a-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="85e5a-131">Kropkę (.) Operator</span><span class="sxs-lookup"><span data-stu-id="85e5a-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="85e5a-132">Użyj `.` operator klasy, struktury, interfejsu lub wyliczenia jako operatora dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="85e5a-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="85e5a-133">Element członkowski może być pola, właściwości, zdarzenia lub metody.</span><span class="sxs-lookup"><span data-stu-id="85e5a-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="85e5a-134">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="85e5a-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="85e5a-135">Wykrzyknika (!) Operator</span><span class="sxs-lookup"><span data-stu-id="85e5a-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="85e5a-136">Użyj `!` operator tylko dla klasy ani interfejsu jako operator dostępu do słownika.</span><span class="sxs-lookup"><span data-stu-id="85e5a-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="85e5a-137">Klasy lub interfejsu musi mieć właściwość domyślny, który akceptuje pojedynczy `String` argumentu.</span><span class="sxs-lookup"><span data-stu-id="85e5a-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="85e5a-138">Identyfikator bezpośrednio po `!` operator staje się wartość argumentu przekazanego do domyślnej właściwości w postaci ciągu.</span><span class="sxs-lookup"><span data-stu-id="85e5a-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="85e5a-139">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="85e5a-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 <span data-ttu-id="85e5a-140">Output trzy wiersze `MsgBox` wszystkich wyświetlania wartość `32856`.</span><span class="sxs-lookup"><span data-stu-id="85e5a-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="85e5a-141">Pierwszy wiersz używa tradycyjny dostęp do właściwości `index`, drugi wykorzystuje fakt, że `index` jest domyślną właściwość klasy `hasDefault`, i trzeci używa słownika dostępu do klasy.</span><span class="sxs-lookup"><span data-stu-id="85e5a-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="85e5a-142">Należy pamiętać, że drugi operand `!` operatora musi być prawidłowym identyfikatorem języka Visual Basic nie jest ujęta w znaki podwójnego cudzysłowu (`" "`).</span><span class="sxs-lookup"><span data-stu-id="85e5a-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="85e5a-143">Innymi słowy nie można użyć literału ciągu lub zmiennej ciągu.</span><span class="sxs-lookup"><span data-stu-id="85e5a-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="85e5a-144">Następujące zmiany do ostatniego wiersza `MsgBox` wywołania generuje błąd, ponieważ `"X"` jest literałem ciągu zamknięte.</span><span class="sxs-lookup"><span data-stu-id="85e5a-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  <span data-ttu-id="85e5a-145">Musi być jawnego odwołania do kolekcji domyślnej.</span><span class="sxs-lookup"><span data-stu-id="85e5a-145">References to default collections must be explicit.</span></span> <span data-ttu-id="85e5a-146">W szczególności, nie można użyć `!` operatora zmiennej późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="85e5a-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="85e5a-147">`!` Znak jest również używany jako `Single` znaku typu.</span><span class="sxs-lookup"><span data-stu-id="85e5a-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e5a-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85e5a-148">See Also</span></span>  
 [<span data-ttu-id="85e5a-149">Struktura programu i konwencje związane z kodami</span><span class="sxs-lookup"><span data-stu-id="85e5a-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="85e5a-150">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="85e5a-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
