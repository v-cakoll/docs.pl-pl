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
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="9abbc-102">Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9abbc-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="9abbc-103">Możesz zaznaczyć tekst programowo w kontrolce <xref:System.Windows.Forms.TextBox> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9abbc-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="9abbc-104">Na przykład, jeśli utworzysz funkcję, która przeszukuje tekst dla określonego ciągu, możesz wybrać tekst, aby wizualnie ostrzec czytnik znalezionych pozycji w ciągu.</span><span class="sxs-lookup"><span data-stu-id="9abbc-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="9abbc-105">Aby programowo zaznaczyć tekst</span><span class="sxs-lookup"><span data-stu-id="9abbc-105">To select text programmatically</span></span>  
  
1. <span data-ttu-id="9abbc-106">Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> na początek tekstu, który chcesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="9abbc-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="9abbc-107">Właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> jest liczbą, która wskazuje punkt wstawiania w ciągu tekstu, z 0 to pozycja z lewej strony.</span><span class="sxs-lookup"><span data-stu-id="9abbc-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="9abbc-108">Jeśli właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> jest ustawiona na wartość równą lub większą od liczby znaków w polu tekstowym, punkt wstawiania zostanie umieszczony po ostatnim znaku.</span><span class="sxs-lookup"><span data-stu-id="9abbc-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2. <span data-ttu-id="9abbc-109">Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na długość tekstu, który chcesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="9abbc-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="9abbc-110">Właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> jest wartością liczbową, która ustawia szerokość punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="9abbc-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="9abbc-111">Ustawienie <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na liczbę większą niż 0 powoduje, że liczba znaków do wybrania, rozpoczynając od bieżącego punktu wstawiania.</span><span class="sxs-lookup"><span data-stu-id="9abbc-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3. <span data-ttu-id="9abbc-112">Obowiązkowe Dostęp do zaznaczonego tekstu za pomocą właściwości <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A>.</span><span class="sxs-lookup"><span data-stu-id="9abbc-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="9abbc-113">Poniższy kod wybiera zawartość pola tekstowego, gdy wystąpi zdarzenie <xref:System.Windows.Forms.Control.Enter> formantu.</span><span class="sxs-lookup"><span data-stu-id="9abbc-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="9abbc-114">Ten przykład sprawdza, czy pole tekstowe ma wartość właściwości <xref:System.Windows.Forms.TextBox.Text%2A>, która nie jest `null` lub ciągiem pustym.</span><span class="sxs-lookup"><span data-stu-id="9abbc-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="9abbc-115">Gdy pole tekstowe odbierze fokus, bieżący tekst w polu tekstowym jest zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="9abbc-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="9abbc-116">Procedura obsługi zdarzeń `TextBox1_Enter` musi być powiązana z kontrolką; Aby uzyskać więcej informacji, zobacz [jak: Tworzenie obsługi zdarzeń w czasie wykonywania dla Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9abbc-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="9abbc-117">Aby przetestować ten przykład, naciśnij klawisz Tab, dopóki pole tekstowe ma fokus.</span><span class="sxs-lookup"><span data-stu-id="9abbc-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="9abbc-118">Po kliknięciu pola tekstowego tekst nie jest zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="9abbc-118">If you click in the text box, the text is unselected.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9abbc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9abbc-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="9abbc-120">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="9abbc-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="9abbc-121">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9abbc-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="9abbc-122">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9abbc-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="9abbc-123">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9abbc-123">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="9abbc-124">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="9abbc-124">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="9abbc-125">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9abbc-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="9abbc-126">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9abbc-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
