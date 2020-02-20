---
title: Jak utworzyć odbicie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 8a5ed345c0aa25312bd74799264e1f66ab4554e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452061"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="3969c-102">Jak utworzyć odbicie</span><span class="sxs-lookup"><span data-stu-id="3969c-102">How to: Create a Reflection</span></span>
<span data-ttu-id="3969c-103">Ten przykład pokazuje, jak używać <xref:System.Windows.Media.VisualBrush> do tworzenia odbicia.</span><span class="sxs-lookup"><span data-stu-id="3969c-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="3969c-104">Ponieważ <xref:System.Windows.Media.VisualBrush> można wyświetlić istniejącej wizualizacji, można użyć tej funkcji do tworzenia interesujących efektów wizualnych, takich jak odbicie i powiększenia.</span><span class="sxs-lookup"><span data-stu-id="3969c-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3969c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="3969c-105">Example</span></span>  
 <span data-ttu-id="3969c-106">Poniższy przykład używa <xref:System.Windows.Media.VisualBrush>, aby utworzyć odbicie <xref:System.Windows.Controls.Border> zawierającej kilka elementów.</span><span class="sxs-lookup"><span data-stu-id="3969c-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="3969c-107">Na poniższej ilustracji przedstawiono dane wyjściowe generowane przez ten przykład.</span><span class="sxs-lookup"><span data-stu-id="3969c-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="3969c-108">![Odbicie odbitego obiektu wizualnego](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="3969c-108">![A reflected Visual object](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="3969c-109">Odbicie odbitego obiektu wizualnego</span><span class="sxs-lookup"><span data-stu-id="3969c-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="3969c-110">Aby uzyskać kompletny przykład, w tym przykłady pokazujące sposób powiększania części ekranu i sposobu tworzenia odbicia, zobacz [przykład VisualBrush](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span><span class="sxs-lookup"><span data-stu-id="3969c-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3969c-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3969c-111">See also</span></span>

- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="3969c-112">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="3969c-112">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
