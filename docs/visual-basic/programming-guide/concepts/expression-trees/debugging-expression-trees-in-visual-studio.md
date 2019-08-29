---
title: Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 3334828475ef5d933ea660ea33ae264d4ccce172
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106869"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)
Można analizować strukturę i zawartość drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwości, która reprezentuje drzewa wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md). (Uwaga, `DebugView` która jest dostępna tylko w trybie debugowania).  

![DebugView drzewa wyrażenia w debugerze programu Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , aby wyświetlić go w wielu wierszach, wybierając **wizualizator tekstu** z ikony lupy obok `DebugView` etykiety.

 ![Wizualizator tekstu zastosowany do wyników elementu "DebugView"](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

Alternatywnie można zainstalować i używać wizualizatora [niestandardowego](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:

- Możliwe do [odczytu wyrażenia](https://github.com/agileobjects/ReadableExpressions) ([Licencja mit](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderuje drzewo wyrażenia jako C# kod:

  ![Wizualizator wyrażeń do odczytu](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- [Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([Licencja mit](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), zapewnia widok graficzny drzewa wyrażenia, jego właściwości i powiązane obiekty; i można renderować drzewo wyrażeń przy użyciu kodu Visual Basic:

  ![Wizualizator ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizator dla drzewa wyrażenia  
  
1. Kliknij ikonę lupy, która pojawia się obok drzewa wyrażenia w **etykietkach**danych, oknie czujki, oknie autostarts lub w oknie **zmiennych lokalnych** .  
  
     Zostanie wyświetlona lista dostępnych wizualizatorów.: 

      ![Otwieranie wizualizatorów z programu Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. Kliknij wizualizator, którego chcesz użyć.  

## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Tworzenie niestandardowych wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`obowiązuje](debugview-syntax.md)
