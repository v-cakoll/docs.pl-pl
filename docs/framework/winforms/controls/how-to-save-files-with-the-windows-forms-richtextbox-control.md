---
title: 'Instrukcje: zapisywanie plików za pomocą kontrolki RichTextBox formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: c5d88e4942d96ee12e8b9f40156090c874386668
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046266"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="270e6-102">Instrukcje: zapisywanie plików za pomocą kontrolki RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="270e6-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>

<span data-ttu-id="270e6-103">Formant Windows Forms <xref:System.Windows.Forms.RichTextBox> może zapisywać informacje wyświetlane w jednym z kilku formatów:</span><span class="sxs-lookup"><span data-stu-id="270e6-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>

- <span data-ttu-id="270e6-104">Zwykły tekst</span><span class="sxs-lookup"><span data-stu-id="270e6-104">Plain text</span></span>

- <span data-ttu-id="270e6-105">Zwykły tekst Unicode</span><span class="sxs-lookup"><span data-stu-id="270e6-105">Unicode plain text</span></span>

- <span data-ttu-id="270e6-106">Format tekstu sformatowanego (RTF)</span><span class="sxs-lookup"><span data-stu-id="270e6-106">Rich-Text Format (RTF)</span></span>

- <span data-ttu-id="270e6-107">RTF z miejscami zamiast obiektów OLE</span><span class="sxs-lookup"><span data-stu-id="270e6-107">RTF with spaces in place of OLE objects</span></span>

- <span data-ttu-id="270e6-108">Zwykły tekst z reprezentacją tekstową obiektów OLE</span><span class="sxs-lookup"><span data-stu-id="270e6-108">Plain text with a textual representation of OLE objects</span></span>

<span data-ttu-id="270e6-109">Aby zapisać plik, wywołaj <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="270e6-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="270e6-110">Możesz również użyć metody **SaveFile** , aby zapisać dane w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="270e6-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="270e6-111">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="270e6-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>

### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="270e6-112">Aby zapisać zawartość kontrolki do pliku</span><span class="sxs-lookup"><span data-stu-id="270e6-112">To save the contents of the control to a file</span></span>

1. <span data-ttu-id="270e6-113">Określ ścieżkę pliku, który ma zostać zapisany.</span><span class="sxs-lookup"><span data-stu-id="270e6-113">Determine the path of the file to be saved.</span></span>

    <span data-ttu-id="270e6-114">Aby to zrobić w aplikacji w świecie rzeczywistym, zazwyczaj używany jest <xref:System.Windows.Forms.SaveFileDialog> składnik.</span><span class="sxs-lookup"><span data-stu-id="270e6-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="270e6-115">Aby zapoznać się z omówieniem, zobacz [Omówienie składnika SaveFileDialog](savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="270e6-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>

2. <span data-ttu-id="270e6-116">Wywołaj <xref:System.Windows.Forms.RichTextBox> metodę kontrolki, określając plik do zapisania i opcjonalnie typ pliku. <xref:System.Windows.Forms.RichTextBox.SaveFile%2A></span><span class="sxs-lookup"><span data-stu-id="270e6-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="270e6-117">W przypadku wywołania metody z nazwą pliku jako jedynego argumentu, plik zostanie zapisany w formacie RTF.</span><span class="sxs-lookup"><span data-stu-id="270e6-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="270e6-118">Aby określić inny typ pliku, wywołaj metodę z wartością <xref:System.Windows.Forms.RichTextBoxStreamType> wyliczenia jako jej drugi argument.</span><span class="sxs-lookup"><span data-stu-id="270e6-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>

    <span data-ttu-id="270e6-119">W poniższym przykładzie ścieżką ustawioną dla lokalizacji pliku tekstu sformatowanego jest folder **Moje dokumenty** .</span><span class="sxs-lookup"><span data-stu-id="270e6-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="270e6-120">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten folder.</span><span class="sxs-lookup"><span data-stu-id="270e6-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="270e6-121">Wybranie tej lokalizacji pozwala również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="270e6-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="270e6-122">W poniższym przykładzie założono, że formularz <xref:System.Windows.Forms.RichTextBox> z kontrolką został już dodany.</span><span class="sxs-lookup"><span data-stu-id="270e6-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>

    ```vb
    Public Sub SaveFile()
       ' You should replace the bold file name in the
       ' sample below with a file name of your own choosing.
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _
       (System.Environment.SpecialFolder.Personal) _
       & "\Testdoc.rtf", _
          RichTextBoxStreamType.RichNoOleObjs)
    End Sub
    ```

    ```csharp
    public void SaveFile()
    {
       // You should replace the bold file name in the
       // sample below with a file name of your own choosing.
       // Note the escape character used (@) when specifying the path.
       richTextBox1.SaveFile(System.Environment.GetFolderPath
       (System.Environment.SpecialFolder.Personal)
       + @"\Testdoc.rtf",
          RichTextBoxStreamType.RichNoOleObjs);
    }
    ```

    ```cpp
    public:
       void SaveFile()
       {
          // You should replace the bold file name in the
          // sample below with a file name of your own choosing.
          richTextBox1->SaveFile(String::Concat
             (System::Environment::GetFolderPath
             (System::Environment::SpecialFolder::Personal),
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);
       }
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="270e6-123">Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="270e6-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="270e6-124">Jeśli aplikacja musi utworzyć plik, aplikacja musi mieć dostęp do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="270e6-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="270e6-125">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="270e6-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="270e6-126">Jeśli plik już istnieje, aplikacja musi mieć tylko uprawnienia do zapisu, które ma mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="270e6-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="270e6-127">Jeśli to możliwe, bezpieczniejsze jest tworzenie pliku podczas wdrażania i udzielanie dostępu do odczytu tylko do jednego pliku, a nie tworzenie dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="270e6-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="270e6-128">Ponadto bardziej bezpieczne jest zapisanie danych do folderów użytkowników niż folder główny lub folder Program Files.</span><span class="sxs-lookup"><span data-stu-id="270e6-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>

## <a name="see-also"></a><span data-ttu-id="270e6-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="270e6-129">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="270e6-130">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="270e6-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="270e6-131">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="270e6-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
