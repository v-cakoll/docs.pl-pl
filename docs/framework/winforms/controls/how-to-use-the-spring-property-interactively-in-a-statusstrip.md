---
title: 'Instrukcje: użycie właściwości Spring interaktywnie w StatusStrip'
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
ms.openlocfilehash: 7d79a885f49168c3883259826e7b8ae62eec1dab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108189"
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Instrukcje: użycie właściwości Spring interaktywnie w StatusStrip
Możesz użyć <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości pozycji <xref:System.Windows.Forms.ToolStripStatusLabel> w kontrolce <xref:System.Windows.Forms.StatusStrip> kontroli. <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> Właściwość określa, czy <xref:System.Windows.Forms.ToolStripStatusLabel> kontroli automatycznie wypełni dostępne miejsce na <xref:System.Windows.Forms.StatusStrip> kontroli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób używania <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości pozycji <xref:System.Windows.Forms.ToolStripStatusLabel> w kontrolce <xref:System.Windows.Forms.StatusStrip> kontroli. <xref:System.Windows.Forms.ToolStripItem.Click> Programu obsługi zdarzeń wykonuje wyłącznie — lub operacji (XOR), aby przełączyć się wartość <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.  
  
 Aby wykorzystać ten przykład kodu, skompiluj i uruchom aplikację, a następnie kliknij **bliski (Spring)** na <xref:System.Windows.Forms.StatusStrip> sterowania, aby przełączyć się wartość <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> właściwości.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
