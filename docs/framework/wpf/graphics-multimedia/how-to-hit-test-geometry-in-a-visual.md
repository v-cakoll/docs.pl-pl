---
title: 'Instrukcje: Przeprowadź test trafienia geometrii w Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 4faf7a131b688fd245c0e207c8bac0f077b06ed5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709055"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="a9d43-102">Instrukcje: Przeprowadź test trafienia geometrii w Visual</span><span class="sxs-lookup"><span data-stu-id="a9d43-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="a9d43-103">W tym przykładzie pokazano, jak przeprowadzić test trafień na obiekt wizualny, który składa się z co najmniej jeden <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="a9d43-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9d43-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9d43-104">Example</span></span>  
 <span data-ttu-id="a9d43-105">Poniższy przykład pokazuje, jak pobrać <xref:System.Windows.Media.DrawingGroup> z visual obiektu, który używa <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a9d43-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="a9d43-106">Hit test jest przeprowadzane na renderowanej zawartości każdego rysunku w <xref:System.Windows.Media.DrawingGroup> do określenia, które geometrii został trafiony.</span><span class="sxs-lookup"><span data-stu-id="a9d43-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9d43-107">W większości przypadków należy użyć <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodę pozwala ustalić, czy punkt przecina dowolne renderowanej zawartości wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="a9d43-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="a9d43-108"><xref:System.Windows.Media.Geometry.FillContains%2A> Metodą jest przeciążona metoda, która pozwala na przeprowadzanie testu trafienia przy użyciu określonego <xref:System.Windows.Point> lub <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="a9d43-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="a9d43-109">Geometria jest malowania, obrysu można rozszerzyć poza granicami wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="a9d43-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="a9d43-110">W takim przypadku można wywołać <xref:System.Windows.Media.Geometry.StrokeContains%2A> oprócz <xref:System.Windows.Media.Geometry.FillContains%2A>.</span><span class="sxs-lookup"><span data-stu-id="a9d43-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="a9d43-111">Możesz też podać <xref:System.Windows.Media.ToleranceType> używany na potrzeby spłaszczanie Beziera.</span><span class="sxs-lookup"><span data-stu-id="a9d43-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9d43-112">W tym przykładzie nie bierze pod uwagę jakichkolwiek plików transformacji lub przycinania, które można stosować do geometrii.</span><span class="sxs-lookup"><span data-stu-id="a9d43-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="a9d43-113">Ponadto w tym przykładzie nie będzie działać z kontrolkę ze stylem, ponieważ nie ma rysunki bezpośrednio związane z nią.</span><span class="sxs-lookup"><span data-stu-id="a9d43-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d43-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9d43-114">See also</span></span>
- [<span data-ttu-id="a9d43-115">Test trafienia w warstwie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="a9d43-115">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="a9d43-116">Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru</span><span class="sxs-lookup"><span data-stu-id="a9d43-116">Hit Test Using Geometry as a Parameter</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
