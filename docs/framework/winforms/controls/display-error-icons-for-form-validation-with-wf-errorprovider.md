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
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="069e4-102">Porady: wyświetlanie ikon błędów dotyczących weryfikacji formularza za pomocą składnika ErrorProvider formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="069e4-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="069e4-103">Możesz użyć składnika <xref:System.Windows.Forms.ErrorProvider> Windows Forms, aby wyświetlić ikonę błędu, gdy użytkownik wprowadzi nieprawidłowe dane.</span><span class="sxs-lookup"><span data-stu-id="069e4-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="069e4-104">Musisz mieć co najmniej dwie kontrolki na formularzu, aby można było przełączać się między nimi i w ten sposób wywoływać kod weryfikacyjny.</span><span class="sxs-lookup"><span data-stu-id="069e4-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="069e4-105">Aby wyświetlić ikonę błędu, gdy wartość kontrolki jest nieprawidłowa</span><span class="sxs-lookup"><span data-stu-id="069e4-105">To display an error icon when a control's value is invalid</span></span>  
  
1. <span data-ttu-id="069e4-106">Dodaj dwie kontrolki — na przykład pola tekstowe — do formularza systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="069e4-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2. <span data-ttu-id="069e4-107">Dodaj składnik <xref:System.Windows.Forms.ErrorProvider> do formularza.</span><span class="sxs-lookup"><span data-stu-id="069e4-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3. <span data-ttu-id="069e4-108">Wybierz pierwszą kontrolkę i Dodaj kod do jej obsługi zdarzeń <xref:System.Windows.Forms.Control.Validating>.</span><span class="sxs-lookup"><span data-stu-id="069e4-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="069e4-109">Aby ten kod działał prawidłowo, procedura musi być połączona ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="069e4-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="069e4-110">Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń w czasie wykonywania dla Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="069e4-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="069e4-111">Poniższy kod sprawdza poprawność danych wprowadzonych przez użytkownika; Jeśli dane są nieprawidłowe, wywoływana jest metoda <xref:System.Windows.Forms.ErrorProvider.SetError%2A>.</span><span class="sxs-lookup"><span data-stu-id="069e4-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="069e4-112">Pierwszy argument metody <xref:System.Windows.Forms.ErrorProvider.SetError%2A> określa, który formant ma wyświetlać ikonę obok.</span><span class="sxs-lookup"><span data-stu-id="069e4-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="069e4-113">Drugi argument jest tekstem błędu do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="069e4-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="069e4-114">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="069e4-114">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4. <span data-ttu-id="069e4-115">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="069e4-115">Run the project.</span></span> <span data-ttu-id="069e4-116">Nieprawidłowy typ (w tym przykładzie dane nieliczbowe) do pierwszej kontrolki, a następnie tabulator do drugiego.</span><span class="sxs-lookup"><span data-stu-id="069e4-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="069e4-117">Gdy zostanie wyświetlona ikona błędu, wskaż ją wskaźnikiem myszy, aby zobaczyć tekst błędu.</span><span class="sxs-lookup"><span data-stu-id="069e4-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069e4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="069e4-118">See also</span></span>

- <xref:System.Windows.Forms.ErrorProvider.SetError%2A>
- [<span data-ttu-id="069e4-119">ErrorProvider, składnik — omówienie</span><span class="sxs-lookup"><span data-stu-id="069e4-119">ErrorProvider Component Overview</span></span>](errorprovider-component-overview-windows-forms.md)
- [<span data-ttu-id="069e4-120">Instrukcje: wyświetlanie błędów w elemencie DataSet za pomocą składnika ErrorProvider formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="069e4-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](view-errors-within-a-dataset-with-wf-errorprovider-component.md)
