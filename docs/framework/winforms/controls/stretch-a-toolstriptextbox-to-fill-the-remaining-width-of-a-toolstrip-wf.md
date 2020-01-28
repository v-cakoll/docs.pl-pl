---
title: 'Porady: rozciąganie ToolStripTextBox w celu uzupełnienia szerokości ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742841"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Porady: rozciąganie ToolStripTextBox w celu uzupełnienia szerokości ToolStrip (Formularze systemu Windows)
Po ustawieniu właściwości <xref:System.Windows.Forms.ToolStrip.Stretch%2A> kontrolki <xref:System.Windows.Forms.ToolStrip> na `true`, formant wypełni jego kontener od końca do końca i zmienia rozmiar, gdy rozmiar kontenera zostanie zmieniony. W tej konfiguracji przydatne może być rozciągnięcie elementu w formancie, takiego jak <xref:System.Windows.Forms.ToolStripTextBox>, wypełnienie dostępnego miejsca i zmiana rozmiaru kontrolki. To rozciąganie jest przydatne, jeśli na przykład chcesz uzyskać wygląd i zachowanie podobne do paska adresu w programie Microsoft® Internet Explorer.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu udostępnia klasę pochodną <xref:System.Windows.Forms.ToolStripTextBox> o nazwie `ToolStripSpringTextBox`. Ta klasa przesłania metodę <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A>, aby obliczyć dostępną szerokość kontrolki nadrzędnej <xref:System.Windows.Forms.ToolStrip> po odjęciu połączonej szerokości wszystkich innych elementów. Ten przykład kodu dostarcza również klasy <xref:System.Windows.Forms.Form> i klasy `Program`, aby pokazać nowe zachowanie.  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
- [Instrukcje: użycie właściwości Spring interaktywnie w kontrolce StatusStrip](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
