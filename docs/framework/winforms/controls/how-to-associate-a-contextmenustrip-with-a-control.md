---
title: 'Porady: skojarzenie właściwości ContextMenuStrip z formantem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], relating
- ContextMenuStrips [Windows Forms], associating with controls
- context menus [Windows Forms], associating with controls
- ContextMenuStrips [Windows Forms], relating
ms.assetid: 6fc40a42-5d69-427f-aa30-0a146193226b
ms.openlocfilehash: 4014324d83e4de634ff7b42204d50fa11dff7ea3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526413"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>Porady: skojarzenie właściwości ContextMenuStrip z formantem
Po utworzeniu sieci formantów i menu skrótów, umożliwia wyświetlenie menu skrótów danego po kliknięciu formantu poniższych procedur. Te procedury skojarzyć <xref:System.Windows.Forms.ContextMenuStrip> z formularza systemu Windows i <xref:System.Windows.Forms.ToolStrip> formantu.  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>Skojarzenie właściwości ContextMenuStrip z formularza systemu Windows  
  
1.  Ustaw <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>Skojarzenie właściwości ContextMenuStrip z formantu ToolStrip  
  
1.  Ustawianie formantu <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy formularz systemu Windows i <xref:System.Windows.Forms.ToolStrip>i kojarzy innej <xref:System.Windows.Forms.ContextMenuStrip> kontroli z każdym z nich.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>  
 <xref:System.Windows.Forms.ToolStrip>  
 [Instrukcje: dodawanie elementów menu do kontrolki ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)  
 [ContextMenuStrip, kontrolka](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
