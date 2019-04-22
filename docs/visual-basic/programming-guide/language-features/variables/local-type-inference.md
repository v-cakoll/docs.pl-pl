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
ms.openlocfilehash: e6214938262b987a1bae4a9ca1d5c945f8b7fe6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826824"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="3f016-102">Wnioskowanie o typie lokalnym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f016-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="3f016-103">Kompilator języka Visual Basic używa *wnioskowanie o typie* Aby określić typy danych zmiennych lokalnych zadeklarowana bez `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3f016-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="3f016-104">Kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="3f016-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="3f016-105">Dzięki temu można deklarować zmienne bez jawne określenie typu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3f016-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="3f016-106">W wyniku deklaracji zarówno `num1` i `num2` są silnie typizowane jako liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="3f016-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  <span data-ttu-id="3f016-107">Jeśli nie chcesz `num2` w poprzednim przykładzie, aby wpisać jako `Integer`, można określić inny typ za pomocą deklaracji, takich jak `Dim num3 As Object = 3` lub `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="3f016-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="3f016-108">Wnioskowanie o typie mogą służyć tylko dla zmiennych lokalnych niestatycznych; Nie można określić typu klasy, pola, właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="3f016-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="3f016-109">Wnioskowanie o typie lokalnym ma zastosowanie na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="3f016-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="3f016-110">Nie można zadeklarować zmienne na poziomie modułu (w obrębie klasy, struktury, modułu lub interfejsu ale nie w obrębie procedurę lub blok).</span><span class="sxs-lookup"><span data-stu-id="3f016-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="3f016-111">Jeśli `num2` w poprzednim przykładzie był to pole klasy zamiast zmiennej lokalnej w procedurze, deklaracja spowodowałoby błąd `Option Strict` i czy sklasyfikować `num2` jako `Object` z `Option Strict` wyłączone.</span><span class="sxs-lookup"><span data-stu-id="3f016-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="3f016-112">Podobnie, wnioskowanie o typie lokalnym nie ma zastosowania do procedury zmienne poziomu zadeklarowane jako `Static`.</span><span class="sxs-lookup"><span data-stu-id="3f016-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="3f016-113">Wpisz vs wnioskowania. Późne powiązania</span><span class="sxs-lookup"><span data-stu-id="3f016-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="3f016-114">Kod używa wnioskowanie o typie jest podobny do kodu, która korzysta z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="3f016-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="3f016-115">Jednak wnioskowanie o typie silnie typy zmiennych, zamiast zostawiać je jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="3f016-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="3f016-116">Kompilator używa inicjator zmiennej do określenia typu w czasie kompilacji, aby wygenerować kod z wczesnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="3f016-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="3f016-117">W poprzednim przykładzie `num2`, takiej jak `num1`, jest `Integer`.</span><span class="sxs-lookup"><span data-stu-id="3f016-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="3f016-118">Zachowanie zmiennych wczesnym wiązaniem różni się od zmiennych z późnym wiązaniem, dla których typ jest znana dopiero w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3f016-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="3f016-119">Wcześnie, wiedząc typu umożliwia kompilatorowi zidentyfikować problemy przed wykonaniem, dokładnie przydzielić pamięci i wykonywać inne optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="3f016-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="3f016-120">Wczesne powiązania umożliwia także języka Visual Basic zintegrowanego środowiska programistycznego (IDE), aby zapewnić pomoc IntelliSense dotyczących elementów członkowskich obiektu.</span><span class="sxs-lookup"><span data-stu-id="3f016-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="3f016-121">Wczesne powiązania jest również preferowana dla wydajności.</span><span class="sxs-lookup"><span data-stu-id="3f016-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="3f016-122">Jest to spowodowane wszystkie dane przechowywane w zmiennej z późnym wiązaniem muszą być zapakowane jako typ `Object`, i uzyskiwanie dostępu do elementów członkowskich typu w czasie wykonywania sprawia, że program wolniej.</span><span class="sxs-lookup"><span data-stu-id="3f016-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="3f016-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3f016-123">Examples</span></span>  
 <span data-ttu-id="3f016-124">Wnioskowanie o typie występuje, gdy zmienna lokalna jest zadeklarowana bez `As` klauzuli i zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="3f016-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="3f016-125">Kompilator używa typ przypisaną wartością początkową jako typ zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3f016-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="3f016-126">Na przykład, każda następujące wiersze kodu deklaruje zmienną typu `String`.</span><span class="sxs-lookup"><span data-stu-id="3f016-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 <span data-ttu-id="3f016-127">Poniższy kod przedstawia dwa sposoby równoważne do utworzenia tablicy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="3f016-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 <span data-ttu-id="3f016-128">Jest łatwa w użyciu wnioskowanie o typie, aby określić typ zmienna sterująca pętli.</span><span class="sxs-lookup"><span data-stu-id="3f016-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="3f016-129">W poniższym kodzie, kompilator wnioskuje, że `number` jest `Integer` ponieważ `someNumbers2` z poprzedniego przykładu jest tablicy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="3f016-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 <span data-ttu-id="3f016-130">Wnioskowanie o typie lokalnym mogą być używane w `Using` instrukcje, aby ustanowić wpisz nazwę zasobu, tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3f016-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 <span data-ttu-id="3f016-131">Również można wywnioskować typu zmiennej na podstawie wartości zwracane funkcji, tak jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="3f016-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="3f016-132">Zarówno `pList1` i `pList2` są tablicami procesów, ponieważ `Process.GetProcesses` zwraca tablicę procesów.</span><span class="sxs-lookup"><span data-stu-id="3f016-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a><span data-ttu-id="3f016-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="3f016-133">Option Infer</span></span>  
 <span data-ttu-id="3f016-134">`Option Infer` Umożliwia określenie, czy wnioskowanie o typie lokalnym jest dozwolone w określonym pliku.</span><span class="sxs-lookup"><span data-stu-id="3f016-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="3f016-135">Aby włączyć lub Blokuj opcję, należy wpisać jedną z następujących instrukcji na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="3f016-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="3f016-136">Jeśli nie określisz wartości `Option Infer` w kodzie jest domyślna wartość kompilatora `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="3f016-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="3f016-137">Dla projektów uaktualniony z [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] lub wcześniej, domyślna wartość kompilatora `Option Infer Off`.</span><span class="sxs-lookup"><span data-stu-id="3f016-137">For projects upgraded from [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="3f016-138">Jeśli ustawiono wartość `Option Infer` w pliku powoduje konflikt z wartości ustawionej w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="3f016-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="3f016-139">Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md) i [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3f016-139">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f016-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f016-140">See also</span></span>

- [<span data-ttu-id="3f016-141">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="3f016-141">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="3f016-142">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="3f016-142">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="3f016-143">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3f016-143">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="3f016-144">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3f016-144">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="3f016-145">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3f016-145">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="3f016-146">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="3f016-146">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="3f016-147">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f016-147">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
