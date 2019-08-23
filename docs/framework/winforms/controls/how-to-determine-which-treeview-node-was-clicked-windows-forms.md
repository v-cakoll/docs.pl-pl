---
title: 'Instrukcje: Określ, który węzeł TreeView został kliknięty (Windows Forms)'
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
ms.openlocfilehash: ab93158daf987e2f19516b8fb3abf80bfe79a12c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967343"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Instrukcje: Określ, który węzeł TreeView został kliknięty (Windows Forms)
Podczas pracy z kontrolką <xref:System.Windows.Forms.TreeView> Windows Forms, typowe zadanie polega na określeniu, który węzeł został kliknięty, i odpowiadać odpowiednio.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Aby określić, który węzeł TreeView został kliknięty  
  
1. Użyj obiektu <xref:System.EventArgs> , aby zwrócić odwołanie do klikniętego obiektu węzła.  
  
2. Ustal, który węzeł został kliknięty, <xref:System.Windows.Forms.TreeViewEventArgs> sprawdzając klasę, która zawiera dane związane ze zdarzeniem.  
  
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
    > Alternatywnie, <xref:System.Windows.Forms.MouseEventArgs> możesz użyć <xref:System.Windows.Forms.Control.MouseDown> zdarzenia <xref:System.Windows.Forms.Control.MouseUp> <xref:System.Drawing.Point.Y%2A> lub,<xref:System.Drawing.Point> Aby uzyskać wartości iwspółrzędnewmiejscu,wktórymnastąpiłokliknięcie.<xref:System.Drawing.Point.X%2A> Następnie użyj <xref:System.Windows.Forms.TreeView> <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metody kontrolki, aby określić, który węzeł został kliknięty.  
  
## <a name="see-also"></a>Zobacz także

- [TreeView, kontrolka](treeview-control-windows-forms.md)
