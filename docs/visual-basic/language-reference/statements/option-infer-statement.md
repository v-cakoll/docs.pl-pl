---
title: "Option Infer — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "72"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4634c198b5fc41a4834cbd3cd96f9d3f1863d09b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="option-infer-statement"></a><span data-ttu-id="61aac-102">Option Infer — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="61aac-102">Option Infer Statement</span></span>
<span data-ttu-id="61aac-103">Umożliwia użycie wnioskowania o typie lokalnym przy deklaracji zmiennych.</span><span class="sxs-lookup"><span data-stu-id="61aac-103">Enables the use of local type inference in declaring variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61aac-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61aac-104">Syntax</span></span>  
  
```  
Option Infer { On | Off }  
```  
  
## <a name="parts"></a><span data-ttu-id="61aac-105">Części</span><span class="sxs-lookup"><span data-stu-id="61aac-105">Parts</span></span>  
  
|<span data-ttu-id="61aac-106">Termin</span><span class="sxs-lookup"><span data-stu-id="61aac-106">Term</span></span>|<span data-ttu-id="61aac-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="61aac-107">Definition</span></span>|  
|---|---|  
|`On`|<span data-ttu-id="61aac-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="61aac-108">Optional.</span></span> <span data-ttu-id="61aac-109">Umożliwia wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="61aac-109">Enables local type inference.</span></span>|  
|`Off`|<span data-ttu-id="61aac-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="61aac-110">Optional.</span></span> <span data-ttu-id="61aac-111">Wyłącza wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="61aac-111">Disables local type inference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61aac-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61aac-112">Remarks</span></span>  
 <span data-ttu-id="61aac-113">Aby ustawić `Option Infer` w pliku, wpisz `Option Infer On` lub `Option Infer Off` na początku pliku przed uruchomieniem jakiegokolwiek kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="61aac-113">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="61aac-114">Jeśli ustawiona wartość `Option Infer` w pliku powoduje konflikt z wartością ustawioną w IDE lub w wierszu polecenia, wartość w pliku ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="61aac-114">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>  
  
 <span data-ttu-id="61aac-115">Podczas ustawiania `Option Infer` do `On`, zmienne lokalne mogą zadeklarować bez jawne określenie typu danych.</span><span class="sxs-lookup"><span data-stu-id="61aac-115">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="61aac-116">Kompilator wnioskuje typ danych zmiennej typu jej wyrażenia inicjowania.</span><span class="sxs-lookup"><span data-stu-id="61aac-116">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>  
  
 <span data-ttu-id="61aac-117">Na poniższej ilustracji `Option Infer` jest włączona.</span><span class="sxs-lookup"><span data-stu-id="61aac-117">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="61aac-118">W deklaracji zmiennej `Dim someVar = 2` jest zadeklarowany jako liczba całkowita przez wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="61aac-118">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>  
  
 <span data-ttu-id="61aac-119">![Widok IntelliSense deklaracji. ] (../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span><span class="sxs-lookup"><span data-stu-id="61aac-119">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasinteger.png "optionInferAsInteger")</span></span>  
<span data-ttu-id="61aac-120">IntelliSense po włączeniu Option Infer</span><span class="sxs-lookup"><span data-stu-id="61aac-120">IntelliSense when Option Infer is on</span></span>  
  
 <span data-ttu-id="61aac-121">Na poniższej ilustracji `Option Infer` jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="61aac-121">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="61aac-122">W deklaracji zmiennej `Dim someVar = 2` jest zadeklarowany jako `Object` przez wnioskowanie o typie.</span><span class="sxs-lookup"><span data-stu-id="61aac-122">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="61aac-123">W tym przykładzie **Option Strict** mają ustawioną wartość **poza** na [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="61aac-123">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
 <span data-ttu-id="61aac-124">![Widok IntelliSense deklaracji. ] (../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span><span class="sxs-lookup"><span data-stu-id="61aac-124">![IntelliSense view of the declaration.](../../../visual-basic/language-reference/statements/media/optioninferasobject.png "optionInferAsObject")</span></span>  
<span data-ttu-id="61aac-125">IntelliSense po Option Infer jest wyłączone</span><span class="sxs-lookup"><span data-stu-id="61aac-125">IntelliSense when Option Infer is off</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61aac-126">Jeśli zmienna jest zadeklarowana jako `Object`, typu run-time można zmienić, gdy program jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="61aac-126">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="61aac-127">wykonuje operacje o nazwie *boxing* i *rozpakowującej* konwersję między `Object` a typem wartości, dzięki czemu wykonanie wolniej.</span><span class="sxs-lookup"><span data-stu-id="61aac-127"> performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="61aac-128">Aby uzyskać informacje o konwersji boxing i konwersja unboxing, zobacz [specyfikacja języka Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="61aac-128">For information about boxing and unboxing, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="61aac-129">Wnioskowanie o typie stosuje na poziomie procedury i nie ma zastosowania poza procedury w klasy, struktury, modułu lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="61aac-129">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>  
  
 <span data-ttu-id="61aac-130">Aby uzyskać dodatkowe informacje, zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="61aac-130">For additional information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="61aac-131">Gdy Option Infer — instrukcja nie jest obecny</span><span class="sxs-lookup"><span data-stu-id="61aac-131">When an Option Infer Statement Is Not Present</span></span>  
 <span data-ttu-id="61aac-132">Jeśli kod źródłowy nie zawiera `Option Infer` instrukcji, **Option Infer** ustawienie [strona kompilowania, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) jest używany.</span><span class="sxs-lookup"><span data-stu-id="61aac-132">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="61aac-133">Jeśli używana jest kompilatora wiersza polecenia, [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) — opcja kompilatora jest używany.</span><span class="sxs-lookup"><span data-stu-id="61aac-133">If the command-line compiler is used, the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>  
  
#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="61aac-134">Aby ustawić Option Infer w środowisku IDE</span><span class="sxs-lookup"><span data-stu-id="61aac-134">To set Option Infer in the IDE</span></span>  
  
1.  <span data-ttu-id="61aac-135">W **Eksploratora rozwiązań**, wybierz projekt.</span><span class="sxs-lookup"><span data-stu-id="61aac-135">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="61aac-136">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="61aac-136">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="61aac-137">Aby uzyskać więcej informacji, zobacz [NIB: Zarządzanie właściwości projektu przy użyciu projektanta projektów](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span><span class="sxs-lookup"><span data-stu-id="61aac-137">For more information, see [NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/en-us/983f3c18-832f-4666-afec-74b716ff3e0e).</span></span>  
  
2.  <span data-ttu-id="61aac-138">Kliknij przycisk **skompilować** kartę.</span><span class="sxs-lookup"><span data-stu-id="61aac-138">Click the **Compile** tab.</span></span>  
  
3.  <span data-ttu-id="61aac-139">Ustaw wartość **Option infer** pole.</span><span class="sxs-lookup"><span data-stu-id="61aac-139">Set the value in the **Option infer** box.</span></span>  
  
 <span data-ttu-id="61aac-140">Podczas tworzenia nowego projektu **Option Infer** ustawienie **skompilować** ustawiono kartę **Option Infer** ustawienie **domyślne VB** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="61aac-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="61aac-141">Aby uzyskać dostęp do **domyślne VB** okna dialogowego, na **narzędzia** menu, kliknij przycisk **opcje**.</span><span class="sxs-lookup"><span data-stu-id="61aac-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="61aac-142">W **opcje** okna dialogowego rozwiń **projekty i rozwiązania**, a następnie kliknij przycisk **domyślne VB**.</span><span class="sxs-lookup"><span data-stu-id="61aac-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="61aac-143">Ustawieniem domyślnym początkowej w **domyślne VB** jest `On`.</span><span class="sxs-lookup"><span data-stu-id="61aac-143">The initial default setting in **VB Defaults** is `On`.</span></span>  
  
#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="61aac-144">Aby ustawić Option Infer w wierszu polecenia</span><span class="sxs-lookup"><span data-stu-id="61aac-144">To set Option Infer on the command line</span></span>  
  
-   <span data-ttu-id="61aac-145">Obejmują [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) w — opcja kompilatora **vbc** polecenia.</span><span class="sxs-lookup"><span data-stu-id="61aac-145">Include the [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="default-data-types-and-values"></a><span data-ttu-id="61aac-146">Dane domyślne typy i wartości</span><span class="sxs-lookup"><span data-stu-id="61aac-146">Default Data Types and Values</span></span>  
 <span data-ttu-id="61aac-147">W poniższej tabeli przedstawiono wyniki określający typ danych oraz inicjator w różnych kombinacji `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="61aac-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="61aac-148">Określony typ danych?</span><span class="sxs-lookup"><span data-stu-id="61aac-148">Data type specified?</span></span>|<span data-ttu-id="61aac-149">Inicjator określona?</span><span class="sxs-lookup"><span data-stu-id="61aac-149">Initializer specified?</span></span>|<span data-ttu-id="61aac-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="61aac-150">Example</span></span>|<span data-ttu-id="61aac-151">Wynik</span><span class="sxs-lookup"><span data-stu-id="61aac-151">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="61aac-152">Nie</span><span class="sxs-lookup"><span data-stu-id="61aac-152">No</span></span>|<span data-ttu-id="61aac-153">Nie</span><span class="sxs-lookup"><span data-stu-id="61aac-153">No</span></span>|`Dim qty`|<span data-ttu-id="61aac-154">Jeśli `Option Strict` jest wyłączone (domyślnie), zmienna jest ustawiana `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="61aac-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="61aac-155">Jeśli `Option Strict` jest włączone, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="61aac-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="61aac-156">Nie</span><span class="sxs-lookup"><span data-stu-id="61aac-156">No</span></span>|<span data-ttu-id="61aac-157">Tak</span><span class="sxs-lookup"><span data-stu-id="61aac-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="61aac-158">Jeśli `Option Infer` znajduje się na (ustawienie domyślne), typ zmiennej przyjmuje dane inicjatora.</span><span class="sxs-lookup"><span data-stu-id="61aac-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="61aac-159">Zobacz [wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="61aac-159">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="61aac-160">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest wyłączony, zmienna ma typ danych `Object`.</span><span class="sxs-lookup"><span data-stu-id="61aac-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="61aac-161">Jeśli `Option Infer` jest wyłączona i `Option Strict` jest włączona, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="61aac-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="61aac-162">Tak</span><span class="sxs-lookup"><span data-stu-id="61aac-162">Yes</span></span>|<span data-ttu-id="61aac-163">Nie</span><span class="sxs-lookup"><span data-stu-id="61aac-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="61aac-164">Zmienna jest ustawiana na wartość domyślną dla typu danych.</span><span class="sxs-lookup"><span data-stu-id="61aac-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="61aac-165">Aby uzyskać więcej informacji, zobacz [instrukcji Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="61aac-165">For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>|  
|<span data-ttu-id="61aac-166">Tak</span><span class="sxs-lookup"><span data-stu-id="61aac-166">Yes</span></span>|<span data-ttu-id="61aac-167">Tak</span><span class="sxs-lookup"><span data-stu-id="61aac-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="61aac-168">Jeśli typ danych Inicjator nie jest możliwe do przekonwertowania na określony typ danych, występuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="61aac-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="61aac-169">Przykład</span><span class="sxs-lookup"><span data-stu-id="61aac-169">Example</span></span>  
 <span data-ttu-id="61aac-170">W poniższych przykładach pokazano sposób `Option Infer` instrukcji umożliwia wnioskowanie o typie lokalnym.</span><span class="sxs-lookup"><span data-stu-id="61aac-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="61aac-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="61aac-171">Example</span></span>  
 <span data-ttu-id="61aac-172">W poniższym przykładzie pokazano, że typu run-time może się różnić, gdy zmienna zostanie zidentyfikowana jako `Object`.</span><span class="sxs-lookup"><span data-stu-id="61aac-172">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>  
  
 [!code-vb[VbVbalrTypeInference#11](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/option-infer-statement_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="61aac-173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61aac-173">See Also</span></span>  
 [<span data-ttu-id="61aac-174">Dim — instrukcja</span><span class="sxs-lookup"><span data-stu-id="61aac-174">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="61aac-175">Wnioskowanie o typie lokalnym</span><span class="sxs-lookup"><span data-stu-id="61aac-175">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="61aac-176">Option Compare — instrukcja</span><span class="sxs-lookup"><span data-stu-id="61aac-176">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="61aac-177">Option Explicit — instrukcja</span><span class="sxs-lookup"><span data-stu-id="61aac-177">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [<span data-ttu-id="61aac-178">Option Strict — instrukcja</span><span class="sxs-lookup"><span data-stu-id="61aac-178">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="61aac-179">Okno dialogowe Opcje domyślne, projektów, Visual Basic</span><span class="sxs-lookup"><span data-stu-id="61aac-179">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)  
 [<span data-ttu-id="61aac-180">/ optioninfer</span><span class="sxs-lookup"><span data-stu-id="61aac-180">/optioninfer</span></span>](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [<span data-ttu-id="61aac-181">Opakowywanie i rozpakowywanie</span><span class="sxs-lookup"><span data-stu-id="61aac-181">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
