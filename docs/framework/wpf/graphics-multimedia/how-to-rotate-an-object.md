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
ms.openlocfilehash: e17d3b7b9986b477df198480129edaf4c139c6bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112066"
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="1df02-102">Jak obrócić obiekt</span><span class="sxs-lookup"><span data-stu-id="1df02-102">How to: Rotate an Object</span></span>
<span data-ttu-id="1df02-103">W tym przykładzie pokazano, jak obrócić obiekt.</span><span class="sxs-lookup"><span data-stu-id="1df02-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="1df02-104">Przykład najpierw tworzy <xref:System.Windows.Media.RotateTransform> a, a <xref:System.Windows.Media.RotateTransform.Angle%2A> następnie określa jego w stopniach.</span><span class="sxs-lookup"><span data-stu-id="1df02-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="1df02-105">Poniższy przykład obraca <xref:System.Windows.Shapes.Polyline> obiekt o 45 stopni w lewym górnym rogu.</span><span class="sxs-lookup"><span data-stu-id="1df02-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1df02-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1df02-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="1df02-107">Właściwości <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> i właściwości <xref:System.Windows.Media.RotateTransform> określić punkt, o którym obiekt jest obrócony.</span><span class="sxs-lookup"><span data-stu-id="1df02-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="1df02-108">Ten punkt środkowy jest wyrażony w przestrzeni współrzędnych elementu, który jest przekształcany.</span><span class="sxs-lookup"><span data-stu-id="1df02-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="1df02-109">Domyślnie obrót jest stosowany do (0,0), który jest lewym górnym rogu obiektu do przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="1df02-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="1df02-110">W następnym przykładzie <xref:System.Windows.Shapes.Polyline> obróci obiekt zgodnie z ruchem wskazówek zegara o 45 stopni względem punktu (25,50).</span><span class="sxs-lookup"><span data-stu-id="1df02-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="1df02-111">Na poniższej ilustracji przedstawiono <xref:System.Windows.Media.Transform> wyniki stosowania a do dwóch obiektów.</span><span class="sxs-lookup"><span data-stu-id="1df02-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="1df02-112">![Obrót 45 stopni z różnymi punktami środkowymi](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="1df02-112">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="1df02-113">Dwa obiekty obracające się o 45 stopni z różnych centrów obrotowych</span><span class="sxs-lookup"><span data-stu-id="1df02-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="1df02-114">W <xref:System.Windows.Shapes.Polyline> poprzednich przykładach jest <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="1df02-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="1df02-115">Po zastosowaniu <xref:System.Windows.Media.Transform> <xref:System.Windows.UIElement.RenderTransform%2A> a do <xref:System.Windows.UIElement>właściwości , można <xref:System.Windows.UIElement.RenderTransformOrigin%2A> użyć właściwości, aby <xref:System.Windows.Media.Transform> określić początek dla każdego, który stosuje się do elementu.</span><span class="sxs-lookup"><span data-stu-id="1df02-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="1df02-116">Ponieważ <xref:System.Windows.UIElement.RenderTransformOrigin%2A> właściwość używa współrzędnych względnych, można zastosować przekształcenie do środka elementu, nawet jeśli nie znasz jego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="1df02-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="1df02-117">Aby uzyskać więcej informacji i na przykład, zobacz [Określanie pochodzenia transformacji przy użyciu wartości względnych](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="1df02-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="1df02-118">Aby uzyskać pełną próbkę, zobacz [Przykład przekształca 2D](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span><span class="sxs-lookup"><span data-stu-id="1df02-118">For the complete sample, see [2D Transforms Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df02-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1df02-119">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="1df02-120">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="1df02-120">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="1df02-121">Tematy in jakże</span><span class="sxs-lookup"><span data-stu-id="1df02-121">How-to Topics</span></span>](transformations-how-to-topics.md)
