---
title: 'Instrukcje: Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 1971d5fe9422c5138f140517e6fd4c9f9b2cf48b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913918"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="e8bd2-102">Instrukcje: Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform</span><span class="sxs-lookup"><span data-stu-id="e8bd2-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="e8bd2-103">Ten przykład pokazuje, jak użyć <xref:System.Windows.Media.MatrixTransform> do przetłumaczenia (przenoszenia) położenia, rozciągnięcia i pochylenia. <xref:System.Windows.Controls.Button></span><span class="sxs-lookup"><span data-stu-id="e8bd2-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8bd2-104"><xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.SkewTransform> <xref:System.Windows.Media.ScaleTransform>Użyj klasy, aby utworzyć niestandardowe przekształcenia, które nie są dostarczane przez klasy,, lub <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.MatrixTransform></span><span class="sxs-lookup"><span data-stu-id="e8bd2-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8bd2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8bd2-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="e8bd2-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8bd2-106">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="e8bd2-107">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="e8bd2-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="e8bd2-108">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="e8bd2-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="e8bd2-109">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="e8bd2-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
