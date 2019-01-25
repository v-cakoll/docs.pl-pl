---
title: 'Instrukcje: Otwieranie plików za pomocą składnika OpenFileDialog'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
ms.openlocfilehash: 87e7640da76205341b9e95310314800ac9dbfe30
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678814"
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>Instrukcje: Otwieranie plików za pomocą składnika OpenFileDialog
<xref:System.Windows.Forms.OpenFileDialog> Składnika pozwala użytkownikom na przeglądanie folderów ich komputera lub dowolnego komputera w sieci, a następnie wybierz jeden lub więcej plików, aby otworzyć. Okno dialogowe zwraca ścieżkę i nazwę pliku wybranego w oknie dialogowym użytkownika.  
  
 Po użytkownik wybrał plik do otwarcia, istnieją dwa podejścia do mechanizmu otwierania pliku. Jeśli wolisz pracować z strumieni plików, można utworzyć wystąpienia <xref:System.IO.StreamReader> klasy. Alternatywnie możesz użyć <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby otworzyć wybranego pliku.  
  
 W poniższym przykładzie pierwszy obejmuje <xref:System.Security.Permissions.FileIOPermission> sprawdzenie uprawnień (zgodnie z opisem w "Uwaga dotycząca zabezpieczeń" poniżej), ale zapewnia dostęp do nazwy pliku. Tej techniki można używać z komputera lokalnego, intranetowych i internetowych stref. Druga metoda wykonuje <xref:System.Security.Permissions.FileIOPermission> sprawdzenie uprawnień, ale lepiej nadaje się dla aplikacji w strefie intranetu lub Internetu.  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>Aby otworzyć plik jako strumienia za pomocą składnika OpenFileDialog  
  
1.  Wyświetlanie **Otwórz plik** okno dialogowe i wywołania metody można otworzyć pliku wybrana przez użytkownika.  
  
     Jedno z podejść jest użycie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe Otwieranie pliku, a następnie użyj wystąpienia <xref:System.IO.StreamReader> klasy można otworzyć pliku.  
  
     W poniższym przykładzie użyto <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń, aby otworzyć wystąpienie <xref:System.Windows.Forms.OpenFileDialog> składnika. Gdy plik jest wybrana, a użytkownik kliknie **OK**, otwiera plik, który został wybrany w oknie dialogowym. W takim przypadku zawartości są wyświetlane w oknie komunikatu, aby zobrazować, czy strumień pliku został odczytany.  
  
    > [!IMPORTANT]
    >  Do pobierania lub ustawiania <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwości zestawu wymaga poziom uprawnień przyznanych <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     W przykładzie założono, formularz ma <xref:System.Windows.Forms.Button> kontroli i <xref:System.Windows.Forms.OpenFileDialog> składnika.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji na temat odczytywania ze strumieni plików Zobacz <xref:System.IO.FileStream.BeginRead%2A> i <xref:System.IO.FileStream.Read%2A>.  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a>Aby otworzyć plik w formacie za pomocą składnika OpenFileDialog  
  
1.  Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe i <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby otworzyć plik.  
  
     <xref:System.Windows.Forms.OpenFileDialog> Składnika <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda zwraca bajtów, które tworzą plik. Bajty te umożliwiają strumień do odczytu. W poniższym przykładzie <xref:System.Windows.Forms.OpenFileDialog> składnik jest utworzone za pomocą filtru "kursora", umożliwiając użytkownikowi na wybranie tylko pliki z rozszerzeniem nazwy pliku`.cur`. Jeśli`.cur` pliku jest wybrany, kursor formularza jest ustawiona na wybranych kursora.  
  
    > [!IMPORTANT]
    >  Aby wywołać <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda, zestaw wymaga, aby poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     W przykładzie założono, formularz ma <xref:System.Windows.Forms.Button> kontroli.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     (Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.OpenFileDialog>
- [OpenFileDialog, składnik](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
