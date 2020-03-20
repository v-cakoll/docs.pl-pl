---
title: Jak zastosować przekształcenia do tekstu
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
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141617"
---
# <a name="how-to-apply-transforms-to-text"></a><span data-ttu-id="d0ef8-102">Jak zastosować przekształcenia do tekstu</span><span class="sxs-lookup"><span data-stu-id="d0ef8-102">How to: Apply Transforms to Text</span></span>
<span data-ttu-id="d0ef8-103">Transformacje mogą zmienić wyświetlanie tekstu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-103">Transforms can alter the display of text in your application.</span></span> <span data-ttu-id="d0ef8-104">W poniższych przykładach użyto różnych typów przekształceń renderowania, aby wpłynąć na wyświetlanie tekstu w formancie. <xref:System.Windows.Controls.TextBlock></span><span class="sxs-lookup"><span data-stu-id="d0ef8-104">The following examples use different types of rendering transforms to affect the display of text in a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0ef8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d0ef8-105">Example</span></span>  
 <span data-ttu-id="d0ef8-106">Poniższy przykład przedstawia tekst obrócony względem określonego punktu na dwuwymiarowej płaszczyźnie x-y.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-106">The following example shows text rotated about a specified point in the two-dimensional x-y plane.</span></span>  
  
 ![Tekst obrócony za pomocą rotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 <span data-ttu-id="d0ef8-108">Poniższy przykład kodu <xref:System.Windows.Media.RotateTransform> używa do obracania tekstu.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-108">The following code example uses a <xref:System.Windows.Media.RotateTransform> to rotate text.</span></span> <span data-ttu-id="d0ef8-109">Wartość <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 obraca element o 90 stopni w prawo.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-109">An <xref:System.Windows.Media.RotateTransform.Angle%2A> value of 90 rotates the element 90 degrees clockwise.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 <span data-ttu-id="d0ef8-110">W poniższym przykładzie pokazano drugi wiersz tekstu przeskalowany o 150% wzdłuż osi x, a trzeci wiersz tekstu przeskalowany o 150% wzdłuż osi y.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-110">The following example shows the second line of text scaled by 150% along the x-axis, and the third line of text scaled by 150% along the y-axis.</span></span>  
  
 ![Tekst skalowany przy użyciu scaletransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 <span data-ttu-id="d0ef8-112">Poniższy przykład kodu <xref:System.Windows.Media.ScaleTransform> używa do skalowania tekstu z jego oryginalnego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-112">The following code example uses a <xref:System.Windows.Media.ScaleTransform> to scale text from its original size.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> <span data-ttu-id="d0ef8-113">Skalowanie tekstu nie jest tym samym, co zwiększenie rozmiaru czcionki tekstu.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-113">Scaling text is not the same as increasing the font size of text.</span></span> <span data-ttu-id="d0ef8-114">Rozmiary czcionek są obliczane niezależnie od siebie w celu zapewnienia najlepszej rozdzielczości w różnych rozmiarach.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-114">Font sizes are calculated independently of each other in order to provide the best resolution at different sizes.</span></span> <span data-ttu-id="d0ef8-115">Z drugiej strony skalowany tekst zachowuje proporcje tekstu o oryginalnym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-115">Scaled text, on the other hand, preserves the proportions of the original-sized text.</span></span>  
  
 <span data-ttu-id="d0ef8-116">W poniższym przykładzie pokazano tekst pochylony wzdłuż osi x.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-116">The following example shows text skewed along the x-axis.</span></span>  
  
 ![Tekst pochylony za pomocą skewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 <span data-ttu-id="d0ef8-118">Poniższy przykład kodu <xref:System.Windows.Media.SkewTransform> używa do pochylenia tekstu.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-118">The following code example uses a <xref:System.Windows.Media.SkewTransform> to skew text.</span></span> <span data-ttu-id="d0ef8-119">Pochylenie, znany również jako ścinanie, jest transformacja, która rozciąga przestrzeń współrzędnych w sposób nieujemny.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-119">A skew, also known as a shear, is a transformation that stretches the coordinate space in a non-uniform manner.</span></span> <span data-ttu-id="d0ef8-120">W tym przykładzie dwa ciągi tekstowe są pochylone -30° i 30° wzdłuż współrzędnej x.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-120">In this example, the two text strings are skewed -30° and 30° along the x-coordinate.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 <span data-ttu-id="d0ef8-121">W poniższym przykładzie przedstawiono tekst przetłumaczony lub przeniesiony wzdłuż osi x i y.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-121">The following example shows text translated, or moved, along the x- and y-axis.</span></span>  
  
 ![Przesunięcie tekstu przy użyciu translatetransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 <span data-ttu-id="d0ef8-123">Poniższy przykład kodu <xref:System.Windows.Media.TranslateTransform> używa do przesunięcia tekstu.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-123">The following code example uses a <xref:System.Windows.Media.TranslateTransform> to offset text.</span></span> <span data-ttu-id="d0ef8-124">W tym przykładzie nieznacznie odsunięta kopia tekstu poniżej tekstu podstawowego tworzy efekt cienia.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-124">In this example, a slightly offset copy of text below the primary text creates a shadow effect.</span></span>  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <span data-ttu-id="d0ef8-125">Zapewnia <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> bogaty zestaw funkcji zapewniających efekty cienia.</span><span class="sxs-lookup"><span data-stu-id="d0ef8-125">The <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> provides a rich set of features for providing shadow effects.</span></span> <span data-ttu-id="d0ef8-126">Aby uzyskać więcej informacji, zobacz [Tworzenie tekstu za pomocą cienia](how-to-create-text-with-a-shadow.md).</span><span class="sxs-lookup"><span data-stu-id="d0ef8-126">For more information, see [Create Text with a Shadow](how-to-create-text-with-a-shadow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ef8-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0ef8-127">See also</span></span>

- [<span data-ttu-id="d0ef8-128">Stosowanie animacji do tekstu</span><span class="sxs-lookup"><span data-stu-id="d0ef8-128">Apply Animations to Text</span></span>](how-to-apply-animations-to-text.md)
