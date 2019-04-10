---
title: Debugowanie drzew w programie Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 95a01a98e771e04afd296428ed56e9518bad9ac2
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59330414"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="72508-102">Debugowanie drzew w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="72508-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="72508-103">Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72508-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="72508-104">Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwość, która jest dostępna tylko w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="72508-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="72508-105">Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="72508-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="72508-106">W celu lepszej reprezentacji treści drzew wyrażeń `DebugView` właściwość używa wizualizatorów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72508-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="72508-107">Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych Wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="72508-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="72508-108">Aby otworzyć wizualizatora drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="72508-108">To open a visualizer for an expression tree</span></span>  
  
1. <span data-ttu-id="72508-109">Kliknij ikonę lupy, która pojawia się obok `DebugView` właściwość drzewo wyrażenia w **DataTips**, **Obejrzyj** oknie **automatyczne** okna, lub **Lokalne** okna.</span><span class="sxs-lookup"><span data-stu-id="72508-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="72508-110">Zostanie wyświetlona lista wizualizatorów.</span><span class="sxs-lookup"><span data-stu-id="72508-110">A list of visualizers is displayed.</span></span>  
  
2. <span data-ttu-id="72508-111">Kliknij pozycję Wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="72508-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="72508-112">Każdy typ wyrażenia jest wyświetlany w wizualizatorze, zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="72508-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="72508-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="72508-113">ParameterExpressions</span></span>  
 <xref:System.Linq.Expressions.ParameterExpression> <span data-ttu-id="72508-114">nazwy zmiennych są wyświetlane z symbolem "$" na początku.</span><span class="sxs-lookup"><span data-stu-id="72508-114">variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="72508-115">Jeśli parametr nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `$var1` lub `$var2`.</span><span class="sxs-lookup"><span data-stu-id="72508-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="72508-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="72508-116">Examples</span></span>  
  
|<span data-ttu-id="72508-117">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="72508-117">Expression</span></span>|`DebugView` <span data-ttu-id="72508-118">property</span><span class="sxs-lookup"><span data-stu-id="72508-118">property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="72508-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="72508-119">ConstantExpressions</span></span>  
 <span data-ttu-id="72508-120">Dla <xref:System.Linq.Expressions.ConstantExpression> obiekty reprezentujące wartości całkowitych, ciągów i `null`, jest wyświetlana wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="72508-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="72508-121">Dla typów numerycznych, które mają standardowa sufiksy jako literały języka C# sufiks jest dodawany do wartości.</span><span class="sxs-lookup"><span data-stu-id="72508-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="72508-122">W poniższej tabeli przedstawiono sufiksy skojarzone z różnych typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="72508-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="72508-123">Typ</span><span class="sxs-lookup"><span data-stu-id="72508-123">Type</span></span>|<span data-ttu-id="72508-124">Suffix</span><span class="sxs-lookup"><span data-stu-id="72508-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="72508-125">U</span><span class="sxs-lookup"><span data-stu-id="72508-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="72508-126">L</span><span class="sxs-lookup"><span data-stu-id="72508-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="72508-127">UL</span><span class="sxs-lookup"><span data-stu-id="72508-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="72508-128">D</span><span class="sxs-lookup"><span data-stu-id="72508-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="72508-129">F</span><span class="sxs-lookup"><span data-stu-id="72508-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="72508-130">M</span><span class="sxs-lookup"><span data-stu-id="72508-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="72508-131">Przykłady</span><span class="sxs-lookup"><span data-stu-id="72508-131">Examples</span></span>  
  
|<span data-ttu-id="72508-132">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="72508-132">Expression</span></span>|`DebugView` <span data-ttu-id="72508-133">property</span><span class="sxs-lookup"><span data-stu-id="72508-133">property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="72508-134">10</span><span class="sxs-lookup"><span data-stu-id="72508-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="72508-135">10D</span><span class="sxs-lookup"><span data-stu-id="72508-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="72508-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="72508-136">BlockExpression</span></span>  
 <span data-ttu-id="72508-137">Jeśli typ <xref:System.Linq.Expressions.BlockExpression> obiekt różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany w `DebugInfo` właściwość w nawiasy ostre (\< i >).</span><span class="sxs-lookup"><span data-stu-id="72508-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="72508-138">W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiektu nie jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="72508-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="72508-139">Przykłady</span><span class="sxs-lookup"><span data-stu-id="72508-139">Examples</span></span>  
  
|<span data-ttu-id="72508-140">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="72508-140">Expression</span></span>|`DebugView` <span data-ttu-id="72508-141">property</span><span class="sxs-lookup"><span data-stu-id="72508-141">property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="72508-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="72508-142">LambdaExpression</span></span>  
 <xref:System.Linq.Expressions.LambdaExpression> <span data-ttu-id="72508-143">obiekty są wyświetlane wraz z ich typy delegowane.</span><span class="sxs-lookup"><span data-stu-id="72508-143">objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="72508-144">Jeśli wyrażenie lambda ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Lambda1` lub `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="72508-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="72508-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="72508-145">Examples</span></span>  
  
|<span data-ttu-id="72508-146">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="72508-146">Expression</span></span>|`DebugView` <span data-ttu-id="72508-147">property</span><span class="sxs-lookup"><span data-stu-id="72508-147">property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="72508-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="72508-148">LabelExpression</span></span>  
 <span data-ttu-id="72508-149">Jeśli określisz wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression> obiektu, ta wartość jest poprzedzana <xref:System.Linq.Expressions.LabelTarget> obiektu.</span><span class="sxs-lookup"><span data-stu-id="72508-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="72508-150">`.Label` Token wskazuje początek etykiety.</span><span class="sxs-lookup"><span data-stu-id="72508-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="72508-151">`.LabelTarget` Token wskazuje docelowy obiektu docelowego, aby przejść do.</span><span class="sxs-lookup"><span data-stu-id="72508-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="72508-152">Jeśli etykieta nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Label1` lub `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="72508-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="72508-153">Przykłady</span><span class="sxs-lookup"><span data-stu-id="72508-153">Examples</span></span>  
  
|<span data-ttu-id="72508-154">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="72508-154">Expression</span></span>|`DebugView` <span data-ttu-id="72508-155">property</span><span class="sxs-lookup"><span data-stu-id="72508-155">property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="72508-156">Operatory zaznaczone</span><span class="sxs-lookup"><span data-stu-id="72508-156">Checked Operators</span></span>  
 <span data-ttu-id="72508-157">Operatory sprawdzane są wyświetlane z symbolu "#" w miejscu dostępnym dla operatora.</span><span class="sxs-lookup"><span data-stu-id="72508-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="72508-158">Na przykład operator dodawania zaznaczone jest wyświetlany jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="72508-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="72508-159">Przykłady</span><span class="sxs-lookup"><span data-stu-id="72508-159">Examples</span></span>  
  
|<span data-ttu-id="72508-160">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="72508-160">Expression</span></span>|`DebugView` <span data-ttu-id="72508-161">property</span><span class="sxs-lookup"><span data-stu-id="72508-161">property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="72508-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72508-162">See also</span></span>

- [<span data-ttu-id="72508-163">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="72508-163">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="72508-164">Debugowanie w Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72508-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)
- [<span data-ttu-id="72508-165">Tworzenie niestandardowych Wizualizatorów</span><span class="sxs-lookup"><span data-stu-id="72508-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
