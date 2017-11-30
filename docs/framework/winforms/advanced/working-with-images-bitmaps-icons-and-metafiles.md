---
title: Praca z obrazami, mapami bitowymi, ikonami i metaplikami
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53dc25d6a23c5cdbba1c640905eadbdc6b1acb71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="ac7e6-102">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="ac7e6-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="ac7e6-103">udostępnia `Bitmap` klasy do pracy z obrazów rastrowych i `Metafile` klasy do pracy z obrazami wektora.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-103"> provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="ac7e6-104">`Bitmap` i `Metafile` klasy zarówno dziedziczą `Image` klasy.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac7e6-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ac7e6-105">In This Section</span></span>  
 [<span data-ttu-id="ac7e6-106">Porady: Rysowanie istniejącej mapy bitowej na ekranie</span><span class="sxs-lookup"><span data-stu-id="ac7e6-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="ac7e6-107">Opisuje sposób załadować i rysowanie map bitowych.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="ac7e6-108">Porady: ładowanie i wyświetlanie metaplików</span><span class="sxs-lookup"><span data-stu-id="ac7e6-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="ac7e6-109">Przedstawia sposób ładowania i rysowanie metapliki.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="ac7e6-110">Przycinanie i skalowanie obrazów w GDI +</span><span class="sxs-lookup"><span data-stu-id="ac7e6-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="ac7e6-111">Wyjaśniono, jak przycinanie i skalowanie obrazów wektorowe i rastrowe.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="ac7e6-112">Porady: obracanie, odzwierciedlanie i pochylanie obrazów</span><span class="sxs-lookup"><span data-stu-id="ac7e6-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="ac7e6-113">Opisuje sposób rysowania obracany, odbitych i spowodowałoby zafałszowanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="ac7e6-114">Porady: używanie trybu interpolacji do sterowania jakością obrazu w czasie skalowania</span><span class="sxs-lookup"><span data-stu-id="ac7e6-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="ac7e6-115">Przedstawia sposób użycia <xref:System.Drawing.Drawing2D.InterpolationMode> wyliczeniu, aby zmienić jakości obrazu.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="ac7e6-116">Porady: tworzenie obrazów miniatur</span><span class="sxs-lookup"><span data-stu-id="ac7e6-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="ac7e6-117">Zawiera opis sposobu tworzenia obrazów miniatur.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="ac7e6-118">Porady: poprawianie wydajności dzięki unikaniu automatycznego skalowania</span><span class="sxs-lookup"><span data-stu-id="ac7e6-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="ac7e6-119">Wyjaśniono, jak narysować obraz bez skalowania automatycznego.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="ac7e6-120">Porady: odczytywanie metadanych obrazu</span><span class="sxs-lookup"><span data-stu-id="ac7e6-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="ac7e6-121">Opisuje sposób odczytać metadanych z obrazu.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="ac7e6-122">Porady: Tworzenie mapy bitowej w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="ac7e6-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="ac7e6-123">Przedstawiono sposób rysowania mapy bitowej w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="ac7e6-124">Porady: wyodrębnianie ikon skojarzonych z plikiem w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ac7e6-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="ac7e6-125">Opisuje sposób wyodrębnić ikonę, która jest osadzony zasób pliku.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ac7e6-126">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ac7e6-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="ac7e6-127">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="ac7e6-128">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="ac7e6-129">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ac7e6-130">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ac7e6-130">Related Sections</span></span>  
 [<span data-ttu-id="ac7e6-131">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="ac7e6-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="ac7e6-132">Zawiera linki do tematów, w których omówiono różne typy map bitowych i manipulowania nimi w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ac7e6-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
