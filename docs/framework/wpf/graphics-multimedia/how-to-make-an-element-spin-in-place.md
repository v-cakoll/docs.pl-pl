---
title: Jak obrócić element w miejscu
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: 2e72389a11e48629c2763fcbd9f7b1945ffff5dd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452795"
---
# <a name="how-to-make-an-element-spin-in-place"></a><span data-ttu-id="2de5f-102">Jak obrócić element w miejscu</span><span class="sxs-lookup"><span data-stu-id="2de5f-102">How to: Make an Element Spin in Place</span></span>
<span data-ttu-id="2de5f-103">Ten przykład pokazuje, jak utworzyć element pokrętła przy użyciu <xref:System.Windows.Media.RotateTransform> i <xref:System.Windows.Media.Animation.DoubleAnimation>.</span><span class="sxs-lookup"><span data-stu-id="2de5f-103">This example shows how to make an element spin by using a <xref:System.Windows.Media.RotateTransform> and a <xref:System.Windows.Media.Animation.DoubleAnimation>.</span></span>  
  
 <span data-ttu-id="2de5f-104">Poniższy przykład stosuje <xref:System.Windows.Media.RotateTransform> do właściwości <xref:System.Windows.UIElement.RenderTransform%2A> elementu.</span><span class="sxs-lookup"><span data-stu-id="2de5f-104">The following example applies the <xref:System.Windows.Media.RotateTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span> <span data-ttu-id="2de5f-105">W przykładzie zastosowano <xref:System.Windows.Media.Animation.DoubleAnimation>, aby animować <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform>.</span><span class="sxs-lookup"><span data-stu-id="2de5f-105">The example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.Media.RotateTransform.Angle%2A> of the <xref:System.Windows.Media.RotateTransform>.</span></span> <span data-ttu-id="2de5f-106">Aby można było obrócić element, przykład ustawia właściwość <xref:System.Windows.UIElement.RenderTransformOrigin%2A> elementu na punkt (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="2de5f-106">To make the element spin in place, the example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property of the element to the point (0.5, 0.5).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2de5f-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="2de5f-107">Example</span></span>  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 <span data-ttu-id="2de5f-108">Aby uzyskać pełną próbkę, która zawiera więcej przykładów transformacji, zobacz przykład przekształceń [2-D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="2de5f-108">For the complete sample, which includes more transformation examples, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2de5f-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2de5f-109">See also</span></span>

- [<span data-ttu-id="2de5f-110">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="2de5f-110">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="2de5f-111">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="2de5f-111">Transforms Overview</span></span>](transforms-overview.md)
