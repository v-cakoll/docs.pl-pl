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
ms.openlocfilehash: d960eaae2aa479e0be74e9a5e4fdbfec8ff411c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182179"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Porady: określanie, który węzeł TreeView został kliknięty (Formularze systemu Windows)
Podczas pracy z <xref:System.Windows.Forms.TreeView> formantem Windows Forms typowym zadaniem jest określenie, który węzeł został kliknięty i odpowiednio reagować.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Aby określić, który węzeł TreeView został kliknięty  
  
1. Użyj <xref:System.EventArgs> obiektu, aby zwrócić odwołanie do kliknięty obiekt węzła.  
  
2. Określ, który węzeł został <xref:System.Windows.Forms.TreeViewEventArgs> kliknięty, sprawdzając klasę, która zawiera dane związane ze zdarzeniem.  
  
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
    > <xref:System.Windows.Forms.MouseEventArgs> Alternatywnie można użyć <xref:System.Windows.Forms.Control.MouseDown> zdarzenia lub, <xref:System.Windows.Forms.Control.MouseUp> aby uzyskać <xref:System.Drawing.Point.X%2A> <xref:System.Drawing.Point.Y%2A> i współrzędnych wartości, gdzie <xref:System.Drawing.Point> nastąpiło kliknięcie. Następnie użyj <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metody formantu, aby określić, który węzeł został kliknięty.  
  
## <a name="see-also"></a>Zobacz też

- [TreeView, kontrolka](treeview-control-windows-forms.md)
