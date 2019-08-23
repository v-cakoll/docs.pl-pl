---
title: Znaki specjalne w Code (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 95bef937912e35cd828bf0090b4cf48ccb3290cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962467"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="1ab7a-102">Znaki specjalne w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ab7a-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="1ab7a-103">Czasami musisz używać znaków specjalnych w kodzie, czyli znaków, które nie są alfabetyczne ani liczbowe.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="1ab7a-104">Znaki interpunkcyjne i specjalne w zestawie znaków Visual Basic mają różne zastosowania, od porządkowania tekstu programu do definiowania zadań wykonywanych przez kompilator lub skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="1ab7a-105">Nie określają operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="1ab7a-106">Nawiasów</span><span class="sxs-lookup"><span data-stu-id="1ab7a-106">Parentheses</span></span>  
 <span data-ttu-id="1ab7a-107">Użyj nawiasów podczas definiowania procedury, takiej jak `Sub` lub. `Function`</span><span class="sxs-lookup"><span data-stu-id="1ab7a-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="1ab7a-108">Wszystkie listy argumentów procedury należy ująć w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="1ab7a-109">Należy również użyć nawiasów do umieszczania zmiennych lub argumentów w grupach logicznych, szczególnie w celu zastąpienia domyślnej kolejności operatorów w wyrażeniu złożonym.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="1ab7a-110">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="1ab7a-111">Po wykonaniu poprzedniego kodu wartość `d` jest 8,225, a `e` wartość to 3.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="1ab7a-112">Obliczenie dla `d` używa domyślnego `/` pierwszeństwa względem `+` i jest równoważne z `d = b + (c / a)`.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="1ab7a-113">Nawiasy w obliczeniach dla `e` zastąpienia domyślnego pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="1ab7a-114">Separatorach</span><span class="sxs-lookup"><span data-stu-id="1ab7a-114">Separators</span></span>  
 <span data-ttu-id="1ab7a-115">Separatory służą do jej sugerowania: oddzielą sekcje kodu.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="1ab7a-116">W Visual Basic znak separatora jest dwukropek (`:`).</span><span class="sxs-lookup"><span data-stu-id="1ab7a-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="1ab7a-117">Użyj separatorów, gdy chcesz uwzględnić wiele instrukcji w pojedynczym wierszu, a nie w osobnych wierszach.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="1ab7a-118">Pozwala to zaoszczędzić miejsce i zwiększa czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="1ab7a-119">Poniższy przykład przedstawia trzy instrukcje oddzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="1ab7a-120">Aby uzyskać więcej informacji, zobacz [jak: Przerywanie i łączenie instrukcji w](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)kodzie.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-120">For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="1ab7a-121">Znak dwukropka (`:`) jest również używany do identyfikowania etykiety instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="1ab7a-122">Aby uzyskać więcej informacji, zobacz [jak: Instrukcje](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)etykiet.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-122">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="1ab7a-123">Połączenie (konkatenacja)</span><span class="sxs-lookup"><span data-stu-id="1ab7a-123">Concatenation</span></span>  
 <span data-ttu-id="1ab7a-124">Użyj operatora do łączenia lub łączenia ciągów razem. `&`</span><span class="sxs-lookup"><span data-stu-id="1ab7a-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="1ab7a-125">Nie należy mylić tego `+` operatora z operatorem, który dodaje razem wartości liczbowe.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="1ab7a-126">Jeśli używasz `+` operatora do łączenia podczas wykonywania operacji na wartościach liczbowych, możesz uzyskać nieprawidłowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="1ab7a-127">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="1ab7a-128">Po wykonaniu poprzedniego kodu wartością `resultA` jest 21,01, a `resultB` wartością jest "10,0111".</span><span class="sxs-lookup"><span data-stu-id="1ab7a-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="1ab7a-129">Operatory dostępu do elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="1ab7a-129">Member Access Operators</span></span>  
 <span data-ttu-id="1ab7a-130">Aby uzyskać dostęp do elementu członkowskiego typu, należy użyć operatora kropki (`.`) lub wykrzyknika (`!`) między nazwą typu a nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="1ab7a-131">Kropka (.) Operator</span><span class="sxs-lookup"><span data-stu-id="1ab7a-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="1ab7a-132">`.` Użyj operatora dla klasy, struktury, interfejsu lub wyliczenia jako operatora dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="1ab7a-133">Składową może być pole, właściwość, zdarzenie lub metoda.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="1ab7a-134">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="1ab7a-135">Wykrzyknik (!) Operator</span><span class="sxs-lookup"><span data-stu-id="1ab7a-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="1ab7a-136">`!` Operatora należy używać tylko w klasie lub interfejsie jako operator dostępu do słownika.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="1ab7a-137">Klasa lub interfejs musi mieć właściwość domyślną, która akceptuje pojedynczy `String` argument.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="1ab7a-138">Identyfikator bezpośrednio po `!` operatorze będzie wartością argumentu przekazaną do domyślnej właściwości jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="1ab7a-139">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="1ab7a-140">Trzy wiersze `MsgBox` wyjściowe wszystkich wyświetlają wartość `32856`.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="1ab7a-141">Pierwszy wiersz używa tradycyjnego dostępu do właściwości `index`, drugi korzysta z faktu, że `index` jest domyślną właściwością klasy `hasDefault`, a trzeci używa dostępu do słownika do klasy.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="1ab7a-142">Należy zauważyć, że drugi operand `!` operatora musi być prawidłowym identyfikatorem Visual Basic, który nie jest ujęty w znaki podwójnego cudzysłowu (`" "`).</span><span class="sxs-lookup"><span data-stu-id="1ab7a-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="1ab7a-143">Innymi słowy, nie można użyć literału ciągu ani zmiennej ciągu.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="1ab7a-144">Następująca zmiana w ostatnim wierszu `MsgBox` wywołania powoduje wygenerowanie błędu, ponieważ `"X"` jest to ujęty w nawias literał ciągu.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="1ab7a-145">Odwołania do kolekcji domyślnych muszą być jawne.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-145">References to default collections must be explicit.</span></span> <span data-ttu-id="1ab7a-146">W szczególności nie można używać `!` operatora na zmiennej z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="1ab7a-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="1ab7a-147">Znak jest również używany `Single` jako znak typu. `!`</span><span class="sxs-lookup"><span data-stu-id="1ab7a-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab7a-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ab7a-148">See also</span></span>

- [<span data-ttu-id="1ab7a-149">Konwencje dotyczące struktury programów i kodu</span><span class="sxs-lookup"><span data-stu-id="1ab7a-149">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="1ab7a-150">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="1ab7a-150">Type Characters</span></span>](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
