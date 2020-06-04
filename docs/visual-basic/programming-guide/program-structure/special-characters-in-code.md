---
title: Znaki specjalne w kodzie
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
ms.openlocfilehash: c9b170ed812474cdeee100f1dc388d5c7e85f2cc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400594"
---
# <a name="special-characters-in-code-visual-basic"></a><span data-ttu-id="13f80-102">Znaki specjalne w Code (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13f80-102">Special Characters in Code (Visual Basic)</span></span>
<span data-ttu-id="13f80-103">Czasami musisz używać znaków specjalnych w kodzie, czyli znaków, które nie są alfabetyczne ani liczbowe.</span><span class="sxs-lookup"><span data-stu-id="13f80-103">Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric.</span></span> <span data-ttu-id="13f80-104">Znaki interpunkcyjne i specjalne w zestawie znaków Visual Basic mają różne zastosowania, od porządkowania tekstu programu do definiowania zadań wykonywanych przez kompilator lub skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="13f80-104">The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs.</span></span> <span data-ttu-id="13f80-105">Nie określają operacji do wykonania.</span><span class="sxs-lookup"><span data-stu-id="13f80-105">They do not specify an operation to be performed.</span></span>  
  
## <a name="parentheses"></a><span data-ttu-id="13f80-106">Nawiasy</span><span class="sxs-lookup"><span data-stu-id="13f80-106">Parentheses</span></span>  
 <span data-ttu-id="13f80-107">Użyj nawiasów podczas definiowania procedury, takiej jak `Sub` lub `Function` .</span><span class="sxs-lookup"><span data-stu-id="13f80-107">Use parentheses when you define a procedure, such as a `Sub` or `Function`.</span></span> <span data-ttu-id="13f80-108">Wszystkie listy argumentów procedury należy ująć w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="13f80-108">You must enclose all procedure argument lists in parentheses.</span></span> <span data-ttu-id="13f80-109">Należy również użyć nawiasów do umieszczania zmiennych lub argumentów w grupach logicznych, szczególnie w celu zastąpienia domyślnej kolejności operatorów w wyrażeniu złożonym.</span><span class="sxs-lookup"><span data-stu-id="13f80-109">You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression.</span></span> <span data-ttu-id="13f80-110">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="13f80-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 <span data-ttu-id="13f80-111">Po wykonaniu poprzedniego kodu wartość `d` jest 8,225, a wartość `e` to 3.</span><span class="sxs-lookup"><span data-stu-id="13f80-111">Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3.</span></span> <span data-ttu-id="13f80-112">Obliczenie dla `d` używa domyślnego pierwszeństwa `/` względem `+` i jest równoważne z `d = b + (c / a)` .</span><span class="sxs-lookup"><span data-stu-id="13f80-112">The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`.</span></span> <span data-ttu-id="13f80-113">Nawiasy w obliczeniach dla `e` zastąpienia domyślnego pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="13f80-113">The parentheses in the calculation for `e` override the default precedence.</span></span>  
  
## <a name="separators"></a><span data-ttu-id="13f80-114">Separatorach</span><span class="sxs-lookup"><span data-stu-id="13f80-114">Separators</span></span>  
 <span data-ttu-id="13f80-115">Separatory służą do jej sugerowania: oddzielą sekcje kodu.</span><span class="sxs-lookup"><span data-stu-id="13f80-115">Separators do what their name suggests: they separate sections of code.</span></span> <span data-ttu-id="13f80-116">W Visual Basic znak separatora jest dwukropek ( `:` ).</span><span class="sxs-lookup"><span data-stu-id="13f80-116">In Visual Basic, the separator character is the colon (`:`).</span></span> <span data-ttu-id="13f80-117">Użyj separatorów, gdy chcesz uwzględnić wiele instrukcji w pojedynczym wierszu, a nie w osobnych wierszach.</span><span class="sxs-lookup"><span data-stu-id="13f80-117">Use separators when you want to include multiple statements on a single line instead of separate lines.</span></span> <span data-ttu-id="13f80-118">Pozwala to zaoszczędzić miejsce i zwiększa czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="13f80-118">This saves space and improves the readability of your code.</span></span> <span data-ttu-id="13f80-119">Poniższy przykład przedstawia trzy instrukcje oddzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="13f80-119">The following example shows three statements separated by colons.</span></span>  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 <span data-ttu-id="13f80-120">Aby uzyskać więcej informacji, zobacz [jak: przerywanie i łączenie instrukcji w kodzie](how-to-break-and-combine-statements-in-code.md).</span><span class="sxs-lookup"><span data-stu-id="13f80-120">For more information, see [How to: Break and Combine Statements in Code](how-to-break-and-combine-statements-in-code.md).</span></span>  
  
 <span data-ttu-id="13f80-121">Znak dwukropka ( `:` ) jest również używany do identyfikowania etykiety instrukcji.</span><span class="sxs-lookup"><span data-stu-id="13f80-121">The colon (`:`) character is also used to identify a statement label.</span></span> <span data-ttu-id="13f80-122">Aby uzyskać więcej informacji, zobacz [instrukcje: etykietowanie instrukcji](how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="13f80-122">For more information, see [How to: Label Statements](how-to-label-statements.md).</span></span>  
  
## <a name="concatenation"></a><span data-ttu-id="13f80-123">Łączenie</span><span class="sxs-lookup"><span data-stu-id="13f80-123">Concatenation</span></span>  
 <span data-ttu-id="13f80-124">Użyj `&` operatora do *łączenia*lub łączenia ciągów razem.</span><span class="sxs-lookup"><span data-stu-id="13f80-124">Use the `&` operator for *concatenation*, or linking strings together.</span></span> <span data-ttu-id="13f80-125">Nie należy mylić tego operatora z `+` operatorem, który dodaje razem wartości liczbowe.</span><span class="sxs-lookup"><span data-stu-id="13f80-125">Do not confuse it with the `+` operator, which adds together numeric values.</span></span> <span data-ttu-id="13f80-126">Jeśli używasz `+` operatora do łączenia podczas wykonywania operacji na wartościach liczbowych, możesz uzyskać nieprawidłowe wyniki.</span><span class="sxs-lookup"><span data-stu-id="13f80-126">If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results.</span></span> <span data-ttu-id="13f80-127">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="13f80-127">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 <span data-ttu-id="13f80-128">Po wykonaniu poprzedniego kodu wartością `resultA` jest 21,01, a wartością `resultB` jest "10,0111".</span><span class="sxs-lookup"><span data-stu-id="13f80-128">Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".</span></span>  
  
## <a name="member-access-operators"></a><span data-ttu-id="13f80-129">Operatory dostępu do elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="13f80-129">Member Access Operators</span></span>  
 <span data-ttu-id="13f80-130">Aby uzyskać dostęp do elementu członkowskiego typu, należy użyć operatora kropki ( `.` ) lub wykrzyknika ( `!` ) między nazwą typu a nazwą elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="13f80-130">To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.</span></span>  
  
### <a name="dot--operator"></a><span data-ttu-id="13f80-131">Kropka (.) Zakład</span><span class="sxs-lookup"><span data-stu-id="13f80-131">Dot (.) Operator</span></span>  
 <span data-ttu-id="13f80-132">Użyj `.` operatora dla klasy, struktury, interfejsu lub wyliczenia jako operatora dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="13f80-132">Use the `.` operator on a class, structure, interface, or enumeration as a member access operator.</span></span> <span data-ttu-id="13f80-133">Składową może być pole, właściwość, zdarzenie lub metoda.</span><span class="sxs-lookup"><span data-stu-id="13f80-133">The member can be a field, property, event, or method.</span></span> <span data-ttu-id="13f80-134">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="13f80-134">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a><span data-ttu-id="13f80-135">Wykrzyknik (!) Zakład</span><span class="sxs-lookup"><span data-stu-id="13f80-135">Exclamation Point (!) Operator</span></span>  
 <span data-ttu-id="13f80-136">Operatora należy używać `!` tylko w klasie lub interfejsie jako operator dostępu do słownika.</span><span class="sxs-lookup"><span data-stu-id="13f80-136">Use the `!` operator only on a class or interface as a dictionary access operator.</span></span> <span data-ttu-id="13f80-137">Klasa lub interfejs musi mieć właściwość domyślną, która akceptuje pojedynczy `String` argument.</span><span class="sxs-lookup"><span data-stu-id="13f80-137">The class or interface must have a default property that accepts a single `String` argument.</span></span> <span data-ttu-id="13f80-138">Identyfikator bezpośrednio po `!` operatorze będzie wartością argumentu przekazaną do domyślnej właściwości jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="13f80-138">The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string.</span></span> <span data-ttu-id="13f80-139">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="13f80-139">The following example demonstrates this.</span></span>  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 <span data-ttu-id="13f80-140">Trzy wiersze wyjściowe `MsgBox` wszystkich wyświetlają wartość `32856` .</span><span class="sxs-lookup"><span data-stu-id="13f80-140">The three output lines of `MsgBox` all display the value `32856`.</span></span> <span data-ttu-id="13f80-141">Pierwszy wiersz używa tradycyjnego dostępu do właściwości `index` , drugi korzysta z faktu, że `index` jest domyślną właściwością klasy `hasDefault` , a trzeci używa dostępu do słownika do klasy.</span><span class="sxs-lookup"><span data-stu-id="13f80-141">The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.</span></span>  
  
 <span data-ttu-id="13f80-142">Należy zauważyć, że drugi operand `!` operatora musi być prawidłowym identyfikatorem Visual Basic, który nie jest ujęty w znaki podwójnego cudzysłowu ( `" "` ).</span><span class="sxs-lookup"><span data-stu-id="13f80-142">Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`).</span></span> <span data-ttu-id="13f80-143">Innymi słowy, nie można użyć literału ciągu ani zmiennej ciągu.</span><span class="sxs-lookup"><span data-stu-id="13f80-143">In other words, you cannot use a string literal or string variable.</span></span> <span data-ttu-id="13f80-144">Następująca zmiana w ostatnim wierszu `MsgBox` wywołania powoduje wygenerowanie błędu, ponieważ `"X"` jest to ujęty w nawias literał ciągu.</span><span class="sxs-lookup"><span data-stu-id="13f80-144">The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.</span></span>  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> <span data-ttu-id="13f80-145">Odwołania do kolekcji domyślnych muszą być jawne.</span><span class="sxs-lookup"><span data-stu-id="13f80-145">References to default collections must be explicit.</span></span> <span data-ttu-id="13f80-146">W szczególności nie można używać `!` operatora na zmiennej z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="13f80-146">In particular, you cannot use the `!` operator on a late-bound variable.</span></span>  
  
 <span data-ttu-id="13f80-147">`!`Znak jest również używany jako `Single` znak typu.</span><span class="sxs-lookup"><span data-stu-id="13f80-147">The `!` character is also used as the `Single` type character.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13f80-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13f80-148">See also</span></span>

- [<span data-ttu-id="13f80-149">Struktura programu i konwencje związane z kodem</span><span class="sxs-lookup"><span data-stu-id="13f80-149">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="13f80-150">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="13f80-150">Type Characters</span></span>](../language-features/data-types/type-characters.md)
