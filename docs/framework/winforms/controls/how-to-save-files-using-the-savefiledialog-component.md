---
title: 'Porady: zapisywanie plików za pomocą składnika SaveFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: 32de7f7e38195271e179d4fae3884b7a39f37c45
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868086"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Porady: zapisywanie plików za pomocą składnika SaveFileDialog

Składnik <xref:System.Windows.Forms.SaveFileDialog> umożliwia użytkownikom przeglądanie systemu plików i wybieranie plików do zapisania. Okno dialogowe zwraca ścieżkę i nazwę pliku, który użytkownik wybrał w oknie dialogowym. Jednak należy napisać kod, aby faktycznie zapisywać pliki na dysku.

### <a name="to-save-a-file-using-the-savefiledialog-component"></a>Aby zapisać plik przy użyciu składnika SaveFileDialog

- Wyświetl okno dialogowe **Zapisz plik** i Wywołaj metodę, aby zapisać plik wybrany przez użytkownika.

  Zapisz plik za pomocą metody <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> składnika <xref:System.Windows.Forms.SaveFileDialog>. Ta metoda zapewnia <xref:System.IO.Stream> obiektu, do którego można pisać.

  W poniższym przykładzie zastosowano Właściwość <xref:System.Windows.Forms.DialogResult>, aby uzyskać nazwę pliku, i metodę <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>, aby zapisać plik. Metoda <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> umożliwia utworzenie strumienia, w którym ma zostać zapisany plik.

  W poniższym przykładzie istnieje formant <xref:System.Windows.Forms.Button> z przydzielonym obrazem. Po kliknięciu tego przycisku zostanie utworzony wystąpienie składnika <xref:System.Windows.Forms.SaveFileDialog> z filtrem umożliwiającym używanie plików typu. gif, JPEG i BMP. Jeśli w oknie dialogowym Zapisz plik zostanie wybrany plik tego typu, obraz przycisku zostanie zapisany.

  > [!IMPORTANT]
  > Aby uzyskać lub ustawić właściwość <xref:System.Windows.Forms.FileDialog.FileName%2A>, zestaw wymaga poziomu uprawnień przyznany przez klasę <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień. Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).

  W przykładzie założono, że formularz ma kontrolkę <xref:System.Windows.Forms.Button> z właściwością <xref:System.Windows.Forms.ButtonBase.Image%2A> ustawioną na plik typu. gif,. jpeg lub. bmp.

  > [!NOTE]
  > Właściwość <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> klasy <xref:System.Windows.Forms.FileDialog> (która z powodu dziedziczenia jest częścią klasy <xref:System.Windows.Forms.SaveFileDialog>) używa indeksu jednego z nich. Jest to ważne w przypadku pisania kodu w celu zapisania danych w określonym formacie (na przykład zapisanie pliku w formacie zwykłego tekstu a binarny). Ta właściwość jest proponowana w poniższym przykładzie.

  ```vb
  Private Sub Button2_Click(ByVal sender As System.Object, _
  ByVal e As System.EventArgs) Handles Button2.Click
      ' Displays a SaveFileDialog so the user can save the Image
      ' assigned to Button2.
      Dim saveFileDialog1 As New SaveFileDialog()
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"
      saveFileDialog1.Title = "Save an Image File"
      saveFileDialog1.ShowDialog()

      ' If the file name is not an empty string open it for saving.
      If saveFileDialog1.FileName <> "" Then
        ' Saves the Image via a FileStream created by the OpenFile method.
        Dim fs As System.IO.FileStream = Ctype _
            (saveFileDialog1.OpenFile(), System.IO.FileStream)
        ' Saves the Image in the appropriate ImageFormat based upon the
        ' file type selected in the dialog box.
        ' NOTE that the FilterIndex property is one-based.
        Select Case saveFileDialog1.FilterIndex
            Case 1
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Jpeg)

            Case 2
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Bmp)

            Case 3
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Gif)
          End Select

          fs.Close()
      End If
  End Sub
  ```

  ```csharp
  private void button2_Click(object sender, System.EventArgs e)
  {
      // Displays a SaveFileDialog so the user can save the Image
      // assigned to Button2.
      SaveFileDialog saveFileDialog1 = new SaveFileDialog();
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
      saveFileDialog1.Title = "Save an Image File";
      saveFileDialog1.ShowDialog();

      // If the file name is not an empty string open it for saving.
      if(saveFileDialog1.FileName != "")
      {
        // Saves the Image via a FileStream created by the OpenFile method.
        System.IO.FileStream fs =
            (System.IO.FileStream)saveFileDialog1.OpenFile();
        // Saves the Image in the appropriate ImageFormat based upon the
        // File type selected in the dialog box.
        // NOTE that the FilterIndex property is one-based.
        switch(saveFileDialog1.FilterIndex)
        {
            case 1 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Jpeg);
            break;

            case 2 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Bmp);
            break;

            case 3 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Gif);
            break;
        }

      fs.Close();
      }
  }
  ```

  ```cpp
  private:
      System::Void button2_Click(System::Object ^ sender,
        System::EventArgs ^ e)
      {
        // Displays a SaveFileDialog so the user can save the Image
        // assigned to Button2.
        SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();
        saveFileDialog1->Filter =
            "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
        saveFileDialog1->Title = "Save an Image File";
        saveFileDialog1->ShowDialog();
        // If the file name is not an empty string, open it for saving.
        if(saveFileDialog1->FileName != "")
        {
            // Saves the Image through a FileStream created by
            // the OpenFile method.
            System::IO::FileStream ^ fs =
              safe_cast\<System::IO::FileStream*>(
              saveFileDialog1->OpenFile());
            // Saves the Image in the appropriate ImageFormat based on
            // the file type selected in the dialog box.
            // Note that the FilterIndex property is one based.
            switch(saveFileDialog1->FilterIndex)
            {
              case 1 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Jpeg);
                  break;
              case 2 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Bmp);
                  break;
              case 3 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Gif);
                  break;
            }
        fs->Close();
        }
      }
  ```

  (Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  Aby uzyskać więcej informacji na temat pisania strumieni plików, zobacz <xref:System.IO.FileStream.BeginWrite%2A> i <xref:System.IO.FileStream.Write%2A>.

  > [!NOTE]
  > Niektóre kontrolki, takie jak kontrolka <xref:System.Windows.Forms.RichTextBox>, mogą zapisywać pliki.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.SaveFileDialog>
- [SaveFileDialog, składnik](savefiledialog-component-windows-forms.md)
