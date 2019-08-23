---
title: 'Instrukcje: Ustaw obrazy w czasie wykonywania (Windows Forms)'
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
ms.openlocfilehash: 99d78a275c8ad8f55d9b0832a794545b65da7e20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917527"
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="6172e-102">Instrukcje: Ustaw obrazy w czasie wykonywania (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6172e-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="6172e-103">Można programowo ustawić obraz wyświetlany przez kontrolkę Windows Forms <xref:System.Windows.Forms.PictureBox> .</span><span class="sxs-lookup"><span data-stu-id="6172e-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="6172e-104">Aby programowo ustawić obraz</span><span class="sxs-lookup"><span data-stu-id="6172e-104">To set a picture programmatically</span></span>  
  
- <span data-ttu-id="6172e-105">Ustaw właściwość przy użyciu <xref:System.Drawing.Image>metodyklasy. <xref:System.Drawing.Image.FromFile%2A> <xref:System.Windows.Forms.PictureBox.Image%2A></span><span class="sxs-lookup"><span data-stu-id="6172e-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="6172e-106">W poniższym przykładzie ścieżką ustawioną dla lokalizacji obrazu jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="6172e-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="6172e-107">Dzieje się tak, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog.</span><span class="sxs-lookup"><span data-stu-id="6172e-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="6172e-108">Pozwala to również użytkownikom z minimalnymi poziomami dostępu do systemu w celu bezpiecznego uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6172e-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="6172e-109">W poniższym przykładzie założono, że formularz <xref:System.Windows.Forms.PictureBox> z kontrolką został już dodany.</span><span class="sxs-lookup"><span data-stu-id="6172e-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="6172e-110">Aby wyczyścić grafikę</span><span class="sxs-lookup"><span data-stu-id="6172e-110">To clear a graphic</span></span>  
  
- <span data-ttu-id="6172e-111">Po pierwsze zwolnij pamięć używaną przez obraz, a następnie wyczyść grafikę.</span><span class="sxs-lookup"><span data-stu-id="6172e-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="6172e-112">Wyrzucanie elementów bezużytecznych zwalnia pamięć później, jeśli zarządzanie pamięcią zostanie problemem.</span><span class="sxs-lookup"><span data-stu-id="6172e-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
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
    > <span data-ttu-id="6172e-113">Aby uzyskać więcej informacji na temat tego, dlaczego <xref:System.Drawing.Image.Dispose%2A> należy używać metody w ten sposób, zobacz [Oczyszczanie zasobów niezarządzanych](../../../standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="6172e-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="6172e-114">Ten kod spowoduje wyczyszczenie obrazu nawet wtedy, gdy grafika została załadowana do kontrolki w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="6172e-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6172e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6172e-115">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6172e-116">PictureBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="6172e-116">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="6172e-117">Instrukcje: Ładowanie obrazu przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="6172e-117">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="6172e-118">Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="6172e-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="6172e-119">PictureBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="6172e-119">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
