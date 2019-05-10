---
title: 'Instrukcje: Animowanie koloru lub nieprzezroczystości elementu SolidColorBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 610a7c4879b4ffe54940e8bc744dcca0711e84d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593397"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="ddc47-102">Instrukcje: Animowanie koloru lub nieprzezroczystości elementu SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="ddc47-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="ddc47-103">W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="ddc47-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddc47-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ddc47-104">Example</span></span>  
 <span data-ttu-id="ddc47-105">W poniższym przykładzie użyto trzy animacji, aby animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="ddc47-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
- <span data-ttu-id="ddc47-106">Pierwszy animacji <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla do <xref:System.Windows.Media.Colors.Gray%2A> gdy wskaźnik myszy zostanie przesunięty prostokąta.</span><span class="sxs-lookup"><span data-stu-id="ddc47-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
- <span data-ttu-id="ddc47-107">Dalej animacji innego <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla do <xref:System.Windows.Media.Colors.Orange%2A> gdy wskaźnik myszy opuszcza prostokąta.</span><span class="sxs-lookup"><span data-stu-id="ddc47-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
- <span data-ttu-id="ddc47-108">Końcowe animacji <xref:System.Windows.Media.Animation.DoubleAnimation>, zmienia przezroczystość pędzla 0,0 po naciśnięciu lewego przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="ddc47-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="ddc47-109">Aby uzyskać pełniejszy przykład pokazuje, jak animować różnego rodzaju pędzle, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="ddc47-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="ddc47-110">Aby uzyskać więcej informacji na temat animacji, zobacz [Przegląd animacja](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ddc47-110">For more information about animation, see the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="ddc47-111">Aby zachować spójność z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt, do ich animacji.</span><span class="sxs-lookup"><span data-stu-id="ddc47-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="ddc47-112">Jednak podczas stosowania pojedynczej animacji w kodzie, jest łatwiejszy w obsłudze <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="ddc47-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="ddc47-113">Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="ddc47-113">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc47-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddc47-114">See also</span></span>

- [<span data-ttu-id="ddc47-115">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="ddc47-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="ddc47-116">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="ddc47-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="ddc47-117">Przykład pędzle</span><span class="sxs-lookup"><span data-stu-id="ddc47-117">Brushes Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159973)
