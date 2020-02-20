---
title: Jak malować obszar gradientem liniowym
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 76c491632911c48db34d932ba3895278591378a5
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452769"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Jak malować obszar gradientem liniowym
Ten przykład pokazuje, jak używać klasy <xref:System.Windows.Media.LinearGradientBrush> do malowania obszaru gradientem liniowym. W poniższym przykładzie <xref:System.Windows.Shapes.Shape.Fill%2A>a <xref:System.Windows.Shapes.Rectangle> jest malowana ukośnym gradientem liniowym, który przechodzi z żółtej do czerwonego do zielonego koloru wapna.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.  
  
 ![Gradient liniowy ukośny](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Aby utworzyć poziomy gradient liniowy, Zmień <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> na (0, 0,5) i (1, 0,5). W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest rysowane z poziomym gradientem liniowym.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.  
  
 ![Poziomy gradient liniowy](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Aby utworzyć pionowy gradient liniowy, Zmień <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> na (0,5, 0) i (0,5, 1). W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest rysowane z pionowym gradientem liniowym.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.  
  
 ![Gradient liniowy pionowy](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
> Przykłady w tym temacie używają domyślnego układu współrzędnych do ustawiania punktów początkowych i punktów końcowych. Domyślny system współrzędnych jest względny w stosunku do pola ograniczenia: 0 wskazuje 0 procent obwiedni, a 1 wskazuje 100 procent obwiedni. Można zmienić ten system współrzędnych, ustawiając właściwość <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>wartość. Bezwzględny układ współrzędnych nie należy do obwiedni. Wartości są interpretowane bezpośrednio w miejscu lokalnym.  
  
 Aby uzyskać więcej przykładów, zobacz [przykłady pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Aby uzyskać więcej informacji o gradientach i innych typach pędzli, zobacz [malowanie przy użyciu pełnych kolorów i gradientów przegląd](painting-with-solid-colors-and-gradients-overview.md).
