---
title: Jak pochylić element
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 8bd860a71253a55cb3148426dbb61cbd3477e95e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561566"
---
# <a name="how-to-skew-an-element"></a>Jak pochylić element
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.SkewTransform> fałszować elementu. Zegara, który jest również nazywany Ścinanie, jest transformację w sposób niejednolitego rozciąga się przestrzeni współrzędnych. Jeden typowy sposób użycia protokołu <xref:System.Windows.Media.SkewTransform> jest symulowanie [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] głębokość [!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)] obiektów.  
  
 Użyj <xref:System.Windows.Media.SkewTransform.CenterX%2A> i <xref:System.Windows.Media.SkewTransform.CenterY%2A> punkt właściwości, aby określić Centrum <xref:System.Windows.Media.SkewTransform>.  
  
 Użyj <xref:System.Windows.Media.SkewTransform.AngleX%2A> i <xref:System.Windows.Media.SkewTransform.AngleY%2A> właściwości do określenia kąta pochylenia osi x i y i pochylanie bieżący układ współrzędnych wzdłuż osi te.  
  
 Przewidywanie efekt transformację pochylenia, rozważ <xref:System.Windows.Media.SkewTransform.AngleX%2A> pochyla wartości na osi x względem oryginalnego układ współrzędnych. W związku z tym dla <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30, oś y obraca 30 stopni za pośrednictwem źródła i pochyla wartości x-o 30 stopni z tego źródła. Podobnie <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 pochyla wartości y kształtu przez 30 stopni ze źródła. Należy pamiętać, że nie jest to ten sam efekt co tłumaczenia (przenoszenia) współrzędnych przez 30 stopni w x i y.  
  
 Poniższy przykład dotyczy pochylenie w poziomie 45 stopni do <xref:System.Windows.Shapes.Rectangle> od środka (0,0).  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformsSample#41](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 Poniższy przykład dotyczy pochylenie w poziomie 45 stopni do <xref:System.Windows.Shapes.Rectangle> od punktu center (25,25).  
  
 [!code-xaml[transformsSample#42](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 Poniższy przykład dotyczy pochylenie w pionie 45 stopni do <xref:System.Windows.Shapes.Rectangle> od punktu center (25,25).  
  
 [!code-xaml[transformsSample#43](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 Na poniższej ilustracji przedstawiono różne pochyla, które są używane w tym przykładzie.  
  
 ![Przykłady obiektu SkewTransform](../../../../docs/framework/wpf/graphics-multimedia/media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
Trzy przedstawione przykłady obiektu SkewTransform  
  
 Pełny przykład, zobacz [2-D transformacje próbki](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.SkewTransform>  
 [Przekształcenia — przegląd](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
