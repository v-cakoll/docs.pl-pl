---
title: Bezpieczniejszy dostęp do plików i danych
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
ms.openlocfilehash: a29c2f7137440e64fbf8095f77d5d10d0505bc2d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185901"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a>Bezpieczniejszy dostęp do plików i danych w formularzach systemu Windows
Program .NET Framework używa uprawnień do ochrony zasobów i danych. Gdzie aplikacja może odczytywać lub zapisywać dane zależy od uprawnień przyznanych aplikacji. Gdy aplikacja działa w środowisku częściowego zaufania, może nie mieć dostępu do danych lub może być konieczna zmiana sposobu uzyskiwania dostępu do danych.  
  
 Po napotkaniu ograniczenia zabezpieczeń, masz dwie opcje: potwierdzić uprawnienie (przy założeniu, że została przyznana do aplikacji) lub użyć wersji funkcji napisane do pracy w częściowym zaufaniu. W poniższych sekcjach omówiono sposób pracy z dostępem do plików, bazy danych i rejestru z aplikacji, które są uruchomione w środowisku częściowego zaufania.  
  
> [!NOTE]
> Domyślnie narzędzia, które generują clickonce wdrożeń domyślnie tych wdrożeń do żądania pełnego zaufania z komputerów, na których są uruchamiane. Jeśli zdecydujesz, że chcesz dodać korzyści zabezpieczeń z uruchamiania w częściowym zaufaniu, należy zmienić to ustawienie domyślne w programie Visual Studio lub jednym z narzędzi zestawu Windows SDK (Mage.exe lub MageUI.exe). Aby uzyskać więcej informacji na temat zabezpieczeń formularzy systemu Windows i sposobu określania odpowiedniego poziomu zaufania dla aplikacji, zobacz [Omówienie zabezpieczeń w formularzach systemu Windows](security-in-windows-forms-overview.md).  
  
## <a name="file-access"></a>Dostęp do plików  
 Klasa <xref:System.Security.Permissions.FileIOPermission> steruje dostępem do plików i folderów w programie .NET Framework. Domyślnie system zabezpieczeń nie udziela <xref:System.Security.Permissions.FileIOPermission> częściowych środowisk zaufania, takich jak lokalny intranet i strefy internetowe. Jednak aplikacja, która wymaga dostępu do plików, może nadal działać w tych środowiskach, jeśli zmodyfikujesz projekt aplikacji lub użyjesz różnych metod dostępu do plików. Domyślnie lokalnej strefie intranetowej przyznaje się prawo do tego samego dostępu do lokacji i tego samego dostępu do katalogu, do łączenia się z lokacją pochodzenia i odczytu z katalogu instalacyjnego. Domyślnie strefa internetowa ma przyznane tylko prawo do łączenia się z powrotem do witryny pochodzenia.  
  
### <a name="user-specified-files"></a>Pliki określone przez użytkownika  
 Jednym ze sposobów radzenia sobie z nie mając uprawnienia dostępu do <xref:System.Windows.Forms.OpenFileDialog> pliku <xref:System.Windows.Forms.SaveFileDialog> jest monitowanie użytkownika o podanie określonych informacji o pliku przy użyciu lub klasy. Ta interakcja z użytkownikiem pomaga zapewnić pewną pewność, że aplikacja nie może złośliwie załadować plików prywatnych lub zastąpić ważnych plików. Metody <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> i zapewniają dostęp do plików odczytu i zapisu, otwierając strumień plików dla pliku określonego przez użytkownika. Metody pomagają również chronić plik użytkownika, zasłaniając ścieżkę pliku.  
  
> [!NOTE]
> Uprawnienia te różnią się w zależności od tego, czy aplikacja znajduje się w strefie Internet lub w intranecie. Aplikacje strefy internetowej <xref:System.Windows.Forms.OpenFileDialog>mogą używać tylko aplikacji intranetowych, podczas gdy aplikacje intranetowe mają nieograniczone uprawnienia do okna dialogowego plików.  
  
 Klasa <xref:System.Security.Permissions.FileDialogPermission> określa, jakiego typu okna dialogowego pliku może używać aplikacja. W poniższej tabeli przedstawiono wartość, która musi być używana dla każdej <xref:System.Windows.Forms.FileDialog> klasy.  
  
|Klasa|Wymagana wartość dostępu|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
> Określone uprawnienie nie jest <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> wymagane, dopóki metoda jest faktycznie wywoływana.  
  
 Uprawnienie do wyświetlania okna dialogowego pliku nie zapewnia <xref:System.Windows.Forms.FileDialog>aplikacji <xref:System.Windows.Forms.OpenFileDialog>pełnego <xref:System.Windows.Forms.SaveFileDialog> dostępu do wszystkich członków programu , i klas. Aby uzyskać dokładne uprawnienia, które są wymagane do wywołania każdej metody, zobacz temat odwołania dla tej metody w dokumentacji biblioteki klas .NET Framework.  
  
 Poniższy przykład kodu <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> używa metody, aby otworzyć plik <xref:System.Windows.Forms.RichTextBox> określony przez użytkownika do formantu. Przykład wymaga <xref:System.Security.Permissions.FileDialogPermission> i skojarzonej wartości wyliczenia. <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> W przykładzie pokazano, <xref:System.Security.SecurityException> jak obsługiwać, aby ustalić, czy funkcja zapisywania powinna być wyłączona. W tym przykładzie <xref:System.Windows.Forms.Button> wymaga, `ButtonOpen`aby <xref:System.Windows.Forms.RichTextBox> formant `RtfBoxMain` <xref:System.Windows.Forms.Form> o nazwie i formancie o nazwie .  
  
> [!NOTE]
> Logika programowania dla funkcji zapisywania nie jest wyświetlana w przykładzie.  
  
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
> W języku Visual C#upewnij się, że dodasz kod, aby włączyć program obsługi zdarzeń. Za pomocą kodu z poprzedniego przykładu, poniższy kod pokazuje, jak włączyć program obsługi zdarzeń.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`  
  
### <a name="other-files"></a>Inne pliki  
 Czasami trzeba będzie odczytać lub zapisać do plików, które użytkownik nie określa, takich jak kiedy należy utrwalić ustawienia aplikacji. W lokalnym intranecie i strefach internetowych aplikacja nie będzie miała uprawnień do przechowywania danych w pliku lokalnym. Jednak aplikacja będzie mogła przechowywać dane w izolowanym magazynie. Magazyn izolowany to abstrakcyjny przedział danych (nie określona lokalizacja magazynu), który zawiera jeden lub więcej izolowanych plików magazynu, nazywanych magazynami, które zawierają rzeczywiste lokalizacje katalogów, w których przechowywane są dane. Uprawnienia dostępu do <xref:System.Security.Permissions.FileIOPermission> plików, takie jak nie są wymagane; Zamiast tego <xref:System.Security.Permissions.IsolatedStoragePermission> klasa kontroluje uprawnienia do izolowanego magazynu. Domyślnie aplikacje uruchomione w lokalnym intranecie i strefach internetowych mogą przechowywać dane przy użyciu magazynu izolowanego; jednak ustawienia, takie jak przydział dysku, mogą się różnić. Aby uzyskać więcej informacji na temat magazynu izolowanego, zobacz [Magazyn izolowany](../../standard/io/isolated-storage.md).  
  
 W poniższym przykładzie użyto magazynu izolowanego do zapisywania danych w pliku znajdującym się w magazynie. Przykład wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> i <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> wartość wyliczenia. W przykładzie pokazano odczytu i <xref:System.Windows.Forms.Button> zapisu niektórych wartości właściwości formantu do pliku w izolowanym magazynie. Funkcja `Read` zostanie wywołana po uruchomieniu aplikacji `Write` i funkcja zostanie wywołana przed zakończeniem aplikacji. Przykład wymaga, `Read` aby `Write` i funkcje <xref:System.Windows.Forms.Form> istnieją jako <xref:System.Windows.Forms.Button> elementy `MainButton`członkowskie formantu o nazwie .  
  
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
 Uprawnienia wymagane do uzyskania dostępu do bazy danych różnią się w zależności od dostawcy bazy danych; jednak tylko aplikacje, które są uruchomione z odpowiednimi uprawnieniami można uzyskać dostęp do bazy danych za pośrednictwem połączenia danych. Aby uzyskać więcej informacji na temat uprawnień wymaganych do uzyskania dostępu do bazy danych, zobacz [Zabezpieczenia dostępu do kodu i ADO.NET](../data/adonet/code-access-security.md).  
  
 Jeśli nie można bezpośrednio uzyskać dostępu do bazy danych, ponieważ aplikacja ma być uruchamiana w częściowym zaufaniu, można użyć usługi sieci Web jako alternatywnego środka dostępu do danych. Usługa sieci Web to oprogramowanie, do które można uzyskać dostęp programowo za pośrednictwem sieci. Dzięki usługom sieci Web aplikacje mogą udostępniać dane w strefach grup kodu. Domyślnie aplikacjom w lokalnym intranecie i strefach internetowych przyznaje się prawo dostępu do swoich witryn pochodzenia, co umożliwia im wywołanie usługi sieci Web hostowanego na tym samym serwerze. Aby uzyskać więcej informacji, zobacz [Usługi sieci Web w ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) lub Windows Communication [Foundation](../wcf/index.md).  
  
## <a name="registry-access"></a>Dostęp do rejestru  
 Klasa <xref:System.Security.Permissions.RegistryPermission> kontroluje dostęp do rejestru systemu operacyjnego. Domyślnie tylko aplikacje, które są uruchomione lokalnie, mogą uzyskiwać dostęp do rejestru.  <xref:System.Security.Permissions.RegistryPermission>tylko przyznaje aplikacji prawo do wypróbowania dostępu do rejestru; nie gwarantuje, że dostęp zakończy się pomyślnie, ponieważ system operacyjny nadal wymusza zabezpieczenia w rejestrze.  
  
 Ponieważ nie można uzyskać dostępu do rejestru w ramach częściowego zaufania, może być konieczne znalezienie innych metod przechowywania danych. Podczas przechowywania ustawień aplikacji należy używać magazynu izolowanego zamiast rejestru. Izolowany magazyn może również służyć do przechowywania innych plików specyficznych dla aplikacji. Można również przechowywać informacje o aplikacji globalnej o serwerze lub witrynie pochodzenia, ponieważ domyślnie aplikacja ma prawo dostępu do witryny pochodzenia.  
  
## <a name="see-also"></a>Zobacz też

- [Bezpieczniejsze drukowanie w formularzach systemu Windows](more-secure-printing-in-windows-forms.md)
- [Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms](additional-security-considerations-in-windows-forms.md)
- [Przegląd zabezpieczeń w formularzach Windows Forms](security-in-windows-forms-overview.md)
- [Zabezpieczenia formularzy systemu Windows](windows-forms-security.md)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
