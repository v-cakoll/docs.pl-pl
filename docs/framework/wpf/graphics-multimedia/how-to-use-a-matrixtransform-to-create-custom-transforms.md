---
title: 'Instrukcje: Użyj MatrixTransform do utworzenia niestandardowych przekształceń'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 179c7986b6a7021f4e1245aef01eb555108ebf4f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358863"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Instrukcje: Użyj MatrixTransform do utworzenia niestandardowych przekształceń
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.MatrixTransform> do tłumaczenia (przenoszenie) pozycji, Stretch Database i pochylanie elementu <xref:System.Windows.Controls.Button>.  
  
> [!NOTE]
>  Użyj <xref:System.Windows.Media.MatrixTransform> klasy w celu utworzenia niestandardowych przekształceń, które nie są dostarczane przez <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, lub <xref:System.Windows.Media.TranslateTransform> klasy.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Przekształcenia — przegląd](transforms-overview.md)
- [Tematy z instrukcjami](transformations-how-to-topics.md)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
