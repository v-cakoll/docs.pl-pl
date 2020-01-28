---
title: 'Porady: określanie, który węzeł TreeView został kliknięty'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: 7a0e2b69bbec0eb03d40bee2c8e2d4bc9c3558f9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742012"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Porady: określanie, który węzeł TreeView został kliknięty (Formularze systemu Windows)
Podczas pracy z kontrolką Windows Forms <xref:System.Windows.Forms.TreeView>, typowe zadanie polega na określeniu, który węzeł został kliknięty, i odpowiednio odpowiedzieć.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Aby określić, który węzeł TreeView został kliknięty  
  
1. Użyj obiektu <xref:System.EventArgs>, aby zwrócić odwołanie do klikniętego obiektu węzła.  
  
2. Ustal, który węzeł został kliknięty, sprawdzając klasę <xref:System.Windows.Forms.TreeViewEventArgs>, która zawiera dane związane ze zdarzeniem.  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    > Alternatywnie można użyć <xref:System.Windows.Forms.MouseEventArgs> zdarzenia <xref:System.Windows.Forms.Control.MouseDown> lub <xref:System.Windows.Forms.Control.MouseUp>, aby uzyskać <xref:System.Drawing.Point.X%2A> i <xref:System.Drawing.Point.Y%2A> wartości współrzędnych <xref:System.Drawing.Point>, gdzie wystąpił przycisk. Następnie użyj metody <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> formantu <xref:System.Windows.Forms.TreeView>, aby określić, który węzeł został kliknięty.  
  
## <a name="see-also"></a>Zobacz także

- [TreeView, kontrolka](treeview-control-windows-forms.md)
