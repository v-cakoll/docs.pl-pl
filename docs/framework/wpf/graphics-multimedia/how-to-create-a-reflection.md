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
ms.openlocfilehash: c791dbbe02faaba790c650d482db092702730fa6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560579"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="cbd07-102">Jak utworzyć odbicie</span><span class="sxs-lookup"><span data-stu-id="cbd07-102">How to: Create a Reflection</span></span>
<span data-ttu-id="cbd07-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.VisualBrush> do tworzenia odbicia.</span><span class="sxs-lookup"><span data-stu-id="cbd07-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="cbd07-104">Ponieważ <xref:System.Windows.Media.VisualBrush> można wyświetlić istniejące visual, ta funkcja umożliwia tworzenie efektów wizualnych interesujące, takie jak odbić i powiększenia.</span><span class="sxs-lookup"><span data-stu-id="cbd07-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbd07-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="cbd07-105">Example</span></span>  
 <span data-ttu-id="cbd07-106">W poniższym przykładzie użyto <xref:System.Windows.Media.VisualBrush> do tworzenia odbicia z <xref:System.Windows.Controls.Border> zawiera wiele elementów.</span><span class="sxs-lookup"><span data-stu-id="cbd07-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="cbd07-107">Na poniższej ilustracji przedstawiono dane wyjściowe, który spowoduje utworzenie w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cbd07-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="cbd07-108">![Obiekt wizualny odzwierciedlone A](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="cbd07-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="cbd07-109">Obiekt Visual odbite</span><span class="sxs-lookup"><span data-stu-id="cbd07-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="cbd07-110">Pełną przykładowej, który zawiera przykłady pokazujące powiększyć części ekranu oraz sposobu tworzenia odbicia, zobacz [próbki VisualBrush](http://go.microsoft.com/fwlink/?LinkID=160049).</span><span class="sxs-lookup"><span data-stu-id="cbd07-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd07-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cbd07-111">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="cbd07-112">Malowanie przy użyciu obrazów, rysowania i wizualizacji</span><span class="sxs-lookup"><span data-stu-id="cbd07-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
