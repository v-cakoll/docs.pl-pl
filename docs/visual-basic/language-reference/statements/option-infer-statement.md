---
title: Option Infer — instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: 59766999c5b03aac7aec13b293feaa8c17f2ced0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338569"
---
# <a name="option-infer-statement"></a><span data-ttu-id="180f2-102">Option Infer — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="180f2-102">Option Infer Statement</span></span>
<span data-ttu-id="180f2-103">Umożliwia użycie wnioskowania o typie lokalnym w zadeklarowania zmiennych.</span><span class="sxs-lookup"><span data-stu-id="180f2-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="180f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="180f2-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="180f2-105">Części</span><span class="sxs-lookup"><span data-stu-id="180f2-105">Parts</span></span>  
  
|<span data-ttu-id="180f2-106">Termin</span><span class="sxs-lookup"><span data-stu-id="180f2-106">Term</span></span>|<span data-ttu-id="180f2-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="180f2-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="180f2-108">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="180f2-108">Optional.</span></span> <span data-ttu-id="180f2-109">Umożliwia wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="180f2-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="180f2-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="180f2-110">Optional.</span></span> <span data-ttu-id="180f2-111">Wyłącza wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="180f2-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="180f2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="180f2-112">Remarks</span></span>  
 <span data-ttu-id="180f2-113">Aby ustawić `Option Infer` w pliku, wpisz `Option Infer On` lub `Option Infer Off` w górnej części pliku, przed uruchomieniem jakiegokolwiek kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="180f2-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="180f2-114">Jeśli ustawiono wartość `Option Infer` w pliku powoduje konflikt z wartości ustawionej w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="180f2-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="180f2-115">Po ustawieniu `Option Infer` do `On`, zmienne lokalne można deklarować bez jawne określenie typu danych.</span><span class="sxs-lookup"><span data-stu-id="180f2-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="180f2-116">Kompilator wnioskuje typ danych zmiennej z typu jej wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="180f2-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="180f2-117">Na poniższej ilustracji `Option Infer` jest włączona.</span><span class="sxs-lookup"><span data-stu-id="180f2-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="180f2-118">Zmienna w deklaracji `Dim someVar = 2` jest zadeklarowany jako liczba całkowita, wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="180f2-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

 <span data-ttu-id="180f2-119">Poniższy zrzut ekranu przedstawia IntelliSense, gdy Option Infer znajduje się na:</span><span class="sxs-lookup"><span data-stu-id="180f2-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span> 
  
 ![Zrzut ekranu przedstawiający widok IntelliSense, gdy Option Infer znajduje się na.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 <span data-ttu-id="180f2-121">Na poniższej ilustracji `Option Infer` jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="180f2-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="180f2-122">Zmienna w deklaracji `Dim someVar = 2` jest zadeklarowany jako `Object` przez wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="180f2-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="180f2-123">W tym przykładzie **Option Strict** jest ustawiana **poza** na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="180f2-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="180f2-124">Poniższy zrzut ekranu przedstawia IntelliSense, gdy Option Infer jest wyłączony:</span><span class="sxs-lookup"><span data-stu-id="180f2-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>
 
 ![Zrzut ekranu przedstawiający widok IntelliSense, gdy Option Infer jest wyłączony.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
>  <span data-ttu-id="180f2-126">Gdy zmienna jest zadeklarowana jako `Object`, można zmienić typu run-time, gdy program jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="180f2-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="180f2-127">Visual Basic wykonuje operacje o nazwie *pakowania* i *Rozpakowywanie* do konwersji między `Object` i typie wartości, co sprawia, że wykonanie wolniej.</span><span class="sxs-lookup"><span data-stu-id="180f2-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="180f2-128">Uzyskać informacji o konwersji boxing i konwersja unboxing, zobacz [specyfikacja języka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="180f2-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>
  
 <span data-ttu-id="180f2-129">Wnioskowanie o typie ma zastosowanie na poziomie procedury i nie ma zastosowania poza procedury w klasie, strukturze, modułu lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="180f2-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="180f2-130">Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="180f2-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="180f2-131">Podczas Option Infer — instrukcja nie jest obecny</span><span class="sxs-lookup"><span data-stu-id="180f2-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="180f2-132">Jeśli kod źródłowy nie zawiera `Option Infer` instrukcji **Option Infer** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany.</span><span class="sxs-lookup"><span data-stu-id="180f2-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="180f2-133">Jeśli jest używany kompilator w wierszu polecenia, [/optioninfer —](../../../visual-basic/reference/command-line-compiler/optioninfer.md) — opcja kompilatora jest używany.</span><span class="sxs-lookup"><span data-stu-id="180f2-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="180f2-134">Aby ustawić Option Infer w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="180f2-134">To set Option Infer in the IDE</span></span>  
  
1. <span data-ttu-id="180f2-135">W **Eksploratora rozwiązań**, wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="180f2-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="180f2-136">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="180f2-136">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="180f2-137">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="180f2-137">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="180f2-138">Ustaw wartość w **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="180f2-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="180f2-139">Podczas tworzenia nowego projektu **Option Infer** ustawienie **skompilować** karta jest ustawiona na **Option Infer** w **ustawienia domyślne VB** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="180f2-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="180f2-140">Aby uzyskać dostęp do **ustawienia domyślne VB** dialogowym **narzędzia** menu, kliknij przycisk **opcje**.</span><span class="sxs-lookup"><span data-stu-id="180f2-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="180f2-141">W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **ustawienia domyślne VB**.</span><span class="sxs-lookup"><span data-stu-id="180f2-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="180f2-142">Ustawieniem domyślnym początkowej w **ustawienia domyślne VB** jest `On`.</span><span class="sxs-lookup"><span data-stu-id="180f2-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="180f2-143">Aby ustawić Option Infer w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="180f2-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="180f2-144">Obejmują [/optioninfer —](../../../visual-basic/reference/command-line-compiler/optioninfer.md) w — opcja kompilatora **vbc** polecenia.</span><span class="sxs-lookup"><span data-stu-id="180f2-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="180f2-145">Dane domyślne typy i wartości</span><span class="sxs-lookup"><span data-stu-id="180f2-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="180f2-146">W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="180f2-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="180f2-147">Określony typ danych?</span><span class="sxs-lookup"><span data-stu-id="180f2-147">Data type specified?</span></span>|<span data-ttu-id="180f2-148">Inicjatora określona?</span><span class="sxs-lookup"><span data-stu-id="180f2-148">Initializer specified?</span></span>|<span data-ttu-id="180f2-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="180f2-149">Example</span></span>|<span data-ttu-id="180f2-150">Wynik</span><span class="sxs-lookup"><span data-stu-id="180f2-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="180f2-151">Nie</span><span class="sxs-lookup"><span data-stu-id="180f2-151">No</span></span>|<span data-ttu-id="180f2-152">Nie</span><span class="sxs-lookup"><span data-stu-id="180f2-152">No</span></span>|`Dim qty`|<span data-ttu-id="180f2-153">Jeśli `Option Strict` jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="180f2-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="180f2-154">Jeśli `Option Strict` jest włączona, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="180f2-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="180f2-155">Nie</span><span class="sxs-lookup"><span data-stu-id="180f2-155">No</span></span>|<span data-ttu-id="180f2-156">Yes</span><span class="sxs-lookup"><span data-stu-id="180f2-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="180f2-157">Jeśli `Option Infer` znajduje się na (ustawienie domyślne), zmienna przyjmuje dane typu inicjatora.</span><span class="sxs-lookup"><span data-stu-id="180f2-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="180f2-158">Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="180f2-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="180f2-159">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączone, zmienna ma typ danych `Object`.</span><span class="sxs-lookup"><span data-stu-id="180f2-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="180f2-160">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="180f2-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="180f2-161">Yes</span><span class="sxs-lookup"><span data-stu-id="180f2-161">Yes</span></span>|<span data-ttu-id="180f2-162">Nie</span><span class="sxs-lookup"><span data-stu-id="180f2-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="180f2-163">Zmienna jest ustawiana na wartość domyślną dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="180f2-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="180f2-164">Aby uzyskać więcej informacji, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="180f2-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="180f2-165">Yes</span><span class="sxs-lookup"><span data-stu-id="180f2-165">Yes</span></span>|<span data-ttu-id="180f2-166">Tak</span><span class="sxs-lookup"><span data-stu-id="180f2-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="180f2-167">Jeśli typ danych Inicjator nie jest konwertowany na określony typ danych, wystąpi błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="180f2-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="180f2-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="180f2-168">Example</span></span>  
 <span data-ttu-id="180f2-169">W poniższych przykładach pokazano sposób, w jaki `Option Infer` instrukcji umożliwia wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="180f2-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="180f2-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="180f2-170">Example</span></span>  
 <span data-ttu-id="180f2-171">W poniższym przykładzie pokazano, że typu run-time może się różnić, gdy zmienna jest identyfikowany jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="180f2-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="180f2-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="180f2-172">See also</span></span>

- [<span data-ttu-id="180f2-173">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="180f2-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="180f2-174">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="180f2-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="180f2-175">Option Compare — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="180f2-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="180f2-176">Option Explicit — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="180f2-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="180f2-177">Option Strict — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="180f2-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="180f2-178">Domyślne ustawienia programu Visual Basic, Projekty, okno dialogowe Opcje</span><span class="sxs-lookup"><span data-stu-id="180f2-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="180f2-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="180f2-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="180f2-180">Opakowywanie i rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="180f2-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
