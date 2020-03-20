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
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Porady: ustalenie, kiedy zmieniono atrybuty formatowania w formancie RichTextBox formularzy systemu Windows
Typowym zastosowaniem formantu Formularze <xref:System.Windows.Forms.RichTextBox> systemu Windows jest formatowanie tekstu z atrybutami, takimi jak opcje czcionek lub style akapitów. Aplikacja może być konieczne śledzenie wszelkich zmian w formatowaniu tekstu w celu wyświetlania paska narzędzi, jak w wielu aplikacjach edytora tekstu.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Aby reagować na zmiany w atrybutach formatowania  
  
1. Napisz kod <xref:System.Windows.Forms.RichTextBox.SelectionChanged> w programie obsługi zdarzeń, aby wykonać odpowiednią akcję w zależności od wartości atrybutu. Poniższy przykład zmienia wygląd przycisku paska narzędzi <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> w zależności od wartości właściwości. Przycisk paska narzędzi zostanie zaktualizowany tylko wtedy, gdy punkt wstawiania zostanie przeniesiony do formantu.  
  
     Poniższy przykład zakłada formularz <xref:System.Windows.Forms.RichTextBox> z formantem i formantem, <xref:System.Windows.Forms.ToolBar> który zawiera przycisk paska narzędzi. Aby uzyskać więcej informacji na temat pasków narzędzi i przycisków paska narzędzi, zobacz [Jak: Dodawanie przycisków do kontrolki paska narzędzi](how-to-add-buttons-to-a-toolbar-control.md).  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
