---
title: Procedury własności
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
ms.openlocfilehash: cb5b0e12512e476b7c96bbfb19f8e4f470f6b498
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363736"
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="6569c-102">Procedury własności (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6569c-102">Property Procedures (Visual Basic)</span></span>

<span data-ttu-id="6569c-103">Procedura właściwości to seria Visual Basic instrukcji, które manipulują właściwością niestandardową w module, klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="6569c-103">A property procedure is a series of Visual Basic statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="6569c-104">Procedury właściwości są również znane jako metody *dostępu do właściwości*.</span><span class="sxs-lookup"><span data-stu-id="6569c-104">Property procedures are also known as *property accessors*.</span></span>

<span data-ttu-id="6569c-105">Visual Basic zapewnia następujące procedury właściwości:</span><span class="sxs-lookup"><span data-stu-id="6569c-105">Visual Basic provides for the following property procedures:</span></span>

- <span data-ttu-id="6569c-106">`Get`Procedura zwraca wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="6569c-107">Jest wywoływana, gdy uzyskujesz dostęp do właściwości w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="6569c-107">It is called when you access the property in an expression.</span></span>
- <span data-ttu-id="6569c-108">`Set`Procedura ustawia właściwość na wartość, łącznie z odwołaniem do obiektu.</span><span class="sxs-lookup"><span data-stu-id="6569c-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="6569c-109">Jest wywoływana, gdy przypiszesz wartość do właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-109">It is called when you assign a value to the property.</span></span>

<span data-ttu-id="6569c-110">Zazwyczaj definiuje się procedury właściwości w parach przy użyciu `Get` instrukcji i `Set` , ale można zdefiniować pojedynczą procedurę, jeśli właściwość jest tylko do odczytu ([Get Statement](../../../language-reference/statements/get-statement.md)) lub tylko do zapisu ([instrukcja set](../../../language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="6569c-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../language-reference/statements/set-statement.md)).</span></span>

<span data-ttu-id="6569c-111">Możesz pominąć `Get` procedurę i w `Set` przypadku korzystania z właściwości, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="6569c-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="6569c-112">Aby uzyskać więcej informacji, zobacz [zaimplementowane właściwości](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="6569c-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>

<span data-ttu-id="6569c-113">Można definiować właściwości w klasach, strukturach i modułach.</span><span class="sxs-lookup"><span data-stu-id="6569c-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="6569c-114">Właściwości są `Public` Domyślnie, co oznacza, że można je wywoływać z dowolnego miejsca w aplikacji, która może uzyskiwać dostęp do kontenera właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>

<span data-ttu-id="6569c-115">Porównanie właściwości i zmiennych można znaleźć [w temacie różnice między właściwościami i zmiennymi w Visual Basic](differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="6569c-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](differences-between-properties-and-variables.md).</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="6569c-116">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="6569c-116">Declaration syntax</span></span>

<span data-ttu-id="6569c-117">Sama właściwość jest definiowana przez blok kodu ujęty w [instrukcji Property](../../../language-reference/statements/property-statement.md) i `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6569c-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="6569c-118">Wewnątrz tego bloku każda procedura właściwości jest wyświetlana jako wewnętrzny blok ujęty w instrukcji deklaracji ( `Get` lub `Set` ) i zgodnej `End` deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6569c-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>

<span data-ttu-id="6569c-119">Składnia do deklarowania właściwości i jej procedur jest następująca:</span><span class="sxs-lookup"><span data-stu-id="6569c-119">The syntax for declaring a property and its procedures is as follows:</span></span>

```vb
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
' - or -
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]
```

<span data-ttu-id="6569c-120">`Modifiers`Można określić poziom dostępu i informacje dotyczące przeciążania, przesłaniania, udostępniania i przesłaniania, a także czy właściwość jest tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="6569c-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="6569c-121">`AccessLevel` `Get` `Set` Procedura lub może być dowolnym poziomem, który jest bardziej restrykcyjny niż poziom dostępu określony dla samej właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="6569c-122">Aby uzyskać więcej informacji, zobacz [instrukcja właściwości](../../../language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6569c-122">For more information, see [Property Statement](../../../language-reference/statements/property-statement.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="6569c-123">Typ danych</span><span class="sxs-lookup"><span data-stu-id="6569c-123">Data Type</span></span>

<span data-ttu-id="6569c-124">Typ danych właściwości i poziom dostępu podmiotu zabezpieczeń są zdefiniowane w `Property` instrukcji, a nie w procedurach właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="6569c-125">Właściwość może mieć tylko jeden typ danych.</span><span class="sxs-lookup"><span data-stu-id="6569c-125">A property can have only one data type.</span></span> <span data-ttu-id="6569c-126">Na przykład nie można zdefiniować właściwości do przechowywania `Decimal` wartości, ale pobrać `Double` wartości.</span><span class="sxs-lookup"><span data-stu-id="6569c-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>

### <a name="access-level"></a><span data-ttu-id="6569c-127">Poziom dostępu</span><span class="sxs-lookup"><span data-stu-id="6569c-127">Access Level</span></span>

<span data-ttu-id="6569c-128">Można jednak zdefiniować poziom dostępu podmiotu zabezpieczeń dla właściwości i jeszcze bardziej ograniczyć poziom dostępu w jednej z jej procedur dotyczących właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="6569c-129">Na przykład można zdefiniować `Public` Właściwość, a następnie zdefiniować `Private Set` procedurę.</span><span class="sxs-lookup"><span data-stu-id="6569c-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="6569c-130">`Get`Procedura pozostanie `Public` .</span><span class="sxs-lookup"><span data-stu-id="6569c-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="6569c-131">Poziom dostępu można zmienić tylko w jednej z procedur dotyczących właściwości i można uczynić go bardziej restrykcyjnym niż główny poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="6569c-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="6569c-132">Aby uzyskać więcej informacji, zobacz [jak: deklarowanie właściwości z mieszanymi poziomami dostępu](how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="6569c-132">For more information, see [How to: Declare a Property with Mixed Access Levels](how-to-declare-a-property-with-mixed-access-levels.md).</span></span>

## <a name="parameter-declaration"></a><span data-ttu-id="6569c-133">Deklaracja parametru</span><span class="sxs-lookup"><span data-stu-id="6569c-133">Parameter declaration</span></span>

<span data-ttu-id="6569c-134">Każdy parametr można zadeklarować w taki sam sposób jak [procedury Sub](sub-procedures.md), z tą różnicą, że mechanizm przekazywania musi być `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="6569c-134">You declare each parameter the same way you do for [Sub Procedures](sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>

<span data-ttu-id="6569c-135">Składnia każdego parametru na liście parametrów jest następująca:</span><span class="sxs-lookup"><span data-stu-id="6569c-135">The syntax for each parameter in the parameter list is as follows:</span></span>

```vb
[Optional] ByVal [ParamArray] parametername As datatype
```

<span data-ttu-id="6569c-136">Jeśli parametr jest opcjonalny, należy również podać wartość domyślną w ramach swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="6569c-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="6569c-137">Składnia określająca wartość domyślną jest następująca:</span><span class="sxs-lookup"><span data-stu-id="6569c-137">The syntax for specifying a default value is as follows:</span></span>

```vb
Optional ByVal parametername As datatype = defaultvalue
```

## <a name="property-value"></a><span data-ttu-id="6569c-138">Wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="6569c-138">Property value</span></span>

<span data-ttu-id="6569c-139">W `Get` procedurze, wartość zwracana jest przekazywana do wyrażenia wywołującego jako wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>

<span data-ttu-id="6569c-140">W `Set` procedurze nowa wartość właściwości jest przenoszona do parametru `Set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="6569c-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="6569c-141">Jeśli jawnie deklarujesz parametr, musisz zadeklarować go przy użyciu tego samego typu danych co właściwość.</span><span class="sxs-lookup"><span data-stu-id="6569c-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="6569c-142">Jeśli parametr nie zostanie zadeklarowany, kompilator używa niejawnego parametru `Value` do reprezentowania nowej wartości, która ma zostać przypisana do właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="6569c-143">Składnia wywołania</span><span class="sxs-lookup"><span data-stu-id="6569c-143">Calling syntax</span></span>

<span data-ttu-id="6569c-144">Wywoływanie procedury właściwości niejawnie przez utworzenie odwołania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="6569c-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="6569c-145">Nazwa właściwości jest używana w taki sam sposób, jak przy użyciu nazwy zmiennej, z tą różnicą, że należy podać wartości dla wszystkich argumentów, które nie są opcjonalne, i należy ująć listę argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="6569c-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="6569c-146">Jeśli nie podano argumentów, można opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="6569c-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="6569c-147">Składnia dla niejawnego wywołania `Set` procedury jest następująca:</span><span class="sxs-lookup"><span data-stu-id="6569c-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>

```vb
propertyname[(argumentlist)] = expression
```

<span data-ttu-id="6569c-148">Składnia dla niejawnego wywołania `Get` procedury jest następująca:</span><span class="sxs-lookup"><span data-stu-id="6569c-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>

```vb
lvalue = propertyname[(argumentlist)]
Do While (propertyname[(argumentlist)] > expression)
```

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="6569c-149">Ilustracja deklaracji i wywołania</span><span class="sxs-lookup"><span data-stu-id="6569c-149">Illustration of declaration and call</span></span>

<span data-ttu-id="6569c-150">Następująca właściwość przechowuje pełną nazwę jako dwie nazwy składników, imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="6569c-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="6569c-151">Podczas odczytywania kodu wywołującego `fullName` `Get` procedura łączy dwie nazwy składników i zwraca pełną nazwę.</span><span class="sxs-lookup"><span data-stu-id="6569c-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="6569c-152">Gdy wywołujący kod przypisze nową pełną nazwę, `Set` procedura próbuje ją podzielić na dwie nazwy składników.</span><span class="sxs-lookup"><span data-stu-id="6569c-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="6569c-153">Jeśli nie znajdzie miejsca, będzie ono przechowywane jako imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="6569c-153">If it does not find a space, it stores it all as the first name.</span></span>

[!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]

<span data-ttu-id="6569c-154">W poniższym przykładzie przedstawiono typowe wywołania procedur właściwości `fullName` :</span><span class="sxs-lookup"><span data-stu-id="6569c-154">The following example shows typical calls to the property procedures of `fullName`:</span></span>

[!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]

## <a name="see-also"></a><span data-ttu-id="6569c-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6569c-155">See also</span></span>

- [<span data-ttu-id="6569c-156">Procedury</span><span class="sxs-lookup"><span data-stu-id="6569c-156">Procedures</span></span>](index.md)
- [<span data-ttu-id="6569c-157">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="6569c-157">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="6569c-158">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="6569c-158">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="6569c-159">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="6569c-159">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="6569c-160">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6569c-160">Differences Between Properties and Variables in Visual Basic</span></span>](differences-between-properties-and-variables.md)
- [<span data-ttu-id="6569c-161">Instrukcje: tworzenie właściwości</span><span class="sxs-lookup"><span data-stu-id="6569c-161">How to: Create a Property</span></span>](how-to-create-a-property.md)
- [<span data-ttu-id="6569c-162">Porady: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="6569c-162">How to: Call a Property Procedure</span></span>](how-to-call-a-property-procedure.md)
- [<span data-ttu-id="6569c-163">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6569c-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="6569c-164">Instrukcje: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="6569c-164">How to: Put a Value in a Property</span></span>](how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="6569c-165">Instrukcje: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="6569c-165">How to: Get a Value from a Property</span></span>](how-to-get-a-value-from-a-property.md)
