---
title: Załaduj pliki do kontrolki RichTextBox
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
ms.openlocfilehash: c31e004ea4cd0821b5f18f0ab0fe2708e6ac4b59
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736288"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="bb34b-102">Porady: ładowanie plików do formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bb34b-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="bb34b-103">Kontrolka <xref:System.Windows.Forms.RichTextBox> Windows Forms może wyświetlić plik w formacie zwykłego tekstu (RTF) Unicode lub RTF.</span><span class="sxs-lookup"><span data-stu-id="bb34b-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="bb34b-104">Aby to zrobić, wywołaj metodę <xref:System.Windows.Forms.RichTextBox.LoadFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="bb34b-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="bb34b-105">Za pomocą metody <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> można również ładować dane ze strumienia.</span><span class="sxs-lookup"><span data-stu-id="bb34b-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="bb34b-106">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="bb34b-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="bb34b-107">Aby załadować plik do kontrolki RichTextBox</span><span class="sxs-lookup"><span data-stu-id="bb34b-107">To load a file into the RichTextBox control</span></span>

1. <span data-ttu-id="bb34b-108">Określ ścieżkę pliku, który ma zostać otwarty za pomocą składnika <xref:System.Windows.Forms.OpenFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="bb34b-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="bb34b-109">Aby zapoznać się z omówieniem, zobacz [Omówienie składnika OpenFileDialog](openfiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="bb34b-109">For an overview, see [OpenFileDialog Component Overview](openfiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="bb34b-110">Wywołaj metodę <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> kontrolki <xref:System.Windows.Forms.RichTextBox>, określając plik do załadowania i opcjonalnego typu pliku.</span><span class="sxs-lookup"><span data-stu-id="bb34b-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="bb34b-111">W poniższym przykładzie plik do załadowania jest pobierany ze właściwości <xref:System.Windows.Forms.FileDialog.FileName%2A> składnika <xref:System.Windows.Forms.OpenFileDialog>.</span><span class="sxs-lookup"><span data-stu-id="bb34b-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="bb34b-112">W przypadku wywołania metody z nazwą pliku jako jedynego argumentu, przyjmuje się, że zostanie on RTF.</span><span class="sxs-lookup"><span data-stu-id="bb34b-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="bb34b-113">Aby określić inny typ pliku, należy wywołać metodę z wartością wyliczenia <xref:System.Windows.Forms.RichTextBoxStreamType> jako drugi argument.</span><span class="sxs-lookup"><span data-stu-id="bb34b-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="bb34b-114">W poniższym przykładzie składnik <xref:System.Windows.Forms.OpenFileDialog> jest wyświetlany po kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="bb34b-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="bb34b-115">Wybrany plik jest następnie otwierany i wyświetlany w kontrolce <xref:System.Windows.Forms.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="bb34b-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="bb34b-116">W tym przykładzie założono, że formularz ma przycisk`btnOpenFile`.</span><span class="sxs-lookup"><span data-stu-id="bb34b-116">This example assumes a form has a button,`btnOpenFile`.</span></span>

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

    <span data-ttu-id="bb34b-117">(Wizualizacja C#, C++wizualizacja) Umieść poniższy kod w Konstruktorze formularza, aby zarejestrować procedurę obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bb34b-117">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

    ```csharp
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);
    ```

    ```cpp
    this->btnOpenFile->Click += gcnew
       System::EventHandler(this, &Form1::btnOpenFile_Click);
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="bb34b-118">Aby można było uruchomić ten proces, zestaw może wymagać poziomu uprawnień przyznanych przez klasę <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bb34b-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="bb34b-119">Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek z powodu niewystarczających uprawnień.</span><span class="sxs-lookup"><span data-stu-id="bb34b-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="bb34b-120">Aby uzyskać więcej informacji, zobacz podstawowe informacje o [zabezpieczeniach dostępu kodu](../../misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="bb34b-120">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bb34b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb34b-121">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="bb34b-122">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="bb34b-122">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="bb34b-123">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bb34b-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
