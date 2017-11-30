---
title: "Porady: zapisywanie plików za pomocą formantu RichTextBox formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d28aeaefca6f8aa13607f1c1e6f72557ef536754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="5588b-102">Porady: zapisywanie plików za pomocą formantu RichTextBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5588b-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="5588b-103">Formularze systemu Windows <xref:System.Windows.Forms.RichTextBox> formant może zapisać informacji wyświetlanych w jednym z kilku formatów:</span><span class="sxs-lookup"><span data-stu-id="5588b-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
-   <span data-ttu-id="5588b-104">Zwykły tekst</span><span class="sxs-lookup"><span data-stu-id="5588b-104">Plain text</span></span>  
  
-   <span data-ttu-id="5588b-105">Unicode zwykłego tekstu</span><span class="sxs-lookup"><span data-stu-id="5588b-105">Unicode plain text</span></span>  
  
-   <span data-ttu-id="5588b-106">Format tekstu sformatowanego (RTF)</span><span class="sxs-lookup"><span data-stu-id="5588b-106">Rich-Text Format (RTF)</span></span>  
  
-   <span data-ttu-id="5588b-107">RTF spacji zamiast obiektów OLE</span><span class="sxs-lookup"><span data-stu-id="5588b-107">RTF with spaces in place of OLE objects</span></span>  
  
-   <span data-ttu-id="5588b-108">Zwykły tekst z reprezentacji tekstowej obiektów OLE</span><span class="sxs-lookup"><span data-stu-id="5588b-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="5588b-109">Aby zapisać plik, należy wywołać <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="5588b-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="5588b-110">Można również użyć **SaveFile** metody w celu zapisywania do strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="5588b-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="5588b-111">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span><span class="sxs-lookup"><span data-stu-id="5588b-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="5588b-112">Aby zapisać zawartość formantu w pliku</span><span class="sxs-lookup"><span data-stu-id="5588b-112">To save the contents of the control to a file</span></span>  
  
1.  <span data-ttu-id="5588b-113">Określ ścieżkę pliku do zapisania.</span><span class="sxs-lookup"><span data-stu-id="5588b-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="5588b-114">Aby to zrobić w rzeczywistych aplikacjach, należy zwykle użyć <xref:System.Windows.Forms.SaveFileDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="5588b-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="5588b-115">Aby uzyskać ogólne informacje, zobacz [savefiledialog — informacje o składniku](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="5588b-115">For an overview, see [SaveFileDialog Component Overview](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="5588b-116">Wywołanie <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> metody <xref:System.Windows.Forms.RichTextBox> kontroli określenie pliku do zapisania i opcjonalnie typu pliku.</span><span class="sxs-lookup"><span data-stu-id="5588b-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="5588b-117">Jeśli należy wywołać metodę jako jej argument tylko nazwą pliku, plik zostanie zapisany jako RTF.</span><span class="sxs-lookup"><span data-stu-id="5588b-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="5588b-118">Aby określić plik innego typu, należy wywołać metodę o wartości <xref:System.Windows.Forms.RichTextBoxStreamType> wyliczenie jako drugi argument.</span><span class="sxs-lookup"><span data-stu-id="5588b-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="5588b-119">W poniższym przykładzie ścieżka ustawiona dla lokalizacji pliku RTF jest **Moje dokumenty** folderu.</span><span class="sxs-lookup"><span data-stu-id="5588b-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="5588b-120">Ta lokalizacja jest używana, ponieważ można założyć, że ten folder zawiera większość komputerów z systemem operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="5588b-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="5588b-121">Wybranie tej lokalizacji również umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5588b-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="5588b-122">W poniższym przykładzie założono formularza z <xref:System.Windows.Forms.RichTextBox> kontroli już dodany.</span><span class="sxs-lookup"><span data-stu-id="5588b-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
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
    >  <span data-ttu-id="5588b-123">W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="5588b-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="5588b-124">Jeśli aplikacja musi utworzyć plik, ta aplikacja wymaga dostępu Tworzenie folderu.</span><span class="sxs-lookup"><span data-stu-id="5588b-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="5588b-125">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="5588b-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="5588b-126">Jeśli plik już istnieje, aplikacja musi tylko dostęp do zapisu, niższego poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="5588b-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="5588b-127">Jeśli to możliwe, jest bezpieczniejsza do utworzenia pliku podczas wdrażania i tylko dostęp do jednego pliku, zamiast tworzyć dostępu dla folderu.</span><span class="sxs-lookup"><span data-stu-id="5588b-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="5588b-128">Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż w folderze głównym lub folderze Program Files.</span><span class="sxs-lookup"><span data-stu-id="5588b-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5588b-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5588b-129">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="5588b-130">RichTextBox — formant</span><span class="sxs-lookup"><span data-stu-id="5588b-130">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="5588b-131">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5588b-131">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
