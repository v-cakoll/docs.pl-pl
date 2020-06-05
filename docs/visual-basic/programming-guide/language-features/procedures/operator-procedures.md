---
title: Procedury operatorów
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: a1dd183570c8aa50efff85bdaebef90bd3b0120f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364321"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="fb903-102">Procedury operatorów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb903-102">Operator Procedures (Visual Basic)</span></span>

<span data-ttu-id="fb903-103">Procedura operatora to seria Visual Basic instrukcji, które definiują zachowanie operatora standardowego (takiego jak `*` , `<>` lub `And` ) dla zdefiniowanej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="fb903-104">Jest to również nazywane *przeciążeniem operatora*.</span><span class="sxs-lookup"><span data-stu-id="fb903-104">This is also called *operator overloading*.</span></span>

## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="fb903-105">Kiedy należy definiować procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="fb903-105">When to Define Operator Procedures</span></span>

<span data-ttu-id="fb903-106">Po zdefiniowaniu klasy lub struktury można zadeklarować zmienne jako typu tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="fb903-107">Czasami taka zmienna musi brać udział w operacji jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="fb903-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="fb903-108">Aby to zrobić, musi to być operand operatora.</span><span class="sxs-lookup"><span data-stu-id="fb903-108">To do this, it must be an operand of an operator.</span></span>

<span data-ttu-id="fb903-109">Visual Basic definiuje operatory tylko dla podstawowych typów danych.</span><span class="sxs-lookup"><span data-stu-id="fb903-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="fb903-110">Można zdefiniować zachowanie operatora, gdy jeden lub oba operandy są typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>

<span data-ttu-id="fb903-111">Aby uzyskać więcej informacji, zobacz [instrukcja operatora](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb903-111">For more information, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="types-of-operator-procedure"></a><span data-ttu-id="fb903-112">Typy procedur operatora</span><span class="sxs-lookup"><span data-stu-id="fb903-112">Types of Operator Procedure</span></span>

<span data-ttu-id="fb903-113">Procedura operatora może być jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="fb903-113">An operator procedure can be one of the following types:</span></span>

- <span data-ttu-id="fb903-114">Definicja operatora jednoargumentowego, gdzie argument jest typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="fb903-115">Definicja operatora binarnego, w którym co najmniej jeden z argumentów jest typem klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>

- <span data-ttu-id="fb903-116">Definicja operatora konwersji, gdzie argument jest typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>

- <span data-ttu-id="fb903-117">Definicja operatora konwersji, która zwraca typ klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>

 <span data-ttu-id="fb903-118">Operatory konwersji są zawsze jednoargumentowe i zawsze `CType` są używane jako definiowane operatory.</span><span class="sxs-lookup"><span data-stu-id="fb903-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="fb903-119">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="fb903-119">Declaration Syntax</span></span>

<span data-ttu-id="fb903-120">Składnia do deklarowania procedury operatora jest następująca:</span><span class="sxs-lookup"><span data-stu-id="fb903-120">The syntax for declaring an operator procedure is as follows:</span></span>

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

<span data-ttu-id="fb903-121">Użyj `Widening` `Narrowing` słowa kluczowego or tylko w operatorze konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="fb903-121">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="fb903-122">Symbol operatora jest zawsze [CType Funkcja](../../../language-reference/functions/ctype-function.md) dla operatora konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="fb903-122">The operator symbol is always [CType Function](../../../language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>

<span data-ttu-id="fb903-123">Należy zadeklarować dwa operandy do definiowania operatora binarnego i zadeklarować jeden operand do definiowania operatora jednoargumentowego, łącznie z operatorem konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="fb903-123">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="fb903-124">Wszystkie operandy muszą być zadeklarowane `ByVal` .</span><span class="sxs-lookup"><span data-stu-id="fb903-124">All operands must be declared `ByVal`.</span></span>

<span data-ttu-id="fb903-125">Każdy operand należy zadeklarować w taki sam sposób, w jaki deklaruje parametry [procedur podrzędnych](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="fb903-125">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="fb903-126">Typ danych</span><span class="sxs-lookup"><span data-stu-id="fb903-126">Data Type</span></span>

<span data-ttu-id="fb903-127">Ponieważ definiujesz operator dla zdefiniowanej klasy lub struktury, co najmniej jeden z operandów musi być typem danych tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-127">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="fb903-128">Dla operatora konwersji typu argument operacji lub typ zwracany musi być typem danych klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb903-128">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>

<span data-ttu-id="fb903-129">Aby uzyskać więcej informacji, zobacz [instrukcja operatora](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb903-129">For more details, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="fb903-130">Składnia wywołania</span><span class="sxs-lookup"><span data-stu-id="fb903-130">Calling Syntax</span></span>

<span data-ttu-id="fb903-131">Procedurę operatora można wywołać niejawnie przy użyciu symbolu operatora w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="fb903-131">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="fb903-132">Należy podać operandy tak samo jak w przypadku wstępnie zdefiniowanych operatorów.</span><span class="sxs-lookup"><span data-stu-id="fb903-132">You supply the operands the same way you do for predefined operators.</span></span>

<span data-ttu-id="fb903-133">Składnia niejawnego wywołania procedury operatora jest następująca:</span><span class="sxs-lookup"><span data-stu-id="fb903-133">The syntax for an implicit call to an operator procedure is as follows:</span></span>

<span data-ttu-id="fb903-134">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="fb903-134">`Dim testStruct As`  *structurename*</span></span>

<span data-ttu-id="fb903-135">`Dim testNewStruct As`  *strukturaname* `= testStruct` *operatorsymbol*      `10`</span><span class="sxs-lookup"><span data-stu-id="fb903-135">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="fb903-136">Ilustracja deklaracji i wywołania</span><span class="sxs-lookup"><span data-stu-id="fb903-136">Illustration of Declaration and Call</span></span>

<span data-ttu-id="fb903-137">Poniższa struktura przechowuje podpisaną 128-bitową wartość całkowitą jako składnik wysokiej kolejności i niskiego rzędu.</span><span class="sxs-lookup"><span data-stu-id="fb903-137">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="fb903-138">Definiuje operator, `+` Aby dodawać dwie `veryLong` wartości i generować wartość będącą wynikiem `veryLong` .</span><span class="sxs-lookup"><span data-stu-id="fb903-138">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

<span data-ttu-id="fb903-139">Poniższy przykład przedstawia typowe wywołanie `+` operatora zdefiniowanego w `veryLong` .</span><span class="sxs-lookup"><span data-stu-id="fb903-139">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="fb903-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb903-140">See also</span></span>

- [<span data-ttu-id="fb903-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="fb903-141">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fb903-142">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="fb903-142">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="fb903-143">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="fb903-143">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="fb903-144">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="fb903-144">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="fb903-145">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="fb903-145">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fb903-146">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="fb903-146">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="fb903-147">Instrukcje: definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="fb903-147">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="fb903-148">Instrukcje: definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="fb903-148">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="fb903-149">Instrukcje: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="fb903-149">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="fb903-150">Instrukcje: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="fb903-150">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
