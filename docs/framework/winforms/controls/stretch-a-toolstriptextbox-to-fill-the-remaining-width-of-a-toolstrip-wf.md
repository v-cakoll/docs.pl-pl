---
title: 'Instrukcje: Rozciąganie elementu ToolStripTextBox w celu wypełnienia pozostałego szerokości ToolStrip (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 707fd2e470a9be1d61d2878eeff845b3cad270db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971928"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Instrukcje: Rozciąganie elementu ToolStripTextBox w celu wypełnienia pozostałego szerokości ToolStrip (formularze Windows)
Po ustawieniu <xref:System.Windows.Forms.ToolStrip.Stretch%2A> właściwość <xref:System.Windows.Forms.ToolStrip> kontrolę `true`, formant wypełnienia jego kontenera od końca do końca i zmienia rozmiar, gdy jego kontenera zmienia rozmiar. W tej konfiguracji, może okazać się przydatne do rozciągania element w kontrolce, takich jak <xref:System.Windows.Forms.ToolStripTextBox>, w celu wypełnienia dostępnego miejsca, jak i rozmiaru, gdy zmienia rozmiar kontrolki. Rozciąganie ten jest przydatne na przykład, jeśli chcesz osiągnąć wygląd i zachowanie podobne do paska adresu w programie Microsoft® Internet Explorer.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu zawiera klasę pochodną <xref:System.Windows.Forms.ToolStripTextBox> o nazwie `ToolStripSpringTextBox`. Ta klasa zastępuje <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> metodę obliczania dostępności szerokość elementu nadrzędnego <xref:System.Windows.Forms.ToolStrip> sterowania po odjęciu łączna szerokość wszystkie pozostałe elementy. Ten przykład kodu udostępnia również <xref:System.Windows.Forms.Form> klasy i `Program` klasę wykazać nowe zachowanie.  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [ToolStrip, kontrolka — architektura](toolstrip-control-architecture.md)
- [Instrukcje: Użycie właściwości Spring interaktywnie w StatusStrip](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
