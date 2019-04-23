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
ms.openlocfilehash: d70c5b8f548cf325083782d6ea185c18fd2fa003
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216213"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a>Instrukcje: dodawanie elementu ToolStripContainer do formularza
Możesz programowo dodać <xref:System.Windows.Forms.ToolStripContainer> do formularza Windows i wypełnić ją za pomocą kontrolek.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób dodawania <xref:System.Windows.Forms.ToolStripContainer> i <xref:System.Windows.Forms.ToolStrip> do formularzy Windows, jak dodać elementy do <xref:System.Windows.Forms.ToolStrip>oraz sposób dodawania <xref:System.Windows.Forms.ToolStrip> do <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poniższy przykład kodu wymaga:  
  
-   Odwołania do zestawów System.Drawing, System.Text i przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStripContainer>
- [ToolStripContainer, kontrolka](toolstripcontainer-control.md)
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
