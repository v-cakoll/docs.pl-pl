---
title: 'Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (formularze Windows)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
ms.openlocfilehash: d0a86d7fe53dba3da6bd63587561f82877bc2f06
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59328338"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="8af20-102">Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="8af20-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="8af20-103">Jeśli używasz formularzy Windows <xref:System.Windows.Forms.PictureBox> formantu w formularzu, można ustawić <xref:System.Windows.Forms.PictureBox.SizeMode%2A> właściwości na niej w celu:</span><span class="sxs-lookup"><span data-stu-id="8af20-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="8af20-104">Wyrównanie obrazu lewy górny róg za pomocą lewego górnego rogu kontrolki</span><span class="sxs-lookup"><span data-stu-id="8af20-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="8af20-105">Wyśrodkuj obraz w kontrolce</span><span class="sxs-lookup"><span data-stu-id="8af20-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="8af20-106">Dopasuj rozmiar formantu, aby dopasować go do jego wyświetlania</span><span class="sxs-lookup"><span data-stu-id="8af20-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="8af20-107">Rozciąganie dowolnego obrazu wyświetla do rozmiaru formantu</span><span class="sxs-lookup"><span data-stu-id="8af20-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="8af20-108">Rozciąganie obrazu (szczególnie jeden format mapy bitowej) może spowodować utratę jakości obrazu.</span><span class="sxs-lookup"><span data-stu-id="8af20-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="8af20-109">Metapliki, które listy instrukcji grafiki rysowanie obrazów w czasie wykonywania, są lepiej dostosowane do rozciągania niż Mapy bitowe mają rozmiar.</span><span class="sxs-lookup"><span data-stu-id="8af20-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="8af20-110">Aby ustawić właściwość SizeMode w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="8af20-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="8af20-111">Ustaw <xref:System.Windows.Forms.PictureBox.SizeMode%2A> do <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (ustawienie domyślne), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, lub <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="8af20-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> <span data-ttu-id="8af20-112">oznacza, że obraz jest umieszczany w formantu lewego górnego rogu; obraz, który jest większy niż formant, powoduje jej dolnej i prawej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="8af20-112">means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> <span data-ttu-id="8af20-113">oznacza, że obraz jest wyśrodkowywana względem kontroli. obraz, który jest większy niż formant, powoduje zewnętrznymi krawędziami obrazu.</span><span class="sxs-lookup"><span data-stu-id="8af20-113">means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> <span data-ttu-id="8af20-114">oznacza to, że rozmiar formantu jest dostosowywana do rozmiaru obrazu.</span><span class="sxs-lookup"><span data-stu-id="8af20-114">means that the size of the control is adjusted to the size of the image.</span></span> <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> <span data-ttu-id="8af20-115">jest odwrotna i oznacza, że rozmiar obrazu jest dostosowywana do rozmiaru formantu.</span><span class="sxs-lookup"><span data-stu-id="8af20-115">is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="8af20-116">W poniższym przykładzie ścieżka lokalizacji obrazu jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="8af20-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="8af20-117">Jest to wykonywane, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8af20-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="8af20-118">Ponadto pozwala to użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8af20-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="8af20-119">W poniższym przykładzie przyjęto założenie, formularz z <xref:System.Windows.Forms.PictureBox> formant został już dodany.</span><span class="sxs-lookup"><span data-stu-id="8af20-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub StretchPic()  
       ' Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage  
       ' Load the picture into the control.  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void StretchPic(){  
       // Stretch the picture to fit the control.  
       PictureBox1.SizeMode = PictureBoxSizeMode.StretchImage;  
       // Load the picture into the control.  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Image.gif")  
    }  
    ```  
  
    ```cpp  
    private:  
       void StretchPic()  
       {  
          // Stretch the picture to fit the control.  
          pictureBox1->SizeMode = PictureBoxSizeMode::StretchImage;  
          // Load the picture into the control.  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8af20-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8af20-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="8af20-121">Instrukcje: dodawanie zdjęcia przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="8af20-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="8af20-122">PictureBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="8af20-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="8af20-123">Instrukcje: ustawienie obrazów w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="8af20-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="8af20-124">PictureBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="8af20-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
