---
title: Ustalanie, kiedy atrybuty formatowania zmieniają się w kontrolce RichTextBox
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
ms.openlocfilehash: f9b2a1028f79059ec7d4d6bf3683100455bb5dea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746034"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Porady: ustalenie, kiedy zmieniono atrybuty formatowania w formancie RichTextBox formularzy systemu Windows
Typowym zastosowaniem kontrolki <xref:System.Windows.Forms.RichTextBox> Windows Forms jest formatowanie tekstu z atrybutami, takimi jak opcje czcionki lub Style akapitu. Aplikacja może wymagać śledzenia wszelkich zmian w formatowaniu tekstu na potrzeby wyświetlania paska narzędzi, jak w wielu aplikacjach do przetwarzania tekstu.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Aby odpowiedzieć na zmiany atrybutów formatowania  
  
1. Napisz kod w programie obsługi zdarzeń <xref:System.Windows.Forms.RichTextBox.SelectionChanged>, aby wykonać odpowiednią akcję w zależności od wartości atrybutu. Poniższy przykład zmienia wygląd przycisku paska narzędzi w zależności od wartości właściwości <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A>. Przycisk paska narzędzi zostanie zaktualizowany tylko wtedy, gdy punkt wstawiania zostanie przeniesiony do kontrolki.  
  
     W poniższym przykładzie przyjęto, że formularz z kontrolką <xref:System.Windows.Forms.RichTextBox> i formantem <xref:System.Windows.Forms.ToolBar> zawierającym przycisk paska narzędzi. Aby uzyskać więcej informacji o paskach narzędzi i przyciskach paska narzędzi, zobacz [jak: dodać przyciski do kontrolki paska narzędzi](how-to-add-buttons-to-a-toolbar-control.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
