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
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Porady: włączenie operacji przeciągania i upuszczania za pomocą formantu RichTextBox formularzy systemu Windows
Operacje przeciągania i upuszczania za pomocą kontrolki <xref:System.Windows.Forms.RichTextBox> Windows Forms są wykonywane przez obsługę zdarzeń <xref:System.Windows.Forms.RichTextBox.DragEnter> i <xref:System.Windows.Forms.RichTextBox.DragDrop>. W ten sposób operacje przeciągania i upuszczania są niezwykle proste z kontrolką <xref:System.Windows.Forms.RichTextBox>.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Aby włączyć operacje przeciągania w kontrolce RichTextBox  
  
1. Ustaw właściwość <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> kontrolki <xref:System.Windows.Forms.RichTextBox> na `true`.  
  
2. Napisz kod w obsłudze zdarzeń zdarzenia <xref:System.Windows.Forms.RichTextBox.DragEnter>. Użyj instrukcji `if`, aby upewnić się, że przeciągane dane mają akceptowalny typ (w tym przypadku tekst). Właściwość <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> można ustawić na dowolną wartość wyliczenia <xref:System.Windows.Forms.DragDropEffects>.  
  
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
  
     (Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
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
  
3. Napisz kod, aby obsłużyć zdarzenie <xref:System.Windows.Forms.RichTextBox.DragDrop>. Użyj metody <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType>, aby pobrać przeciągane dane.  
  
     W poniższym przykładzie kod ustawia właściwość <xref:System.Windows.Forms.RichTextBox.Text%2A> kontrolki <xref:System.Windows.Forms.RichTextBox> równej przeciąganym danym. Jeśli w kontrolce <xref:System.Windows.Forms.RichTextBox> istnieje już tekst, przeciągany tekst zostanie wstawiony w punkcie wstawiania.  
  
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
  
     (Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.  
  
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
  
1. Zapisz i skompiluj aplikację. Gdy jest uruchomiona, uruchom program WordPad.  
  
     WordPad jest edytorem tekstu instalowanym przez system Windows, który umożliwia wykonywanie operacji przeciągania i upuszczania. Jest dostępny przez kliknięcie przycisku **Start** , wybranie polecenia **uruchom**, wpisanie `WordPad` w polu tekstowym okna dialogowego **Uruchamianie** , a następnie kliknięcie przycisku **OK**.  
  
2. Gdy program WordPad jest otwarty, wpisz w nim ciąg tekstowy. Za pomocą myszy zaznacz tekst, a następnie przeciągnij zaznaczony tekst do kontrolki <xref:System.Windows.Forms.RichTextBox> w aplikacji systemu Windows.  
  
     Należy zauważyć, że po umieszczeniu wskaźnika myszy na kontrolce <xref:System.Windows.Forms.RichTextBox> (i w efekcie podniesienia <xref:System.Windows.Forms.RichTextBox.DragEnter> zdarzenia) wskaźnik myszy ulegnie zmianie i można upuścić zaznaczony tekst do kontrolki <xref:System.Windows.Forms.RichTextBox>.  
  
     Po zwolnieniu przycisku myszy zaznaczony tekst zostanie porzucony (oznacza to, że zdarzenie <xref:System.Windows.Forms.RichTextBox.DragDrop> jest zgłaszane) i zostanie wstawione w kontrolce <xref:System.Windows.Forms.RichTextBox>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox>
- [Instrukcje: wykonywanie operacji przeciągania i upuszczania między aplikacjami](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
