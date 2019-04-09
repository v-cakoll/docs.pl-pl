---
title: 'Instrukcje: Animowanie przesunięcia 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 3e27c2d5f0cd44235a1d897b1b8f057808ae6bd8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168275"
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="b681a-102">Instrukcje: Animowanie przesunięcia 3D</span><span class="sxs-lookup"><span data-stu-id="b681a-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="b681a-103">W tym temacie pokazano, jak animować przekształcenie tłumaczenia nastavit [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="b681a-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="b681a-104">Poniższy kod pokazuje zastosowanie <xref:System.Windows.Media.Media3D.TranslateTransform3D> obiekt <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="b681a-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="b681a-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Właściwości tego <xref:System.Windows.Media.Media3D.TranslateTransform3D> obiektu jest animowany przy użyciu kodu poniżej.</span><span class="sxs-lookup"><span data-stu-id="b681a-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="b681a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="b681a-106">Example</span></span>  
 <span data-ttu-id="b681a-107">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="b681a-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b681a-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b681a-108">See also</span></span>

- [<span data-ttu-id="b681a-109">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="b681a-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b681a-110">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="b681a-110">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="b681a-111">Przegląd Grafika 3-D</span><span class="sxs-lookup"><span data-stu-id="b681a-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="b681a-112">Przegląd Przekształcenia</span><span class="sxs-lookup"><span data-stu-id="b681a-112">Transforms Overview</span></span>](transforms-overview.md)
