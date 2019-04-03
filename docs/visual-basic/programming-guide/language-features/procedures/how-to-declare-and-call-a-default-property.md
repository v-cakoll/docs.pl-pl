---
title: 'Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic'
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
ms.openlocfilehash: f11b5a184b72df68e302094dee762ec6876a397c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829333"
---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="5ec1d-102">Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ec1d-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="5ec1d-103">A *właściwość domyślna* jest właściwością klasy lub struktury, których Twój kod może uzyskać dostęp bez określania go.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="5ec1d-104">Podczas wywoływania kodu nazwy klasy lub struktury, ale nie właściwości i kontekst zezwala na dostęp do właściwości, Visual Basic jest rozpoznawana jako dostęp do tej klasy lub struktury domyślnej właściwości jeśli taka istnieje.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-104">When calling code names a class or structure but not a property, and the context allows access to a property, Visual Basic resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="5ec1d-105">Klasa lub struktura może mieć co najwyżej jeden domyślny właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="5ec1d-106">Jednak można przeciążać właściwości domyślne i mieć więcej niż jedną wersję.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="5ec1d-107">Aby uzyskać więcej informacji, zobacz temat [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="5ec1d-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="5ec1d-108">Aby zadeklarować właściwość domyślną</span><span class="sxs-lookup"><span data-stu-id="5ec1d-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="5ec1d-109">Zadeklaruj właściwość w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-109">Declare the property in the normal way.</span></span> <span data-ttu-id="5ec1d-110">Nie określaj `Shared` lub `Private` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="5ec1d-111">Obejmują `Default` — słowo kluczowe w deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="5ec1d-112">Określ co najmniej jeden parametr dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="5ec1d-113">Nie można zdefiniować domyślnej właściwości, które nie wymaga co najmniej jednego argumentu.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#17)]  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="5ec1d-114">Aby wywoływanie w właściwości domyślnej</span><span class="sxs-lookup"><span data-stu-id="5ec1d-114">To call a default property</span></span>  
  
1.  <span data-ttu-id="5ec1d-115">Zadeklaruj zmienną typu zawierającego klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-115">Declare a variable of the containing class or structure type.</span></span>  
  
     [!code-vb[VbVbcnProcedures#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#16)]  
  
2.  <span data-ttu-id="5ec1d-116">Użyj nazwy zmiennej wyłącznie w wyrażeniu, w których zwykle zawierałoby nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-116">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     [!code-vb[VbVbcnProcedures#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="5ec1d-117">Postępuj zgodnie z nazwą zmiennej listy argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-117">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="5ec1d-118">Domyślna właściwość musi mieć co najmniej jednego argumentu.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-118">A default property must take at least one argument.</span></span>  
  
     [!code-vb[VbVbcnProcedures#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#20)]  
  
4.  <span data-ttu-id="5ec1d-119">Aby pobrać wartość właściwości domyślne, za pomocą nazwę zmiennej listy argumentów, w wyrażeniu lub równości (`=`) Zaloguj się w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-119">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#15)]  
  
5.  <span data-ttu-id="5ec1d-120">Aby ustawić właściwości wartość domyślna, nazwa zmiennej za pomocą listy argumentów, po lewej stronie instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-120">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     [!code-vb[VbVbcnProcedures#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#14)]  
  
6.  <span data-ttu-id="5ec1d-121">Zawsze można określić nazwę właściwości domyślnej wraz z nazwą zmiennej, tak jak dostęp do wszystkich innych właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-121">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     [!code-vb[VbVbcnProcedures#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#19)]  
  
## <a name="example"></a><span data-ttu-id="5ec1d-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ec1d-122">Example</span></span>  
 <span data-ttu-id="5ec1d-123">Poniższy przykład deklaruje właściwości domyślnej klasy.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-123">The following example declares a default property on a class.</span></span>  
  
 [!code-vb[VbVbcnProcedures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="5ec1d-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ec1d-124">Example</span></span>  
 <span data-ttu-id="5ec1d-125">Poniższy przykład pokazuje, jak wywoływanie w właściwości domyślnej `myProperty` klasy `class1`.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-125">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="5ec1d-126">Instrukcje przypisania trzy przechowywać wartości w `myProperty`i <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> wywołanie odczytuje wartości.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-126">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 [!code-vb[VbVbcnProcedures#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#13)]  
  
 <span data-ttu-id="5ec1d-127">Najczęściej właściwości domyślnej jest <xref:Microsoft.VisualBasic.Collection.Item%2A> właściwość różnych klas kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-127">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5ec1d-128">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="5ec1d-128">Robust Programming</span></span>  
 <span data-ttu-id="5ec1d-129">Właściwości domyślnych może spowodować zmniejszenie małe znaki kodu źródłowego, ale mogą robić więjsze kodu czytelność.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-129">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="5ec1d-130">Jeśli kod wywołujący nie są zaznajomieni z klasy lub struktury, jeśli go nawiązuje odwołanie do nazwy klasy lub struktury nie może być określone czy tego odwołania uzyskuje dostęp do, klasa lub struktura lub domyślnej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-130">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="5ec1d-131">Może to prowadzić do błędów kompilatora lub błędy subtelne logiki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-131">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="5ec1d-132">Trochę zmniejsza ryzyko wystąpienia błędów właściwości domyślne przy użyciu zawsze [Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md) ustawienie typu kompilatora sprawdzanie `On`.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-132">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="5ec1d-133">Jeśli planujesz użyć wstępnie zdefiniowanych klasy lub struktury w kodzie, należy określić, czy ma ona właściwości domyślnej, a jeśli tak, jakie jego nazwa jest.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-133">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="5ec1d-134">Z powodu niedogodności należy rozważyć nie definiuje właściwości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-134">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="5ec1d-135">Aby zwiększyć czytelność kodu należy również wziąć pod uwagę zawsze odwołujące się do wszystkich właściwości jawnie, nawet domyślne właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ec1d-135">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ec1d-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ec1d-136">See also</span></span>

- [<span data-ttu-id="5ec1d-137">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="5ec1d-137">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="5ec1d-138">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="5ec1d-138">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5ec1d-139">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="5ec1d-139">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="5ec1d-140">Default</span><span class="sxs-lookup"><span data-stu-id="5ec1d-140">Default</span></span>](../../../../visual-basic/language-reference/modifiers/default.md)
- [<span data-ttu-id="5ec1d-141">Różnice między właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5ec1d-141">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="5ec1d-142">Instrukcje: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="5ec1d-142">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="5ec1d-143">Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="5ec1d-143">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="5ec1d-144">Instrukcje: Wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="5ec1d-144">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="5ec1d-145">Instrukcje: Umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="5ec1d-145">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="5ec1d-146">Instrukcje: Pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="5ec1d-146">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
