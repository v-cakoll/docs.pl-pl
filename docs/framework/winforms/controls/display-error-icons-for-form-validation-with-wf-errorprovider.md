---
title: 'Porady: wyświetlanie ikon błędów dotyczących walidacji formularza za pomocą składnika ErrorProvider formularzy systemu Windows'
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
ms.openlocfilehash: 237a61cc21a18805fa502c9870d8ea472ac54d71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527303"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Porady: wyświetlanie ikon błędów dotyczących walidacji formularza za pomocą składnika ErrorProvider formularzy systemu Windows
Formularze systemu Windows można użyć <xref:System.Windows.Forms.ErrorProvider> składników, które mają być wyświetlane ikony błędu, gdy użytkownik wprowadzi nieprawidłowe dane. Musi mieć co najmniej dwóch kontrolek w formularzu celu karcie między nimi i tym samym wywołanie kodu walidacji.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Aby wyświetlić ikony błędu, gdy wartość formantu jest nieprawidłowy  
  
1.  Dodaj formanty dwóch — na przykład pól tekstowych — na formularzu systemu Windows.  
  
2.  Dodaj <xref:System.Windows.Forms.ErrorProvider> składnika w formularzu.  
  
3.  Wybierz pierwszą kontrolkę i Dodaj kod, aby jego <xref:System.Windows.Forms.Control.Validating> obsługi zdarzeń. Aby ten kod, aby działać poprawnie procedura musi być podłączony do zdarzenia. Aby uzyskać więcej informacji, zobacz [porady: tworzenie obsługi zdarzeń w Uruchom czasu dla formularzy systemu Windows](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Poniższy kod sprawdza poprawność danych, które użytkownik wprowadził; Jeśli dane są nieprawidłowe, <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda jest wywoływana. Pierwszy argument funkcji <xref:System.Windows.Forms.ErrorProvider.SetError%2A> Metoda określa, które sterowania do wyświetlenia obok ikony. Drugi argument jest błąd tekst do wyświetlenia.  
  
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
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  Uruchom projekt. Wpisz nieprawidłowe (w tym przykładzie nieliczbową) dane na pierwszą kontrolkę, a następnie kartę do drugiego. Po wyświetleniu ikony błędu wskaż go z kursorem myszy, aby wyświetlić tekst błędu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [ErrorProvider, składnik — omówienie](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [Instrukcje: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy Windows Forms](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
