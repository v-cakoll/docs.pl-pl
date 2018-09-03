---
title: Jak obrócić element w miejscu
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 56385d7c31465e25f19486ea5cdaa8876cdb30ff
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461634"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="87b77-102">Jak obrócić element w miejscu</span><span class="sxs-lookup"><span data-stu-id="87b77-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="87b77-103">Ten przykład pokazuje, jak do uczynienia elementu Uruchom za pomocą <xref:System.Windows.Media.RotateTransform> i <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="87b77-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="87b77-104">Następujący przykład dotyczy <xref:System.Windows.Media.RotateTransform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości elementu.</span><span class="sxs-lookup"><span data-stu-id="87b77-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="87b77-105">W przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="87b77-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="87b77-106">Aby element pokrętła w miejscu, w przykładzie <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość elementu w punkcie (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="87b77-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87b77-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="87b77-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="87b77-108">Aby uzyskać pełny przykład, który zawiera więcej przykładów transformacji, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="87b77-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87b77-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87b77-109">See Also</span></span>  
 [<span data-ttu-id="87b77-110">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="87b77-110">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="87b77-111">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="87b77-111">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
