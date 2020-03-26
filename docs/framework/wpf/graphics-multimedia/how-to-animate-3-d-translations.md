---
title: 'Jak: Animowanie tłumaczeń 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations
- 3D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 7d4fff9c74663bd220ad5d15a983bcb639621afd
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112261"
---
# <a name="how-to-animate-3d-translations"></a><span data-ttu-id="43bb3-102">Jak: Animowanie tłumaczeń 3D</span><span class="sxs-lookup"><span data-stu-id="43bb3-102">How to: Animate 3D Translations</span></span>
<span data-ttu-id="43bb3-103">W tym temacie pokazano, jak animować transformację tłumaczenia ustawioną w modelu 3D.</span><span class="sxs-lookup"><span data-stu-id="43bb3-103">This topic demonstrates how to animate a translation transformation set on a 3D model.</span></span>  
  
 <span data-ttu-id="43bb3-104">Poniższy kod przedstawia zastosowanie <xref:System.Windows.Media.Media3D.TranslateTransform3D> obiektu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> do właściwości <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="43bb3-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="43bb3-105">Właściwość <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> tego <xref:System.Windows.Media.Media3D.TranslateTransform3D> obiektu jest animowany przy użyciu kodu poniżej.</span><span class="sxs-lookup"><span data-stu-id="43bb3-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="43bb3-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="43bb3-106">Example</span></span>  
 <span data-ttu-id="43bb3-107">Poniższy kod przedstawia cały przykład.</span><span class="sxs-lookup"><span data-stu-id="43bb3-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="43bb3-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43bb3-108">See also</span></span>

- [<span data-ttu-id="43bb3-109">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="43bb3-109">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="43bb3-110">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="43bb3-110">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="43bb3-111">Omówienie grafiki 3D</span><span class="sxs-lookup"><span data-stu-id="43bb3-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="43bb3-112">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="43bb3-112">Transforms Overview</span></span>](transforms-overview.md)
