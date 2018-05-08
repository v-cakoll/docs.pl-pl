---
title: Jak usunąć atrament na niestandardowej kontrolce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [WPF], erasing ink on
- ink [WPF], erasing on custom control
ms.assetid: d88c50f9-b4d8-4962-a28b-67d6a15a5fe0
ms.openlocfilehash: 66c0d19b368b56821fd4034ec4c7cd397b244ab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-erase-ink-on-a-custom-control"></a>Jak usunąć atrament na niestandardowej kontrolce
<xref:System.Windows.Ink.IncrementalStrokeHitTester> Określa, czy obecnie narysowanego obrysu przecina obrysu innego.  Jest to przydatne do tworzenia formantu, który umożliwia użytkownikowi wymazać części pociągnięcia, sposób użytkownik może na <xref:System.Windows.Controls.InkCanvas> podczas <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> ma ustawioną wartość <xref:System.Windows.Controls.InkCanvasEditingMode.EraseByPoint>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy kontrolkę niestandardową, który umożliwia użytkownikowi na usunięcie części pociągnięć.  W tym przykładzie tworzy kontrolkę, która zawiera odręczne po zainicjowaniu.  Aby utworzyć formant, który zbiera pismo odręczne, zobacz [Tworzenie formantu danych wejściowych odręcznego](../../../../docs/framework/wpf/advanced/creating-an-ink-input-control.md).  
  
 [!code-csharp[HowToEraseInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToEraseInk/CSharp/InkEraser.cs#1)]
 [!code-vb[HowToEraseInk#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToEraseInk/VisualBasic/InkEraser.vb#1)]
