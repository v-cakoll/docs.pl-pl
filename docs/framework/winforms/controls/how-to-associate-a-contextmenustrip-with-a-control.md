---
title: 'Instrukcje: Kojarzenie kontrolki ContextMenuStrip z kontrolką'
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
ms.openlocfilehash: 979245291a03b07b7bad548193737c0577b5c107
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221124"
---
# <a name="how-to-associate-a-contextmenustrip-with-a-control"></a>Instrukcje: Kojarzenie kontrolki ContextMenuStrip z kontrolką
Po utworzeniu menu skrótów i kontrolki, na których należy użyć poniższych procedur do wyświetlenia menu skrótów danego, gdy użytkownik kliknie prawym przyciskiem myszy formant. Te procedury skojarzyć <xref:System.Windows.Forms.ContextMenuStrip> z formularza Windows i <xref:System.Windows.Forms.ToolStrip> kontroli.  
  
### <a name="to-associate-a-contextmenustrip-with-a-windows-form"></a>Aby skojarzenie właściwości ContextMenuStrip z formularzem Windows  
  
1.  Ustaw <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.  
  
### <a name="to-associate-a-contextmenustrip-with-a-toolstrip-control"></a>Aby skojarzyć kontrolki ContextMenuStrip z formantu ToolStrip  
  
1.  Ustaw dla formantu <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość na nazwę skojarzonego <xref:System.Windows.Forms.ContextMenuStrip>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy formularz Windows i <xref:System.Windows.Forms.ToolStrip>i kojarzy innego <xref:System.Windows.Forms.ContextMenuStrip> kontrolki z każdym z nich.  
  
 [!code-csharp[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ContextMenuStrip/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>
- <xref:System.Windows.Forms.ToolStrip>
- [Instrukcje: Dodawanie elementów Menu do paska ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md)
- [ContextMenuStrip, kontrolka](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
