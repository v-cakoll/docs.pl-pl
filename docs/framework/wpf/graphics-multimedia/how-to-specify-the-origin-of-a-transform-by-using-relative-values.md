---
title: Jak określić źródło przekształcenia przy użyciu wartości względnych
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: ff263af8fbedeec483eee213c07dd4ec169805de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561410"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="c61fe-102">Jak określić źródło przekształcenia przy użyciu wartości względnych</span><span class="sxs-lookup"><span data-stu-id="c61fe-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="c61fe-103">W tym przykładzie pokazano, jak Użyj względne wartości w celu określenia pochodzenia <xref:System.Windows.UIElement.RenderTransform%2A> do zastosowano <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="c61fe-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="c61fe-104">Gdy można obracanie, skalowanie i pochylanie <xref:System.Windows.FrameworkElement> przy użyciu <xref:System.Windows.UIElement.RenderTransform%2A> właściwość, domyślne ustawienie jest stosowana transformacja lewego górnego rogu elementu.</span><span class="sxs-lookup"><span data-stu-id="c61fe-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="c61fe-105">Jeśli chcesz obracanie, skalowanie i pochylanie z Centrum elementu można kompensacji ustawiając Centrum przekształcenie Centrum elementu.</span><span class="sxs-lookup"><span data-stu-id="c61fe-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="c61fe-106">Rozwiązania wymaga jednak, że znasz rozmiar elementu.</span><span class="sxs-lookup"><span data-stu-id="c61fe-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="c61fe-107">Prostszy sposób stosowania przekształcenia do Centrum elementu jest określenie jego <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości (0,5, 0,5), zamiast ustawiania wartości center na transformacji samego.</span><span class="sxs-lookup"><span data-stu-id="c61fe-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c61fe-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c61fe-108">Example</span></span>  
 <span data-ttu-id="c61fe-109">W poniższym przykładzie użyto <xref:System.Windows.Media.RotateTransform> obracania <xref:System.Windows.Controls.Button> 45 stopni w prawo.</span><span class="sxs-lookup"><span data-stu-id="c61fe-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="c61fe-110">Ponieważ przykładzie nie określa Centrum, przycisk obraca informacje o punkcie (0, 0), który jest jego lewym górnym rogu.</span><span class="sxs-lookup"><span data-stu-id="c61fe-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="c61fe-111"><xref:System.Windows.Media.RotateTransform> Jest stosowany do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c61fe-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="c61fe-112">Na poniższej ilustracji przedstawiono wynik transformacji, na przykład, który jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="c61fe-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="c61fe-113">![Przycisk przekształcony przy użyciu właściwości RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="c61fe-113">![A button transformed using RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="c61fe-114">Obrót w prawo 45 stopni przy użyciu właściwości RenderTransform</span><span class="sxs-lookup"><span data-stu-id="c61fe-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="c61fe-115">W poniższym przykładzie również użyto <xref:System.Windows.Media.RotateTransform> obracania <xref:System.Windows.Controls.Button> 45 stopni w prawo, jednak w tym przykładzie <xref:System.Windows.UIElement.RenderTransformOrigin%2A> przycisku (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="c61fe-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="c61fe-116">W związku z tym obrót jest stosowany do Centrum przycisku zamiast do lewego górnego rogu.</span><span class="sxs-lookup"><span data-stu-id="c61fe-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="c61fe-117">Na poniższej ilustracji przedstawiono wynik transformacji, na przykład, który jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="c61fe-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="c61fe-118">![Przycisk przekształcony o jego center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="c61fe-118">![A button transformed about its center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="c61fe-119">45 stopni przy użyciu właściwości RenderTransform RenderTransformOrigin z (0,5, 0,5)</span><span class="sxs-lookup"><span data-stu-id="c61fe-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="c61fe-120">Aby uzyskać więcej informacji na temat przekształcania <xref:System.Windows.FrameworkElement> obiekty, zobacz [przekształca omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c61fe-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c61fe-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c61fe-121">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="c61fe-122">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="c61fe-122">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="c61fe-123">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c61fe-123">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
