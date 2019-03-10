---
title: 'Instrukcje: Dołączanie ShortCut Menu do węzła TreeView'
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
ms.openlocfilehash: 537593399db7deb775929cd742a749ce47890db6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703627"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treeview-node"></a>Instrukcje: Dołączanie ShortCut Menu do węzła TreeView
Formularze Windows <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla hierarchię węzłów, podobnie jak pliki i foldery, wyświetlana w okienku po lewej stronie Eksploratora Windows. Ustawiając <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości, można zapewnić kontekstową operacje użytkownika po ich prawym przyciskiem myszy <xref:System.Windows.Forms.TreeView> kontroli. Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnika za pomocą poszczególnych <xref:System.Windows.Forms.TreeNode> elementy, można dodać niestandardowe poziom funkcjonalności menu skrótów do Twojej <xref:System.Windows.Forms.TreeView> kontrolki.  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-programmatically"></a>Aby programowo kojarzenie menu skrótów za pomocą elementu TreeNode  
  
1.  Utwórz wystąpienie <xref:System.Windows.Forms.TreeView> sterować za pomocą właściwości, utworzenie głównego <xref:System.Windows.Forms.TreeNode>, a następnie dodaj węzły podrzędne.  
  
2.  Utwórz wystąpienie <xref:System.Windows.Forms.ContextMenuStrip> składnik, a następnie dodaj <xref:System.Windows.Forms.ToolStripMenuItem> dla każdej operacji, które chcesz udostępnić w czasie wykonywania.  
  
3.  Ustaw <xref:System.Windows.Forms.TreeNode.ContextMenuStrip%2A> własności odpowiednie <xref:System.Windows.Forms.TreeNode> do menu skrótów, możesz utworzyć.  
  
4.  Gdy ta właściwość jest ustawiona, zostanie wyświetlone menu skrótów, po kliknięciu prawym przyciskiem myszy węzeł.  
  
 Poniższy przykład kodu tworzy podstawową <xref:System.Windows.Forms.TreeView> i <xref:System.Windows.Forms.ContextMenuStrip> skojarzonego z certyfikatem głównym <xref:System.Windows.Forms.TreeNode> z <xref:System.Windows.Forms.TreeView>. Trzeba będzie dostosować opcje menu do tych, które mieszczą się <xref:System.Windows.Forms.TreeView> tworzysz. Ponadto, można napisać kod obsługujący <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.  
  
 [!code-cpp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/cpp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/cpp/Form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.TreeNodeContextMenuStrip#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.TreeNodeContextMenuStrip/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ContextMenuStrip>
- [TreeView, kontrolka](treeview-control-windows-forms.md)
