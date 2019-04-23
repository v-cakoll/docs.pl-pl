---
title: Używanie przekształceń do skalowania kolorów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
ms.openlocfilehash: 9c8f2392137d04f56096120cec64b60c42c47419
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59107988"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="94359-102">Używanie przekształceń do skalowania kolorów</span><span class="sxs-lookup"><span data-stu-id="94359-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="94359-103">Przekształcenie skalowania mnoży co najmniej cztery składowych przez liczbę.</span><span class="sxs-lookup"><span data-stu-id="94359-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="94359-104">Wpisów macierzy kolorów, które reprezentują skalowania są podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="94359-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="94359-105">Składnik skalowania</span><span class="sxs-lookup"><span data-stu-id="94359-105">Component to be scaled</span></span>|<span data-ttu-id="94359-106">Wpis macierzy</span><span class="sxs-lookup"><span data-stu-id="94359-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="94359-107">Czerwony</span><span class="sxs-lookup"><span data-stu-id="94359-107">Red</span></span>|<span data-ttu-id="94359-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="94359-108">[0][0]</span></span>|  
|<span data-ttu-id="94359-109">Zielony</span><span class="sxs-lookup"><span data-stu-id="94359-109">Green</span></span>|<span data-ttu-id="94359-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="94359-110">[1][1]</span></span>|  
|<span data-ttu-id="94359-111">Niebieski</span><span class="sxs-lookup"><span data-stu-id="94359-111">Blue</span></span>|<span data-ttu-id="94359-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="94359-112">[2][2]</span></span>|  
|<span data-ttu-id="94359-113">alfa</span><span class="sxs-lookup"><span data-stu-id="94359-113">Alpha</span></span>|<span data-ttu-id="94359-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="94359-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="94359-115">Skalowanie z jednego koloru</span><span class="sxs-lookup"><span data-stu-id="94359-115">Scaling One Color</span></span>  
 <span data-ttu-id="94359-116">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="94359-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="94359-117">Następnie kod jest skalowana składnik niebieski każdego piksela na obrazie ośmiokrotnego 2.</span><span class="sxs-lookup"><span data-stu-id="94359-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="94359-118">Oryginalny obraz jest rysowany wraz z obrazu przekształcone.</span><span class="sxs-lookup"><span data-stu-id="94359-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="94359-119">Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i skalowany obraz po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="94359-119">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Zrzut ekranu porównuje kolory oryginalnego i skalowanych.](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 <span data-ttu-id="94359-121">W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim niebieski skalowania.</span><span class="sxs-lookup"><span data-stu-id="94359-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="94359-122">Pamiętaj, że składnik niebieski w czwartym pasek koloru próby z 0,8 Update 0.6.</span><span class="sxs-lookup"><span data-stu-id="94359-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="94359-123">To dlatego, że [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zachowuje część ułamkową wyniku.</span><span class="sxs-lookup"><span data-stu-id="94359-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="94359-124">Na przykład (2)(0.8) = 1.6, i Update 0.6 część ułamkową parametru 1.6.</span><span class="sxs-lookup"><span data-stu-id="94359-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="94359-125">Zachowywanie tylko część ułamkową gwarantuje, czy wynik jest zawsze w zakresie [0, 1].</span><span class="sxs-lookup"><span data-stu-id="94359-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="94359-126">Oryginał</span><span class="sxs-lookup"><span data-stu-id="94359-126">Original</span></span>|<span data-ttu-id="94359-127">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="94359-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="94359-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="94359-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="94359-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="94359-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="94359-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="94359-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="94359-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="94359-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="94359-136">Skalowanie wielu kolorów</span><span class="sxs-lookup"><span data-stu-id="94359-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="94359-137">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="94359-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="94359-138">Następnie kod skaluje składników czerwonego, zielonego i niebieskiego każdego piksela na obrazie.</span><span class="sxs-lookup"><span data-stu-id="94359-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="94359-139">Składniki czerwone są skalowane w dół 25 procent, zielony składniki są skalowane w dół 35 procent i składniki niebieskie są skalowane w dół 50 procent.</span><span class="sxs-lookup"><span data-stu-id="94359-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="94359-140">Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i skalowany obraz po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="94359-140">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Zrzut ekranu porównuje kolory oryginalnego i skalowanych.](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 <span data-ttu-id="94359-142">W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim czerwonego, zielonego i niebieskiego skalowanie.</span><span class="sxs-lookup"><span data-stu-id="94359-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="94359-143">Oryginał</span><span class="sxs-lookup"><span data-stu-id="94359-143">Original</span></span>|<span data-ttu-id="94359-144">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="94359-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="94359-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="94359-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="94359-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="94359-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="94359-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="94359-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="94359-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="94359-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="94359-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94359-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94359-153">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="94359-154">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94359-154">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="94359-155">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="94359-155">Recoloring Images</span></span>](recoloring-images.md)
