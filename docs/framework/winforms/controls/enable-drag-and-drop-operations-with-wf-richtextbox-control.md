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
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Porady: włączenie operacji przeciągania i upuszczania za pomocą formantu RichTextBox formularzy systemu Windows
Operacje przeciągania i upuszczania za pomocą formantu Windows Forms <xref:System.Windows.Forms.RichTextBox> są wykonywane przez obsługę <xref:System.Windows.Forms.RichTextBox.DragEnter> zdarzeń i. <xref:System.Windows.Forms.RichTextBox.DragDrop> W związku z tym operacje przeciągania <xref:System.Windows.Forms.RichTextBox> i upuszczania są niezwykle proste z formantem.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Aby włączyć operacje przeciągania w formancie RichTextBox  
  
1. Ustaw <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> właściwość <xref:System.Windows.Forms.RichTextBox> formantu na `true`.  
  
2. Napisz kod w programie <xref:System.Windows.Forms.RichTextBox.DragEnter> obsługi zdarzeń zdarzenia. Użyj `if` instrukcji, aby upewnić się, że przeciągane dane są akceptowalnym typem (w tym przypadku tekst). Właściwość <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> można ustawić na dowolną <xref:System.Windows.Forms.DragDropEffects> wartość wyliczenia.  
  
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
  
     (Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
3. Napisz kod do <xref:System.Windows.Forms.RichTextBox.DragDrop> obsługi zdarzenia. Użyj <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metody, aby pobrać przeciągane dane.  
  
     W poniższym przykładzie kod <xref:System.Windows.Forms.RichTextBox.Text%2A> ustawia <xref:System.Windows.Forms.RichTextBox> właściwość formantu równą przeciąganym danym. Jeśli w <xref:System.Windows.Forms.RichTextBox> formancie znajduje się już tekst, przeciągany tekst jest wstawiany w punkcie wstawiania.  
  
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
  
     (Visual C# i Visual C++) Umieść następujący kod w konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Aby przetestować funkcję przeciągania i upuszczania w aplikacji  
  
1. Zapisz i skompiluj aplikację. Podczas pracy uruchom program WordPad.  
  
     WordPad to edytor tekstu zainstalowany przez system Windows, który umożliwia operacje przeciągania i upuszczania. Jest on dostępny po kliknięciu przycisku **Start,** **wybraniu przycisku Uruchom,** wpisując `WordPad` w polu tekstowym okna dialogowego **Uruchom,** a następnie klikając **przycisk OK**.  
  
2. Po otwarciu programu WordPad wpisz w nim ciąg tekstu. Za pomocą myszy zaznacz tekst, a następnie przeciągnij <xref:System.Windows.Forms.RichTextBox> zaznaczony tekst do formantu w aplikacji systemu Windows.  
  
     Należy zauważyć, że po <xref:System.Windows.Forms.RichTextBox> wstrząśniu myszy <xref:System.Windows.Forms.RichTextBox.DragEnter> na formancie (i, w związku z <xref:System.Windows.Forms.RichTextBox> tym, podnieść zdarzenie), wskaźnik myszy zmienia się i można upuścić zaznaczony tekst do formantu.  
  
     Po zwolnieniu przycisku myszy zaznaczony tekst jest <xref:System.Windows.Forms.RichTextBox.DragDrop> odrzucany (oznacza to, że <xref:System.Windows.Forms.RichTextBox> zdarzenie jest wywoływane) i jest wstawiany do formantu.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.RichTextBox>
- [Porady: wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
