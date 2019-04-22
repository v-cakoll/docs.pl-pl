---
title: Procedury własności (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
ms.openlocfilehash: 47e93ee17f160ce5cd701fd0a12ec16b3997ce9b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828352"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="064c9-102">Procedury własności (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="064c9-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="064c9-103">Procedury właściwości jest szereg instrukcji, które manipulowania właściwości niestandardowych dla modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="064c9-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="064c9-104">Procedury własności są również nazywane *Akcesory właściwości*.</span><span class="sxs-lookup"><span data-stu-id="064c9-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="064c9-105">Visual Basic zawiera następujące procedury właściwości:</span><span class="sxs-lookup"><span data-stu-id="064c9-105">Visual Basic provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="064c9-106">A `Get` procedura zwraca wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="064c9-107">Jest ona wywoływana, gdy uzyskujesz dostęp do właściwości w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="064c9-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="064c9-108">A `Set` procedury ustawia właściwość na wartość, w tym odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="064c9-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="064c9-109">Jest ona wywoływana podczas przypisywania wartości do właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="064c9-110">Zazwyczaj definiowanie procedury właściwości w parach, za pomocą `Get` i `Set` instrukcji, ale można zdefiniować tych procedurach, tylko, jeśli właściwość jest tylko do odczytu ([instrukcja Get](../../../../visual-basic/language-reference/statements/get-statement.md)) lub tylko do zapisu ([zestawu Instrukcja](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="064c9-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="064c9-111">Możesz pominąć `Get` i `Set` procedury w przypadku przy użyciu automatycznie implementowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="064c9-112">Aby uzyskać więcej informacji, zobacz [implemented Properties](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="064c9-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="064c9-113">Można zdefiniować właściwości klas, struktur i modułów.</span><span class="sxs-lookup"><span data-stu-id="064c9-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="064c9-114">Właściwości są `Public` domyślnie, co oznacza, że można go wywołać z dowolnego miejsca w aplikacji, które mogą uzyskiwać dostęp do właściwości kontenera.</span><span class="sxs-lookup"><span data-stu-id="064c9-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="064c9-115">Dla porównania z właściwościami i zmiennymi, zobacz [różnice między właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="064c9-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="064c9-116">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="064c9-116">Declaration Syntax</span></span>  
 <span data-ttu-id="064c9-117">Sama właściwość jest definiowany przez blok kodu ujęte w [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="064c9-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="064c9-118">Wewnątrz tego bloku każdej procedury właściwość pojawia się jako wewnętrzny blok ujęte w instrukcji deklaracji (`Get` lub `Set`) i dopasowywania `End` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="064c9-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="064c9-119">Składnia deklaracji właściwości i jej procedury jest następująca:</span><span class="sxs-lookup"><span data-stu-id="064c9-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 <span data-ttu-id="064c9-120">`Modifiers` Można określić poziom dostępu i informacji dotyczących przeciążenia, zastępowanie, udostępnianie i przesłanianie, a także tego, czy właściwość jest tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="064c9-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="064c9-121">`AccessLevel` Na `Get` lub `Set` procedura może być dowolny poziom, który jest bardziej restrykcyjny niż poziom dostępu, określony dla samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="064c9-122">Aby uzyskać więcej informacji, zobacz [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="064c9-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="064c9-123">Typ danych</span><span class="sxs-lookup"><span data-stu-id="064c9-123">Data Type</span></span>  
 <span data-ttu-id="064c9-124">Typ danych właściwości i poziom dostępu jednostki są definiowane w `Property` instrukcji, a nie w procedurach właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="064c9-125">Właściwość może mieć tylko jednego typu danych.</span><span class="sxs-lookup"><span data-stu-id="064c9-125">A property can have only one data type.</span></span> <span data-ttu-id="064c9-126">Na przykład nie można zdefiniować właściwości w celu przechowywania `Decimal` wartość, ale pobieranie `Double` wartość.</span><span class="sxs-lookup"><span data-stu-id="064c9-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="064c9-127">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="064c9-127">Access Level</span></span>  
 <span data-ttu-id="064c9-128">Można jednak określić poziom dostępu jednostki dla właściwości i bardziej ograniczyć poziomu dostępu na jeden z jego procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="064c9-129">Na przykład można zdefiniować `Public` właściwości, a następnie zdefiniować `Private Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="064c9-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="064c9-130">`Get` Pozostaje procedury `Public`.</span><span class="sxs-lookup"><span data-stu-id="064c9-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="064c9-131">Można zmienić poziomu dostępu tylko w jednym procedury właściwości i można tworzyć tylko je bardziej restrykcyjny niż poziom dostępu podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="064c9-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="064c9-132">Aby uzyskać więcej informacji, zobacz [jak: Deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="064c9-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="064c9-133">Deklaracja parametru</span><span class="sxs-lookup"><span data-stu-id="064c9-133">Parameter Declaration</span></span>  
 <span data-ttu-id="064c9-134">Zadeklaruj taki sam sposób jak w przypadku każdego parametru [procedury Sub](./sub-procedures.md), z tą różnicą, że mechanizm przekazywania musi być `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="064c9-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="064c9-135">Składnia dla każdego parametru na liście parametrów jest w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="064c9-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="064c9-136">Jeśli parametr jest opcjonalny, należy również podać wartości domyślnej w ramach swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="064c9-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="064c9-137">Składnia określająca wartość domyślna jest następująca:</span><span class="sxs-lookup"><span data-stu-id="064c9-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="064c9-138">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="064c9-138">Property Value</span></span>  
 <span data-ttu-id="064c9-139">W `Get` procedury, wartość zwracana jest dostarczany do wywoływania wyrażenia jako wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="064c9-140">W `Set` procedury, nowa wartość właściwości jest przekazywana do parametru `Set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="064c9-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="064c9-141">Jeśli parametr jest jawnie deklarować, należy zadeklarować ją za pomocą tego samego typu danych, ponieważ właściwość.</span><span class="sxs-lookup"><span data-stu-id="064c9-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="064c9-142">Jeśli nie deklaruj parametru, kompilator używa niejawny parametr `Value` do reprezentowania nową wartość do przypisania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="064c9-143">Składnia wywoływania</span><span class="sxs-lookup"><span data-stu-id="064c9-143">Calling Syntax</span></span>  
 <span data-ttu-id="064c9-144">Wywoływanie procedury właściwości są niejawnie, wprowadzając odwołanie do właściwości.</span><span class="sxs-lookup"><span data-stu-id="064c9-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="064c9-145">Możesz użyć nazwy właściwości taki sam sposób użyje nazwę zmiennej, z tą różnicą, że należy podać wartości w argumentach, które nie są opcjonalne i listy argumentów należy ująć w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="064c9-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="064c9-146">Jeśli zostały dostarczone żadne argumenty, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="064c9-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="064c9-147">Składnia wywołanie niejawne `Set` procedura jest następująca:</span><span class="sxs-lookup"><span data-stu-id="064c9-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="064c9-148">Składnia wywołanie niejawne `Get` procedura jest następująca:</span><span class="sxs-lookup"><span data-stu-id="064c9-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="064c9-149">Ilustracja deklaracji i wywołanie</span><span class="sxs-lookup"><span data-stu-id="064c9-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="064c9-150">Następująca właściwość przechowuje pełną nazwę w postaci dwie nazwy składowych, imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="064c9-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="064c9-151">Podczas wywoływania kodu odczytuje `fullName`, `Get` procedury łączy dwie nazwy składowych i zwraca pełną nazwę.</span><span class="sxs-lookup"><span data-stu-id="064c9-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="064c9-152">Gdy kod wywołujący przypisuje nową pełną nazwę, `Set` procedury próbuje podzielenie go na dwie nazwy składowych.</span><span class="sxs-lookup"><span data-stu-id="064c9-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="064c9-153">Jeśli nie znajdzie spację, przechowuje on wszystkie jako imię.</span><span class="sxs-lookup"><span data-stu-id="064c9-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="064c9-154">W poniższym przykładzie przedstawiono typowe wywołania procedur właściwość `fullName`.</span><span class="sxs-lookup"><span data-stu-id="064c9-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="064c9-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="064c9-155">See also</span></span>

- [<span data-ttu-id="064c9-156">Procedury</span><span class="sxs-lookup"><span data-stu-id="064c9-156">Procedures</span></span>](./index.md)
- [<span data-ttu-id="064c9-157">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="064c9-157">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="064c9-158">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="064c9-158">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="064c9-159">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="064c9-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="064c9-160">Różnice między właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="064c9-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="064c9-161">Instrukcje: Tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="064c9-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="064c9-162">Instrukcje: Wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="064c9-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="064c9-163">Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="064c9-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="064c9-164">Instrukcje: Umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="064c9-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="064c9-165">Instrukcje: Pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="064c9-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
