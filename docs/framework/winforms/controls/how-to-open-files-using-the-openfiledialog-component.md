---
title: "Porady: otwieranie plików za pomocą składnika OpenFileDialog"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fabe176ade1ae94a20100162ab7ab6fadfb2999f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a>Porady: otwieranie plików za pomocą składnika OpenFileDialog
<xref:System.Windows.Forms.OpenFileDialog> Składnika pozwala użytkownikom na przeglądanie folderów do komputera lub dowolnego komputera w sieci i wybierz jeden lub więcej plików, aby otworzyć. Okno dialogowe zwraca ścieżkę i nazwę pliku wybrany w oknie dialogowym przez użytkownika.  
  
 Gdy użytkownik wybrał plik, który można otworzyć, istnieją dwa podejścia do mechanizmu otwierania pliku. Jeśli wolisz używać strumieni plików, można utworzyć wystąpienia <xref:System.IO.StreamReader> klasy. Alternatywnie można użyć <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby otworzyć wybranego pliku.  
  
 W poniższym przykładzie pierwsze obejmuje <xref:System.Security.Permissions.FileIOPermission> sprawdzenie uprawnień (zgodnie z opisem "Zabezpieczeń poniższymi"), ale zapewnia dostęp do nazwy pliku. Ta metoda służy ze stref komputera lokalnego, intranetowych i internetowych. Druga metoda powoduje także <xref:System.Security.Permissions.FileIOPermission> sprawdzenie uprawnień, ale jest lepiej odpowiednie dla aplikacji w strefie intranetu lub Internetu.  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a>Umożliwia otwarcie pliku jako strumień za pomocą składnika OpenFileDialog  
  
1.  Wyświetl **Otwieranie pliku** okno dialogowe i wywołanie metody można otworzyć pliku wybrane przez użytkownika.  
  
     Jednym z podejść jest użycie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe Otwieranie pliku i użyć wystąpienia <xref:System.IO.StreamReader> klasy można otworzyć pliku.  
  
     Poniższym przykładzie użyto <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń, aby otworzyć wystąpienie <xref:System.Windows.Forms.OpenFileDialog> składnika. Gdy plik jest wybrany, a użytkownik kliknie **OK**, otwiera plik wybrany w oknie dialogowym. W takim przypadku zawartość są wyświetlane w oknie komunikatu, tak, aby pokazać, strumień pliku został odczytany.  
  
    > [!IMPORTANT]
    >  Można pobrać lub ustawić <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwość, z zestawu wymaga do poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     W przykładzie założono formularz zawiera <xref:System.Windows.Forms.Button> kontroli i <xref:System.Windows.Forms.OpenFileDialog> składnika.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  Aby uzyskać więcej informacji na temat odczytywanie ze strumieni plików, zobacz <xref:System.IO.FileStream.BeginRead%2A> i <xref:System.IO.FileStream.Read%2A>.  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a>Umożliwia otwarcie pliku jako pliku za pomocą składnika OpenFileDialog  
  
1.  Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe i <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby otworzyć plik.  
  
     <xref:System.Windows.Forms.OpenFileDialog> Składnika <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda zwraca liczbę bajtów, które tworzą pliku. Tych bajtów nadaj strumień do odczytu. W poniższym przykładzie <xref:System.Windows.Forms.OpenFileDialog> składnik zostanie uruchomiony przy użyciu filtru "kursora", co pozwala użytkownikowi na wybranie tylko pliki z rozszerzeniem nazwy pliku`.cur`. Jeśli`.cur` pliku jest wybrana, kursor formularza ma ustawioną wartość wybranego kursora.  
  
    > [!IMPORTANT]
    >  Aby wywołać <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metody używanemu zestawowi wymaga do poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
     W przykładzie założono formularz zawiera <xref:System.Windows.Forms.Button> formantu.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog, składnik](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
