---
title: Instrukcja wnioskowania opcji (Visual Basic)
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
ms.openlocfilehash: e7f5fcc6d76f654f53eea6677962cb097e98b881
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912302"
---
# <a name="option-infer-statement"></a><span data-ttu-id="625dd-102">Option Infer — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="625dd-102">Option Infer Statement</span></span>
<span data-ttu-id="625dd-103">Umożliwia użycie wnioskowania o typie lokalnym podczas deklarowania zmiennych.</span><span class="sxs-lookup"><span data-stu-id="625dd-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="625dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="625dd-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="625dd-105">Części</span><span class="sxs-lookup"><span data-stu-id="625dd-105">Parts</span></span>  
  
|<span data-ttu-id="625dd-106">Termin</span><span class="sxs-lookup"><span data-stu-id="625dd-106">Term</span></span>|<span data-ttu-id="625dd-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="625dd-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="625dd-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="625dd-108">Optional.</span></span> <span data-ttu-id="625dd-109">Włącza wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="625dd-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="625dd-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="625dd-110">Optional.</span></span> <span data-ttu-id="625dd-111">Wyłącza wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="625dd-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="625dd-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="625dd-112">Remarks</span></span>  
 <span data-ttu-id="625dd-113">Aby ustawić `Option Infer` w pliku, wpisz `Option Infer On` lub `Option Infer Off` w górnej części pliku przed jakimkolwiek innym kodem źródłowym.</span><span class="sxs-lookup"><span data-stu-id="625dd-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="625dd-114">Jeśli wartość ustawiona dla `Option Infer` w pliku powoduje konflikt z wartością ustawioną w środowisku IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="625dd-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="625dd-115">Po ustawieniu na `Option Infer` `On`wartość można zadeklarować zmienne lokalne bez jawnego wypełniania typu danych.</span><span class="sxs-lookup"><span data-stu-id="625dd-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="625dd-116">Kompilator wnioskuje typ danych zmiennej z typu wyrażenia inicjującego.</span><span class="sxs-lookup"><span data-stu-id="625dd-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="625dd-117">Na poniższej ilustracji `Option Infer` jest włączona.</span><span class="sxs-lookup"><span data-stu-id="625dd-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="625dd-118">Zmienna w deklaracji `Dim someVar = 2` jest zadeklarowana jako liczba całkowita przez wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="625dd-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

 <span data-ttu-id="625dd-119">Poniższy zrzut ekranu przedstawia technologię IntelliSense, gdy jest włączona opcja wnioskowanie:</span><span class="sxs-lookup"><span data-stu-id="625dd-119">The following screenshot shows IntelliSense when Option Infer is on:</span></span> 
  
 ![Zrzut ekranu przedstawiający widok IntelliSense, gdy opcja wnioskowanie jest włączona.](./media/option-infer-statement/option-infer-as-integer-on.png)  
  
 <span data-ttu-id="625dd-121">Na poniższej ilustracji `Option Infer` jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="625dd-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="625dd-122">Zmienna w deklaracji `Dim someVar = 2` jest zadeklarowana `Object` jako wnioskowanie typu przez.</span><span class="sxs-lookup"><span data-stu-id="625dd-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="625dd-123">W tym przykładzie ustawienie **Option Strict** jest **wyłączone** na [stronie kompilacja, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="625dd-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="625dd-124">Poniższy zrzut ekranu przedstawia funkcję IntelliSense, gdy wywnioskowanie opcji jest wyłączone:</span><span class="sxs-lookup"><span data-stu-id="625dd-124">The following screenshot shows IntelliSense when Option Infer is off:</span></span>
 
 ![Zrzut ekranu przedstawiający widok IntelliSense, gdy wywnioskowanie opcji jest wyłączone.](./media/option-infer-statement/option-infer-as-object-off.png)  
  
> [!NOTE]
> <span data-ttu-id="625dd-126">Gdy zmienna jest zadeklarowana jako `Object`, typ czasu wykonywania może ulec zmianie, gdy program jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="625dd-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="625dd-127">Visual Basic wykonuje operacje nazywane opakowaniem i rozpakowywaniem w celu `Object` konwersji między i typu wartości, co powoduje wolniejsze wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="625dd-127">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="625dd-128">Aby uzyskać informacje na temat pakowania i rozpakowywania, zobacz [Specyfikacja języka Visual Basic](~/_vblang/spec/conversions.md#value-type-conversions).</span><span class="sxs-lookup"><span data-stu-id="625dd-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>
  
 <span data-ttu-id="625dd-129">Wnioskowanie o typie ma zastosowanie na poziomie procedury i nie ma zastosowania poza procedurą w klasie, strukturze, module lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="625dd-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="625dd-130">Aby uzyskać dodatkowe informacje, zobacz temat wnioskowanie o [typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="625dd-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="625dd-131">Gdy nie ma instrukcji wnioskowania o opcji</span><span class="sxs-lookup"><span data-stu-id="625dd-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="625dd-132">Jeśli kod źródłowy nie zawiera `Option Infer` instrukcji, zostanie użyta **opcja wnioskowanie** dotyczące ustawienia na [stronie kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="625dd-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="625dd-133">Jeśli używany jest kompilator wiersza polecenia, opcja kompilatora [/optioninfer —](../../../visual-basic/reference/command-line-compiler/optioninfer.md) jest używana.</span><span class="sxs-lookup"><span data-stu-id="625dd-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="625dd-134">Aby ustawić wnioskowanie opcji w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="625dd-134">To set Option Infer in the IDE</span></span>  
  
1. <span data-ttu-id="625dd-135">W **Eksplorator rozwiązań**wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="625dd-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="625dd-136">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="625dd-136">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="625dd-137">Kliknij kartę **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="625dd-137">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="625dd-138">Ustaw wartość w polu wnioskowanie dotyczące **opcji** .</span><span class="sxs-lookup"><span data-stu-id="625dd-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="625dd-139">Podczas tworzenia nowego projektu, **opcja wnioskowanie opcji** na karcie Kompilowanie ma ustawioną wartość ustawienia **wnioskowania** w oknie dialogowym **Ustawienia domyślne języka vb** .</span><span class="sxs-lookup"><span data-stu-id="625dd-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="625dd-140">Aby uzyskać dostęp do okna dialogowego **Ustawienia domyślne VB** , w menu **Narzędzia** kliknij polecenie **Opcje**.</span><span class="sxs-lookup"><span data-stu-id="625dd-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="625dd-141">W oknie dialogowym **Opcje** rozwiń węzeł **projekty i rozwiązania**, a następnie kliknij pozycję **Ustawienia domyślne w języku VB**.</span><span class="sxs-lookup"><span data-stu-id="625dd-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="625dd-142">Początkowe domyślne ustawienie w **języku VB** domyślnie ma `On`wartość.</span><span class="sxs-lookup"><span data-stu-id="625dd-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="625dd-143">Aby ustawić wnioskowanie opcji w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="625dd-143">To set Option Infer on the command line</span></span>  
  
- <span data-ttu-id="625dd-144">Dołącz opcję kompilatora [/optioninfer —](../../../visual-basic/reference/command-line-compiler/optioninfer.md) do polecenia **VBC** .</span><span class="sxs-lookup"><span data-stu-id="625dd-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="625dd-145">Domyślne typy danych i wartości</span><span class="sxs-lookup"><span data-stu-id="625dd-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="625dd-146">W poniższej tabeli opisano wyniki różnych kombinacji określania typu danych i inicjatora w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="625dd-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="625dd-147">Określono typ danych?</span><span class="sxs-lookup"><span data-stu-id="625dd-147">Data type specified?</span></span>|<span data-ttu-id="625dd-148">Określono inicjator?</span><span class="sxs-lookup"><span data-stu-id="625dd-148">Initializer specified?</span></span>|<span data-ttu-id="625dd-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="625dd-149">Example</span></span>|<span data-ttu-id="625dd-150">Wynik</span><span class="sxs-lookup"><span data-stu-id="625dd-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="625dd-151">Nie</span><span class="sxs-lookup"><span data-stu-id="625dd-151">No</span></span>|<span data-ttu-id="625dd-152">Nie</span><span class="sxs-lookup"><span data-stu-id="625dd-152">No</span></span>|`Dim qty`|<span data-ttu-id="625dd-153">Jeśli `Option Strict` jest wyłączone (wartość domyślna), zmienna jest ustawiona na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="625dd-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="625dd-154">Jeśli `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="625dd-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="625dd-155">Nie</span><span class="sxs-lookup"><span data-stu-id="625dd-155">No</span></span>|<span data-ttu-id="625dd-156">Tak</span><span class="sxs-lookup"><span data-stu-id="625dd-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="625dd-157">Jeśli `Option Infer` jest włączone (wartość domyślna), zmienna Pobiera typ danych inicjatora.</span><span class="sxs-lookup"><span data-stu-id="625dd-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="625dd-158">Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="625dd-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="625dd-159">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączona, zmienna `Object`Pobiera typ danych.</span><span class="sxs-lookup"><span data-stu-id="625dd-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="625dd-160">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="625dd-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="625dd-161">Tak</span><span class="sxs-lookup"><span data-stu-id="625dd-161">Yes</span></span>|<span data-ttu-id="625dd-162">Nie</span><span class="sxs-lookup"><span data-stu-id="625dd-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="625dd-163">Zmienna jest inicjowana do wartości domyślnej dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="625dd-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="625dd-164">Aby uzyskać więcej informacji, zobacz [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="625dd-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="625dd-165">Tak</span><span class="sxs-lookup"><span data-stu-id="625dd-165">Yes</span></span>|<span data-ttu-id="625dd-166">Tak</span><span class="sxs-lookup"><span data-stu-id="625dd-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="625dd-167">Jeśli typ danych inicjatora nie zostanie przekonwertowany na określony typ danych, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="625dd-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="625dd-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="625dd-168">Example</span></span>  
 <span data-ttu-id="625dd-169">W poniższych przykładach pokazano, `Option Infer` jak instrukcja włącza wnioskowanie typu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="625dd-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="625dd-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="625dd-170">Example</span></span>  
 <span data-ttu-id="625dd-171">Poniższy przykład pokazuje, że typ czasu wykonywania może się różnić, gdy zmienna jest identyfikowana jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="625dd-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="625dd-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="625dd-172">See also</span></span>

- [<span data-ttu-id="625dd-173">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="625dd-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="625dd-174">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="625dd-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="625dd-175">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="625dd-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [<span data-ttu-id="625dd-176">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="625dd-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="625dd-177">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="625dd-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="625dd-178">Domyślne ustawienia programu Visual Basic, Projekty, Opcje — okno dialogowe</span><span class="sxs-lookup"><span data-stu-id="625dd-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="625dd-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="625dd-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="625dd-180">Konwersja boxing i konwersja unboxing</span><span class="sxs-lookup"><span data-stu-id="625dd-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
