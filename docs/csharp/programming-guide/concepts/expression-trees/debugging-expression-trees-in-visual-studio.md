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
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Debugowanie drzew w programie Visual Studio (C#)
Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwość, która reprezentuje drzew wyrażeń, przy użyciu specjalnej składni opisane [poniżej](#debugview-syntax). (Należy pamiętać, że `DebugView` jest dostępna tylko w trybie debugowania.)  

![DebugView drzewa wyrażeń w debugerze programu Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

Ponieważ `DebugView` jest ciągiem, możesz użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) do wyświetlenia w wielu wierszach, wybierając **Wizualizator tekstu** z na ikonę szkła powiększającego obok `DebugView` Etykieta.

 ![Wizualizator tekstu zastosowane do wyników "DebugView"](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Alternatywnie, można zainstalować i używać [niestandardowego wizualizatora](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń:

* [Wyrażenia można odczytać](https://github.com/agileobjects/ReadableExpressions) ([licencją MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), która jest dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), powoduje wyświetlenie drzewa wyrażeń jako C# kodu:

  ![Czytelny Wizualizator wyrażeń](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [Wizualizatora drzewa wyrażenie](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencją MIT](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), zawiera graficzne przedstawienie drzewa wyrażeń, a jej właściwości i obiektów związanych z:

  ![Wizualizator ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizatora drzewa wyrażeń  
  
1. Kliknij ikonę lupy, która pojawia się obok drzewa wyrażeń w **DataTips**, **Obejrzyj** oknie **automatyczne** oknie lub **zmiennychlokalnych** okna.  
  
     Zostanie wyświetlona lista dostępnych wizualizatorów.: 

      ![Wizualizatory otwierania w programie Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Kliknij pozycję Wizualizator, którego chcesz użyć.  

## <a name="debugview-syntax"></a>`DebugView` Składnia 

Każdy typ wyrażenia są wyświetlane według `DebugView` właściwości zgodnie z opisem w poniższych sekcjach.  
  
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
