---
title: 'Instrukcje: Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: aeccb961db539d4cc6dea75fb487fba06e59d6de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769268"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="c9a1c-102">Instrukcje: Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform</span><span class="sxs-lookup"><span data-stu-id="c9a1c-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="c9a1c-103">W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.MatrixTransform> do tłumaczenia (przenoszenie) pozycji, Stretch Database i pochylanie elementu <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="c9a1c-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9a1c-104">Użyj <xref:System.Windows.Media.MatrixTransform> klasy w celu utworzenia niestandardowych przekształceń, które nie są dostarczane przez <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, lub <xref:System.Windows.Media.TranslateTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="c9a1c-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9a1c-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9a1c-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="c9a1c-106">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9a1c-106">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="c9a1c-107">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="c9a1c-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="c9a1c-108">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="c9a1c-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="c9a1c-109">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="c9a1c-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
