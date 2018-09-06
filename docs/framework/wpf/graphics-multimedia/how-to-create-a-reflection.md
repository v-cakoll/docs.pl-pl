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
ms.openlocfilehash: 716adff5c5c41e6601e384b6669516cb6ba1041d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777798"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="c985f-102">Jak utworzyć odbicie</span><span class="sxs-lookup"><span data-stu-id="c985f-102">How to: Create a Reflection</span></span>
<span data-ttu-id="c985f-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.VisualBrush> utworzyć odbicie.</span><span class="sxs-lookup"><span data-stu-id="c985f-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="c985f-104">Ponieważ <xref:System.Windows.Media.VisualBrush> można wyświetlić istniejącej wizualizacji, ta funkcja umożliwia tworzenie efektów wizualnych interesujące, takie jak odbić i powiększenia.</span><span class="sxs-lookup"><span data-stu-id="c985f-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c985f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c985f-105">Example</span></span>  
 <span data-ttu-id="c985f-106">W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> do tworzenie odbicia <xref:System.Windows.Controls.Border> zawiera wiele elementów.</span><span class="sxs-lookup"><span data-stu-id="c985f-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="c985f-107">Poniższa ilustracja przedstawia ten przykład generuje dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c985f-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="c985f-108">![A odzwierciedlone obiekt wizualny](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="c985f-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="c985f-109">Odbitych obiekt wizualny</span><span class="sxs-lookup"><span data-stu-id="c985f-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="c985f-110">Aby uzyskać pełny przykład, który zawiera przykłady pokazujące, jak części ekranu, powiększanie i Tworzenie odbić, zobacz [przykładowe VisualBrush](https://go.microsoft.com/fwlink/?LinkID=160049).</span><span class="sxs-lookup"><span data-stu-id="c985f-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c985f-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c985f-111">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="c985f-112">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="c985f-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
