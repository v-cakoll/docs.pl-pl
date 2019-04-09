---
title: 'Instrukcje: Używanie trybu interpolacji do sterowania jakością obrazu w czasie skalowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: 75f5077c2d969f026a28834144c219f289843dd6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080985"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a><span data-ttu-id="0701f-102">Instrukcje: Używanie trybu interpolacji do sterowania jakością obrazu w czasie skalowania</span><span class="sxs-lookup"><span data-stu-id="0701f-102">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>
<span data-ttu-id="0701f-103">Tryb interpolacji <xref:System.Drawing.Graphics> obiekt ma wpływ na sposób [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] obrazów w skali (odcinkach i zmniejsza).</span><span class="sxs-lookup"><span data-stu-id="0701f-103">The interpolation mode of a <xref:System.Drawing.Graphics> object influences the way [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] scales (stretches and shrinks) images.</span></span> <span data-ttu-id="0701f-104"><xref:System.Drawing.Drawing2D.InterpolationMode> Wyliczenie definiuje kilka trybów interpolacji, niektóre z nich są wyświetlane na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="0701f-104">The <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration defines several interpolation modes, some of which are shown in the following list:</span></span>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 <span data-ttu-id="0701f-105">Obraz jest rozciągany tak, każdego piksela oryginalnego obrazu, musi być zmapowany do grupy pikseli większy obraz.</span><span class="sxs-lookup"><span data-stu-id="0701f-105">To stretch an image, each pixel in the original image must be mapped to a group of pixels in the larger image.</span></span> <span data-ttu-id="0701f-106">Aby zmniejszyć obrazu, grup pikseli, oryginalnym obrazie musi być zamapowany na jednym pikseli w mniejszym obrazem.</span><span class="sxs-lookup"><span data-stu-id="0701f-106">To shrink an image, groups of pixels in the original image must be mapped to single pixels in the smaller image.</span></span> <span data-ttu-id="0701f-107">Skuteczność algorytmy, które wykonują te mapowania określa jakość skalowany obraz.</span><span class="sxs-lookup"><span data-stu-id="0701f-107">The effectiveness of the algorithms that perform these mappings determines the quality of a scaled image.</span></span> <span data-ttu-id="0701f-108">Algorytmy, które powoduje, że wyższej jakości skalowanych zwykle wymagają więcej czasu na przetwarzanie.</span><span class="sxs-lookup"><span data-stu-id="0701f-108">Algorithms that produce higher-quality scaled images tend to require more processing time.</span></span> <span data-ttu-id="0701f-109">Z powyższej listy <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> jest tryb najniższej jakości i <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> jest tryb najwyższej jakości.</span><span class="sxs-lookup"><span data-stu-id="0701f-109">In the preceding list, <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> is the lowest-quality mode and <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> is the highest-quality mode.</span></span>  
  
 <span data-ttu-id="0701f-110">Aby ustawić tryb interpolacji, należy przypisać jeden z elementów członkowskich <xref:System.Drawing.Drawing2D.InterpolationMode> wyliczeniu, aby <xref:System.Drawing.Graphics.InterpolationMode%2A> właściwość <xref:System.Drawing.Graphics> obiektu.</span><span class="sxs-lookup"><span data-stu-id="0701f-110">To set the interpolation mode, assign one of the members of the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to the <xref:System.Drawing.Graphics.InterpolationMode%2A> property of a <xref:System.Drawing.Graphics> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0701f-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="0701f-111">Example</span></span>  
 <span data-ttu-id="0701f-112">Poniższy przykład pobiera obraz i następnie zmniejsza obraz z trzech trybów różnych interpolacji.</span><span class="sxs-lookup"><span data-stu-id="0701f-112">The following example draws an image and then shrinks the image with three different interpolation modes.</span></span>  
  
 <span data-ttu-id="0701f-113">Na poniższej ilustracji przedstawiono oryginalnego obrazu i trzy obrazy mniejsze.</span><span class="sxs-lookup"><span data-stu-id="0701f-113">The following illustration shows the original image and the three smaller images.</span></span>  
  
 ![Zrzut ekranu pokazujący obraz ze zróżnicowanymi ustawieniami interpolacji.](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0701f-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0701f-115">Compiling the Code</span></span>  
 <span data-ttu-id="0701f-116">Poprzedni przykład jest przeznaczony do użytku z formularzami Windows Forms i potrzebny <xref:System.Windows.Forms.PaintEventArgs> `e`, czyli parametrem <xref:System.Windows.Forms.Control.Paint> programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="0701f-116">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0701f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0701f-117">See also</span></span>

- [<span data-ttu-id="0701f-118">Obrazy, mapy bitowe i metapliki</span><span class="sxs-lookup"><span data-stu-id="0701f-118">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
- [<span data-ttu-id="0701f-119">Praca z obrazami, mapami bitowymi, ikonami i metaplikami</span><span class="sxs-lookup"><span data-stu-id="0701f-119">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](working-with-images-bitmaps-icons-and-metafiles.md)
