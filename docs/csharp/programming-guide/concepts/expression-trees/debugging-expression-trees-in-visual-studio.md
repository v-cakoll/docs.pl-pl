---
title: Debugowanie drzew wyrażeń w programie Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 0b3017f2800a2eb7332028b9cfe6ed9877222087
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Debugowanie drzew wyrażeń w programie Visual Studio (C#)
Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażenia, można użyć `DebugView` właściwość, która jest dostępna tylko w trybie debugowania. Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
 Aby lepiej reprezentuje zawartość drzewa wyrażeń `DebugView` właściwość używa wizualizatorów programu Visual Studio. Aby uzyskać więcej informacji, zobacz [utworzyć niestandardowe Wizualizatory](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizatora drzewa wyrażeń  
  
1.  Kliknij ikonę lupy, który jest wyświetlany obok pozycji `DebugView` właściwości drzewo wyrażeń w **etykietek danych**, **czujki** okna, **automatycznych** okna, lub **Zmiennych lokalnych** okna.  
  
     Zostanie wyświetlona lista wizualizatorów.  
  
2.  Kliknij pozycję Wizualizator, którego chcesz użyć.  
  
 Każdy typ wyrażenia jest wyświetlany w wizualizatora, zgodnie z opisem w poniższych sekcjach.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression> nazwy zmiennych są wyświetlane przy użyciu symbolu "$" na początku.  
  
 Jeśli parametr nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `$var1` lub `$var2`.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int), "num");`|`$num`|  
|`ParameterExpression numParam =  Expression.Parameter(typeof(int));`|`$var1`|  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Dla <xref:System.Linq.Expressions.ConstantExpression> obiektów, które reprezentują wartości całkowite, ciągi, i `null`, jest wyświetlana wartość stałą.  
  
 Dla typów numerycznych, które mają standardowe sufiksy jako literały C# sufiks zostanie dodany do wartości. W poniższej tabeli przedstawiono sufiksy skojarzone z różnymi typami liczbowych.  
  
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
 Jeśli typ <xref:System.Linq.Expressions.BlockExpression> obiektu różni się od typu ostatniego wyrażenia w bloku, jest wyświetlany w `DebugInfo` właściwości w nawiasy (\< i >). W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiekt nie jest wyświetlany.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`BlockExpression block = Expression.Block(Expression.Constant("test"));`|`.Block() {`<br /><br /> `"test"`<br /><br /> `}`|  
|`BlockExpression block =  Expression.Block(typeof(Object), Expression.Constant("test"));`|`.Block<System.Object>() {`<br /><br /> `"test"`<br /><br /> `}`|  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression> obiekty są wyświetlane wraz z ich typy delegowane.  
  
 Jeśli wyrażenie lambda nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `#Lambda1` lub `#Lambda2`.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1));`|`.Lambda #Lambda1<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
|`LambdaExpression lambda =  Expression.Lambda<Func<int>>(Expression.Constant(1), "SampleLambda", null);`|`.Lambda SampleLambda<System.Func'1[System.Int32]>() {`<br /><br /> `1`<br /><br /> `}`|  
  
## <a name="labelexpression"></a>LabelExpression  
 Jeśli określono wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression> obiektu, ta wartość jest wyświetlana przed <xref:System.Linq.Expressions.LabelTarget> obiektu.  
  
 `.Label` Token wskazuje początek etykiety. `.LabelTarget` Docelowego obiektu docelowego, aby przejść do wskazuje token.  
  
 Jeśli etykieta nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `#Label1` lub `#Label2`.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`LabelTarget target = Expression.Label(typeof(int), "SampleLabel"); BlockExpression block = Expression.Block( Expression.Goto(target, Expression.Constant(0)), Expression.Label(target, Expression.Constant(-1)));`|`.Block() {`<br /><br /> `.Goto SampleLabel { 0 };`<br /><br /> `.Label`<br /><br /> `-1`<br /><br /> `.LabelTarget SampleLabel:`<br /><br /> `}`|  
|`LabelTarget target = Expression.Label(); BlockExpression block = Expression.Block( Expression.Goto(target5), Expression.Label(target5));`|`.Block() {`<br /><br /> `.Goto #Label1 { };`<br /><br /> `.Label`<br /><br /> `.LabelTarget #Label1:`<br /><br /> `}`|  
  
## <a name="checked-operators"></a>Operatory zaznaczenia  
 Operatory zaznaczone są wyświetlane ze znakiem "#" przed operatora. Na przykład operator dodawania zaznaczenia jest wyświetlany jako `#+`.  
  
### <a name="examples"></a>Przykłady  
  
|Wyrażenie|`DebugView` Właściwość|  
|----------------|--------------------------|  
|`Expression expr = Expression.AddChecked( Expression.Constant(1), Expression.Constant(2));`|`1 #+ 2`|  
|`Expression expr = Expression.ConvertChecked( Expression.Constant(10.0), typeof(int));`|`#(System.Int32)10D`|  
  
## <a name="see-also"></a>Zobacz też  
 [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
 [Utwórz niestandardowe Wizualizatory](/visualstudio/debugger/create-custom-visualizers-of-data)
