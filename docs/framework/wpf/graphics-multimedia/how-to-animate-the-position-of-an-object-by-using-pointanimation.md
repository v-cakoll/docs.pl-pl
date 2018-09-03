---
title: Jak animować położenie obiektu z wykorzystaniem PointAnimation
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], animation
- animation [WPF], PointAnimation
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
ms.openlocfilehash: 91447685988d91dfe86707c2cf265deabeb717b9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2018
ms.locfileid: "43465698"
---
# <a name="how-to-animate-the-position-of-an-object-by-using-pointanimation"></a><span data-ttu-id="ef1c2-102">Jak animować położenie obiektu z wykorzystaniem PointAnimation</span><span class="sxs-lookup"><span data-stu-id="ef1c2-102">How to: Animate the Position of an Object by Using PointAnimation</span></span>
<span data-ttu-id="ef1c2-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.Animation.PointAnimation> klasy, aby animować obiekt <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimation> class to animate an object along a <xref:System.Windows.Shapes.Path>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef1c2-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ef1c2-104">Example</span></span>  
 <span data-ttu-id="ef1c2-105">Poniższy przykład powoduje przeniesienie elipsę <xref:System.Windows.Shapes.Path> z jednego miejsca na ekranie do innego.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-105">The following example moves an ellipse along a <xref:System.Windows.Shapes.Path> from one point on the screen to another.</span></span> <span data-ttu-id="ef1c2-106">Przykład animuje położenie <xref:System.Windows.Media.EllipseGeometry> przy użyciu <xref:System.Windows.Media.Animation.PointAnimation> animować <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-106">The example animates the position of an <xref:System.Windows.Media.EllipseGeometry> by using <xref:System.Windows.Media.Animation.PointAnimation> to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ef1c2-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef1c2-107">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimation>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.EllipseGeometry>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>  
 [<span data-ttu-id="ef1c2-108">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="ef1c2-108">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="ef1c2-109">Grafika i multimedia</span><span class="sxs-lookup"><span data-stu-id="ef1c2-109">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)  
 [<span data-ttu-id="ef1c2-110">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ef1c2-110">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)  
 [<span data-ttu-id="ef1c2-111">Animacja i chronometraż</span><span class="sxs-lookup"><span data-stu-id="ef1c2-111">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="ef1c2-112">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="ef1c2-112">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
