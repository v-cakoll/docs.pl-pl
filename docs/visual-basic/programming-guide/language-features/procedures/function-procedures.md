---
title: Procedury funkcji
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: b0ba96a875fd8785e45eee565beefe4b961ffc9d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388754"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="212f4-102">Procedury funkcji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="212f4-102">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="212f4-103">`Function`Procedura jest serią Visual Basic instrukcji ujętych w `Function` `End Function` instrukcji i.</span><span class="sxs-lookup"><span data-stu-id="212f4-103">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="212f4-104">`Function`Procedura wykonuje zadanie, a następnie zwraca sterowanie do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="212f4-104">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="212f4-105">Gdy zwraca formant, zwraca również wartość do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="212f4-105">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="212f4-106">Za każdym razem, gdy procedura jest wywoływana, jej instrukcje są uruchamiane, rozpoczynając od pierwszej instrukcji wykonywalnej po `Function` instrukcji i kończąc na pierwszej `End Function` , `Exit Function` , lub `Return` napotkanej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="212f4-106">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="212f4-107">Można zdefiniować `Function` procedurę w module, klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="212f4-107">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="212f4-108">Jest to `Public` domyślne ustawienie, które oznacza, że można wywołać go z dowolnego miejsca w aplikacji, która ma dostęp do modułu, klasy lub struktury, w której został zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="212f4-108">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="212f4-109">`Function`Procedura może przyjmować argumenty, takie jak stałe, zmienne lub wyrażenia, które są do niego przekazane przez wywołujący kod.</span><span class="sxs-lookup"><span data-stu-id="212f4-109">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="212f4-110">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="212f4-110">Declaration syntax</span></span>

<span data-ttu-id="212f4-111">Składnia do deklarowania `Function` procedury jest następująca:</span><span class="sxs-lookup"><span data-stu-id="212f4-111">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="212f4-112">*Modyfikatory* mogą określać poziom dostępu i informacje dotyczące przeciążania, przesłaniania, udostępniania i przesłaniania.</span><span class="sxs-lookup"><span data-stu-id="212f4-112">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="212f4-113">Aby uzyskać więcej informacji, zobacz [Instrukcja function](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="212f4-113">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="212f4-114">Każdy parametr należy zadeklarować w taki sam sposób jak [procedury Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="212f4-114">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="212f4-115">Typ danych</span><span class="sxs-lookup"><span data-stu-id="212f4-115">Data type</span></span>

<span data-ttu-id="212f4-116">Każda `Function` procedura ma typ danych, tak jak każda zmienna.</span><span class="sxs-lookup"><span data-stu-id="212f4-116">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="212f4-117">Ten typ danych jest określany przez `As` klauzulę w `Function` instrukcji i określa typ danych wartości zwracanej przez funkcję do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="212f4-117">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="212f4-118">Przedstawiono następujące przykładowe deklaracje.</span><span class="sxs-lookup"><span data-stu-id="212f4-118">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="212f4-119">Aby uzyskać więcej informacji, zobacz sekcję "części" w [instrukcji funkcji](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="212f4-119">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="212f4-120">Zwracanie wartości</span><span class="sxs-lookup"><span data-stu-id="212f4-120">Returning values</span></span>

<span data-ttu-id="212f4-121">Wartość, `Function` którą procedura odsyła z powrotem do wywołującego kodu jest nazywana jego wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="212f4-121">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="212f4-122">Ta procedura zwraca tę wartość na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="212f4-122">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="212f4-123">Używa `Return` instrukcji, aby określić wartość zwracaną, i natychmiast zwraca kontrolę do wywołującego programu.</span><span class="sxs-lookup"><span data-stu-id="212f4-123">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="212f4-124">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="212f4-124">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="212f4-125">Przypisuje wartość do własnej nazwy funkcji w jednej lub kilku instrukcjach procedury.</span><span class="sxs-lookup"><span data-stu-id="212f4-125">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="212f4-126">Formant nie wraca do wywołującego programu do momentu `Exit Function` `End Function` wykonania instrukcji lub.</span><span class="sxs-lookup"><span data-stu-id="212f4-126">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="212f4-127">Ilustruje to poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="212f4-127">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="212f4-128">Zaletą przypisania wartości zwracanej do nazwy funkcji jest to, że formant nie zwraca z procedury do momentu napotkania `Exit Function` `End Function` instrukcji or.</span><span class="sxs-lookup"><span data-stu-id="212f4-128">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="212f4-129">Pozwala to na przypisanie wartości wstępnej i dostosowanie jej później w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="212f4-129">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="212f4-130">Aby uzyskać więcej informacji na temat zwracanych wartości, zobacz [Instrukcja function](../../../language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="212f4-130">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="212f4-131">Aby uzyskać informacje na temat zwracania tablic, zobacz [tablice](../arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="212f4-131">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="212f4-132">Składnia wywołania</span><span class="sxs-lookup"><span data-stu-id="212f4-132">Calling syntax</span></span>

<span data-ttu-id="212f4-133">Procedurę można wywołać `Function` przez dołączenie jej nazwy i argumentów po prawej stronie instrukcji przypisania lub w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="212f4-133">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="212f4-134">Musisz podać wartości dla wszystkich argumentów, które nie są opcjonalne, i należy ująć listę argumentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="212f4-134">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="212f4-135">Jeśli nie podano argumentów, można opcjonalnie pominąć nawiasy.</span><span class="sxs-lookup"><span data-stu-id="212f4-135">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="212f4-136">Składnia wywołania `Function` procedury jest następująca.</span><span class="sxs-lookup"><span data-stu-id="212f4-136">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="212f4-137">*lvalue* `=` *funkcjaname* `[(` *listaargumentów*    `)]`</span><span class="sxs-lookup"><span data-stu-id="212f4-137">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="212f4-138">`If ((`*funkcjaname* `[(` *listaargumentów* `)] / 3) <=` *wyrażenie*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="212f4-138">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="212f4-139">Po wywołaniu `Function` procedury nie trzeba używać jej wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="212f4-139">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="212f4-140">W przeciwnym razie wszystkie akcje funkcji są wykonywane, ale zwracana wartość jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="212f4-140">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="212f4-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>jest często wywoływany w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="212f4-141"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="212f4-142">Ilustracja deklaracji i wywołania</span><span class="sxs-lookup"><span data-stu-id="212f4-142">Illustration of declaration and call</span></span>

<span data-ttu-id="212f4-143">Poniższa `Function` procedura oblicza najdłuższy Trójkąt lub przeciwprostokątnej, z prawej strony, z uwzględnieniem wartości pozostałych dwóch stron.</span><span class="sxs-lookup"><span data-stu-id="212f4-143">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="212f4-144">Poniższy przykład przedstawia typowe wywołanie `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="212f4-144">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="212f4-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="212f4-145">See also</span></span>

- [<span data-ttu-id="212f4-146">Procedury</span><span class="sxs-lookup"><span data-stu-id="212f4-146">Procedures</span></span>](./index.md)
- [<span data-ttu-id="212f4-147">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="212f4-147">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="212f4-148">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="212f4-148">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="212f4-149">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="212f4-149">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="212f4-150">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="212f4-150">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="212f4-151">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="212f4-151">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="212f4-152">Instrukcje: tworzenie procedury, która zwraca wartość</span><span class="sxs-lookup"><span data-stu-id="212f4-152">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="212f4-153">Porady: zwracanie wartości z procedury</span><span class="sxs-lookup"><span data-stu-id="212f4-153">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="212f4-154">Instrukcje: wywoływanie procedury zwracającej wartość</span><span class="sxs-lookup"><span data-stu-id="212f4-154">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
