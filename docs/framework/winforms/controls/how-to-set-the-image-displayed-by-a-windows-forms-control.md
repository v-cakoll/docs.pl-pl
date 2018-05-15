---
title: 'Porady: ustawianie obrazu wyświetlanego przez formant formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Button control [Windows Forms], images
- Windows Forms controls, images
- controls [Windows Forms], images
- images [Windows Forms], Windows Forms controls
- examples [Windows Forms], controls
ms.assetid: 9445af8f-4f62-48b0-a3f6-068058964b9f
ms.openlocfilehash: 4870f9e2acc48a90e1e2193d514926fedee05f61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-image-displayed-by-a-windows-forms-control"></a><span data-ttu-id="1f023-102">Porady: ustawianie obrazu wyświetlanego przez formant formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1f023-102">How to: Set the Image Displayed by a Windows Forms Control</span></span>
<span data-ttu-id="1f023-103">Kilka formantów formularzy systemu Windows można wyświetlić obrazy.</span><span class="sxs-lookup"><span data-stu-id="1f023-103">Several Windows Forms controls can display images.</span></span> <span data-ttu-id="1f023-104">Obrazy te można ikony, które Objaśnienie przeznaczenia formantu, takie jak ikoną dyskietki na przycisku określające **zapisać** polecenia.</span><span class="sxs-lookup"><span data-stu-id="1f023-104">These images can be icons that clarify the purpose of the control, such as a diskette icon on a button denoting the **Save** command.</span></span> <span data-ttu-id="1f023-105">Alternatywnie ikony może być obrazy tła, aby mieć kontrolę wygląd i zachowanie, które mają.</span><span class="sxs-lookup"><span data-stu-id="1f023-105">Alternatively, the icons can be background images to give the control the appearance and behavior you want.</span></span>  
  
### <a name="to-set-the-image-displayed-by-a-control"></a><span data-ttu-id="1f023-106">Aby ustawić obrazu wyświetlanego przez formant</span><span class="sxs-lookup"><span data-stu-id="1f023-106">To set the image displayed by a control</span></span>  
  
1.  <span data-ttu-id="1f023-107">Ustawianie formantu `Image` lub `BackgroundImage` dla właściwości typu obiektu <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="1f023-107">Set the control's `Image` or `BackgroundImage` property to an object of type <xref:System.Drawing.Image>.</span></span> <span data-ttu-id="1f023-108">Ogólnie rzecz biorąc, użytkownik będzie można ładowanie obrazu z pliku za pomocą <xref:System.Drawing.Image.FromFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1f023-108">Generally, you will be loading the image from a file by using the <xref:System.Drawing.Image.FromFile%2A> method.</span></span>  
  
     <span data-ttu-id="1f023-109">W poniższym przykładzie kodu, ścieżka ustawiona dla lokalizacji obrazu jest **Moje obrazy** folderu.</span><span class="sxs-lookup"><span data-stu-id="1f023-109">In the following code example, the path set for the location of the image is the **My Pictures** folder.</span></span> <span data-ttu-id="1f023-110">Ten katalog zawiera większość komputerów z systemem operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="1f023-110">Most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="1f023-111">Dzięki temu użytkownicy z poziomami dostępu minimalny system można bezpiecznie uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1f023-111">This also enables users with minimal system access levels to run the application safely.</span></span> <span data-ttu-id="1f023-112">Poniższy przykład kodu wymaga już formularza z <xref:System.Windows.Forms.PictureBox> dodano formant.</span><span class="sxs-lookup"><span data-stu-id="1f023-112">The following code example requires that you already have a form with a <xref:System.Windows.Forms.PictureBox> control added.</span></span>  
  
    ```vb  
    ' Replace the image named below  
    ' with an icon of your own choosing.  
    PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.MyPictures) _  
       & "\Image.gif")  
    ```  
  
    ```csharp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.MyPictures)  
       + @"\Image.gif");  
    ```  
  
    ```cpp  
    // Replace the image named below  
    // with an icon of your own choosing.  
    pictureBox1->Image = Image::FromFile(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::MyPictures),  
       "\\Image.gif"));  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1f023-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f023-113">See Also</span></span>  
 <xref:System.Drawing.Image.FromFile%2A>  
 <xref:System.Drawing.Image>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>
