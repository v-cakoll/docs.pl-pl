---
title: Wyświetlanie ikon błędów dla walidacji formularza za pomocą składnika ErrorProvider
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
ms.openlocfilehash: a1e346e332db489351f59c9a0c03ae731baf3dc3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745906"
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a>Porady: wyświetlanie ikon błędów dotyczących weryfikacji formularza za pomocą składnika ErrorProvider formularzy systemu Windows
Możesz użyć składnika <xref:System.Windows.Forms.ErrorProvider> Windows Forms, aby wyświetlić ikonę błędu, gdy użytkownik wprowadzi nieprawidłowe dane. Musisz mieć co najmniej dwie kontrolki na formularzu, aby można było przełączać się między nimi i w ten sposób wywoływać kod weryfikacyjny.  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a>Aby wyświetlić ikonę błędu, gdy wartość kontrolki jest nieprawidłowa  
  
1. Dodaj dwie kontrolki — na przykład pola tekstowe — do formularza systemu Windows.  
  
2. Dodaj składnik <xref:System.Windows.Forms.ErrorProvider> do formularza.  
  
3. Wybierz pierwszą kontrolkę i Dodaj kod do jej obsługi zdarzeń <xref:System.Windows.Forms.Control.Validating>. Aby ten kod działał prawidłowo, procedura musi być połączona ze zdarzeniem. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń w czasie wykonywania dla Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).  
  
     Poniższy kod sprawdza poprawność danych wprowadzonych przez użytkownika; Jeśli dane są nieprawidłowe, wywoływana jest metoda <xref:System.Windows.Forms.ErrorProvider.SetError%2A>. Pierwszy argument metody <xref:System.Windows.Forms.ErrorProvider.SetError%2A> określa, który formant ma wyświetlać ikonę obok. Drugi argument jest tekstem błędu do wyświetlenia.  
  
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
  
     (Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. Uruchom projekt. Nieprawidłowy typ (w tym przykładzie dane nieliczbowe) do pierwszej kontrolki, a następnie tabulator do drugiego. Gdy zostanie wyświetlona ikona błędu, wskaż ją wskaźnikiem myszy, aby zobaczyć tekst błędu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [ErrorProvider, składnik — omówienie](errorprovider-component-overview-windows-forms.md)
- [Instrukcje: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy Windows Forms](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
