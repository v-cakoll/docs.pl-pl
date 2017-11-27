---
title: Obrazy, mapy bitowe i metapliki
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], about metafiles
- bitmaps [Windows Forms], about bitmaps
- images [Windows Forms], about images
- Windows Forms, images
ms.assetid: 7152b45b-a55c-49bc-8c78-ae002a844f71
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f48027e413f9573158cfa2c3748fc93408b3f83
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="images-bitmaps-and-metafiles"></a><span data-ttu-id="52e70-102">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="52e70-102">Images, Bitmaps, and Metafiles</span></span>
<span data-ttu-id="52e70-103">`Image` Klasa jest abstrakcyjna klasa podstawowa, który udostępnia metody do pracy z obrazów rastrowych (map bitowych) i wektor obrazy (metapliki).</span><span class="sxs-lookup"><span data-stu-id="52e70-103">The `Image` class is an abstract base class that provides methods for working with raster images (bitmaps) and vector images (metafiles).</span></span> <span data-ttu-id="52e70-104">`Bitmap` Klasy i <xref:System.Drawing.Imaging.Metafile> zarówno dziedziczy z klasy `Image` klasy.</span><span class="sxs-lookup"><span data-stu-id="52e70-104">The `Bitmap` class and the <xref:System.Drawing.Imaging.Metafile> class both inherit from the `Image` class.</span></span> <span data-ttu-id="52e70-105">`Bitmap` Klasa rozszerza się na funkcjach `Image` klasy, zapewniając dodatkowe metody ładowania, zapisywania i modyfikowania obrazów rastrowych.</span><span class="sxs-lookup"><span data-stu-id="52e70-105">The `Bitmap` class expands on the capabilities of the `Image` class by providing additional methods for loading, saving, and manipulating raster images.</span></span> <span data-ttu-id="52e70-106"><xref:System.Drawing.Imaging.Metafile> Klasa rozszerza się na funkcjach `Image` klasy, zapewniając dodatkowe metody rejestrowania i badanie wektor obrazów.</span><span class="sxs-lookup"><span data-stu-id="52e70-106">The <xref:System.Drawing.Imaging.Metafile> class expands on the capabilities of the `Image` class by providing additional methods for recording and examining vector images.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52e70-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="52e70-107">In This Section</span></span>  
 [<span data-ttu-id="52e70-108">Typy map bitowych</span><span class="sxs-lookup"><span data-stu-id="52e70-108">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 <span data-ttu-id="52e70-109">W tym artykule omówiono różne formaty obrazu.</span><span class="sxs-lookup"><span data-stu-id="52e70-109">Discusses the various image formats.</span></span>  
  
 [<span data-ttu-id="52e70-110">Metapliki w GDI +</span><span class="sxs-lookup"><span data-stu-id="52e70-110">Metafiles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/metafiles-in-gdi.md)  
 <span data-ttu-id="52e70-111">W tym artykule omówiono [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obsługę metapliki.</span><span class="sxs-lookup"><span data-stu-id="52e70-111">Discusses [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] support for metafiles.</span></span>  
  
 [<span data-ttu-id="52e70-112">Rysowanie, pozycjonowanie i klonowanie obrazów w GDI +</span><span class="sxs-lookup"><span data-stu-id="52e70-112">Drawing, Positioning, and Cloning Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/drawing-positioning-and-cloning-images-in-gdi.md)  
 <span data-ttu-id="52e70-113">W tym artykule omówiono metody wektor rysowania i obrazy rastrowe z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="52e70-113">Discusses methods for drawing vector and raster images with managed code.</span></span>  
  
 [<span data-ttu-id="52e70-114">Przycinanie i skalowanie obrazów w GDI +</span><span class="sxs-lookup"><span data-stu-id="52e70-114">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="52e70-115">W tym artykule omówiono metody przycinanie i skalowanie obrazów wektorowe i rastrowe z kodu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="52e70-115">Discusses methods for cropping and scaling vector and raster images with managed code</span></span>  
  
## <a name="reference"></a><span data-ttu-id="52e70-116">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="52e70-116">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="52e70-117">Ta klasa opisuje i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="52e70-117">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="52e70-118">Ta klasa opisuje oraz zawiera łącza do wszystkich jego elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="52e70-118">Describes this class and has links to all of its members</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52e70-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="52e70-119">Related Sections</span></span>  
 [<span data-ttu-id="52e70-120">Praca z obrazami, mapami bitowymi, ikony i metapliki</span><span class="sxs-lookup"><span data-stu-id="52e70-120">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="52e70-121">Zawiera łącza do tematów, które pokazują, jak używać obrazów w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="52e70-121">Contains links to topics that demonstrate how to use images in your application.</span></span>
