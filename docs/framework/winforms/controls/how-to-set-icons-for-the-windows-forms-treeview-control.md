---
title: 'Instrukcje: Ustawienie ikon dla kontrolki TreeView formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: 49b44c604a8532c6d2beb39b917f3e5ade339c49
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564032"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Instrukcje: Ustawienie ikon dla kontrolki TreeView formularzy Windows
Formularze Windows <xref:System.Windows.Forms.TreeView> formant może wyświetlać ikony obok każdego węzła. Ikony są pozycjonowane natychmiastowego po lewej stronie tekstu węzła. Aby wyświetlić te ikony, należy skojarzyć widok drzewa z <xref:System.Windows.Forms.ImageList> kontroli. Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnika ImageList](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) i [jak: Dodawanie lub usuwanie obrazów za pomocą Windows składnika ImageList formularzy](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
>  Usterki programu Microsoft .NET Framework w wersji 1.1 zapobiega wyświetlaniu w obrazów <xref:System.Windows.Forms.TreeView> węzłów, gdy Twoja aplikacja wywołuje <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Aby obejść ten problem, należy wywołać <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> w swojej `Main` metoda natychmiast po wywołaniu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Ten problem został rozwiązany w [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].  
  
### <a name="to-display-images-in-a-tree-view"></a>Aby wyświetlić obrazy w widoku drzewa  
  
1.  Ustaw <xref:System.Windows.Forms.TreeView> kontrolki <xref:System.Windows.Forms.TreeView.ImageList%2A> właściwości do istniejących <xref:System.Windows.Forms.ImageList> kontrolki, które chcesz użyć.  
  
     Te właściwości można ustawić w projektancie w oknie właściwości lub w kodzie.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2.  Ustaw węzeł <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> i <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> właściwości. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> Właściwość określa obraz wyświetlany dla stanów normalne i rozwiniętego węzła i <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> właściwość określa obraz wyświetlany dla wybranego stanu węzła.  
  
     Te właściwości można ustawić w kodzie lub w obrębie elementu TreeNode Editor. Aby otworzyć Edytor TreeNode, kliknij przycisk oznaczony wielokropkiem ( ![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości w oknie dialogowym właściwości.  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a>Zobacz także
- [TreeView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)
- [Instrukcje: Dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Instrukcje: Iterowanie wszystkich węzłów kontrolki TreeView formularzy Windows](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: Określanie, który węzeł TreeView został kliknięty](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: Dodawanie niestandardowych informacji do TreeView lub ListView — formant (formularze Windows)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
