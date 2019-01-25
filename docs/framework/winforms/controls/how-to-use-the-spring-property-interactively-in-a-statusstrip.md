---
title: 'Instrukcje: Użycie właściwości Spring interaktywnie w StatusStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: cfce4e75d47bcaf67610312b95093282f9d1fa91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582287"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Instrukcje: Użycie właściwości Spring interaktywnie w StatusStrip
Możesz użyć <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości pozycji <xref:System.Windows.Forms.ToolStripStatusLabel> w kontrolce <xref:System.Windows.Forms.StatusStrip> kontroli. <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Właściwość określa, czy <xref:System.Windows.Forms.ToolStripStatusLabel> kontroli automatycznie wypełni dostępne miejsce na <xref:System.Windows.Forms.StatusStrip> kontroli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości pozycji <xref:System.Windows.Forms.ToolStripStatusLabel> w kontrolce <xref:System.Windows.Forms.StatusStrip> kontroli. <xref:System.Windows.Forms.ToolStripItem.Click> Programu obsługi zdarzeń wykonuje wyłącznie — lub operacji (XOR), aby przełączyć się wartość <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.  
  
 Aby wykorzystać ten przykład kodu, skompiluj i uruchom aplikację, a następnie kliknij **bliski (Spring)** na <xref:System.Windows.Forms.StatusStrip> sterowania, aby przełączyć się wartość <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby uzyskać informacje o tworzeniu tego przykładu z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [jak: Skompilować i uruchomić przykładowy kod pełną Windows Forms przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
