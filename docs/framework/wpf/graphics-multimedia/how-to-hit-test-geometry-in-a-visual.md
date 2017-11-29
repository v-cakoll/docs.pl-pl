---
title: "Jak przeprowadzić test trafienia geometrii w Visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ab125fe4031b5408eb202f21ce0fdf4314781f1a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a><span data-ttu-id="fe3ac-102">Jak przeprowadzić test trafienia geometrii w Visual</span><span class="sxs-lookup"><span data-stu-id="fe3ac-102">How to: Hit Test Geometry in a Visual</span></span>
<span data-ttu-id="fe3ac-103">W tym przykładzie przedstawiono sposób wykonywania testu trafienia na obiekt wizualny, który składa się z co najmniej jeden <xref:System.Windows.Media.Geometry> obiektów.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-103">This example shows how to perform a hit test on a visual object that is composed of one or more <xref:System.Windows.Media.Geometry> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe3ac-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="fe3ac-104">Example</span></span>  
 <span data-ttu-id="fe3ac-105">Poniższy przykład przedstawia sposób pobrać <xref:System.Windows.Media.DrawingGroup> z obiektu visual, która używa <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-105">The following example shows how to retrieve the <xref:System.Windows.Media.DrawingGroup> from a visual object that uses the <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> method.</span></span> <span data-ttu-id="fe3ac-106">Testu trafienia następnie odbywa się na renderowanej zawartości każdego rysunku w <xref:System.Windows.Media.DrawingGroup> do określenia, które geometrii został trafiony.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-106">A hit test is then performed on the rendered content of each drawing in the <xref:System.Windows.Media.DrawingGroup> to determine which geometry was hit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe3ac-107">W większości przypadków należy użyć <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodę, aby określić, czy punkt przecina żadnego renderowanej zawartości obiektu visual.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-107">In most cases, you would use the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method to determine whether a point intersects any of the rendered content of a visual.</span></span>  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <span data-ttu-id="fe3ac-108"><xref:System.Windows.Media.Geometry.FillContains%2A> Metody jest przeciążona metoda służy do testowania trafienia przy użyciu określonej <xref:System.Windows.Point> lub <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-108">The <xref:System.Windows.Media.Geometry.FillContains%2A> method is an overloaded method that allows you to hit test by using a specified <xref:System.Windows.Point> or <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="fe3ac-109">Geometrię jest malowania, obrysu można rozszerzyć poza granicami wypełnienia.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-109">If a geometry is stroked, the stroke can extend outside the fill bounds.</span></span> <span data-ttu-id="fe3ac-110">W takim przypadku można wywołać <xref:System.Windows.Media.Geometry.StrokeContains%2A> oprócz <xref:System.Windows.Media.Geometry.FillContains%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-110">In which case, you may want to call <xref:System.Windows.Media.Geometry.StrokeContains%2A> in addition to <xref:System.Windows.Media.Geometry.FillContains%2A>.</span></span>  
  
 <span data-ttu-id="fe3ac-111">Można też podać <xref:System.Windows.Media.ToleranceType> używany na potrzeby spłaszczanie Beziera.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-111">You can also provide a <xref:System.Windows.Media.ToleranceType> that is used for the purposes of Bezier flattening.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe3ac-112">W tym przykładzie nie bierze pod uwagę transformacje lub wycinek, który może być stosowany do geometrii.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-112">This sample does not take into account any transforms or clipping that may be applied to the geometry.</span></span> <span data-ttu-id="fe3ac-113">Ponadto w tym przykładzie nie będzie działać z formantu, ponieważ nie ma rysunki bezpośrednio związane z nią.</span><span class="sxs-lookup"><span data-stu-id="fe3ac-113">In addition, this sample will not work with a styled control, since it does not have any drawings directly associated with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3ac-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe3ac-114">See Also</span></span>  
 [<span data-ttu-id="fe3ac-115">Testowanie w warstwie Visual trafień</span><span class="sxs-lookup"><span data-stu-id="fe3ac-115">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="fe3ac-116">Kliknij przycisk Test przy użyciu geometrii jako parametr</span><span class="sxs-lookup"><span data-stu-id="fe3ac-116">Hit Test Using Geometry as a Parameter</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
