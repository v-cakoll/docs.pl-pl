---
title: Option Infer — Instrukcja
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 72
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c8bd94bc8dd379edfda8c4350428684a5cda0b1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="option-infer-statement"></a><span data-ttu-id="e5540-102">Option Infer — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5540-102">Option Infer Statement</span></span>
<span data-ttu-id="e5540-103">Umożliwia użycie wnioskowania o typie lokalnym przy deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="e5540-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5540-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5540-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="e5540-105">Części</span><span class="sxs-lookup"><span data-stu-id="e5540-105">Parts</span></span>  
  
|<span data-ttu-id="e5540-106">Termin</span><span class="sxs-lookup"><span data-stu-id="e5540-106">Term</span></span>|<span data-ttu-id="e5540-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="e5540-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="e5540-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e5540-108">Optional.</span></span> <span data-ttu-id="e5540-109">Umożliwia wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e5540-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="e5540-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e5540-110">Optional.</span></span> <span data-ttu-id="e5540-111">Wyłącza wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e5540-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5540-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5540-112">Remarks</span></span>  
 <span data-ttu-id="e5540-113">Aby ustawić `Option Infer` w pliku, wpisz `Option Infer On` lub `Option Infer Off` na początku pliku przed uruchomieniem jakiegokolwiek kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e5540-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="e5540-114">Jeśli ustawiona wartość `Option Infer` w pliku powoduje konflikt z wartością ustawioną w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="e5540-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="e5540-115">Podczas ustawiania `Option Infer` do `On`, zmienne lokalne mogą zadeklarować bez jawne określenie typu danych.</span><span class="sxs-lookup"><span data-stu-id="e5540-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="e5540-116">Kompilator wnioskuje typ danych zmiennej typu jej wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="e5540-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="e5540-117">Na poniższej ilustracji `Option Infer` jest włączona.</span><span class="sxs-lookup"><span data-stu-id="e5540-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="e5540-118">W deklaracji zmiennej `Dim someVar = 2` jest zadeklarowany jako liczba całkowita przez wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="e5540-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="e5540-119">![Widok IntelliSense deklaracji. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="e5540-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="e5540-120">IntelliSense po włączeniu Option Infer</span><span class="sxs-lookup"><span data-stu-id="e5540-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="e5540-121">Na poniższej ilustracji `Option Infer` jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="e5540-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="e5540-122">W deklaracji zmiennej `Dim someVar = 2` jest zadeklarowany jako `Object` przez wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="e5540-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="e5540-123">W tym przykładzie **Option Strict** mają ustawioną wartość **poza** na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e5540-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="e5540-124">![Widok IntelliSense deklaracji. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="e5540-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="e5540-125">IntelliSense po Option Infer jest wyłączone</span><span class="sxs-lookup"><span data-stu-id="e5540-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5540-126">Jeśli zmienna jest zadeklarowana jako `Object`, typu run-time można zmienić, gdy program jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="e5540-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="e5540-127">wykonuje operacje o nazwie *boxing* i *rozpakowującej* konwersję między `Object` a typem wartości, dzięki czemu wykonanie wolniej.</span><span class="sxs-lookup"><span data-stu-id="e5540-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="e5540-128">Aby uzyskać informacje o konwersji boxing i konwersja unboxing, zobacz [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e5540-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="e5540-129">Wnioskowanie o typie stosuje na poziomie procedury i nie ma zastosowania poza procedury w klasy, struktury, modułu lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="e5540-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="e5540-130">Aby uzyskać dodatkowe informacje, zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="e5540-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="e5540-131">Gdy Option Infer — instrukcja nie jest obecny</span><span class="sxs-lookup"><span data-stu-id="e5540-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="e5540-132">Jeśli kod źródłowy nie zawiera `Option Infer` instrukcji, **Option Infer** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany.</span><span class="sxs-lookup"><span data-stu-id="e5540-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="e5540-133">Jeśli używana jest kompilatora wiersza polecenia, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) — opcja kompilatora jest używany.</span><span class="sxs-lookup"><span data-stu-id="e5540-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="e5540-134">Aby ustawić Option Infer w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="e5540-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="e5540-135">W **Eksploratora rozwiązań**, wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="e5540-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="e5540-136">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e5540-136">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="e5540-137">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="e5540-137">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="e5540-138">Ustaw wartość **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="e5540-138">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="e5540-139">Podczas tworzenia nowego projektu **Option Infer** ustawienie **skompilować** ustawiono kartę **Option Infer** ustawienie **domyślne VB** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="e5540-139">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="e5540-140">Aby uzyskać dostęp do **domyślne VB** okna dialogowego, na **narzędzia** menu, kliknij przycisk **opcje**.</span><span class="sxs-lookup"><span data-stu-id="e5540-140">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="e5540-141">W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**.</span><span class="sxs-lookup"><span data-stu-id="e5540-141">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="e5540-142">Ustawieniem domyślnym początkowej w **domyślne VB** jest `On`.</span><span class="sxs-lookup"><span data-stu-id="e5540-142">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="e5540-143">Aby ustawić Option Infer w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="e5540-143">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="e5540-144">Obejmują [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) w — opcja kompilatora **vbc** polecenia.</span><span class="sxs-lookup"><span data-stu-id="e5540-144">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="e5540-145">Dane domyślne typy i wartości</span><span class="sxs-lookup"><span data-stu-id="e5540-145">Default Data Types and Values</span></span>  
 <span data-ttu-id="e5540-146">W poniższej tabeli przedstawiono wyniki określający typ danych oraz inicjator w różnych kombinacji `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e5540-146">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="e5540-147">Określony typ danych?</span><span class="sxs-lookup"><span data-stu-id="e5540-147">Data type specified?</span></span>|<span data-ttu-id="e5540-148">Inicjator określona?</span><span class="sxs-lookup"><span data-stu-id="e5540-148">Initializer specified?</span></span>|<span data-ttu-id="e5540-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5540-149">Example</span></span>|<span data-ttu-id="e5540-150">Wynik</span><span class="sxs-lookup"><span data-stu-id="e5540-150">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="e5540-151">Nie</span><span class="sxs-lookup"><span data-stu-id="e5540-151">No</span></span>|<span data-ttu-id="e5540-152">Nie</span><span class="sxs-lookup"><span data-stu-id="e5540-152">No</span></span>|`Dim qty`|<span data-ttu-id="e5540-153">Jeśli `Option Strict` jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e5540-153">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="e5540-154">Jeśli `Option Strict` jest włączone, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e5540-154">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="e5540-155">Nie</span><span class="sxs-lookup"><span data-stu-id="e5540-155">No</span></span>|<span data-ttu-id="e5540-156">Tak</span><span class="sxs-lookup"><span data-stu-id="e5540-156">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="e5540-157">Jeśli `Option Infer` znajduje się na (ustawienie domyślne), typ zmiennej przyjmuje dane inicjatora.</span><span class="sxs-lookup"><span data-stu-id="e5540-157">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="e5540-158">Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="e5540-158">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="e5540-159">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączony, zmienna ma typ danych `Object`.</span><span class="sxs-lookup"><span data-stu-id="e5540-159">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="e5540-160">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e5540-160">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="e5540-161">Tak</span><span class="sxs-lookup"><span data-stu-id="e5540-161">Yes</span></span>|<span data-ttu-id="e5540-162">Nie</span><span class="sxs-lookup"><span data-stu-id="e5540-162">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="e5540-163">Zmienna jest ustawiana na wartość domyślną dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="e5540-163">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="e5540-164">Aby uzyskać więcej informacji, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e5540-164">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="e5540-165">Tak</span><span class="sxs-lookup"><span data-stu-id="e5540-165">Yes</span></span>|<span data-ttu-id="e5540-166">Tak</span><span class="sxs-lookup"><span data-stu-id="e5540-166">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="e5540-167">Jeśli typ danych Inicjator nie jest możliwe do przekonwertowania na określony typ danych, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e5540-167">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e5540-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5540-168">Example</span></span>  
 <span data-ttu-id="e5540-169">W poniższych przykładach pokazano sposób `Option Infer` instrukcji umożliwia wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="e5540-169">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e5540-170">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5540-170">Example</span></span>  
 <span data-ttu-id="e5540-171">W poniższym przykładzie pokazano, że typu run-time może się różnić, gdy zmienna zostanie zidentyfikowana jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="e5540-171">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e5540-172">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5540-172">See Also</span></span>  
 [<span data-ttu-id="e5540-173">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5540-173">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="e5540-174">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="e5540-174">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="e5540-175">Option Compare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5540-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="e5540-176">Option Explicit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5540-176">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="e5540-177">Option Strict, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e5540-177">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="e5540-178">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5540-178">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="e5540-179">/optioninfer</span><span class="sxs-lookup"><span data-stu-id="e5540-179">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="e5540-180">Konwersja boxing i konwersja unboxing</span><span class="sxs-lookup"><span data-stu-id="e5540-180">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
