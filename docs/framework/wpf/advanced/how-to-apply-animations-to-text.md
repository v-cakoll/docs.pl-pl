---
title: 'Instrukcje: Zastosuj animacje do tekstu'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: e62c8288460206e7ebfbc18787bd9c2f2144a5bc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356965"
---
# <a name="how-to-apply-animations-to-text"></a><span data-ttu-id="23459-102">Instrukcje: Zastosuj animacje do tekstu</span><span class="sxs-lookup"><span data-stu-id="23459-102">How to: Apply Animations to Text</span></span>
<span data-ttu-id="23459-103">Animacji można zmienić ekran i wygląd tekstu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="23459-103">Animations can alter the display and appearance of text in your application.</span></span> <span data-ttu-id="23459-104">W poniższych przykładach używane różne rodzaje animacji wpływa na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> kontroli.</span><span class="sxs-lookup"><span data-stu-id="23459-104">The following examples use different types of animations to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23459-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="23459-105">Example</span></span>  
 <span data-ttu-id="23459-106">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować szerokość blok tekstu.</span><span class="sxs-lookup"><span data-stu-id="23459-106">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the width of the text block.</span></span> <span data-ttu-id="23459-107">Wartość szerokości zmieni się z szerokość blok tekstu 0 dany okres 10 sekund, a następnie odwraca wartości szerokości i jest kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="23459-107">The width value changes from the width of the text block to 0 over a duration of 10 seconds, and then reverses the width values and continues.</span></span> <span data-ttu-id="23459-108">Ten typ animacji tworzy efekt czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="23459-108">This type of animation creates a wipe effect.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 <span data-ttu-id="23459-109">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować nieprzezroczystość blok tekstu.</span><span class="sxs-lookup"><span data-stu-id="23459-109">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the opacity of the text block.</span></span> <span data-ttu-id="23459-110">Wartość nieprzezroczystości zmieni się z wersji 1.0 0 dany okres 5 sekund, a następnie odwraca nieprzezroczystość wartości i jest kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="23459-110">The opacity value changes from 1.0 to 0 over a duration of 5 seconds, and then reverses the opacity values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 <span data-ttu-id="23459-111">Na poniższym diagramie przedstawiono efekt <xref:System.Windows.Controls.TextBlock> kontroli, zmiana jego nieprzezroczystości od `1.00` do `0.00` podczas 5-sekundowego interwału definicją <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span><span class="sxs-lookup"><span data-stu-id="23459-111">The following diagram shows the effect of the <xref:System.Windows.Controls.TextBlock> control changing its opacity from `1.00` to `0.00` during the 5-second interval defined by the <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.</span></span>  
  
 <span data-ttu-id="23459-112">![Tekst, zmiana nieprzezroczystość z 1,00 0,00](./media/fadedtext01.png "FadedText01")</span><span class="sxs-lookup"><span data-stu-id="23459-112">![Text changing opacity from 1.00 to 0.00](./media/fadedtext01.png "FadedText01")</span></span>  
<span data-ttu-id="23459-113">Nieprzezroczystość tekstu zmiana z 1,00 0,00</span><span class="sxs-lookup"><span data-stu-id="23459-113">Text Opacity changing from 1.00 to 0.00</span></span>  
  
 <span data-ttu-id="23459-114">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ColorAnimation> animować kolor pierwszego planu blok tekstu.</span><span class="sxs-lookup"><span data-stu-id="23459-114">The following example uses a <xref:System.Windows.Media.Animation.ColorAnimation> to animate the foreground color of the text block.</span></span> <span data-ttu-id="23459-115">Wartość koloru pierwszego planu zmieni się z jednego koloru na drugi kolor dany okres 5 sekund, a następnie odwraca wartości kolorów i jest kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="23459-115">The foreground color value changes from one color to a second color over a duration of 5 seconds, and then reverses the color values and continues.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 <span data-ttu-id="23459-116">W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> wymienić blok tekstu.</span><span class="sxs-lookup"><span data-stu-id="23459-116">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to rotate the text block.</span></span> <span data-ttu-id="23459-117">Blok tekstu wykonuje pełne obrotu w czasie trwania wynoszącego 20 sekund i następnie w dalszym ciągu należy powtórzyć obrót.</span><span class="sxs-lookup"><span data-stu-id="23459-117">The text block performs a full rotation over a duration of 20 seconds, and then continues to repeat the rotation.</span></span>  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a><span data-ttu-id="23459-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23459-118">See also</span></span>
- [<span data-ttu-id="23459-119">Animacja — przegląd</span><span class="sxs-lookup"><span data-stu-id="23459-119">Animation Overview</span></span>](../graphics-multimedia/animation-overview.md)
