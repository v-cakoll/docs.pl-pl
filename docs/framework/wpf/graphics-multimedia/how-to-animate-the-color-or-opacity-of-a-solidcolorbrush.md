---
title: Jak animować kolor lub nieprzezroczystość SolidColorBrush
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452886"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a><span data-ttu-id="7f675-102">Jak animować kolor lub nieprzezroczystość SolidColorBrush</span><span class="sxs-lookup"><span data-stu-id="7f675-102">How to: Animate the Color or Opacity of a SolidColorBrush</span></span>
<span data-ttu-id="7f675-103">Ten przykład pokazuje, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="7f675-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f675-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7f675-104">Example</span></span>  
 <span data-ttu-id="7f675-105">W poniższym przykładzie zastosowano trzy animacje do animowania <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="7f675-105">The following example uses three animations to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> and <xref:System.Windows.Media.Brush.Opacity%2A> of a <xref:System.Windows.Media.SolidColorBrush>.</span></span>  
  
- <span data-ttu-id="7f675-106">Pierwsza animacja, <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla na <xref:System.Windows.Media.Colors.Gray%2A>, gdy wskaźnik myszy zostanie przesunięty do prostokąta.</span><span class="sxs-lookup"><span data-stu-id="7f675-106">The first animation, a <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Gray%2A> when the mouse enters the rectangle.</span></span>  
  
- <span data-ttu-id="7f675-107">Kolejna animacja, inna <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla na <xref:System.Windows.Media.Colors.Orange%2A>, gdy wskaźnik myszy opuszcza prostokąt.</span><span class="sxs-lookup"><span data-stu-id="7f675-107">The next animation, another <xref:System.Windows.Media.Animation.ColorAnimation>, changes the brush's color to <xref:System.Windows.Media.Colors.Orange%2A> when the mouse leaves the rectangle.</span></span>  
  
- <span data-ttu-id="7f675-108">Ostatnia animacja, <xref:System.Windows.Media.Animation.DoubleAnimation>, zmienia krycie pędzla na 0,0 po naciśnięciu lewego przycisku myszy.</span><span class="sxs-lookup"><span data-stu-id="7f675-108">The final animation, a <xref:System.Windows.Media.Animation.DoubleAnimation>, changes the brush's opacity to 0.0 when the left mouse button is pressed.</span></span>  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 <span data-ttu-id="7f675-109">Aby zapoznać się z bardziej kompletnym przykładem, który pokazuje, jak animować różne typy pędzli, zobacz [przykład pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="7f675-109">For a more complete sample, which shows how to animate different types of brushes, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="7f675-110">Aby uzyskać więcej informacji na temat animacji, zobacz [Omówienie animacji](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7f675-110">For more information about animation, see the [Animation Overview](animation-overview.md).</span></span>  
  
 <span data-ttu-id="7f675-111">Aby zapewnić spójność z innymi przykładami animacji, wersje kodu tego przykładu używają obiektu <xref:System.Windows.Media.Animation.Storyboard>, aby zastosować ich animacje.</span><span class="sxs-lookup"><span data-stu-id="7f675-111">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply their animations.</span></span> <span data-ttu-id="7f675-112">Jednak podczas stosowania pojedynczej animacji w kodzie, łatwiej jest używać metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> zamiast używać <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="7f675-112">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="7f675-113">Aby zapoznać się z przykładem, zobacz [Animuj a Property bez używania scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="7f675-113">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f675-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7f675-114">See also</span></span>

- [<span data-ttu-id="7f675-115">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="7f675-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="7f675-116">Scenorysy — przegląd</span><span class="sxs-lookup"><span data-stu-id="7f675-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="7f675-117">Przykładowe pędzle</span><span class="sxs-lookup"><span data-stu-id="7f675-117">Brushes Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
