---
title: 'Instrukcje: Przeprowadzanie testu trafienia geometrii w wizualizacji'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923377"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="b8b7c-102">Instrukcje: Przeprowadzanie testu trafienia geometrii w wizualizacji</span><span class="sxs-lookup"><span data-stu-id="b8b7c-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="b8b7c-103">Ten przykład pokazuje, jak wykonać test trafień na obiekcie wizualizacji, który składa się z co <xref:System.Windows.Media.Geometry> najmniej jednego obiektu.</span><span class="sxs-lookup"><span data-stu-id="b8b7c-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8b7c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b8b7c-104">Example</span></span>  
 <span data-ttu-id="b8b7c-105">Poniższy przykład pokazuje, <xref:System.Windows.Media.DrawingGroup> jak pobrać z obiektu wizualizacji, który <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> używa metody.</span><span class="sxs-lookup"><span data-stu-id="b8b7c-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="b8b7c-106">Test trafień jest następnie wykonywany dla renderowanej zawartości każdego rysunku w programie, <xref:System.Windows.Media.DrawingGroup> aby określić, która geometria została trafiona.</span><span class="sxs-lookup"><span data-stu-id="b8b7c-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8b7c-107">W większości przypadków można użyć <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody, aby określić, czy punkt przecina zawartość wizualizacji.</span><span class="sxs-lookup"><span data-stu-id="b8b7c-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="b8b7c-108">Metoda jest przeciążoną metodą, która umożliwia trafienie testu przy użyciu określonego <xref:System.Windows.Point> lub <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.Geometry.FillContains%2A></span><span class="sxs-lookup"><span data-stu-id="b8b7c-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="b8b7c-109">W przypadku wybrania geometrii, naciśnięcie może wykraczać poza granice wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="b8b7c-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="b8b7c-110">W takim przypadku może być konieczne wywołanie <xref:System.Windows.Media.Geometry.StrokeContains%2A> dodatku do. <xref:System.Windows.Media.Geometry.FillContains%2A></span><span class="sxs-lookup"><span data-stu-id="b8b7c-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="b8b7c-111">Możesz również podać <xref:System.Windows.Media.ToleranceType> , który jest używany do celów spłaszczania Beziera.</span><span class="sxs-lookup"><span data-stu-id="b8b7c-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8b7c-112">Ten przykład nie uwzględnia żadnych transformacji lub wycinków, które mogą być stosowane do geometrii.</span><span class="sxs-lookup"><span data-stu-id="b8b7c-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="b8b7c-113">Ponadto ten przykład nie będzie działał z kontrolką z stylem, ponieważ nie ma bezpośrednio skojarzonych z nim rysunków.</span><span class="sxs-lookup"><span data-stu-id="b8b7c-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b7c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b8b7c-114">See also</span></span>

- [<span data-ttu-id="b8b7c-115">Test trafienia w warstwie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="b8b7c-115">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="b8b7c-116">Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru</span><span class="sxs-lookup"><span data-stu-id="b8b7c-116">Hit Test Using Geometry as a Parameter</span></span>](how-to-hit-test-using-geometry-as-a-parameter.md)
