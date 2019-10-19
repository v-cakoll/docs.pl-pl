---
title: Set — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583240"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="3326c-102">Set — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3326c-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="3326c-103">Deklaruje procedurę właściwości `Set` służącą do przypisywania wartości do właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3326c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3326c-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="3326c-105">Części</span><span class="sxs-lookup"><span data-stu-id="3326c-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="3326c-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3326c-106">Optional.</span></span> <span data-ttu-id="3326c-107">Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="3326c-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="3326c-108">Opcjonalne dla co najwyżej jednej instrukcji `Get` i `Set` w tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="3326c-109">Może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="3326c-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="3326c-110">Protected</span><span class="sxs-lookup"><span data-stu-id="3326c-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="3326c-111">Friend</span><span class="sxs-lookup"><span data-stu-id="3326c-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="3326c-112">Private</span><span class="sxs-lookup"><span data-stu-id="3326c-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="3326c-113">Zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3326c-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="3326c-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3326c-114">Required.</span></span> <span data-ttu-id="3326c-115">Parametr zawierający nową wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="3326c-116">Wymagane, jeśli `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="3326c-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="3326c-117">Typ danych parametru `value`.</span><span class="sxs-lookup"><span data-stu-id="3326c-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="3326c-118">Określony typ danych musi być taki sam jak typ danych właściwości, w której jest zadeklarowana ta instrukcja `Set`.</span><span class="sxs-lookup"><span data-stu-id="3326c-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="3326c-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="3326c-119">Optional.</span></span> <span data-ttu-id="3326c-120">Jedna lub więcej instrukcji, które są uruchamiane po wywołaniu procedury `Set` właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="3326c-121">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="3326c-121">Required.</span></span> <span data-ttu-id="3326c-122">Kończy definicję procedury `Set` właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3326c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3326c-123">Remarks</span></span>  
 <span data-ttu-id="3326c-124">Każda właściwość musi mieć procedurę właściwości `Set`, chyba że właściwość jest oznaczona `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="3326c-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="3326c-125">Procedura `Set` służy do ustawiania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="3326c-126">Visual Basic automatycznie wywołuje procedurę `Set` właściwości, gdy instrukcja przypisania dostarcza wartość, która ma być przechowywana we właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="3326c-127">Visual Basic przekazuje parametr do procedury `Set` podczas przypisywania właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="3326c-128">Jeśli nie podasz parametru dla `Set`, zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value`.</span><span class="sxs-lookup"><span data-stu-id="3326c-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="3326c-129">Parametr zawiera wartość, która ma zostać przypisana do właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="3326c-130">Zwykle ta wartość jest przechowywana w prywatnej zmiennej lokalnej i zwracana przy każdym wywołaniu procedury `Get`.</span><span class="sxs-lookup"><span data-stu-id="3326c-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="3326c-131">Treść deklaracji właściwości może zawierać tylko `Get` i `Set` procedur między [instrukcją właściwości](../../../visual-basic/language-reference/statements/property-statement.md) i instrukcją `End Property`.</span><span class="sxs-lookup"><span data-stu-id="3326c-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="3326c-132">Nie może on przechowywać żadnych elementów innych niż te procedury.</span><span class="sxs-lookup"><span data-stu-id="3326c-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="3326c-133">W szczególności nie można zapisać bieżącej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="3326c-134">Ta wartość musi być przechowywana poza właściwością, ponieważ w przypadku przechowywania jej w ramach jednej z procedur dotyczących właściwości inna procedura właściwości nie będzie mogła uzyskać do niej dostępu.</span><span class="sxs-lookup"><span data-stu-id="3326c-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="3326c-135">Typowym podejściem jest przechowywanie wartości w zmiennej [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) zadeklarowanej na tym samym poziomie co właściwość.</span><span class="sxs-lookup"><span data-stu-id="3326c-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="3326c-136">Należy zdefiniować `Set` procedury wewnątrz właściwości, do której ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="3326c-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="3326c-137">Procedura `Set` domyślnie jest poziomem dostępu właściwości zawierającego, chyba że w instrukcji `Set` użyto `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="3326c-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="3326c-138">Przepisy</span><span class="sxs-lookup"><span data-stu-id="3326c-138">Rules</span></span>  
  
- <span data-ttu-id="3326c-139">**Mieszane poziomy dostępu.**</span><span class="sxs-lookup"><span data-stu-id="3326c-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="3326c-140">W przypadku definiowania właściwości do odczytu i zapisu można opcjonalnie określić inny poziom dostępu dla `Get` lub procedury `Set`, ale nie dla obu tych opcji.</span><span class="sxs-lookup"><span data-stu-id="3326c-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="3326c-141">W takim przypadku poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="3326c-142">Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować procedurę `Set` `Private`, ale nie `Public`.</span><span class="sxs-lookup"><span data-stu-id="3326c-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="3326c-143">Jeśli definiujesz Właściwość `WriteOnly`, procedura `Set` reprezentuje całą właściwość.</span><span class="sxs-lookup"><span data-stu-id="3326c-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="3326c-144">Nie można zadeklarować innego poziomu dostępu dla `Set`, ponieważ spowodowałoby to ustawienie dwóch poziomów dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="3326c-145">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="3326c-145">Behavior</span></span>  
  
- <span data-ttu-id="3326c-146">**Powrót z procedury właściwości.**</span><span class="sxs-lookup"><span data-stu-id="3326c-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="3326c-147">Gdy procedura `Set` zwraca kod wywołujący, wykonanie kontynuuje się po instrukcji, która dostarczyła wartość do zapisania.</span><span class="sxs-lookup"><span data-stu-id="3326c-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="3326c-148">procedury właściwości `Set` mogą być zwracane przy użyciu [instrukcji return](../../../visual-basic/language-reference/statements/return-statement.md) lub [instrukcji Exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3326c-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="3326c-149">Instrukcje `Exit Property` i `Return` powodują natychmiastowe wyjście z procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="3326c-150">Dowolna liczba instrukcji `Exit Property` i `Return` może występować w dowolnym miejscu procedury i można mieszać instrukcje `Exit Property` i `Return`.</span><span class="sxs-lookup"><span data-stu-id="3326c-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3326c-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="3326c-151">Example</span></span>  
 <span data-ttu-id="3326c-152">Poniższy przykład używa instrukcji `Set`, aby ustawić wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="3326c-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="3326c-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3326c-153">See also</span></span>

- [<span data-ttu-id="3326c-154">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3326c-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="3326c-155">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3326c-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="3326c-156">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3326c-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="3326c-157">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="3326c-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
