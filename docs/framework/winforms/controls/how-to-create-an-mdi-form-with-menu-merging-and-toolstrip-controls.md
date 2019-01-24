---
title: 'Instrukcje: Tworzenie formularza MDI ze scalaniem Menu i formantów ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: 6cbab3c588aa74809a7aef80ae6ffc4c3772069f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54646019"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>Instrukcje: Tworzenie formularza MDI ze scalaniem Menu i formantów ToolStrip
<xref:System.Windows.Forms?displayProperty=nameWithType> Przestrzeń nazw obsługuje wiele aplikacji interfejsu (MDI) dokumentu i <xref:System.Windows.Forms.MenuStrip> kontrolka obsługuje scalania menu. Formularze MDI może również <xref:System.Windows.Forms.ToolStrip> kontrolki.  
  
 Brak zaawansowaną obsługę dla tej funkcji w programie Visual Studio.  
  
 Zobacz też [instruktażu: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStripPanel> formanty z formularza MDI. Formularz obsługuje także menu scalanie z menu podrzędne.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy przykład kodu wymaga:  
  
-   Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz również [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz także
- [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
