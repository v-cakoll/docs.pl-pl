---
title: "Get — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1ff062a5e3bf41794bd5b4c90f1e188d6d97480
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="get-statement"></a><span data-ttu-id="6e3e4-102">Get — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e3e4-102">Get Statement</span></span>
<span data-ttu-id="6e3e4-103">Deklaruje `Get` procedury właściwości używane do pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e3e4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e3e4-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="6e3e4-105">Części</span><span class="sxs-lookup"><span data-stu-id="6e3e4-105">Parts</span></span>  
  
|<span data-ttu-id="6e3e4-106">Termin</span><span class="sxs-lookup"><span data-stu-id="6e3e4-106">Term</span></span>|<span data-ttu-id="6e3e4-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="6e3e4-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="6e3e4-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-108">Optional.</span></span> <span data-ttu-id="6e3e4-109">Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="6e3e4-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="6e3e4-110">Opcjonalnie na maksymalnie jeden `Get` i `Set` instrukcje w tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="6e3e4-111">Może to być jedna z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6e3e4-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="6e3e4-112">-   [Chronione](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="6e3e4-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="6e3e4-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="6e3e4-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="6e3e4-114">-   [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="6e3e4-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="6e3e4-115">Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6e3e4-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="6e3e4-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-116">Optional.</span></span> <span data-ttu-id="6e3e4-117">Co najmniej jeden instrukcji, które podczas uruchamiania `Get` właściwości procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="6e3e4-118">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-118">Required.</span></span> <span data-ttu-id="6e3e4-119">Kończy definicję `Get` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e3e4-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e3e4-120">Remarks</span></span>  
 <span data-ttu-id="6e3e4-121">Dla każdej właściwości musi mieć `Get` procedury właściwości, chyba że właściwość jest oznaczona jako `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="6e3e4-122">`Get` Procedura służy do zwracania bieżącej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="6e3e4-123">Visual Basic automatycznie wywołuje właściwość `Get` procedury, gdy wartość właściwości zażąda wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="6e3e4-124">Treść deklaracja właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="6e3e4-125">Nie można zapisać żadnych innych niż te procedury.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="6e3e4-126">W szczególności go nie można zapisać bieżącą wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="6e3e4-127">Ta wartość poza właściwości, muszą być przechowywane, ponieważ Jeśli przechowujesz wewnątrz jednej z właściwości procedur procedurę właściwości nie można do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="6e3e4-128">Jest zwykle podejście do przechowywania wartości [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) zadeklarować zmiennej na tym samym poziomie jako wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="6e3e4-129">Należy zdefiniować `Get` procedurę wewnątrz właściwości, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="6e3e4-130">`Get` Procedury Domyślnie poziom dostępu do jego właściwości zawierającego tylko w przypadku `accessmodifier` w `Get` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6e3e4-131">Reguły</span><span class="sxs-lookup"><span data-stu-id="6e3e4-131">Rules</span></span>  
  
-   <span data-ttu-id="6e3e4-132">**Mieszanymi poziomami dostępu.**</span><span class="sxs-lookup"><span data-stu-id="6e3e4-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="6e3e4-133">Jeśli definiujesz właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu różnych jednego `Get` lub `Set` procedura, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="6e3e4-134">Jeśli to zrobisz, poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="6e3e4-135">Na przykład, jeśli właściwość jest zadeklarowany jako `Friend`, mogą zadeklarować `Get` procedury `Private`, ale nie `Public`.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="6e3e4-136">Jeśli definiujesz `ReadOnly` właściwość `Get` procedury reprezentuje cały właściwość.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="6e3e4-137">Nie można zadeklarować poziom dostępu różnych `Get`, ponieważ który ustawiał dwa poziomy dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="6e3e4-138">**Typ zwracany.**</span><span class="sxs-lookup"><span data-stu-id="6e3e4-138">**Return Type.**</span></span> <span data-ttu-id="6e3e4-139">[Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md) można zadeklarować typu danych zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="6e3e4-140">`Get` Procedury automatycznie zwraca typ danych.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="6e3e4-141">Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="6e3e4-142">Jeśli `Property` instrukcji nie określa `returntype`, zwraca procedury `Object`.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6e3e4-143">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="6e3e4-143">Behavior</span></span>  
  
-   <span data-ttu-id="6e3e4-144">**Zwracanie z procedury.**</span><span class="sxs-lookup"><span data-stu-id="6e3e4-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="6e3e4-145">Gdy `Get` procedura zwraca do kodu wywołującego, wykonanie jest kontynuowane w instrukcji, która żądanej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="6e3e4-146">`Get`procedury własności może zwracać wartości przy użyciu [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md) lub wartości zwracanej nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="6e3e4-147">Aby uzyskać więcej informacji, zobacz "Zwraca wartość" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6e3e4-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="6e3e4-148">`Exit Property` i `Return` instrukcje spowodować natychmiastowe wyjścia z procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="6e3e4-149">Dowolną liczbę `Exit Property` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Property` i `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="6e3e4-150">**Wartość zwracana.**</span><span class="sxs-lookup"><span data-stu-id="6e3e4-150">**Return Value.**</span></span> <span data-ttu-id="6e3e4-151">Zwraca wartość z `Get` procedury, można przypisać wartości do nazwy właściwości lub dołączyć go w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6e3e4-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="6e3e4-152">`Return` Instrukcja jednocześnie przypisuje `Get` procedura zwraca wartość i kończy procedurę.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="6e3e4-153">Jeśli używasz `Exit Property` bez przypisywanie wartości do nazwy właściwości `Get` procedury zwraca wartość domyślna dla typu danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="6e3e4-154">Aby uzyskać więcej informacji, zobacz "Zwraca wartość" w [instrukcji Function](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6e3e4-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="6e3e4-155">Poniższy przykład przedstawia dwa sposoby właściwości tylko do odczytu `quoteForTheDay` może zwrócić wartość przechowywana w zmiennej prywatnej `quoteValue`.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="6e3e4-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e3e4-156">Example</span></span>  
 <span data-ttu-id="6e3e4-157">W poniższym przykładzie użyto `Get` instrukcji, aby zwrócić wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="6e3e4-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6e3e4-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e3e4-158">See Also</span></span>  
 [<span data-ttu-id="6e3e4-159">Set — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e3e4-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="6e3e4-160">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e3e4-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="6e3e4-161">Exit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="6e3e4-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="6e3e4-162">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="6e3e4-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="6e3e4-163">Wskazówki: Definiowanie klas</span><span class="sxs-lookup"><span data-stu-id="6e3e4-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
