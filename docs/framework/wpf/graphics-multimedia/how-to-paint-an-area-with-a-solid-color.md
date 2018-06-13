---
title: Jak malować obszar jednolitym kolorem
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: 7e8e3fa5a379f02c3bb126c17bbe37fc0f3d57cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561335"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>Jak malować obszar jednolitym kolorem
Namalować obszar jednolitym kolorem służy pędzel wstępnie zdefiniowanych systemu, takich jak <xref:System.Windows.Media.Brushes.Red%2A> lub <xref:System.Windows.Media.Brushes.Blue%2A>, lub można utworzyć nowy <xref:System.Windows.Media.SolidColorBrush> i opisz jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> przy użyciu wartości alfa, czerwony, zielony i niebieski. W języku XAML może również malowanie obszar jednolitym kolorem przy użyciu notacji szesnastkową.  
  
 W poniższym przykładzie użyto każdego z tych metod do malowania <xref:System.Windows.Shapes.Rectangle> niebieski.  
  
## <a name="example"></a>Przykład  
 **Używanie pędzla wstępnie zdefiniowane**  
  
 W poniższym przykładzie używa wstępnie zdefiniowanych pędzla <xref:System.Windows.Media.Brushes.Blue%2A> namalować niebieski prostokąta.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **Przy użyciu notacji szesnastkowej**  
  
 W następnym przykładzie użyto szesnastkowym 8-cyfrowy namalować niebieski prostokąta.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **Przy użyciu wartości ARGB**  
  
 W następnym przykładzie jest tworzony <xref:System.Windows.Media.SolidColorBrush> oraz opis jego <xref:System.Windows.Media.SolidColorBrush.Color%2A> przy użyciu ARGB wartości kolor niebieski.  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 Dla innych sposobów opisujący kolor <xref:System.Windows.Media.Color> struktury.  
  
 **Tematy pokrewne**  
  
 Aby uzyskać więcej informacji na temat <xref:System.Windows.Media.SolidColorBrush> i dodatkowe przykłady, zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) omówienie.  
  
 Ten przykładowy kod jest częścią większego przykładu udostępnionego dla <xref:System.Windows.Media.SolidColorBrush> klasy. Pełny przykład, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Brushes>
