---
title: 'Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows'
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
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909809"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>Instrukcje: ustawienie ikon dla kontrolki TreeView formularzy systemu Windows
Kontrolka <xref:System.Windows.Forms.TreeView> Windows Forms może wyświetlać ikony obok każdego węzła. Ikony są umieszczane bezpośrednio po lewej stronie tekstu węzła. Aby wyświetlić te ikony, należy skojarzyć widok drzewa z <xref:System.Windows.Forms.ImageList> kontrolką. Aby uzyskać więcej informacji na temat list obrazów, zobacz [składnik ImageList](imagelist-component-windows-forms.md) i [instrukcje: Dodawanie lub usuwanie obrazów za pomocą składnika](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)ImageList Windows Forms.  
  
> [!NOTE]
> Usterka w programie Microsoft .NET Framework w wersji 1,1 uniemożliwia wyświetlanie obrazów <xref:System.Windows.Forms.TreeView> w węzłach, gdy <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>aplikacja jest wywoływana. Aby obejść ten błąd, wywołaj <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> `Main` metodę natychmiast po wywołaniu <xref:System.Windows.Forms.Application.EnableVisualStyles%2A>. Ta usterka została naprawiona w .NET Framework 2,0.  
  
### <a name="to-display-images-in-a-tree-view"></a>Aby wyświetlić obrazy w widoku drzewa  
  
1. <xref:System.Windows.Forms.TreeView> Ustaw Właściwość<xref:System.Windows.Forms.TreeView.ImageList%2A> kontrolki na istniejącą <xref:System.Windows.Forms.ImageList> kontrolkę, której chcesz użyć.  
  
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
  
2. Ustaw właściwości węzła <xref:System.Windows.Forms.TreeNode.ImageIndex%2A> i <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> . Właściwość określa obraz wyświetlany dla Stanów normalne i rozwinięte węzła, <xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A> a właściwość określa obraz wyświetlany dla wybranego stanu węzła. <xref:System.Windows.Forms.TreeNode.ImageIndex%2A>  
  
     Te właściwości można ustawić w kodzie lub w edytorze TreeNode. Aby otworzyć Edytor TreeNode, kliknij przycisk wielokropka ( ![przycisk wielokropka (...) w okno właściwości programu Visual](./media/visual-studio-ellipsis-button.png)Studio) obok <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości okno właściwości.  
  
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
- [Instrukcje: Dodawanie i usuwanie węzłów za pomocą kontrolki TreeView Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Instrukcje: Wykonaj iterację wszystkich węzłów kontrolki Windows Forms TreeView](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [Instrukcje: Określ, który węzeł TreeView został kliknięty](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [Instrukcje: Dodawanie niestandardowych informacji do kontrolki TreeView lub ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
