---
title: Załaduj pliki do kontrolki RichTextBox
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
ms.openlocfilehash: c31e004ea4cd0821b5f18f0ab0fe2708e6ac4b59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736288"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Porady: ładowanie plików do formantu RichTextBox formularzy systemu Windows

Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms może wyświetlić plik w formacie zwykłego tekstu (RTF) Unicode lub RTF. Aby to zrobić, wywołaj metodę <xref:System.Windows.Forms.RichTextBox.LoadFile%2A>. Za pomocą metody <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> można również ładować dane ze strumienia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-load-a-file-into-the-richtextbox-control"></a>Aby załadować plik do kontrolki RichTextBox

1. Określ ścieżkę pliku, który ma zostać otwarty za pomocą składnika <xref:System.Windows.Forms.OpenFileDialog>. Aby zapoznać się z omówieniem, zobacz [Omówienie składnika OpenFileDialog](openfiledialog-component-overview-windows-forms.md).

2. Wywołaj metodę <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> kontrolki <xref:System.Windows.Forms.RichTextBox>, określając plik do załadowania i opcjonalnego typu pliku. W poniższym przykładzie plik do załadowania jest pobierany ze właściwości <xref:System.Windows.Forms.FileDialog.FileName%2A> składnika <xref:System.Windows.Forms.OpenFileDialog>. W przypadku wywołania metody z nazwą pliku jako jedynego argumentu, przyjmuje się, że zostanie on RTF. Aby określić inny typ pliku, należy wywołać metodę z wartością wyliczenia <xref:System.Windows.Forms.RichTextBoxStreamType> jako drugi argument.

    W poniższym przykładzie składnik <xref:System.Windows.Forms.OpenFileDialog> jest wyświetlany po kliknięciu przycisku. Wybrany plik jest następnie otwierany i wyświetlany w kontrolce <xref:System.Windows.Forms.RichTextBox>. W tym przykładzie założono, że formularz ma przycisk`btnOpenFile`.

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

    (Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > Aby można było uruchomić ten proces, zestaw może wymagać poziomu uprawnień przyznanych przez klasę <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
