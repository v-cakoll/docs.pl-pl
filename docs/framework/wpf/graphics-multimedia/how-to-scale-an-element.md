---
title: 'Instrukcje: Skalowanie elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 607b3a11085f746503c1b82552f1740b49d9ef5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942077"
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="429fc-102">Instrukcje: Skalowanie elementu</span><span class="sxs-lookup"><span data-stu-id="429fc-102">How to: Scale an Element</span></span>
<span data-ttu-id="429fc-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.ScaleTransform> skalowania elementu.</span><span class="sxs-lookup"><span data-stu-id="429fc-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="429fc-104">Użyj <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> i <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> właściwości przez współczynnik określisz zmiany rozmiaru elementu.</span><span class="sxs-lookup"><span data-stu-id="429fc-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="429fc-105">Na przykład <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> wartość 1.5 rozciąga elementu do 150 procent jego oryginalna szerokość.</span><span class="sxs-lookup"><span data-stu-id="429fc-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="429fc-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> wartość 0,5 zmniejsza wysokość elementu o 50%.</span><span class="sxs-lookup"><span data-stu-id="429fc-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="429fc-107">Użyj <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> właściwości, aby określić punkt, który jest środek operacji skalowania.</span><span class="sxs-lookup"><span data-stu-id="429fc-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="429fc-108">Domyślnie <xref:System.Windows.Media.ScaleTransform> skupia się w momencie (0,0), który odnosi się do lewego górnego rogu prostokąta.</span><span class="sxs-lookup"><span data-stu-id="429fc-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="429fc-109">Ma to wpływ przenoszenia elementu, a także sprawia, że wyświetlane, ponieważ po zastosowaniu <xref:System.Windows.Media.Transform>, zmień przestrzeni współrzędnych, w której znajduje się obiekt.</span><span class="sxs-lookup"><span data-stu-id="429fc-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="429fc-110">W poniższym przykładzie użyto <xref:System.Windows.Media.ScaleTransform> dwukrotnie rozmiar 50 przez 50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="429fc-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="429fc-111"><xref:System.Windows.Media.ScaleTransform> Ma wartość 0 (domyślnie) dla obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="429fc-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="429fc-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="429fc-112">Example</span></span>  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="429fc-113">Zwykle ustawiasz <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A> do środka obiekt, który jest skalowany: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).</span><span class="sxs-lookup"><span data-stu-id="429fc-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="429fc-114">W poniższym przykładzie pokazano inny <xref:System.Windows.Shapes.Rectangle> który podwaja się rozmiar jednak to <xref:System.Windows.Media.ScaleTransform> ma wartość 25 w obu <xref:System.Windows.Media.ScaleTransform.CenterX%2A> i <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, która odnosi się do Centrum prostokąta.</span><span class="sxs-lookup"><span data-stu-id="429fc-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="429fc-115">Poniższa ilustracja przedstawia różnicę między tymi dwoma <xref:System.Windows.Media.ScaleTransform> operacji.</span><span class="sxs-lookup"><span data-stu-id="429fc-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="429fc-116">Linia kropkowana pokazuje rozmiar i położenie prostokąta przed skalowaniem.</span><span class="sxs-lookup"><span data-stu-id="429fc-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="429fc-117">![Skale x 2 z różnymi punktami](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="429fc-117">![2x scales with different center points](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="429fc-118">Dwie operacje ScaleTransform — za pomocą identycznych wartości ScaleX i ScaleY, ale różnych centrów</span><span class="sxs-lookup"><span data-stu-id="429fc-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="429fc-119">Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="429fc-119">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="429fc-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="429fc-120">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="429fc-121">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="429fc-121">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="429fc-122">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="429fc-122">How-to Topics</span></span>](transformations-how-to-topics.md)
