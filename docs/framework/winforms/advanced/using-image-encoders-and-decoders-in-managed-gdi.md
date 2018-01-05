---
title: "Używanie kodeków obrazu w zarządzanym GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 084e8ff21e308cc20b633719dd31809b96b3c79a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="45637-102">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="45637-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="45637-103"><xref:System.Drawing> Przestrzeń nazw zawiera <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> klasy do przechowywania i manipulowanie obrazów.</span><span class="sxs-lookup"><span data-stu-id="45637-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="45637-104">Za pomocą kodery obrazów w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], można zapisać obrazy z pamięci na dysku.</span><span class="sxs-lookup"><span data-stu-id="45637-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="45637-105">Za pomocą dekodery obrazów w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], można załadować obrazów z dysku do pamięci.</span><span class="sxs-lookup"><span data-stu-id="45637-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="45637-106">Koder tłumaczy dane w <xref:System.Drawing.Image> lub <xref:System.Drawing.Bitmap> obiekt do formatu pliku wyznaczonych dysku.</span><span class="sxs-lookup"><span data-stu-id="45637-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="45637-107">Dekoder tłumaczy dane w pliku dysku format wymagany przez <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="45637-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="45637-108">zawiera wbudowane kodeków obsługujących następujące typy plików:</span><span class="sxs-lookup"><span data-stu-id="45637-108"> has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="45637-109">BMP</span><span class="sxs-lookup"><span data-stu-id="45637-109">BMP</span></span>  
  
-   <span data-ttu-id="45637-110">GIF</span><span class="sxs-lookup"><span data-stu-id="45637-110">GIF</span></span>  
  
-   <span data-ttu-id="45637-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="45637-111">JPEG</span></span>  
  
-   <span data-ttu-id="45637-112">PNG</span><span class="sxs-lookup"><span data-stu-id="45637-112">PNG</span></span>  
  
-   <span data-ttu-id="45637-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="45637-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="45637-114">ma również wbudowane dekoderów, które obsługują następujące typy plików:</span><span class="sxs-lookup"><span data-stu-id="45637-114"> also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="45637-115">WMF</span><span class="sxs-lookup"><span data-stu-id="45637-115">WMF</span></span>  
  
-   <span data-ttu-id="45637-116">EMF</span><span class="sxs-lookup"><span data-stu-id="45637-116">EMF</span></span>  
  
-   <span data-ttu-id="45637-117">IKONA</span><span class="sxs-lookup"><span data-stu-id="45637-117">ICON</span></span>  
  
 <span data-ttu-id="45637-118">W poniższych tematach opisano kodeków bardziej szczegółowo:</span><span class="sxs-lookup"><span data-stu-id="45637-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45637-119">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="45637-119">In This Section</span></span>  
 [<span data-ttu-id="45637-120">Instrukcje: lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="45637-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="45637-121">Opisuje sposób listy koderów dostępne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="45637-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="45637-122">Instrukcje: lista zainstalowanych dekoderów</span><span class="sxs-lookup"><span data-stu-id="45637-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="45637-123">Opisuje sposób wyświetlania dekodery dostępne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="45637-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="45637-124">Instrukcje: określanie parametrów obsługiwanych przez koder</span><span class="sxs-lookup"><span data-stu-id="45637-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="45637-125">Opisuje sposób wyświetlania <xref:System.Drawing.Imaging.EncoderParameters> obsługiwanych przez koder.</span><span class="sxs-lookup"><span data-stu-id="45637-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="45637-126">Instrukcje: konwertowanie obrazu w formacie BMP na format PNG</span><span class="sxs-lookup"><span data-stu-id="45637-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="45637-127">Opisuje sposób zapisywania obraz w formacie inny obraz.</span><span class="sxs-lookup"><span data-stu-id="45637-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="45637-128">Instrukcje: ustawianie poziomu dekompresji JPEG</span><span class="sxs-lookup"><span data-stu-id="45637-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="45637-129">Zawiera opis sposobu zmiany poziomu jakości obrazu.</span><span class="sxs-lookup"><span data-stu-id="45637-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="45637-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="45637-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="45637-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="45637-131">Related Sections</span></span>  
 [<span data-ttu-id="45637-132">Informacje o kodzie zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="45637-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="45637-133">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="45637-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
