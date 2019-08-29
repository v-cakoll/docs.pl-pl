---
title: Debugowanie drzew wyrażeń w programie Visual StudioC#()
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: 43091d11dfc1fae3e6f047f35b61e992c5aaf50b
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70104904"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Debugowanie drzew wyrażeń w programie Visual StudioC#()
Można analizować strukturę i zawartość drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwości, która reprezentuje drzewa wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md). (Uwaga, `DebugView` która jest dostępna tylko w trybie debugowania).  

![DebugView drzewa wyrażenia w debugerze programu Visual Studio](media/debugging-expression-trees-in-visual-studio/debugview.png)

Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , aby wyświetlić go w wielu wierszach, wybierając **wizualizator tekstu** z ikony lupy obok `DebugView` etykiety.

 ![Wizualizator tekstu zastosowany do wyników elementu "DebugView"](media/debugging-expression-trees-in-visual-studio/string_visualizer.png)

Alternatywnie można zainstalować i używać wizualizatora [niestandardowego](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:

- Możliwe do [odczytu wyrażenia](https://github.com/agileobjects/ReadableExpressions) ([Licencja mit](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderuje drzewo wyrażenia jako C# kod:

  ![Wizualizator wyrażeń do odczytu](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- [Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([Licencja mit](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)), udostępnia widok graficzny drzewa wyrażenia, jego właściwości i powiązane obiekty:

  ![Wizualizator ExpressionToString](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizator dla drzewa wyrażenia  
  
1. Kliknij ikonę lupy, która pojawia się obok drzewa wyrażenia w **etykietkach**danych, oknie czujki, oknie autostarts lub w oknie **zmiennych lokalnych** .  
  
     Zostanie wyświetlona lista dostępnych wizualizatorów.: 

      ![Otwieranie wizualizatorów z programu Visual Studio](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers.png)

2. Kliknij wizualizator, którego chcesz użyć.  
  
## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (C#)](./index.md)
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)
- [Tworzenie niestandardowych wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`obowiązuje](debugview-syntax.md)
