---
title: 'Instrukcje: dynamiczne dodawanie elementów ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: 9426c7cb3251dbbd95727b78c57be7a0b71556e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624013"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a>Instrukcje: dynamiczne dodawanie elementów ToolStrip
Możesz dynamicznie wypełnić kolekcję elementów menu <xref:System.Windows.Forms.ToolStrip> kontrolować, po otwarciu menu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak dynamicznie dodać elementy do <xref:System.Windows.Forms.ContextMenuStrip> kontroli. W przykładzie pokazano również sposób ponownie użyj tego samego <xref:System.Windows.Forms.ContextMenuStrip> dla trzech różnych kontrolek w formularzu.  
  
 W tym przykładzie <xref:System.Windows.Forms.ToolStripDropDown.Opening> program obsługi zdarzeń wypełnia kolekcję elementów menu. <xref:System.Windows.Forms.ToolStripDropDown.Opening> Sprawdza, czy program obsługi zdarzeń <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> właściwości i dodaje <xref:System.Windows.Forms.ToolStripItem> opisujące kontroli źródła.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów System.Drawing i pozycję System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
