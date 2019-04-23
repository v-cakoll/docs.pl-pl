---
title: 'Instrukcje: ustalenie, kiedy zmieniono atrybuty formatowania w kontrolce RichTextBox formularzy systemu Windows'
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
ms.openlocfilehash: a90affde9de36f1c83d5b7c21b40580cdf53402e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59308461"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="38293-102">Instrukcje: ustalenie, kiedy zmieniono atrybuty formatowania w kontrolce RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="38293-102">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="38293-103">Typowym zastosowaniem formularzy Windows Forms <xref:System.Windows.Forms.RichTextBox> kontroli jest formatowanie tekstu za pomocą atrybutów, takich jak opcje czcionki lub style.</span><span class="sxs-lookup"><span data-stu-id="38293-103">A common use of the Windows Forms <xref:System.Windows.Forms.RichTextBox> control is formatting text with attributes such as font options or paragraph styles.</span></span> <span data-ttu-id="38293-104">Twoja aplikacja może potrzebować śledzić wszystkie zmiany wprowadzone w tekst na potrzeby wyświetlania paska narzędzi, tak jak w wielu aplikacjach edytora tekstów.</span><span class="sxs-lookup"><span data-stu-id="38293-104">Your application may need to keep track of any changes in text formatting for the purpose of displaying a toolbar, as in many word-processing applications.</span></span>  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a><span data-ttu-id="38293-105">Aby odpowiadanie na zmiany w formatowaniu atrybutów</span><span class="sxs-lookup"><span data-stu-id="38293-105">To respond to changes in formatting attributes</span></span>  
  
1. <span data-ttu-id="38293-106">Pisanie kodu w <xref:System.Windows.Forms.RichTextBox.SelectionChanged> programu obsługi zdarzeń, aby wykonać odpowiednią akcję, zależnie od wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="38293-106">Write code in the <xref:System.Windows.Forms.RichTextBox.SelectionChanged> event handler to perform an appropriate action depending on the value of the attribute.</span></span> <span data-ttu-id="38293-107">Poniższy przykład umożliwia zmianę wyglądu przycisku paska narzędzi w zależności od wartości <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="38293-107">The following example changes the appearance of a toolbar button depending on the value of the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="38293-108">Przycisk paska narzędzi będą aktualizowane po przeniesieniu punktu wstawiania w formancie.</span><span class="sxs-lookup"><span data-stu-id="38293-108">The toolbar button will only be updated when the insertion point is moved in the control.</span></span>  
  
     <span data-ttu-id="38293-109">W poniższym przykładzie przyjęto założenie, formularz z <xref:System.Windows.Forms.RichTextBox> kontroli i <xref:System.Windows.Forms.ToolBar> kontrolki, która zawiera przycisk paska narzędzi.</span><span class="sxs-lookup"><span data-stu-id="38293-109">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control and a <xref:System.Windows.Forms.ToolBar> control that contains a toolbar button.</span></span> <span data-ttu-id="38293-110">Aby uzyskać więcej informacji na temat pasków narzędzi i przyciski paska narzędzi, zobacz [jak: Dodawanie przycisków do formantu ToolBar](how-to-add-buttons-to-a-toolbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="38293-110">For more information about toolbars and toolbar buttons, see [How to: Add Buttons to a ToolBar Control](how-to-add-buttons-to-a-toolbar-control.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38293-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38293-111">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="38293-112">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="38293-112">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="38293-113">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="38293-113">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
