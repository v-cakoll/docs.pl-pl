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
ms.openlocfilehash: 5db6fc886fe53fb60d38471bd463868ce2f37fc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541901"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Bezpieczniejszy dostęp do plików i danych w formularzach systemu Windows
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Używa uprawnień w celu ochrony zasobów i danych. Gdy aplikacja może odczytu lub zapisu danych zależy od uprawnienia do aplikacji. Po uruchomieniu aplikacji w środowisku częściowej relacji zaufania, może nie mieć dostępu do danych mogą też zmienić sposób dostępu do danych.  
  
 Gdy występują ograniczenia zabezpieczeń, dostępne są dwie opcje: assert uprawnień (przy założeniu udzielono aplikacji) lub użyj wersji funkcji zapisywane do pracy w częściowej relacji zaufania. W poniższych sekcjach omówiono sposób pracy z pliku bazy danych i dostępu do rejestru z aplikacji, które są uruchomione w środowisku częściowej relacji zaufania.  
  
> [!NOTE]
>  Domyślnie narzędzia, które generują [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] wdrożeń domyślne tych wdrożeń do żądania pełnego zaufania z komputerów, na których są uruchamiane. Jeśli zdecydujesz się korzystać z zalet zwiększyć bezpieczeństwo działa w częściowej relacji zaufania, należy zmienić to ustawienie domyślne w programie Visual Studio lub jednym z [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] narzędzia (Mage.exe lub MageUI.exe). Aby uzyskać więcej informacji o zabezpieczeniach formularzy systemu Windows i na jak określić poziom zaufania odpowiednie dla aplikacji, zobacz [zabezpieczeń w formularzach systemu Windows-omówienie](../../../docs/framework/winforms/security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Dostęp do plików  
 <xref:System.Security.Permissions.FileIOPermission> Klasy kontroli dostępu do plików i folderów w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Domyślnie system zabezpieczeń nie powoduje przyznania <xref:System.Security.Permissions.FileIOPermission> środowiskach częściowej relacji zaufania, takie jak strefach Internet i Lokalny intranet. Jednak aplikacja, która wymaga dostępu do plików mogą nadal działać w tych środowiskach, jeśli możesz zmodyfikować projekt aplikacji lub użyć różnych metod na dostęp do plików. Domyślnie lokalnej strefy intranetowej to prawo ma dostęp do tej samej witryny i tym samym dostęp do katalogu, do nawiązywania ponownego połączenia ze swoją witryną źródłową i do odczytu z jego katalogu instalacyjnego. Domyślnie strefy internetowej, jest tylko prawo do nawiązywania ponownego połączenia ze swoją witryną źródłową.  
  
### <a name="user-specified-files"></a>Pliki określone przez użytkownika  
 Jednym ze sposobów postępowania z nie ma dostępu do plików uprawnienie jest monitowanie użytkownika o podanie informacji określonego pliku przy użyciu <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> klasy. Interakcji z użytkownikiem pomaga zapewnić niektórych aplikacji nie złośliwe ładować pliki prywatne lub zastąpić ważnych plików. <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> i <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody udostępniają uprawnienia odczytu i zapisu plików, otwierając strumienia pliku dla pliku, określonej przez użytkownika. Metody również chronić pliku użytkownika przesłaniania ścieżki pliku.  
  
> [!NOTE]
>  Te uprawnienia są różne w zależności od tego, czy aplikacja jest w strefie Internet lub strefy intranetowej. Aplikacje internetowe strefy można używać tylko <xref:System.Windows.Forms.OpenFileDialog>, podczas gdy aplikacje intranetowe mają nieograniczony pliku okna dialogowego uprawnień.  
  
 <xref:System.Security.Permissions.FileDialogPermission> Klasa określa, jaki typ pliku — okno dialogowe, aplikacja może używać. W poniższej tabeli przedstawiono wartości musi mieć używania każdego <xref:System.Windows.Forms.FileDialog> klasy.  
  
|Class|Wartość wymagany dostęp|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  Określone uprawnienie nie jest wymagana do <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> faktycznie jest wywoływana metoda.  
  
 Uprawnienia, aby wyświetlić okno dialogowe pliku nie powoduje przyznania Twojej aplikacji pełny dostęp do wszystkich członków <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, i <xref:System.Windows.Forms.SaveFileDialog> klasy. Dokładne uprawnienia, które są wymagane do każdej metody wywołania można znaleźć w temacie dotyczącym tej metody w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] biblioteka dokumentacji klasy.  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę otwierania pliku określonego przez użytkownika do <xref:System.Windows.Forms.RichTextBox> formantu. Przykład wymaga <xref:System.Security.Permissions.FileDialogPermission> oraz skojarzonych z nimi <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> wartości wyliczenia. W przykładzie pokazano sposób obsługi <xref:System.Security.SecurityException> ustalenie, czy zapisywanie funkcji powinny być wyłączone. W tym przykładzie wymaga, aby Twoje <xref:System.Windows.Forms.Form> ma <xref:System.Windows.Forms.Button> formantu o nazwie `ButtonOpen`, a <xref:System.Windows.Forms.RichTextBox> formantu o nazwie `RtfBoxMain`.  
  
> [!NOTE]
>  Logika programowania zapisywania funkcji nie pokazano w przykładzie.  
  
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
>  W środowisku Visual C#, upewnij się, że należy dodać kodu w celu włączenia obsługi zdarzeń. Przy użyciu kodu z poprzedniego przykładu, poniższy kod przedstawia sposób włączania obsługi zdarzeń.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Inne pliki  
 Czasami należy do odczytu lub zapisu do plików, że użytkownik nie określi, np. gdy muszą zostać zachowane ustawienia aplikacji. W strefach Internet i Lokalny intranet aplikacji nie ma uprawnień do przechowywania danych w pliku lokalnym. Jednak aplikacja będzie do przechowywania danych w magazynie izolowanym. Izolowany magazyn jest przedział danych abstrakcyjny (nie lokalizację przechowywania określonych), zawierający pliki izolowanych magazynów, nazywany magazynów, zawierające lokalizacje katalogowych, których są przechowywane dane. Uprawnienia dostępu, takich jak plików <xref:System.Security.Permissions.FileIOPermission> nie są wymagane; zamiast tego <xref:System.Security.Permissions.IsolatedStoragePermission> klasa steruje uprawnienia dla izolowanego magazynu. Domyślnie aplikacje, które są uruchomione w strefach Internet i Lokalny intranet mogą przechowywać dane przy użyciu izolowanego magazynu; jednak można wybrać różne ustawienia, takie jak przydział dysku. Aby uzyskać więcej informacji na temat izolowane magazynu, zobacz [izolowanych magazynów](../../../docs/standard/io/isolated-storage.md).  
  
 W poniższym przykładzie użyto izolowanych magazynów można zapisać danych do pliku znajdującego się w magazynie. Przykład wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> i <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> wartość wyliczenia. W przykładzie pokazano, odczytywanie i zapisywanie niektórych wartości właściwości <xref:System.Windows.Forms.Button> formantu w pliku w magazynie izolowanym. `Read` Funkcja może zostać wywołana po uruchomieniu aplikacji i `Write` funkcja może zostać wywołana przed zakończeniem aplikacji. Przykład wymaga, aby `Read` i `Write` funkcje istnieje jako elementy członkowskie <xref:System.Windows.Forms.Form> zawierający <xref:System.Windows.Forms.Button> formantu o nazwie `MainButton`.  
  
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
 Uprawnienia wymagane do uzyskania dostępu bazy danych różnić w zależności od dostawcy bazy danych; jednak tylko te aplikacje, które działają z odpowiednimi uprawnieniami można uzyskać dostępu do bazy danych za pośrednictwem połączenia danych. Aby uzyskać więcej informacji dotyczących uprawnień, które są wymagane do uzyskania dostępu bazy danych, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../../../docs/framework/data/adonet/code-access-security.md).  
  
 Jeśli nie można bezpośrednio dostęp do bazy danych, ponieważ ma aplikację do uruchamiania w częściowej relacji zaufania, można użyć usługi sieci Web jako alternatywę oznacza dostępu do danych. Usługi sieci Web jest to oprogramowanie, które mogą uzyskiwać programowo za pośrednictwem sieci. Z usługami sieci Web aplikacje mogą udostępniać dane w różnych strefach grupy kodu. Domyślnie aplikacje w strefach Internet i Lokalny intranet mają prawo dostępu do swoich witryn pochodzenia, co umożliwia ich do wywoływania usługi sieci Web hostowanych na tym samym serwerze. Aby uzyskać więcej informacji, zobacz [usług sieci Web w technologii ASP.NET AJAX](http://msdn.microsoft.com/library/8290e543-7eff-47a4-aace-681f3c07229b) lub [Windows Communication Foundation](http://msdn.microsoft.com/library/ms735119.aspx).  
  
## <a name="registry-access"></a>Dostęp do rejestru  
 <xref:System.Security.Permissions.RegistryPermission> Klasy kontroluje dostęp do rejestru systemu operacyjnego. Domyślnie tylko uruchomione lokalnie aplikacje mogą uzyskać dostępu do rejestru.  <xref:System.Security.Permissions.RegistryPermission> tylko daje aplikacji prawo próby dostępu do rejestru; go nie gwarantuje, że dostęp powiedzie się, ponieważ system operacyjny nadal wymusza zabezpieczeń do rejestru.  
  
 Ponieważ nie można uzyskać dostępu do rejestru w częściowej relacji zaufania, konieczne może być znaleźć inne metody przechowywania danych. Po zapisaniu ustawień aplikacji należy używać izolowanego magazynu, zamiast rejestru. Izolowany magazyn mogą służyć do przechowywania plików innych aplikacji. Można również przechowywać informacje o aplikacji globalnego dotyczące serwera lub witryny pochodzenia, ponieważ domyślnie aplikacja jest uprawnień dostępu do witryny ze swoją witryną źródłową.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczniejsze drukowanie w formularzach Windows Forms](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 [Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 [Przegląd zabezpieczeń w formularzach Windows Forms](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 [Zabezpieczenia formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-security.md)  
 [Mage.exe (narzędzie generowania manifestu i edytowania)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)  
 [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
