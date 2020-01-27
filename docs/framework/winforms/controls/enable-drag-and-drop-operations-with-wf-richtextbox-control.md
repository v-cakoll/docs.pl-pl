---
title: Włączanie operacji przeciągania i upuszczania za pomocą kontrolki RichTextBox
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
ms.openlocfilehash: 3c17560dee012912aea2938654f1dc4dc56e0725
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745822"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="7618a-102">Porady: włączenie operacji przeciągania i upuszczania za pomocą formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7618a-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="7618a-103">Operacje przeciągania i upuszczania za pomocą kontrolki <xref:System.Windows.Forms.RichTextBox> Windows Forms są wykonywane przez obsługę zdarzeń <xref:System.Windows.Forms.RichTextBox.DragEnter> i <xref:System.Windows.Forms.RichTextBox.DragDrop>.</span><span class="sxs-lookup"><span data-stu-id="7618a-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="7618a-104">W ten sposób operacje przeciągania i upuszczania są niezwykle proste z kontrolką <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="7618a-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="7618a-105">Aby włączyć operacje przeciągania w kontrolce RichTextBox</span><span class="sxs-lookup"><span data-stu-id="7618a-105">To enable drag operations in a RichTextBox control</span></span>  
  
1. <span data-ttu-id="7618a-106">Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> kontrolki <xref:System.Windows.Forms.RichTextBox> na `true`.</span><span class="sxs-lookup"><span data-stu-id="7618a-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2. <span data-ttu-id="7618a-107">Napisz kod w obsłudze zdarzeń zdarzenia <xref:System.Windows.Forms.RichTextBox.DragEnter>.</span><span class="sxs-lookup"><span data-stu-id="7618a-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="7618a-108">Użyj instrukcji `if`, aby upewnić się, że przeciągane dane mają akceptowalny typ (w tym przypadku tekst).</span><span class="sxs-lookup"><span data-stu-id="7618a-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="7618a-109">Właściwość <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> można ustawić na dowolną wartość wyliczenia <xref:System.Windows.Forms.DragDropEffects>.</span><span class="sxs-lookup"><span data-stu-id="7618a-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
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
  
     <span data-ttu-id="7618a-110">(Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7618a-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
3. <span data-ttu-id="7618a-111">Napisz kod, aby obsłużyć zdarzenie <xref:System.Windows.Forms.RichTextBox.DragDrop>.</span><span class="sxs-lookup"><span data-stu-id="7618a-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="7618a-112">Użyj metody <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType>, aby pobrać przeciągane dane.</span><span class="sxs-lookup"><span data-stu-id="7618a-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="7618a-113">W poniższym przykładzie kod ustawia właściwość <xref:System.Windows.Forms.RichTextBox.Text%2A> kontrolki <xref:System.Windows.Forms.RichTextBox> równej przeciąganym danym.</span><span class="sxs-lookup"><span data-stu-id="7618a-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="7618a-114">Jeśli w kontrolce <xref:System.Windows.Forms.RichTextBox> istnieje już tekst, przeciągany tekst zostanie wstawiony w punkcie wstawiania.</span><span class="sxs-lookup"><span data-stu-id="7618a-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
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
  
     <span data-ttu-id="7618a-115">(Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7618a-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="7618a-116">Aby przetestować funkcję przeciągania i upuszczania w aplikacji</span><span class="sxs-lookup"><span data-stu-id="7618a-116">To test the drag-and-drop functionality in your application</span></span>  
  
1. <span data-ttu-id="7618a-117">Zapisz i skompiluj aplikację.</span><span class="sxs-lookup"><span data-stu-id="7618a-117">Save and build your application.</span></span> <span data-ttu-id="7618a-118">Gdy jest uruchomiona, uruchom program WordPad.</span><span class="sxs-lookup"><span data-stu-id="7618a-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="7618a-119">WordPad jest edytorem tekstu instalowanym przez system Windows, który umożliwia wykonywanie operacji przeciągania i upuszczania.</span><span class="sxs-lookup"><span data-stu-id="7618a-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="7618a-120">Jest dostępny przez kliknięcie przycisku **Start** , wybranie polecenia **uruchom**, wpisanie `WordPad` w polu tekstowym okna dialogowego **Uruchamianie** , a następnie kliknięcie przycisku **OK**.</span><span class="sxs-lookup"><span data-stu-id="7618a-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2. <span data-ttu-id="7618a-121">Gdy program WordPad jest otwarty, wpisz w nim ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="7618a-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="7618a-122">Za pomocą myszy zaznacz tekst, a następnie przeciągnij zaznaczony tekst do kontrolki <xref:System.Windows.Forms.RichTextBox> w aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7618a-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="7618a-123">Należy zauważyć, że po umieszczeniu wskaźnika myszy na kontrolce <xref:System.Windows.Forms.RichTextBox> (i w efekcie podniesienia <xref:System.Windows.Forms.RichTextBox.DragEnter> zdarzenia) wskaźnik myszy ulegnie zmianie i można upuścić zaznaczony tekst do kontrolki <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="7618a-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="7618a-124">Po zwolnieniu przycisku myszy zaznaczony tekst zostanie porzucony (oznacza to, że zdarzenie <xref:System.Windows.Forms.RichTextBox.DragDrop> jest zgłaszane) i zostanie wstawione w kontrolce <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="7618a-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7618a-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7618a-125">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="7618a-126">Instrukcje: wykonywanie operacji przeciągania i upuszczania między aplikacjami</span><span class="sxs-lookup"><span data-stu-id="7618a-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [<span data-ttu-id="7618a-127">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="7618a-127">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="7618a-128">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7618a-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
