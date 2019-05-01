---
title: 'Instrukcje: Zdjęcia przy użyciu narzędzia Projektant (formularze Windows)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 6bdf7c3df0ffd97dd88a4c442a8a73593a0447ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941066"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="0c23b-102">Instrukcje: Zdjęcia przy użyciu narzędzia Projektant (formularze Windows)</span><span class="sxs-lookup"><span data-stu-id="0c23b-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>
<span data-ttu-id="0c23b-103">Za pomocą interfejsu Windows Forms <xref:System.Windows.Forms.PictureBox> kontrolki, można załadować i wyświetlania obrazu w postaci, w czasie projektowania, ustawiając <xref:System.Windows.Forms.PictureBox.Image%2A> właściwość prawidłowy obraz.</span><span class="sxs-lookup"><span data-stu-id="0c23b-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="0c23b-104">W poniższej tabeli przedstawiono typy plików dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="0c23b-104">The following table shows the acceptable file types.</span></span>  
  
|<span data-ttu-id="0c23b-105">Typ</span><span class="sxs-lookup"><span data-stu-id="0c23b-105">Type</span></span>|<span data-ttu-id="0c23b-106">Rozszerzenie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="0c23b-106">File name extension</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="0c23b-107">Mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="0c23b-107">Bitmap</span></span>|<span data-ttu-id="0c23b-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="0c23b-108">.bmp</span></span>|  
|<span data-ttu-id="0c23b-109">Ikona</span><span class="sxs-lookup"><span data-stu-id="0c23b-109">Icon</span></span>|<span data-ttu-id="0c23b-110">.ico</span><span class="sxs-lookup"><span data-stu-id="0c23b-110">.ico</span></span>|  
|<span data-ttu-id="0c23b-111">GIF</span><span class="sxs-lookup"><span data-stu-id="0c23b-111">GIF</span></span>|<span data-ttu-id="0c23b-112">.gif</span><span class="sxs-lookup"><span data-stu-id="0c23b-112">.gif</span></span>|  
|<span data-ttu-id="0c23b-113">Metafile</span><span class="sxs-lookup"><span data-stu-id="0c23b-113">Metafile</span></span>|<span data-ttu-id="0c23b-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="0c23b-114">.wmf</span></span>|  
|<span data-ttu-id="0c23b-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="0c23b-115">JPEG</span></span>|<span data-ttu-id="0c23b-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="0c23b-116">.jpg</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="0c23b-117">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="0c23b-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0c23b-118">Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="0c23b-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0c23b-119">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0c23b-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="0c23b-120">Aby wyświetlić obraz w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="0c23b-120">To display a picture at design time</span></span>  
  
1. <span data-ttu-id="0c23b-121">Rysowanie <xref:System.Windows.Forms.PictureBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="0c23b-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>  
  
2. <span data-ttu-id="0c23b-122">W oknie dialogowym właściwości wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwości, a następnie kliknij przycisk wielokropka, aby wyświetlić **Otwórz** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="0c23b-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>  
  
3. <span data-ttu-id="0c23b-123">Jeśli potrzebujesz określonego typu pliku (na przykład pliki GIF), wybierz ją w **pliki typu** pole.</span><span class="sxs-lookup"><span data-stu-id="0c23b-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>  
  
4. <span data-ttu-id="0c23b-124">Wybierz plik, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="0c23b-124">Select the file you want to display.</span></span>  
  
### <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="0c23b-125">Aby wyczyścić obrazu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="0c23b-125">To clear the picture at design time</span></span>  
  
1. <span data-ttu-id="0c23b-126">Na **właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwości i kliknij prawym przyciskiem myszy mały obraz miniatury, który pojawia się po lewej stronie nazwy obiektu obrazu.</span><span class="sxs-lookup"><span data-stu-id="0c23b-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="0c23b-127">Wybierz **resetowania**.</span><span class="sxs-lookup"><span data-stu-id="0c23b-127">Choose **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c23b-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c23b-128">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="0c23b-129">PictureBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="0c23b-129">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="0c23b-130">Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="0c23b-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="0c23b-131">Instrukcje: Ustawienie obrazów w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="0c23b-131">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="0c23b-132">PictureBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="0c23b-132">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
