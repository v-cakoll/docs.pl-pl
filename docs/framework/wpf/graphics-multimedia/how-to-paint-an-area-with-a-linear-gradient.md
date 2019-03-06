---
title: 'Instrukcje: Maluj obszar gradientem liniowym'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: c48ff13811d784ecc7042b73b964a9e6f2d42a34
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367248"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Instrukcje: Maluj obszar gradientem liniowym
W tym przykładzie pokazano, jak używać <xref:System.Windows.Media.LinearGradientBrush> klasy Maluj obszar gradientem liniowym. W poniższym przykładzie <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> jest malowany przechodzi z żółtym kolor czerwony, niebieski do Limonowozielony Ukośny gradient liniowy.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Poniższa ilustracja przedstawia gradientu utworzony w poprzednim przykładzie.  
  
 ![Po przekątnej gradientu liniowego](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Aby utworzyć poziomego gradientu liniowego, zmienić <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> do (0,0.5) i (1,0.5). W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany poziomego gradientu liniowego.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Poniższa ilustracja przedstawia gradientu utworzony w poprzednim przykładzie.  
  
 ![Poziomy gradient liniowy](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Aby utworzyć pionowe gradientu liniowego, zmienić <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> do (0.5,0) i (0.5,1). W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowane pionowy gradientem liniowym.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Poniższa ilustracja przedstawia gradientu utworzony w poprzednim przykładzie.  
  
 ![Gradient liniowy pionowy](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  Przykłady w tym temacie na użytek w układzie współrzędnych domyślne ustawienie punktach i punktów końcowych. System współrzędnych domyślne są określane względem obwiedni: 0 oznacza wartość 0 procent obwiedni, a wartość 1 oznacza 100 procent obwiedni. Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> właściwości na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>. Bezwzględnych współrzędnych jest względem obwiedni. Wartości są interpretowane bezpośrednio w przestrzeni lokalnej.  
  
 Aby uzyskać więcej przykładów, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji na temat gradientów oraz inne rodzaje pędzle, zobacz [malowanie jednolitymi kolorami i gradientami — Przegląd](painting-with-solid-colors-and-gradients-overview.md).
