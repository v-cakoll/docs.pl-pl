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
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="4a062-102">Instrukcje: Otwieranie plików za pomocą składnika OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="4a062-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="4a062-103"><xref:System.Windows.Forms.OpenFileDialog> Składnika pozwala użytkownikom na przeglądanie folderów ich komputera lub dowolnego komputera w sieci, a następnie wybierz jeden lub więcej plików, aby otworzyć.</span><span class="sxs-lookup"><span data-stu-id="4a062-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="4a062-104">Okno dialogowe zwraca ścieżkę i nazwę pliku wybranego w oknie dialogowym użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a062-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="4a062-105">Po użytkownik wybrał plik do otwarcia, istnieją dwa podejścia do mechanizmu otwierania pliku.</span><span class="sxs-lookup"><span data-stu-id="4a062-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="4a062-106">Jeśli wolisz pracować z strumieni plików, można utworzyć wystąpienia <xref:System.IO.StreamReader> klasy.</span><span class="sxs-lookup"><span data-stu-id="4a062-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="4a062-107">Alternatywnie możesz użyć <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby otworzyć wybranego pliku.</span><span class="sxs-lookup"><span data-stu-id="4a062-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="4a062-108">W poniższym przykładzie pierwszy obejmuje <xref:System.Security.Permissions.FileIOPermission> sprawdzenie uprawnień (zgodnie z opisem w "Uwaga dotycząca zabezpieczeń" poniżej), ale zapewnia dostęp do nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4a062-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="4a062-109">Tej techniki można używać z komputera lokalnego, intranetowych i internetowych stref.</span><span class="sxs-lookup"><span data-stu-id="4a062-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="4a062-110">Druga metoda wykonuje <xref:System.Security.Permissions.FileIOPermission> sprawdzenie uprawnień, ale lepiej nadaje się dla aplikacji w strefie intranetu lub Internetu.</span><span class="sxs-lookup"><span data-stu-id="4a062-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="4a062-111">Aby otworzyć plik jako strumienia za pomocą składnika OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="4a062-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="4a062-112">Wyświetlanie **Otwórz plik** okno dialogowe i wywołania metody można otworzyć pliku wybrana przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4a062-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="4a062-113">Jedno z podejść jest użycie <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe Otwieranie pliku, a następnie użyj wystąpienia <xref:System.IO.StreamReader> klasy można otworzyć pliku.</span><span class="sxs-lookup"><span data-stu-id="4a062-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="4a062-114">W poniższym przykładzie użyto <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Click> programu obsługi zdarzeń, aby otworzyć wystąpienie <xref:System.Windows.Forms.OpenFileDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="4a062-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="4a062-115">Gdy plik jest wybrana, a użytkownik kliknie **OK**, otwiera plik, który został wybrany w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="4a062-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="4a062-116">W takim przypadku zawartości są wyświetlane w oknie komunikatu, aby zobrazować, czy strumień pliku został odczytany.</span><span class="sxs-lookup"><span data-stu-id="4a062-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4a062-117">Do pobierania lub ustawiania <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwości zestawu wymaga poziom uprawnień przyznanych <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="4a062-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="4a062-118">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="4a062-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="4a062-119">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="4a062-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="4a062-120">W przykładzie założono, formularz ma <xref:System.Windows.Forms.Button> kontroli i <xref:System.Windows.Forms.OpenFileDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="4a062-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
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
  
     <span data-ttu-id="4a062-121">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4a062-121">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="4a062-122">Aby uzyskać więcej informacji na temat odczytywania ze strumieni plików Zobacz <xref:System.IO.FileStream.BeginRead%2A> i <xref:System.IO.FileStream.Read%2A>.</span><span class="sxs-lookup"><span data-stu-id="4a062-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="4a062-123">Aby otworzyć plik w formacie za pomocą składnika OpenFileDialog</span><span class="sxs-lookup"><span data-stu-id="4a062-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="4a062-124">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe i <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby otworzyć plik.</span><span class="sxs-lookup"><span data-stu-id="4a062-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="4a062-125"><xref:System.Windows.Forms.OpenFileDialog> Składnika <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda zwraca bajtów, które tworzą plik.</span><span class="sxs-lookup"><span data-stu-id="4a062-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="4a062-126">Bajty te umożliwiają strumień do odczytu.</span><span class="sxs-lookup"><span data-stu-id="4a062-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="4a062-127">W poniższym przykładzie <xref:System.Windows.Forms.OpenFileDialog> składnik jest utworzone za pomocą filtru "kursora", umożliwiając użytkownikowi na wybranie tylko pliki z rozszerzeniem nazwy pliku`.cur`.</span><span class="sxs-lookup"><span data-stu-id="4a062-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="4a062-128">Jeśli`.cur` pliku jest wybrany, kursor formularza jest ustawiona na wybranych kursora.</span><span class="sxs-lookup"><span data-stu-id="4a062-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4a062-129">Aby wywołać <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metoda, zestaw wymaga, aby poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="4a062-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="4a062-130">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="4a062-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="4a062-131">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="4a062-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="4a062-132">W przykładzie założono, formularz ma <xref:System.Windows.Forms.Button> kontroli.</span><span class="sxs-lookup"><span data-stu-id="4a062-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
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
  
     <span data-ttu-id="4a062-133">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieść następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4a062-133">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4a062-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a062-134">See also</span></span>
- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="4a062-135">OpenFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="4a062-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
