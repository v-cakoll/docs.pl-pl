---
title: 'Instrukcje: Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: aeccb961db539d4cc6dea75fb487fba06e59d6de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182315"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Instrukcje: Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.MatrixTransform> do tłumaczenia (przenoszenie) pozycji, Stretch Database i pochylanie elementu <xref:System.Windows.Controls.Button>.  
  
> [!NOTE]
>  Użyj <xref:System.Windows.Media.MatrixTransform> klasy w celu utworzenia niestandardowych przekształceń, które nie są dostarczane przez <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, lub <xref:System.Windows.Media.TranslateTransform> klasy.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Przegląd Przekształcenia](transforms-overview.md)
- [— Tematy porad](transformations-how-to-topics.md)
- [Przegląd Kształty i podstawowe rysowanie w WPF](shapes-and-basic-drawing-in-wpf-overview.md)
