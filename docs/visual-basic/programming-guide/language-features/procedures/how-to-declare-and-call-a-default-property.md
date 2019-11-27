---
title: 'Instrukcje: deklarowanie i wywoływanie właściwości domyślnej'
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
ms.openlocfilehash: b01188ed8a9ff4da95a6975dcac3509625fdffb2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349680"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="f6302-102">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6302-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="f6302-103">*Właściwość domyślna* jest klasą lub właściwością struktury, do której Twój kod może uzyskać dostęp bez określania go.</span><span class="sxs-lookup"><span data-stu-id="f6302-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="f6302-104">Podczas wywoływania nazw kodu klasy lub struktury, ale nie do właściwości, a kontekst umożliwia dostęp do właściwości, Visual Basic rozpoznaje dostęp do tej klasy lub domyślnej właściwości tej struktury, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="f6302-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="f6302-105">Klasa lub struktura może mieć co najwyżej jedną właściwość domyślną.</span><span class="sxs-lookup"><span data-stu-id="f6302-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="f6302-106">Można jednak przeciążyć właściwość domyślną i mieć więcej niż jedną wersję.</span><span class="sxs-lookup"><span data-stu-id="f6302-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="f6302-107">Aby uzyskać więcej informacji, zobacz [domyślne](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="f6302-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="f6302-108">Aby zadeklarować właściwość domyślną</span><span class="sxs-lookup"><span data-stu-id="f6302-108">To declare a default property</span></span>  
  
1. <span data-ttu-id="f6302-109">Zadeklaruj właściwość w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="f6302-109">Declare the property in the normal way.</span></span> <span data-ttu-id="f6302-110">Nie określaj słowa kluczowego `Shared` ani `Private`.</span><span class="sxs-lookup"><span data-stu-id="f6302-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2. <span data-ttu-id="f6302-111">Uwzględnij słowo kluczowe `Default` w deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="f6302-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3. <span data-ttu-id="f6302-112">Określ co najmniej jeden parametr właściwości.</span><span class="sxs-lookup"><span data-stu-id="f6302-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="f6302-113">Nie można zdefiniować właściwości domyślnej, która nie przyjmuje co najmniej jednego argumentu.</span><span class="sxs-lookup"><span data-stu-id="f6302-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="f6302-114">Aby wywołać właściwość domyślną</span><span class="sxs-lookup"><span data-stu-id="f6302-114">To call a default property</span></span>  
  
1. <span data-ttu-id="f6302-115">Zadeklaruj zmienną zawierającą typ klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="f6302-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2. <span data-ttu-id="f6302-116">Użyj samej nazwy zmiennej w wyrażeniu, gdzie zwykle zawiera nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="f6302-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="f6302-117">Postępuj według nazwy zmiennej z listą argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="f6302-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="f6302-118">Właściwość domyślna musi mieć co najmniej jeden argument.</span><span class="sxs-lookup"><span data-stu-id="f6302-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4. <span data-ttu-id="f6302-119">Aby pobrać wartość domyślną właściwości, użyj nazwy zmiennej z listą argumentów w wyrażeniu lub po znaku równości (`=`) w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="f6302-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5. <span data-ttu-id="f6302-120">Aby ustawić domyślną wartość właściwości, użyj nazwy zmiennej z listą argumentów po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="f6302-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6. <span data-ttu-id="f6302-121">Można zawsze określić domyślną nazwę właściwości wraz z nazwą zmiennej, tak jak w przypadku uzyskania dostępu do innej właściwości.</span><span class="sxs-lookup"><span data-stu-id="f6302-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="f6302-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6302-122">Example</span></span>  
 <span data-ttu-id="f6302-123">Poniższy przykład deklaruje właściwość domyślną klasy.</span><span class="sxs-lookup"><span data-stu-id="f6302-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="f6302-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6302-124">Example</span></span>  
 <span data-ttu-id="f6302-125">Poniższy przykład ilustruje sposób wywołania właściwości domyślnej `myProperty` w klasie `class1`.</span><span class="sxs-lookup"><span data-stu-id="f6302-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="f6302-126">Trzy instrukcje przypisania przechowują wartości w `myProperty`, a wywołanie <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> odczytuje wartości.</span><span class="sxs-lookup"><span data-stu-id="f6302-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="f6302-127">Najbardziej typowym zastosowaniem właściwości domyślnej jest właściwość <xref:Microsoft.VisualBasic.Collection.Item%2A> w różnych klasach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="f6302-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f6302-128">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="f6302-128">Robust Programming</span></span>  
 <span data-ttu-id="f6302-129">Właściwości domyślne mogą spowodować niewielkie zmniejszenie kodu źródłowego, ale może to utrudnić odczytywanie kodu.</span><span class="sxs-lookup"><span data-stu-id="f6302-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="f6302-130">Jeśli kod wywołujący nie jest zaznajomiony z klasą lub strukturą, gdy tworzy odwołanie do nazwy klasy lub struktury, nie można określić, czy odwołanie uzyskuje dostęp do samej klasy lub struktury, czy też do właściwości domyślnej.</span><span class="sxs-lookup"><span data-stu-id="f6302-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="f6302-131">Może to prowadzić do błędów kompilatora lub niewielkich błędów logiki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f6302-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="f6302-132">Możesz nieco skrócić ryzyko błędów właściwości domyślnych, zawsze używając [instrukcji Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) , aby ustawić sprawdzanie typu kompilatora do `On`.</span><span class="sxs-lookup"><span data-stu-id="f6302-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="f6302-133">Jeśli planujesz użycie wstępnie zdefiniowanej klasy lub struktury w kodzie, musisz określić, czy ma ona właściwość domyślną, a jeśli tak, to jaki jest jej nazwa.</span><span class="sxs-lookup"><span data-stu-id="f6302-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="f6302-134">Ze względu na te wady należy rozważyć niedefiniowanie właściwości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="f6302-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="f6302-135">Aby uzyskać czytelność kodu, należy również rozważyć zawsze odwołanie do wszystkich właściwości jawnie, nawet właściwości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="f6302-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6302-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6302-136">See also</span></span>

- [<span data-ttu-id="f6302-137">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="f6302-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="f6302-138">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="f6302-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="f6302-139">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f6302-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="f6302-140">Default</span><span class="sxs-lookup"><span data-stu-id="f6302-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)
- [<span data-ttu-id="f6302-141">Różnice między właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6302-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="f6302-142">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="f6302-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="f6302-143">Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="f6302-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="f6302-144">Instrukcje: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="f6302-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="f6302-145">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="f6302-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="f6302-146">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="f6302-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
