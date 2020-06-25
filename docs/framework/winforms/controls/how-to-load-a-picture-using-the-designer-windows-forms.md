---
title: 'Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant'
description: Dowiedz się, jak za pomocą formantu PictureBox Windows Forms załadować i wyświetlić obraz w formularzu w czasie projektowania.
ms.date: 03/30/2017
helpviewer_keywords:
- picture formats
- images [Windows Forms], displaying on Windows Forms
- pictures [Windows Forms], displaying
- forms [Windows Forms], displaying images
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 4dc7b973-afb1-4276-8322-20825af96655
ms.openlocfilehash: a05ffe19412fc7a4e3e02f01336d89cce39fac8a
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325592"
---
# <a name="how-to-load-a-picture-using-the-designer-windows-forms"></a><span data-ttu-id="7ff93-103">Porady: dodawanie zdjęcia przy użyciu narzędzia Projektant (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="7ff93-103">How to: Load a Picture Using the Designer (Windows Forms)</span></span>

<span data-ttu-id="7ff93-104">Za pomocą <xref:System.Windows.Forms.PictureBox> kontrolki Windows Forms można załadować i wyświetlić obraz w formularzu w czasie projektowania, ustawiając <xref:System.Windows.Forms.PictureBox.Image%2A> Właściwość na prawidłowy obraz.</span><span class="sxs-lookup"><span data-stu-id="7ff93-104">With the Windows Forms <xref:System.Windows.Forms.PictureBox> control, you can load and display a picture on a form at design time by setting the <xref:System.Windows.Forms.PictureBox.Image%2A> property to a valid picture.</span></span> <span data-ttu-id="7ff93-105">W poniższej tabeli przedstawiono akceptowalne typy plików.</span><span class="sxs-lookup"><span data-stu-id="7ff93-105">The following table shows the acceptable file types.</span></span>

|<span data-ttu-id="7ff93-106">Typ</span><span class="sxs-lookup"><span data-stu-id="7ff93-106">Type</span></span>|<span data-ttu-id="7ff93-107">Rozszerzenie nazwy pliku</span><span class="sxs-lookup"><span data-stu-id="7ff93-107">File name extension</span></span>|
|---|---|
|<span data-ttu-id="7ff93-108">Mapy</span><span class="sxs-lookup"><span data-stu-id="7ff93-108">Bitmap</span></span>|<span data-ttu-id="7ff93-109">bmp</span><span class="sxs-lookup"><span data-stu-id="7ff93-109">.bmp</span></span>|
|<span data-ttu-id="7ff93-110">Ikona</span><span class="sxs-lookup"><span data-stu-id="7ff93-110">Icon</span></span>|<span data-ttu-id="7ff93-111">. ico</span><span class="sxs-lookup"><span data-stu-id="7ff93-111">.ico</span></span>|
|<span data-ttu-id="7ff93-112">GIF</span><span class="sxs-lookup"><span data-stu-id="7ff93-112">GIF</span></span>|<span data-ttu-id="7ff93-113">gif</span><span class="sxs-lookup"><span data-stu-id="7ff93-113">.gif</span></span>|
|<span data-ttu-id="7ff93-114">Metafile</span><span class="sxs-lookup"><span data-stu-id="7ff93-114">Metafile</span></span>|<span data-ttu-id="7ff93-115">. wmf</span><span class="sxs-lookup"><span data-stu-id="7ff93-115">.wmf</span></span>|
|<span data-ttu-id="7ff93-116">JPEG</span><span class="sxs-lookup"><span data-stu-id="7ff93-116">JPEG</span></span>|<span data-ttu-id="7ff93-117">jpg</span><span class="sxs-lookup"><span data-stu-id="7ff93-117">.jpg</span></span>|

## <a name="to-display-a-picture-at-design-time"></a><span data-ttu-id="7ff93-118">Aby wyświetlić obraz w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="7ff93-118">To display a picture at design time</span></span>

1. <span data-ttu-id="7ff93-119">Narysuj <xref:System.Windows.Forms.PictureBox> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="7ff93-119">Draw a <xref:System.Windows.Forms.PictureBox> control on a form.</span></span>

2. <span data-ttu-id="7ff93-120">W oknie **Właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> Właściwość, a następnie wybierz przycisk wielokropka, aby wyświetlić okno dialogowe **Otwórz** .</span><span class="sxs-lookup"><span data-stu-id="7ff93-120">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property, then select the ellipsis button to display the **Open** dialog box.</span></span>

3. <span data-ttu-id="7ff93-121">Jeśli szukasz określonego typu pliku (na przykład plików GIF), wybierz go w polu **Pliki typu** .</span><span class="sxs-lookup"><span data-stu-id="7ff93-121">If you're looking for a specific file type (for example, .gif files), select it in the **Files of type** box.</span></span>

4. <span data-ttu-id="7ff93-122">Wybierz plik, który chcesz wyświetlić.</span><span class="sxs-lookup"><span data-stu-id="7ff93-122">Select the file you want to display.</span></span>

## <a name="to-clear-the-picture-at-design-time"></a><span data-ttu-id="7ff93-123">Aby wyczyścić obraz w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="7ff93-123">To clear the picture at design time</span></span>

1. <span data-ttu-id="7ff93-124">W oknie **Właściwości** wybierz <xref:System.Windows.Forms.PictureBox.Image%2A> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="7ff93-124">In the **Properties** window, select the <xref:System.Windows.Forms.PictureBox.Image%2A> property.</span></span> <span data-ttu-id="7ff93-125">Kliknij prawym przyciskiem myszy mały obraz miniatury, który pojawia się po lewej stronie nazwy obiektu obrazu, a następnie wybierz polecenie **Zresetuj**.</span><span class="sxs-lookup"><span data-stu-id="7ff93-125">Right-click the small thumbnail image that appears to the left of the name of the image object, and then choose **Reset**.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ff93-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7ff93-126">See also</span></span>

- <xref:System.Windows.Forms.PictureBox>
- [<span data-ttu-id="7ff93-127">PictureBox — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="7ff93-127">PictureBox Control Overview</span></span>](picturebox-control-overview-windows-forms.md)
- [<span data-ttu-id="7ff93-128">Instrukcje: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="7ff93-128">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)
- [<span data-ttu-id="7ff93-129">Instrukcje: ustawienie obrazów w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="7ff93-129">How to: Set Pictures at Run Time</span></span>](how-to-set-pictures-at-run-time-windows-forms.md)
- [<span data-ttu-id="7ff93-130">PictureBox — Formant</span><span class="sxs-lookup"><span data-stu-id="7ff93-130">PictureBox Control</span></span>](picturebox-control-windows-forms.md)
