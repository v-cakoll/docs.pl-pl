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
ms.openlocfilehash: 94b165757de636b2570798a21fd7c483264e37c5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949951"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Bezpieczniejszy dostęp do plików i danych w formularzach systemu Windows
.NET Framework używa uprawnień do ochrony zasobów i danych. Miejsce, w którym aplikacja może odczytywać lub zapisywać dane, zależy od uprawnień przyznanych aplikacji. Gdy aplikacja jest uruchamiana w środowisku częściowej relacji zaufania, może nie mieć dostępu do danych lub może zajść konieczność zmiany sposobu uzyskiwania dostępu do danych.  
  
 W przypadku wystąpienia ograniczenia zabezpieczeń są dostępne dwie opcje: Potwierdź uprawnienie (przy założeniu, że zostało ono przyznane aplikacji) lub użyj wersji funkcji zapisaną do pracy w częściowej relacji zaufania. W poniższych sekcjach omówiono sposób pracy z dostępem do plików, baz danych i rejestrów z aplikacji, które działają w środowisku częściowej relacji zaufania.  
  
> [!NOTE]
> Domyślnie narzędzia generujące wdrożenia ClickOnce domyślnie wdrażają te wdrożenia w celu żądania pełnego zaufania z komputerów, na których te komputery są uruchamiane. Jeśli zdecydujesz, że chcesz mieć dodatkowe korzyści z używania programu w częściowej relacji zaufania, musisz zmienić to ustawienie domyślne w Visual Studio lub jednym z narzędzi Windows SDK (Mage. exe lub MageUI. exe). Aby uzyskać więcej informacji o zabezpieczeniach Windows Forms i sposobach określania odpowiedniego poziomu zaufania dla aplikacji, zobacz [zabezpieczenia w Windows Forms Omówienie](security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Dostęp do plików  
 <xref:System.Security.Permissions.FileIOPermission> Klasa kontroluje dostęp do plików i folderów w .NET Framework. Domyślnie system zabezpieczeń nie przyznaje do częściowych środowisk <xref:System.Security.Permissions.FileIOPermission> zaufania, takich jak lokalny intranet i strefy internetowe. Jednak aplikacja wymagająca dostępu do plików może nadal działać w tych środowiskach w przypadku modyfikacji projektu aplikacji lub do uzyskiwania dostępu do plików za pomocą różnych metod. Domyślnie lokalna strefa intranetowa ma dostęp do tego samego dostępu do lokacji i tego samego dostępu do katalogu, aby można było połączyć się z powrotem z lokacją jego pochodzenia i odczytać z katalogu instalacyjnego. Domyślnie strefa Internet ma przyznane prawo do nawiązywania połączenia z witryną źródłową.  
  
### <a name="user-specified-files"></a>Pliki określone przez użytkownika  
 Jednym ze sposobów postępowania z brakiem uprawnień dostępu do plików jest wyświetlenie monitu o podanie określonych informacji o pliku przy <xref:System.Windows.Forms.OpenFileDialog> użyciu <xref:System.Windows.Forms.SaveFileDialog> klasy lub. Ta interakcja użytkownika pomaga zapewnić pewne gwarancje, że aplikacja nie może złośliwie ładować prywatnych plików ani zastępować ważnych plików. Metody <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> i<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> zapewniają dostęp do odczytu i zapisu, otwierając strumień plików dla pliku określonego przez użytkownika. Metody pomagają również chronić plik użytkownika przez zaciemnienie ścieżki pliku.  
  
> [!NOTE]
> Te uprawnienia różnią się w zależności od tego, czy aplikacja znajduje się w strefie Internet czy intranet. Aplikacje strefy internetowej mogą korzystać tylko z <xref:System.Windows.Forms.OpenFileDialog>, natomiast aplikacje intranetowe mają uprawnienia do okna dialogowego nieograniczonego pliku.  
  
 <xref:System.Security.Permissions.FileDialogPermission> Klasa określa typ okna dialogowego, który może być używany przez aplikację. W poniższej tabeli przedstawiono wartość, którą trzeba wykonać, aby użyć <xref:System.Windows.Forms.FileDialog> każdej klasy.  
  
|Class|Wymagana wartość dostępu|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> Nie żąda się określonego uprawnienia, dopóki <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> Metoda nie zostanie faktycznie wywołana.  
  
 Uprawnienie do wyświetlania pliku okno dialogowe nie przyznaje aplikacji pełnego dostępu do wszystkich elementów członkowskich <xref:System.Windows.Forms.FileDialog>klas, <xref:System.Windows.Forms.OpenFileDialog>i <xref:System.Windows.Forms.SaveFileDialog> . Aby uzyskać dokładne uprawnienia, które są wymagane do wywołania każdej metody, zobacz temat referencyjny dla tej metody w dokumentacji biblioteki klas .NET Framework.  
  
 Poniższy przykład kodu używa <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metody do otwierania pliku określonego przez użytkownika <xref:System.Windows.Forms.RichTextBox> w kontrolce. Przykład wymaga <xref:System.Security.Permissions.FileDialogPermission> i skojarzonej <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> wartości wyliczenia. W przykładzie pokazano, jak obsłużyć, <xref:System.Security.SecurityException> aby określić, czy funkcja Save powinna być wyłączona. Ten przykład wymaga, aby <xref:System.Windows.Forms.Form> <xref:System.Windows.Forms.Button> miało <xref:System.Windows.Forms.RichTextBox> kontrolkę `ButtonOpen`o nazwie i kontrolkę `RtfBoxMain`o nazwie.  
  
> [!NOTE]
> W przykładzie nie pokazano logiki programowania dla funkcji Zapisz.  
  
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
> W programie C#Visual należy dodać kod, aby włączyć obsługę zdarzeń. Używając kodu z poprzedniego przykładu, poniższy kod pokazuje, jak włączyć obsługę zdarzeń.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Inne pliki  
 Czasami konieczne jest odczytanie lub zapisanie plików, które nie są określone przez użytkownika, na przykład w przypadku konieczności utrwalania ustawień aplikacji. W lokalnym intranecie i strefach internetowych aplikacja nie będzie miała uprawnienia do przechowywania danych w pliku lokalnym. Jednak aplikacja będzie mogła przechowywać dane w izolowanym magazynie. Magazyn izolowany jest abstrakcyjnym przedziałem danych (nie konkretną lokalizacją przechowywania), który zawiera jeden lub więcej izolowanych plików magazynu o nazwie Stores, które zawierają rzeczywiste lokalizacje katalogów, w których są przechowywane dane. Uprawnienia dostępu do plików <xref:System.Security.Permissions.FileIOPermission> , takie jak nie są wymagane; <xref:System.Security.Permissions.IsolatedStoragePermission> zamiast tego Klasa kontroluje uprawnienia do magazynu izolowanego. Domyślnie aplikacje działające w lokalnym intranecie i strefach internetowych mogą przechowywać dane przy użyciu magazynu izolowanego. Jednak ustawienia takie jak przydział dysku mogą się różnić. Aby uzyskać więcej informacji na temat izolowanego magazynu, zobacz [izolowany magazyn](../../standard/io/isolated-storage.md).  
  
 Poniższy przykład używa wydzielonej pamięci masowej do zapisywania danych do pliku znajdującego się w sklepie. Przykład wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> i wartość wyliczenia. W przykładzie pokazano odczytywanie i zapisywanie określonych wartości <xref:System.Windows.Forms.Button> właściwości kontrolki do pliku w magazynie izolowanym. Funkcja zostałaby wywołana po uruchomieniu aplikacji `Write` , a funkcja zostałaby wywołana przed zakończeniem działania aplikacji. `Read` Przykład wymaga, aby `Read` funkcje i `Write` <xref:System.Windows.Forms.Form> istniały jako elementy członkowskie obiektu, który zawiera <xref:System.Windows.Forms.Button> kontrolkę `MainButton`o nazwie.  
  
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
 Uprawnienia wymagane do uzyskania dostępu do bazy danych różnią się w zależności od dostawcy bazy danych. jednak tylko aplikacje z odpowiednimi uprawnieniami mogą uzyskiwać dostęp do bazy danych za pomocą połączenia danych. Aby uzyskać więcej informacji o uprawnieniach, które są wymagane do uzyskania dostępu do bazy danych, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../data/adonet/code-access-security.md).  
  
 Jeśli nie możesz uzyskać bezpośredniego dostępu do bazy danych, ponieważ aplikacja ma działać w częściowej relacji zaufania, możesz użyć usługi sieci Web jako alternatywnej metody dostępu do danych. Usługa sieci Web to oprogramowanie, które można programowo uzyskać dostęp za pośrednictwem sieci. Dzięki usługom sieci Web aplikacje mogą udostępniać dane między strefami grup kodu. Domyślnie aplikacje w lokalnym intranecie i strefach internetowych uzyskują prawo dostępu do swoich witryn pochodzenia, co umożliwia im Wywoływanie usługi sieci Web hostowanej na tym samym serwerze. Aby uzyskać więcej informacji, zobacz [usługi sieci Web w ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) lub [Windows Communication Foundation](../wcf/index.md).  
  
## <a name="registry-access"></a>Dostęp do rejestru  
 <xref:System.Security.Permissions.RegistryPermission> Klasa kontroluje dostęp do rejestru systemu operacyjnego. Domyślnie tylko aplikacje, które są uruchomione lokalnie, mogą uzyskać dostęp do rejestru.  <xref:System.Security.Permissions.RegistryPermission>przyznaje aplikacji prawo do wypróbowania dostępu do rejestru; nie gwarantuje to, że dostęp powiedzie się, ponieważ system operacyjny nadal wymusza zabezpieczenia rejestru.  
  
 Ponieważ nie można uzyskać dostępu do rejestru w ramach częściowej relacji zaufania, może być konieczne znalezienie innych metod przechowywania danych. Podczas przechowywania ustawień aplikacji należy użyć izolowanego magazynu zamiast rejestru. Magazyn izolowany może być również używany do przechowywania innych plików specyficznych dla aplikacji. Możesz również przechowywać globalne informacje o aplikacji dotyczące serwera lub lokacji pochodzenia, ponieważ domyślnie aplikacja otrzymuje prawo dostępu do witryny jego pochodzenia.  
  
## <a name="see-also"></a>Zobacz także

- [Bezpieczniejsze drukowanie w formularzach Windows Forms](more-secure-printing-in-windows-forms.md)
- [Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Przegląd zabezpieczeń w formularzach Windows Forms](security-in-windows-forms-overview.md)
- [Zabezpieczenia formularzy Windows Forms](windows-forms-security.md)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
