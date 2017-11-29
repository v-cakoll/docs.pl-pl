---
title: "Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant (formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9049bf5f9467401bff098459b8f5ed55c1ee1975
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="10377-102">Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="10377-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>
<span data-ttu-id="10377-103">Windows Forms <xref:System.Windows.Forms.PictureBox> sterowania, można załadować i wyświetlić obraz w formularzu w czasie projektowania, ustawiając <xref:System.Windows.Forms.PictureBox.Image%2A> właściwości nieprawidłowy obraz.</span><span class="sxs-lookup"><span data-stu-id="10377-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="10377-104">W poniższej tabeli przedstawiono typy plików akceptowane.</span><span class="sxs-lookup"><span data-stu-id="10377-104">The following table shows the acceptable file types.</span></span>  
  
|<span data-ttu-id="10377-105">Typ</span><span class="sxs-lookup"><span data-stu-id="10377-105">Type</span></span>|<span data-ttu-id="10377-106">Rozszerzenie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="10377-106">File name extension</span></span>|  
|----------|-------------------------|  
|<span data-ttu-id="10377-107">Mapy bitowej</span><span class="sxs-lookup"><span data-stu-id="10377-107">Bitmap</span></span>|<span data-ttu-id="10377-108">BMP</span><span class="sxs-lookup"><span data-stu-id="10377-108">.bmp</span></span>|  
|<span data-ttu-id="10377-109">Ikona</span><span class="sxs-lookup"><span data-stu-id="10377-109">Icon</span></span>|<span data-ttu-id="10377-110">ICO</span><span class="sxs-lookup"><span data-stu-id="10377-110">.ico</span></span>|  
|<span data-ttu-id="10377-111">GIF</span><span class="sxs-lookup"><span data-stu-id="10377-111">GIF</span></span>|<span data-ttu-id="10377-112">GIF</span><span class="sxs-lookup"><span data-stu-id="10377-112">.gif</span></span>|  
|<span data-ttu-id="10377-113">Metaplik</span><span class="sxs-lookup"><span data-stu-id="10377-113">Metafile</span></span>|<span data-ttu-id="10377-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="10377-114">.wmf</span></span>|  
|<span data-ttu-id="10377-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="10377-115">JPEG</span></span>|<span data-ttu-id="10377-116">jpg</span><span class="sxs-lookup"><span data-stu-id="10377-116">.jpg</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="10377-117">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="10377-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="10377-118">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="10377-118">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="10377-119">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="10377-119">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="10377-120">Aby wyświetlić obraz w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="10377-120">To display a picture at design time</span></span>  
  
1.  <span data-ttu-id="10377-121">Rysuj <xref:System.Windows.Forms.PictureBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="10377-121">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>  
  
2.  <span data-ttu-id="10377-122">W oknie właściwości, wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwości, a następnie kliknij przycisk wielokropka, aby wyświetlić **Otwórz** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="10377-122">On the Properties window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then click the ellipsis button to display the **Open** dialog box.</span></span>  
  
3.  <span data-ttu-id="10377-123">Jeśli szukasz dla określonego typu pliku (na przykład GIF), wybierz go w **pliki typu** pole.</span><span class="sxs-lookup"><span data-stu-id="10377-123">If you are looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>  
  
4.  <span data-ttu-id="10377-124">Wybierz plik, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="10377-124">Select the file you want to display.</span></span>  
  
### <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="10377-125">Aby wyczyścić obrazu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="10377-125">To clear the picture at design time</span></span>  
  
1.  <span data-ttu-id="10377-126">Na **właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwości i kliknij prawym przyciskiem myszy mały obraz miniatury, który wydaje się po lewej stronie nazwy obiektu obrazu.</span><span class="sxs-lookup"><span data-stu-id="10377-126">On the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property and right-click the small thumbnail image that appears to the left of the name of the image object.</span></span> <span data-ttu-id="10377-127">Wybierz **zresetować**.</span><span class="sxs-lookup"><span data-stu-id="10377-127">Choose **Reset**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10377-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10377-128">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 [<span data-ttu-id="10377-129">Informacje o formancie PictureBox</span><span class="sxs-lookup"><span data-stu-id="10377-129">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="10377-130">Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="10377-130">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="10377-131">Porady: ustawienie obrazów w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="10377-131">How to: Set Pictures at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-pictures-at-run-time-windows-forms.md)  
 [<span data-ttu-id="10377-132">PictureBox — formant</span><span class="sxs-lookup"><span data-stu-id="10377-132">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)
