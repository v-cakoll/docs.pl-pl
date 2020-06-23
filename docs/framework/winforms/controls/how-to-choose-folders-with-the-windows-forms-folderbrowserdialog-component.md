---
title: Wybieranie folderów ze składnikiem FolderBrowserDialog
description: Dowiedz się, jak używać składnika FolderBrowserDialog Windows Forms w aplikacjach systemu Windows tworzonych w celu monitowania użytkowników o wybranie folderu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: 11d01bbaec3b82bc221960ebab5e33ca1aa302db
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903678"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Porady: wybieranie folderów za pomocą składnika FolderBrowserDialog formularzy systemu Windows

Często w aplikacjach systemu Windows tworzone są monity użytkowników o wybranie folderu, najczęściej w celu zapisania zestawu plików. Składnik Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> pozwala łatwo wykonać to zadanie.

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Aby wybrać foldery ze składnikiem FolderBrowserDialog

1. W procedurze Sprawdź <xref:System.Windows.Forms.FolderBrowserDialog> Właściwość składnika, <xref:System.Windows.Forms.Form.DialogResult%2A> Aby zobaczyć, jak okno dialogowe zostało zamknięte i pobrać wartość <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwości składnika.

2. Jeśli musisz ustawić górny folder, który będzie wyświetlany w widoku drzewa okna dialogowego, ustaw <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> Właściwość, która przyjmuje element członkowski <xref:System.Environment.SpecialFolder> wyliczenia.

3. Ponadto można ustawić <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> Właściwość, która określa ciąg tekstowy, który pojawia się w górnej części widoku drzewa folderów.

    W poniższym przykładzie <xref:System.Windows.Forms.FolderBrowserDialog> składnik jest używany do wybrania folderu, podobnie jak podczas tworzenia projektu w programie Visual Studio i zostanie wyświetlony monit o wybranie folderu w celu zapisania go w programie. W tym przykładzie nazwa folderu jest następnie wyświetlana w <xref:System.Windows.Forms.TextBox> kontrolce formularza. Dobrym pomysłem jest umieszczenie lokalizacji w obszarze edytowalnym, takim jak <xref:System.Windows.Forms.TextBox> kontrolka, dzięki czemu użytkownicy mogą edytować wybór w przypadku wystąpienia błędu lub innych problemów. W tym przykładzie przyjęto, że formularz ze <xref:System.Windows.Forms.FolderBrowserDialog> składnikiem i <xref:System.Windows.Forms.TextBox> kontrolką.

    ```vb
    Public Sub ChooseFolder()
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then
            TextBox1.Text = FolderBrowserDialog1.SelectedPath
        End If
    End Sub
    ```

    ```csharp
    public void ChooseFolder()
    {
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)
        {
            textBox1.Text = folderBrowserDialog1.SelectedPath;
        }
    }
    ```

    ```cpp
    public:
       void ChooseFolder()
       {
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)
          {
             textBox1->Text = folderBrowserDialog1->SelectedPath;
          }
       }
    ```

    > [!IMPORTANT]
    > Aby użyć tej klasy, zestaw wymaga poziomu uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> Właściwość, która jest częścią <xref:System.Security.Permissions.FileIOPermissionAccess> wyliczenia. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).

Informacje o sposobach zapisywania plików znajdują się w temacie [How to: Save files using the SaveFileDialog](how-to-save-files-using-the-savefiledialog-component.md).

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog — Informacje o składniku (Formularze systemu Windows)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog, składnik](folderbrowserdialog-component-windows-forms.md)
