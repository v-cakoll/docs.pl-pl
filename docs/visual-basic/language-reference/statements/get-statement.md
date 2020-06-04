---
title: Get — Instrukcja
ms.date: 07/20/2015
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
ms.openlocfilehash: 31936fb2c8f658203a43702a2b5fa4ee2481beb5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404605"
---
# <a name="get-statement"></a><span data-ttu-id="cb56c-102">Get — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cb56c-102">Get Statement</span></span>
<span data-ttu-id="cb56c-103">Deklaruje `Get` procedurę właściwości używaną do pobrania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb56c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb56c-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="cb56c-105">Części</span><span class="sxs-lookup"><span data-stu-id="cb56c-105">Parts</span></span>  
  
|<span data-ttu-id="cb56c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="cb56c-106">Term</span></span>|<span data-ttu-id="cb56c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="cb56c-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="cb56c-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cb56c-108">Optional.</span></span> <span data-ttu-id="cb56c-109">Zobacz [listę atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="cb56c-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="cb56c-110">Opcjonalne dla co najwyżej jednej `Get` instrukcji i `Set` w tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="cb56c-111">Może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="cb56c-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="cb56c-112">-   [Chronione](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="cb56c-112">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="cb56c-113">-   [Osoby](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="cb56c-113">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="cb56c-114">-   [Użytek](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="cb56c-114">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="cb56c-115">Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="cb56c-115">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="cb56c-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cb56c-116">Optional.</span></span> <span data-ttu-id="cb56c-117">Jedna lub więcej instrukcji, które są uruchamiane, gdy `Get` wywoływana jest procedura właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="cb56c-118">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cb56c-118">Required.</span></span> <span data-ttu-id="cb56c-119">Kończy definicję `Get` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb56c-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb56c-120">Remarks</span></span>  
 <span data-ttu-id="cb56c-121">Każda właściwość musi mieć `Get` procedurę właściwości, chyba że właściwość jest oznaczona `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="cb56c-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="cb56c-122">`Get`Procedura służy do zwracania bieżącej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="cb56c-123">Visual Basic automatycznie wywołuje procedurę właściwości, `Get` gdy wyrażenie żąda wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="cb56c-124">Treść deklaracji właściwości może zawierać tylko właściwości `Get` i `Set` procedury między [instrukcją właściwości](property-statement.md) a `End Property` instrukcją.</span><span class="sxs-lookup"><span data-stu-id="cb56c-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="cb56c-125">Nie może on przechowywać żadnych elementów innych niż te procedury.</span><span class="sxs-lookup"><span data-stu-id="cb56c-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="cb56c-126">W szczególności nie można zapisać bieżącej wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="cb56c-127">Ta wartość musi być przechowywana poza właściwością, ponieważ w przypadku przechowywania jej w ramach jednej z procedur dotyczących właściwości inna procedura właściwości nie będzie mogła uzyskać do niej dostępu.</span><span class="sxs-lookup"><span data-stu-id="cb56c-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="cb56c-128">Typowym podejściem jest przechowywanie wartości w zmiennej [prywatnej](../modifiers/private.md) zadeklarowanej na tym samym poziomie co właściwość.</span><span class="sxs-lookup"><span data-stu-id="cb56c-128">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="cb56c-129">Należy zdefiniować `Get` procedurę wewnątrz właściwości, do której ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="cb56c-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="cb56c-130">`Get`Procedura jest domyślnie ustawiona na poziom dostępu właściwości zawierającej, chyba że zostanie użyta `accessmodifier` `Get` instrukcja w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="cb56c-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="cb56c-131">Reguły</span><span class="sxs-lookup"><span data-stu-id="cb56c-131">Rules</span></span>  
  
- <span data-ttu-id="cb56c-132">**Mieszane poziomy dostępu.**</span><span class="sxs-lookup"><span data-stu-id="cb56c-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="cb56c-133">W przypadku definiowania właściwości do odczytu i zapisu można opcjonalnie określić inny poziom dostępu dla `Get` lub `Set` procedury, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="cb56c-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="cb56c-134">W takim przypadku poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="cb56c-135">Na przykład, jeśli właściwość jest zadeklarowana `Friend` , można zadeklarować `Get` procedurę `Private` , ale nie `Public` .</span><span class="sxs-lookup"><span data-stu-id="cb56c-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="cb56c-136">W przypadku definiowania `ReadOnly` właściwości `Get` procedura reprezentuje całą właściwość.</span><span class="sxs-lookup"><span data-stu-id="cb56c-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="cb56c-137">Nie można zadeklarować innego poziomu dostępu dla `Get` , ponieważ spowodowałoby to ustawienie dwóch poziomów dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="cb56c-138">**Typ zwracany.**</span><span class="sxs-lookup"><span data-stu-id="cb56c-138">**Return Type.**</span></span> <span data-ttu-id="cb56c-139">[Instrukcja Property](property-statement.md) może deklarować typ danych zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-139">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="cb56c-140">`Get`Procedura automatycznie zwraca ten typ danych.</span><span class="sxs-lookup"><span data-stu-id="cb56c-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="cb56c-141">Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="cb56c-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="cb56c-142">Jeśli instrukcja nie zostanie `Property` określona `returntype` , procedura zwraca wartość `Object` .</span><span class="sxs-lookup"><span data-stu-id="cb56c-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cb56c-143">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="cb56c-143">Behavior</span></span>  
  
- <span data-ttu-id="cb56c-144">**Powrót z procedury.**</span><span class="sxs-lookup"><span data-stu-id="cb56c-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="cb56c-145">Gdy `Get` procedura zwraca kod wywołujący, wykonywanie jest kontynuowane w instrukcji, która zażądała wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="cb56c-146">`Get`procedury właściwości mogą zwracać wartość przy użyciu [instrukcji return](return-statement.md) lub przez przypisanie wartości zwracanej do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-146">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="cb56c-147">Aby uzyskać więcej informacji, zobacz "wartość zwracana" w [instrukcji funkcji](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cb56c-147">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="cb56c-148">`Exit Property`Instrukcje i `Return` powodują natychmiastowe wyjście z procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="cb56c-149">Dowolna liczba `Exit Property` `Return` instrukcji i może występować w dowolnym miejscu procedury i można mieszać i wypełniać `Exit Property` `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="cb56c-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="cb56c-150">**Wartość zwracana.**</span><span class="sxs-lookup"><span data-stu-id="cb56c-150">**Return Value.**</span></span> <span data-ttu-id="cb56c-151">Aby zwrócić wartość z `Get` procedury, można przypisać wartość do nazwy właściwości lub dołączyć ją do [instrukcji return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cb56c-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="cb56c-152">`Return`Instrukcja równocześnie przypisuje `Get` wartość zwracaną przez procedurę i kończy procedurę.</span><span class="sxs-lookup"><span data-stu-id="cb56c-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="cb56c-153">Jeśli używasz `Exit Property` bez przypisywania wartości do nazwy właściwości, `Get` procedura zwraca wartość domyślną dla typu danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="cb56c-154">Aby uzyskać więcej informacji, zobacz "wartość zwracana" w [instrukcji funkcji](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="cb56c-154">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="cb56c-155">Poniższy przykład ilustruje dwa sposoby, gdy właściwość tylko do odczytu `quoteForTheDay` może zwracać wartość przechowywaną w zmiennej prywatnej `quoteValue` .</span><span class="sxs-lookup"><span data-stu-id="cb56c-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="cb56c-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb56c-156">Example</span></span>  
 <span data-ttu-id="cb56c-157">Poniższy przykład używa instrukcji, `Get` Aby zwrócić wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb56c-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="cb56c-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb56c-158">See also</span></span>

- [<span data-ttu-id="cb56c-159">Set — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cb56c-159">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="cb56c-160">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="cb56c-160">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="cb56c-161">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="cb56c-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="cb56c-162">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="cb56c-162">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="cb56c-163">Wskazówki: definiowanie klas</span><span class="sxs-lookup"><span data-stu-id="cb56c-163">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
