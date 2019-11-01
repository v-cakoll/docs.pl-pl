---
title: Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: b27ab41f3c3d9bd488fd0f7aaa5010f2997946de
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198274"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Debugowanie drzew wyrażeń w programie Visual Studio (Visual Basic)
Można analizować strukturę i zawartość drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć właściwości `DebugView`, która reprezentuje drzewa wyrażeń [przy użyciu specjalnej składni](debugview-syntax.md). (Należy zauważyć, że `DebugView` jest dostępny tylko w trybie debugowania).  

![Zrzut ekranu przedstawiający DebugView drzewa wyrażenia.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) , aby wyświetlić go w wielu wierszach, wybierając **wizualizator tekstu** z ikony lupy, obok etykiety `DebugView`.

 ![Zrzut ekranu wizualizatora tekstu stosowany do wyników DebugView.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Alternatywnie można zainstalować i używać [wizualizatora niestandardowego](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:

- [Wyrażenia](https://github.com/agileobjects/ReadableExpressions) możliwe do odczytu ([licencja mit](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderowanie drzewa wyrażenia C# jako kodu:

  ![Zrzut ekranu przedstawiający wizualizator wyrażeń możliwych do odczytu.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([licencja mit](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) zawiera graficzny widok drzewa wyrażenia, jego właściwości i powiązane obiekty; i można renderować drzewo wyrażeń przy użyciu kodu Visual Basic:

  ![Zrzut ekranu przedstawiający wizualizator ExpressionToString.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizator dla drzewa wyrażenia  
  
1. Kliknij ikonę lupy, która pojawia się obok drzewa wyrażenia w **etykietkach**danych, oknie **czujki** , oknie **autostarts** lub w oknie **zmiennych lokalnych** .  
  
    Zostanie wyświetlona lista dostępnych wizualizatorów.: 

    ![Zrzut ekranu przedstawiający Wizualizatory otwierające użytkownika z programu Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Kliknij wizualizator, którego chcesz użyć.  

## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Tworzenie niestandardowych wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data)
- [Składnia `DebugView`](debugview-syntax.md)
