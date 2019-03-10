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
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a><span data-ttu-id="a6aaf-102">Instrukcje: Określić, który węzeł TreeView został kliknięty (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="a6aaf-102">How to: Determine Which TreeView Node Was Clicked (Windows Forms)</span></span>
<span data-ttu-id="a6aaf-103">Podczas pracy z formularzami Windows <xref:System.Windows.Forms.TreeView> kontrolki, często wykonywanego zadania ma na celu określenie węzeł, który został kliknięty i odpowiednio reagować.</span><span class="sxs-lookup"><span data-stu-id="a6aaf-103">When working with the Windows Forms <xref:System.Windows.Forms.TreeView> control, a common task is to determine which node was clicked, and respond appropriately.</span></span>  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a><span data-ttu-id="a6aaf-104">Aby ustalić, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="a6aaf-104">To determine which TreeView node was clicked</span></span>  
  
1.  <span data-ttu-id="a6aaf-105">Użyj <xref:System.EventArgs> obiekt do zwrotu odwołanie do obiektu klikniętego węzła.</span><span class="sxs-lookup"><span data-stu-id="a6aaf-105">Use the <xref:System.EventArgs> object to return a reference to the clicked node object.</span></span>  
  
2.  <span data-ttu-id="a6aaf-106">Określanie, który węzeł został kliknięty, sprawdzając <xref:System.Windows.Forms.TreeViewEventArgs> klasy, która zawiera dane związane ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="a6aaf-106">Determine which node was clicked by checking the <xref:System.Windows.Forms.TreeViewEventArgs> class, which contains data related to the event.</span></span>  
  
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
    >  <span data-ttu-id="a6aaf-107">Alternatywnie, można użyć <xref:System.Windows.Forms.MouseEventArgs> z <xref:System.Windows.Forms.Control.MouseDown> lub <xref:System.Windows.Forms.Control.MouseUp> zdarzeń, aby uzyskać <xref:System.Drawing.Point.X%2A> i <xref:System.Drawing.Point.Y%2A> koordynować wartości <xref:System.Drawing.Point> gdzie wystąpiło kliknięcie.</span><span class="sxs-lookup"><span data-stu-id="a6aaf-107">As an alternative, you can use the <xref:System.Windows.Forms.MouseEventArgs> of the <xref:System.Windows.Forms.Control.MouseDown> or <xref:System.Windows.Forms.Control.MouseUp> event to get the <xref:System.Drawing.Point.X%2A> and <xref:System.Drawing.Point.Y%2A> coordinate values of the <xref:System.Drawing.Point> where the click occurred.</span></span> <span data-ttu-id="a6aaf-108">Następnie należy użyć <xref:System.Windows.Forms.TreeView> kontrolki <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> metodę pozwala ustalić, który węzeł został kliknięty.</span><span class="sxs-lookup"><span data-stu-id="a6aaf-108">Then, use the <xref:System.Windows.Forms.TreeView> control's <xref:System.Windows.Forms.TreeView.GetNodeAt%2A> method to determine which node was clicked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6aaf-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6aaf-109">See also</span></span>
- [<span data-ttu-id="a6aaf-110">TreeView, kontrolka</span><span class="sxs-lookup"><span data-stu-id="a6aaf-110">TreeView Control</span></span>](treeview-control-windows-forms.md)
