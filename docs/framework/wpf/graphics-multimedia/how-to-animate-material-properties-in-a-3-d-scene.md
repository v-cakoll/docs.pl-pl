---
title: 'Instrukcje: Animowanie właściwości materiału w scenie 3D'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: 8dfd7f01b87e2becfbcf57544ec4f8340cf8d5cc
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662550"
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a><span data-ttu-id="1b762-102">Instrukcje: Animowanie właściwości materiału w scenie 3D</span><span class="sxs-lookup"><span data-stu-id="1b762-102">How to: Animate Material Properties in a 3-D Scene</span></span>
<span data-ttu-id="1b762-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.Brush.Opacity%2A> właściwość <xref:System.Windows.Media.Media3D.Material> zastosowano do modelu 3-D.</span><span class="sxs-lookup"><span data-stu-id="1b762-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a 3-D model.</span></span>  
  
 <span data-ttu-id="1b762-104">Poniższy przykład kodu przedstawia <xref:System.Windows.Media.LinearGradientBrush> używany jako <xref:System.Windows.Media.Media3D.Material> zastosowany do obiektu 3D.</span><span class="sxs-lookup"><span data-stu-id="1b762-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="1b762-105"><xref:System.Windows.Media.Brush.Opacity%2A> Właściwości tego <xref:System.Windows.Media.LinearGradientBrush> jest animowany przy użyciu Poniższy przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="1b762-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="1b762-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b762-106">Example</span></span>  
 <span data-ttu-id="1b762-107">Poniższy kod przedstawia całej próbki.</span><span class="sxs-lookup"><span data-stu-id="1b762-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1b762-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b762-108">See also</span></span>

- [<span data-ttu-id="1b762-109">Tworzenie sceny 3D</span><span class="sxs-lookup"><span data-stu-id="1b762-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="1b762-110">Grafika 3D — przegląd</span><span class="sxs-lookup"><span data-stu-id="1b762-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
