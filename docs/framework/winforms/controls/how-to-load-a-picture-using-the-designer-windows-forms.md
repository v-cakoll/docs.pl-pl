---
title: 'Instrukcje: Ładowanie obrazu przy użyciu narzędzia Projektant (Windows Forms)'
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: 818bc63b5b3bea6c73804f716a72ba3cd1a62b4c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039679"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="85c47-102">Instrukcje: Ładowanie obrazu przy użyciu narzędzia Projektant (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="85c47-102">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="85c47-103">Za pomocą kontrolki Windows Forms <xref:System.Windows.Forms.PictureBox> można załadować i wyświetlić obraz w formularzu w czasie projektowania, <xref:System.Windows.Forms.PictureBox.Image%2A> ustawiając właściwość na prawidłowy obraz.</span><span class="sxs-lookup"><span data-stu-id="85c47-103">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="85c47-104">W poniższej tabeli przedstawiono akceptowalne typy plików.</span><span class="sxs-lookup"><span data-stu-id="85c47-104">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="85c47-105">Typ</span><span class="sxs-lookup"><span data-stu-id="85c47-105">Type</span></span>|<span data-ttu-id="85c47-106">Rozszerzenie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="85c47-106">File name extension</span></span>|
|---|---|
|<span data-ttu-id="85c47-107">Mapy</span><span class="sxs-lookup"><span data-stu-id="85c47-107">Bitmap</span></span>|<span data-ttu-id="85c47-108">.bmp</span><span class="sxs-lookup"><span data-stu-id="85c47-108">.bmp</span></span>|
|<span data-ttu-id="85c47-109">Ikona</span><span class="sxs-lookup"><span data-stu-id="85c47-109">Icon</span></span>|<span data-ttu-id="85c47-110">.ico</span><span class="sxs-lookup"><span data-stu-id="85c47-110">.ico</span></span>|
|<span data-ttu-id="85c47-111">GIF</span><span class="sxs-lookup"><span data-stu-id="85c47-111">GIF</span></span>|<span data-ttu-id="85c47-112">.gif</span><span class="sxs-lookup"><span data-stu-id="85c47-112">.gif</span></span>|
|<span data-ttu-id="85c47-113">Metafile</span><span class="sxs-lookup"><span data-stu-id="85c47-113">Metafile</span></span>|<span data-ttu-id="85c47-114">.wmf</span><span class="sxs-lookup"><span data-stu-id="85c47-114">.wmf</span></span>|
|<span data-ttu-id="85c47-115">JPEG</span><span class="sxs-lookup"><span data-stu-id="85c47-115">JPEG</span></span>|<span data-ttu-id="85c47-116">.jpg</span><span class="sxs-lookup"><span data-stu-id="85c47-116">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="85c47-117">Aby wyświetlić obraz w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="85c47-117">To display a picture at design time</span></span>

1. <span data-ttu-id="85c47-118">Narysuj <xref:System.Windows.Forms.PictureBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="85c47-118">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="85c47-119">W oknie **Właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwość, a następnie wybierz przycisk wielokropka, aby wyświetlić okno dialogowe **Otwórz** .</span><span class="sxs-lookup"><span data-stu-id="85c47-119">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="85c47-120">Jeśli szukasz określonego typu pliku (na przykład plików GIF), wybierz go w polu **Pliki typu** .</span><span class="sxs-lookup"><span data-stu-id="85c47-120">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="85c47-121">Wybierz plik, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="85c47-121">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="85c47-122">Aby wyczyścić obraz w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="85c47-122">To clear the picture at design time</span></span>

1. <span data-ttu-id="85c47-123">W oknie **Właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> właściwość.</span><span class="sxs-lookup"><span data-stu-id="85c47-123">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="85c47-124">Kliknij prawym przyciskiem myszy mały obraz miniatury, który pojawia się po lewej stronie nazwy obiektu obrazu, a następnie wybierz polecenie **Zresetuj**.</span><span class="sxs-lookup"><span data-stu-id="85c47-124">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="85c47-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="85c47-125">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="85c47-126">PictureBox, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="85c47-126">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="85c47-127">Instrukcje: Modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="85c47-127">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="85c47-128">Instrukcje: Ustawianie obrazów w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="85c47-128">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="85c47-129">PictureBox, kontrolka</span><span class="sxs-lookup"><span data-stu-id="85c47-129">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
