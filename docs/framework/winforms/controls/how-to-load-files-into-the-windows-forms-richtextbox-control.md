---
title: 'Porady: ładowanie plików do formantu RichTextBox formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: 4d43536cab7806b8cf2de3d63b2d9f7f10024c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Porady: ładowanie plików do formantu RichTextBox formularzy systemu Windows
Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant może wyświetlać zwykłego tekstu, jako zwykły tekst Unicode lub plik tekst sformatowany (RTF). Aby to zrobić, należy wywołać <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metody. Można również użyć <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodę, aby załadować dane ze strumienia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a>Ładowanie pliku w formancie RichTextBox  
  
1.  Określanie ścieżki pliku, który można otworzyć za pomocą <xref:System.Windows.Forms.OpenFileDialog> składnika. Aby uzyskać ogólne informacje, zobacz [openfiledialog — informacje o składniku](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).  
  
2.  Wywołanie <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metody <xref:System.Windows.Forms.RichTextBox> formantu, określając można załadować pliku i opcjonalnie typu pliku. W poniższym przykładzie pliku do załadowania jest pobierana z <xref:System.Windows.Forms.OpenFileDialog> składnika <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwości. Wywołanie metody przy użyciu nazwy pliku jako jej argument tylko typu pliku zostanie zakłada się, że można RTF. Aby określić plik innego typu, należy wywołać metodę o wartości <xref:System.Windows.Forms.RichTextBoxStreamType> wyliczenie jako drugi argument.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.OpenFileDialog> składnika jest wyświetlany po kliknięciu przycisku. Wybrany plik jest otwarty i wyświetlana w <xref:System.Windows.Forms.RichTextBox> formantu. W tym przykładzie założono formularza znajduje się przycisk`btnOpenFile`.  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     (Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  Aby uruchomić ten proces, używanego zestawu może wymagać poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox, kontrolka](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
