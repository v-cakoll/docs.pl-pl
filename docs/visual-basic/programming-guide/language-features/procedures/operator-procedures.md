---
title: Procedury operatorów (Visual Basic)
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
ms.openlocfilehash: 80c9a77494be95365899c6a25435fcfc5d2a7293
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175022"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="24ed8-102">Procedury operatorów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24ed8-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="24ed8-103">Procedury operatora to szereg instrukcji, które definiują zachowanie standardowego operatora (takie jak `*`, `<>`, lub `And`) dla klasy lub struktury, które zostały zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="24ed8-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="24ed8-104">Jest to również nazywane *przeciążenia operatora*.</span><span class="sxs-lookup"><span data-stu-id="24ed8-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="24ed8-105">Kiedy należy zdefiniować procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="24ed8-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="24ed8-106">Po zdefiniowaniu klasy lub struktury można zadeklarować zmienne typu tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24ed8-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="24ed8-107">Czasami takiej zmiennej musi uczestniczyć w operacji jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="24ed8-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="24ed8-108">Aby to zrobić, musi być operand operatora.</span><span class="sxs-lookup"><span data-stu-id="24ed8-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="24ed8-109">Visual Basic definiuje operatory tylko na jego typów podstawowych danych.</span><span class="sxs-lookup"><span data-stu-id="24ed8-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="24ed8-110">Można zdefiniować zachowanie operatorowi, gdy jeden lub oba operandy są typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24ed8-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="24ed8-111">Aby uzyskać więcej informacji, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="24ed8-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="24ed8-112">Typy procedury operatora</span><span class="sxs-lookup"><span data-stu-id="24ed8-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="24ed8-113">Procedury operatora może być jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="24ed8-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="24ed8-114">Definicja operatora jednoargumentowego, gdy argument jest typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24ed8-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="24ed8-115">Definicja operatora binarnego, gdzie jest co najmniej jeden z argumentów typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24ed8-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="24ed8-116">Definicja operatora konwersji, gdy argument jest typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24ed8-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="24ed8-117">Definicja operatora konwersji, która zwraca typ klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24ed8-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="24ed8-118">Operatory konwersji są zawsze jednoargumentowy i zawsze używaj `CType` jako operator jest definiowany.</span><span class="sxs-lookup"><span data-stu-id="24ed8-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="24ed8-119">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="24ed8-119">Declaration Syntax</span></span>  
 <span data-ttu-id="24ed8-120">Składnia do deklarowania procedury operatora jest następująca:</span><span class="sxs-lookup"><span data-stu-id="24ed8-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  <span data-ttu-id="24ed8-121">*operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *typu danych* </span><span class="sxs-lookup"><span data-stu-id="24ed8-121">*operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="24ed8-122">Możesz użyć `Widening` lub `Narrowing` — słowo kluczowe tylko dla operatora konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="24ed8-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="24ed8-123">Symbol operatora jest zawsze [funkcja CType](../../../../visual-basic/language-reference/functions/ctype-function.md) dla operatora konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="24ed8-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="24ed8-124">Zadeklaruj dwóch argumentów operacji, aby zdefiniować operator binarny i Zadeklaruj jeden argument, aby zdefiniować operator jednoargumentowy, łącznie z operatora konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="24ed8-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="24ed8-125">Wszystkie operandy muszą być zadeklarowane `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="24ed8-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="24ed8-126">Zadeklaruj każdy argument ten sam sposób możesz deklarować parametry [procedury Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="24ed8-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="24ed8-127">Typ danych</span><span class="sxs-lookup"><span data-stu-id="24ed8-127">Data Type</span></span>  
 <span data-ttu-id="24ed8-128">Ponieważ operator są definiowane dla klasy lub struktury, zdefiniowane przez Ciebie, co najmniej jeden z argumentów musi być typu danych z tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24ed8-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="24ed8-129">Dla operatora konwersji typu argument lub zwracany typ musi być typu danych, klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="24ed8-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="24ed8-130">Aby uzyskać więcej informacji, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="24ed8-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="24ed8-131">Składnia wywoływania</span><span class="sxs-lookup"><span data-stu-id="24ed8-131">Calling Syntax</span></span>  
 <span data-ttu-id="24ed8-132">Wywoływanie procedury operatora jest niejawnie przy użyciu znaku operator w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="24ed8-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="24ed8-133">Argumenty operacji Podaj ten sam sposób jak w przypadku operatorów wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="24ed8-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="24ed8-134">Składnia wywołanie niejawne procedury operatora jest następująca:</span><span class="sxs-lookup"><span data-stu-id="24ed8-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 `Dim testStruct As`  *<span data-ttu-id="24ed8-135">structurename</span><span class="sxs-lookup"><span data-stu-id="24ed8-135">structurename</span></span>*  
  
 `Dim testNewStruct As`  <span data-ttu-id="24ed8-136">*structurename*`= testStruct`*operatorsymbol* </span><span class="sxs-lookup"><span data-stu-id="24ed8-136">*structurename*  `= testStruct`  *operatorsymbol*</span></span>  `10`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="24ed8-137">Ilustracja deklaracji i wywołanie</span><span class="sxs-lookup"><span data-stu-id="24ed8-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="24ed8-138">Następującą strukturę przechowuje wartość liczby całkowitej ze znakiem 128-bitowego, jako części składowe wyższego rzędu i niskiego rzędu.</span><span class="sxs-lookup"><span data-stu-id="24ed8-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="24ed8-139">Definiuje on `+` operatora, aby dodać dwa `veryLong` wartości i generować co `veryLong` wartość.</span><span class="sxs-lookup"><span data-stu-id="24ed8-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 <span data-ttu-id="24ed8-140">W poniższym przykładzie przedstawiono typowe wywołanie `+` operator wobec `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="24ed8-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a><span data-ttu-id="24ed8-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24ed8-141">See also</span></span>

- [<span data-ttu-id="24ed8-142">Procedury</span><span class="sxs-lookup"><span data-stu-id="24ed8-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="24ed8-143">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="24ed8-143">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="24ed8-144">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="24ed8-144">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="24ed8-145">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="24ed8-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="24ed8-146">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="24ed8-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="24ed8-147">Operator — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="24ed8-147">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="24ed8-148">Instrukcje: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="24ed8-148">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="24ed8-149">Instrukcje: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="24ed8-149">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="24ed8-150">Instrukcje: Wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="24ed8-150">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="24ed8-151">Instrukcje: Używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="24ed8-151">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
