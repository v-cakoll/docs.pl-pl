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
ms.openlocfilehash: 8750c48d08161260a1dba6ab69098980f25a5d55
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589646"
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
  
- Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
