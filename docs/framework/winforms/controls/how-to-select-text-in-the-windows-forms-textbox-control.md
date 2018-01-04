---
title: 'Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows'
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
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 535ee9e7359782f24d48d895f094afbe47e1023b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="c8c6a-102">Porady: zaznaczanie tekstu w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c8c6a-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="c8c6a-103">Zaznacz tekst programowo w formularzach systemu Windows <xref:System.Windows.Forms.TextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="c8c6a-104">Na przykład Utwórz funkcję, która umożliwia wyszukiwanie tekstu dla określonego ciągu, można wybrać tekst, który wizualnie alertów czytnik pozycji znaleziony ciąg.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="c8c6a-105">Aby programowo zaznaczyć tekst</span><span class="sxs-lookup"><span data-stu-id="c8c6a-105">To select text programmatically</span></span>  
  
1.  <span data-ttu-id="c8c6a-106">Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwości początek tekstu, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="c8c6a-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Właściwość jest liczbą, która wskazuje punkt wstawiania w ciągu tekstowym, używając 0 jest pozycji lewej.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="c8c6a-108">Jeśli <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwość jest ustawiona na wartość równa lub większa niż liczba znaków w polu tekstowym, punkt wstawiania znajduje się po ostatnim znakiem.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2.  <span data-ttu-id="c8c6a-109">Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości długość tekstu, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="c8c6a-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Właściwość ma wartość liczbową Ustawia szerokość punkt wstawiania.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="c8c6a-111">Ustawienie <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> większą niż 0 powoduje, że ten numer znaków, które można wybrać, zaczynając od bieżącego punkt wstawiania.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3.  <span data-ttu-id="c8c6a-112">(Opcjonalnie) Dostęp do zaznaczonego tekstu za pośrednictwem <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="c8c6a-113">Kod poniżej wybiera zawartość tekstu dialogowe formantu <xref:System.Windows.Forms.Control.Enter> zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="c8c6a-114">W tym przykładzie sprawdza, czy pole ma wartość <xref:System.Windows.Forms.TextBox.Text%2A> właściwość, która nie jest `null` lub ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="c8c6a-115">Gdy pole tekstowe otrzymuje fokus, tekst w polu tekstowym jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="c8c6a-116">`TextBox1_Enter` Obsługi zdarzeń musi być powiązana do formantu, aby uzyskać więcej informacji, zobacz [porady: tworzenie obsługi zdarzeń w Uruchom czasu dla formularzy systemu Windows](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c8c6a-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="c8c6a-117">Aby przetestować w tym przykładzie, naciśnij klawisz Tab, dopóki pole ma fokus.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="c8c6a-118">Jeśli klikniesz przycisk w polu tekstowym tekst nie jest zaznaczona.</span><span class="sxs-lookup"><span data-stu-id="c8c6a-118">If you click in the text box, the text is unselected.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8c6a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8c6a-119">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="c8c6a-120">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c8c6a-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="c8c6a-121">Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8c6a-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c8c6a-122">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8c6a-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c8c6a-123">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="c8c6a-123">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="c8c6a-124">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="c8c6a-124">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="c8c6a-125">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c8c6a-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="c8c6a-126">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c8c6a-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
