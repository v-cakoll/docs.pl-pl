---
title: 'Porady: zapisywanie plików za pomocą składnika SaveFileDialog'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cace4dcd9aa5eb5d46579044905bbf2e5d755b66
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="90804-102">Porady: zapisywanie plików za pomocą składnika SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="90804-102">How to: Save Files Using the SaveFileDialog Component</span></span>
<span data-ttu-id="90804-103"><xref:System.Windows.Forms.SaveFileDialog> Składnika umożliwia użytkownikom przeglądać systemu plików i wybierz pliki do zapisania.</span><span class="sxs-lookup"><span data-stu-id="90804-103">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="90804-104">Okno dialogowe zwraca ścieżkę i nazwę pliku wybranego w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="90804-104">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="90804-105">Jednak należy napisać kod do faktycznie zapisu plików do dysku.</span><span class="sxs-lookup"><span data-stu-id="90804-105">However, you must write the code to actually write the files to disk.</span></span>  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="90804-106">Aby zapisać plik za pomocą składnika SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="90804-106">To save a file using the SaveFileDialog component</span></span>  
  
-   <span data-ttu-id="90804-107">Wyświetl **Zapisz plik** okno dialogowe i wywołanie metody można zapisać pliku wybrane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="90804-107">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>  
  
     <span data-ttu-id="90804-108">Użyj <xref:System.Windows.Forms.SaveFileDialog> składnika <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metodę, aby zapisać plik.</span><span class="sxs-lookup"><span data-stu-id="90804-108">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="90804-109">Ta metoda umożliwia <xref:System.IO.Stream> możesz zapisywać do obiektu.</span><span class="sxs-lookup"><span data-stu-id="90804-109">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>  
  
     <span data-ttu-id="90804-110">Poniższym przykładzie użyto <xref:System.Windows.Forms.DialogResult> właściwości można pobrać nazwy pliku i <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> metodę, aby zapisać plik.</span><span class="sxs-lookup"><span data-stu-id="90804-110">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="90804-111"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Metoda daje strumień pliku do zapisu.</span><span class="sxs-lookup"><span data-stu-id="90804-111">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>  
  
     <span data-ttu-id="90804-112">W poniższym przykładzie jest <xref:System.Windows.Forms.Button> kontroli z obrazem przypisane do niej.</span><span class="sxs-lookup"><span data-stu-id="90804-112">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="90804-113">Po kliknięciu przycisku, <xref:System.Windows.Forms.SaveFileDialog> składnik zostanie uruchomiony z filtrem, który umożliwia pliki typu GIF, JPEG i BMP.</span><span class="sxs-lookup"><span data-stu-id="90804-113">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="90804-114">Zaznaczenie tego typu pliku w oknie dialogowym Zapisz plik jest zapisywany obraz przycisku.</span><span class="sxs-lookup"><span data-stu-id="90804-114">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="90804-115">Można pobrać lub ustawić <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwość, z zestawu wymaga do poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="90804-115">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="90804-116">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="90804-116">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="90804-117">Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="90804-117">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="90804-118">W przykładzie założono formularz zawiera <xref:System.Windows.Forms.Button> sterować za pomocą jego <xref:System.Windows.Forms.ButtonBase.Image%2A> właściwość w pliku typu GIF, JPEG lub bmp.</span><span class="sxs-lookup"><span data-stu-id="90804-118">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="90804-119"><xref:System.Windows.Forms.FileDialog> Klasy <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> właściwości (które z powodu dziedziczenia jest częścią <xref:System.Windows.Forms.SaveFileDialog> klasy) używa jednego indeksu.</span><span class="sxs-lookup"><span data-stu-id="90804-119">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="90804-120">Jest to ważne podczas pisania kodu w celu zapisywania danych w określonym formacie (na przykład plik zostanie zapisany w postaci zwykłego tekstu lub format binarny).</span><span class="sxs-lookup"><span data-stu-id="90804-120">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="90804-121">Ta właściwość jest umieszczony w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="90804-121">This property is featured in the example below.</span></span>  
  
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
  
     <span data-ttu-id="90804-122">(Visual C# i [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) umieścić następujący kod w Konstruktorze formularza, aby zarejestrować program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="90804-122">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     <span data-ttu-id="90804-123">Aby uzyskać więcej informacji na temat pisania strumieni plików, zobacz <xref:System.IO.FileStream.BeginWrite%2A> i <xref:System.IO.FileStream.Write%2A>.</span><span class="sxs-lookup"><span data-stu-id="90804-123">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="90804-124">Niektóre formanty, takie jak <xref:System.Windows.Forms.RichTextBox> kontrolować, ma możliwość zapisania plików.</span><span class="sxs-lookup"><span data-stu-id="90804-124">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span> <span data-ttu-id="90804-125">Aby uzyskać więcej informacji, zobacz sekcję "Savefiledialog — składnik" artykułu technicznego bibliotece MSDN Online [niezbędne kodu dla systemu Windows dialogowe w formularzach](http://go.microsoft.com/fwlink/?LinkID=102575).</span><span class="sxs-lookup"><span data-stu-id="90804-125">For more information, see the "SaveFileDialog Component" section of the MSDN Online Library technical article, [Essential Code for Windows Forms Dialog Boxes](http://go.microsoft.com/fwlink/?LinkID=102575).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90804-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90804-126">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="90804-127">SaveFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="90804-127">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
