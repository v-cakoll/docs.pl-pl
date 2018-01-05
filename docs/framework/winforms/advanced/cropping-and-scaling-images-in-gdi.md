---
title: "Przycinanie i skalowanie obrazów w GDI+"
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
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0bbe7ac4b8c541ea76392f94f538e41816cf5c3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="11d97-102">Przycinanie i skalowanie obrazów w GDI+</span><span class="sxs-lookup"><span data-stu-id="11d97-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="11d97-103">Można użyć <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> klasy do rysowania i umieść wektor obrazów i obrazów rastrowych.</span><span class="sxs-lookup"><span data-stu-id="11d97-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <span data-ttu-id="11d97-104"><xref:System.Drawing.Graphics.DrawImage%2A>jest przeciążona metoda, więc może dostarczyć argumenty na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="11d97-104"><xref:System.Drawing.Graphics.DrawImage%2A> is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="11d97-105">DrawImage zmian</span><span class="sxs-lookup"><span data-stu-id="11d97-105">DrawImage Variations</span></span>  
 <span data-ttu-id="11d97-106">Zmiana jednego <xref:System.Drawing.Graphics.DrawImage%2A> metoda <xref:System.Drawing.Bitmap> i <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="11d97-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="11d97-107">Prostokąt określa obiekt docelowy operacji rysowania; oznacza to określa prostokąta do rysowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="11d97-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="11d97-108">Jeśli rozmiar docelowy prostokąt różni się od rozmiaru oryginalnego obrazu, obraz jest skalowane w celu dopasowania prostokąt docelowy.</span><span class="sxs-lookup"><span data-stu-id="11d97-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="11d97-109">Poniższy przykład kodu pokazuje sposób rysowania trzy razy ten sam obraz: drugi raz z bez skalowania, drugi raz z rozszerzenia, a drugi raz z kompresji:</span><span class="sxs-lookup"><span data-stu-id="11d97-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="11d97-110">Na poniższej ilustracji przedstawiono trzy obrazy.</span><span class="sxs-lookup"><span data-stu-id="11d97-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="11d97-111">![Skalowanie](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="11d97-111">![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="11d97-112">Niektóre zmiany <xref:System.Drawing.Graphics.DrawImage%2A> metoda ma parametr prostokąta źródłowego, a także parametr docelowy prostokąt.</span><span class="sxs-lookup"><span data-stu-id="11d97-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="11d97-113">Parametr prostokąta źródłowego określa część oryginalnego obrazu do rysowania.</span><span class="sxs-lookup"><span data-stu-id="11d97-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="11d97-114">Docelowy prostokąt określa prostokąta do rysowania część obrazu.</span><span class="sxs-lookup"><span data-stu-id="11d97-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="11d97-115">Jeśli rozmiar docelowy prostokąt różni się od rozmiaru prostokąta źródłowego, obraz jest skalowane w celu dopasowania prostokąt docelowy.</span><span class="sxs-lookup"><span data-stu-id="11d97-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="11d97-116">Poniższy przykładowy kod przedstawia sposób tworzenia <xref:System.Drawing.Bitmap> z pliku Runner.jpg.</span><span class="sxs-lookup"><span data-stu-id="11d97-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="11d97-117">Obraz jest rysowany z bez skalowania w (0, 0).</span><span class="sxs-lookup"><span data-stu-id="11d97-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="11d97-118">Następnie niewielką część obrazu jest rysowany dwa razy: raz z kompresji i drugi raz z rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="11d97-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="11d97-119">Na poniższej ilustracji przedstawiono nieskalowanego obrazu i części obrazu skompresowanej i rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="11d97-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="11d97-120">![Przycinanie i skalowanie](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="11d97-120">![Cropping and Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11d97-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11d97-121">See Also</span></span>  
 [<span data-ttu-id="11d97-122">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="11d97-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="11d97-123">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="11d97-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
