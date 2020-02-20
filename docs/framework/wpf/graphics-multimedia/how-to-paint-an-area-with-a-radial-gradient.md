---
title: Jak malować obszar gradientem promieniowym
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 8a53d5d7247f82905816265f7c92b22f287591c5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452756"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="feca5-102">Jak malować obszar gradientem promieniowym</span><span class="sxs-lookup"><span data-stu-id="feca5-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="feca5-103">Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.RadialGradientBrush> do malowania obszaru z gradientem promieniowym.</span><span class="sxs-lookup"><span data-stu-id="feca5-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feca5-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="feca5-104">Example</span></span>  
 <span data-ttu-id="feca5-105">Poniższy przykład używa <xref:System.Windows.Media.RadialGradientBrush>, aby malować prostokąt z gradientem promieniowym, który przechodzi z żółtego do czerwonego do zielonego koloru wapna.</span><span class="sxs-lookup"><span data-stu-id="feca5-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="feca5-106">Na poniższej ilustracji przedstawiono gradient z poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="feca5-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="feca5-107">Ogranicznik gradientu został wyróżniony.</span><span class="sxs-lookup"><span data-stu-id="feca5-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="feca5-108">![Gradienty zatrzymane w gradiencie promieniowym](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="feca5-108">![Gradient stops in a radial gradient](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="feca5-109">W przykładach w tym temacie użyto domyślnego układu współrzędnych do ustawiania punktów kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="feca5-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="feca5-110">Domyślny system współrzędnych jest względny w stosunku do pola ograniczenia: 0 wskazuje 0 procent obwiedni, a 1 wskazuje 100 procent obwiedni.</span><span class="sxs-lookup"><span data-stu-id="feca5-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="feca5-111">Można zmienić ten system współrzędnych, ustawiając właściwość <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na <xref:System.Windows.Media.BrushMappingMode.Absolute>wartość.</span><span class="sxs-lookup"><span data-stu-id="feca5-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="feca5-112">Bezwzględny układ współrzędnych nie należy do obwiedni.</span><span class="sxs-lookup"><span data-stu-id="feca5-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="feca5-113">Wartości są interpretowane bezpośrednio w miejscu lokalnym.</span><span class="sxs-lookup"><span data-stu-id="feca5-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="feca5-114">Aby uzyskać dodatkowe przykłady <xref:System.Windows.Media.RadialGradientBrush>, zobacz [Przykładowe pędzle](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="feca5-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span> <span data-ttu-id="feca5-115">Aby uzyskać więcej informacji o gradientach i innych typach pędzli, zobacz [malowanie przy użyciu pełnych kolorów i gradientów przegląd](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="feca5-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>
