---
title: 'Instrukcje: Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923405"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="5532f-102">Instrukcje: Przeprowadzanie testu trafienia przy użyciu geometrii jako parametru</span><span class="sxs-lookup"><span data-stu-id="5532f-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="5532f-103">Ten przykład pokazuje, jak wykonać test trafień na obiekcie wizualizacji przy użyciu <xref:System.Windows.Media.Geometry> jako parametru testu trafień.</span><span class="sxs-lookup"><span data-stu-id="5532f-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5532f-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5532f-104">Example</span></span>  
 <span data-ttu-id="5532f-105">Poniższy przykład pokazuje, jak skonfigurować test trafień za pomocą <xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> dla metody.</span><span class="sxs-lookup"><span data-stu-id="5532f-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="5532f-106">Wartość, która jest przesyłana `OnMouseDown` do metody, <xref:System.Windows.Media.Geometry> jest używana do utworzenia obiektu w celu rozszerzenia zakresu testu trafień. <xref:System.Windows.Point></span><span class="sxs-lookup"><span data-stu-id="5532f-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="5532f-107">Właściwość zawiera informacje o wynikach testu <xref:System.Windows.Media.Geometry> trafień wykorzystujących jako parametr testu trafień. <xref:System.Windows.Media.GeometryHitTestResult> <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A></span><span class="sxs-lookup"><span data-stu-id="5532f-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="5532f-108">Na poniższej ilustracji przedstawiono relacje między geometrią testu trafień (niebieski okrąg) i renderowanej zawartości docelowego obiektu wizualizacji (czerwony kwadrat).</span><span class="sxs-lookup"><span data-stu-id="5532f-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 ![Diagram pokazujący IntersectionDetail używany podczas testowania trafień.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 <span data-ttu-id="5532f-110">Poniższy przykład pokazuje, jak zaimplementować wywołanie zwrotne testu trafień, <xref:System.Windows.Media.Geometry> gdy jest używany jako parametr testu trafień.</span><span class="sxs-lookup"><span data-stu-id="5532f-110">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="5532f-111">Parametr jest rzutowany <xref:System.Windows.Media.GeometryHitTestResult> do w celu <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> pobrania wartości właściwości. `result`</span><span class="sxs-lookup"><span data-stu-id="5532f-111">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="5532f-112">Wartość właściwości pozwala określić, czy <xref:System.Windows.Media.Geometry> parametr testu trafień jest w pełni lub częściowo zawarty w renderowanej zawartości docelowego testu trafień.</span><span class="sxs-lookup"><span data-stu-id="5532f-112">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="5532f-113">W tym przypadku przykładowy kod dodaje tylko wyniki testów trafień do listy dla wizualizacji, które są w pełni zawarte w granicy docelowej.</span><span class="sxs-lookup"><span data-stu-id="5532f-113">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> <span data-ttu-id="5532f-114">Nie należy wywoływać <xref:System.Windows.Media.IntersectionDetail.Empty> wywołaniazwrotnego,jeśliszczegółymiędzyczęściowe<xref:System.Windows.Media.HitTestResult> są.</span><span class="sxs-lookup"><span data-stu-id="5532f-114">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5532f-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5532f-115">See also</span></span>

- [<span data-ttu-id="5532f-116">Test trafienia w warstwie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="5532f-116">Hit Testing in the Visual Layer</span></span>](hit-testing-in-the-visual-layer.md)
- [<span data-ttu-id="5532f-117">Przeprowadzanie testu trafienia geometrii w wizualizacji</span><span class="sxs-lookup"><span data-stu-id="5532f-117">Hit Test Geometry in a Visual</span></span>](how-to-hit-test-geometry-in-a-visual.md)
