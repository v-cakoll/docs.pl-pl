---
title: "Jak użyć MatrixTransform do utworzenia niestandardowych przekształceń"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1414ae590be10c3adcc6857492e23bf659beec67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="7b523-102">Jak użyć MatrixTransform do utworzenia niestandardowych przekształceń</span><span class="sxs-lookup"><span data-stu-id="7b523-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="7b523-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.MatrixTransform> do tłumaczenia (przenoszenia) pozycji, rozciąganie i pochylanie z <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="7b523-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b523-104">Użyj <xref:System.Windows.Media.MatrixTransform> klasy w celu utworzenia niestandardowych przekształceń, które nie są dostarczane przez <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, lub <xref:System.Windows.Media.TranslateTransform> klasy.</span><span class="sxs-lookup"><span data-stu-id="7b523-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b523-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b523-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="7b523-106">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7b523-106">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="7b523-107">Przekształcenia — przegląd</span><span class="sxs-lookup"><span data-stu-id="7b523-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="7b523-108">Tematy z instrukcjami</span><span class="sxs-lookup"><span data-stu-id="7b523-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="7b523-109">Kształty i podstawowe rysowanie w programie WPF — przegląd</span><span class="sxs-lookup"><span data-stu-id="7b523-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
