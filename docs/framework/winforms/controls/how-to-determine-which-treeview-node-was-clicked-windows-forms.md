---
title: 'Instrukcje: Określić, który węzeł TreeView został kliknięty (formularze Windows)'
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
ms.openlocfilehash: 1bc883cca2ef7fa7abd65362da054251513af76a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713920"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>Instrukcje: Określić, który węzeł TreeView został kliknięty (formularze Windows)
Podczas pracy z formularzami Windows <xref:System.Windows.Forms.TreeView> kontrolki, często wykonywanego zadania ma na celu określenie węzeł, który został kliknięty i odpowiednio reagować.  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>Aby ustalić, który węzeł TreeView został kliknięty  
  
1.  Użyj <xref:System.EventArgs> obiekt do zwrotu odwołanie do obiektu klikniętego węzła.  
  
2.  Określanie, który węzeł został kliknięty, sprawdzając <xref:System.Windows.Forms.TreeViewEventArgs> klasy, która zawiera dane związane ze zdarzeniem.  
  
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
    >  Alternatywnie, można użyć <xref:System.Windows.Forms.MouseEventArgs> z <xref:System.Windows.Forms.Control.MouseDown> lub <xref:System.Windows.Forms.Control.MouseUp> zdarzeń, aby uzyskać <xref:System.Drawing.Point.X%2A> i <xref:System.Drawing.Point.Y%2A> koordynować wartości <xref:System.Drawing.Point> gdzie wystąpiło kliknięcie. Następnie należy użyć <xref:System.Windows.Forms.TreeView> kontrolki <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metodę pozwala ustalić, który węzeł został kliknięty.  
  
## <a name="see-also"></a>Zobacz także
- [TreeView, kontrolka](treeview-control-windows-forms.md)
