---
title: Jak skalować element
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: f39bb4408e5b61912da30088de7c9f62587bc278
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="a8edb-102">Jak skalować element</span><span class="sxs-lookup"><span data-stu-id="a8edb-102">How to: Scale an Element</span></span>
<span data-ttu-id="a8edb-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.ScaleTransform> skalowania elementu.</span><span class="sxs-lookup"><span data-stu-id="a8edb-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="a8edb-104">Użyj <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości przez współczynnik określisz zmiany rozmiaru elementu.</span><span class="sxs-lookup"><span data-stu-id="a8edb-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="a8edb-105">Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartość 1.5 rozciąga się do 150 procent oryginalną szerokość elementu.</span><span class="sxs-lookup"><span data-stu-id="a8edb-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="a8edb-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> wartość 0,5 zmniejsza wysokość elementu 50 procent.</span><span class="sxs-lookup"><span data-stu-id="a8edb-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="a8edb-107">Użyj <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> właściwości, aby określić punkt, który jest Centrum operacji skalowania.</span><span class="sxs-lookup"><span data-stu-id="a8edb-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="a8edb-108">Domyślnie <xref:System.Windows.Media.ScaleTransform> skupia się w punkcie (0,0), która odpowiada górnego lewego rogu prostokąta.</span><span class="sxs-lookup"><span data-stu-id="a8edb-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="a8edb-109">Ma to wpływ przenoszenia elementu, a także sprawia, że są większe, ponieważ po zastosowaniu <xref:System.Windows.Media.Transform>, można zmienić przestrzeni współrzędnych, w której znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="a8edb-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="a8edb-110">W poniższym przykładzie użyto <xref:System.Windows.Media.ScaleTransform> podwojenia rozmiaru 50 przez 50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="a8edb-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="a8edb-111"><xref:System.Windows.Media.ScaleTransform> Ma wartość 0 (wartość domyślna) dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8edb-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8edb-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a8edb-112">Example</span></span>  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="a8edb-113">Zwykle ustawić <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> do Centrum obiektu, który ma: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).</span><span class="sxs-lookup"><span data-stu-id="a8edb-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="a8edb-114">W poniższym przykładzie przedstawiono innego <xref:System.Windows.Shapes.Rectangle> który jest podwójny rozmiar; jednak to <xref:System.Windows.Media.ScaleTransform> ma wartość 25 dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, które odpowiada Centrum prostokąta.</span><span class="sxs-lookup"><span data-stu-id="a8edb-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="a8edb-115">Na poniższej ilustracji przedstawiono różnice między tymi dwoma <xref:System.Windows.Media.ScaleTransform> operacji.</span><span class="sxs-lookup"><span data-stu-id="a8edb-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="a8edb-116">Linia kropkowana pokazuje rozmiar i położenie okna przed skalowania.</span><span class="sxs-lookup"><span data-stu-id="a8edb-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="a8edb-117">![Skale x 2 z różnymi punktami](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="a8edb-117">![2x scales with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="a8edb-118">Dwie operacje ScaleTransform z identycznymi wartościami ScaleX i ScaleY, ale różnych centrów</span><span class="sxs-lookup"><span data-stu-id="a8edb-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="a8edb-119">Pełny przykład, zobacz [2-D transformacje próbki](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="a8edb-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8edb-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a8edb-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="a8edb-121">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="a8edb-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="a8edb-122">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="a8edb-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
