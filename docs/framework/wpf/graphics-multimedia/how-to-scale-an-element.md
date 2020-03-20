---
title: Jak skalować element
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: a383ad84f1db4d937469943092a03517f68777ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187435"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="74c85-102">Jak skalować element</span><span class="sxs-lookup"><span data-stu-id="74c85-102">How to: Scale an Element</span></span>
<span data-ttu-id="74c85-103">W tym przykładzie <xref:System.Windows.Media.ScaleTransform> pokazano, jak użyć a do skalowania elementu.</span><span class="sxs-lookup"><span data-stu-id="74c85-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="74c85-104">Użyj <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> i, aby zmienić rozmiar elementu według określonego współczynnika.</span><span class="sxs-lookup"><span data-stu-id="74c85-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="74c85-105">Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartość 1,5 rozciąga element do 150 procent jego pierwotnej szerokości.</span><span class="sxs-lookup"><span data-stu-id="74c85-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="74c85-106">Wartość <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 zmniejsza wysokość elementu o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="74c85-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="74c85-107">Użyj <xref:System.Windows.Media.ScaleTransform.CenterX%2A> właściwości <xref:System.Windows.Media.ScaleTransform.CenterY%2A> i, aby określić punkt, który jest środkiem operacji skalowania.</span><span class="sxs-lookup"><span data-stu-id="74c85-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="74c85-108">Domyślnie a <xref:System.Windows.Media.ScaleTransform> jest wyśrodkowany w punkcie (0,0), co odpowiada lewemu górnemu rogu prostokąta.</span><span class="sxs-lookup"><span data-stu-id="74c85-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="74c85-109">Ma to wpływ na przenoszenie elementu, a także na jego <xref:System.Windows.Media.Transform>powiększanie, ponieważ po zastosowaniu elementu , należy zmienić przestrzeń współrzędnych, w której znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="74c85-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="74c85-110">W poniższym przykładzie <xref:System.Windows.Media.ScaleTransform> użyto do podwojenia rozmiaru 50 <xref:System.Windows.Shapes.Rectangle>na 50 .</span><span class="sxs-lookup"><span data-stu-id="74c85-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="74c85-111">Wartość <xref:System.Windows.Media.ScaleTransform> 0 (domyślna) dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>i .</span><span class="sxs-lookup"><span data-stu-id="74c85-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74c85-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="74c85-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="74c85-113"><xref:System.Windows.Media.ScaleTransform.CenterX%2A> Zazwyczaj ustawia się <xref:System.Windows.Media.ScaleTransform.CenterY%2A> i na środku obiektu, który jest<xref:System.Windows.FrameworkElement.Width%2A>skalowany: <xref:System.Windows.FrameworkElement.Height%2A>( /2, /2).</span><span class="sxs-lookup"><span data-stu-id="74c85-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="74c85-114">W poniższym <xref:System.Windows.Shapes.Rectangle> przykładzie pokazano inny, który jest podwojony rozmiar; jednak ma <xref:System.Windows.Media.ScaleTransform> to wartość 25 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> dla <xref:System.Windows.Media.ScaleTransform.CenterY%2A>obu i , która odpowiada środkowi prostokąta.</span><span class="sxs-lookup"><span data-stu-id="74c85-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="74c85-115">Na poniższej ilustracji przedstawiono różnicę między tymi dwoma <xref:System.Windows.Media.ScaleTransform> operacjami.</span><span class="sxs-lookup"><span data-stu-id="74c85-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="74c85-116">Linia kropkowana pokazuje rozmiar i położenie prostokąta przed skalowaniem.</span><span class="sxs-lookup"><span data-stu-id="74c85-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="74c85-117">![2x wagi z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="74c85-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="74c85-118">Dwie operacje ScaleTransform z identycznymi wartościami ScaleX i ScaleY, ale z różnymi centrami</span><span class="sxs-lookup"><span data-stu-id="74c85-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="74c85-119">Aby uzyskać pełną próbkę, zobacz [przykład przekształca 2-W](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="74c85-119">For the complete sample, see [2-D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74c85-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74c85-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="74c85-121">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="74c85-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="74c85-122">Tematy in jakże</span><span class="sxs-lookup"><span data-stu-id="74c85-122">How-to Topics</span></span>](transformations-how-to-topics.md)
