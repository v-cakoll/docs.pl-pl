---
title: 'Instrukcje: Animuj położenie i kolor zatrzymania gradientu'
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
ms.openlocfilehash: 6d8c1bb5cd133b2ee9d50a7e851d2ca3b4fff023
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368889"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a><span data-ttu-id="4e640-102">Instrukcje: Animuj położenie i kolor zatrzymania gradientu</span><span class="sxs-lookup"><span data-stu-id="4e640-102">How to: Animate the Position or Color of a Gradient Stop</span></span>
<span data-ttu-id="4e640-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.GradientStop.Color%2A> i <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> obiektów.</span><span class="sxs-lookup"><span data-stu-id="4e640-103">This example shows how to animate the <xref:System.Windows.Media.GradientStop.Color%2A> and <xref:System.Windows.Media.GradientStop.Offset%2A> of <xref:System.Windows.Media.GradientStop> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e640-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e640-104">Example</span></span>  
 <span data-ttu-id="4e640-105">Poniższy przykład animuje trzy ograniczniki gradientu wewnątrz <xref:System.Windows.Media.LinearGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="4e640-105">The following example animates three gradient stops inside a <xref:System.Windows.Media.LinearGradientBrush>.</span></span> <span data-ttu-id="4e640-106">W przykładzie zastosowano trzy animacji, z których każdy animuje różnych gradientu:</span><span class="sxs-lookup"><span data-stu-id="4e640-106">The example uses three animations, each of which animates a different gradient stop:</span></span>  
  
-   <span data-ttu-id="4e640-107">Pierwszy animacji <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje pierwszy zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Offset%2A> od 0,0 do 1,0, a następnie ponownie 0,0.</span><span class="sxs-lookup"><span data-stu-id="4e640-107">The first animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, animates the first gradient stop's <xref:System.Windows.Media.GradientStop.Offset%2A> from 0.0 to 1.0 and then back to 0.0.</span></span> <span data-ttu-id="4e640-108">Dlatego pierwszy kolor w gradientu przesunięcia od lewej do prawej krawędzi prostokąta, a następnie ponownie po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="4e640-108">As a result, the first color in the gradient shifts from the left side to the right side of the rectangle and then back to the left side.</span></span>  
  
-   <span data-ttu-id="4e640-109">Drugiej animacji <xref:System.Windows.Media.Animation.ColorAnimation>, animuje drugi zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> do <xref:System.Windows.Media.Colors.Yellow%2A> , a następnie ponownie do <xref:System.Windows.Media.Colors.Purple%2A>.</span><span class="sxs-lookup"><span data-stu-id="4e640-109">The second animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, animates the second gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> from <xref:System.Windows.Media.Colors.Purple%2A> to <xref:System.Windows.Media.Colors.Yellow%2A> and then back to <xref:System.Windows.Media.Colors.Purple%2A>.</span></span> <span data-ttu-id="4e640-110">W rezultacie kolor środkowy gradientu zmieni się z purpurowy żółty i ponownie purpurowy.</span><span class="sxs-lookup"><span data-stu-id="4e640-110">As a result, the middle color in the gradient changes from purple to yellow and back to purple.</span></span>  
  
-   <span data-ttu-id="4e640-111">Trzeci animacji innego <xref:System.Windows.Media.Animation.ColorAnimation>, animuje nieprzezroczystość trzeci zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> przez -1, a następnie ponownie.</span><span class="sxs-lookup"><span data-stu-id="4e640-111">The third animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, animates the opacity of the third gradient stop's <xref:System.Windows.Media.GradientStop.Color%2A> by -1 and then back.</span></span> <span data-ttu-id="4e640-112">W rezultacie trzeci kolor gradientu zacieniony i następnie ponownie staje się nieprzezroczyste.</span><span class="sxs-lookup"><span data-stu-id="4e640-112">As a result, the third color in the gradient fades away and then becomes opaque again.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 <span data-ttu-id="4e640-113">Mimo że w tym przykładzie użyto <xref:System.Windows.Media.LinearGradientBrush>, proces jest taki sam dla animowanie <xref:System.Windows.Media.GradientStop> obiektów wewnątrz <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="4e640-113">Although this example uses a <xref:System.Windows.Media.LinearGradientBrush>, the process is the same for animating <xref:System.Windows.Media.GradientStop> objects inside a <xref:System.Windows.Media.RadialGradientBrush>.</span></span>  
  
 <span data-ttu-id="4e640-114">Aby uzyskać więcej przykładów, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="4e640-114">For additional examples, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e640-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4e640-115">See also</span></span>
- <xref:System.Windows.Media.GradientStop>
- [<span data-ttu-id="4e640-116">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="4e640-116">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4e640-117">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="4e640-117">Storyboards Overview</span></span>](storyboards-overview.md)
