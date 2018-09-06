---
title: 'Porady: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 77c4b01100aec2df16d5eb844f73f7a2bfa115aa
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864749"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Porady: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant
Formularze Windows <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla hierarchię węzłów, podobnie jak pliki i foldery, wyświetlana w okienku po lewej stronie funkcji Eksploratora Windows w systemach operacyjnych Windows. Ustawiając <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości, można zapewnić kontekstową operacje użytkownika po ich prawym przyciskiem myszy <xref:System.Windows.Forms.TreeView> kontroli. Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnika za pomocą poszczególnych <xref:System.Windows.Forms.TreeNode> elementy, można dodać niestandardowe poziom funkcjonalności menu skrótów do Twojej <xref:System.Windows.Forms.TreeView> kontrolki.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Aby skojarzyć menu skrótów z elementu TreeNode w czasie projektowania  
  
1.  Dodaj <xref:System.Windows.Forms.TreeView> sterowania do formularza, a następnie dodaj węzły do <xref:System.Windows.Forms.TreeView> zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Dodaj <xref:System.Windows.Forms.ContextMenuStrip> składnika do formularza, a następnie dodaj elementy menu do menu skrótów, które reprezentują operacje poziomu węzła, które chcesz udostępnić w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie elementów Menu do paska ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Otwórz ponownie **TreeNodeEditor** okno dialogowe <xref:System.Windows.Forms.TreeView> sterowania, wybierz węzeł, aby edytować, a następnie ustaw jego <xref:System.Windows.Forms.ContextMenuStrip> właściwości do menu skrótów, który został dodany.  
  
4.  Gdy ta właściwość jest ustawiona, zostanie wyświetlone menu skrótów, po kliknięciu prawym przyciskiem myszy węzeł.  
  
     Ponadto, można napisać kod obsługujący <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.  
  
## <a name="see-also"></a>Zobacz też  
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [ContextMenuStrip, kontrolka](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
