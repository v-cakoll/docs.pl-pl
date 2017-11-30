---
title: "Używanie przekształceń do skalowania kolorów"
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
- transformations [Windows Forms], for scaling colors
- colors [Windows Forms], scaling
ms.assetid: df23c887-7fd6-4b15-ad94-e30b5bd4b849
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4584b74cd7a394f7dd04d0cfba150b907ca7c82
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="3dfff-102">Używanie przekształceń do skalowania kolorów</span><span class="sxs-lookup"><span data-stu-id="3dfff-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="3dfff-103">Transformacja skalowania mnoży przynajmniej jednej z czterech składowych liczbą.</span><span class="sxs-lookup"><span data-stu-id="3dfff-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="3dfff-104">Wpisów macierzy kolorów, które reprezentują skalowanie są podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="3dfff-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="3dfff-105">Składnik skalowania</span><span class="sxs-lookup"><span data-stu-id="3dfff-105">Component to be scaled</span></span>|<span data-ttu-id="3dfff-106">Wpis macierzy</span><span class="sxs-lookup"><span data-stu-id="3dfff-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="3dfff-107">czerwony</span><span class="sxs-lookup"><span data-stu-id="3dfff-107">Red</span></span>|<span data-ttu-id="3dfff-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="3dfff-108">[0][0]</span></span>|  
|<span data-ttu-id="3dfff-109">zielony</span><span class="sxs-lookup"><span data-stu-id="3dfff-109">Green</span></span>|<span data-ttu-id="3dfff-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="3dfff-110">[1][1]</span></span>|  
|<span data-ttu-id="3dfff-111">niebieski</span><span class="sxs-lookup"><span data-stu-id="3dfff-111">Blue</span></span>|<span data-ttu-id="3dfff-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="3dfff-112">[2][2]</span></span>|  
|<span data-ttu-id="3dfff-113">Alpha</span><span class="sxs-lookup"><span data-stu-id="3dfff-113">Alpha</span></span>|<span data-ttu-id="3dfff-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="3dfff-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="3dfff-115">Skalowanie jednego koloru</span><span class="sxs-lookup"><span data-stu-id="3dfff-115">Scaling One Color</span></span>  
 <span data-ttu-id="3dfff-116">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="3dfff-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="3dfff-117">Następnie kod skaluje składnika niebieski każdego piksela obrazu o 2.</span><span class="sxs-lookup"><span data-stu-id="3dfff-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="3dfff-118">Oryginalnego obrazu jest rysowane obok przekształcone obrazu.</span><span class="sxs-lookup"><span data-stu-id="3dfff-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="3dfff-119">Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i skalowanie obrazów po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="3dfff-119">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="3dfff-120">![Skali kolorów](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span><span class="sxs-lookup"><span data-stu-id="3dfff-120">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans3.png "colortrans3")</span></span>  
  
 <span data-ttu-id="3dfff-121">W poniższej tabeli wymieniono wektory kolor słupków cztery przed i po niebieski skalowania.</span><span class="sxs-lookup"><span data-stu-id="3dfff-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="3dfff-122">Należy pamiętać, że składnik niebieski w czwartym pasek koloru próby z 0,8 0,6.</span><span class="sxs-lookup"><span data-stu-id="3dfff-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="3dfff-123">Jest to spowodowane tym [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] zachowuje część ułamkowa wyniku.</span><span class="sxs-lookup"><span data-stu-id="3dfff-123">That is because [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] retains only the fractional part of the result.</span></span> <span data-ttu-id="3dfff-124">Na przykład (2)(0.8) = 1.6, i część ułamkowa w wersji 1.6 jest 0,6.</span><span class="sxs-lookup"><span data-stu-id="3dfff-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="3dfff-125">Zachowywanie tylko część ułamkowa zapewnia, że wynik zawsze jest w zakresie [0, 1].</span><span class="sxs-lookup"><span data-stu-id="3dfff-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="3dfff-126">Oryginał</span><span class="sxs-lookup"><span data-stu-id="3dfff-126">Original</span></span>|<span data-ttu-id="3dfff-127">Skalowania</span><span class="sxs-lookup"><span data-stu-id="3dfff-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="3dfff-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="3dfff-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="3dfff-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="3dfff-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="3dfff-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="3dfff-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="3dfff-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="3dfff-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="3dfff-136">Skalowanie wiele kolorów</span><span class="sxs-lookup"><span data-stu-id="3dfff-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="3dfff-137">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektów z pliku ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="3dfff-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="3dfff-138">Następnie kod skaluje składniki czerwony, zielonemu i niebieskiemu każdego piksela obrazu.</span><span class="sxs-lookup"><span data-stu-id="3dfff-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="3dfff-139">Czerwony składniki są skalowane w dół 25 procent zielony składniki są skalowane w dół 35% i niebieski składniki są skalowane w dół 50 procent.</span><span class="sxs-lookup"><span data-stu-id="3dfff-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="3dfff-140">Na poniższej ilustracji przedstawiono oryginalnego obrazu po lewej stronie i skalowanie obrazów po prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="3dfff-140">The following illustration shows the original image on the left and the scaled image on the right.</span></span>  
  
 <span data-ttu-id="3dfff-141">![Skali kolorów](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span><span class="sxs-lookup"><span data-stu-id="3dfff-141">![Scale Colors](../../../../docs/framework/winforms/advanced/media/colortrans4.png "colortrans4")</span></span>  
  
 <span data-ttu-id="3dfff-142">W poniższej tabeli wymieniono wektory kolor słupków cztery przed i po czerwonemu, zielonemu i niebieski skalowanie.</span><span class="sxs-lookup"><span data-stu-id="3dfff-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="3dfff-143">Oryginał</span><span class="sxs-lookup"><span data-stu-id="3dfff-143">Original</span></span>|<span data-ttu-id="3dfff-144">Skalowania</span><span class="sxs-lookup"><span data-stu-id="3dfff-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="3dfff-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="3dfff-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="3dfff-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="3dfff-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="3dfff-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="3dfff-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="3dfff-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="3dfff-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="3dfff-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3dfff-153">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dfff-153">See Also</span></span>  
 <xref:System.Drawing.Imaging.ColorMatrix>  
 <xref:System.Drawing.Imaging.ImageAttributes>  
 [<span data-ttu-id="3dfff-154">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3dfff-154">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="3dfff-155">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="3dfff-155">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)
