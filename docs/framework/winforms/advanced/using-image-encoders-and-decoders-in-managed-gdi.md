---
title: Używanie kodeków obrazu w zarządzanym GDI+
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: e56bc20eb55d694d19b25d9e94e5c9d9e3952628
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666449"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="5a8dc-102">Używanie kodeków obrazu w zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="5a8dc-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="5a8dc-103"><xref:System.Drawing> Przestrzeń nazw zawiera <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> klasy do przechowywania i manipulowania obrazami.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="5a8dc-104">Za pomocą kodeków obrazu w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], można napisać obrazów z pamięci na dysk.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="5a8dc-105">Za pomocą dekodery obrazów w [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], możesz załadować obrazy z dysku do pamięci.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="5a8dc-106">Koder przekształca dane w <xref:System.Drawing.Image> lub <xref:System.Drawing.Bitmap> obiekt do formatu pliku wyznaczonym dysku.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="5a8dc-107">Dekoder przekształca dane w pliku dysku do formatu wymaganego przez <xref:System.Drawing.Image> i <xref:System.Drawing.Bitmap> obiektów.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="5a8dc-108">zawiera wbudowane kodeków, które obsługują następujące typy plików:</span><span class="sxs-lookup"><span data-stu-id="5a8dc-108">has built-in encoders and decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="5a8dc-109">BMP</span><span class="sxs-lookup"><span data-stu-id="5a8dc-109">BMP</span></span>  
  
- <span data-ttu-id="5a8dc-110">GIF</span><span class="sxs-lookup"><span data-stu-id="5a8dc-110">GIF</span></span>  
  
- <span data-ttu-id="5a8dc-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="5a8dc-111">JPEG</span></span>  
  
- <span data-ttu-id="5a8dc-112">PNG</span><span class="sxs-lookup"><span data-stu-id="5a8dc-112">PNG</span></span>  
  
- <span data-ttu-id="5a8dc-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="5a8dc-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="5a8dc-114">ma również wbudowane dekoderów, które obsługują następujące typy plików:</span><span class="sxs-lookup"><span data-stu-id="5a8dc-114">also has built-in decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="5a8dc-115">WMF</span><span class="sxs-lookup"><span data-stu-id="5a8dc-115">WMF</span></span>  
  
- <span data-ttu-id="5a8dc-116">EMF</span><span class="sxs-lookup"><span data-stu-id="5a8dc-116">EMF</span></span>  
  
- <span data-ttu-id="5a8dc-117">ICON</span><span class="sxs-lookup"><span data-stu-id="5a8dc-117">ICON</span></span>  
  
 <span data-ttu-id="5a8dc-118">W poniższych tematach omówiono kodeków bardziej szczegółowo:</span><span class="sxs-lookup"><span data-stu-id="5a8dc-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a8dc-119">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5a8dc-119">In This Section</span></span>  
 [<span data-ttu-id="5a8dc-120">Instrukcje: Lista zainstalowanych koderów</span><span class="sxs-lookup"><span data-stu-id="5a8dc-120">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)  
 <span data-ttu-id="5a8dc-121">Opisuje sposób wyświetlenia listy przypadku koderów dostępnych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="5a8dc-122">Instrukcje: Lista zainstalowanych dekoderów</span><span class="sxs-lookup"><span data-stu-id="5a8dc-122">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)  
 <span data-ttu-id="5a8dc-123">Opisuje sposób wyświetlenia listy dekodery dostępne na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="5a8dc-124">Instrukcje: Określanie parametrów obsługiwanych przez koder</span><span class="sxs-lookup"><span data-stu-id="5a8dc-124">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="5a8dc-125">W tym artykule opisano sposób wyświetlenia listy <xref:System.Drawing.Imaging.EncoderParameters> obsługiwanych przez koder.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="5a8dc-126">Instrukcje: Konwertowanie obrazu BMP na format PNG</span><span class="sxs-lookup"><span data-stu-id="5a8dc-126">How to: Convert a BMP image to a PNG image</span></span>](how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="5a8dc-127">W tym artykule opisano, jak zapisać obraz w formacie inny obraz.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="5a8dc-128">Instrukcje: Ustawianie poziomu dekompresji JPEG</span><span class="sxs-lookup"><span data-stu-id="5a8dc-128">How to: Set JPEG Compression Level</span></span>](how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="5a8dc-129">W tym artykule opisano, jak zmienić poziom jakości obrazu.</span><span class="sxs-lookup"><span data-stu-id="5a8dc-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5a8dc-130">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="5a8dc-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="5a8dc-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5a8dc-131">Related Sections</span></span>  
 [<span data-ttu-id="5a8dc-132">Informacje o kodzie zarządzanym GDI+</span><span class="sxs-lookup"><span data-stu-id="5a8dc-132">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
  
 [<span data-ttu-id="5a8dc-133">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="5a8dc-133">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
