---
title: TextBox — Informacje o formancie [Formularze systemu Windows]
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: ed4a40c172e527c6210bc31ab2575ebc08ead1bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671242"
---
# <a name="textbox-control-overview-windows-forms"></a><span data-ttu-id="99ed0-102">TextBox — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="99ed0-102">TextBox Control Overview (Windows Forms)</span></span>
<span data-ttu-id="99ed0-103">Windows Forms, pola tekstowe są używane do pobrać dane wejściowe od użytkownika lub do wyświetlania tekstu.</span><span class="sxs-lookup"><span data-stu-id="99ed0-103">Windows Forms text boxes are used to get input from the user or to display text.</span></span> <span data-ttu-id="99ed0-104"><xref:System.Windows.Forms.TextBox> Kontroli jest zazwyczaj używana do edycji tekstu, mimo że można również on tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="99ed0-104">The <xref:System.Windows.Forms.TextBox> control is generally used for editable text, although it can also be made read-only.</span></span> <span data-ttu-id="99ed0-105">Pola tekstowe można wyświetlić wiele wierszy, zawijanie tekstu do rozmiaru formantu i dodać podstawowe formatowanie.</span><span class="sxs-lookup"><span data-stu-id="99ed0-105">Text boxes can display multiple lines, wrap text to the size of the control, and add basic formatting.</span></span> <span data-ttu-id="99ed0-106"><xref:System.Windows.Forms.TextBox> Control oferuje jeden format stylu tekstu wyświetlane lub wprowadzone w formancie.</span><span class="sxs-lookup"><span data-stu-id="99ed0-106">The <xref:System.Windows.Forms.TextBox> control provides a single format style for text displayed or entered into the control.</span></span> <span data-ttu-id="99ed0-107">Aby wyświetlić wiele typów tekstu sformatowanego, użyj <xref:System.Windows.Forms.RichTextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="99ed0-107">To display multiple types of formatted text, use the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="99ed0-108">Aby uzyskać więcej informacji, zobacz [informacje o formancie RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="99ed0-108">For more information, see [RichTextBox Control Overview](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).</span></span>  
  
## <a name="working-with-the-textbox-control"></a><span data-ttu-id="99ed0-109">Praca z kontrolki TextBox</span><span class="sxs-lookup"><span data-stu-id="99ed0-109">Working with the TextBox Control</span></span>  
 <span data-ttu-id="99ed0-110">Tekst wyświetlany przez kontrolkę znajduje się w <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="99ed0-110">The text displayed by the control is contained in the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span> <span data-ttu-id="99ed0-111">Domyślnie można wprowadzić do 2048 znaków w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="99ed0-111">By default, you can enter up to 2048 characters in a text box.</span></span> <span data-ttu-id="99ed0-112">Jeśli ustawisz <xref:System.Windows.Forms.TextBox.Multiline%2A> właściwości `true`, możesz wprowadzić maksymalnie 32 KB tekstu.</span><span class="sxs-lookup"><span data-stu-id="99ed0-112">If you set the <xref:System.Windows.Forms.TextBox.Multiline%2A> property to `true`, you can enter up to 32 KB of text.</span></span> <span data-ttu-id="99ed0-113"><xref:System.Windows.Forms.TextBox.Text%2A> Właściwość można ustawić w czasie projektowania w oknie właściwości w czasie wykonywania w kodzie lub w danych wejściowych użytkownika w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="99ed0-113">The <xref:System.Windows.Forms.TextBox.Text%2A> property can be set at design time with the Properties Window, at run time in code, or by user input at run time.</span></span> <span data-ttu-id="99ed0-114">W czasie wykonywania można pobrać bieżącą zawartość pola tekstowego, czytając <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="99ed0-114">The current contents of a text box can be retrieved at run time by reading the <xref:System.Windows.Forms.TextBox.Text%2A> property.</span></span>  
  
 <span data-ttu-id="99ed0-115">Poniższy przykład kodu ustawia tekst w kontrolce, w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="99ed0-115">The following code example sets text in the control at run time.</span></span> <span data-ttu-id="99ed0-116">`InitializeMyControl` Procedury nie zostanie wykonany automatycznie; musi zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="99ed0-116">The `InitializeMyControl` procedure will not execute automatically; it must be called.</span></span>  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a><span data-ttu-id="99ed0-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="99ed0-117">See also</span></span>
- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="99ed0-118">Instrukcje: Kontrolowanie punktu wstawiania w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="99ed0-118">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="99ed0-119">Instrukcje: Tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="99ed0-119">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="99ed0-120">Instrukcje: Tworzenie pola tekstowego tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="99ed0-120">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="99ed0-121">Instrukcje: Umieszczanie cudzysłowu w ciągu</span><span class="sxs-lookup"><span data-stu-id="99ed0-121">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="99ed0-122">Instrukcje: Zaznaczanie tekstu w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="99ed0-122">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="99ed0-123">Instrukcje: Wyświetlanie wielu wierszy w formancie TextBox formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="99ed0-123">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="99ed0-124">TextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="99ed0-124">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
