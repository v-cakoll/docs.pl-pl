---
title: 'Instrukcje: ładowanie plików do kontrolki RichTextBox formularzy systemu Windows'
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
ms.openlocfilehash: 0f52b4ff869d7a2220dd2d40e0ab90bbfb7d24ae
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046168"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a>Instrukcje: ładowanie plików do kontrolki RichTextBox formularzy systemu Windows

Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms może wyświetlić plik w formacie zwykłego tekstu (RTF) Unicode lub RTF. Aby to zrobić, wywołaj <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodę. Można również użyć <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metody do ładowania danych ze strumienia. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.

### <a name="to-load-a-file-into-the-richtextbox-control"></a>Aby załadować plik do kontrolki RichTextBox

1. Określ ścieżkę pliku, który ma zostać otwarty za pomocą <xref:System.Windows.Forms.OpenFileDialog> składnika. Aby zapoznać się z omówieniem, zobacz [Omówienie składnika OpenFileDialog](openfiledialog-component-overview-windows-forms.md).

2. Wywołaj <xref:System.Windows.Forms.RichTextBox> metodę kontrolki, określając plik do załadowania i opcjonalnie typ pliku. <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> W poniższym przykładzie plik do załadowania jest pobierany ze <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwości składnika. W przypadku wywołania metody z nazwą pliku jako jedynego argumentu, przyjmuje się, że zostanie on RTF. Aby określić inny typ pliku, wywołaj metodę z wartością <xref:System.Windows.Forms.RichTextBoxStreamType> wyliczenia jako jej drugi argument.

    W poniższym <xref:System.Windows.Forms.OpenFileDialog> przykładzie składnik jest wyświetlany po kliknięciu przycisku. Wybrany plik jest następnie otwierany i wyświetlany w <xref:System.Windows.Forms.RichTextBox> kontrolce. W tym przykładzie założono, że formularz ma`btnOpenFile`przycisk,.

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
    > Aby można było uruchomić ten proces, zestaw może wymagać poziomu uprawnień przyznany przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasę. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox, kontrolka](richtextbox-control-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
