---
title: 'Instrukcje: zapisywanie plików za pomocą składnika SaveFileDialog'
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
ms.openlocfilehash: 3245caa3b7f001ecd68f30b8d30437ec26074a1a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914961"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="2aa61-102">Instrukcje: zapisywanie plików za pomocą składnika SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="2aa61-102">How to: Save Files Using the SaveFileDialog Component</span></span>
<span data-ttu-id="2aa61-103"><xref:System.Windows.Forms.SaveFileDialog> Składnik umożliwia użytkownikom przeglądanie systemu plików i wybieranie plików do zapisania.</span><span class="sxs-lookup"><span data-stu-id="2aa61-103">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="2aa61-104">Okno dialogowe zwraca ścieżkę i nazwę pliku, który użytkownik wybrał w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="2aa61-104">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="2aa61-105">Jednak należy napisać kod, aby faktycznie zapisywać pliki na dysku.</span><span class="sxs-lookup"><span data-stu-id="2aa61-105">However, you must write the code to actually write the files to disk.</span></span>  
  
### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="2aa61-106">Aby zapisać plik przy użyciu składnika SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="2aa61-106">To save a file using the SaveFileDialog component</span></span>  
  
- <span data-ttu-id="2aa61-107">Wyświetl okno dialogowe **Zapisz plik** i Wywołaj metodę, aby zapisać plik wybrany przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2aa61-107">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>  
  
     <span data-ttu-id="2aa61-108">Użyj <xref:System.Windows.Forms.SaveFileDialog> metody<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> składnika, aby zapisać plik.</span><span class="sxs-lookup"><span data-stu-id="2aa61-108">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="2aa61-109">Ta metoda daje <xref:System.IO.Stream> obiekt, do którego można pisać.</span><span class="sxs-lookup"><span data-stu-id="2aa61-109">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>  
  
     <span data-ttu-id="2aa61-110">W poniższym przykładzie zastosowano <xref:System.Windows.Forms.DialogResult> właściwość w celu pobrania nazwy pliku <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> i metody zapisania pliku.</span><span class="sxs-lookup"><span data-stu-id="2aa61-110">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="2aa61-111"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> Metoda umożliwia utworzenie strumienia, w którym ma zostać zapisany plik.</span><span class="sxs-lookup"><span data-stu-id="2aa61-111">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>  
  
     <span data-ttu-id="2aa61-112">W poniższym przykładzie istnieje <xref:System.Windows.Forms.Button> formant z przydzielonym obrazem.</span><span class="sxs-lookup"><span data-stu-id="2aa61-112">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="2aa61-113">Kliknięcie tego przycisku powoduje <xref:System.Windows.Forms.SaveFileDialog> wystąpienie składnika z filtrem umożliwiającym używanie plików typu. gif, JPEG i BMP.</span><span class="sxs-lookup"><span data-stu-id="2aa61-113">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="2aa61-114">Jeśli w oknie dialogowym Zapisz plik zostanie wybrany plik tego typu, obraz przycisku zostanie zapisany.</span><span class="sxs-lookup"><span data-stu-id="2aa61-114">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2aa61-115">Aby uzyskać lub ustawić <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwość, zestaw wymaga poziomu uprawnień przyznany <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> przez klasę.</span><span class="sxs-lookup"><span data-stu-id="2aa61-115">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="2aa61-116">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2aa61-116">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="2aa61-117">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="2aa61-117">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="2aa61-118">W przykładzie założono, że formularz <xref:System.Windows.Forms.Button> ma kontrolkę <xref:System.Windows.Forms.ButtonBase.Image%2A> z właściwością ustawioną na plik typu. gif, JPEG lub BMP.</span><span class="sxs-lookup"><span data-stu-id="2aa61-118">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2aa61-119">Właściwość klasy (która z powodu dziedziczenia <xref:System.Windows.Forms.SaveFileDialog> , jest częścią klasy) używa indeksu jednego. <xref:System.Windows.Forms.FileDialog> <xref:System.Windows.Forms.FileDialog.FilterIndex%2A></span><span class="sxs-lookup"><span data-stu-id="2aa61-119">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="2aa61-120">Jest to ważne w przypadku pisania kodu w celu zapisania danych w określonym formacie (na przykład zapisanie pliku w formacie zwykłego tekstu a binarny).</span><span class="sxs-lookup"><span data-stu-id="2aa61-120">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="2aa61-121">Ta właściwość jest proponowana w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2aa61-121">This property is featured in the example below.</span></span>  
  
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
  
     <span data-ttu-id="2aa61-122">(Wizualizacje C# i C++wizualizacje) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2aa61-122">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button2.Click += new System.EventHandler(this.button2_Click);  
    ```  
  
    ```cpp  
    this->button2->Click += gcnew  
       System::EventHandler(this, &Form1::button2_Click);  
    ```  
  
     <span data-ttu-id="2aa61-123">Aby uzyskać więcej informacji na temat pisania strumieni plików <xref:System.IO.FileStream.BeginWrite%2A> , <xref:System.IO.FileStream.Write%2A>Zobacz i.</span><span class="sxs-lookup"><span data-stu-id="2aa61-123">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2aa61-124">Niektóre kontrolki, takie jak <xref:System.Windows.Forms.RichTextBox> kontrolka, mogą zapisywać pliki.</span><span class="sxs-lookup"><span data-stu-id="2aa61-124">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span> <span data-ttu-id="2aa61-125">Aby uzyskać więcej informacji, zobacz sekcję "składnik SaveFileDialog" w artykule technicznym Biblioteka MSDN Online Library — [zasadniczy kod dla Windows Forms okien](https://go.microsoft.com/fwlink/?LinkID=102575)dialogowych.</span><span class="sxs-lookup"><span data-stu-id="2aa61-125">For more information, see the "SaveFileDialog Component" section of the MSDN Online Library technical article, [Essential Code for Windows Forms Dialog Boxes](https://go.microsoft.com/fwlink/?LinkID=102575).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aa61-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2aa61-126">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="2aa61-127">SaveFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="2aa61-127">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
