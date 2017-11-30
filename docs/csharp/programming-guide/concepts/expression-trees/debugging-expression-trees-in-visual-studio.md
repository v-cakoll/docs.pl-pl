---
title: "Debugowanie drzew wyrażeń w programie Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
caps.latest.revision: "4"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74df8ba339526e20850cd8b8f1a4b37c20e22ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a><span data-ttu-id="12efb-102">Debugowanie drzew wyrażeń w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="12efb-102">Debugging Expression Trees in Visual Studio (C#)</span></span>
<span data-ttu-id="12efb-103">Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="12efb-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="12efb-104">Aby uzyskać szybki przegląd struktury drzewa wyrażenia, można użyć `DebugView` właściwość, która jest dostępna tylko w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="12efb-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="12efb-105">Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="12efb-105">For more information about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="12efb-106">Aby lepiej reprezentuje zawartość drzewa wyrażeń `DebugView` właściwość używa wizualizatorów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="12efb-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="12efb-107">Aby uzyskać więcej informacji, zobacz [utworzyć niestandardowe Wizualizatory](/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="12efb-107">For more information, see [Create Custom Visualizers](/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="12efb-108">Aby otworzyć wizualizatora drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="12efb-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="12efb-109">Kliknij ikonę lupy, który jest wyświetlany obok pozycji `DebugView` właściwości drzewo wyrażeń w **etykietek danych**, **czujki** okna, **automatycznych** okna, lub **Zmiennych lokalnych** okna.</span><span class="sxs-lookup"><span data-stu-id="12efb-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="12efb-110">Zostanie wyświetlona lista wizualizatorów.</span><span class="sxs-lookup"><span data-stu-id="12efb-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="12efb-111">Kliknij pozycję Wizualizator, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="12efb-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="12efb-112">Każdy typ wyrażenia jest wyświetlany w wizualizatora, zgodnie z opisem w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="12efb-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="12efb-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="12efb-113">ParameterExpressions</span></span>  
 <span data-ttu-id="12efb-114"><xref:System.Linq.Expressions.ParameterExpression>nazwy zmiennych są wyświetlane przy użyciu symbolu "$" na początku.</span><span class="sxs-lookup"><span data-stu-id="12efb-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="12efb-115">Jeśli parametr nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `$var1` lub `$var2`.</span><span class="sxs-lookup"><span data-stu-id="12efb-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="12efb-116">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12efb-116">Examples</span></span>  
  
|<span data-ttu-id="12efb-117">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="12efb-117">Expression</span></span>|<span data-ttu-id="12efb-118">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="12efb-118">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a><span data-ttu-id="12efb-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="12efb-119">ConstantExpressions</span></span>  
 <span data-ttu-id="12efb-120">Dla <xref:System.Linq.Expressions.ConstantExpression> obiektów, które reprezentują wartości całkowite, ciągi, i `null`, jest wyświetlana wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="12efb-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
 <span data-ttu-id="12efb-121">Dla typów numerycznych, które mają standardowe sufiksy jako literały C# sufiks zostanie dodany do wartości.</span><span class="sxs-lookup"><span data-stu-id="12efb-121">For numeric types that have standard suffixes as C# literals, the suffix is added to the value.</span></span> <span data-ttu-id="12efb-122">W poniższej tabeli przedstawiono sufiksy skojarzone z różnymi typami liczbowych.</span><span class="sxs-lookup"><span data-stu-id="12efb-122">The following table shows the suffixes associated with various numeric types.</span></span>  
  
|<span data-ttu-id="12efb-123">Typ</span><span class="sxs-lookup"><span data-stu-id="12efb-123">Type</span></span>|<span data-ttu-id="12efb-124">Sufiks</span><span class="sxs-lookup"><span data-stu-id="12efb-124">Suffix</span></span>|  
|----------|------------|  
|<xref:System.UInt32>|<span data-ttu-id="12efb-125">U</span><span class="sxs-lookup"><span data-stu-id="12efb-125">U</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="12efb-126">L</span><span class="sxs-lookup"><span data-stu-id="12efb-126">L</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="12efb-127">UL</span><span class="sxs-lookup"><span data-stu-id="12efb-127">UL</span></span>|  
|<xref:System.Double>|<span data-ttu-id="12efb-128">D</span><span class="sxs-lookup"><span data-stu-id="12efb-128">D</span></span>|  
|<xref:System.Single>|<span data-ttu-id="12efb-129">F</span><span class="sxs-lookup"><span data-stu-id="12efb-129">F</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="12efb-130">M</span><span class="sxs-lookup"><span data-stu-id="12efb-130">M</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="12efb-131">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12efb-131">Examples</span></span>  
  
|<span data-ttu-id="12efb-132">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="12efb-132">Expression</span></span>|<span data-ttu-id="12efb-133">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="12efb-133">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="12efb-134">10</span><span class="sxs-lookup"><span data-stu-id="12efb-134">10</span></span>|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|<span data-ttu-id="12efb-135">10D</span><span class="sxs-lookup"><span data-stu-id="12efb-135">10D</span></span>|  
  
## <a name="blockexpression"></a><span data-ttu-id="12efb-136">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="12efb-136">BlockExpression</span></span>  
 <span data-ttu-id="12efb-137">Jeśli typ <xref:System.Linq.Expressions.BlockExpression> obiektu różni się od typu ostatniego wyrażenia w bloku, jest wyświetlany w `DebugInfo` właściwości w nawiasy (\< i >).</span><span class="sxs-lookup"><span data-stu-id="12efb-137">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="12efb-138">W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiekt nie jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="12efb-138">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="12efb-139">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12efb-139">Examples</span></span>  
  
|<span data-ttu-id="12efb-140">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="12efb-140">Expression</span></span>|<span data-ttu-id="12efb-141">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="12efb-141">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a><span data-ttu-id="12efb-142">LambdaExpression</span><span class="sxs-lookup"><span data-stu-id="12efb-142">LambdaExpression</span></span>  
 <span data-ttu-id="12efb-143"><xref:System.Linq.Expressions.LambdaExpression>obiekty są wyświetlane wraz z ich typy delegowane.</span><span class="sxs-lookup"><span data-stu-id="12efb-143"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="12efb-144">Jeśli wyrażenie lambda nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `#Lambda1` lub `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="12efb-144">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="12efb-145">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12efb-145">Examples</span></span>  
  
|<span data-ttu-id="12efb-146">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="12efb-146">Expression</span></span>|<span data-ttu-id="12efb-147">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="12efb-147">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a><span data-ttu-id="12efb-148">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="12efb-148">LabelExpression</span></span>  
 <span data-ttu-id="12efb-149">Jeśli określono wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression> obiektu, ta wartość jest wyświetlana przed <xref:System.Linq.Expressions.LabelTarget> obiektu.</span><span class="sxs-lookup"><span data-stu-id="12efb-149">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="12efb-150">`.Label` Token wskazuje początek etykiety.</span><span class="sxs-lookup"><span data-stu-id="12efb-150">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="12efb-151">`.LabelTarget` Docelowego obiektu docelowego, aby przejść do wskazuje token.</span><span class="sxs-lookup"><span data-stu-id="12efb-151">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="12efb-152">Jeśli etykieta nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `#Label1` lub `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="12efb-152">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="12efb-153">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12efb-153">Examples</span></span>  
  
|<span data-ttu-id="12efb-154">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="12efb-154">Expression</span></span>|<span data-ttu-id="12efb-155">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="12efb-155">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a><span data-ttu-id="12efb-156">Operatory zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="12efb-156">Checked Operators</span></span>  
 <span data-ttu-id="12efb-157">Operatory zaznaczone są wyświetlane ze znakiem "#" przed operatora.</span><span class="sxs-lookup"><span data-stu-id="12efb-157">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="12efb-158">Na przykład operator dodawania zaznaczenia jest wyświetlany jako `#+`.</span><span class="sxs-lookup"><span data-stu-id="12efb-158">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="12efb-159">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12efb-159">Examples</span></span>  
  
|<span data-ttu-id="12efb-160">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="12efb-160">Expression</span></span>|<span data-ttu-id="12efb-161">`DebugView`Właściwość</span><span class="sxs-lookup"><span data-stu-id="12efb-161">`DebugView` property</span></span>|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a><span data-ttu-id="12efb-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12efb-162">See Also</span></span>  
 [<span data-ttu-id="12efb-163">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="12efb-163">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="12efb-164">Debugowanie w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="12efb-164">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="12efb-165">Utwórz niestandardowe Wizualizatory</span><span class="sxs-lookup"><span data-stu-id="12efb-165">Create Custom Visualizers</span></span>](/visualstudio/debugger/create-custom-visualizers-of-data)
