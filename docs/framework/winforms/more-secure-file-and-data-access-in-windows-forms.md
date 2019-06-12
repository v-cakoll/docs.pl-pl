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
ms.openlocfilehash: c804a0a751969377c292613fdae8cc19b266ffa9
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834059"
---
# <a name="more-secure-file-and-data-access-in-windows-forms"></a><span data-ttu-id="bb1d0-102">Bezpieczniejszy dostęp do plików i danych w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bb1d0-102">More Secure File and Data Access in Windows Forms</span></span>
<span data-ttu-id="bb1d0-103">.NET Framework używa uprawnień w celu ochrony zasobów i danych.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-103">The .NET Framework uses permissions to help protect resources and data.</span></span> <span data-ttu-id="bb1d0-104">Gdzie aplikacji może odczytać lub zapisać danych zależy od uprawnienia nadane aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-104">Where your application can read or write data depends on the permissions granted to the application.</span></span> <span data-ttu-id="bb1d0-105">Po uruchomieniu aplikacji w środowisku częściowej relacji zaufania, może nie mieć dostępu do danych lub może być zmienić sposób dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-105">When your application runs in a partial trust environment, you might not have access to your data or you might have to change the way you access the data.</span></span>  
  
 <span data-ttu-id="bb1d0-106">Gdy występują ograniczenia zabezpieczeń, masz dwie opcje: asercja uprawnień (przy założeniu, zostanie przyznany aplikacji) lub korzystania z wersji funkcji zapisywane do pracy w trybie częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-106">When you encounter a security restriction, you have two options: assert the permission (assuming it has been granted to your application), or use a version of the feature written to work in partial trust.</span></span> <span data-ttu-id="bb1d0-107">W poniższych sekcjach omówiono sposób pracy z pliku, bazy danych i dostęp do rejestru z aplikacji, które są uruchomione w środowisku częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-107">The following sections discuss how to work with file, database, and registry access from applications that are running in a partial trust environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb1d0-108">Domyślnie, narzędzia, które generują [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] wdrożeń domyślnie wdrożeń żądania pełne zaufanie z komputerów, na których działają.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-108">By default, tools that generate [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] deployments default these deployments to requesting Full Trust from the computers on which they run.</span></span> <span data-ttu-id="bb1d0-109">Jeśli zdecydujesz, że chcesz, aby zwiększyć bezpieczeństwo zalet działających w częściowej relacji zaufania, należy zmienić to ustawienie domyślne w programie Visual Studio lub jednym z narzędzi Windows Software Development Kit (SDK) (Mage.exe lub MageUI.exe).</span><span class="sxs-lookup"><span data-stu-id="bb1d0-109">If you decide you want the added security benefits of running in partial trust, you must change this default in either Visual Studio or one of the Windows Software Development Kit (SDK) tools (Mage.exe or MageUI.exe).</span></span> <span data-ttu-id="bb1d0-110">Aby uzyskać więcej informacji o zabezpieczeniach Windows Forms i na temat sposobu określenia odpowiedniego poziomu zaufania dla aplikacji, zobacz [zabezpieczeń w Windows Forms — omówienie](security-in-windows-forms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bb1d0-110">For more information about Windows Forms security, and on how to determine the appropriate trust level for your application, see [Security in Windows Forms Overview](security-in-windows-forms-overview.md).</span></span>  
  
## <a name="file-access"></a><span data-ttu-id="bb1d0-111">Dostęp do plików</span><span class="sxs-lookup"><span data-stu-id="bb1d0-111">File Access</span></span>  
 <span data-ttu-id="bb1d0-112"><xref:System.Security.Permissions.FileIOPermission> Klasy kontroli dostępu do plików i folderów w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-112">The <xref:System.Security.Permissions.FileIOPermission> class controls file and folder access in the .NET Framework.</span></span> <span data-ttu-id="bb1d0-113">Domyślnie system zabezpieczeń nie powoduje przyznania <xref:System.Security.Permissions.FileIOPermission> środowiskach częściowej relacji zaufania, takich jak lokalny intranet i stref internetowych.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-113">By default, the security system does not grant the <xref:System.Security.Permissions.FileIOPermission> to partial trust environments such as the local intranet and Internet zones.</span></span> <span data-ttu-id="bb1d0-114">Jednak aplikacja, która wymaga dostępu do plików mogą nadal działać w tych środowiskach, jeśli zmodyfikować projekt aplikacji, lub uzyskiwania dostępu do plików za pomocą różnych metod.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-114">However, an application that requires file access can still function in these environments if you modify the design of your application or use different methods to access files.</span></span> <span data-ttu-id="bb1d0-115">Domyślnie strefy Lokalny intranet jest prawo do tego samego dostępu do witryn i tego samego dostępu do katalogów, do łączenia z powrotem do witryny pochodzenia i odczytać z jego katalogu instalacji.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-115">By default, the local intranet zone is granted the right to have same site access and same directory access, to connect back to the site of its origin, and to read from its installation directory.</span></span> <span data-ttu-id="bb1d0-116">Domyślnie strefy Internet jest tylko prawo do łączenia z powrotem do witryny pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-116">By default, the Internet zone, is only granted the right to connect back to the site of its origin.</span></span>  
  
### <a name="user-specified-files"></a><span data-ttu-id="bb1d0-117">Pliki określone przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="bb1d0-117">User-Specified Files</span></span>  
 <span data-ttu-id="bb1d0-118">Jednym ze sposobów, aby poradzić sobie z nie mają dostępu do pliku uprawnień jest aby monitować użytkownika o podanie informacji o pliku określonego za pomocą <xref:System.Windows.Forms.OpenFileDialog> lub <xref:System.Windows.Forms.SaveFileDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-118">One way to deal with not having file access permission is to prompt the user to provide specific file information by using the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> class.</span></span> <span data-ttu-id="bb1d0-119">Ta interakcja użytkownika pomaga zapewnić niektórych aplikacji nie złośliwie ładować pliki prywatne lub zastąpić ważnych plików.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-119">This user interaction helps provide some assurance that the application cannot maliciously load private files or overwrite important files.</span></span> <span data-ttu-id="bb1d0-120"><xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> i <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody zapewniają uprawnienia odczytu i zapisu plików, otwierając strumienia pliku dla pliku, określonej przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-120">The <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> and <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> methods provide read and write file access by opening the file stream for the file that the user specified.</span></span> <span data-ttu-id="bb1d0-121">Te metody także chronić pliku użytkownika przesłaniania ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-121">The methods also help protect the user's file by obscuring the file's path.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb1d0-122">Uprawnienia te różnią się w zależności od tego, czy aplikacja jest w strefie Internet lub strefy intranetowej.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-122">These permissions differ depending on whether your application is in the Internet zone or Intranet zone.</span></span> <span data-ttu-id="bb1d0-123">Można używać tylko aplikacji do strefy Internet <xref:System.Windows.Forms.OpenFileDialog>, podczas gdy aplikacji intranetowych mają nieograniczony uprawnień okna dialogowego do pliku.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-123">Internet zone applications can only use the <xref:System.Windows.Forms.OpenFileDialog>, whereas Intranet applications have unrestricted file dialog permission.</span></span>  
  
 <span data-ttu-id="bb1d0-124"><xref:System.Security.Permissions.FileDialogPermission> Klasa określa, jakiego rodzaju okno dialogowe pliku można użyć w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-124">The <xref:System.Security.Permissions.FileDialogPermission> class specifies what type of file dialog box your application can use.</span></span> <span data-ttu-id="bb1d0-125">W poniższej tabeli przedstawiono wartości potrzebne do używania każdego <xref:System.Windows.Forms.FileDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-125">The following table shows the value you must have to use each <xref:System.Windows.Forms.FileDialog> class.</span></span>  
  
|<span data-ttu-id="bb1d0-126">Class</span><span class="sxs-lookup"><span data-stu-id="bb1d0-126">Class</span></span>|<span data-ttu-id="bb1d0-127">Wartość wymaganego dostępu</span><span class="sxs-lookup"><span data-stu-id="bb1d0-127">Required access value</span></span>|  
|-----------|---------------------------|  
|<xref:System.Windows.Forms.OpenFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Open>|  
|<xref:System.Windows.Forms.SaveFileDialog>|<xref:System.Security.Permissions.FileDialogPermissionAccess.Save>|  
  
> [!NOTE]
>  <span data-ttu-id="bb1d0-128">Określone uprawnienie nie jest wymagana do momentu <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> faktycznie jest wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-128">The specific permission is not requested until the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method is actually called.</span></span>  
  
 <span data-ttu-id="bb1d0-129">Uprawnienia, aby wyświetlić okno dialogowe pliku nie przyznaje Twojej aplikacji uzyskanie pełnego dostępu do wszystkich członków <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, i <xref:System.Windows.Forms.SaveFileDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-129">Permission to display a file dialog box does not grant your application full access to all members of the <xref:System.Windows.Forms.FileDialog>, <xref:System.Windows.Forms.OpenFileDialog>, and <xref:System.Windows.Forms.SaveFileDialog> classes.</span></span> <span data-ttu-id="bb1d0-130">Uprawnienia, które są wymagane do wywołania każdej metody w temacie odwołania dla tej metody w dokumentacji biblioteki klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-130">For the exact permissions that are required to call each method, see the reference topic for that method in the .NET Framework class library documentation.</span></span>  
  
 <span data-ttu-id="bb1d0-131">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby otworzyć plik określony przez użytkownika do <xref:System.Windows.Forms.RichTextBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-131">The following code example uses the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open a user-specified file into a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="bb1d0-132">Przykład wymaga <xref:System.Security.Permissions.FileDialogPermission> oraz skojarzonych z nimi <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> wartość wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-132">The example requires <xref:System.Security.Permissions.FileDialogPermission> and the associated <xref:System.Security.Permissions.FileDialogPermissionAttribute.Open%2A> enumeration value.</span></span> <span data-ttu-id="bb1d0-133">W przykładzie pokazano sposób obsługi <xref:System.Security.SecurityException> ustalenie, czy zapisywanie funkcji powinna być wyłączona.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-133">The example demonstrates how to handle the <xref:System.Security.SecurityException> to determine whether the save feature should be disabled.</span></span> <span data-ttu-id="bb1d0-134">W tym przykładzie wymaga, aby Twoje <xref:System.Windows.Forms.Form> ma <xref:System.Windows.Forms.Button> formantu o nazwie `ButtonOpen`, a <xref:System.Windows.Forms.RichTextBox> formantu o nazwie `RtfBoxMain`.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-134">This example requires that your <xref:System.Windows.Forms.Form> has a <xref:System.Windows.Forms.Button> control named `ButtonOpen`, and a <xref:System.Windows.Forms.RichTextBox> control named `RtfBoxMain`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb1d0-135">Logikę programistyczną zapisywania funkcji nie pokazano w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-135">The programming logic for the save feature is not shown in the example.</span></span>  
  
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
>  <span data-ttu-id="bb1d0-136">W Visual C#, upewnij się, że dodasz kod, aby włączyć program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-136">In Visual C#, ensure that you add code to enable the event handler.</span></span> <span data-ttu-id="bb1d0-137">Za pomocą kodu z poprzedniego przykładu, poniższy kod przedstawia sposób włączania obsługi zdarzeń.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span><span class="sxs-lookup"><span data-stu-id="bb1d0-137">By using the code from the previous example, the following code shows how to enable the event handler.`this.ButtonOpen.Click += newSystem.Windows.Forms.EventHandler(this.ButtonOpen_Click);`</span></span>  
  
### <a name="other-files"></a><span data-ttu-id="bb1d0-138">Inne pliki</span><span class="sxs-lookup"><span data-stu-id="bb1d0-138">Other Files</span></span>  
 <span data-ttu-id="bb1d0-139">Czasami konieczne będzie odczytu lub zapisu do plików, że użytkownik nie określi, takie jak kiedy muszą zostać zachowane ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-139">Sometimes you will need to read or write to files that the user does not specify, such as when you must persist application settings.</span></span> <span data-ttu-id="bb1d0-140">Lokalny intranet i stref internetowych aplikacji, nie będzie ona uprawnienia do przechowywania danych w pliku lokalnym.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-140">In the local intranet and Internet zones, your application will not have permission to store data in a local file.</span></span> <span data-ttu-id="bb1d0-141">Jednak aplikacja będzie przechowywać dane w magazynie izolowanym.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-141">However, your application will be able to store data in isolated storage.</span></span> <span data-ttu-id="bb1d0-142">Wydzielona pamięć masowa jest przedział danych abstrakcyjny (nie lokalizacja określonego magazynu), który zawiera jeden lub więcej plików wydzielonej pamięci masowej, nazywanego magazynem, zawierające rzeczywistą lokalizację katalogu gdzie dane są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-142">Isolated storage is an abstract data compartment (not a specific storage location) that contains one or more isolated storage files, called stores, that contain the actual directory locations where data is stored.</span></span> <span data-ttu-id="bb1d0-143">Plik uprawnień dostępu, takich jak <xref:System.Security.Permissions.FileIOPermission> nie są wymagane; zamiast tego <xref:System.Security.Permissions.IsolatedStoragePermission> klasy określa uprawnienia do wydzielonej pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-143">File access permissions like <xref:System.Security.Permissions.FileIOPermission> are not required; instead, the <xref:System.Security.Permissions.IsolatedStoragePermission> class controls the permissions for isolated storage.</span></span> <span data-ttu-id="bb1d0-144">Domyślnie aplikacje, które są uruchomione w lokalnej sieci intranet i stref internetowych mogą być przechowywane dane przy użyciu izolowanego magazynu; Jednak ustawienia, takie jak przydział dysku mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-144">By default, applications that are running in the local intranet and Internet zones can store data using isolated storage; however, settings like disk quota can vary.</span></span> <span data-ttu-id="bb1d0-145">Aby uzyskać więcej informacji na temat wydzielonej pamięci masowej, zobacz [wydzielonej pamięci masowej](../../standard/io/isolated-storage.md).</span><span class="sxs-lookup"><span data-stu-id="bb1d0-145">For more information about isolated storage, see [Isolated Storage](../../standard/io/isolated-storage.md).</span></span>  
  
 <span data-ttu-id="bb1d0-146">W poniższym przykładzie użyto wydzielonej pamięci masowej można zapisać danych do pliku znajdującego się w magazynie.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-146">The following example uses isolated storage to write data to a file located in a store.</span></span> <span data-ttu-id="bb1d0-147">Przykład wymaga <xref:System.Security.Permissions.IsolatedStorageFilePermission> i <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> wartość wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-147">The example requires <xref:System.Security.Permissions.IsolatedStorageFilePermission> and the <xref:System.Security.Permissions.IsolatedStorageContainment.DomainIsolationByUser> enumeration value.</span></span> <span data-ttu-id="bb1d0-148">W przykładzie pokazano odczytywania i zapisywania określonych wartości właściwości <xref:System.Windows.Forms.Button> formantu do pliku w wydzielonej pamięci masowej.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-148">The example demonstrates reading and writing certain property values of the <xref:System.Windows.Forms.Button> control to a file in isolated storage.</span></span> <span data-ttu-id="bb1d0-149">`Read` Funkcja może być wywoływana po uruchomieniu aplikacji i `Write` funkcja może zostać wywołana przed zakończeniem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-149">The `Read` function would be called after the application starts and the `Write` function would be called before the application ends.</span></span> <span data-ttu-id="bb1d0-150">Przykład wymaga, aby `Read` i `Write` funkcje istnieje jako elementy członkowskie <xref:System.Windows.Forms.Form> zawierający <xref:System.Windows.Forms.Button> formantu o nazwie `MainButton`.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-150">The example requires that the `Read` and `Write` functions exist as members of a <xref:System.Windows.Forms.Form> that contains a <xref:System.Windows.Forms.Button> control named `MainButton`.</span></span>  
  
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
  
## <a name="database-access"></a><span data-ttu-id="bb1d0-151">Dostęp do bazy danych</span><span class="sxs-lookup"><span data-stu-id="bb1d0-151">Database Access</span></span>  
 <span data-ttu-id="bb1d0-152">Uprawnienia wymagane do uzyskania dostępu bazy danych różnią się zależnie od dostawcy bazy danych; jednak tylko te aplikacje, które działają z odpowiednimi uprawnieniami mogą uzyskać dostęp do bazy danych za pośrednictwem połączenia danych.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-152">The permissions required to access a database vary based on the database provider; however, only applications that are running with the appropriate permissions can access a database through a data connection.</span></span> <span data-ttu-id="bb1d0-153">Aby uzyskać więcej informacji na temat uprawnień, które są wymagane do dostępu do bazy danych, zobacz [zabezpieczenia dostępu kodu i ADO.NET](../data/adonet/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="bb1d0-153">For more information about the permissions that are required to access a database, see [Code Access Security and ADO.NET](../data/adonet/code-access-security.md).</span></span>  
  
 <span data-ttu-id="bb1d0-154">Jeśli nie można bezpośrednio dostęp do bazy danych, ponieważ chcesz, aby aplikację do uruchamiania w częściowej relacji zaufania, można użyć usługi sieci Web, jako alternatywę oznacza, że dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-154">If you cannot directly access a database because you want your application to run in partial trust, you can use a Web service as an alternative means to access your data.</span></span> <span data-ttu-id="bb1d0-155">Usługi sieci Web to oprogramowanie, którego ma programowo dostęp za pośrednictwem sieci.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-155">A Web service is a piece of software that can be programmatically accessed over a network.</span></span> <span data-ttu-id="bb1d0-156">Za pomocą usług sieci Web aplikacje mogą udostępniać dane w strefach grupy kodu.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-156">With Web services, applications can share data across code group zones.</span></span> <span data-ttu-id="bb1d0-157">Domyślnie aplikacje w lokalny intranet i Internet strefy mają prawo dostępu do swoich witryn pochodzenia, który umożliwia wywoływanie usługi sieci Web hostowanych na tym samym serwerze.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-157">By default, applications in the local intranet and Internet zones are granted the right to access their sites of origin, which enables them to call a Web service hosted on the same server.</span></span> <span data-ttu-id="bb1d0-158">Aby uzyskać więcej informacji, zobacz [usług sieci Web w technologii ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) lub [Windows Communication Foundation](../wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="bb1d0-158">For more information see [Web Services in ASP.NET AJAX](https://docs.microsoft.com/previous-versions/aspnet/bb398785(v=vs.100)) or [Windows Communication Foundation](../wcf/index.md).</span></span>  
  
## <a name="registry-access"></a><span data-ttu-id="bb1d0-159">Dostęp do rejestru</span><span class="sxs-lookup"><span data-stu-id="bb1d0-159">Registry Access</span></span>  
 <span data-ttu-id="bb1d0-160"><xref:System.Security.Permissions.RegistryPermission> Klasy kontroluje dostęp do rejestru systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-160">The <xref:System.Security.Permissions.RegistryPermission> class controls access to the operating system registry.</span></span> <span data-ttu-id="bb1d0-161">Domyślnie tylko aplikacje, które działają lokalnie można uzyskać dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-161">By default, only applications that are running locally can access the registry.</span></span>  <span data-ttu-id="bb1d0-162"><xref:System.Security.Permissions.RegistryPermission> przyznaje tylko aplikację po prawej stronie, aby spróbować dostępu do rejestru; go nie gwarantuje, że dostęp powiedzie się, ponieważ system operacyjny nadal wymusza zabezpieczeń w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-162"><xref:System.Security.Permissions.RegistryPermission> only grants an application the right to try registry access; it does not guarantee access will succeed, because the operating system still enforces security on the registry.</span></span>  
  
 <span data-ttu-id="bb1d0-163">Ponieważ nie można uzyskać dostępu do rejestru w częściowej relacji zaufania, konieczne może być znaleźć inne metody przechowywania danych.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-163">Because you cannot access the registry under partial trust, you may need to find other methods of storing your data.</span></span> <span data-ttu-id="bb1d0-164">Gdy zapisujesz ustawienia aplikacji, należy użyć wydzielonej pamięci masowej zamiast rejestru.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-164">When you store application settings, use isolated storage instead of the registry.</span></span> <span data-ttu-id="bb1d0-165">Wydzielona pamięć masowa może także służyć do przechowywania inne pliki specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-165">Isolated storage can also be used to store other application-specific files.</span></span> <span data-ttu-id="bb1d0-166">Można również przechowywać informacje globalnej aplikacji serwera lub witryny pochodzenia, ponieważ domyślnie aplikacja jest prawo do uzyskiwania dostępu do witryny pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="bb1d0-166">You can also store global application information about the server or site of origin, because by default an application is granted the right to access the site of its origin.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1d0-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb1d0-167">See also</span></span>

- [<span data-ttu-id="bb1d0-168">Bezpieczniejsze drukowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb1d0-168">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)
- [<span data-ttu-id="bb1d0-169">Dodatkowe zagadnienia z zakresu zabezpieczeń dotyczące formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb1d0-169">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)
- [<span data-ttu-id="bb1d0-170">Przegląd zabezpieczeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb1d0-170">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)
- [<span data-ttu-id="bb1d0-171">Zabezpieczenia formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb1d0-171">Windows Forms Security</span></span>](windows-forms-security.md)
- [<span data-ttu-id="bb1d0-172">Mage.exe (narzędzie generowania manifestu i edytowania)</span><span class="sxs-lookup"><span data-stu-id="bb1d0-172">Mage.exe (Manifest Generation and Editing Tool)</span></span>](../tools/mage-exe-manifest-generation-and-editing-tool.md)
- [<span data-ttu-id="bb1d0-173">MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)</span><span class="sxs-lookup"><span data-stu-id="bb1d0-173">MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)</span></span>](../tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
