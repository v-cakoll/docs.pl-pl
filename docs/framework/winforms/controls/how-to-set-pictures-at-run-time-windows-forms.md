---
title: 'Porady: ustawienie obrazów w czasie wykonywania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
ms.openlocfilehash: bd0509c05fd9c1cfc0c631fcd613c64d20296f6b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746736"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="11c32-102">Porady: ustawienie obrazów w czasie wykonywania (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="11c32-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="11c32-103">Można programowo ustawić obraz wyświetlany przez kontrolkę <xref:System.Windows.Forms.PictureBox> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="11c32-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="11c32-104">Aby programowo ustawić obraz</span><span class="sxs-lookup"><span data-stu-id="11c32-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="11c32-105">Ustaw właściwość <xref:System.Windows.Forms.PictureBox.Image%2A> przy użyciu metody <xref:System.Drawing.Image.FromFile%2A> klasy <xref:System.Drawing.Image>.</span><span class="sxs-lookup"><span data-stu-id="11c32-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="11c32-106">W poniższym przykładzie ścieżką ustawioną dla lokalizacji obrazu jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="11c32-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="11c32-107">Dzieje się tak, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog.</span><span class="sxs-lookup"><span data-stu-id="11c32-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="11c32-108">Pozwala to również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11c32-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="11c32-109">W poniższym przykładzie założono, że formularz z kontrolką <xref:System.Windows.Forms.PictureBox> został już dodany.</span><span class="sxs-lookup"><span data-stu-id="11c32-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="11c32-110">Aby wyczyścić grafikę</span><span class="sxs-lookup"><span data-stu-id="11c32-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="11c32-111">Po pierwsze zwolnij pamięć używaną przez obraz, a następnie wyczyść grafikę.</span><span class="sxs-lookup"><span data-stu-id="11c32-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="11c32-112">Wyrzucanie elementów bezużytecznych zwalnia pamięć później, jeśli zarządzanie pamięcią zostanie problemem.</span><span class="sxs-lookup"><span data-stu-id="11c32-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="11c32-113">Aby uzyskać więcej informacji na temat tego, dlaczego należy używać metody <xref:System.Drawing.Image.Dispose%2A> w ten sposób, zobacz [Oczyszczanie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="11c32-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="11c32-114">Ten kod spowoduje wyczyszczenie obrazu nawet wtedy, gdy grafika została załadowana do kontrolki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="11c32-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11c32-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11c32-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="11c32-116">PictureBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="11c32-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="11c32-117">Instrukcje: dodawanie zdjęcia przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="11c32-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="11c32-118">Instrukcje: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="11c32-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="11c32-119">PictureBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="11c32-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
