---
title: 'Instrukcje: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 1cc90ed9a103c41dbf85e39a43d307b1c0422603
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191450"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Instrukcje: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant
Formularze Windows <xref:System.Windows.Forms.TreeView> kontrolka Wyświetla hierarchię węzłów, podobnie jak pliki i foldery, wyświetlana w okienku po lewej stronie funkcji Eksploratora Windows w systemach operacyjnych Windows. Ustawiając <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwości, można zapewnić kontekstową operacje użytkownika po ich prawym przyciskiem myszy <xref:System.Windows.Forms.TreeView> kontroli. Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnika za pomocą poszczególnych <xref:System.Windows.Forms.TreeNode> elementy, można dodać niestandardowe poziom funkcjonalności menu skrótów do Twojej <xref:System.Windows.Forms.TreeView> kontrolki.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Aby skojarzyć menu skrótów z elementu TreeNode w czasie projektowania  
  
1.  Dodaj <xref:System.Windows.Forms.TreeView> sterowania do formularza, a następnie dodaj węzły do <xref:System.Windows.Forms.TreeView> zgodnie z potrzebami. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie węzłów za pomocą Windows kontrolki TreeView formularzy](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md).  
  
2.  Dodaj <xref:System.Windows.Forms.ContextMenuStrip> składnika do formularza, a następnie dodaj elementy menu do menu skrótów, które reprezentują operacje poziomu węzła, które chcesz udostępnić w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie elementów Menu do paska ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).  
  
3.  Otwórz ponownie **TreeNodeEditor** okno dialogowe <xref:System.Windows.Forms.TreeView> sterowania, wybierz węzeł, aby edytować, a następnie ustaw jego <xref:System.Windows.Forms.ContextMenuStrip> właściwości do menu skrótów, który został dodany.  
  
4.  Gdy ta właściwość jest ustawiona, zostanie wyświetlone menu skrótów, po kliknięciu prawym przyciskiem myszy węzeł.  
  
     Ponadto, można napisać kod obsługujący <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.  
  
## <a name="see-also"></a>Zobacz także

- [TreeView — Formant](treeview-control-windows-forms.md)
- [TreeView, kontrolka — omówienie](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip — Formant](contextmenustrip-control.md)
