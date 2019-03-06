---
title: 'Instrukcje: Animuj przesunięcie 3-D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 0290beac5a92a955b39d0b8fcc24705346c2964a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351921"
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="406d9-102">Instrukcje: Animuj przesunięcie 3-D</span><span class="sxs-lookup"><span data-stu-id="406d9-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="406d9-103">W tym temacie pokazano, jak animować przekształcenie tłumaczenia nastavit [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="406d9-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="406d9-104">Poniższy kod pokazuje zastosowanie <xref:System.Windows.Media.Media3D.TranslateTransform3D> obiekt <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="406d9-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="406d9-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Właściwości tego <xref:System.Windows.Media.Media3D.TranslateTransform3D> obiektu jest animowany przy użyciu kodu poniżej.</span><span class="sxs-lookup"><span data-stu-id="406d9-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="406d9-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="406d9-106">Example</span></span>  
 <span data-ttu-id="406d9-107">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="406d9-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="406d9-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="406d9-108">See also</span></span>
- [<span data-ttu-id="406d9-109">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="406d9-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="406d9-110">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="406d9-110">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="406d9-111">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="406d9-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="406d9-112">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="406d9-112">Transforms Overview</span></span>](transforms-overview.md)
