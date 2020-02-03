---
title: Kontrolowanie punktu wstawiania w kontrolce TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742203"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="6ccaf-102">Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6ccaf-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="6ccaf-103">Gdy kontrolka <xref:System.Windows.Forms.TextBox> Windows Forms po raz pierwszy uzyska fokus, domyślne Wstawianie w polu tekstowym znajduje się po lewej stronie dowolnego istniejącego tekstu.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="6ccaf-104">Użytkownik może przenieść punkt wstawiania za pomocą klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="6ccaf-105">Jeśli pole tekstowe utraci, a następnie odzyska fokus, punkt wstawiania będzie wszędzie tam, gdzie został on ostatnio umieszczony.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="6ccaf-106">W niektórych przypadkach takie zachowanie może być rozuzgadniane z użytkownikiem.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="6ccaf-107">W aplikacji do przetwarzania tekstu użytkownik może oczekiwać, że nowe znaki pojawiają się po dowolnym istniejącym tekście.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="6ccaf-108">W aplikacji do wprowadzania danych użytkownik może oczekiwać, że nowe znaki zastąpią wszelkie istniejące wpisy.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="6ccaf-109">Właściwości <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> i <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> umożliwiają modyfikowanie zachowania odpowiednio do potrzeb.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="6ccaf-110">Aby kontrolować punkt wstawiania w kontrolce TextBox</span><span class="sxs-lookup"><span data-stu-id="6ccaf-110">To control the insertion point in a TextBox control</span></span>  
  
1. <span data-ttu-id="6ccaf-111">Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="6ccaf-112">Zero umieszcza punkt wstawiania bezpośrednio z lewej strony pierwszego znaku.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2. <span data-ttu-id="6ccaf-113">Obowiązkowe Ustaw właściwość <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> na długość tekstu, który chcesz wybrać.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="6ccaf-114">Poniższy kod zawsze zwraca punkt wstawiania do 0.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="6ccaf-115">Procedura obsługi zdarzeń `TextBox1_Enter` musi być powiązana z kontrolką; Aby uzyskać więcej informacji, zobacz [Tworzenie programów obsługi zdarzeń w Windows Forms](../creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6ccaf-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../creating-event-handlers-in-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="6ccaf-116">Uwidacznianie domyślnego punktu wstawiania</span><span class="sxs-lookup"><span data-stu-id="6ccaf-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="6ccaf-117"><xref:System.Windows.Forms.TextBox> punkt wstawiania jest domyślnie widoczny w nowym formularzu tylko wtedy, gdy formant <xref:System.Windows.Forms.TextBox> jest pierwszy w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="6ccaf-118">W przeciwnym razie punkt wstawiania pojawia się tylko wtedy, gdy podajesz <xref:System.Windows.Forms.TextBox> fokus przy użyciu klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="6ccaf-119">Aby punkt wstawiania pola tekstowego był widoczny domyślnie w nowym formularzu</span><span class="sxs-lookup"><span data-stu-id="6ccaf-119">To make the text box insertion point visible by default on a new form</span></span>  
  
- <span data-ttu-id="6ccaf-120">Ustaw właściwość <xref:System.Windows.Forms.Control.TabIndex%2A> kontrolki <xref:System.Windows.Forms.TextBox> na `0`.</span><span class="sxs-lookup"><span data-stu-id="6ccaf-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ccaf-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ccaf-121">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="6ccaf-122">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6ccaf-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="6ccaf-123">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ccaf-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="6ccaf-124">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="6ccaf-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="6ccaf-125">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="6ccaf-125">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="6ccaf-126">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ccaf-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="6ccaf-127">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6ccaf-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="6ccaf-128">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6ccaf-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
