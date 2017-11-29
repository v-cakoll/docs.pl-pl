---
title: "Jak zastosować przekształcenia do tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ed10a00d3d62f7eae91e5932a917be692de868b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="986a5-102">Jak zastosować przekształcenia do tekstu</span><span class="sxs-lookup"><span data-stu-id="986a5-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="986a5-103">Transformacje można zmienić wyświetlanie tekstu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="986a5-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="986a5-104">W poniższych przykładach użyto różnego rodzaju transformacje renderowania wpływ na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> formantu.</span><span class="sxs-lookup"><span data-stu-id="986a5-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="986a5-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="986a5-105">Example</span></span>  
 <span data-ttu-id="986a5-106">W poniższym przykładzie przedstawiono tekst obraca wokół punktu określonego w płaszczyźnie dwuwymiarowa x i y.</span><span class="sxs-lookup"><span data-stu-id="986a5-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 <span data-ttu-id="986a5-107">![Tekst obrócony przy użyciu RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span><span class="sxs-lookup"><span data-stu-id="986a5-107">![Text rotated using a RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")</span></span>  
<span data-ttu-id="986a5-108">Przykład tekstu obracany o 90 stopni</span><span class="sxs-lookup"><span data-stu-id="986a5-108">Example of text rotated 90 degrees</span></span>  
  
 <span data-ttu-id="986a5-109">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.RotateTransform> obracania tekstu.</span><span class="sxs-lookup"><span data-stu-id="986a5-109">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="986a5-110"><xref:System.Windows.Media.RotateTransform.Angle%2A> Wartość 90 obraca element 90 stopni w prawo.</span><span class="sxs-lookup"><span data-stu-id="986a5-110">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="986a5-111">W poniższym przykładzie pokazano drugi wiersz tekstu skalowania o 150% wzdłuż osi x, a trzeci wiersz tekstu skalowania o 150% wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="986a5-111">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 <span data-ttu-id="986a5-112">![Tekst wyskalowany przy użyciu ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span><span class="sxs-lookup"><span data-stu-id="986a5-112">![Text scaled using a ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")</span></span>  
<span data-ttu-id="986a5-113">Przykład skalowana tekstu</span><span class="sxs-lookup"><span data-stu-id="986a5-113">Example of scaled text</span></span>  
  
 <span data-ttu-id="986a5-114">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.ScaleTransform> na skali tekst z oryginalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="986a5-114">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  <span data-ttu-id="986a5-115">Skalowanie tekstu nie jest taka sama jak zwiększyć rozmiar czcionki tekstu.</span><span class="sxs-lookup"><span data-stu-id="986a5-115">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="986a5-116">Rozmiary czcionek są obliczane niezależnie od siebie nawzajem w celu zapewnienia najlepsze rozwiązania w różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="986a5-116">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="986a5-117">Skalowanie tekstu z drugiej strony, zachowuje proporcje o rozmiarze oryginalny tekst.</span><span class="sxs-lookup"><span data-stu-id="986a5-117">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="986a5-118">W poniższym przykładzie przedstawiono tekst niesymetryczna wzdłuż osi x.</span><span class="sxs-lookup"><span data-stu-id="986a5-118">The following example shows text skewed along the x-axis.</span></span>  
  
 <span data-ttu-id="986a5-119">![Tekst niesymetryczna przy użyciu metody SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span><span class="sxs-lookup"><span data-stu-id="986a5-119">![Text skewed using a SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")</span></span>  
<span data-ttu-id="986a5-120">Przykład spowodowałoby zafałszowanie tekstu</span><span class="sxs-lookup"><span data-stu-id="986a5-120">Example of skewed text</span></span>  
  
 <span data-ttu-id="986a5-121">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.SkewTransform> fałszować tekstu.</span><span class="sxs-lookup"><span data-stu-id="986a5-121">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="986a5-122">Zegara, znanej także jako Ścinanie jest transformację w sposób niejednolitego rozciąga się przestrzeni współrzędnych.</span><span class="sxs-lookup"><span data-stu-id="986a5-122">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="986a5-123">W tym przykładzie dwa ciągi są spowodowałoby zafałszowanie-30 i 30 wzdłuż współrzędną x.</span><span class="sxs-lookup"><span data-stu-id="986a5-123">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="986a5-124">W poniższym przykładzie przedstawiono tekstu translacji lub przenieść wzdłuż x i y.</span><span class="sxs-lookup"><span data-stu-id="986a5-124">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 <span data-ttu-id="986a5-125">![Przesunięcie, przy użyciu TranslateTransform tekstu](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span><span class="sxs-lookup"><span data-stu-id="986a5-125">![Text offset using a TranslateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")</span></span>  
<span data-ttu-id="986a5-126">Przykład tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="986a5-126">Example of translated text</span></span>  
  
 <span data-ttu-id="986a5-127">Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.TranslateTransform> do Przesunięcie tekstu.</span><span class="sxs-lookup"><span data-stu-id="986a5-127">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="986a5-128">W tym przykładzie nieco przesunięcia kopię tekstu poniżej tekst podstawowy tworzy efektem cienia.</span><span class="sxs-lookup"><span data-stu-id="986a5-128">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <span data-ttu-id="986a5-129"><xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Zawiera bogaty zestaw funkcji do prezentowania efekty cienia.</span><span class="sxs-lookup"><span data-stu-id="986a5-129">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="986a5-130">Aby uzyskać więcej informacji, zobacz [Tworzenie tekstu w tle](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="986a5-130">For more information, see [Create Text with a Shadow](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986a5-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="986a5-131">See Also</span></span>  
 [<span data-ttu-id="986a5-132">Zastosowanie animacji do tekstu</span><span class="sxs-lookup"><span data-stu-id="986a5-132">Apply Animations to Text</span></span>](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
