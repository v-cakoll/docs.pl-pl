---
title: 'Instrukcje: włączenie operacji przeciągania i upuszczania za pomocą kontrolki RichTextBox formularzy systemu Windows'
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
ms.openlocfilehash: 5c60fe411fcbf6257c8aaacf1f7400c11c150ddc
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310281"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Instrukcje: włączenie operacji przeciągania i upuszczania za pomocą kontrolki RichTextBox formularzy systemu Windows
Operacje przeciągania i upuszczania za pomocą interfejsu Windows Forms <xref:System.Windows.Forms.RichTextBox> kontrolki są wykonywane przez obsługi <xref:System.Windows.Forms.RichTextBox.DragEnter> i <xref:System.Windows.Forms.RichTextBox.DragDrop> zdarzenia. W związku z tym, przeciągnij i upuść operacje są bardzo proste dzięki <xref:System.Windows.Forms.RichTextBox> kontroli.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Aby włączyć operacji przeciągania w formancie RichTextBox  
  
1. Ustaw <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> właściwość <xref:System.Windows.Forms.RichTextBox> kontrolę `true`.  
  
2. Pisz kod w obsłudze zdarzeń <xref:System.Windows.Forms.RichTextBox.DragEnter> zdarzeń. Użyj `if` instrukcję, aby upewnij się, że dane przeciąganie typu dopuszczalnych (w tym przypadku tekstu). <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> Właściwość można ustawić na dowolną wartość <xref:System.Windows.Forms.DragDropEffects> wyliczenia.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
3. Napisz kod obsługujący <xref:System.Windows.Forms.RichTextBox.DragDrop> zdarzeń. Użyj <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metody do pobierania danych przeciągania.  
  
     W przykładzie poniżej kod ustawia <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwość <xref:System.Windows.Forms.RichTextBox> kontrolować równa danych przeciągania. Jeśli istnieje już tekstu w <xref:System.Windows.Forms.RichTextBox> wstawieniu kontrolki, przeciąganego tekstowego w punkcie wstawiania.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a>Aby przetestować funkcje przeciągania i upuszczania w aplikacji  
  
1. Zapisz i skompiluj aplikację. Gdy jest uruchomiona, uruchom program WordPad.  
  
     Program WordPad, jest Edytor tekstu, zainstalowane przez Windows, która umożliwia wykonywanie operacji przeciągania i upuszczania. Jest dostępny, klikając **Start** przycisku, wybierając **Uruchom**, wpisz `WordPad` w polu tekstowym **Uruchom** okno dialogowe, a następnie klikając polecenie  **OK**.  
  
2. Po otwarciu programu WordPad, wpisz ciąg tekstowy w nim. Za pomocą myszy, zaznacz tekst, a następnie przeciągnij zaznaczony tekst do <xref:System.Windows.Forms.RichTextBox> kontrolki w aplikacji Windows.  
  
     Należy zauważyć, że po wskazaniu myszą w <xref:System.Windows.Forms.RichTextBox> kontroli (i w związku z tym, wywoływanie <xref:System.Windows.Forms.RichTextBox.DragEnter> zdarzeń), wskaźnik myszy zmienia i mogą porzucić zaznaczonego tekstu do <xref:System.Windows.Forms.RichTextBox> kontroli.  
  
     Po zwolnieniu przycisku myszy zaznaczony tekst jest porzucany (czyli <xref:System.Windows.Forms.RichTextBox.DragDrop> zdarzenie jest zgłaszane w) jest umieszczany w ramach <xref:System.Windows.Forms.RichTextBox> kontroli.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox>
- [Instrukcje: Wykonywanie mapowania i zmniejszanie operacji przeciągania i upuszczania między aplikacjami](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
