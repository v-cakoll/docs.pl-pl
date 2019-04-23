---
title: Debugowanie drzew w programie Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 95a01a98e771e04afd296428ed56e9518bad9ac2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330414"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Debugowanie drzew w programie Visual Studio (C#)
Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwość, która jest dostępna tylko w trybie debugowania. Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
 W celu lepszej reprezentacji treści drzew wyrażeń `DebugView` właściwość używa wizualizatorów programu Visual Studio. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych Wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizatora drzewa wyrażeń  
  
1. Kliknij ikonę lupy, która pojawia się obok `DebugView` właściwość drzewo wyrażenia w **DataTips**, **Obejrzyj** oknie **automatyczne** okna, lub **Lokalne** okna.  
  
     Zostanie wyświetlona lista wizualizatorów.  
  
2. Kliknij pozycję Wizualizator, którego chcesz użyć.  
  
 Każdy typ wyrażenia jest wyświetlany w wizualizatorze, zgodnie z opisem w poniższych sekcjach.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression> nazwy zmiennych są wyświetlane z symbolem "$" na początku.  
  
 Jeśli parametr nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `$var1` lub `$var2`.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Dla <xref:System.Linq.Expressions.ConstantExpression> obiekty reprezentujące wartości całkowitych, ciągów i `null`, jest wyświetlana wartość stałą.  
  
 Dla typów numerycznych, które mają standardowa sufiksy jako literały języka C# sufiks jest dodawany do wartości. W poniższej tabeli przedstawiono sufiksy skojarzone z różnych typów liczbowych.  
  
|Typ|Suffix|  
|----------|------------|  
|<xref:System.UInt32>|U|  
|<xref:System.Int64>|L|  
|<xref:System.UInt64>|UL|  
|<xref:System.Double>|D|  
|<xref:System.Single>|F|  
|<xref:System.Decimal>|M|  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`int num = 10; ConstantExpression expr = Expression.Constant(num);`|10|  
|`double num = 10; ConstantExpression expr = Expression.Constant(num);`|10D|  
  
## <a name="blockexpression"></a>BlockExpression  
 Jeśli typ <xref:System.Linq.Expressions.BlockExpression> obiekt różni się od typu ostatniego wyrażenia w bloku, typ jest wyświetlany w `DebugInfo` właściwość w nawiasy ostre (\< i >). W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiektu nie jest wyświetlana.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> obiekty są wyświetlane wraz z ich typy delegowane.  
  
 Jeśli wyrażenie lambda ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Lambda1` lub `#Lambda2`.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 Jeśli określisz wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression> obiektu, ta wartość jest poprzedzana <xref:System.Linq.Expressions.LabelTarget> obiektu.  
  
 `.Label` Token wskazuje początek etykiety. `.LabelTarget` Token wskazuje docelowy obiektu docelowego, aby przejść do.  
  
 Jeśli etykieta nie ma nazwę, przypisano automatycznie wygenerowaną nazwę, taką jak `#Label1` lub `#Label2`.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>Operatory zaznaczone  
 Operatory sprawdzane są wyświetlane z symbolu "#" w miejscu dostępnym dla operatora. Na przykład operator dodawania zaznaczone jest wyświetlany jako `#+`.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Tworzenie niestandardowych wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data)
