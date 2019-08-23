---
title: 'Instrukcje: Stosowanie przekształceń do tekstu'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956470"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="d82e7-102">Instrukcje: Stosowanie przekształceń do tekstu</span><span class="sxs-lookup"><span data-stu-id="d82e7-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="d82e7-103">Przekształcenia mogą zmieniać sposób wyświetlania tekstu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d82e7-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="d82e7-104">W poniższych przykładach są używane różne typy transformacji renderowania, które wpływają na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="d82e7-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d82e7-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d82e7-105">Example</span></span>  
 <span data-ttu-id="d82e7-106">Poniższy przykład pokazuje tekst obrócony wokół określonego punktu w dwuwymiarowej płaszczyźnie x-y.</span><span class="sxs-lookup"><span data-stu-id="d82e7-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![Tekst obrócony przy użyciu elementu RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="d82e7-108">Poniższy przykład kodu używa <xref:System.Windows.Media.RotateTransform> do obracania tekstu.</span><span class="sxs-lookup"><span data-stu-id="d82e7-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="d82e7-109">Wartość <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 powoduje obrócenie elementu o 90 stopni w prawo.</span><span class="sxs-lookup"><span data-stu-id="d82e7-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="d82e7-110">Poniższy przykład pokazuje drugi wiersz tekstu skalowanego przez 150% wzdłuż osi x, a trzeci wiersz tekstu skalowany przez 150% wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="d82e7-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![Tekst skalowany przy użyciu ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 <span data-ttu-id="d82e7-112">Poniższy przykład kodu używa <xref:System.Windows.Media.ScaleTransform> do skalowania tekstu z oryginalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="d82e7-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> <span data-ttu-id="d82e7-113">Skalowanie tekstu nie jest takie samo, jak zwiększenie rozmiaru czcionki tekstu.</span><span class="sxs-lookup"><span data-stu-id="d82e7-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="d82e7-114">Rozmiary czcionek są obliczane niezależnie od siebie w celu zapewnienia optymalnego rozwiązania w różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="d82e7-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="d82e7-115">Z drugiej strony skalowanego tekstu zachowuje proporcje pierwotnego tekstu.</span><span class="sxs-lookup"><span data-stu-id="d82e7-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="d82e7-116">Poniższy przykład przedstawia tekst pochylony wzdłuż osi x.</span><span class="sxs-lookup"><span data-stu-id="d82e7-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![Tekst skośny przy użyciu SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 <span data-ttu-id="d82e7-118">Poniższy przykład kodu używa <xref:System.Windows.Media.SkewTransform> do pochylania tekstu.</span><span class="sxs-lookup"><span data-stu-id="d82e7-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="d82e7-119">Skośność, nazywana również ścinaniem, to transformacja, która rozciąga przestrzeń współrzędnych w sposób niejednolity.</span><span class="sxs-lookup"><span data-stu-id="d82e7-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="d82e7-120">W tym przykładzie dwa ciągi tekstowe są skośne — 30 ° i 30 ° wzdłuż współrzędnej x.</span><span class="sxs-lookup"><span data-stu-id="d82e7-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="d82e7-121">Poniższy przykład pokazuje tekst przetłumaczony lub przenoszony, wzdłuż osi x i y.</span><span class="sxs-lookup"><span data-stu-id="d82e7-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![Przesunięcie tekstu przy użyciu TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="d82e7-123">Poniższy przykład kodu używa <xref:System.Windows.Media.TranslateTransform> do przesunięcia tekstu.</span><span class="sxs-lookup"><span data-stu-id="d82e7-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="d82e7-124">W tym przykładzie nieznacznie przesunięta kopia tekstu poniżej podstawowego tekstu tworzy efekt cienia.</span><span class="sxs-lookup"><span data-stu-id="d82e7-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <span data-ttu-id="d82e7-125"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Oferuje bogaty zestaw funkcji do zapewniania efektów cienia.</span><span class="sxs-lookup"><span data-stu-id="d82e7-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="d82e7-126">Aby uzyskać więcej informacji, zobacz [Tworzenie tekstu przy użyciu cienia](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="d82e7-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82e7-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d82e7-127">See also</span></span>

- [<span data-ttu-id="d82e7-128">Stosowanie animacji do tekstu</span><span class="sxs-lookup"><span data-stu-id="d82e7-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
