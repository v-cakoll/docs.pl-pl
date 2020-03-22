---
title: Debugowanie drzew w programie Visual Studio
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: c6c44d079ab0854b2325b82d3569280752da32fb
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266836"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Drzewa wyrażeń debugowania w programie Visual Studio (Visual Basic)
Podczas debugowania aplikacji można analizować strukturę i zawartość drzew wyrażeń. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwości, która reprezentuje drzewa wyrażeń przy użyciu [specjalnej składni](debugview-syntax.md). (Należy `DebugView` zauważyć, że jest dostępny tylko w trybie debugowania.)  

![Zrzut ekranu przedstawiający debugview drzewa wyrażeń.](media/debugging-expression-trees-in-visual-studio/debugview-visual-basic.png)

Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu,](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) aby wyświetlić go w wielu wierszach, `DebugView` wybierając **wizualizator tekstu** z ikony lupy obok etykiety.

 ![Zrzut ekranu przedstawiający wizualizator tekstu zastosowany do wyników debugview.](media/debugging-expression-trees-in-visual-studio/string-visualizer-vb.png)

Alternatywnie można zainstalować i używać [niestandardowego wizualizatora](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:

- [Czytelne wyrażenia](https://github.com/agileobjects/ReadableExpressions) [(licencja MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępna w [programie Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)), renderuje drzewo wyrażeń jako kod C#:

  ![Zrzut ekranu przedstawiający wizualizator wyrażeń czytelnych.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Wizualizator drzewa wyrażeń](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) [(licencja MIT),](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)zapewnia graficzny widok drzewa wyrażeń, jego właściwości i powiązanych obiektów; i może renderować drzewo wyrażeń przy użyciu kodu języka Visual Basic:

  ![Zrzut ekranu przedstawiający wizualizator ExpressionToString.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer-vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizator dla drzewa wyrażeń  
  
1. Kliknij ikonę lupy wyświetlaną obok drzewa wyrażeń w **etykietkach danych**, oknie **Czujka,** **Autos** lub w oknie **Zmiennicy.**  
  
    Zostanie wyświetlona lista dostępnych wizualizatorów.:

    ![Zrzut ekranu przedstawiający użytkownika otwierającego wizualizatory z programu Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers-vb.png)

2. Kliknij wizualizator, którego chcesz użyć.  

## <a name="see-also"></a>Zobacz też

- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Tworzenie niestandardowych wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`Składni](debugview-syntax.md)
