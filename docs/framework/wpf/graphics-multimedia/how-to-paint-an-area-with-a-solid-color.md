---
title: Jak malować obszar jednolitym kolorem
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: 017c685139979ec3aa411be6e6b5fdf0e91657de
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075551"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Jak malować obszar jednolitym kolorem
Maluj obszar jednolitym kolorem, umożliwia wstępnie zdefiniowanego pędzla, takich jak <xref:System.Windows.Media.Brushes.Red%2A> lub <xref:System.Windows.Media.Brushes.Blue%2A>, lub można utworzyć nowy <xref:System.Windows.Media.SolidColorBrush> i opisano jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> przy użyciu wartości alfa, czerwony, zielony i niebieski. W XAML mogą również Maluj obszar jednolitym kolorem przy użyciu notacji szesnastkowego.  
  
 W poniższym przykładzie użyto każdego z tych metod do malowania <xref:System.Windows.Shapes.Rectangle> niebieski.  
  
## <a name="example"></a>Przykład  
 **Przy użyciu wstępnie zdefiniowanych pędzla**  
  
 W poniższym przykładzie używa wstępnie zdefiniowanych pędzla <xref:System.Windows.Media.Brushes.Blue%2A> namalować niebieski prostokąt.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Przy użyciu notacji szesnastkowej**  
  
 W następnym przykładzie użyto 8-cyfrowej notacji szesnastkowej namalować niebieski prostokąt.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Przy użyciu wartości ARGB**  
  
 Następny przykład tworzy <xref:System.Windows.Media.SolidColorBrush> i opisano jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> przy użyciu ARGB wartości kolor niebieski.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Aby uzyskać inne sposoby opisujący kolor, zobacz <xref:System.Windows.Media.Color> struktury.  
  
 **Tematy pokrewne**  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.SolidColorBrush> i dodatkowe przykłady, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) Przegląd.  
  
 Ten przykład kodu jest częścią większego przykładu przewidzianego dla <xref:System.Windows.Media.SolidColorBrush> klasy. Aby uzyskać pełny przykład, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Brushes>
