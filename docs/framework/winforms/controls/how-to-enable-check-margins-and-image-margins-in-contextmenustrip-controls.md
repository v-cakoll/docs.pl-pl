---
title: 'Instrukcje: włączanie marginesów zaznaczania i marginesów obrazów w kontrolkach ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ShowCheckMargin property [Windows Forms]
- ShowImageMargin property [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: eb584e71-59da-4012-aaca-dbe1c7c7a156
ms.openlocfilehash: bf8440704a7e457d0c987c933cc26e0e12e9565f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591693"
---
# <a name="how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls"></a>Instrukcje: włączanie marginesów zaznaczania i marginesów obrazów w kontrolkach ContextMenuStrip
Można dostosować <xref:System.Windows.Forms.ToolStripMenuItem> obiekty w swojej <xref:System.Windows.Forms.MenuStrip> kontrolę dzięki znaczniki wyboru i obrazów niestandardowych.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć elementy menu, które mają znaczniki wyboru i obrazów niestandardowych.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
 Ustaw <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A?displayProperty=nameWithType> właściwości, aby określić, kiedy znaczniki wyboru i obrazy niestandardowe są wyświetlane w elementów menu.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
