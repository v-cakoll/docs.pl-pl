---
title: Przycinanie i skalowanie obrazów w GDI+
ms.date: 03/30/2017
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
ms.openlocfilehash: c3cdb06e99770808461f9266fb5f07df9074149b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183732"
---
# <a name="cropping-and-scaling-images-in-gdi"></a><span data-ttu-id="eb0e2-102">Przycinanie i skalowanie obrazów w GDI+</span><span class="sxs-lookup"><span data-stu-id="eb0e2-102">Cropping and Scaling Images in GDI+</span></span>
<span data-ttu-id="eb0e2-103">Możesz użyć <xref:System.Drawing.Graphics.DrawImage%2A> metody <xref:System.Drawing.Graphics> klasy do rysowania i umieść wektor obrazów i obrazów rastrowych.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-103">You can use the <xref:System.Drawing.Graphics.DrawImage%2A> method of the <xref:System.Drawing.Graphics> class to draw and position vector images and raster images.</span></span> <xref:System.Drawing.Graphics.DrawImage%2A> <span data-ttu-id="eb0e2-104">jest przeciążona metoda, dzięki czemu może dostarczyć argumentów na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-104">is an overloaded method, so there are several ways you can supply it with arguments.</span></span>  
  
## <a name="drawimage-variations"></a><span data-ttu-id="eb0e2-105">DrawImage — zmiany</span><span class="sxs-lookup"><span data-stu-id="eb0e2-105">DrawImage Variations</span></span>  
 <span data-ttu-id="eb0e2-106">Zmiana jednego <xref:System.Drawing.Graphics.DrawImage%2A> metoda otrzymuje <xref:System.Drawing.Bitmap> i <xref:System.Drawing.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-106">One variation of the <xref:System.Drawing.Graphics.DrawImage%2A> method receives a <xref:System.Drawing.Bitmap> and a <xref:System.Drawing.Rectangle>.</span></span> <span data-ttu-id="eb0e2-107">Prostokąt Określa lokalizację docelową dla operacji rysowania; oznacza to, że Określa ona prostokąta do rysowania obrazu.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-107">The rectangle specifies the destination for the drawing operation; that is, it specifies the rectangle in which to draw the image.</span></span> <span data-ttu-id="eb0e2-108">Jeśli rozmiar prostokąta docelowego jest inna niż rozmiar oryginalnego obrazu, obraz, który jest skalowany w celu dopasowania prostokąta docelowego.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-108">If the size of the destination rectangle is different from the size of the original image, the image is scaled to fit the destination rectangle.</span></span> <span data-ttu-id="eb0e2-109">Poniższy przykład kodu pokazuje sposób rysowania trzy razy ten sam obraz: drugi raz z bez skalowania, drugi raz z rozszerzenia a drugi raz z kompresji:</span><span class="sxs-lookup"><span data-stu-id="eb0e2-109">The following code example shows how to draw the same image three times: once with no scaling, once with an expansion, and once with a compression:</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 <span data-ttu-id="eb0e2-110">Poniższa ilustracja przedstawia trzy obrazy.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-110">The following illustration shows the three pictures.</span></span>  
  
 <span data-ttu-id="eb0e2-111">![Skalowanie](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span><span class="sxs-lookup"><span data-stu-id="eb0e2-111">![Scaling](./media/aboutgdip03-art06.gif "AboutGdip03_Art06")</span></span>  
  
 <span data-ttu-id="eb0e2-112">Kilka odmian <xref:System.Drawing.Graphics.DrawImage%2A> metoda ma parametr prostokąta źródłowego, a także parametr prostokąta docelowego.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-112">Some variations of the <xref:System.Drawing.Graphics.DrawImage%2A> method have a source-rectangle parameter as well as a destination-rectangle parameter.</span></span> <span data-ttu-id="eb0e2-113">Parametr prostokąta źródłowego określa część oryginalnego obrazu, aby narysować.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-113">The source-rectangle parameter specifies the portion of the original image to draw.</span></span> <span data-ttu-id="eb0e2-114">Prostokąta docelowego określa prostokąta do rysowania część obrazu.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-114">The destination rectangle specifies the rectangle in which to draw that portion of the image.</span></span> <span data-ttu-id="eb0e2-115">Jeśli rozmiar prostokąta docelowego jest inna niż rozmiar prostokąta źródłowego, obraz jest skalowane w celu dopasowania prostokąta docelowego.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-115">If the size of the destination rectangle is different from the size of the source rectangle, the picture is scaled to fit the destination rectangle.</span></span>  
  
 <span data-ttu-id="eb0e2-116">Poniższy przykład kodu pokazuje sposób tworzenia <xref:System.Drawing.Bitmap> z pliku Runner.jpg.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-116">The following code example shows how to construct a <xref:System.Drawing.Bitmap> from the file Runner.jpg.</span></span> <span data-ttu-id="eb0e2-117">Całego obrazu narysowany bez skalowania w (0, 0).</span><span class="sxs-lookup"><span data-stu-id="eb0e2-117">The entire image is drawn with no scaling at (0, 0).</span></span> <span data-ttu-id="eb0e2-118">Następnie niewielką część obrazu jest rysowana dwa razy: rozszerzenie raz przy użyciu kompresji i drugi raz.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-118">Then a small portion of the image is drawn twice: once with a compression and once with an expansion.</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 <span data-ttu-id="eb0e2-119">Na poniższej ilustracji pokazuje nieskalowanego obrazu i fragmenty skompresowane i rozwiniętej obrazu.</span><span class="sxs-lookup"><span data-stu-id="eb0e2-119">The following illustration shows the unscaled image, and the compressed and expanded image portions.</span></span>  
  
 <span data-ttu-id="eb0e2-120">![Przycinanie i skalowanie](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span><span class="sxs-lookup"><span data-stu-id="eb0e2-120">![Cropping and Scaling](./media/aboutgdip03-art07.gif "AboutGdip03_Art07")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb0e2-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eb0e2-121">See also</span></span>

- [<span data-ttu-id="eb0e2-122">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="eb0e2-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="eb0e2-123">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="eb0e2-123">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
