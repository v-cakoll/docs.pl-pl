---
title: 'Porady: włączenie operacji przeciągania i upuszczania za pomocą kontrolki RichTextBox formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17bf3b8e50c4e51cb14225e402903428a309d67a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a>Porady: włączenie operacji przeciągania i upuszczania za pomocą kontrolki RichTextBox formularzy systemu Windows
Operacje przeciągania i upuszczania w formularzach systemu Windows <xref:System.Windows.Forms.RichTextBox> formantu są realizowane przez Obsługa <xref:System.Windows.Forms.RichTextBox.DragEnter> i <xref:System.Windows.Forms.RichTextBox.DragDrop> zdarzenia. W związku z tym są bardzo proste operacje przeciągania i upuszczania <xref:System.Windows.Forms.RichTextBox> formantu.  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a>Aby włączyć operacji przeciągania w formancie RichTextBox  
  
1.  Ustaw <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> właściwość <xref:System.Windows.Forms.RichTextBox> formant `true`.  
  
2.  Pisanie kodu w obsłudze zdarzeń <xref:System.Windows.Forms.RichTextBox.DragEnter> zdarzeń. Użyj `if` instrukcję w celu zapewnienia, że dane przeciągane jest dopuszczalne typu (w tym przypadku tekst). <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> Właściwość można ustawić wartości elementu <xref:System.Windows.Forms.DragDropEffects> wyliczenia.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
3.  Napisać kod obsługujący <xref:System.Windows.Forms.RichTextBox.DragDrop> zdarzeń. Użyj <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> metody do pobierania danych przeciągania.  
  
     W przykładzie poniżej kod ustawia <xref:System.Windows.Forms.RichTextBox.Text%2A> właściwość <xref:System.Windows.Forms.RichTextBox> kontrolować równa dane przeciągane. Jeśli istnieje już tekstu w <xref:System.Windows.Forms.RichTextBox> punkt wstawiania jest wstawiany formant, przeciąganego tekstu.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
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
  
1.  Zapisz i skompilować aplikację. Gdy jest uruchomiona, uruchom program WordPad.  
  
     Program WordPad jest zainstalowany w systemie Windows, która zezwala na wykonywanie operacji przeciągania i upuszczania edytora tekstu. Nie jest dostępny, klikając **Start** przycisku, wybierając **Uruchom**, wpisz `WordPad` w polu tekstowym **Uruchom** — okno dialogowe, a następnie klikając polecenie  **OK**.  
  
2.  Po otwarciu WordPad, wpisz ciąg tekstu w nim. Za pomocą myszy, zaznacz tekst, a następnie przeciągnij zaznaczony tekst do <xref:System.Windows.Forms.RichTextBox> kontroli w aplikacji systemu Windows.  
  
     Zwróć uwagę, że po wskazaniu myszy na <xref:System.Windows.Forms.RichTextBox> formantu (i w związku z tym, zgłoś <xref:System.Windows.Forms.RichTextBox.DragEnter> zdarzeń), zmiany wskaźnika myszy, a mogą porzucić zaznaczonego tekstu w <xref:System.Windows.Forms.RichTextBox> formantu.  
  
     Po zwolnieniu przycisku myszy zaznaczony tekst zostanie porzucony (oznacza to, <xref:System.Windows.Forms.RichTextBox.DragDrop> zdarzenia) i jest wstawiana <xref:System.Windows.Forms.RichTextBox> formantu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBox>  
 [Instrukcje: wykonywanie operacji przeciągania i upuszczania między aplikacjami](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 [RichTextBox, kontrolka](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
