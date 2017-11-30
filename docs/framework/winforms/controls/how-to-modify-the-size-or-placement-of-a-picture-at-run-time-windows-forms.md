---
title: "Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (Formularze systemu Windows)"
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
- images [Windows Forms], controlling placement in PictureBox control [Windows Forms]
- examples [Windows Forms], PictureBox control
- PictureBox control [Windows Forms], picture size and alignment
- pictures [Windows Forms], controlling placement in PictureBox control [Windows Forms]
ms.assetid: d0b332a3-fae2-4891-957c-dc3e17743326
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: df67871b0b133297a6f53ff9e4a42c7630a5f56d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms"></a><span data-ttu-id="9bdea-102">Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="9bdea-102">How to: Modify the Size or Placement of a Picture at Run Time (Windows Forms)</span></span>
<span data-ttu-id="9bdea-103">Jeśli używasz interfejsu Windows Forms <xref:System.Windows.Forms.PictureBox> kontrolki na formularzu, można ustawić <xref:System.Windows.Forms.PictureBox.SizeMode%2A> właściwości w celu:</span><span class="sxs-lookup"><span data-stu-id="9bdea-103">If you use the Windows Forms <xref:System.Windows.Forms.PictureBox> control on a form, you can set the <xref:System.Windows.Forms.PictureBox.SizeMode%2A> property on it to:</span></span>  
  
-   <span data-ttu-id="9bdea-104">Wyrównanie obrazu lewym górnym rogu z lewym górnym rogu formantu</span><span class="sxs-lookup"><span data-stu-id="9bdea-104">Align the picture's upper left corner with the control's upper left corner</span></span>  
  
-   <span data-ttu-id="9bdea-105">Centrum obrazów w formancie</span><span class="sxs-lookup"><span data-stu-id="9bdea-105">Center the picture within the control</span></span>  
  
-   <span data-ttu-id="9bdea-106">Dopasuj rozmiar formantu w celu dopasowania obraz, który zawiera</span><span class="sxs-lookup"><span data-stu-id="9bdea-106">Adjust the size of the control to fit the picture it displays</span></span>  
  
-   <span data-ttu-id="9bdea-107">Rozciąganie obrazu wyświetla do rozmiaru formantu</span><span class="sxs-lookup"><span data-stu-id="9bdea-107">Stretch any picture it displays to fit the control</span></span>  
  
 <span data-ttu-id="9bdea-108">Rozciąganie obrazu (szczególnie jeden format mapy bitowej) może spowodować utratę jakości obrazu.</span><span class="sxs-lookup"><span data-stu-id="9bdea-108">Stretching a picture (especially one in bitmap format) can produce a loss in image quality.</span></span> <span data-ttu-id="9bdea-109">Metapliki, które list grafiki instrukcje dotyczące rysowanie obrazów w czasie wykonywania, są lepiej dostosowane do rozciągania niż map bitowych.</span><span class="sxs-lookup"><span data-stu-id="9bdea-109">Metafiles, which are lists of graphics instructions for drawing images at run time, are better suited for stretching than bitmaps are.</span></span>  
  
### <a name="to-set-the-sizemode-property-at-run-time"></a><span data-ttu-id="9bdea-110">Można ustawić właściwości SizeMode w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="9bdea-110">To set the SizeMode property at run time</span></span>  
  
1.  <span data-ttu-id="9bdea-111">Ustaw <xref:System.Windows.Forms.PictureBox.SizeMode%2A> do <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (ustawienie domyślne), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, lub <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span><span class="sxs-lookup"><span data-stu-id="9bdea-111">Set <xref:System.Windows.Forms.PictureBox.SizeMode%2A> to <xref:System.Windows.Forms.PictureBoxSizeMode.Normal> (the default), <xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>, <xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>, or <xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>.</span></span> <span data-ttu-id="9bdea-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal>oznacza, że obraz jest umieszczany w formantu lewego górnego rogu; Jeśli obraz jest większy niż formant, jego dolnej i prawej krawędzi są obcinane.</span><span class="sxs-lookup"><span data-stu-id="9bdea-112"><xref:System.Windows.Forms.PictureBoxSizeMode.Normal> means that the image is placed in the control's upper-left corner; if the image is larger than the control, its lower and right edges are clipped.</span></span> <span data-ttu-id="9bdea-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage>oznacza, że obraz jest wyśrodkowywany względem kontroli. Jeśli obraz jest większy niż formant, zewnętrznej krawędzi obrazu są obcinane.</span><span class="sxs-lookup"><span data-stu-id="9bdea-113"><xref:System.Windows.Forms.PictureBoxSizeMode.CenterImage> means that the image is centered within the control; if the image is larger than the control, the picture's outside edges are clipped.</span></span> <span data-ttu-id="9bdea-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize>oznacza, że rozmiar formantu zostanie dopasowana do rozmiaru obrazu.</span><span class="sxs-lookup"><span data-stu-id="9bdea-114"><xref:System.Windows.Forms.PictureBoxSizeMode.AutoSize> means that the size of the control is adjusted to the size of the image.</span></span> <span data-ttu-id="9bdea-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage>jest odwrotna i oznacza, że rozmiar obrazu jest dostosowana do rozmiaru formantu.</span><span class="sxs-lookup"><span data-stu-id="9bdea-115"><xref:System.Windows.Forms.PictureBoxSizeMode.StretchImage> is the reverse, and means that the size of the image is adjusted to the size of the control.</span></span>  
  
     <span data-ttu-id="9bdea-116">W poniższym przykładzie ścieżka zestawu dla lokalizacji obrazu jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="9bdea-116">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="9bdea-117">Tej operacji, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="9bdea-117">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="9bdea-118">To umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9bdea-118">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="9bdea-119">W poniższym przykładzie założono formularza z <xref:System.Windows.Forms.PictureBox> kontroli już dodany.</span><span class="sxs-lookup"><span data-stu-id="9bdea-119">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9bdea-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9bdea-120">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="9bdea-121">Porady: Dodawanie zdjęcia przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="9bdea-121">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="9bdea-122">Informacje o formancie PictureBox</span><span class="sxs-lookup"><span data-stu-id="9bdea-122">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="9bdea-123">Porady: ustawienie obrazów w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="9bdea-123">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="9bdea-124">PictureBox — formant</span><span class="sxs-lookup"><span data-stu-id="9bdea-124">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
