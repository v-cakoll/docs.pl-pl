---
title: 'Instrukcje: Wyświetlanie ikon błędów weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error icons
- ErrorProvider component [Windows Forms], displaying error icons
- error messages [Windows Forms], displaying icons
ms.assetid: 3b681a32-9db4-497b-a34b-34980eabee46
ms.openlocfilehash: fa230e326a91853d6b23d5901317a86f628f6c72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679113"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Instrukcje: Wyświetlanie ikon błędów weryfikacji formularza za pomocą składnika ErrorProvider formularzy Windows
Można używać formularzy Windows <xref:System.Windows.Forms.ErrorProvider> składnika, aby wyświetlić ikona błędu, gdy użytkownik wprowadzi nieprawidłowe dane. Musi mieć co najmniej dwa formanty w formularzu w celu karcie między nimi i tym samym wywoływać kod sprawdzania poprawności.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Aby wyświetlić ikona błędu, gdy wartość kontrolki jest nieprawidłowa.  
  
1.  Dodaj dwie kontrolki — na przykład, pola tekstowe — do formularza Windows.  
  
2.  Dodaj <xref:System.Windows.Forms.ErrorProvider> składnika do formularza.  
  
3.  Wybierz pierwszy formant i dodać kod do jego <xref:System.Windows.Forms.Control.Validating> programu obsługi zdarzeń. Aby ten kod działał prawidłowo procedury muszą być podłączone do zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Poniższy kod sprawdza poprawność danych, które użytkownik wprowadził; Jeśli dane są nieprawidłowe, <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda jest wywoływana. Pierwszy argument <xref:System.Windows.Forms.ErrorProvider.SetError%2A> Metoda określa, które kontrolują, aby wyświetlić ikonę obok pozycji. Drugi argument jest tekst błędu, aby wyświetlić.  
  
    ```vb  
    Private Sub TextBox1_Validating(ByVal Sender As Object, _  
       ByVal e As System.ComponentModel.CancelEventArgs) Handles _  
       TextBox1.Validating  
          If Not IsNumeric(TextBox1.Text) Then  
             ErrorProvider1.SetError(TextBox1, "Not a numeric value.")  
          Else  
             ' Clear the error.  
             ErrorProvider1.SetError(TextBox1, "")  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void textBox1_Validating (object sender,  
       System.ComponentModel.CancelEventArgs e)  
    {  
       try  
       {  
          int x = Int32.Parse(textBox1.Text);  
          errorProvider1.SetError(textBox1, "");  
       }  
       catch (Exception ex)  
       {  
          errorProvider1.SetError(textBox1, "Not an integer value.");  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void textBox1_Validating(System::Object ^  sender,  
          System::ComponentModel::CancelEventArgs ^  e)  
       {  
          try  
          {  
             int x = Int32::Parse(textBox1->Text);  
             errorProvider1->SetError(textBox1, "");  
          }  
          catch (System::Exception ^ ex)  
          {  
             errorProvider1->SetError(textBox1, "Not an integer value.");  
          }  
       }  
    ```  
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  Uruchom projekt. Wpisz nieprawidłowe (w tym przykładzie nieliczbową) dane na pierwszą kontrolkę, a następnie kartę do drugiego. Gdy jest wyświetlana ikona błędu, wskaż go za pomocą wskaźnika myszy, aby wyświetlić tekst błędu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [ErrorProvider, składnik — omówienie](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)
- [Instrukcje: Wyświetl błędy w zestawie danych za pomocą składnika ErrorProvider formularzy Windows](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
