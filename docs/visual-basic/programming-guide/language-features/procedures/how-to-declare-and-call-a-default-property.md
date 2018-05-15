---
title: 'Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- defaults [Visual Basic], properties
- properties [Visual Basic], default
- procedures [Visual Basic], defining
- default properties [Visual Basic], in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
ms.openlocfilehash: 7805ee4dcd4bad0d0624c97ccc25232e9bc31ba4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="8cc2b-102">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8cc2b-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="8cc2b-103">A *domyślna właściwość* jest właściwością klasy lub struktury kodu można uzyskać dostęp bez określania go.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="8cc2b-104">Podczas wywoływania kodu nazwy klasy lub struktury, ale nie właściwości i kontekst zezwala na dostęp do właściwości, Visual Basic rozpoznaje dostępu do tej klasy lub struktury domyślnej właściwości, jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="8cc2b-105">Klasy lub struktury może mieć co najwyżej jeden domyślny właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="8cc2b-106">Jednak można przeciążać właściwości domyślnej i więcej niż jedna wersja go.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="8cc2b-107">Aby uzyskać więcej informacji, zobacz [domyślne](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="8cc2b-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="8cc2b-108">Deklarowanie właściwości domyślne</span><span class="sxs-lookup"><span data-stu-id="8cc2b-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="8cc2b-109">Deklarowanie właściwości w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-109">Declare the property in the normal way.</span></span> <span data-ttu-id="8cc2b-110">Nie określaj `Shared` lub `Private` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="8cc2b-111">Obejmują `Default` — słowo kluczowe w deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="8cc2b-112">Określ co najmniej jeden parametr dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="8cc2b-113">Nie można zdefiniować domyślnej właściwości, które nie wymaga co najmniej jednego argumentu.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="8cc2b-114">Wywoływanie właściwości domyślne</span><span class="sxs-lookup"><span data-stu-id="8cc2b-114">To call a default property</span></span>  
  
1.  <span data-ttu-id="8cc2b-115">Deklarowanie zmiennej typu zawierającego klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]  
  
2.  <span data-ttu-id="8cc2b-116">Użyj nazwy zmiennej w wyrażeniu, w którym zwykle obejmuje nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]  
  
3.  <span data-ttu-id="8cc2b-117">Wykonaj nazwy zmiennej z listy argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="8cc2b-118">Domyślna właściwość musi mieć co najmniej jednego argumentu.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]  
  
4.  <span data-ttu-id="8cc2b-119">Można pobrać wartości właściwości domyślnej, użyj nazwy zmiennej, z listy argumentów w wyrażeniu lub po równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]  
  
5.  <span data-ttu-id="8cc2b-120">Aby ustawić wartość właściwości domyślnej, użyj nazwy zmiennej, z listy argumentów po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]  
  
6.  <span data-ttu-id="8cc2b-121">Zawsze można określić domyślną nazwę właściwości wraz z nazwą zmiennej, tak jak będzie można uzyskać dostępu do innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]  
  
## <a name="example"></a><span data-ttu-id="8cc2b-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="8cc2b-122">Example</span></span>  
 <span data-ttu-id="8cc2b-123">Poniższy przykład deklaruje właściwości domyślnej klasy.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]  
  
## <a name="example"></a><span data-ttu-id="8cc2b-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="8cc2b-124">Example</span></span>  
 <span data-ttu-id="8cc2b-125">W poniższym przykładzie pokazano sposób wywoływania domyślnej właściwości `myProperty` w klasie `class1`.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="8cc2b-126">Instrukcje przypisania trzy przechowywanie wartości w `myProperty`i <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> wywołania odczytuje wartości.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]  
  
 <span data-ttu-id="8cc2b-127">Najczęściej właściwości domyślnej jest <xref:Microsoft.VisualBasic.Collection.Item%2A> właściwości na różne klasy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8cc2b-128">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="8cc2b-128">Robust Programming</span></span>  
 <span data-ttu-id="8cc2b-129">Właściwości domyślnych może spowodować zmniejszenie małych znaków kodu źródłowego, ale może wprowadzić czytelność kodu.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="8cc2b-130">Jeśli kod wywołujący nie są zaznajomieni z klasy lub struktury, podczas wykonywania odwołanie do nazwy klasy lub struktury nie może być niektórych czy uzyskuje dostęp tego odwołania do klasy lub struktury, sam lub domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="8cc2b-131">Może to prowadzić do błędów kompilatora lub błędy niewielkie logiki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="8cc2b-132">Nieco zmniejsza ryzyko błędów właściwości domyślne przy użyciu zawsze [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) można ustawić typ kompilatora sprawdzania `On`.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="8cc2b-133">Jeśli planujesz użyć wstępnie zdefiniowanych klasy lub struktury w kodzie, należy określić, czy ma ona domyślnej właściwości, a jeśli tak, jakie jego nazwa jest.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="8cc2b-134">Z powodu niedogodności należy rozważyć nie definiuje właściwości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="8cc2b-135">Aby zwiększyć czytelność kodu należy również wziąć pod uwagę zawsze odwołujących się do wszystkich właściwości jawnie, nawet domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cc2b-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc2b-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8cc2b-136">See Also</span></span>  
 [<span data-ttu-id="8cc2b-137">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="8cc2b-137">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="8cc2b-138">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="8cc2b-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="8cc2b-139">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8cc2b-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="8cc2b-140">Default</span><span class="sxs-lookup"><span data-stu-id="8cc2b-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)  
 [<span data-ttu-id="8cc2b-141">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8cc2b-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="8cc2b-142">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="8cc2b-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="8cc2b-143">Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="8cc2b-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="8cc2b-144">Instrukcje: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="8cc2b-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="8cc2b-145">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="8cc2b-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="8cc2b-146">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="8cc2b-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
