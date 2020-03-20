---
title: Jak malować obszar jednolitym kolorem
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849525"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Jak malować obszar jednolitym kolorem
Aby pomalować obszar jednolitym kolorem, można użyć wstępnie zdefiniowanego <xref:System.Windows.Media.Brushes.Blue%2A>pędzla systemowego, <xref:System.Windows.Media.SolidColorBrush> takiego <xref:System.Windows.Media.SolidColorBrush.Color%2A> jak <xref:System.Windows.Media.Brushes.Red%2A> lub , lub utworzyć nowy i opisać jego użycie przy użyciu wartości alfa, czerwonej, zielonej i niebieskiej. W języku XAML można również malować obszar o jednolitym kolorze za pomocą notacji szesnastkowej.  
  
 Poniższe przykłady używa każdej z tych <xref:System.Windows.Shapes.Rectangle> technik do malowania niebieski.  
  
## <a name="example"></a>Przykład  
 **Korzystanie ze wstępnie zdefiniowanego pędzla**  
  
 W poniższym przykładzie użyto wstępnie <xref:System.Windows.Media.Brushes.Blue%2A> zdefiniowanego pędzla do malowania prostokąta na niebiesko.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Korzystanie z notacji szesnastkowej**  
  
 W następnym przykładzie użyto 8-cyfrowego notacji szesnastkowe do malowania prostokąta na niebiesko.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Korzystanie z wartości ARGB**  
  
 Następny przykład tworzy <xref:System.Windows.Media.SolidColorBrush> i <xref:System.Windows.Media.SolidColorBrush.Color%2A> opisuje jego przy użyciu argb wartości dla koloru niebieskiego.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Aby uzyskać inne sposoby opisywania koloru, zobacz strukturę. <xref:System.Windows.Media.Color>  
  
 **Tematy pokrewne**  
  
 Aby uzyskać <xref:System.Windows.Media.SolidColorBrush> więcej informacji na temat i dodatkowych przykładów, zobacz [Omówienie malowania z jednolitymi kolorami i gradientami.](painting-with-solid-colors-and-gradients-overview.md)  
  
 W tym przykładzie kodu jest częścią <xref:System.Windows.Media.SolidColorBrush> większego przykładu przewidzianego dla klasy. Aby uzyskać pełną próbkę, zobacz [Próbka pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.Brushes>
