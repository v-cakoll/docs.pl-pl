---
title: Jak skalować element
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 34d954f68747be9eedc0ef71634e0c18b411d260
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112053"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="75c12-102">Jak skalować element</span><span class="sxs-lookup"><span data-stu-id="75c12-102">How to: Scale an Element</span></span>
<span data-ttu-id="75c12-103">W tym przykładzie <xref:System.Windows.Media.ScaleTransform> pokazano, jak użyć a do skalowania elementu.</span><span class="sxs-lookup"><span data-stu-id="75c12-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="75c12-104">Użyj <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> właściwości <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> i, aby zmienić rozmiar elementu według określonego współczynnika.</span><span class="sxs-lookup"><span data-stu-id="75c12-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="75c12-105">Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartość 1,5 rozciąga element do 150 procent jego pierwotnej szerokości.</span><span class="sxs-lookup"><span data-stu-id="75c12-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="75c12-106">Wartość <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 zmniejsza wysokość elementu o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="75c12-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="75c12-107">Użyj <xref:System.Windows.Media.ScaleTransform.CenterX%2A> właściwości <xref:System.Windows.Media.ScaleTransform.CenterY%2A> i, aby określić punkt, który jest środkiem operacji skalowania.</span><span class="sxs-lookup"><span data-stu-id="75c12-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="75c12-108">Domyślnie a <xref:System.Windows.Media.ScaleTransform> jest wyśrodkowany w punkcie (0,0), co odpowiada lewemu górnemu rogu prostokąta.</span><span class="sxs-lookup"><span data-stu-id="75c12-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="75c12-109">Ma to wpływ na przenoszenie elementu, a także na jego <xref:System.Windows.Media.Transform>powiększanie, ponieważ po zastosowaniu elementu , należy zmienić przestrzeń współrzędnych, w której znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="75c12-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="75c12-110">W poniższym przykładzie <xref:System.Windows.Media.ScaleTransform> użyto do podwojenia rozmiaru 50 <xref:System.Windows.Shapes.Rectangle>na 50 .</span><span class="sxs-lookup"><span data-stu-id="75c12-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="75c12-111">Wartość <xref:System.Windows.Media.ScaleTransform> 0 (domyślna) dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>i .</span><span class="sxs-lookup"><span data-stu-id="75c12-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75c12-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="75c12-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="75c12-113"><xref:System.Windows.Media.ScaleTransform.CenterX%2A> Zazwyczaj ustawia się <xref:System.Windows.Media.ScaleTransform.CenterY%2A> i na środku obiektu, który jest<xref:System.Windows.FrameworkElement.Width%2A>skalowany: <xref:System.Windows.FrameworkElement.Height%2A>( /2, /2).</span><span class="sxs-lookup"><span data-stu-id="75c12-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="75c12-114">W poniższym <xref:System.Windows.Shapes.Rectangle> przykładzie pokazano inny, który jest podwojony rozmiar; jednak ma <xref:System.Windows.Media.ScaleTransform> to wartość 25 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> dla <xref:System.Windows.Media.ScaleTransform.CenterY%2A>obu i , która odpowiada środkowi prostokąta.</span><span class="sxs-lookup"><span data-stu-id="75c12-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="75c12-115">Na poniższej ilustracji przedstawiono różnicę między tymi dwoma <xref:System.Windows.Media.ScaleTransform> operacjami.</span><span class="sxs-lookup"><span data-stu-id="75c12-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="75c12-116">Linia kropkowana pokazuje rozmiar i położenie prostokąta przed skalowaniem.</span><span class="sxs-lookup"><span data-stu-id="75c12-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="75c12-117">![2x wagi z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="75c12-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="75c12-118">Dwie operacje ScaleTransform z identycznymi wartościami ScaleX i ScaleY, ale z różnymi centrami</span><span class="sxs-lookup"><span data-stu-id="75c12-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="75c12-119">Aby uzyskać pełną próbkę, zobacz [Przykład przekształca 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="75c12-119">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c12-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75c12-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="75c12-121">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="75c12-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="75c12-122">Tematy in jakże</span><span class="sxs-lookup"><span data-stu-id="75c12-122">How-to Topics</span></span>](transformations-how-to-topics.md)
