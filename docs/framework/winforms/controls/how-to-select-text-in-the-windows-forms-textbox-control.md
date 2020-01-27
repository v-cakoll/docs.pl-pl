---
title: Zaznaczanie tekstu w kontrolce TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8a32e40f14ddae6f8ddcaa6d62337329df6fde26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745315"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows
Możesz zaznaczyć tekst programowo w kontrolce <xref:System.Windows.Forms.TextBox> Windows Forms. Na przykład, jeśli utworzysz funkcję, która przeszukuje tekst dla określonego ciągu, możesz wybrać tekst, aby wizualnie ostrzec czytnik znalezionych pozycji w ciągu.  
  
### <a name="to-select-text-programmatically"></a>Aby programowo zaznaczyć tekst  
  
1. Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> na początek tekstu, który chcesz wybrać.  
  
     Właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> jest liczbą, która wskazuje punkt wstawiania w ciągu tekstu, z 0 to pozycja z lewej strony. Jeśli właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> jest ustawiona na wartość równą lub większą od liczby znaków w polu tekstowym, punkt wstawiania zostanie umieszczony po ostatnim znaku.  
  
2. Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na długość tekstu, który chcesz wybrać.  
  
     Właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> jest wartością liczbową, która ustawia szerokość punktu wstawiania. Ustawienie <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na liczbę większą niż 0 powoduje, że liczba znaków do wybrania, rozpoczynając od bieżącego punktu wstawiania.  
  
3. Obowiązkowe Dostęp do zaznaczonego tekstu za pomocą właściwości <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>.  
  
     Poniższy kod wybiera zawartość pola tekstowego, gdy wystąpi zdarzenie <xref:System.Windows.Forms.Control.Enter> formantu. Ten przykład sprawdza, czy pole tekstowe ma wartość właściwości <xref:System.Windows.Forms.TextBox.Text%2A>, która nie jest `null` lub ciągiem pustym. Gdy pole tekstowe odbierze fokus, bieżący tekst w polu tekstowym jest zaznaczony. Procedura obsługi zdarzeń `TextBox1_Enter` musi być powiązana z kontrolką; Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń w czasie wykonywania dla Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Aby przetestować ten przykład, naciśnij klawisz Tab, dopóki pole tekstowe ma fokus. Po kliknięciu pola tekstowego tekst nie jest zaznaczony.  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- [TextBox, kontrolka — omówienie](textbox-control-overview-windows-forms.md)
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
