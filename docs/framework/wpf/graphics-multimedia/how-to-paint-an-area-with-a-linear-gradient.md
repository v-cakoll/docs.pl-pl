---
title: "Jak malować obszar gradientem liniowym"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dcc37651d6f1f304f15d3244c2504517a2a9fb76
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>Jak malować obszar gradientem liniowym
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.LinearGradientBrush> klasy namalować obszar o gradientu liniowego. W poniższym przykładzie <xref:System.Windows.Shapes.Shape.Fill%2A> z <xref:System.Windows.Shapes.Rectangle> jest malowany przekątnej gradientu liniowego, który przejścia z żółtym na kolor czerwony, niebieski do Limonowy zielony.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie gradientu.  
  
 ![Przekątnej gradientu liniowego](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 Aby utworzyć poziomego gradientu liniowego, zmienić <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> do (0,0.5) i (1,0.5). W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany poziomego gradientu liniowego.  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie gradientu.  
  
 ![Poziomy gradient liniowy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 Aby utworzyć pionowy gradient liniowy, zmienić <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> i <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> z <xref:System.Windows.Media.LinearGradientBrush> do (0.5,0) i (0.5,1). W poniższym przykładzie <xref:System.Windows.Shapes.Rectangle> jest malowany pionowy gradientu liniowego.  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie gradientu.  
  
 ![Gradient liniowy pionowy](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  Przykłady w tym temacie Korzystanie z systemu współrzędnych domyślne ustawienie punkty początkowy i końcowy. System współrzędnych domyślna jest określana względem obwiedni: 0 wskazuje 0 procent obwiedni, a wartość 1 oznacza 100 procent obwiedni. Ten układ współrzędnych można zmienić, określając <xref:System.Windows.Media.GradientBrush.MappingMode%2A> na wartość <xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>. Bezwzględny układ współrzędnych nie jest określana względem obwiedni. Wartości są interpretowane bezpośrednio w lokalnej przestrzeni.  
  
 Aby uzyskać dodatkowe przykłady, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji na temat gradientach i innych typów pędzle zobacz [Malowanie z kolorami i przegląd gradienty](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
