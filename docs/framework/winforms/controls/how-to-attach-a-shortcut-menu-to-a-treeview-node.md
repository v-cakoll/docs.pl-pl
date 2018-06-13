---
title: 'Porady: dołączanie menu ShortCut do węzła TreeView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shortcut menus [Windows Forms], adding to TreeView controls
- TreeView control [Windows Forms], adding shortcut menus
- tree nodes in TreeView control [Windows Forms], shortcut menus
ms.assetid: a23c6752-fd8f-44ad-b781-bab37962fc7c
ms.openlocfilehash: 737e74184b0763ed84b4e585f2508d69944d0e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528223"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>Porady: dołączanie menu ShortCut do węzła TreeView
Formularze systemu Windows <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla hierarchię węzłów, podobnie jak pliki i foldery wyświetlane w okienku po lewej stronie Eksploratora Windows. Przez ustawienie <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości, można podać kontekstowa operacji użytkownikowi po ich prawym przyciskiem myszy <xref:System.Windows.Forms.TreeView> formantu. Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnika z poszczególnymi <xref:System.Windows.Forms.TreeNode> elementy, można dodać dostosowanego poziomu funkcjonalności menu skrótów do Twojej <xref:System.Windows.Forms.TreeView> kontrolki.  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>Aby skojarzyć menu skrótów z elementu TreeNode programowo  
  
1.  Utwórz wystąpienie <xref:System.Windows.Forms.TreeView> sterować za pomocą właściwości, należy utworzyć katalog główny <xref:System.Windows.Forms.TreeNode>, a następnie dodaj węzły podrzędne.  
  
2.  Utwórz wystąpienie <xref:System.Windows.Forms.ContextMenuStrip> składnik, a następnie dodaj <xref:System.Windows.Forms.ToolStripMenuItem> dla każdej operacji, które mają być dostępne w czasie wykonywania.  
  
3.  Ustaw <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> odpowiednie właściwości <xref:System.Windows.Forms.TreeNode> do tworzenia menu skrótów.  
  
4.  Gdy ta właściwość jest ustawiona, zostanie wyświetlone menu skrótów po kliknięciu prawym przyciskiem myszy węzeł.  
  
 Poniższy przykład kodu tworzy podstawowego <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ContextMenuStrip> skojarzony z elementem głównym <xref:System.Windows.Forms.TreeNode> z <xref:System.Windows.Forms.TreeView>. Należy dostosować opcje menu do tych, które pasują do <xref:System.Windows.Forms.TreeView> tworzysz. Ponadto można napisać kod obsługujący <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
