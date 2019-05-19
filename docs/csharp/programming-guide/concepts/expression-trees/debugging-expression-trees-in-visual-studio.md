---
title: Debugowanie drzew w programie Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 4017e2c2592dc1d6067b428fc1d47f37775abf85
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877153"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="eb5ae-102">Debugowanie drzew w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="eb5ae-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="eb5ae-103">Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="eb5ae-104">Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwość, która reprezentuje drzew wyrażeń, przy użyciu specjalnej składni opisane [poniżej](#debugview-syntax).</span><span class="sxs-lookup"><span data-stu-id="eb5ae-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which represents expression trees using a special syntax described [below](#debugview-syntax).</span></span> <span data-ttu-id="eb5ae-105">(Należy pamiętać, że `DebugView` jest dostępna tylko w trybie debugowania.)</span><span class="sxs-lookup"><span data-stu-id="eb5ae-105">(Note that `DebugView` is available only in debug mode.)</span></span>  

![DebugView drzewa wyrażeń w debugerze programu Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

<span data-ttu-id="eb5ae-107">Ponieważ `DebugView` jest ciągiem, możesz użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) do wyświetlenia w wielu wierszach, wybierając **Wizualizator tekstu** z na ikonę szkła powiększającego obok `DebugView` Etykieta.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-107">Since `DebugView` is a string, you can use the [built-in Text Visualizer](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) to view it across multiple lines, by selecting **Text Visualizer** from the magnifying glass icon next to the `DebugView` label.</span></span>

 ![Wizualizator tekstu zastosowane do wyników "DebugView"](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

<span data-ttu-id="eb5ae-109">Alternatywnie, można zainstalować i używać [niestandardowego wizualizatora](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="eb5ae-109">Alternatively, you can install and use [a custom visualizer](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) for expression trees:</span></span>

* <span data-ttu-id="eb5ae-110">[Wyrażenia można odczytać](https://github.com/agileobjects/ReadableExpressions) ([licencją MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), która jest dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), powoduje wyświetlenie drzewa wyrażeń jako C# kodu:</span><span class="sxs-lookup"><span data-stu-id="eb5ae-110">[Readable Expressions](https://github.com/agileobjects/ReadableExpressions) ([MIT license](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), available at the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renders the expression tree as C# code:</span></span>

  ![Czytelny Wizualizator wyrażeń](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* <span data-ttu-id="eb5ae-112">[Wizualizatora drzewa wyrażenie](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencją MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), zawiera graficzne przedstawienie drzewa wyrażeń, a jej właściwości i obiektów związanych z:</span><span class="sxs-lookup"><span data-stu-id="eb5ae-112">[Expression Tree Visualizer](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT license](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), provides a graphical view of the expression tree, its properties, and related objects:</span></span>

  ![Wizualizator ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="eb5ae-114">Aby otworzyć wizualizatora drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="eb5ae-114">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="eb5ae-115">Kliknij ikonę lupy, która pojawia się obok drzewa wyrażeń w **DataTips**, **Obejrzyj** oknie **automatyczne** oknie lub **zmiennychlokalnych** okna.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-115">Click the magnifying glass icon that appears next to the expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="eb5ae-116">Zostanie wyświetlona lista dostępnych wizualizatorów.:</span><span class="sxs-lookup"><span data-stu-id="eb5ae-116">A list of available visualizers is displayed.:</span></span> 

      ![Wizualizatory otwierania w programie Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. <span data-ttu-id="eb5ae-118">Kliknij pozycję Wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-118">Click the visualizer you want to use.</span></span>  

## <a name="debugview-syntax"></a><span data-ttu-id="eb5ae-119">`DebugView` Składnia</span><span class="sxs-lookup"><span data-stu-id="eb5ae-119">`DebugView` syntax</span></span> 

<span data-ttu-id="eb5ae-120">Każdy typ wyrażenia są wyświetlane według `DebugView` właściwości zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-120">Each expression type is displayed by the `DebugView` property as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="eb5ae-121">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="eb5ae-121">ParameterExpressions</span></span>  
 <span data-ttu-id="eb5ae-122"><xref:System.Linq.Expressions.ParameterExpression> nazwy zmiennych są wyświetlane z symbolem "$" na początku.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-122"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="eb5ae-123">Jeśli parametr nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `$var1` lub `$var2`.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-123">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="eb5ae-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="eb5ae-124">Examples</span></span>  
  
|<span data-ttu-id="eb5ae-125">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="eb5ae-125">Expression</span></span>|<span data-ttu-id="eb5ae-126">`DebugView` Właściwość</span><span class="sxs-lookup"><span data-stu-id="eb5ae-126">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="eb5ae-127">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="eb5ae-127">ConstantExpressions</span></span>  
 <span data-ttu-id="eb5ae-128">Dla <xref:System.Linq.Expressions.ConstantExpression> obiekty reprezentujące wartości całkowitych, ciągów i `null`, jest wyświetlana wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-128">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="eb5ae-129">Dla typów numerycznych, które mają standardowa sufiksy jako literały języka C# sufiks jest dodawany do wartości.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-129">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="eb5ae-130">W poniższej tabeli przedstawiono sufiksy skojarzone z różnych typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-130">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="eb5ae-131">Typ</span><span class="sxs-lookup"><span data-stu-id="eb5ae-131">Type</span></span>|<span data-ttu-id="eb5ae-132">Suffix</span><span class="sxs-lookup"><span data-stu-id="eb5ae-132">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="eb5ae-133">U</span><span class="sxs-lookup"><span data-stu-id="eb5ae-133">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="eb5ae-134">L</span><span class="sxs-lookup"><span data-stu-id="eb5ae-134">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="eb5ae-135">UL</span><span class="sxs-lookup"><span data-stu-id="eb5ae-135">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="eb5ae-136">D</span><span class="sxs-lookup"><span data-stu-id="eb5ae-136">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="eb5ae-137">F</span><span class="sxs-lookup"><span data-stu-id="eb5ae-137">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="eb5ae-138">M</span><span class="sxs-lookup"><span data-stu-id="eb5ae-138">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="eb5ae-139">Przykłady</span><span class="sxs-lookup"><span data-stu-id="eb5ae-139">Examples</span></span>  
  
|<span data-ttu-id="eb5ae-140">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="eb5ae-140">Expression</span></span>|<span data-ttu-id="eb5ae-141">`DebugView` Właściwość</span><span class="sxs-lookup"><span data-stu-id="eb5ae-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="eb5ae-142">10</span><span class="sxs-lookup"><span data-stu-id="eb5ae-142">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="eb5ae-143">10D</span><span class="sxs-lookup"><span data-stu-id="eb5ae-143">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="eb5ae-144">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="eb5ae-144">BlockExpression</span></span>  
 <span data-ttu-id="eb5ae-145">Jeśli typ <xref:System.Linq.Expressions.BlockExpression> obiekt różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany w `DebugInfo` właściwość w nawiasy ostre (\< i >).</span><span class="sxs-lookup"><span data-stu-id="eb5ae-145">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="eb5ae-146">W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiektu nie jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-146">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="eb5ae-147">Przykłady</span><span class="sxs-lookup"><span data-stu-id="eb5ae-147">Examples</span></span>  
  
|<span data-ttu-id="eb5ae-148">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="eb5ae-148">Expression</span></span>|<span data-ttu-id="eb5ae-149">`DebugView` Właściwość</span><span class="sxs-lookup"><span data-stu-id="eb5ae-149">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="eb5ae-150">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="eb5ae-150">LambdaExpression</span></span>  
 <span data-ttu-id="eb5ae-151"><xref:System.Linq.Expressions.LambdaExpression> obiekty są wyświetlane wraz z ich typy delegowane.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-151"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="eb5ae-152">Jeśli wyrażenie lambda ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Lambda1` lub `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-152">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="eb5ae-153">Przykłady</span><span class="sxs-lookup"><span data-stu-id="eb5ae-153">Examples</span></span>  
  
|<span data-ttu-id="eb5ae-154">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="eb5ae-154">Expression</span></span>|<span data-ttu-id="eb5ae-155">`DebugView` Właściwość</span><span class="sxs-lookup"><span data-stu-id="eb5ae-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="eb5ae-156">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="eb5ae-156">LabelExpression</span></span>  
 <span data-ttu-id="eb5ae-157">Jeśli określisz wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression> obiektu, ta wartość jest poprzedzana <xref:System.Linq.Expressions.LabelTarget> obiektu.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-157">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="eb5ae-158">`.Label` Token wskazuje początek etykiety.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-158">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="eb5ae-159">`.LabelTarget` Token wskazuje docelowy obiektu docelowego, aby przejść do.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-159">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="eb5ae-160">Jeśli etykieta nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Label1` lub `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-160">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="eb5ae-161">Przykłady</span><span class="sxs-lookup"><span data-stu-id="eb5ae-161">Examples</span></span>  
  
|<span data-ttu-id="eb5ae-162">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="eb5ae-162">Expression</span></span>|<span data-ttu-id="eb5ae-163">`DebugView` Właściwość</span><span class="sxs-lookup"><span data-stu-id="eb5ae-163">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="eb5ae-164">Operatory zaznaczone</span><span class="sxs-lookup"><span data-stu-id="eb5ae-164">Checked Operators</span></span>  
 <span data-ttu-id="eb5ae-165">Operatory sprawdzane są wyświetlane z symbolu "#" w miejscu dostępnym dla operatora.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-165">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="eb5ae-166">Na przykład operator dodawania zaznaczone jest wyświetlany jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="eb5ae-166">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="eb5ae-167">Przykłady</span><span class="sxs-lookup"><span data-stu-id="eb5ae-167">Examples</span></span>  
  
|<span data-ttu-id="eb5ae-168">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="eb5ae-168">Expression</span></span>|<span data-ttu-id="eb5ae-169">`DebugView` Właściwość</span><span class="sxs-lookup"><span data-stu-id="eb5ae-169">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="eb5ae-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb5ae-170">See also</span></span>

- [<span data-ttu-id="eb5ae-171">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="eb5ae-171">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="eb5ae-172">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eb5ae-172">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="eb5ae-173">Tworzenie niestandardowych wizualizatorów</span><span class="sxs-lookup"><span data-stu-id="eb5ae-173">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
