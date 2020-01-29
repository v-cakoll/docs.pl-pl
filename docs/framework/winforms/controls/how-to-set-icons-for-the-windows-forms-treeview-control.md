---
title: Ustawianie ikon dla kontrolki TreeView
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
ms.openlocfilehash: e3d7fc35c6d9f70822cdd0b69dd12f3d469f4ffa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737261"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Porady: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.TreeView> Windows Forms może wyświetlać ikony obok każdego węzła. Ikony są umieszczane bezpośrednio po lewej stronie tekstu węzła. Aby wyświetlić te ikony, należy skojarzyć widok drzewa z kontrolką <xref:System.Windows.Forms.ImageList>. Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnik ImageList](imagelist-component-windows-forms.md) i [instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).  
  
> [!NOTE]
> Usterka w programie Microsoft .NET Framework w wersji 1,1 uniemożliwia wyświetlanie obrazów na węzłach <xref:System.Windows.Forms.TreeView>, gdy aplikacja wywoła <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>. Aby obejść ten błąd, wywołaj <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> w metodzie `Main` natychmiast po wywołaniu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Ta usterka została naprawiona w .NET Framework 2,0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Aby wyświetlić obrazy w widoku drzewa  
  
1. Ustaw właściwość <xref:System.Windows.Forms.TreeView.ImageList%2A> kontrolki <xref:System.Windows.Forms.TreeView> na istniejącą kontrolkę <xref:System.Windows.Forms.ImageList>, której chcesz użyć.  
  
     Te właściwości można ustawić w projektancie przy użyciu okno Właściwości lub w kodzie.  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. Ustaw właściwości <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> i <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> węzła. Właściwość <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> określa obraz wyświetlany dla Stanów normalne i rozwinięte węzła, a właściwość <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> określa obraz wyświetlany dla wybranego stanu węzła.  
  
     Te właściwości można ustawić w kodzie lub w edytorze TreeNode. Aby otworzyć Edytor TreeNode, kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno Właściwości programu Visual Studio.](./media/visual-studio-ellipsis-button.png)) obok właściwości <xref:System.Windows.Forms.TreeView.Nodes%2A> na okno Właściwości.  
  
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

- [TreeView, kontrolka — omówienie](treeview-control-overview-windows-forms.md)
- [Instrukcje: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Instrukcje: iterowanie po wszystkich węzłach kontrolki TreeView formularzy Windows Forms](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: określanie, który węzeł TreeView został kliknięty](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
