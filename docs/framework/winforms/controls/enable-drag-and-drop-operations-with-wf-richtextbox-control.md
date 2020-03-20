---
title: Włącz operacje przeciągania i upuszczania za pomocą kontrolki RichTextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 27e5c18598552c465ef17f5e58069bc10e401c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182353"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="83370-102">Porady: włączenie operacji przeciągania i upuszczania za pomocą formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83370-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="83370-103">Operacje przeciągania i upuszczania za pomocą formantu Windows Forms <xref:System.Windows.Forms.RichTextBox> są wykonywane przez obsługę <xref:System.Windows.Forms.RichTextBox.DragEnter> zdarzeń i. <xref:System.Windows.Forms.RichTextBox.DragDrop></span><span class="sxs-lookup"><span data-stu-id="83370-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="83370-104">W związku z tym operacje przeciągania <xref:System.Windows.Forms.RichTextBox> i upuszczania są niezwykle proste z formantem.</span><span class="sxs-lookup"><span data-stu-id="83370-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="83370-105">Aby włączyć operacje przeciągania w formancie RichTextBox</span><span class="sxs-lookup"><span data-stu-id="83370-105">To enable drag operations in a RichTextBox control</span></span>  
  
1. <span data-ttu-id="83370-106">Ustaw <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> właściwość <xref:System.Windows.Forms.RichTextBox> formantu na `true`.</span><span class="sxs-lookup"><span data-stu-id="83370-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2. <span data-ttu-id="83370-107">Napisz kod w programie <xref:System.Windows.Forms.RichTextBox.DragEnter> obsługi zdarzeń zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="83370-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="83370-108">Użyj `if` instrukcji, aby upewnić się, że przeciągane dane są akceptowalnym typem (w tym przypadku tekst).</span><span class="sxs-lookup"><span data-stu-id="83370-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="83370-109">Właściwość <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> można ustawić na dowolną <xref:System.Windows.Forms.DragDropEffects> wartość wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="83370-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     <span data-ttu-id="83370-110">(Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="83370-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3. <span data-ttu-id="83370-111">Napisz kod do <xref:System.Windows.Forms.RichTextBox.DragDrop> obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="83370-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="83370-112">Użyj <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metody, aby pobrać przeciągane dane.</span><span class="sxs-lookup"><span data-stu-id="83370-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="83370-113">W poniższym przykładzie kod <xref:System.Windows.Forms.RichTextBox.Text%2A> ustawia <xref:System.Windows.Forms.RichTextBox> właściwość formantu równą przeciąganym danym.</span><span class="sxs-lookup"><span data-stu-id="83370-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="83370-114">Jeśli w <xref:System.Windows.Forms.RichTextBox> formancie znajduje się już tekst, przeciągany tekst jest wstawiany w punkcie wstawiania.</span><span class="sxs-lookup"><span data-stu-id="83370-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragDrop  
       Dim i As Int16
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     <span data-ttu-id="83370-115">(Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="83370-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="83370-116">Aby przetestować funkcję przeciągania i upuszczania w aplikacji</span><span class="sxs-lookup"><span data-stu-id="83370-116">To test the drag-and-drop functionality in your application</span></span>  
  
1. <span data-ttu-id="83370-117">Zapisz i skompiluj aplikację.</span><span class="sxs-lookup"><span data-stu-id="83370-117">Save and build your application.</span></span> <span data-ttu-id="83370-118">Podczas pracy uruchom program WordPad.</span><span class="sxs-lookup"><span data-stu-id="83370-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="83370-119">WordPad to edytor tekstu zainstalowany przez system Windows, który umożliwia operacje przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="83370-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="83370-120">Jest on dostępny po kliknięciu przycisku **Start,** **wybraniu przycisku Uruchom,** wpisując `WordPad` w polu tekstowym okna dialogowego **Uruchom,** a następnie klikając **przycisk OK**.</span><span class="sxs-lookup"><span data-stu-id="83370-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2. <span data-ttu-id="83370-121">Po otwarciu programu WordPad wpisz w nim ciąg tekstu.</span><span class="sxs-lookup"><span data-stu-id="83370-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="83370-122">Za pomocą myszy zaznacz tekst, a następnie przeciągnij <xref:System.Windows.Forms.RichTextBox> zaznaczony tekst do formantu w aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="83370-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="83370-123">Należy zauważyć, że po <xref:System.Windows.Forms.RichTextBox> wstrząśniu myszy <xref:System.Windows.Forms.RichTextBox.DragEnter> na formancie (i, w związku z <xref:System.Windows.Forms.RichTextBox> tym, podnieść zdarzenie), wskaźnik myszy zmienia się i można upuścić zaznaczony tekst do formantu.</span><span class="sxs-lookup"><span data-stu-id="83370-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="83370-124">Po zwolnieniu przycisku myszy zaznaczony tekst jest <xref:System.Windows.Forms.RichTextBox.DragDrop> odrzucany (oznacza to, że <xref:System.Windows.Forms.RichTextBox> zdarzenie jest wywoływane) i jest wstawiany do formantu.</span><span class="sxs-lookup"><span data-stu-id="83370-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83370-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83370-125">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="83370-126">Porady: wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami</span><span class="sxs-lookup"><span data-stu-id="83370-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [<span data-ttu-id="83370-127">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="83370-127">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="83370-128">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="83370-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
