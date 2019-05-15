---
title: 'Instrukcje: dodawanie elementu ToolStripContainer do formularza'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 3d69bc6ed0cf23da8315ae95565300d151069d51
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582567"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a>Instrukcje: dodawanie elementu ToolStripContainer do formularza
Możesz programowo dodać <xref:System.Windows.Forms.ToolStripContainer> do formularza Windows i wypełnić ją za pomocą kontrolek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób dodawania <xref:System.Windows.Forms.ToolStripContainer> i <xref:System.Windows.Forms.ToolStrip> do formularzy Windows, jak dodać elementy do <xref:System.Windows.Forms.ToolStrip>oraz sposób dodawania <xref:System.Windows.Forms.ToolStrip> do <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy przykład kodu wymaga:  
  
- Odwołania do zestawów System.Drawing, System.Text i przestrzeń nazw System.Windows.Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStripContainer, kontrolka](toolstripcontainer-control.md)
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
