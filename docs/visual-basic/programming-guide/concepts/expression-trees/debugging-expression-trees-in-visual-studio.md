---
title: "Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ff1bee9c3c3fdeafab24368d2c7e8376d4ff7b97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)
Można analizować struktury i zawartości drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażenia, można użyć `DebugView` właściwość, która jest dostępna tylko w trybie debugowania. Aby uzyskać więcej informacji na temat debugowania, zobacz [debugowania w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
 Aby lepiej reprezentuje zawartość drzewa wyrażeń `DebugView` właściwość używa wizualizatorów programu Visual Studio. Aby uzyskać więcej informacji, zobacz [utworzyć niestandardowe Wizualizatory](/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizatora drzewa wyrażeń  
  
1.  Kliknij ikonę lupy, który jest wyświetlany obok pozycji `DebugView` właściwości drzewo wyrażeń w **etykietek danych**, **czujki** okna, **automatycznych** okna, lub **Zmiennych lokalnych** okna.  
  
     Zostanie wyświetlona lista wizualizatorów.  
  
2.  Kliknij pozycję Wizualizator, którego chcesz użyć.  
  
 Każdy typ wyrażenia jest wyświetlany w wizualizatora, zgodnie z opisem w poniższych sekcjach.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression>nazwy zmiennych są wyświetlane przy użyciu symbolu "$" na początku.  
  
 Jeśli parametr nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `$var1` lub `$var2`.  
  
### <a name="examples"></a>Przykłady  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     `DebugView`Właściwość  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     `DebugView`Właściwość  
  
     `$var1`  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Dla <xref:System.Linq.Expressions.ConstantExpression> obiektów, które reprezentują wartości całkowite, ciągi, i `null`, jest wyświetlana wartość stałą.  
  
### <a name="examples"></a>Przykłady  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView`Właściwość  
  
     10  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     `DebugView`Właściwość  
  
     10D  
  
## <a name="blockexpression"></a>BlockExpression  
 Jeśli typ <xref:System.Linq.Expressions.BlockExpression> obiektu różni się od typu ostatniego wyrażenia w bloku, jest wyświetlany w `DebugInfo` właściwości w nawiasy (\< i >). W przeciwnym razie typ <xref:System.Linq.Expressions.BlockExpression> obiekt nie jest wyświetlany.  
  
### <a name="examples"></a>Przykłady  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     `DebugView`Właściwość  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     `DebugView`Właściwość  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a>LambdaExpression  
 <xref:System.Linq.Expressions.LambdaExpression>obiekty są wyświetlane wraz z ich typy delegowane.  
  
 Jeśli wyrażenie lambda nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `#Lambda1` lub `#Lambda2`.  
  
### <a name="examples"></a>Przykłady  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     `DebugView`Właściwość  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     `DebugView`Właściwość  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a>LabelExpression  
 Jeśli określono wartość domyślną dla <xref:System.Linq.Expressions.LabelExpression> obiektu, ta wartość jest wyświetlana przed <xref:System.Linq.Expressions.LabelTarget> obiektu.  
  
 `.Label` Token wskazuje początek etykiety. `.LabelTarget` Docelowego obiektu docelowego, aby przejść do wskazuje token.  
  
 Jeśli etykieta nie ma nazwy, przypisano użyciem nazwy wygenerowanej automatycznie, takich jak `#Label1` lub `#Label2`.  
  
### <a name="examples"></a>Przykłady  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     `DebugView`Właściwość  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     `DebugView`Właściwość  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a>Operatory zaznaczenia  
 Operatory zaznaczone są wyświetlane ze znakiem "#" przed operatora. Na przykład operator dodawania zaznaczenia jest wyświetlany jako `#+`.  
  
### <a name="examples"></a>Przykłady  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     `DebugView`Właściwość  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     `DebugView`Właściwość  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a>Zobacz też  
 [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
 [Utwórz niestandardowe Wizualizatory](/visualstudio/debugger/create-custom-visualizers-of-data)
