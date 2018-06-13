---
title: 'Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows'
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
ms.openlocfilehash: ced563eb063bbcc429cdf1447a0158459e5d5c97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530741"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="24a51-102">Porady: kontrolowanie punktu wstawiania w formancie TextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="24a51-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="24a51-103">Gdy program Windows Forms <xref:System.Windows.Forms.TextBox> formant najpierw uzyskuje fokus, wstawiania domyślną w polu tekstowym znajduje się na lewo od istniejącego tekstu.</span><span class="sxs-lookup"><span data-stu-id="24a51-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="24a51-104">Użytkownik może przenieść punkt wstawiania z klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="24a51-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="24a51-105">Jeśli pole tekstowe utraci i ponownie otrzymuje fokus, punkt wstawiania będzie wszędzie tam, gdzie użytkownika ostatniego umieszczenia go.</span><span class="sxs-lookup"><span data-stu-id="24a51-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="24a51-106">W niektórych przypadkach to zachowanie może być niejasna dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="24a51-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="24a51-107">W edytorze tekstu aplikacji, użytkownik może spodziewać się nowe znaki są wyświetlane po istniejącego tekstu.</span><span class="sxs-lookup"><span data-stu-id="24a51-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="24a51-108">W aplikacji zapisu danych użytkownik może spodziewać się nowych znaków, aby zastąpić istniejący wpis.</span><span class="sxs-lookup"><span data-stu-id="24a51-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="24a51-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> i <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości umożliwia modyfikowanie zachowania do własnych potrzeb.</span><span class="sxs-lookup"><span data-stu-id="24a51-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="24a51-110">Aby kontrolować punktu wstawiania w formancie TextBox</span><span class="sxs-lookup"><span data-stu-id="24a51-110">To control the insertion point in a TextBox control</span></span>  
  
1.  <span data-ttu-id="24a51-111">Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> właściwości odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="24a51-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="24a51-112">Zero umieszcza punkt wstawiania natychmiast po lewej stronie pierwszego znaku.</span><span class="sxs-lookup"><span data-stu-id="24a51-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2.  <span data-ttu-id="24a51-113">(Opcjonalnie) Ustaw <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> właściwości długość tekstu, aby wybrać.</span><span class="sxs-lookup"><span data-stu-id="24a51-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="24a51-114">Poniższy kod zawsze zwraca punkt wstawiania na 0.</span><span class="sxs-lookup"><span data-stu-id="24a51-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="24a51-115">`TextBox1_Enter` Obsługi zdarzeń musi być powiązana do formantu, aby uzyskać więcej informacji, zobacz [tworzenie obsługi zdarzeń w formularzach systemu Windows](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="24a51-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span></span>  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="24a51-116">Zapewnienie widoczności domyślnie punkt wstawiania</span><span class="sxs-lookup"><span data-stu-id="24a51-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="24a51-117"><xref:System.Windows.Forms.TextBox> Jest widoczne domyślnie w nowego formularza tylko wtedy, gdy punkt wstawiania <xref:System.Windows.Forms.TextBox> formant jest pierwszy w kolejności tabulacji.</span><span class="sxs-lookup"><span data-stu-id="24a51-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="24a51-118">W przeciwnym razie punkt wstawiania jest wyświetlana tylko wtedy, gdy przekażesz <xref:System.Windows.Forms.TextBox> fokus klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="24a51-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="24a51-119">Aby punkt wstawiania pole tekstowe widoczne domyślnie na nowy formularz</span><span class="sxs-lookup"><span data-stu-id="24a51-119">To make the text box insertion point visible by default on a new form</span></span>  
  
-   <span data-ttu-id="24a51-120">Ustaw <xref:System.Windows.Forms.TextBox> formantu <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości `0`.</span><span class="sxs-lookup"><span data-stu-id="24a51-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a51-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="24a51-121">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="24a51-122">TextBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="24a51-122">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="24a51-123">Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24a51-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="24a51-124">Instrukcje: tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="24a51-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="24a51-125">Instrukcje: umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="24a51-125">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="24a51-126">Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24a51-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="24a51-127">Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24a51-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="24a51-128">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="24a51-128">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
