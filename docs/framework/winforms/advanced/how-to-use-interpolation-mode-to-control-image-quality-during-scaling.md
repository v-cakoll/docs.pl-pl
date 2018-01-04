---
title: "Porady: używanie trybu interpolacji do sterowania jakością obrazu w czasie skalowania"
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
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8bbc17b8344fca496dcf8f4077a69b6db1453c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="07dcd-102">Porady: używanie trybu interpolacji do sterowania jakością obrazu w czasie skalowania</span><span class="sxs-lookup"><span data-stu-id="07dcd-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="07dcd-103">Tryb interpolacji <xref:System.Drawing.Graphics> obiektu wpływa na sposób [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obrazów w skali (odcinkach i zmniejsza).</span><span class="sxs-lookup"><span data-stu-id="07dcd-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="07dcd-104"><xref:System.Drawing.Drawing2D.InterpolationMode> Wyliczenie definiuje kilka trybów interpolacji, niektóre z nich są wyświetlane na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="07dcd-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="07dcd-105">Do rozciągania obrazów, każdego piksela oryginalnego obrazu muszą być zamapowane do grupy pikseli większy obraz.</span><span class="sxs-lookup"><span data-stu-id="07dcd-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="07dcd-106">Aby zmniejszyć rozmiar obrazu, grup pikseli oryginalnego obrazu musi być zamapowany na jednym pikseli mniejsze.</span><span class="sxs-lookup"><span data-stu-id="07dcd-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="07dcd-107">Skuteczność algorytmy, które wykonują te mapowania określa jakość skalowanie obrazu.</span><span class="sxs-lookup"><span data-stu-id="07dcd-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="07dcd-108">Algorytmy, które powodują powstanie wyższej jakości skalowane obrazy zwykle wymagają więcej czasu przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="07dcd-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="07dcd-109">Na powyższej liście <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> jest tryb najniższym jakości i <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> jest tryb najwyższej jakości.</span><span class="sxs-lookup"><span data-stu-id="07dcd-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="07dcd-110">Aby ustawić tryb interpolacji, przypisać jeden z elementów członkowskich <xref:System.Drawing.Drawing2D.InterpolationMode> wyliczeniu, aby <xref:System.Drawing.Graphics.InterpolationMode%2A> właściwość <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="07dcd-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07dcd-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="07dcd-111">Example</span></span>  
 <span data-ttu-id="07dcd-112">Rysuje obraz, zmniejsza rozmiar obrazu z trzech trybów różnych interpolacji w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="07dcd-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="07dcd-113">Na poniższej ilustracji przedstawiono oryginalnego obrazu i trzy obrazy mniejsze.</span><span class="sxs-lookup"><span data-stu-id="07dcd-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 <span data-ttu-id="07dcd-114">![Obraz ze zróżnicowanymi ustawieniami interpolacji](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")</span><span class="sxs-lookup"><span data-stu-id="07dcd-114">![Image with Varied Interpolation Settings](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")</span></span>  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07dcd-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="07dcd-115">Compiling the Code</span></span>  
 <span data-ttu-id="07dcd-116">Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="07dcd-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07dcd-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07dcd-117">See Also</span></span>  
 [<span data-ttu-id="07dcd-118">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="07dcd-118">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [<span data-ttu-id="07dcd-119">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="07dcd-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
