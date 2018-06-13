---
title: 'Porady: rozciąganie ToolStripTextBox w celu uzupełnienia szerokości ToolStrip (Formularze systemu Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: bd58cbd109b8e3dd04c6a284dc6926e95830fb61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537723"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Porady: rozciąganie ToolStripTextBox w celu uzupełnienia szerokości ToolStrip (Formularze systemu Windows)
Podczas ustawiania <xref:System.Windows.Forms.ToolStrip.Stretch%2A> właściwość <xref:System.Windows.Forms.ToolStrip> formant `true`, formantu wypełnia jego kontenera od końca do końca i zmienia rozmiar w przypadku jego kontenera zmienia rozmiar. Ta konfiguracja może być przydatne do rozciągania elementu w formancie, takich jak <xref:System.Windows.Forms.ToolStripTextBox>, w celu wypełnienia dostępnego miejsca, jak i rozmiaru, gdy zmienia rozmiar formantu. Rozciąganie ten jest przydatne, na przykład, jeśli chcesz osiągnąć wygląd i zachowanie jest podobne do paska adresu w programie Microsoft® Internet Explorer.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu przedstawiono klasę pochodzącą od <xref:System.Windows.Forms.ToolStripTextBox> o nazwie `ToolStripSpringTextBox`. Ta klasa zastępuje <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> metodę obliczania dostępności szerokość elementu nadrzędnego <xref:System.Windows.Forms.ToolStrip> kontrolować, po odjęciu łączna szerokość wszystkie inne elementy. W tym przykładzie kodu udostępnia również <xref:System.Windows.Forms.Form> klasy i `Program` klasy, aby zademonstrować nowe zachowanie.  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [ToolStrip, kontrolka — architektura](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Instrukcje: użycie właściwości Spring interaktywnie w kontrolce StatusStrip](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
