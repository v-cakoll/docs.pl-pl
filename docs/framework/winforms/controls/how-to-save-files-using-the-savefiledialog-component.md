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
ms.openlocfilehash: ca6ca5adbbe20a438ba936778ba71f1a163b40e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a>Porady: zapisywanie plików za pomocą składnika SaveFileDialog
<xref:System.Windows.Forms.SaveFileDialog> Składnika umożliwia użytkownikom przeglądać systemu plików i wybierz pliki do zapisania. Okno dialogowe zwraca ścieżkę i nazwę pliku wybranego w oknie dialogowym. Jednak należy napisać kod do faktycznie zapisu plików do dysku.  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a>Aby zapisać plik za pomocą składnika SaveFileDialog  
  
-   Wyświetl **Zapisz plik** okno dialogowe i wywołanie metody można zapisać pliku wybrane przez użytkownika.  
  
     Użyj <xref:System.Windows.Forms.SaveFileDialog> składnika <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metodę, aby zapisać plik. Ta metoda umożliwia <xref:System.IO.Stream> możesz zapisywać do obiektu.  
  
     Poniższym przykładzie użyto <xref:System.Windows.Forms.DialogResult> właściwości można pobrać nazwy pliku i <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby zapisać plik. <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Metoda daje strumień pliku do zapisu.  
  
     W poniższym przykładzie jest <xref:System.Windows.Forms.Button> kontroli z obrazem przypisane do niej. Po kliknięciu przycisku, <xref:System.Windows.Forms.SaveFileDialog> składnik zostanie uruchomiony z filtrem, który umożliwia pliki typu GIF, JPEG i BMP. Zaznaczenie tego typu pliku w oknie dialogowym Zapisz plik jest zapisywany obraz przycisku.  
  
    > [!IMPORTANT]
    >  Można pobrać lub ustawić <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwość, z zestawu wymaga do poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     W przykładzie założono formularz zawiera <xref:System.Windows.Forms.Button> sterować za pomocą jego <xref:System.Windows.Forms.ButtonBase.Image%2A> właściwość w pliku typu GIF, JPEG lub bmp.  
  
    > [!NOTE]
    >  <xref:System.Windows.Forms.FileDialog> Klasy <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> właściwości (które z powodu dziedziczenia jest częścią <xref:System.Windows.Forms.SaveFileDialog> klasy) używa jednego indeksu. Jest to ważne podczas pisania kodu w celu zapisywania danych w określonym formacie (na przykład plik zostanie zapisany w postaci zwykłego tekstu lub format binarny). Ta właściwość jest umieszczony w poniższym przykładzie.  
  
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
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     Aby uzyskać więcej informacji na temat pisania strumieni plików, zobacz <xref:System.IO.FileStream.BeginWrite%2A> i <xref:System.IO.FileStream.Write%2A>.  
  
    > [!NOTE]
    >  Niektóre formanty, takie jak <xref:System.Windows.Forms.RichTextBox> kontrolować, ma możliwość zapisania plików. Aby uzyskać więcej informacji, zobacz sekcję "Savefiledialog — składnik" artykułu technicznego bibliotece MSDN Online [niezbędne kodu dla systemu Windows dialogowe w formularzach](http://go.microsoft.com/fwlink/?LinkID=102575).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog, składnik](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
