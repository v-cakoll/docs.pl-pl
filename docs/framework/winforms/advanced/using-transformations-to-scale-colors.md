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
ms.openlocfilehash: 81c0ddf5b937d604559a9eb1a8b598885546c97f
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504965"
---
# <a name="using-transformations-to-scale-colors"></a><span data-ttu-id="9d99f-102">Używanie przekształceń do skalowania kolorów</span><span class="sxs-lookup"><span data-stu-id="9d99f-102">Using Transformations to Scale Colors</span></span>
<span data-ttu-id="9d99f-103">Przekształcenie skalowania mnoży co najmniej cztery składowych przez liczbę.</span><span class="sxs-lookup"><span data-stu-id="9d99f-103">A scaling transformation multiplies one or more of the four color components by a number.</span></span> <span data-ttu-id="9d99f-104">Wpisów macierzy kolorów, które reprezentują skalowania są podane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="9d99f-104">The color matrix entries that represent scaling are given in the following table.</span></span>  
  
|<span data-ttu-id="9d99f-105">Składnik skalowania</span><span class="sxs-lookup"><span data-stu-id="9d99f-105">Component to be scaled</span></span>|<span data-ttu-id="9d99f-106">Wpis macierzy</span><span class="sxs-lookup"><span data-stu-id="9d99f-106">Matrix entry</span></span>|  
|----------------------------|------------------|  
|<span data-ttu-id="9d99f-107">Czerwony</span><span class="sxs-lookup"><span data-stu-id="9d99f-107">Red</span></span>|<span data-ttu-id="9d99f-108">[0][0]</span><span class="sxs-lookup"><span data-stu-id="9d99f-108">[0][0]</span></span>|  
|<span data-ttu-id="9d99f-109">Zielony</span><span class="sxs-lookup"><span data-stu-id="9d99f-109">Green</span></span>|<span data-ttu-id="9d99f-110">[1][1]</span><span class="sxs-lookup"><span data-stu-id="9d99f-110">[1][1]</span></span>|  
|<span data-ttu-id="9d99f-111">Niebieski</span><span class="sxs-lookup"><span data-stu-id="9d99f-111">Blue</span></span>|<span data-ttu-id="9d99f-112">[2][2]</span><span class="sxs-lookup"><span data-stu-id="9d99f-112">[2][2]</span></span>|  
|<span data-ttu-id="9d99f-113">alfa</span><span class="sxs-lookup"><span data-stu-id="9d99f-113">Alpha</span></span>|<span data-ttu-id="9d99f-114">[3][3]</span><span class="sxs-lookup"><span data-stu-id="9d99f-114">[3][3]</span></span>|  
  
## <a name="scaling-one-color"></a><span data-ttu-id="9d99f-115">Skalowanie z jednego koloru</span><span class="sxs-lookup"><span data-stu-id="9d99f-115">Scaling One Color</span></span>  
 <span data-ttu-id="9d99f-116">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="9d99f-116">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="9d99f-117">Następnie kod jest skalowana składnik niebieski każdego piksela na obrazie ośmiokrotnego 2.</span><span class="sxs-lookup"><span data-stu-id="9d99f-117">Then the code scales the blue component of each pixel in the image by a factor of 2.</span></span> <span data-ttu-id="9d99f-118">Oryginalny obraz jest rysowany wraz z obrazu przekształcone.</span><span class="sxs-lookup"><span data-stu-id="9d99f-118">The original image is drawn alongside the transformed image.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.RecoloringImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#41)]  
  
 <span data-ttu-id="9d99f-119">Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i skalowany obraz po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="9d99f-119">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Zrzut ekranu porównuje kolory oryginalnego i skalowanych.](./media/using-transformations-to-scale-colors/four-bar-scale-one-color.png)  
  
 <span data-ttu-id="9d99f-121">W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim niebieski skalowania.</span><span class="sxs-lookup"><span data-stu-id="9d99f-121">The following table lists the color vectors for the four bars before and after the blue scaling.</span></span> <span data-ttu-id="9d99f-122">Pamiętaj, że składnik niebieski w czwartym pasek koloru próby z 0,8 Update 0.6.</span><span class="sxs-lookup"><span data-stu-id="9d99f-122">Note that the blue component in the fourth color bar went from 0.8 to 0.6.</span></span> <span data-ttu-id="9d99f-123">Wynika to z GDI + część ułamkową wyniku zachowuje.</span><span class="sxs-lookup"><span data-stu-id="9d99f-123">That is because GDI+ retains only the fractional part of the result.</span></span> <span data-ttu-id="9d99f-124">Na przykład (2)(0.8) = 1.6, i Update 0.6 część ułamkową parametru 1.6.</span><span class="sxs-lookup"><span data-stu-id="9d99f-124">For example, (2)(0.8) = 1.6, and the fractional part of 1.6 is 0.6.</span></span> <span data-ttu-id="9d99f-125">Zachowywanie tylko część ułamkową gwarantuje, czy wynik jest zawsze w zakresie [0, 1].</span><span class="sxs-lookup"><span data-stu-id="9d99f-125">Retaining only the fractional part ensures that the result is always in the interval [0, 1].</span></span>  
  
|<span data-ttu-id="9d99f-126">Oryginał</span><span class="sxs-lookup"><span data-stu-id="9d99f-126">Original</span></span>|<span data-ttu-id="9d99f-127">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="9d99f-127">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="9d99f-128">(0.4, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-128">(0.4, 0.4, 0.4, 1)</span></span>|<span data-ttu-id="9d99f-129">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-129">(0.4, 0.4, 0.8, 1)</span></span>|  
|<span data-ttu-id="9d99f-130">(0.4, 0.2, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-130">(0.4, 0.2, 0.2, 1)</span></span>|<span data-ttu-id="9d99f-131">(0.4, 0.2, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-131">(0.4, 0.2, 0.4, 1)</span></span>|  
|<span data-ttu-id="9d99f-132">(0.2, 0.4, 0.2, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-132">(0.2, 0.4, 0.2, 1)</span></span>|<span data-ttu-id="9d99f-133">(0.2, 0.4, 0.4, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-133">(0.2, 0.4, 0.4, 1)</span></span>|  
|<span data-ttu-id="9d99f-134">(0.4, 0.4, 0.8, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-134">(0.4, 0.4, 0.8, 1)</span></span>|<span data-ttu-id="9d99f-135">(0.4, 0.4, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-135">(0.4, 0.4, 0.6, 1)</span></span>|  
  
## <a name="scaling-multiple-colors"></a><span data-ttu-id="9d99f-136">Skalowanie wielu kolorów</span><span class="sxs-lookup"><span data-stu-id="9d99f-136">Scaling Multiple Colors</span></span>  
 <span data-ttu-id="9d99f-137">Poniższy przykład tworzy <xref:System.Drawing.Image> obiektu na podstawie pliku ColorBars2.bmp.</span><span class="sxs-lookup"><span data-stu-id="9d99f-137">The following example constructs an <xref:System.Drawing.Image> object from the file ColorBars2.bmp.</span></span> <span data-ttu-id="9d99f-138">Następnie kod skaluje składników czerwonego, zielonego i niebieskiego każdego piksela na obrazie.</span><span class="sxs-lookup"><span data-stu-id="9d99f-138">Then the code scales the red, green, and blue components of each pixel in the image.</span></span> <span data-ttu-id="9d99f-139">Składniki czerwone są skalowane w dół 25 procent, zielony składniki są skalowane w dół 35 procent i składniki niebieskie są skalowane w dół 50 procent.</span><span class="sxs-lookup"><span data-stu-id="9d99f-139">The red components are scaled down 25 percent, the green components are scaled down 35 percent, and the blue components are scaled down 50 percent.</span></span>  
  
 [!code-csharp[System.Drawing.RecoloringImages#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.RecoloringImages#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#42)]  
  
 <span data-ttu-id="9d99f-140">Na poniższej ilustracji przedstawiono oryginalny obraz po lewej stronie i skalowany obraz po prawej stronie:</span><span class="sxs-lookup"><span data-stu-id="9d99f-140">The following illustration shows the original image on the left and the scaled image on the right:</span></span>  
  
 ![Zrzut ekranu porównuje kolory oryginalnego i skalowanych.](./media/using-transformations-to-scale-colors/four-bar-scale-multiple-colors.png)  
  
 <span data-ttu-id="9d99f-142">W poniższej tabeli wymieniono wektorów kolor słupków cztery przed i po nim czerwonego, zielonego i niebieskiego skalowanie.</span><span class="sxs-lookup"><span data-stu-id="9d99f-142">The following table lists the color vectors for the four bars before and after the red, green and blue scaling.</span></span>  
  
|<span data-ttu-id="9d99f-143">Oryginał</span><span class="sxs-lookup"><span data-stu-id="9d99f-143">Original</span></span>|<span data-ttu-id="9d99f-144">Skalowanie</span><span class="sxs-lookup"><span data-stu-id="9d99f-144">Scaled</span></span>|  
|--------------|------------|  
|<span data-ttu-id="9d99f-145">(0.6, 0.6, 0.6, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-145">(0.6, 0.6, 0.6, 1)</span></span>|<span data-ttu-id="9d99f-146">(0.45, 0.39, 0.3, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-146">(0.45, 0.39, 0.3, 1)</span></span>|  
|<span data-ttu-id="9d99f-147">(0, 1, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-147">(0, 1, 1, 1)</span></span>|<span data-ttu-id="9d99f-148">(0, 0.65, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-148">(0, 0.65, 0.5, 1)</span></span>|  
|<span data-ttu-id="9d99f-149">(1, 1, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-149">(1, 1, 0, 1)</span></span>|<span data-ttu-id="9d99f-150">(0.75, 0.65, 0, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-150">(0.75, 0.65, 0, 1)</span></span>|  
|<span data-ttu-id="9d99f-151">(1, 0, 1, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-151">(1, 0, 1, 1)</span></span>|<span data-ttu-id="9d99f-152">(0.75, 0, 0.5, 1)</span><span class="sxs-lookup"><span data-stu-id="9d99f-152">(0.75, 0, 0.5, 1)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9d99f-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d99f-153">See also</span></span>

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [<span data-ttu-id="9d99f-154">Grafika i rysowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d99f-154">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="9d99f-155">Ponowne kolorowanie obrazów</span><span class="sxs-lookup"><span data-stu-id="9d99f-155">Recoloring Images</span></span>](recoloring-images.md)
