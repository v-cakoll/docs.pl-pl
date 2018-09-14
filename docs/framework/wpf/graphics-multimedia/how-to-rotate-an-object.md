---
title: Jak obrócić obiekt
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: b5a954158388e8b85589042e9d1f3b82c1747e30
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591506"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="f18f5-102">Jak obrócić obiekt</span><span class="sxs-lookup"><span data-stu-id="f18f5-102">How to: Rotate an Object</span></span>
<span data-ttu-id="f18f5-103">Ten przykład pokazuje, jak obrócić obiekt.</span><span class="sxs-lookup"><span data-stu-id="f18f5-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="f18f5-104">W przykładzie najpierw jest tworzony <xref:System.Windows.Media.RotateTransform> , a następnie określa jego <xref:System.Windows.Media.RotateTransform.Angle%2A> w stopniach.</span><span class="sxs-lookup"><span data-stu-id="f18f5-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="f18f5-105">Poniższy przykład obraca <xref:System.Windows.Shapes.Polyline> obiektu 45 stopni, o jego lewego górnego rogu.</span><span class="sxs-lookup"><span data-stu-id="f18f5-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18f5-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="f18f5-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="f18f5-107"><xref:System.Windows.Media.RotateTransform.CenterX%2A> i <xref:System.Windows.Media.RotateTransform.CenterY%2A> właściwości <xref:System.Windows.Media.RotateTransform> Określ punkt o tym, które obrotu obiektu.</span><span class="sxs-lookup"><span data-stu-id="f18f5-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="f18f5-108">Ten punkt środkowy jest wyrażona w układzie współrzędnych elementu, który jest przekształcany.</span><span class="sxs-lookup"><span data-stu-id="f18f5-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="f18f5-109">Domyślnie obrót jest stosowany do (0,0), czyli lewego górnego rogu obiektu do przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="f18f5-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="f18f5-110">Obraca się w następnym przykładzie <xref:System.Windows.Shapes.Polyline> obiektu do ruchu wskazówek zegara 45 stopni, o punkt (25,50).</span><span class="sxs-lookup"><span data-stu-id="f18f5-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="f18f5-111">Na poniższej ilustracji przedstawiono wyniki zastosowania <xref:System.Windows.Media.Transform> do dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="f18f5-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="f18f5-112">![Obroty 45 stopni z różnymi punktami](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="f18f5-112">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="f18f5-113">Dwa obiekty, które Obrót o 45 stopni za pośrednictwem różnych obrotowych centrów</span><span class="sxs-lookup"><span data-stu-id="f18f5-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="f18f5-114"><xref:System.Windows.Shapes.Polyline> w poprzednich przykładach <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f18f5-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="f18f5-115">Po zastosowaniu <xref:System.Windows.Media.Transform> do <xref:System.Windows.UIElement.RenderTransform%2A> właściwość <xref:System.Windows.UIElement>, możesz użyć <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwości w celu określenia początek dla każdego <xref:System.Windows.Media.Transform> przeznaczonych do elementu.</span><span class="sxs-lookup"><span data-stu-id="f18f5-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="f18f5-116">Ponieważ <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość używa współrzędnych względnych, można zastosować przekształcenie do środka elementu, nawet jeśli nie znasz jego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="f18f5-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="f18f5-117">Aby uzyskać więcej informacji i przykład zobacz [Określ źródło przekształcenia przy użyciu wartości względnych](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="f18f5-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="f18f5-118">Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="f18f5-118">For the complete sample, see [2-D Transforms Sample](https://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f18f5-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f18f5-119">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="f18f5-120">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="f18f5-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="f18f5-121">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="f18f5-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
