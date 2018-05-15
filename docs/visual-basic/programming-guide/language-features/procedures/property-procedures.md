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
ms.openlocfilehash: a0a73494c3573973d88823a7b5a5a83d2672e7d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="b2240-102">Procedury własności (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2240-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="b2240-103">Procedury właściwości jest szereg instrukcji, które modyfikowania właściwości niestandardowych dla modułu, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="b2240-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="b2240-104">Procedury własności są również znane jako *metod dostępu do właściwości*.</span><span class="sxs-lookup"><span data-stu-id="b2240-104">Property procedures are also known as *property accessors*.</span></span>  
  
 <span data-ttu-id="b2240-105">Visual Basic zawiera następujące procedury właściwości:</span><span class="sxs-lookup"><span data-stu-id="b2240-105">Visual Basic provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="b2240-106">A `Get` procedury zwraca wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="b2240-107">Jest ona wywoływana, gdy uzyskujesz dostęp do właściwości w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="b2240-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="b2240-108">A `Set` procedury ustawia właściwość na wartość, tym odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="b2240-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="b2240-109">Jest to przypisanie wartości do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="b2240-110">Procedury własności zazwyczaj Definiowanie parami przy użyciu `Get` i `Set` instrukcji, ale można zdefiniować tych procedurach, tylko jeśli właściwość jest tylko do odczytu ([instrukcja Get](../../../../visual-basic/language-reference/statements/get-statement.md)) lub w trybie tylko do zapisu ([ustawić Instrukcja](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="b2240-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="b2240-111">Można pominąć `Get` i `Set` procedury w przypadku przy użyciu automatycznie implementowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="b2240-112">Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b2240-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="b2240-113">Można zdefiniować właściwości klas, struktur i modułów.</span><span class="sxs-lookup"><span data-stu-id="b2240-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="b2240-114">Właściwości są `Public` domyślnie oznacza można Zadzwoń z dowolnego miejsca w aplikacji, które mogą uzyskiwać dostęp do właściwości kontenera.</span><span class="sxs-lookup"><span data-stu-id="b2240-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="b2240-115">Porównanie właściwości i zmiennych, zobacz [różnice pomiędzy właściwościami i zmiennymi w Visual Basic](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="b2240-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="b2240-116">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="b2240-116">Declaration Syntax</span></span>  
 <span data-ttu-id="b2240-117">Właściwość jest zdefiniowana za pomocą bloku kodu ujętą w nawiasy klamrowe [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md) i `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b2240-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="b2240-118">W tym bloku każdej procedury właściwości pojawia się jako wewnętrzny bloku ujętą w nawiasy klamrowe instrukcji deklaracji (`Get` lub `Set`) i dopasowywania `End` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b2240-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="b2240-119">Składnia deklaracji właściwości i jej procedury wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="b2240-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
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
  
 <span data-ttu-id="b2240-120">`Modifiers` Można określić poziom dostępu i informacji dotyczących przeładowanie, zastępowanie udostępniania i przesłanianie, a także określa, czy właściwość jest tylko do odczytu lub w trybie tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b2240-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="b2240-121">`AccessLevel` Na `Get` lub `Set` procedura może być żadnych poziom, który jest bardziej restrykcyjny niż poziom dostępu do określonej dla samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="b2240-122">Aby uzyskać więcej informacji, zobacz [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b2240-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="b2240-123">Typ danych</span><span class="sxs-lookup"><span data-stu-id="b2240-123">Data Type</span></span>  
 <span data-ttu-id="b2240-124">Typ danych właściwości i poziom główny dostępu są definiowane w `Property` instrukcji nie w procedurach właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="b2240-125">Właściwości może mieć tylko jednego typu danych.</span><span class="sxs-lookup"><span data-stu-id="b2240-125">A property can have only one data type.</span></span> <span data-ttu-id="b2240-126">Na przykład nie można zdefiniować właściwości do przechowywania `Decimal` wartość, ale pobrać `Double` wartość.</span><span class="sxs-lookup"><span data-stu-id="b2240-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="b2240-127">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="b2240-127">Access Level</span></span>  
 <span data-ttu-id="b2240-128">Jednak można zdefiniować na poziom główny dostępu dla właściwości i bardziej ograniczyć poziom dostępu w jednej z jego właściwości procedur.</span><span class="sxs-lookup"><span data-stu-id="b2240-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="b2240-129">Na przykład można zdefiniować `Public` właściwości, a następnie definiuje `Private Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="b2240-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="b2240-130">`Get` Pozostaje procedury `Public`.</span><span class="sxs-lookup"><span data-stu-id="b2240-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="b2240-131">Można zmienić poziom dostępu w tylko jednej z właściwości procedur i można tworzyć tylko on bardziej restrykcyjny niż poziom dostępu do podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="b2240-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="b2240-132">Aby uzyskać więcej informacji, zobacz [porady: deklarowanie właściwości z mieszanych poziomów dostępu](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b2240-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="b2240-133">Deklaracja parametru</span><span class="sxs-lookup"><span data-stu-id="b2240-133">Parameter Declaration</span></span>  
 <span data-ttu-id="b2240-134">Deklarowanie tak samo jak w przypadku każdego parametru [procedury Sub](./sub-procedures.md), z wyjątkiem tego, że mechanizm przekazywania musi być `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="b2240-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="b2240-135">Dla każdego parametru na liście parametrów ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="b2240-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="b2240-136">Jeśli parametr jest opcjonalny, należy również podać wartości domyślnej jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="b2240-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="b2240-137">Składnia służąca do określania wartości domyślnej jest następujący:</span><span class="sxs-lookup"><span data-stu-id="b2240-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="b2240-138">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="b2240-138">Property Value</span></span>  
 <span data-ttu-id="b2240-139">W `Get` procedury, zwracana wartość jest dostarczany do wywoływania wyrażenia jako wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="b2240-140">W `Set` procedury, nowa wartość właściwości jest przekazywany parametr `Set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="b2240-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="b2240-141">Jawnie deklarować parametr, należy ją zadeklarować tego samego typu danych jako wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="b2240-142">Jeśli parametr nie jest zadeklarować, kompilator używa parametru niejawne `Value` do reprezentowania nową wartość do przypisania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="b2240-143">Składnia wywoływania</span><span class="sxs-lookup"><span data-stu-id="b2240-143">Calling Syntax</span></span>  
 <span data-ttu-id="b2240-144">Wywołanie procedury właściwości jest niejawnie przez utworzenie odwołania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="b2240-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="b2240-145">Możesz użyć nazwy właściwości taki sam sposób, należy użyć nazwy zmiennej, z wyjątkiem tego, że należy podać wartości dla wszystkich argumentów, które nie są opcjonalne i listy argumentów należy ująć w nawias.</span><span class="sxs-lookup"><span data-stu-id="b2240-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="b2240-146">Jeśli nie jest dostarczony bez argumentów, opcjonalnie można pominąć nawiasów.</span><span class="sxs-lookup"><span data-stu-id="b2240-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="b2240-147">Składnia niejawne wywołanie `Set` procedura wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="b2240-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="b2240-148">Składnia niejawne wywołanie `Get` procedura wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="b2240-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="b2240-149">Ilustracja deklaracji i wywołanie</span><span class="sxs-lookup"><span data-stu-id="b2240-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="b2240-150">Następująca właściwość przechowuje pełną nazwę jako dwóch nazw składników, imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="b2240-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="b2240-151">Gdy odczytuje kod wywołujący `fullName`, `Get` procedura łączy dwie nazwy składników i zwraca pełną nazwę.</span><span class="sxs-lookup"><span data-stu-id="b2240-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="b2240-152">Gdy kod wywołujący przypisuje nową pełną nazwę, `Set` procedury próbuje podzielić dwie nazwy składowych.</span><span class="sxs-lookup"><span data-stu-id="b2240-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="b2240-153">Jeśli nie znajdzie spację, przechowuje on wszystkie jako pierwszej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b2240-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 <span data-ttu-id="b2240-154">W poniższym przykładzie przedstawiono typowe wywołania procedury właściwości `fullName`.</span><span class="sxs-lookup"><span data-stu-id="b2240-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b2240-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2240-155">See Also</span></span>  
 [<span data-ttu-id="b2240-156">Procedury</span><span class="sxs-lookup"><span data-stu-id="b2240-156">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="b2240-157">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="b2240-157">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="b2240-158">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="b2240-158">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="b2240-159">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="b2240-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="b2240-160">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2240-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="b2240-161">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="b2240-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="b2240-162">Instrukcje: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="b2240-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="b2240-163">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2240-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="b2240-164">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="b2240-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="b2240-165">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="b2240-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
