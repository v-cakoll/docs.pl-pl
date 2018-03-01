---
title: "Set — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b18e6c858e64e78d7ab85fdaafd70e510f7a02f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="08987-102">Set — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08987-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="08987-103">Deklaruje `Set` procedury właściwości używane do przypisania wartości dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08987-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="08987-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="08987-105">Części</span><span class="sxs-lookup"><span data-stu-id="08987-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="08987-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08987-106">Optional.</span></span> <span data-ttu-id="08987-107">Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="08987-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="08987-108">Opcjonalnie na maksymalnie jeden `Get` i `Set` instrukcje w tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="08987-109">Może to być jedna z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="08987-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="08987-110">Chronione</span><span class="sxs-lookup"><span data-stu-id="08987-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [<span data-ttu-id="08987-111">Friend</span><span class="sxs-lookup"><span data-stu-id="08987-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [<span data-ttu-id="08987-112">Prywatne</span><span class="sxs-lookup"><span data-stu-id="08987-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 <span data-ttu-id="08987-113">Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="08987-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="08987-114">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="08987-114">Required.</span></span> <span data-ttu-id="08987-115">Parametr zawierający nową wartość dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="08987-116">Jeśli wymagane `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="08987-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="08987-117">Typ danych `value` parametru.</span><span class="sxs-lookup"><span data-stu-id="08987-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="08987-118">Określony typ danych musi być taki sam jak typ danych właściwości gdzie to `Set` zadeklarowano instrukcji.</span><span class="sxs-lookup"><span data-stu-id="08987-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="08987-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="08987-119">Optional.</span></span> <span data-ttu-id="08987-120">Co najmniej jeden instrukcji, które podczas uruchamiania `Set` właściwości procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="08987-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="08987-121">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="08987-121">Required.</span></span> <span data-ttu-id="08987-122">Kończy definicję `Set` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08987-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="08987-123">Remarks</span></span>  
 <span data-ttu-id="08987-124">Dla każdej właściwości musi mieć `Set` procedury właściwości, chyba że właściwość jest oznaczona jako `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="08987-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="08987-125">`Set` Procedura służy do ustawiania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="08987-126">Visual Basic automatycznie wywołuje właściwość `Set` procedury w przypadku instrukcji przypisania udostępnia wartość jest przechowywana we właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="08987-127">Visual Basic przekazuje parametr `Set` procedury podczas przypisania właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="08987-128">Jeśli nie podasz parametru `Set`, zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value`.</span><span class="sxs-lookup"><span data-stu-id="08987-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="08987-129">Parametr zawiera wartość do przypisania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="08987-130">Zazwyczaj przechowywać tę wartość w zmiennej lokalnej prywatnych i przywrócić go przy każdym `Get` procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="08987-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="08987-131">Treść deklaracja właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="08987-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="08987-132">Nie można zapisać żadnych innych niż te procedury.</span><span class="sxs-lookup"><span data-stu-id="08987-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="08987-133">W szczególności go nie można zapisać bieżącą wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="08987-134">Ta wartość poza właściwości, muszą być przechowywane, ponieważ Jeśli przechowujesz wewnątrz jednej z właściwości procedur procedurę właściwości nie można do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="08987-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="08987-135">Jest zwykle podejście do przechowywania wartości [prywatnej](../../../visual-basic/language-reference/modifiers/private.md) zadeklarować zmiennej na tym samym poziomie jako wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="08987-136">Należy zdefiniować `Set` procedurę wewnątrz właściwości, której dotyczy.</span><span class="sxs-lookup"><span data-stu-id="08987-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="08987-137">`Set` Procedury Domyślnie poziom dostępu do jego właściwości zawierającego tylko w przypadku `accessmodifier` w `Set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="08987-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="08987-138">Reguły</span><span class="sxs-lookup"><span data-stu-id="08987-138">Rules</span></span>  
  
-   <span data-ttu-id="08987-139">**Mieszanymi poziomami dostępu.**</span><span class="sxs-lookup"><span data-stu-id="08987-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="08987-140">Jeśli definiujesz właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu różnych jednego `Get` lub `Set` procedura, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="08987-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="08987-141">Jeśli to zrobisz, poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="08987-142">Na przykład, jeśli właściwość jest zadeklarowany jako `Friend`, mogą zadeklarować `Set` procedury `Private`, ale nie `Public`.</span><span class="sxs-lookup"><span data-stu-id="08987-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="08987-143">Jeśli definiujesz `WriteOnly` właściwość `Set` procedury reprezentuje cały właściwość.</span><span class="sxs-lookup"><span data-stu-id="08987-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="08987-144">Nie można zadeklarować poziom dostępu różnych `Set`, ponieważ który ustawiał dwa poziomy dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="08987-145">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="08987-145">Behavior</span></span>  
  
-   <span data-ttu-id="08987-146">**Zwracanie z procedury właściwości.**</span><span class="sxs-lookup"><span data-stu-id="08987-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="08987-147">Gdy `Set` procedura zwraca do kodu wywołującego, wykonanie jest kontynuowane po instrukcji, która podane wartości, które mają być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="08987-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="08987-148">`Set`procedury własności może zwrócić przy użyciu [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md) lub [instrukcji Zakończ](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="08987-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="08987-149">`Exit Property` i `Return` instrukcje spowodować natychmiastowe wyjścia z procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="08987-150">Dowolną liczbę `Exit Property` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Property` i `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="08987-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08987-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="08987-151">Example</span></span>  
 <span data-ttu-id="08987-152">W poniższym przykładzie użyto `Set` instrukcji można ustawić wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="08987-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="08987-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="08987-153">See Also</span></span>  
 [<span data-ttu-id="08987-154">Get — instrukcja</span><span class="sxs-lookup"><span data-stu-id="08987-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="08987-155">Property — instrukcja</span><span class="sxs-lookup"><span data-stu-id="08987-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="08987-156">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="08987-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="08987-157">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="08987-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
