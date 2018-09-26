---
title: Jak przyciąć obraz
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: 189cb92d581ccc9209ebdb4de18487951d17818a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47090055"
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="a171e-102">Jak przyciąć obraz</span><span class="sxs-lookup"><span data-stu-id="a171e-102">How to: Crop an Image</span></span>
<span data-ttu-id="a171e-103">W tym przykładzie pokazano, jak przyciąć obraz przy użyciu <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span><span class="sxs-lookup"><span data-stu-id="a171e-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="a171e-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> jest używany głównie podczas kodowania przycięty wersję obrazu można zapisać się do pliku.</span><span class="sxs-lookup"><span data-stu-id="a171e-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="a171e-105">Aby przyciąć obraz do wyświetlania celów zobacz [utworzyć obszar przycinania](https://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) tematu.</span><span class="sxs-lookup"><span data-stu-id="a171e-105">To crop an image for display purposes see the [Create a Clip Region](https://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a171e-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="a171e-106">Example</span></span>  
 <span data-ttu-id="a171e-107">Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definiuje zasoby używane w ramach przykłady przedstawiono poniżej.</span><span class="sxs-lookup"><span data-stu-id="a171e-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="a171e-108">Poniższy przykład tworzy obrazów przy użyciu <xref:System.Windows.Media.Imaging.CroppedBitmap> jako źródło.</span><span class="sxs-lookup"><span data-stu-id="a171e-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="a171e-109"><xref:System.Windows.Media.Imaging.CroppedBitmap> Może również służyć jako źródła innego <xref:System.Windows.Media.Imaging.CroppedBitmap>, łańcuch przycinania.</span><span class="sxs-lookup"><span data-stu-id="a171e-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="a171e-110">Należy pamiętać, że <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> używa wartości, które są względne wobec źródła przycięte mapy bitowej i obraz początkowy.</span><span class="sxs-lookup"><span data-stu-id="a171e-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="a171e-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a171e-111">See Also</span></span>  
 [<span data-ttu-id="a171e-112">Utwórz obszar przycinania</span><span class="sxs-lookup"><span data-stu-id="a171e-112">Create a Clip Region</span></span>](https://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376)
