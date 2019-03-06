---
title: 'Instrukcje: Określ źródło przekształcenia przy użyciu wartości względnych'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: bdcc17e2d9bf68170c10dd8e35670f3e072a527c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352571"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="71576-102">Instrukcje: Określ źródło przekształcenia przy użyciu wartości względnych</span><span class="sxs-lookup"><span data-stu-id="71576-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="71576-103">Ten przykład pokazuje, jak określić źródło przy użyciu wartości względnych <xref:System.Windows.UIElement.RenderTransform%2A> mający zastosowanie do <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="71576-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="71576-104">Kiedy należy obrócić, skalowania lub pochylania <xref:System.Windows.FrameworkElement> przy użyciu <xref:System.Windows.UIElement.RenderTransform%2A> właściwość, domyślne ustawienie ma zastosowanie transformacji do lewego górnego rogu elementu.</span><span class="sxs-lookup"><span data-stu-id="71576-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="71576-105">Jeśli chcesz obrócić, skalowania lub pochylić z Centrum elementu można kompensacji, ustawiając środek przekształcenia do środka elementu.</span><span class="sxs-lookup"><span data-stu-id="71576-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="71576-106">Rozwiązanie wymaga jednak, że znasz rozmiar elementu.</span><span class="sxs-lookup"><span data-stu-id="71576-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="71576-107">Łatwiejszy sposób stosowania transformacji do środka elementu jest określenie jego <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości (0,5, 0,5), zamiast ustawiać wartość center na przekształcenie, sam.</span><span class="sxs-lookup"><span data-stu-id="71576-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71576-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="71576-108">Example</span></span>  
 <span data-ttu-id="71576-109">W poniższym przykładzie użyto <xref:System.Windows.Media.RotateTransform> wymienić <xref:System.Windows.Controls.Button> 45 stopni w prawo.</span><span class="sxs-lookup"><span data-stu-id="71576-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="71576-110">Ponieważ przykładu nie określa Centrum, przycisk obraca się o punkt (0, 0), który jest jego lewego górnego rogu.</span><span class="sxs-lookup"><span data-stu-id="71576-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="71576-111"><xref:System.Windows.Media.RotateTransform> Jest stosowany do <xref:System.Windows.UIElement.RenderTransform%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="71576-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="71576-112">Poniższa ilustracja przedstawia wynik transformacji, na przykład, który następuje po.</span><span class="sxs-lookup"><span data-stu-id="71576-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="71576-113">![Przekształcona przy użyciu RenderTransform przycisku](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="71576-113">![A button transformed using RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="71576-114">45 stopni obrót w prawo wokół przy użyciu RenderTransform właściwość</span><span class="sxs-lookup"><span data-stu-id="71576-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="71576-115">W poniższym przykładzie użyto również <xref:System.Windows.Media.RotateTransform> wymienić <xref:System.Windows.Controls.Button> 45 stopni zgodnie ze wskazówkami zegara, ale w tym przykładzie <xref:System.Windows.UIElement.RenderTransformOrigin%2A> przycisku (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="71576-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="71576-116">W rezultacie obrót zastosowano do środka przycisk, a nie do lewego górnego rogu.</span><span class="sxs-lookup"><span data-stu-id="71576-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="71576-117">Poniższa ilustracja przedstawia wynik transformacji, na przykład, który następuje po.</span><span class="sxs-lookup"><span data-stu-id="71576-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="71576-118">![Przycisk przekształcony o jej środka](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="71576-118">![A button transformed about its center](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="71576-119">45 stopni przy użyciu RenderTransform właściwość RenderTransformOrigin z (0,5, 0,5)</span><span class="sxs-lookup"><span data-stu-id="71576-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="71576-120">Aby uzyskać więcej informacji na temat przekształcania <xref:System.Windows.FrameworkElement> obiekty, zobacz [przekształca Przegląd](transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="71576-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71576-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71576-121">See also</span></span>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="71576-122">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="71576-122">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="71576-123">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="71576-123">How-to Topics</span></span>](transformations-how-to-topics.md)
