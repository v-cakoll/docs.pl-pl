---
title: 'Instrukcje: ładowanie plików do kontrolki RichTextBox formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: 0f52b4ff869d7a2220dd2d40e0ab90bbfb7d24ae
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046168"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="8fa2c-102">Instrukcje: ładowanie plików do kontrolki RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8fa2c-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="8fa2c-103">Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms może wyświetlić plik w formacie zwykłego tekstu (RTF) Unicode lub RTF.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="8fa2c-104">Aby to zrobić, wywołaj <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="8fa2c-105">Można również użyć <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> metody do ładowania danych ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="8fa2c-106">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="8fa2c-107">Aby załadować plik do kontrolki RichTextBox</span><span class="sxs-lookup"><span data-stu-id="8fa2c-107">To load a file into the RichTextBox control</span></span>

1. <span data-ttu-id="8fa2c-108">Określ ścieżkę pliku, który ma zostać otwarty za pomocą <xref:System.Windows.Forms.OpenFileDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="8fa2c-109">Aby zapoznać się z omówieniem, zobacz [Omówienie składnika OpenFileDialog](openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="8fa2c-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="8fa2c-110">Wywołaj <xref:System.Windows.Forms.RichTextBox> metodę kontrolki, określając plik do załadowania i opcjonalnie typ pliku. <xref:System.Windows.Forms.RichTextBox.LoadFile%2A></span><span class="sxs-lookup"><span data-stu-id="8fa2c-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="8fa2c-111">W poniższym przykładzie plik do załadowania jest pobierany ze <xref:System.Windows.Forms.OpenFileDialog> <xref:System.Windows.Forms.FileDialog.FileName%2A> właściwości składnika.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="8fa2c-112">W przypadku wywołania metody z nazwą pliku jako jedynego argumentu, przyjmuje się, że zostanie on RTF.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="8fa2c-113">Aby określić inny typ pliku, wywołaj metodę z wartością <xref:System.Windows.Forms.RichTextBoxStreamType> wyliczenia jako jej drugi argument.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="8fa2c-114">W poniższym <xref:System.Windows.Forms.OpenFileDialog> przykładzie składnik jest wyświetlany po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="8fa2c-115">Wybrany plik jest następnie otwierany i wyświetlany w <xref:System.Windows.Forms.RichTextBox> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="8fa2c-116">W tym przykładzie założono, że formularz ma`btnOpenFile`przycisk,.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-116">This example assumes a form has a button,`btnOpenFile`.</span></span>

    ```vb
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _
       ByVal e As System.EventArgs) Handles btnOpenFile.Click
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _
              RichTextBoxStreamType.RichText)
          End If
    End Sub
    ```

    ```csharp
    private void btnOpenFile_Click(object sender, System.EventArgs e)
    {
       if(openFileDialog1.ShowDialog() == DialogResult.OK)
       {
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);
       }
    }
    ```

    ```cpp
    private:
       void btnOpenFile_Click(System::Object ^  sender,
          System::EventArgs ^  e)
       {
          if(openFileDialog1->ShowDialog() == DialogResult::OK)
          {
             richTextBox1->LoadFile(openFileDialog1->FileName,
                RichTextBoxStreamType::RichText);
          }
       }
    ```

    <span data-ttu-id="8fa2c-117">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-117">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="8fa2c-118">Aby można było uruchomić ten proces, zestaw może wymagać poziomu uprawnień przyznany przez <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> klasę.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="8fa2c-119">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="8fa2c-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="8fa2c-120">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="8fa2c-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8fa2c-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fa2c-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="8fa2c-122">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8fa2c-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="8fa2c-123">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8fa2c-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
