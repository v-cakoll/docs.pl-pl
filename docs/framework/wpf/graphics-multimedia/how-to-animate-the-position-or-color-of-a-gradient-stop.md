---
title: Jak animować położenie i kolor zatrzymania gradientu
ms.date: 03/30/2017
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
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452847"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="cbdf4-102">Jak animować położenie i kolor zatrzymania gradientu</span><span class="sxs-lookup"><span data-stu-id="cbdf4-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="cbdf4-103">Ten przykład pokazuje, jak animować <xref:System.Windows.Media.GradientStop.Color%2A> i <xref:System.Windows.Media.GradientStop.Offset%2A> obiektów <xref:System.Windows.Media.GradientStop>.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbdf4-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbdf4-104">Example</span></span>  
 <span data-ttu-id="cbdf4-105">Poniższy przykład umożliwia animowanie trzech zatrzymań gradientów wewnątrz <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="cbdf4-106">W przykładzie są stosowane trzy animacje, z których każdy jest animowany w innym stopniu gradientu:</span><span class="sxs-lookup"><span data-stu-id="cbdf4-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
- <span data-ttu-id="cbdf4-107">Pierwsza animacja, <xref:System.Windows.Media.Animation.DoubleAnimation>, Animuj pierwszy <xref:System.Windows.Media.GradientStop.Offset%2A> stopu gradientu od 0,0 do 1,0, a następnie z powrotem do 0,0.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="cbdf4-108">W efekcie pierwszy kolor w gradiencie zostanie przesunięty z lewej strony do prawej krawędzi prostokąta, a następnie z powrotem do lewej strony.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
- <span data-ttu-id="cbdf4-109">Druga animacja, <xref:System.Windows.Media.Animation.ColorAnimation>, Animuj <xref:System.Windows.Media.GradientStop.Color%2A> drugiego zatrzymania gradientu z <xref:System.Windows.Media.Colors.Purple%2A> do <xref:System.Windows.Media.Colors.Yellow%2A>, a następnie z powrotem do <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="cbdf4-110">W efekcie kolor środkowy w gradiencie zmieni się z purpurowy na żółty i z powrotem na purpurowy.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
- <span data-ttu-id="cbdf4-111">Trzecia animacja, inna <xref:System.Windows.Media.Animation.ColorAnimation>, Animuj nieprzezroczystość trzeciego zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> o-1, a następnie z powrotem.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="cbdf4-112">W efekcie trzeci kolor w gradiencie znika, a następnie zmienia się nieprzezroczystie.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="cbdf4-113">Chociaż w tym przykładzie używa <xref:System.Windows.Media.LinearGradientBrush>, proces jest taki sam dla animacji obiektów <xref:System.Windows.Media.GradientStop> w <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="cbdf4-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="cbdf4-114">Aby uzyskać więcej przykładów, zobacz [przykład pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="cbdf4-114">For additional examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbdf4-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbdf4-115">See also</span></span>

- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="cbdf4-116">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="cbdf4-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="cbdf4-117">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="cbdf4-117">Storyboards Overview</span></span>](storyboards-overview.md)
