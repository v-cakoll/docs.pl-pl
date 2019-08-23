---
title: 'Instrukcje: Malowanie obszaru gradientem liniowym'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: 92c9ccd846dbbce043d13e6ba82b9fa8e72fa8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916164"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Instrukcje: Malowanie obszaru gradientem liniowym
Ten przykład pokazuje, <xref:System.Windows.Media.LinearGradientBrush> jak używać klasy do malowania obszaru gradientem liniowym. W poniższym przykładzie <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Rectangle> kolor jest malowany ukośnym gradientem liniowym, który przechodzi z żółtego do czerwonego do zielonego na zielony.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.  
  
 ![Gradient liniowy ukośny](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Aby utworzyć poziomy gradient liniowy, Zmień wartości <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> z do (0, 0,5) i (1, 0,5). W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany poziom gradientu liniowego.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.  
  
 ![Poziomy gradient liniowy](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Aby utworzyć pionowy gradient liniowy, Zmień <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> wartości <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush> do (0,5, 0) i (0,5, 1). W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany pionowym gradientem liniowym.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono gradient utworzony w poprzednim przykładzie.  
  
 ![Gradient liniowy pionowy](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
> Przykłady w tym temacie używają domyślnego układu współrzędnych do ustawiania punktów początkowych i punktów końcowych. Domyślny system współrzędnych jest względny w stosunku do pola ograniczenia: wartość 0 oznacza 0 procent obwiedni, a 1 wskazuje 100 procent obwiedni. Można zmienić ten system współrzędnych przez ustawienie <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość. <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType> Bezwzględny układ współrzędnych nie należy do obwiedni. Wartości są interpretowane bezpośrednio w miejscu lokalnym.  
  
 Aby uzyskać więcej przykładów, zobacz [przykłady pędzli](https://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji o gradientach i innych typach pędzli, zobacz [malowanie przy użyciu pełnych kolorów i gradientów przegląd](painting-with-solid-colors-and-gradients-overview.md).
