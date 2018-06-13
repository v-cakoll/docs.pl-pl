---
title: 'Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows'
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
ms.openlocfilehash: 8fd1cfb0764d16b86cd639d8266d1cceff874932
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536697"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a>Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows
Zaznacz tekst programowo w formularzach systemu Windows <xref:System.Windows.Forms.TextBox> formantu. Na przykład Utwórz funkcję, która umożliwia wyszukiwanie tekstu dla określonego ciągu, można wybrać tekst, który wizualnie alertów czytnik pozycji znaleziony ciąg.  
  
### <a name="to-select-text-programmatically"></a>Aby programowo zaznaczyć tekst  
  
1.  Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwości początek tekstu, aby wybrać.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Właściwość jest liczbą, która wskazuje punkt wstawiania w ciągu tekstowym, używając 0 jest pozycji lewej. Jeśli <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwość jest ustawiona na wartość równa lub większa niż liczba znaków w polu tekstowym, punkt wstawiania znajduje się po ostatnim znakiem.  
  
2.  Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości długość tekstu, aby wybrać.  
  
     <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Właściwość ma wartość liczbową Ustawia szerokość punkt wstawiania. Ustawienie <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> większą niż 0 powoduje, że ten numer znaków, które można wybrać, zaczynając od bieżącego punkt wstawiania.  
  
3.  (Opcjonalnie) Dostęp do zaznaczonego tekstu za pośrednictwem <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> właściwości.  
  
     Kod poniżej wybiera zawartość tekstu dialogowe formantu <xref:System.Windows.Forms.Control.Enter> zdarzenie. W tym przykładzie sprawdza, czy pole ma wartość <xref:System.Windows.Forms.TextBox.Text%2A> właściwość, która nie jest `null` lub ciąg pusty. Gdy pole tekstowe otrzymuje fokus, tekst w polu tekstowym jest zaznaczone. `TextBox1_Enter` Obsługi zdarzeń musi być powiązana do formantu, aby uzyskać więcej informacji, zobacz [porady: tworzenie obsługi zdarzeń w Uruchom czasu dla formularzy systemu Windows](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Aby przetestować w tym przykładzie, naciśnij klawisz Tab, dopóki pole ma fokus. Jeśli klikniesz przycisk w polu tekstowym tekst nie jest zaznaczona.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextBox>  
 [TextBox, kontrolka — omówienie](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego tylko do odczytu](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Instrukcje: umieszczanie cudzysłowu w ciągu](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox, kontrolka](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
