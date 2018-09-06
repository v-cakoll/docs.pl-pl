---
title: Bezpieczniejszy dostęp do plików i danych w formularzach systemu Windows
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [Windows Forms], file access
- registry [Windows Forms]
- data access [Windows Forms]
- database access (Windows Forms security)
- data [Windows Forms], secure access
- file access [Windows Forms]
- security [Windows Forms], data access
ms.assetid: 3cd3e55b-2f5e-40dd-835d-f50f7ce08967
ms.openlocfilehash: d5a9b08188e346fdea5b155149dee1ef8368c2a0
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881106"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Bezpieczniejszy dostęp do plików i danych w formularzach systemu Windows
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Używa uprawnień w celu ochrony zasobów i danych. Gdzie aplikacji może odczytać lub zapisać danych zależy od uprawnienia nadane aplikacji. Po uruchomieniu aplikacji w środowisku częściowej relacji zaufania, może nie mieć dostępu do danych lub może być zmienić sposób dostępu do danych.  
  
 Gdy występują ograniczenia zabezpieczeń, masz dwie opcje: asercja uprawnień (przy założeniu, zostanie przyznany aplikacji) lub korzystania z wersji funkcji zapisywane do pracy w trybie częściowego zaufania. W poniższych sekcjach omówiono sposób pracy z pliku, bazy danych i dostęp do rejestru z aplikacji, które są uruchomione w środowisku częściowej relacji zaufania.  
  
> [!NOTE]
>  Domyślnie, narzędzia, które generują [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] wdrożeń domyślnie wdrożeń żądania pełne zaufanie z komputerów, na których działają. Jeśli chcesz, aby zwiększyć bezpieczeństwo zalet działających w częściowej relacji zaufania, należy zmienić to ustawienie domyślne w programie Visual Studio lub w jednym z [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] narzędzia (Mage.exe lub MageUI.exe). Aby uzyskać więcej informacji o zabezpieczeniach Windows Forms i na temat sposobu określenia odpowiedniego poziomu zaufania dla aplikacji, zobacz [zabezpieczeń w Windows Forms — omówienie](../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Dostęp do plików  
 <xref:System.Security.Permissions.FileIOPermission> Klasy kontroli dostępu do plików i folderów w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Domyślnie system zabezpieczeń nie powoduje przyznania <xref:System.Security.Permissions.FileIOPermission> środowiskach częściowej relacji zaufania, takich jak lokalny intranet i stref internetowych. Jednak aplikacja, która wymaga dostępu do plików mogą nadal działać w tych środowiskach, jeśli zmodyfikować projekt aplikacji, lub uzyskiwania dostępu do plików za pomocą różnych metod. Domyślnie strefy Lokalny intranet jest prawo do tego samego dostępu do witryn i tego samego dostępu do katalogów, do łączenia z powrotem do witryny pochodzenia i odczytać z jego katalogu instalacji. Domyślnie strefy Internet jest tylko prawo do łączenia z powrotem do witryny pochodzenia.  
  
### <a name="user-specified-files"></a>Pliki określone przez użytkownika  
 Jednym ze sposobów, aby poradzić sobie z nie mają dostępu do pliku uprawnień jest aby monitować użytkownika o podanie informacji o pliku określonego za pomocą <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> klasy. Ta interakcja użytkownika pomaga zapewnić niektórych aplikacji nie złośliwie ładować pliki prywatne lub zastąpić ważnych plików. <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> i <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody zapewniają uprawnienia odczytu i zapisu plików, otwierając strumienia pliku dla pliku, określonej przez użytkownika. Te metody także chronić pliku użytkownika przesłaniania ścieżki pliku.  
  
> [!NOTE]
>  Uprawnienia te różnią się w zależności od tego, czy aplikacja jest w strefie Internet lub strefy intranetowej. Można używać tylko aplikacji do strefy Internet <xref:System.Windows.Forms.OpenFileDialog>, podczas gdy aplikacji intranetowych mają nieograniczony uprawnień okna dialogowego do pliku.  
  
 <xref:System.Security.Permissions.FileDialogPermission> Klasa określa, jakiego rodzaju okno dialogowe pliku można użyć w aplikacji. W poniższej tabeli przedstawiono wartości potrzebne do używania każdego <xref:System.Windows.Forms.FileDialog> klasy.  
  
|Class|Wartość wymaganego dostępu|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  Określone uprawnienie nie jest wymagana do momentu <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> faktycznie jest wywoływana metoda.  
  
 Uprawnienia, aby wyświetlić okno dialogowe pliku nie przyznaje Twojej aplikacji uzyskanie pełnego dostępu do wszystkich członków <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, i <xref:System.Windows.Forms.SaveFileDialog> klasy. Uprawnienia, które są wymagane do wywołania każdej metody, zobacz temat referencyjny dla tej metody w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] dokumentacji biblioteki klasy.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby otworzyć plik określony przez użytkownika do <xref:System.Windows.Forms.RichTextBox> kontroli. Przykład wymaga <xref:System.Security.Permissions.FileDialogPermission> oraz skojarzonych z nimi <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> wartość wyliczenia. W przykładzie pokazano sposób obsługi <xref:System.Security.SecurityException> ustalenie, czy zapisywanie funkcji powinna być wyłączona. W tym przykładzie wymaga, aby Twoje <xref:System.Windows.Forms.Form> ma <xref:System.Windows.Forms.Button> formantu o nazwie `ButtonOpen`, a <xref:System.Windows.Forms.RichTextBox> formantu o nazwie `RtfBoxMain`.  
  
> [!NOTE]
>  Logikę programistyczną zapisywania funkcji nie pokazano w przykładzie.  
  
```vb  
Private Sub ButtonOpen_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles ButtonOpen.Click   
  
    Dim editingFileName as String = ""  
    Dim saveAllowed As Boolean = True  
  
    ' Displays the OpenFileDialog.  
    If (OpenFileDialog1.ShowDialog() = DialogResult.OK) Then  
        Dim userStream as System.IO.Stream  
        Try   
            ' Opens the file stream for the file selected by the user.  
            userStream =OpenFileDialog1.OpenFile()   
            Me.RtfBoxMain.LoadFile(userStream, _  
                RichTextBoxStreamType.PlainText)  
        Finally  
            userStream.Close()  
        End Try  
  
        ' Tries to get the file name selected by the user.  
        ' Failure means that the application does not have  
        ' unrestricted permission to the file.  
        Try   
            editingFileName = OpenFileDialog1.FileName  
        Catch ex As Exception  
            If TypeOf ex Is System.Security.SecurityException Then   
                ' The application does not have unrestricted permission   
                ' to the file so the save feature will be disabled.  
                saveAllowed = False   
            Else   
                Throw ex  
            End If  
        End Try  
    End If  
End Sub  
```  
  
```csharp  
private void ButtonOpen_Click(object sender, System.EventArgs e)   
{  
    String editingFileName = "";  
    Boolean saveAllowed = true;  
  
    // Displays the OpenFileDialog.  
    if (openFileDialog1.ShowDialog() == DialogResult.OK)   
    {  
        // Opens the file stream for the file selected by the user.  
        using (System.IO.Stream userStream = openFileDialog1.OpenFile())   
        {  
            this.RtfBoxMain.LoadFile(userStream,  
                RichTextBoxStreamType.PlainText);  
            userStream.Close();  
        }  
  
        // Tries to get the file name selected by the user.  
        // Failure means that the application does not have  
        // unrestricted permission to the file.  
        try   
        {  
            editingFileName = openFileDialog1.FileName;  
        }   
        catch (Exception ex)   
        {  
            if (ex is System.Security.SecurityException)   
            {  
                // The application does not have unrestricted permission   
                // to the file so the save feature will be disabled.  
                saveAllowed = false;   
            }   
            else   
            {  
                throw ex;  
            }  
        }  
    }  
}  
```  
  
> [!NOTE]
>  W Visual C#, upewnij się, że dodasz kod, aby włączyć program obsługi zdarzeń. Za pomocą kodu z poprzedniego przykładu, poniższy kod przedstawia sposób włączania obsługi zdarzeń.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Inne pliki  
 Czasami konieczne będzie odczytu lub zapisu do plików, że użytkownik nie określi, takie jak kiedy muszą zostać zachowane ustawienia aplikacji. Lokalny intranet i stref internetowych aplikacji, nie będzie ona uprawnienia do przechowywania danych w pliku lokalnym. Jednak aplikacja będzie przechowywać dane w magazynie izolowanym. Wydzielona pamięć masowa jest przedział danych abstrakcyjny (nie lokalizacja określonego magazynu), który zawiera jeden lub więcej plików wydzielonej pamięci masowej, nazywanego magazynem, zawierające rzeczywistą lokalizację katalogu gdzie dane są przechowywane. Plik uprawnień dostępu, takich jak <xref:System.Security.Permissions.FileIOPermission> nie są wymagane; zamiast tego <xref:System.Security.Permissions.IsolatedStoragePermission> klasy określa uprawnienia do wydzielonej pamięci masowej. Domyślnie aplikacje, które są uruchomione w lokalnej sieci intranet i stref internetowych mogą być przechowywane dane przy użyciu izolowanego magazynu; Jednak ustawienia, takie jak przydział dysku mogą się różnić. Aby uzyskać więcej informacji na temat wydzielonej pamięci masowej, zobacz [wydzielonej pamięci masowej](../../../docs/standard/io/isolated-storage.md).  
  
 W poniższym przykładzie użyto wydzielonej pamięci masowej można zapisać danych do pliku znajdującego się w magazynie. Przykład wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> i <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> wartość wyliczenia. W przykładzie pokazano odczytywania i zapisywania określonych wartości właściwości <xref:System.Windows.Forms.Button> formantu do pliku w wydzielonej pamięci masowej. `Read` Funkcja może być wywoływana po uruchomieniu aplikacji i `Write` funkcja może zostać wywołana przed zakończeniem aplikacji. Przykład wymaga, aby `Read` i `Write` funkcje istnieje jako elementy członkowskie <xref:System.Windows.Forms.Form> zawierający <xref:System.Windows.Forms.Button> formantu o nazwie `MainButton`.  
  
```vb  
' Reads the button options from the isolated storage. Uses Default values   
' for the button if the options file does not exist.  
Public Sub Read()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try  
        ' Checks to see if the options.txt file exists.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
  
            ' Opens the file because it exists.  
            Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
                 (filename, IO.FileMode.Open,isoStore)  
            Dim reader as System.IO.StreamReader  
            Try   
                reader = new System.IO.StreamReader(isos)  
  
                ' Reads the values stored.  
                Dim converter As System.ComponentModel.TypeConverter  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Color))  
  
                Me.MainButton.BackColor = _   
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
                me.MainButton.ForeColor = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Color)  
  
                converter = System.ComponentModel.TypeDescriptor.GetConverter _   
                    (GetType(Font))  
                me.MainButton.Font = _  
                        CType(converter.ConvertFromString _   
                         (reader.ReadLine()), Font)  
  
            Catch ex As Exception  
                Debug.WriteLine("Cannot read options " + _  
                    ex.ToString())  
            Finally  
                reader.Close()  
            End Try  
        End If  
  
    Catch ex As Exception  
        Debug.WriteLine("Cannot read options " + ex.ToString())  
    End Try  
End Sub  
  
' Writes the button options to the isolated storage.  
Public Sub Write()   
    Dim isoStore As System.IO.IsolatedStorage.IsolatedStorageFile = _  
        System.IO.IsolatedStorage.IsolatedStorageFile. _   
        GetUserStoreForDomain()  
  
    Dim filename As String = "options.txt"  
    Try   
        ' Checks if the file exists, and if it does, tries to delete it.  
        If (isoStore.GetFileNames(filename).GetLength(0) <> 0) Then  
            isoStore.DeleteFile(filename)  
        End If  
    Catch ex As Exception  
        Debug.WriteLine("Cannot delete file " + ex.ToString())  
    End Try  
  
    ' Creates the options.txt file and writes the button options to it.  
    Dim writer as System.IO.StreamWriter  
    Try   
        Dim isos As New System.IO.IsolatedStorage.IsolatedStorageFileStream _   
             (filename, IO.FileMode.CreateNew, isoStore)  
  
        writer = New System.IO.StreamWriter(isos)  
        Dim converter As System.ComponentModel.TypeConverter  
  
        converter = System.ComponentModel.TypeDescriptor.GetConverter _   
           (GetType(Color))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.BackColor))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.ForeColor))  
  
        converter = System.ComponentModel TypeDescriptor.GetConverter _   
           (GetType(Font))  
        writer.WriteLine(converter.ConvertToString( _  
            Me.MainButton.Font))  
  
    Catch ex as Exception  
        Debug.WriteLine("Cannot write options " + ex.ToString())  
  
    Finally  
        writer.Close()  
    End Try  
End Sub  
```  
  
```csharp  
// Reads the button options from the isolated storage. Uses default values   
// for the button if the options file does not exist.  
public void Read()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try  
    {  
        // Checks to see if the options.txt file exists.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            // Opens the file because it exists.  
            System.IO.IsolatedStorage.IsolatedStorageFileStream isos =   
                new System.IO.IsolatedStorage.IsolatedStorageFileStream  
                    (filename, System.IO.FileMode.Open,isoStore);  
            System.IO.StreamReader reader = null;  
            try   
            {  
                reader = new System.IO.StreamReader(isos);  
  
                // Reads the values stored.  
                TypeConverter converter ;  
                converter = TypeDescriptor.GetConverter(typeof(Color));  
  
                this.MainButton.BackColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
                this.MainButton.ForeColor =   
                 (Color)(converter.ConvertFromString(reader.ReadLine()));  
  
                converter = TypeDescriptor.GetConverter(typeof(Font));  
                this.MainButton.Font =   
                  (Font)(converter.ConvertFromString(reader.ReadLine()));  
            }  
            catch (Exception ex)  
            {   
                System.Diagnostics.Debug.WriteLine  
                     ("Cannot read options " + ex.ToString());  
            }  
            finally  
            {  
                reader.Close();  
            }  
        }  
    }   
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot read options " + ex.ToString());  
    }  
}  
  
// Writes the button options to the isolated storage.  
public void Write()   
{  
    System.IO.IsolatedStorage.IsolatedStorageFile isoStore =   
        System.IO.IsolatedStorage.IsolatedStorageFile.  
        GetUserStoreForDomain();  
  
    string filename = "options.txt";  
    try   
    {  
        // Checks if the file exists and, if it does, tries to delete it.  
        if (isoStore.GetFileNames(filename).GetLength(0) != 0)   
        {  
            isoStore.DeleteFile(filename);  
        }  
    }  
    catch (Exception ex)   
    {  
        System.Diagnostics.Debug.WriteLine  
            ("Cannot delete file " + ex.ToString());  
    }  
  
    // Creates the options file and writes the button options to it.  
    System.IO.StreamWriter writer = null;  
    try   
    {  
        System.IO.IsolatedStorage.IsolatedStorageFileStream isos = new   
            System.IO.IsolatedStorage.IsolatedStorageFileStream(filename,   
            System.IO.FileMode.CreateNew,isoStore);  
  
        writer = new System.IO.StreamWriter(isos);  
        TypeConverter converter ;  
  
        converter = TypeDescriptor.GetConverter(typeof(Color));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.BackColor));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.ForeColor));  
  
        converter = TypeDescriptor.GetConverter(typeof(Font));  
        writer.WriteLine(converter.ConvertToString(  
            this.MainButton.Font));  
  
    }  
    catch (Exception ex)  
    {   
        System.Diagnostics.Debug.WriteLine  
           ("Cannot write options " + ex.ToString());  
    }  
    finally  
    {  
        writer.Close();  
    }  
}  
```  
  
## <a name="database-access"></a>Dostęp do bazy danych  
 Uprawnienia wymagane do uzyskania dostępu bazy danych różnią się zależnie od dostawcy bazy danych; jednak tylko te aplikacje, które działają z odpowiednimi uprawnieniami mogą uzyskać dostęp do bazy danych za pośrednictwem połączenia danych. Aby uzyskać więcej informacji na temat uprawnień, które są wymagane do dostępu do bazy danych, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../../docs/framework/data/adonet/code-access-security.md).  
  
 Jeśli nie można bezpośrednio dostęp do bazy danych, ponieważ chcesz, aby aplikację do uruchamiania w częściowej relacji zaufania, można użyć usługi sieci Web, jako alternatywę oznacza, że dostęp do danych. Usługi sieci Web to oprogramowanie, którego ma programowo dostęp za pośrednictwem sieci. Za pomocą usług sieci Web aplikacje mogą udostępniać dane w strefach grupy kodu. Domyślnie aplikacje w lokalny intranet i Internet strefy mają prawo dostępu do swoich witryn pochodzenia, który umożliwia wywoływanie usługi sieci Web hostowanych na tym samym serwerze. Aby uzyskać więcej informacji, zobacz [usług sieci Web w technologii ASP.NET AJAX](https://msdn.microsoft.com/library/8290e543-7eff-47a4-aace-681f3c07229b) lub [Windows Communication Foundation](https://msdn.microsoft.com/library/ms735119.aspx).  
  
## <a name="registry-access"></a>Dostęp do rejestru  
 <xref:System.Security.Permissions.RegistryPermission> Klasy kontroluje dostęp do rejestru systemu operacyjnego. Domyślnie tylko aplikacje, które działają lokalnie można uzyskać dostępu do rejestru.  <xref:System.Security.Permissions.RegistryPermission> przyznaje tylko aplikację po prawej stronie, aby spróbować dostępu do rejestru; go nie gwarantuje, że dostęp powiedzie się, ponieważ system operacyjny nadal wymusza zabezpieczeń w rejestrze.  
  
 Ponieważ nie można uzyskać dostępu do rejestru w częściowej relacji zaufania, konieczne może być znaleźć inne metody przechowywania danych. Gdy zapisujesz ustawienia aplikacji, należy użyć wydzielonej pamięci masowej zamiast rejestru. Wydzielona pamięć masowa może także służyć do przechowywania inne pliki specyficzne dla aplikacji. Można również przechowywać informacje globalnej aplikacji serwera lub witryny pochodzenia, ponieważ domyślnie aplikacja jest prawo do uzyskiwania dostępu do witryny pochodzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczniejsze drukowanie w formularzach Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Przegląd zabezpieczeń w formularzach Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Zabezpieczenia formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)  
 [Mage.exe (narzędzie generowania manifestu i edytowania)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
