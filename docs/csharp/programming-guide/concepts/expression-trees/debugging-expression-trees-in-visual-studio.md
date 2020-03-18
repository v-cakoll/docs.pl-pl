---
title: Debugowanie drzew wyrażeń w programie Visual Studio (C#)
ms.date: 07/20/2015
ms.assetid: 1369fa25-0fbd-4b92-98d0-8df79c49c27a
ms.openlocfilehash: cf1708d1155e48d8609baca2067baa66dae08c5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169691"
---
# <a name="debugging-expression-trees-in-visual-studio-c"></a>Debugowanie drzew wyrażeń w programie Visual Studio (C#)
Można analizować strukturę i zawartość drzew wyrażeń podczas debugowania aplikacji. Aby uzyskać szybki przegląd struktury drzewa wyrażeń, można użyć `DebugView` właściwości, która reprezentuje drzewa wyrażeń przy użyciu [specjalnej składni](debugview-syntax.md). (Należy `DebugView` pamiętać, że jest dostępna tylko w trybie debugowania.)  

![Zrzut ekranu przedstawiający widok debugowania drzewa wyrażeń w debugerze VS.](media/debugging-expression-trees-in-visual-studio/debugview-expression-tree.png)

Ponieważ `DebugView` jest ciągiem, można użyć [wbudowanego wizualizatora tekstu,](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer) aby wyświetlić go w wielu wierszach, `DebugView` wybierając **wizualizację tekstu** z ikony lupy obok etykiety.

 ![Zrzut ekranu przedstawiający wizualizator tekstu zastosowany do wyników debugowania.](media/debugging-expression-trees-in-visual-studio/string-visualizer-debugview.png)

Alternatywnie można zainstalować i używać [niestandardowego wizualizatora](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data) dla drzew wyrażeń, takich jak:

- [Wyrażenia czytelne](https://github.com/agileobjects/ReadableExpressions) ([licencja MIT](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md), dostępne w [portalu Visual Studio Marketplace),](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers)renderują drzewo wyrażeń jako kod Języka C#:

  ![Zrzut ekranu przedstawiający wizualizator wyrażeń czytelnych.](media/debugging-expression-trees-in-visual-studio/readable-expressions-visualizer.png)

- [Visualizer drzewa wyrażeń](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) [(licencja MIT)](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)zapewnia graficzny widok drzewa wyrażeń, jego właściwości i powiązanych obiektów:

  ![Zrzut ekranu przedstawiający wizualizator drzewa wyrażeń.](media/debugging-expression-trees-in-visual-studio/expression-to-string-visualizer.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Aby otworzyć wizualizator drzewa wyrażeń  
  
1. Kliknij ikonę lupy wyświetlaną obok drzewa wyrażeń w **etykietkach danych,** oknie **Czujka,** **autos** lub w oknie **Locals.**  

    Zostanie wyświetlona lista dostępnych wizualizatorów.:

    ![Zrzut ekranu przedstawiający otwieranie wizualizatorów z programu Visual Studio.](media/debugging-expression-trees-in-visual-studio/expression-tree-visualizers.png)

2. Kliknij wizualizator, którego chcesz użyć.  
  
## <a name="see-also"></a>Zobacz też

- [Drzewa wyrażeń (C#)](./index.md)
- [Debugowanie w programie Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Tworzenie niestandardowych wizualizatorów](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView`Składni](debugview-syntax.md)
