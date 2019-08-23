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
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Instrukcje: Tworzenie niestandardowych przekształceń przy użyciu elementu MatrixTransform
Ten przykład pokazuje, jak użyć <xref:System.Windows.Media.MatrixTransform> do przetłumaczenia (przenoszenia) położenia, rozciągnięcia i pochylenia. <xref:System.Windows.Controls.Button>  
  
> [!NOTE]
> <xref:System.Windows.Media.RotateTransform> <xref:System.Windows.Media.SkewTransform> <xref:System.Windows.Media.ScaleTransform>Użyj klasy, aby utworzyć niestandardowe przekształcenia, które nie są dostarczane przez klasy,, lub <xref:System.Windows.Media.TranslateTransform>. <xref:System.Windows.Media.MatrixTransform>  
  
## <a name="example"></a>Przykład  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Przekształcenia — przegląd](transforms-overview.md)
- [Tematy z instrukcjami](transformations-how-to-topics.md)
- [Kształty i podstawowe rysowanie w programie WPF — przegląd](shapes-and-basic-drawing-in-wpf-overview.md)
