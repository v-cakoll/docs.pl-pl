---
title: 'Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania'
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
ms.openlocfilehash: fea813d7b9fe585e35b729b8b64e3a5f414ef76d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141969"
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="dd0af-102">Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="dd0af-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="dd0af-103">Jeśli używasz formantu Windows Forms <xref:System.Windows.Forms.PictureBox> w <xref:System.Windows.Forms.PictureBox.SizeMode%2A> formularzu, można ustawić właściwość na nim:</span><span class="sxs-lookup"><span data-stu-id="dd0af-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
- <span data-ttu-id="dd0af-104">Wyrównaj lewy górny róg obrazu z lewym górnym rogu formantu</span><span class="sxs-lookup"><span data-stu-id="dd0af-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
- <span data-ttu-id="dd0af-105">Wyśrodkuj obraz w formancie</span><span class="sxs-lookup"><span data-stu-id="dd0af-105">Center the picture within the control</span></span>  
  
- <span data-ttu-id="dd0af-106">Dostosuj rozmiar formantu do wyświetlanego obrazu</span><span class="sxs-lookup"><span data-stu-id="dd0af-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
- <span data-ttu-id="dd0af-107">Rozciągnij dowolny obraz, który wyświetli, aby dopasować go do</span><span class="sxs-lookup"><span data-stu-id="dd0af-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="dd0af-108">Rozciąganie obrazu (zwłaszcza w formacie bitmapowym) może spowodować utratę jakości obrazu.</span><span class="sxs-lookup"><span data-stu-id="dd0af-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="dd0af-109">Metafile, które są listami instrukcji graficznych do rysowania obrazów w czasie wykonywania, lepiej nadają się do rozciągania niż mapy bitowe.</span><span class="sxs-lookup"><span data-stu-id="dd0af-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="dd0af-110">Aby ustawić właściwość SizeMode w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="dd0af-110">To set the SizeMode property at run time</span></span>  
  
1. <span data-ttu-id="dd0af-111">Ustaw <xref:System.Windows.Forms.PictureBox.SizeMode%2A> <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> na (domyślnie), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>lub <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="dd0af-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="dd0af-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>oznacza, że obraz jest umieszczony w lewym górnym rogu formantu; jeśli obraz jest większy niż formant, jego dolna i prawa krawędź są przycinane.</span><span class="sxs-lookup"><span data-stu-id="dd0af-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="dd0af-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>oznacza, że obraz jest wyśrodkowany w formancie; jeśli obraz jest większy niż formant, krawędzie zewnętrzne obrazu zostaną przycięte.</span><span class="sxs-lookup"><span data-stu-id="dd0af-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="dd0af-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>oznacza, że rozmiar formantu jest dostosowany do rozmiaru obrazu.</span><span class="sxs-lookup"><span data-stu-id="dd0af-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="dd0af-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>jest odwrotna i oznacza, że rozmiar obrazu jest dostosowany do rozmiaru formantu.</span><span class="sxs-lookup"><span data-stu-id="dd0af-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="dd0af-116">W poniższym przykładzie ścieżką ustawioną dla lokalizacji obrazu jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="dd0af-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="dd0af-117">Odbywa się to, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać ten katalog.</span><span class="sxs-lookup"><span data-stu-id="dd0af-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="dd0af-118">Umożliwia to również użytkownikom z minimalnymi poziomami dostępu do systemu bezpieczne uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd0af-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="dd0af-119">Poniższy przykład zakłada formularz <xref:System.Windows.Forms.PictureBox> z formantu już dodane.</span><span class="sxs-lookup"><span data-stu-id="dd0af-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd0af-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd0af-120">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="dd0af-121">Instrukcje: dodawanie zdjęcia przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="dd0af-121">How to: Load a Picture Using the Designer</span></span>](how-to-load-a-picture-using-the-designer-windows-forms.md)
- [<span data-ttu-id="dd0af-122">PictureBox — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="dd0af-122">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="dd0af-123">Instrukcje: ustawienie obrazów w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="dd0af-123">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="dd0af-124">PictureBox — Formant</span><span class="sxs-lookup"><span data-stu-id="dd0af-124">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
