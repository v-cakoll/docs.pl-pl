---
title: 'Instrukcje: Usuń atrament na niestandardowej kontrolce'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
ms.openlocfilehash: 60e2af64cb0c5b313f4f1201cab70da6a88f61e7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365896"
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>Instrukcje: Usuń atrament na niestandardowej kontrolce
<xref:System.Windows.Ink.IncrementalStrokeHitTester> Określa, czy obecnie rysowane obrysu przecina innego obrysu.  Jest to przydatne w przypadku tworzenia formantu, który umożliwia użytkownikowi wymazać część pociągnięcia, sposób użytkownik może na <xref:System.Windows.Controls.InkCanvas> podczas <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> ustawiono <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy formant niestandardowy, który umożliwia użytkownikowi wymazać część pociągnięcia.  Ten przykład tworzy formant, który zawiera pisma odręcznego, po jego zainicjowaniu.  Aby utworzyć formant, który umożliwia zbieranie pisma odręcznego, zobacz [tworzenie kontrolki danych wejściowych pisma odręcznego](creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
