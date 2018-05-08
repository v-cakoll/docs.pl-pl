---
title: 'Porady: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 2700be06ceb4c20926d6af9c962799db4afc31da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Porady: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant
Formularze systemu Windows <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla hierarchię węzłów, podobnie jak pliki i foldery wyświetlane w okienku po lewej stronie Eksploratora Windows funkcji w systemach operacyjnych Windows. Przez ustawienie <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości, można podać kontekstowa operacji użytkownikowi po ich prawym przyciskiem myszy <xref:System.Windows.Forms.TreeView> formantu. Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnika z poszczególnymi <xref:System.Windows.Forms.TreeNode> elementy, można dodać dostosowanego poziomu funkcjonalności menu skrótów do Twojej <xref:System.Windows.Forms.TreeView> kontrolki.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Aby skojarzyć menu skrótów z elementu TreeNode w czasie projektowania  
  
1.  Dodaj <xref:System.Windows.Forms.TreeView> sterowania do formularza, a następnie dodaj węzły do <xref:System.Windows.Forms.TreeView> zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie i usuwanie węzłów za pomocą formantu TreeView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Dodaj <xref:System.Windows.Forms.ContextMenuStrip> składnika do formularza, a następnie dodaj elementy menu do menu skrótów, które reprezentują chcesz udostępnić w czasie wykonywania operacji na poziomie węzła. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie elementów Menu do paska ContextMenuStrip](../../../../docs/framework/winforms/controls/how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Otwórz ponownie **TreeNodeEditor** okno dialogowe <xref:System.Windows.Forms.TreeView> sterowania, wybierz węzeł, aby edytować i ustawić jej <xref:System.Windows.Forms.ContextMenuStrip> właściwości do menu skrótów, który został dodany.  
  
4.  Gdy ta właściwość jest ustawiona, zostanie wyświetlone menu skrótów po kliknięciu prawym przyciskiem myszy węzeł.  
  
     Ponadto można napisać kod obsługujący <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.  
  
## <a name="see-also"></a>Zobacz też  
 [TreeView, kontrolka](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [TreeView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [ContextMenuStrip, kontrolka](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)
