---
title: Jak zastosować animacje do tekstu
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174631"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="5d1ae-102">Jak zastosować animacje do tekstu</span><span class="sxs-lookup"><span data-stu-id="5d1ae-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="5d1ae-103">Animacje mogą zmieniać wyświetlanie i wygląd tekstu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="5d1ae-104">Poniższe przykłady używają różnych typów animacji, aby <xref:System.Windows.Controls.TextBlock> wpłynąć na wyświetlanie tekstu w formancie.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d1ae-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="5d1ae-105">Example</span></span>  
 <span data-ttu-id="5d1ae-106">W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania szerokości bloku tekstu.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="5d1ae-107">Wartość szerokości zmienia się z szerokości bloku tekstu na 0 w czasie trwania 10 sekund, a następnie odwraca wartości szerokości i kontynuuje.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="5d1ae-108">Ten typ animacji tworzy efekt czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="5d1ae-109">W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania krycia bloku tekstu.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="5d1ae-110">Wartość krycia zmienia się z 1,0 na 0 w czasie trwania 5 sekund, a następnie odwraca wartości krycia i kontynuuje.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="5d1ae-111">Na poniższym diagramie <xref:System.Windows.Controls.TextBlock> przedstawiono efekt zmiany `1.00` krycia formantu z do `0.00` <xref:System.Windows.Media.Animation.Timeline.Duration%2A>5-sekundowego interwału zdefiniowanego przez .</span><span class="sxs-lookup"><span data-stu-id="5d1ae-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 ![Zmiana krycia tekstu z 1,00 na 0,00.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 <span data-ttu-id="5d1ae-113">W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.ColorAnimation> do animowania koloru pierwszego planu bloku tekstu.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-113">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="5d1ae-114">Wartość koloru pierwszego planu zmienia się z jednego koloru na drugi w czasie trwania 5 sekund, a następnie odwraca wartości kolorów i kontynuuje.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-114">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="5d1ae-115">W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimation> do obracania bloku tekstu.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-115">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="5d1ae-116">Blok tekstu wykonuje pełny obrót przez 20 sekund, a następnie kontynuuje powtarzanie obrotu.</span><span class="sxs-lookup"><span data-stu-id="5d1ae-116">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="5d1ae-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d1ae-117">See also</span></span>

- [<span data-ttu-id="5d1ae-118">Przegląd Animacja</span><span class="sxs-lookup"><span data-stu-id="5d1ae-118">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
