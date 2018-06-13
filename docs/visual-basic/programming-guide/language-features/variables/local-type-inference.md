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
ms.openlocfilehash: b33b8b2d17c240e380377528d4f5d2f511381a7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655326"
---
# <a name="local-type-inference-visual-basic"></a><span data-ttu-id="479f3-102">Wnioskowanie o typie lokalnym (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="479f3-102">Local Type Inference (Visual Basic)</span></span>
<span data-ttu-id="479f3-103">Kompilator Visual Basic używa *wnioskowanie* do określania typów danych zmienna lokalna zadeklarowana bez `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="479f3-103">The Visual Basic compiler uses *type inference* to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="479f3-104">Kompilator wnioskuje typ zmiennej typu wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="479f3-104">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="479f3-105">Dzięki temu można zadeklarować zmienne bez jawne określenie typu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="479f3-105">This enables you to declare variables without explicitly stating a type, as shown in the following example.</span></span> <span data-ttu-id="479f3-106">W wyniku deklaracjami zarówno `num1` i `num2` są silnie typizowane liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="479f3-106">As a result of the declarations, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_1.vb)]  
 
> [!NOTE]
>  <span data-ttu-id="479f3-107">Jeśli nie chcesz `num2` w poprzednim przykładzie, aby wpisać jako `Integer`, można określić innego typu za pomocą deklaracji, takich jak `Dim num3 As Object = 3` lub `Dim num4 As Double = 3`.</span><span class="sxs-lookup"><span data-stu-id="479f3-107">If you do not want `num2` in the previous example to be typed as an `Integer`, you can specify another type by using a declaration like `Dim num3 As Object = 3` or `Dim num4 As Double = 3`.</span></span>  

> [!NOTE]
>  <span data-ttu-id="479f3-108">Wnioskowanie o typie mogą służyć tylko dla zmiennych lokalnych niestatyczna; Nie można określić typu pola klasy, właściwości lub funkcji.</span><span class="sxs-lookup"><span data-stu-id="479f3-108">Type inference can be used only for non-static local variables; it cannot be used to determine the type of class fields, properties, or functions.</span></span>
 
 <span data-ttu-id="479f3-109">Wnioskowanie o typie lokalnym stosowana na poziomie procedury.</span><span class="sxs-lookup"><span data-stu-id="479f3-109">Local type inference applies at procedure level.</span></span> <span data-ttu-id="479f3-110">Nie można zadeklarować zmienne na poziomie modułu (w ramach klasy, struktury, modułu lub interfejs jednak nie wcześniej niż procedurę lub blok).</span><span class="sxs-lookup"><span data-stu-id="479f3-110">It cannot be used to declare variables at module level (within a class, structure, module, or interface but not within a procedure or block).</span></span> <span data-ttu-id="479f3-111">Jeśli `num2` w poprzednim przykładzie zostały pola klasy zamiast zmiennej lokalnej w procedurze, deklaracji mogłoby spowodować błąd `Option Strict` i czy sklasyfikować `num2` jako `Object` z `Option Strict` off.</span><span class="sxs-lookup"><span data-stu-id="479f3-111">If `num2` in the previous example were a field of a class instead of a local variable in a procedure, the declaration would cause an error with `Option Strict` on, and would classify `num2` as an `Object` with `Option Strict` off.</span></span> <span data-ttu-id="479f3-112">Podobnie, wnioskowanie o typie lokalnym nie ma zastosowania do zmiennych poziomu procedury zadeklarowany jako `Static`.</span><span class="sxs-lookup"><span data-stu-id="479f3-112">Similarly, local type inference does not apply to procedure level variables declared as `Static`.</span></span>  
  
## <a name="type-inference-vs-late-binding"></a><span data-ttu-id="479f3-113">Wpisz wnioskowania vs. Późne wiązanie</span><span class="sxs-lookup"><span data-stu-id="479f3-113">Type Inference vs. Late Binding</span></span>  
 <span data-ttu-id="479f3-114">Kod używa wnioskowanie typu podobny kod, który korzysta z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="479f3-114">Code that uses type inference resembles code that relies on late binding.</span></span> <span data-ttu-id="479f3-115">Jednak wnioskowanie o typie silnie typy zmiennej zamiast zostawiać je jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="479f3-115">However, type inference strongly types the variable instead of leaving it as `Object`.</span></span> <span data-ttu-id="479f3-116">Kompilator używa inicjator zmiennej można określić typu zmienną w czasie kompilacji, aby wygenerować kod z wczesnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="479f3-116">The compiler uses a variable's initializer to determine the variable's type at compile time to produce early-bound code.</span></span> <span data-ttu-id="479f3-117">W poprzednim przykładzie `num2`, takiej jak `num1`, jest typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="479f3-117">In the previous example, `num2`, like `num1`, is typed as an `Integer`.</span></span>  
  
 <span data-ttu-id="479f3-118">Zachowanie zmiennych z wczesnym wiązaniem różni się od zmiennych z późnym wiązaniem, dla których typ jest znany tylko w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="479f3-118">The behavior of early-bound variables differs from that of late-bound variables, for which the type is known only at run time.</span></span> <span data-ttu-id="479f3-119">Znajomość typu wczesne włącza kompilator, aby zidentyfikować problemy przed realizacją, dokładnie przydzielić pamięci i wykonywać inne optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="479f3-119">Knowing the type early enables the compiler to identify problems before execution, allocate memory precisely, and perform other optimizations.</span></span> <span data-ttu-id="479f3-120">Wczesne powiązania umożliwia również Visual Basic zintegrowane środowisko programistyczne (IDE), aby zapewnić pomoc IntelliSense dotyczących elementów członkowskich obiektu.</span><span class="sxs-lookup"><span data-stu-id="479f3-120">Early binding also enables the Visual Basic integrated development environment (IDE) to provide IntelliSense Help about the members of an object.</span></span> <span data-ttu-id="479f3-121">Wczesne powiązania jest również preferowane wydajności.</span><span class="sxs-lookup"><span data-stu-id="479f3-121">Early binding is also preferred for performance.</span></span> <span data-ttu-id="479f3-122">Jest to spowodowane wszystkie dane przechowywane w zmiennej późnym wiązaniem musi być zawijany jako typ `Object`, i uzyskiwanie dostępu do elementów członkowskich tego typu w czasie wykonywania sprawia, że program wolniej.</span><span class="sxs-lookup"><span data-stu-id="479f3-122">This is because all data stored in a late-bound variable must be wrapped as type `Object`, and accessing members of the type at run time makes the program slower.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="479f3-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="479f3-123">Examples</span></span>  
 <span data-ttu-id="479f3-124">Wnioskowanie o typie występuje, gdy zmienna lokalna jest zadeklarowana bez `As` klauzuli i zainicjować.</span><span class="sxs-lookup"><span data-stu-id="479f3-124">Type inference occurs when a local variable is declared without an `As` clause and initialized.</span></span> <span data-ttu-id="479f3-125">Kompilator używa typu przypisanej wartości początkowej typu zmienną.</span><span class="sxs-lookup"><span data-stu-id="479f3-125">The compiler uses the type of the assigned initial value as the type of the variable.</span></span> <span data-ttu-id="479f3-126">Na przykład, każdy z poniższych wierszy kodu deklaruje zmienną typu `String`.</span><span class="sxs-lookup"><span data-stu-id="479f3-126">For example, each of the following lines of code declares a variable of type `String`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_2.vb)]  
  
 <span data-ttu-id="479f3-127">Poniższy kod przedstawia dwa sposoby równoważne do utworzenia tablicy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="479f3-127">The following code demonstrates two equivalent ways to create an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_3.vb)]  
  
 <span data-ttu-id="479f3-128">Jest to łatwe w użyciu wnioskowanie o typie można określić typu zmienna sterująca pętli for.</span><span class="sxs-lookup"><span data-stu-id="479f3-128">It is convenient to use type inference to determine the type of a loop control variable.</span></span> <span data-ttu-id="479f3-129">W poniższym kodzie kompilator wnioskuje który `number` jest `Integer` ponieważ `someNumbers2` z poprzedniego przykładu jest tablica liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="479f3-129">In the following code, the compiler infers that `number` is an `Integer` because `someNumbers2` from the previous example is an array of integers.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_4.vb)]  
  
 <span data-ttu-id="479f3-130">Wnioskowanie o typie lokalnym mogą być używane w `Using` instrukcje w celu ustalenia typu nazwa zasobu, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="479f3-130">Local type inference can be used in `Using` statements to establish the type of the resource name, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_5.vb)]  
  
 <span data-ttu-id="479f3-131">Typ zmiennej również można wywnioskować na podstawie wartości zwracanych z funkcji, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="479f3-131">The type of a variable can also be inferred from the return values of functions, as the following example demonstrates.</span></span> <span data-ttu-id="479f3-132">Zarówno `pList1` i `pList2` są tablice procesy, ponieważ `Process.GetProcesses` zwraca tablicę procesów.</span><span class="sxs-lookup"><span data-stu-id="479f3-132">Both `pList1` and `pList2` are arrays of processes because `Process.GetProcesses` returns an array of processes.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/local-type-inference_6.vb)]  
  
## <a name="option-infer"></a><span data-ttu-id="479f3-133">Option Infer</span><span class="sxs-lookup"><span data-stu-id="479f3-133">Option Infer</span></span>  
 <span data-ttu-id="479f3-134">`Option Infer` Ta funkcja umożliwia określenie, czy wnioskowanie o typie lokalnym jest dozwolone w pliku.</span><span class="sxs-lookup"><span data-stu-id="479f3-134">`Option Infer` enables you specify whether local type inference is allowed in a particular file.</span></span> <span data-ttu-id="479f3-135">Aby włączyć lub opcji, wpisz jedno z następujących instrukcji na początku pliku.</span><span class="sxs-lookup"><span data-stu-id="479f3-135">To enable or to block the option, type one of the following statements at the start of the file.</span></span>  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 <span data-ttu-id="479f3-136">Jeśli nie określisz wartości `Option Infer` w kodzie domyślnym kompilatora jest `Option Infer On`.</span><span class="sxs-lookup"><span data-stu-id="479f3-136">If you do not specify a value for `Option Infer` in your code, the compiler default is `Option Infer On`.</span></span> <span data-ttu-id="479f3-137">Dla projektów uaktualnione z [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] lub starszym, jest domyślną kompilatora `Option Infer Off`.</span><span class="sxs-lookup"><span data-stu-id="479f3-137">For projects upgraded from [!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)] or earlier, the compiler default is `Option Infer Off`.</span></span>  
  
 <span data-ttu-id="479f3-138">Jeśli ustawiona wartość `Option Infer` w pliku powoduje konflikt z wartością ustawioną w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="479f3-138">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="479f3-139">Aby uzyskać więcej informacji, zobacz [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md) i [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="479f3-139">For more information, see [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="479f3-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="479f3-140">See Also</span></span>  
 [<span data-ttu-id="479f3-141">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="479f3-141">Anonymous Types</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [<span data-ttu-id="479f3-142">Wczesne i późne powiązania</span><span class="sxs-lookup"><span data-stu-id="479f3-142">Early and Late Binding</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="479f3-143">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="479f3-143">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="479f3-144">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="479f3-144">For...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="479f3-145">Option Infer, instrukcja</span><span class="sxs-lookup"><span data-stu-id="479f3-145">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="479f3-146">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="479f3-146">/optioninfer</span></span>](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="479f3-147">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="479f3-147">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
