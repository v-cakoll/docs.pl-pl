---
title: Określanie zmiany atrybutów formatowania w formancie RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: a190c3479b58464763e0eefdd32d14e88a1f05e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142267"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="4b7e5-102">Porady: ustalenie, kiedy zmieniono atrybuty formatowania w formancie RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4b7e5-102">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="4b7e5-103">Typowym zastosowaniem formantu Formularze <xref:System.Windows.Forms.RichTextBox> systemu Windows jest formatowanie tekstu z atrybutami, takimi jak opcje czcionek lub style akapitów.</span><span class="sxs-lookup"><span data-stu-id="4b7e5-103">A common use of the Windows Forms <xref:System.Windows.Forms.RichTextBox> control is formatting text with attributes such as font options or paragraph styles.</span></span> <span data-ttu-id="4b7e5-104">Aplikacja może być konieczne śledzenie wszelkich zmian w formatowaniu tekstu w celu wyświetlania paska narzędzi, jak w wielu aplikacjach edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="4b7e5-104">Your application may need to keep track of any changes in text formatting for the purpose of displaying a toolbar, as in many word-processing applications.</span></span>  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a><span data-ttu-id="4b7e5-105">Aby reagować na zmiany w atrybutach formatowania</span><span class="sxs-lookup"><span data-stu-id="4b7e5-105">To respond to changes in formatting attributes</span></span>  
  
1. <span data-ttu-id="4b7e5-106">Napisz kod <xref:System.Windows.Forms.RichTextBox.SelectionChanged> w programie obsługi zdarzeń, aby wykonać odpowiednią akcję w zależności od wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4b7e5-106">Write code in the <xref:System.Windows.Forms.RichTextBox.SelectionChanged> event handler to perform an appropriate action depending on the value of the attribute.</span></span> <span data-ttu-id="4b7e5-107">Poniższy przykład zmienia wygląd przycisku paska narzędzi <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> w zależności od wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="4b7e5-107">The following example changes the appearance of a toolbar button depending on the value of the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="4b7e5-108">Przycisk paska narzędzi zostanie zaktualizowany tylko wtedy, gdy punkt wstawiania zostanie przeniesiony do formantu.</span><span class="sxs-lookup"><span data-stu-id="4b7e5-108">The toolbar button will only be updated when the insertion point is moved in the control.</span></span>  
  
     <span data-ttu-id="4b7e5-109">Poniższy przykład zakłada formularz <xref:System.Windows.Forms.RichTextBox> z formantem i formantem, <xref:System.Windows.Forms.ToolBar> który zawiera przycisk paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="4b7e5-109">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control and a <xref:System.Windows.Forms.ToolBar> control that contains a toolbar button.</span></span> <span data-ttu-id="4b7e5-110">Aby uzyskać więcej informacji na temat pasków narzędzi i przycisków paska narzędzi, zobacz [Jak: Dodawanie przycisków do kontrolki paska narzędzi](how-to-add-buttons-to-a-toolbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="4b7e5-110">For more information about toolbars and toolbar buttons, see [How to: Add Buttons to a ToolBar Control](how-to-add-buttons-to-a-toolbar-control.md).</span></span>  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4b7e5-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4b7e5-111">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="4b7e5-112">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="4b7e5-112">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="4b7e5-113">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="4b7e5-113">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
