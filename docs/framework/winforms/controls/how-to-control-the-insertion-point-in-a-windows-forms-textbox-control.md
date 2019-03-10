---
title: 'Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: cb3e7e7a44391ec7ee34ad0659f4185bd2304d26
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714895"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a>Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows
Gdy formularze Windows <xref:System.Windows.Forms.TextBox> formant najpierw otrzymuje fokus, wstawiania domyślną w polu tekstowym znajduje się po lewej stronie wszelki istniejący tekst. Użytkownik może przenieść punkt wstawiania, za pomocą klawiatury lub myszy. Jeśli pole tekstowe traci, a następnie ponownie otrzymuje fokus, kursor będzie wszędzie tam, gdzie użytkownik ostatniego umieszczenia go.  
  
 W niektórych przypadkach to zachowanie może być niejasna dla użytkownika. W edytorze tekstu aplikacji, użytkownik może oczekiwać nowe znaki pojawi się po wszelki istniejący tekst. W aplikacji zapisu danych użytkownik może się spodziewać nowe znaki zastąpienie dowolnego istniejącego wpisu. <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> i <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości umożliwia modyfikowanie zachowania do konkretnego celu.  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a>Aby kontrolować punktu wstawiania w formancie TextBox  
  
1.  Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwość do odpowiedniej wartości. Zero umieszcza punkt wstawiania natychmiast na lewo od pierwszego znaku.  
  
2.  (Opcjonalnie) Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości do długości tekstu, aby wybrać.  
  
     Poniższy kod zawsze zwraca punkt wstawiania do 0. `TextBox1_Enter` Programu obsługi zdarzeń musi być powiązana z formantem; Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach Windows Forms](../creating-event-handlers-in-windows-forms.md).  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a>Uwidaczniania domyślnie punkt wstawiania  
 <xref:System.Windows.Forms.TextBox> Punkt wstawiania znajduje się domyślnie w nowy formularz tylko wtedy, gdy widoczny <xref:System.Windows.Forms.TextBox> formant jest pierwszy w kolejności tabulacji. W przeciwnym razie punkt wstawiania jest wyświetlana tylko wtedy, gdy udzielisz <xref:System.Windows.Forms.TextBox> fokus klawiatury lub myszy.  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a>Aby uwidocznić punkt wstawiania pole tekstowe domyślnie na nowego formularza  
  
-   Ustaw <xref:System.Windows.Forms.TextBox> kontrolki <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość `0`.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: Tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: Umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: Zaznaczanie tekstu w formancie TextBox formularzy Windows](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Instrukcje: Wyświetlanie wielu wierszy w formancie TextBox formularzy Windows](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
