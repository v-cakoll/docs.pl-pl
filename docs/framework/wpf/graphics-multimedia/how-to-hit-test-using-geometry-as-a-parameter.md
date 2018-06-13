---
title: Jak przeprowadzać test trafienia przy użyciu geometrii jako parametru
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 57b04f7f8c9bcc21f6b970c2981c2bab51044c10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561258"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a><span data-ttu-id="c9c60-102">Jak przeprowadzać test trafienia przy użyciu geometrii jako parametru</span><span class="sxs-lookup"><span data-stu-id="c9c60-102">How to: Hit Test Using Geometry as a Parameter</span></span>
<span data-ttu-id="c9c60-103">W tym przykładzie przedstawiono sposób wykonywania testu trafienia na obiekt wizualny przy użyciu <xref:System.Windows.Media.Geometry> jako trafienie testowania parametru.</span><span class="sxs-lookup"><span data-stu-id="c9c60-103">This example shows how to perform a hit test on a visual object using a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9c60-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9c60-104">Example</span></span>  
 <span data-ttu-id="c9c60-105">Poniższy przykład przedstawia sposób konfigurowane za pomocą testu trafienia <xref:System.Windows.Media.GeometryHitTestParameters> dla <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c9c60-105">The following example shows how to set up a hit test using <xref:System.Windows.Media.GeometryHitTestParameters> for the <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> method.</span></span> <span data-ttu-id="c9c60-106"><xref:System.Windows.Point> Wartość, która została przekazana do `OnMouseDown` metoda służy do tworzenia <xref:System.Windows.Media.Geometry> obiekt, aby rozszerzyć zakres testu trafienia.</span><span class="sxs-lookup"><span data-stu-id="c9c60-106">The <xref:System.Windows.Point> value that is passed to the `OnMouseDown` method is used to create a <xref:System.Windows.Media.Geometry> object in order to expand the range of the hit test.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <span data-ttu-id="c9c60-107"><xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Właściwość <xref:System.Windows.Media.GeometryHitTestResult> zawiera informacje o wynikach testu trafienia, która używa <xref:System.Windows.Media.Geometry> jako trafienie testowania parametru.</span><span class="sxs-lookup"><span data-stu-id="c9c60-107">The <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property of <xref:System.Windows.Media.GeometryHitTestResult> provides information about the results of a hit test that uses a <xref:System.Windows.Media.Geometry> as a hit test parameter.</span></span> <span data-ttu-id="c9c60-108">Na poniższej ilustracji przedstawiono relacje między geometrii testu trafienia (niebieskie koło) a renderowanej zawartości obiektu visual docelowego (czerwonego kwadratu).</span><span class="sxs-lookup"><span data-stu-id="c9c60-108">The following illustration shows the relationship between the hit test geometry (the blue circle) and the rendered content of the target visual object (the red square).</span></span>  
  
 <span data-ttu-id="c9c60-109">![Testowanie trafień Diagram właściwości IntersectionDetail użytej w](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span><span class="sxs-lookup"><span data-stu-id="c9c60-109">![Diagram of IntersectionDetail used in hit testing](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")</span></span>  
<span data-ttu-id="c9c60-110">Przecięcia testu trafienia geometrii i obiekt docelowy obiekt wizualny</span><span class="sxs-lookup"><span data-stu-id="c9c60-110">Intersection between hit test geometry and target visual object</span></span>  
  
 <span data-ttu-id="c9c60-111">Poniższy przykład przedstawia sposób wykonania testu trafienia wywołanie zwrotne po <xref:System.Windows.Media.Geometry> jest używany jako parametr testu trafienia.</span><span class="sxs-lookup"><span data-stu-id="c9c60-111">The following example shows how to implement a hit test callback when a <xref:System.Windows.Media.Geometry> is used as a hit test parameter.</span></span> <span data-ttu-id="c9c60-112">`result` Parametru jest rzutowane na <xref:System.Windows.Media.GeometryHitTestResult> Aby pobrać wartość <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c9c60-112">The `result` parameter is cast to a <xref:System.Windows.Media.GeometryHitTestResult> in order to retrieve the value of the <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> property.</span></span> <span data-ttu-id="c9c60-113">Wartość właściwości pozwala określić, czy <xref:System.Windows.Media.Geometry> parametru testu trafienia pełni lub częściowo zawarty w renderowanej zawartości elementu docelowego testu trafienia.</span><span class="sxs-lookup"><span data-stu-id="c9c60-113">The property value allows you to determine if the <xref:System.Windows.Media.Geometry> hit test parameter is fully or partially contained within the rendered content of the hit test target.</span></span> <span data-ttu-id="c9c60-114">W takim przypadku przykładowy kod jest tylko dodawanie wyników testu trafienia na liście elementy wizualne znajdujące się całkowicie w obrębie granicy docelowej.</span><span class="sxs-lookup"><span data-stu-id="c9c60-114">In this case, the sample code is only adding hit test results to the list for visuals that are fully contained within the target boundary.</span></span>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <span data-ttu-id="c9c60-115"><xref:System.Windows.Media.HitTestResult> Wywołania zwrotnego nie powinna być wywoływana, gdy szczegół przecięcia <xref:System.Windows.Media.IntersectionDetail.Empty>.</span><span class="sxs-lookup"><span data-stu-id="c9c60-115">The <xref:System.Windows.Media.HitTestResult> callback should not be called when the intersection detail is <xref:System.Windows.Media.IntersectionDetail.Empty>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c60-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9c60-116">See Also</span></span>  
 [<span data-ttu-id="c9c60-117">Test trafienia w warstwie wizualizacji</span><span class="sxs-lookup"><span data-stu-id="c9c60-117">Hit Testing in the Visual Layer</span></span>](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [<span data-ttu-id="c9c60-118">Przeprowadzanie testu trafienia geometrii w wizualizacji</span><span class="sxs-lookup"><span data-stu-id="c9c60-118">Hit Test Geometry in a Visual</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
