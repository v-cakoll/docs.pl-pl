---
title: "Porady: wyświetlanie ikon błędów dotyczących walidacji formularza za pomocą składnika ErrorProvider formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 02638ab59c0ba1c0eb0f8090be118b3d5a9111f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-error-icons-for-form-validation-with-the-windows-forms-errorprovider-component"></a><span data-ttu-id="978ff-102">Porady: wyświetlanie ikon błędów dotyczących walidacji formularza za pomocą składnika ErrorProvider formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="978ff-102">How to: Display Error Icons for Form Validation with the Windows Forms ErrorProvider Component</span></span>
<span data-ttu-id="978ff-103">Formularze systemu Windows można użyć <xref:System.Windows.Forms.ErrorProvider> składników, które mają być wyświetlane ikony błędu, gdy użytkownik wprowadzi nieprawidłowe dane.</span><span class="sxs-lookup"><span data-stu-id="978ff-103">You can use a Windows Forms <xref:System.Windows.Forms.ErrorProvider> component to display an error icon when the user enters invalid data.</span></span> <span data-ttu-id="978ff-104">Musi mieć co najmniej dwóch kontrolek w formularzu celu karcie między nimi i tym samym wywołanie kodu walidacji.</span><span class="sxs-lookup"><span data-stu-id="978ff-104">You must have at least two controls on the form in order to tab between them and thereby invoke the validation code.</span></span>  
  
### <a name="to-display-an-error-icon-when-a-controls-value-is-invalid"></a><span data-ttu-id="978ff-105">Aby wyświetlić ikony błędu, gdy wartość formantu jest nieprawidłowy</span><span class="sxs-lookup"><span data-stu-id="978ff-105">To display an error icon when a control's value is invalid</span></span>  
  
1.  <span data-ttu-id="978ff-106">Dodaj formanty dwóch — na przykład pól tekstowych — na formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="978ff-106">Add two controls — for example, text boxes — to a Windows Form.</span></span>  
  
2.  <span data-ttu-id="978ff-107">Dodaj <xref:System.Windows.Forms.ErrorProvider> składnika w formularzu.</span><span class="sxs-lookup"><span data-stu-id="978ff-107">Add an <xref:System.Windows.Forms.ErrorProvider> component to the form.</span></span>  
  
3.  <span data-ttu-id="978ff-108">Wybierz pierwszą kontrolkę i Dodaj kod, aby jego <xref:System.Windows.Forms.Control.Validating> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="978ff-108">Select the first control and add code to its <xref:System.Windows.Forms.Control.Validating> event handler.</span></span> <span data-ttu-id="978ff-109">Aby ten kod, aby działać poprawnie procedura musi być podłączony do zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="978ff-109">In order for this code to run properly, the procedure must be connected to the event.</span></span> <span data-ttu-id="978ff-110">Aby uzyskać więcej informacji, zobacz [porady: tworzenie obsługi zdarzeń w Uruchom czasu dla formularzy systemu Windows](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="978ff-110">For more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="978ff-111">Poniższy kod sprawdza poprawność danych, które użytkownik wprowadził; Jeśli dane są nieprawidłowe, <xref:System.Windows.Forms.ErrorProvider.SetError%2A> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="978ff-111">The following code tests the validity of the data the user has entered; if the data is invalid, the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method is called.</span></span> <span data-ttu-id="978ff-112">Pierwszy argument funkcji <xref:System.Windows.Forms.ErrorProvider.SetError%2A> Metoda określa, które sterowania do wyświetlenia obok ikony.</span><span class="sxs-lookup"><span data-stu-id="978ff-112">The first argument of the <xref:System.Windows.Forms.ErrorProvider.SetError%2A> method specifies which control to display the icon next to.</span></span> <span data-ttu-id="978ff-113">Drugi argument jest błąd tekst do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="978ff-113">The second argument is the error text to display.</span></span>  
  
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
  
     <span data-ttu-id="978ff-114">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="978ff-114">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.textBox1.Validating += new  
    System.ComponentModel.CancelEventHandler(this.textBox1_Validating);  
    ```  
  
    ```cpp  
    this->textBox1->Validating += gcnew  
       System::ComponentModel::CancelEventHandler  
       (this, &Form1::textBox1_Validating);  
    ```  
  
4.  <span data-ttu-id="978ff-115">Uruchom projekt.</span><span class="sxs-lookup"><span data-stu-id="978ff-115">Run the project.</span></span> <span data-ttu-id="978ff-116">Wpisz nieprawidłowe (w tym przykładzie nieliczbową) dane na pierwszą kontrolkę, a następnie kartę do drugiego.</span><span class="sxs-lookup"><span data-stu-id="978ff-116">Type invalid (in this example, non-numeric) data into the first control, and then tab to the second.</span></span> <span data-ttu-id="978ff-117">Po wyświetleniu ikony błędu wskaż go z kursorem myszy, aby wyświetlić tekst błędu.</span><span class="sxs-lookup"><span data-stu-id="978ff-117">When the error icon is displayed, point at it with the mouse pointer to see the error text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978ff-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="978ff-118">See Also</span></span>  
 <xref:System.Windows.Forms.ErrorProvider.SetError%2A>  
 [<span data-ttu-id="978ff-119">Informacje o składniku ErrorProvider</span><span class="sxs-lookup"><span data-stu-id="978ff-119">ErrorProvider Component Overview</span></span>](../../../../docs/framework/winforms/controls/errorprovider-component-overview-windows-forms.md)  
 [<span data-ttu-id="978ff-120">Porady: wyświetlanie błędów w zestawie danych z systemu Windows składnika ErrorProvider formularzy</span><span class="sxs-lookup"><span data-stu-id="978ff-120">How to: View Errors Within a DataSet with the Windows Forms ErrorProvider Component</span></span>](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)
