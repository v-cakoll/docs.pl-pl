---
title: Wnioskowanie o typie lokalnym (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 2b239e17ba7fa0b6a6b08d52f4394541eaa08b28
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775724"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="5c447-102">Wnioskowanie o typie lokalnym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c447-102">Local Type Inference (Visual Basic)</span></span>

<span data-ttu-id="5c447-103">Kompilator Visual Basic używa *wnioskowania typu* w celu określenia typów danych zmiennych lokalnych zadeklarowanych bez klauzuli `As`.</span><span class="sxs-lookup"><span data-stu-id="5c447-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="5c447-104">Kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="5c447-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="5c447-105">Dzięki temu można zadeklarować zmienne bez jawnego stwierdzenia typu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c447-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="5c447-106">W wyniku deklaracji zarówno `num1`, jak i `num2` są silnie wpisane jako liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="5c447-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>

[!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]

> [!NOTE]
> <span data-ttu-id="5c447-107">Jeśli nie chcesz, aby `num2` w poprzednim przykładzie zostały wpisane jako `Integer`, możesz określić inny typ za pomocą deklaracji, takiej jak `Dim num3 As Object = 3` lub `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="5c447-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>

> [!NOTE]
> <span data-ttu-id="5c447-108">Wnioskowanie o typie może być używane tylko w przypadku niestatycznych zmiennych lokalnych; nie można jej użyć do określenia typu pól klasy, właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="5c447-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>

<span data-ttu-id="5c447-109">Wnioskowanie o typie lokalnym jest stosowane na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="5c447-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="5c447-110">Nie można jej użyć do deklarowania zmiennych na poziomie modułu (w obrębie klasy, struktury, modułu lub interfejsu, ale nie wewnątrz procedury lub bloku).</span><span class="sxs-lookup"><span data-stu-id="5c447-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="5c447-111">Jeśli `num2` w poprzednim przykładzie było polem klasy, a nie zmienną lokalną w procedurze, deklaracja spowodowałaby błąd z `Option Strict` on i klasyfikuje `num2` jako `Object` z `Option Strict` off.</span><span class="sxs-lookup"><span data-stu-id="5c447-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="5c447-112">Podobnie wnioskowanie o typie lokalnym nie ma zastosowania do zmiennych poziomu procedury zadeklarowanych jako `Static`.</span><span class="sxs-lookup"><span data-stu-id="5c447-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>

## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="5c447-113">Wnioskowanie o typie a późne wiązanie</span><span class="sxs-lookup"><span data-stu-id="5c447-113">Type Inference vs. Late Binding</span></span>

<span data-ttu-id="5c447-114">Kod używający wnioskowania o typie przypomina kod, który opiera się na późnym powiązaniu.</span><span class="sxs-lookup"><span data-stu-id="5c447-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="5c447-115">Jednak typ wnioskowania o silnej liczbie typów zmiennej zamiast opuszczania jej jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="5c447-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="5c447-116">Kompilator używa inicjatora zmiennej do określenia typu zmiennej w czasie kompilacji w celu utworzenia kodu z wczesnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="5c447-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="5c447-117">W poprzednim przykładzie `num2`, jak `num1`, jest wpisana jako `Integer`.</span><span class="sxs-lookup"><span data-stu-id="5c447-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>

<span data-ttu-id="5c447-118">Zachowanie zmiennych wczesnych powiązań różni się od wartości zmiennych z późnym wiązaniem, dla których typ jest znany tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5c447-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="5c447-119">Poznanie typu wczesnego pozwala kompilatorowi identyfikować problemy przed wykonaniem, przydzielać pamięć dokładnie i wykonywać inne optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="5c447-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="5c447-120">Wczesne wiązanie umożliwia również Visual Basic zintegrowanego środowiska programistycznego (IDE), aby zapewnić pomoc IntelliSense na temat elementów członkowskich obiektu.</span><span class="sxs-lookup"><span data-stu-id="5c447-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="5c447-121">Wczesne wiązanie jest również preferowane dla wydajności.</span><span class="sxs-lookup"><span data-stu-id="5c447-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="5c447-122">Wynika to z faktu, że wszystkie dane przechowywane w zmiennej późnej powiązania muszą być opakowane jako typ `Object` i dostęp do elementów członkowskich typu w czasie wykonywania sprawia, że program jest wolniejszy.</span><span class="sxs-lookup"><span data-stu-id="5c447-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>

## <a name="examples"></a><span data-ttu-id="5c447-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5c447-123">Examples</span></span>

<span data-ttu-id="5c447-124">Wnioskowanie o typie występuje, gdy zmienna lokalna jest zadeklarowana bez klauzuli `As` i została zainicjowana.</span><span class="sxs-lookup"><span data-stu-id="5c447-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="5c447-125">Kompilator używa typu przypisanej wartości początkowej jako typu zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5c447-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="5c447-126">Na przykład każdy z poniższych wierszy kodu deklaruje zmienną typu `String`.</span><span class="sxs-lookup"><span data-stu-id="5c447-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>

[!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]

<span data-ttu-id="5c447-127">Poniższy kod ilustruje dwa równoważne sposoby tworzenia tablicy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="5c447-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]

<span data-ttu-id="5c447-128">Użycie wnioskowania typu w celu określenia typu zmiennej kontrolnej pętli.</span><span class="sxs-lookup"><span data-stu-id="5c447-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="5c447-129">W poniższym kodzie kompilator wnioskuje, że `number` jest `Integer`, ponieważ `someNumbers2` z poprzedniego przykładu jest tablicą liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="5c447-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>

[!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]

<span data-ttu-id="5c447-130">Wnioskowanie o typie lokalnym może być używane w instrukcjach `Using` do ustalenia typu nazwy zasobu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c447-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>

[!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]

<span data-ttu-id="5c447-131">Typ zmiennej może być również wywnioskowany na podstawie zwracanych wartości funkcji, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5c447-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="5c447-132">Zarówno `pList1`, jak i `pList2` są tablicami procesów, ponieważ `Process.GetProcesses` zwraca tablicę procesów.</span><span class="sxs-lookup"><span data-stu-id="5c447-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>

[!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]

## <a name="option-infer"></a><span data-ttu-id="5c447-133">Wnioskowanie dotyczące opcji</span><span class="sxs-lookup"><span data-stu-id="5c447-133">Option Infer</span></span>

<span data-ttu-id="5c447-134">`Option Infer` umożliwia określenie, czy w określonym pliku jest dozwolone wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="5c447-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="5c447-135">Aby włączyć lub zablokować opcję, wpisz jedną z poniższych instrukcji na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="5c447-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>

`Option Infer On`

`Option Infer Off`

<span data-ttu-id="5c447-136">Jeśli nie określisz wartości dla `Option Infer` w kodzie, domyślnym kompilatorem jest `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="5c447-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span>

<span data-ttu-id="5c447-137">Jeśli wartość ustawiona dla `Option Infer` w pliku powoduje konflikt z wartością ustawioną w środowisku IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="5c447-137">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="5c447-138">Aby uzyskać więcej informacji, zobacz temat [opcja wnioskowanie](../../../../visual-basic/language-reference/statements/option-infer-statement.md) i [Strona kompilacja, projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5c447-138">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

## <a name="see-also"></a><span data-ttu-id="5c447-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c447-139">See also</span></span>

- [<span data-ttu-id="5c447-140">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="5c447-140">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="5c447-141">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="5c447-141">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="5c447-142">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5c447-142">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="5c447-143">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5c447-143">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="5c447-144">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5c447-144">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="5c447-145">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="5c447-145">-optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="5c447-146">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c447-146">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
