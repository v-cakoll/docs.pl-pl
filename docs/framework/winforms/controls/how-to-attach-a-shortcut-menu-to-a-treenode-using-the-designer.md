---
title: 'Instrukcje: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040447"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>Instrukcje: dołączanie menu skrótów do TreeNode przy użyciu narzędzia Projektant
Kontrolka <xref:System.Windows.Forms.TreeView> Windows Forms Wyświetla hierarchię węzłów, podobnie jak pliki i foldery wyświetlane w lewym okienku funkcji Eksplorator Windows w systemach operacyjnych Windows. Ustawiając <xref:System.Windows.Forms.Control.ContextMenuStrip%2A> właściwość, można zapewnić użytkownikowi operacje zależne od kontekstu po <xref:System.Windows.Forms.TreeView> kliknięciu kontrolki prawym przyciskiem myszy. Kojarząc <xref:System.Windows.Forms.ContextMenuStrip> składnik z poszczególnymi <xref:System.Windows.Forms.TreeNode> elementami, można dodać dostosowany poziom funkcji menu <xref:System.Windows.Forms.TreeView> skrótów do kontrolek.

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>Aby skojarzyć menu skrótów z elementem TreeNode w czasie projektowania

1. Dodaj kontrolkę do formularza, a następnie Dodaj do niej <xref:System.Windows.Forms.TreeView> węzły. <xref:System.Windows.Forms.TreeView> Aby uzyskać więcej informacji, zobacz [jak: Dodawanie i usuwanie węzłów za pomocą kontrolki](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)TreeView Windows Forms.

2. <xref:System.Windows.Forms.ContextMenuStrip> Dodaj składnik do formularza, a następnie Dodaj elementy menu do menu skrótów, które reprezentuje operacje na poziomie węzła, które mają być dostępne w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodaj elementy menu do ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md).

3. Otwórz ponownie okno dialogowe **TreeNodeEditor** dla <xref:System.Windows.Forms.TreeView> kontrolki, wybierz węzeł do edycji i ustaw jego <xref:System.Windows.Forms.ContextMenuStrip> właściwość na dodane menu skrótów.

4. Gdy ta właściwość jest ustawiona, menu skrótów będzie wyświetlane po kliknięciu prawym przyciskiem myszy węzła.

     Ponadto należy napisać kod, aby obsłużyć <xref:System.Windows.Forms.ToolStripItem.Click> zdarzenia dla tych elementów menu.

## <a name="see-also"></a>Zobacz także

- [TreeView, kontrolka](treeview-control-windows-forms.md)
- [TreeView, kontrolka — omówienie](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip, kontrolka](contextmenustrip-control.md)
