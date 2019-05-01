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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972292"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Instrukcje: ustalenie, kiedy zmieniono atrybuty formatowania w kontrolce RichTextBox formularzy systemu Windows
Typowym zastosowaniem formularzy Windows Forms <xref:System.Windows.Forms.RichTextBox> kontroli jest formatowanie tekstu za pomocą atrybutów, takich jak opcje czcionki lub style. Twoja aplikacja może potrzebować śledzić wszystkie zmiany wprowadzone w tekst na potrzeby wyświetlania paska narzędzi, tak jak w wielu aplikacjach edytora tekstów.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Aby odpowiadanie na zmiany w formatowaniu atrybutów  
  
1. Pisanie kodu w <xref:System.Windows.Forms.RichTextBox.SelectionChanged> programu obsługi zdarzeń, aby wykonać odpowiednią akcję, zależnie od wartości atrybutu. Poniższy przykład umożliwia zmianę wyglądu przycisku paska narzędzi w zależności od wartości <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> właściwości. Przycisk paska narzędzi będą aktualizowane po przeniesieniu punktu wstawiania w formancie.  
  
     W poniższym przykładzie przyjęto założenie, formularz z <xref:System.Windows.Forms.RichTextBox> kontroli i <xref:System.Windows.Forms.ToolBar> kontrolki, która zawiera przycisk paska narzędzi. Aby uzyskać więcej informacji na temat pasków narzędzi i przyciski paska narzędzi, zobacz [jak: Dodawanie przycisków do formantu ToolBar](how-to-add-buttons-to-a-toolbar-control.md).  
  
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
