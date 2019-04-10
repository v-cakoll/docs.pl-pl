---
title: 'Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy systemu Windows'
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
ms.openlocfilehash: 3bb1245cd47084935d632ff345a32058db6074e1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321718"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy systemu Windows
Zaznacz tekst programowo w formularzach Windows Forms <xref:System.Windows.Forms.TextBox> kontroli. Na przykład jeśli utworzysz funkcję, która umożliwia wyszukiwanie tekstu dla określonego ciągu, można wybrać tekst, który wizualnie alert czytnik pozycji znaleziony ciąg.  
  
### <a name="to-select-text-programmatically"></a>Programowe Zaznaczanie tekstu  
  
1. Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwości tekstu, aby wybrać na początek.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Właściwość jest liczbą, która wskazuje punkt wstawiania w ciągu tekstowym, używając 0 jest pozycja skrajnie po lewej. Jeśli <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwość jest ustawiona na wartość równa lub większa niż liczba znaków w polu tekstowym, punkt wstawiania jest umieszczany za ostatnim znakiem.  
  
2. Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości do długości tekstu, aby wybrać.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Właściwość ma wartość liczbowa, która ustawia szerokość punktu wstawiania. Ustawienie <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na liczbę większą niż 0 powoduje, że tę liczbę znaków, które mają zostać zaznaczone, począwszy od bieżącego punktu wstawiania.  
  
3. (Opcjonalnie) Dostęp do zaznaczonego tekstu za pomocą <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> właściwości.  
  
     Kod poniżej wybiera zawartość tekstu pola, gdy kontrolka <xref:System.Windows.Forms.Control.Enter> wystąpi zdarzenie. W tym przykładzie sprawdza, czy pole tekstowe ma wartość <xref:System.Windows.Forms.TextBox.Text%2A> właściwość, która jest `null` ani być pustym ciągiem. Gdy pole tekstowe uzyskuje fokus, jest zaznaczony tekst w polu tekstowym. `TextBox1_Enter` Programu obsługi zdarzeń musi być powiązana z formantem; Aby uzyskać więcej informacji, zobacz [jak: Tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Aby przetestować w tym przykładzie, naciśnij klawisz Tab, aż pole ma fokus. Tekst nie jest zaznaczona, po kliknięciu w polu tekstowym.  
  
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
- [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy systemu Windows](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy systemu Windows](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Instrukcje: tworzenie pola tekstowego tylko do odczytu](how-to-create-a-read-only-text-box-windows-forms.md)
- [Instrukcje: umieszczanie cudzysłowu w ciągu](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy systemu Windows](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, kontrolka](textbox-control-windows-forms.md)
