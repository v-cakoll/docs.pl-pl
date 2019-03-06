---
title: 'Instrukcje: Zastosuj przekształcenia do tekstu'
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
ms.openlocfilehash: fd86293c539bf58ac93894e0b879dddb984825e1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378952"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="6d720-102">Instrukcje: Zastosuj przekształcenia do tekstu</span><span class="sxs-lookup"><span data-stu-id="6d720-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="6d720-103">Przekształcenia można zmienić wyświetlanie tekstu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6d720-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="6d720-104">W poniższych przykładach używane różne rodzaje transformacje renderowania wpływa na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> kontroli.</span><span class="sxs-lookup"><span data-stu-id="6d720-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d720-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6d720-105">Example</span></span>  
 <span data-ttu-id="6d720-106">Poniższy przykład pokazuje tekst obrócony dotyczące określonego punktu na płaszczyźnie dwuwymiarowej x i y.</span><span class="sxs-lookup"><span data-stu-id="6d720-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="6d720-107">![Tekst obrócony przy użyciu RotateTransform](./media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="6d720-107">![Text rotated using a RotateTransform](./media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="6d720-108">Przykład tekstu obróconą o 90 stopni</span><span class="sxs-lookup"><span data-stu-id="6d720-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="6d720-109">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.RotateTransform> Aby obrócić tekst.</span><span class="sxs-lookup"><span data-stu-id="6d720-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="6d720-110"><xref:System.Windows.Media.RotateTransform.Angle%2A> Wartość 90 obraca element 90 stopni w prawo.</span><span class="sxs-lookup"><span data-stu-id="6d720-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="6d720-111">Poniższy przykład pokazuje, drugi wiersz tekstu skalowania przez 150% wzdłuż osi x, a trzeci wiersz tekstu skalowania przez 150% wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="6d720-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="6d720-112">![Tekst skalowane za pomocą ScaleTransform](./media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="6d720-112">![Text scaled using a ScaleTransform](./media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="6d720-113">Przykład skalowany tekst</span><span class="sxs-lookup"><span data-stu-id="6d720-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="6d720-114">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.ScaleTransform> na tekst w skali od oryginalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="6d720-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="6d720-115">Skalowanie tekst nie jest taka sama, jak zwiększyć rozmiar czcionki tekstu.</span><span class="sxs-lookup"><span data-stu-id="6d720-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="6d720-116">Rozmiary czcionek są obliczane niezależnie od siebie, aby zapewnić najlepsze rozwiązania w różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="6d720-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="6d720-117">Skalowany tekst zachowuje z drugiej strony, jeśli chodzi o rozmiarze oryginalny tekst.</span><span class="sxs-lookup"><span data-stu-id="6d720-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="6d720-118">Poniższy przykład pokazuje tekst skośny wzdłuż osi x.</span><span class="sxs-lookup"><span data-stu-id="6d720-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="6d720-119">![Tekst skośny przy użyciu metody SkewTransform](./media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="6d720-119">![Text skewed using a SkewTransform](./media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="6d720-120">Przykładowy tekst skośny</span><span class="sxs-lookup"><span data-stu-id="6d720-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="6d720-121">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.SkewTransform> fałszować tekstu.</span><span class="sxs-lookup"><span data-stu-id="6d720-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="6d720-122">Przesunięcia czasowego, znany także jako Pochyl jest przekształcenie, które rozciąga przestrzeni współrzędnych w sposób obsługuje technologię niejednolitego.</span><span class="sxs-lookup"><span data-stu-id="6d720-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="6d720-123">W tym przykładzie dwa ciągi są niesymetryczne-30 i 30 wzdłuż współrzędną x.</span><span class="sxs-lookup"><span data-stu-id="6d720-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="6d720-124">Poniższy przykład pokazuje tekst przetłumaczony lub przeniesiona, wzdłuż osi x i y.</span><span class="sxs-lookup"><span data-stu-id="6d720-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="6d720-125">![Przesunięcie, przy użyciu TranslateTransform tekstu](./media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="6d720-125">![Text offset using a TranslateTransform](./media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="6d720-126">Przykład przetłumaczonego tekstu</span><span class="sxs-lookup"><span data-stu-id="6d720-126">Example of translated text</span></span>  
  
 <span data-ttu-id="6d720-127">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.TranslateTransform> na przesunięcie tekstu.</span><span class="sxs-lookup"><span data-stu-id="6d720-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="6d720-128">W tym przykładzie nieco przesunięcia kopię tekstu poniżej tekst podstawowy tworzy efekt w tle.</span><span class="sxs-lookup"><span data-stu-id="6d720-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="6d720-129"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Zapewnia bogaty zestaw funkcji do prezentowania efekty.</span><span class="sxs-lookup"><span data-stu-id="6d720-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="6d720-130">Aby uzyskać więcej informacji, zobacz [Utwórz tekst z cieniem](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="6d720-130">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d720-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d720-131">See also</span></span>
- [<span data-ttu-id="6d720-132">Stosowanie animacji do tekstu</span><span class="sxs-lookup"><span data-stu-id="6d720-132">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
