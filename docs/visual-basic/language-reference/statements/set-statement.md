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
ms.openlocfilehash: 0a8d95ffbabf03a0e6c9d88edb28c248b60f3252
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783880"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="43093-102">Set — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43093-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="43093-103">Deklaruje `Set` procedury właściwości używane do przypisywania wartości do właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43093-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43093-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="43093-105">Części</span><span class="sxs-lookup"><span data-stu-id="43093-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="43093-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="43093-106">Optional.</span></span> <span data-ttu-id="43093-107">Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="43093-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="43093-108">Opcjonalnie na co najwyżej jeden z `Get` i `Set` instrukcje w tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="43093-109">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="43093-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="43093-110">Protected</span><span class="sxs-lookup"><span data-stu-id="43093-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="43093-111">Friend</span><span class="sxs-lookup"><span data-stu-id="43093-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="43093-112">Private</span><span class="sxs-lookup"><span data-stu-id="43093-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="43093-113">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="43093-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="43093-114">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="43093-114">Required.</span></span> <span data-ttu-id="43093-115">Parametr zawierający nową wartość dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="43093-116">Jeśli wymagane `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="43093-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="43093-117">Typ danych `value` parametru.</span><span class="sxs-lookup"><span data-stu-id="43093-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="43093-118">Określony typ danych musi być taki sam jak typ danych właściwości gdzie to `Set` instrukcji jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="43093-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="43093-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="43093-119">Optional.</span></span> <span data-ttu-id="43093-120">Jedna lub więcej instrukcji, które są uruchamiane podczas `Set` nosi nazwę procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="43093-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="43093-121">Required.</span></span> <span data-ttu-id="43093-122">Kończy definicję `Set` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43093-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43093-123">Remarks</span></span>  
 <span data-ttu-id="43093-124">Dla każdej właściwości musi mieć `Set` procedury właściwości, chyba że właściwość jest oznaczona `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="43093-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="43093-125">`Set` Procedura służy do ustawiania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="43093-126">Visual Basic automatycznie wywołuje właściwość `Set` procedury w przypadku instrukcji przypisania udostępnia wartość jest przechowywana we właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="43093-127">Visual Basic przekazuje parametr `Set` procedury podczas przypisania właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="43093-128">Jeśli parametr nie zostanie podana `Set`, zintegrowanego środowiska programistycznego (IDE) korzysta z niejawny parametr o nazwie `value`.</span><span class="sxs-lookup"><span data-stu-id="43093-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="43093-129">Parametr przechowuje wartość do przypisania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="43093-130">Zazwyczaj przechowywać tę wartość w zmiennej lokalnej prywatne i przywrócić go zawsze wtedy, gdy `Get` procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="43093-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="43093-131">Treść deklaracja właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43093-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="43093-132">Nie można zapisać coś innego niż te procedury.</span><span class="sxs-lookup"><span data-stu-id="43093-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="43093-133">W szczególności go nie można zapisać bieżącą wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="43093-134">Ta wartość poza właściwości, muszą być przechowywane, ponieważ jeśli będą przechowywane w jednej z procedur właściwość, inne procedury właściwości nie można uzyskać do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="43093-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="43093-135">Zwykle rozwiązaniem jest wartość jest przechowywana w [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) Zmienna zadeklarowana na tym samym poziomie jak właściwość.</span><span class="sxs-lookup"><span data-stu-id="43093-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="43093-136">Należy zdefiniować `Set` procedury właściwości, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="43093-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="43093-137">`Set` Procedury wartość domyślna to poziom dostępu do jego zawierającą je właściwość, chyba że używasz `accessmodifier` w `Set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43093-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="43093-138">reguły</span><span class="sxs-lookup"><span data-stu-id="43093-138">Rules</span></span>  
  
- <span data-ttu-id="43093-139">**Mieszanymi poziomami dostępu.**</span><span class="sxs-lookup"><span data-stu-id="43093-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="43093-140">Jeśli zamierzasz zdefiniować właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu do różnych dla dowolnego `Get` lub `Set` procedury, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="43093-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="43093-141">Jeśli to zrobisz, procedura poziom dostępu musi być bardziej restrykcyjny niż poziom dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="43093-142">Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować `Set` procedury `Private`, ale nie `Public`.</span><span class="sxs-lookup"><span data-stu-id="43093-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="43093-143">Jeśli definiujesz `WriteOnly` właściwości `Set` procedury reprezentuje cały właściwość.</span><span class="sxs-lookup"><span data-stu-id="43093-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="43093-144">Nie można zadeklarować dostęp inny poziom `Set`, ponieważ, ustawić dwa poziomy dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="43093-145">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="43093-145">Behavior</span></span>  
  
- <span data-ttu-id="43093-146">**Zwracanie z procedury właściwości.**</span><span class="sxs-lookup"><span data-stu-id="43093-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="43093-147">Gdy `Set` procedury zwraca do kodu wywołującego, wykonywanie jest kontynuowane po instrukcji, która podano wartość, która ma być przechowywany.</span><span class="sxs-lookup"><span data-stu-id="43093-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="43093-148">`Set` procedury własności może zwrócić przy użyciu [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md) lub [instrukcji zakończenia](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="43093-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="43093-149">`Exit Property` i `Return` instrukcji powodują natychmiastowego wyjścia z procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="43093-150">Dowolną liczbę `Exit Property` i `Return` instrukcji może występować w dowolnym miejscu w ramach procedury i możesz mieszać `Exit Property` i `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43093-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43093-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="43093-151">Example</span></span>  
 <span data-ttu-id="43093-152">W poniższym przykładzie użyto `Set` instrukcję, aby ustawić wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="43093-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="43093-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43093-153">See also</span></span>

- [<span data-ttu-id="43093-154">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="43093-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="43093-155">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="43093-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="43093-156">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="43093-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="43093-157">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="43093-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
