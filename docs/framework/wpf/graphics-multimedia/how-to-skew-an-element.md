---
title: Jak pochylić element
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: f828e4d4e59fa5ed31f81f3e83570a25add19e01
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43877083"
---
# <a name="how-to-skew-an-element"></a>Jak pochylić element
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.SkewTransform> do Pochyl element. Przesunięcia czasowego, który jest znany także jako Pochyl, to przekształcenie, które rozciąga przestrzeni współrzędnych w sposób obsługuje technologię niejednolitego. Jednym z zastosowań typowe <xref:System.Windows.Media.SkewTransform> jest symulowania [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] głębokość w [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] obiektów.  
  
 Użyj <xref:System.Windows.Media.SkewTransform.CenterX%2A> i <xref:System.Windows.Media.SkewTransform.CenterY%2A> punkt właściwości, aby określić Centrum <xref:System.Windows.Media.SkewTransform>.  
  
 Użyj <xref:System.Windows.Media.SkewTransform.AngleX%2A> i <xref:System.Windows.Media.SkewTransform.AngleY%2A> właściwości do określenia kąta pochylenie w osi x i y oraz pochylanie bieżący układ współrzędnych wzdłuż tych osi.  
  
 Do przewidywania wpływu transformację pochylenia, rozważ <xref:System.Windows.Media.SkewTransform.AngleX%2A> pochyla wartości osi x, względem oryginalnego współrzędnych. W związku z tym, aby uzyskać <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, oś y obraca się 30 stopni za pośrednictwem źródła i pochyla wartości x — 30 stopni z tego źródła. Podobnie <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 pochyla wartości y kształtu o 30 stopni ze źródła. Należy pamiętać, że nie jest taki sam skutek jak tłumaczenia (przenoszenie) współrzędnych przez 30 stopni w x i y.  
  
 Następujący przykład dotyczy poziomej przesunięcia czasowego 45 stopni na <xref:System.Windows.Shapes.Rectangle> z punktu centralnego (0,0).  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Następujący przykład dotyczy poziomej przesunięcia czasowego 45 stopni na <xref:System.Windows.Shapes.Rectangle> z punktu centralnego (25,25).  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Następujący przykład dotyczy pionowej przesunięcia czasowego 45 stopni na <xref:System.Windows.Shapes.Rectangle> z punktu centralnego (25,25).  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Poniższa ilustracja przedstawia różne niesymetryczności, które są używane w tym przykładzie.  
  
 ![SkewTransform — przykłady](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Przedstawione trzy przykłady SkewTransform —  
  
 Aby uzyskać pełny przykład, zobacz [przykładowych przekształceń 2-D](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
