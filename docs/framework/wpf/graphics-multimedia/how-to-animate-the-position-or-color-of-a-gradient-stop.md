---
title: "Jak animować położenie i kolor zatrzymania gradientu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 968d285d8a3345da9810f0ba4797bf8b2e33d36e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="e0d21-102">Jak animować położenie i kolor zatrzymania gradientu</span><span class="sxs-lookup"><span data-stu-id="e0d21-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="e0d21-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.GradientStop.Color%2A> i <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> obiektów.</span><span class="sxs-lookup"><span data-stu-id="e0d21-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0d21-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0d21-104">Example</span></span>  
 <span data-ttu-id="e0d21-105">Poniższy przykład animuje trzy gradientu wewnątrz <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="e0d21-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="e0d21-106">W przykładzie użyto animacje trzy, z których każdy animuje różnych gradientu:</span><span class="sxs-lookup"><span data-stu-id="e0d21-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
-   <span data-ttu-id="e0d21-107">Pierwszy animacji <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje pierwszy ograniczniku gradientu <xref:System.Windows.Media.GradientStop.Offset%2A> od 0,0 do 1,0, a następnie z powrotem do 0,0.</span><span class="sxs-lookup"><span data-stu-id="e0d21-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="e0d21-108">W związku z tym pierwszy kolorów w gradientu przesunięcia od lewej do prawej krawędzi prostokąta, a następnie z powrotem do lewej.</span><span class="sxs-lookup"><span data-stu-id="e0d21-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
-   <span data-ttu-id="e0d21-109">Drugi animacji <xref:System.Windows.Media.Animation.ColorAnimation>, animuje drugi ograniczniku gradientu <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> do <xref:System.Windows.Media.Colors.Yellow%2A> , a następnie z powrotem do <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="e0d21-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="e0d21-110">W związku z tym Środkowy kolor gradientu zmienia purpurowy żółty i z powrotem na fioletowo.</span><span class="sxs-lookup"><span data-stu-id="e0d21-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
-   <span data-ttu-id="e0d21-111">Trzeci animacji innego <xref:System.Windows.Media.Animation.ColorAnimation>, animuje przezroczystość trzeci ograniczniku gradientu <xref:System.Windows.Media.GradientStop.Color%2A> przez wartość -1, a następnie ponownie.</span><span class="sxs-lookup"><span data-stu-id="e0d21-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="e0d21-112">W związku z tym trzeci kolor gradientu zniknie i następnie ponownie staje się przezroczystości.</span><span class="sxs-lookup"><span data-stu-id="e0d21-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="e0d21-113">Mimo że w tym przykładzie użyto <xref:System.Windows.Media.LinearGradientBrush>, proces jest taki sam dla animacji <xref:System.Windows.Media.GradientStop> obiektów wewnątrz <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="e0d21-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="e0d21-114">Aby uzyskać dodatkowe przykłady, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="e0d21-114">For additional examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d21-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e0d21-115">See Also</span></span>  
 <xref:System.Windows.Media.GradientStop>  
 [<span data-ttu-id="e0d21-116">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="e0d21-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="e0d21-117">Scenorys — omówienie</span><span class="sxs-lookup"><span data-stu-id="e0d21-117">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
