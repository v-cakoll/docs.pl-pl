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
ms.openlocfilehash: 4784ddd563ccec0f7e6271700781ee1b5d3ac105
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318419"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="9dbea-102">Instrukcje: zapisywanie plików za pomocą kontrolki RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9dbea-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="9dbea-103">Formularze Windows <xref:System.Windows.Forms.RichTextBox> kontroli można zapisać informacji wyświetlanych w jednym z kilku formatów:</span><span class="sxs-lookup"><span data-stu-id="9dbea-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
-   <span data-ttu-id="9dbea-104">Zwykły tekst</span><span class="sxs-lookup"><span data-stu-id="9dbea-104">Plain text</span></span>  
  
-   <span data-ttu-id="9dbea-105">Zwykły tekst w formacie Unicode</span><span class="sxs-lookup"><span data-stu-id="9dbea-105">Unicode plain text</span></span>  
  
-   <span data-ttu-id="9dbea-106">Format tekstu sformatowanego (RTF)</span><span class="sxs-lookup"><span data-stu-id="9dbea-106">Rich-Text Format (RTF)</span></span>  
  
-   <span data-ttu-id="9dbea-107">RTF spacji zamiast obiektów OLE</span><span class="sxs-lookup"><span data-stu-id="9dbea-107">RTF with spaces in place of OLE objects</span></span>  
  
-   <span data-ttu-id="9dbea-108">Zwykły tekst z reprezentacji tekstowej obiektów OLE</span><span class="sxs-lookup"><span data-stu-id="9dbea-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="9dbea-109">Aby zapisać plik, należy wywołać <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9dbea-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="9dbea-110">Można również użyć **SaveFile** metody, aby zapisać dane w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="9dbea-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="9dbea-111">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="9dbea-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="9dbea-112">Aby zapisać zawartości formantu w pliku</span><span class="sxs-lookup"><span data-stu-id="9dbea-112">To save the contents of the control to a file</span></span>  
  
1. <span data-ttu-id="9dbea-113">Określ ścieżkę do pliku do zapisania.</span><span class="sxs-lookup"><span data-stu-id="9dbea-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="9dbea-114">Aby to zrobić w aplikacji rzeczywistych, zazwyczaj używasz <xref:System.Windows.Forms.SaveFileDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="9dbea-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="9dbea-115">Aby uzyskać przegląd, zobacz [savefiledialog — informacje o składniku](savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9dbea-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="9dbea-116">Wywołaj <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody <xref:System.Windows.Forms.RichTextBox> kontrolki, określając plik, aby zapisać i opcjonalnie typu pliku.</span><span class="sxs-lookup"><span data-stu-id="9dbea-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="9dbea-117">Jeśli chcesz wywołać metodę z nazwą pliku jako argument tylko, plik zostanie zapisany jako RTF.</span><span class="sxs-lookup"><span data-stu-id="9dbea-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="9dbea-118">Aby określić inny typ pliku, należy wywołać metodę z wartością <xref:System.Windows.Forms.RichTextBoxStreamType> wyliczenia jako swój drugi argument.</span><span class="sxs-lookup"><span data-stu-id="9dbea-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="9dbea-119">W poniższym przykładzie ścieżkę zestawu dla lokalizacji pliku RTF jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="9dbea-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="9dbea-120">Ta lokalizacja jest używana, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego folderu.</span><span class="sxs-lookup"><span data-stu-id="9dbea-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="9dbea-121">Wybranie tej lokalizacji również umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9dbea-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="9dbea-122">W poniższym przykładzie przyjęto założenie, formularz z <xref:System.Windows.Forms.RichTextBox> formant został już dodany.</span><span class="sxs-lookup"><span data-stu-id="9dbea-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
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
    >  <span data-ttu-id="9dbea-123">W tym przykładzie tworzy nowy plik, jeśli go jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="9dbea-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="9dbea-124">Jeśli aplikacja musi utworzyć plik, ta aplikacja musi mieć dostęp do tworzenia folderu.</span><span class="sxs-lookup"><span data-stu-id="9dbea-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="9dbea-125">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="9dbea-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="9dbea-126">Jeśli plik już istnieje, aplikacja musi jedynie dostęp do zapisu, mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="9dbea-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="9dbea-127">W przypadku, gdy jest to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i tylko przyznać dostęp do odczytu do pojedynczego pliku zamiast tworzyć dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="9dbea-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="9dbea-128">Ponadto jest bardziej bezpieczne, można zapisać danych do folderów użytkowników niż do folderu głównego lub do folderu Program Files.</span><span class="sxs-lookup"><span data-stu-id="9dbea-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dbea-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9dbea-129">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="9dbea-130">RichTextBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="9dbea-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="9dbea-131">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9dbea-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
