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
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="fd3a9-102">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fd3a9-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="fd3a9-103">Zaznacz tekst programowo w formularzach Windows Forms <xref:System.Windows.Forms.TextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="fd3a9-104">Na przykład jeśli utworzysz funkcję, która umożliwia wyszukiwanie tekstu dla określonego ciągu, można wybrać tekst, który wizualnie alert czytnik pozycji znaleziony ciąg.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="fd3a9-105">Programowe Zaznaczanie tekstu</span><span class="sxs-lookup"><span data-stu-id="fd3a9-105">To select text programmatically</span></span>  
  
1. <span data-ttu-id="fd3a9-106">Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwości tekstu, aby wybrać na początek.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="fd3a9-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Właściwość jest liczbą, która wskazuje punkt wstawiania w ciągu tekstowym, używając 0 jest pozycja skrajnie po lewej.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="fd3a9-108">Jeśli <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwość jest ustawiona na wartość równa lub większa niż liczba znaków w polu tekstowym, punkt wstawiania jest umieszczany za ostatnim znakiem.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2. <span data-ttu-id="fd3a9-109">Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości do długości tekstu, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="fd3a9-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Właściwość ma wartość liczbowa, która ustawia szerokość punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="fd3a9-111">Ustawienie <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na liczbę większą niż 0 powoduje, że tę liczbę znaków, które mają zostać zaznaczone, począwszy od bieżącego punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3. <span data-ttu-id="fd3a9-112">(Opcjonalnie) Dostęp do zaznaczonego tekstu za pomocą <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="fd3a9-113">Kod poniżej wybiera zawartość tekstu pola, gdy kontrolka <xref:System.Windows.Forms.Control.Enter> wystąpi zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="fd3a9-114">W tym przykładzie sprawdza, czy pole tekstowe ma wartość <xref:System.Windows.Forms.TextBox.Text%2A> właściwość, która jest `null` ani być pustym ciągiem.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="fd3a9-115">Gdy pole tekstowe uzyskuje fokus, jest zaznaczony tekst w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="fd3a9-116">`TextBox1_Enter` Programu obsługi zdarzeń musi być powiązana z formantem; Aby uzyskać więcej informacji, zobacz [jak: Tworzenie procedur obsługi zdarzeń w czasie wykonywania dla formularzy Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="fd3a9-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="fd3a9-117">Aby przetestować w tym przykładzie, naciśnij klawisz Tab, aż pole ma fokus.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="fd3a9-118">Tekst nie jest zaznaczona, po kliknięciu w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="fd3a9-118">If you click in the text box, the text is unselected.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd3a9-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fd3a9-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="fd3a9-120">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="fd3a9-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="fd3a9-121">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fd3a9-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="fd3a9-122">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fd3a9-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="fd3a9-123">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="fd3a9-123">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="fd3a9-124">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="fd3a9-124">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="fd3a9-125">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fd3a9-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="fd3a9-126">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="fd3a9-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
