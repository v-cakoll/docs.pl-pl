---
title: 'Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows'
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
ms.openlocfilehash: cb3e7e7a44391ec7ee34ad0659f4185bd2304d26
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714895"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="55d14-102">Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="55d14-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="55d14-103">Gdy formularze Windows <xref:System.Windows.Forms.TextBox> formant najpierw otrzymuje fokus, wstawiania domyślną w polu tekstowym znajduje się po lewej stronie wszelki istniejący tekst.</span><span class="sxs-lookup"><span data-stu-id="55d14-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="55d14-104">Użytkownik może przenieść punkt wstawiania, za pomocą klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="55d14-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="55d14-105">Jeśli pole tekstowe traci, a następnie ponownie otrzymuje fokus, kursor będzie wszędzie tam, gdzie użytkownik ostatniego umieszczenia go.</span><span class="sxs-lookup"><span data-stu-id="55d14-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="55d14-106">W niektórych przypadkach to zachowanie może być niejasna dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="55d14-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="55d14-107">W edytorze tekstu aplikacji, użytkownik może oczekiwać nowe znaki pojawi się po wszelki istniejący tekst.</span><span class="sxs-lookup"><span data-stu-id="55d14-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="55d14-108">W aplikacji zapisu danych użytkownik może się spodziewać nowe znaki zastąpienie dowolnego istniejącego wpisu.</span><span class="sxs-lookup"><span data-stu-id="55d14-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="55d14-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> i <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości umożliwia modyfikowanie zachowania do konkretnego celu.</span><span class="sxs-lookup"><span data-stu-id="55d14-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="55d14-110">Aby kontrolować punktu wstawiania w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="55d14-110">To control the insertion point in a TextBox control</span></span>  
  
1.  <span data-ttu-id="55d14-111">Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwość do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="55d14-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="55d14-112">Zero umieszcza punkt wstawiania natychmiast na lewo od pierwszego znaku.</span><span class="sxs-lookup"><span data-stu-id="55d14-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2.  <span data-ttu-id="55d14-113">(Opcjonalnie) Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości do długości tekstu, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="55d14-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="55d14-114">Poniższy kod zawsze zwraca punkt wstawiania do 0.</span><span class="sxs-lookup"><span data-stu-id="55d14-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="55d14-115">`TextBox1_Enter` Programu obsługi zdarzeń musi być powiązana z formantem; Aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach Windows Forms](../creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="55d14-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../creating-event-handlers-in-windows-forms.md).</span></span>  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="55d14-116">Uwidaczniania domyślnie punkt wstawiania</span><span class="sxs-lookup"><span data-stu-id="55d14-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="55d14-117"><xref:System.Windows.Forms.TextBox> Punkt wstawiania znajduje się domyślnie w nowy formularz tylko wtedy, gdy widoczny <xref:System.Windows.Forms.TextBox> formant jest pierwszy w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="55d14-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="55d14-118">W przeciwnym razie punkt wstawiania jest wyświetlana tylko wtedy, gdy udzielisz <xref:System.Windows.Forms.TextBox> fokus klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="55d14-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="55d14-119">Aby uwidocznić punkt wstawiania pole tekstowe domyślnie na nowego formularza</span><span class="sxs-lookup"><span data-stu-id="55d14-119">To make the text box insertion point visible by default on a new form</span></span>  
  
-   <span data-ttu-id="55d14-120">Ustaw <xref:System.Windows.Forms.TextBox> kontrolki <xref:System.Windows.Forms.Control.TabIndex%2A> właściwość `0`.</span><span class="sxs-lookup"><span data-stu-id="55d14-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55d14-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55d14-121">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="55d14-122">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="55d14-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="55d14-123">Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="55d14-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="55d14-124">Instrukcje: Tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="55d14-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="55d14-125">Instrukcje: Umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="55d14-125">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="55d14-126">Instrukcje: Zaznaczanie tekstu w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="55d14-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="55d14-127">Instrukcje: Wyświetlanie wielu wierszy w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="55d14-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="55d14-128">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="55d14-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
