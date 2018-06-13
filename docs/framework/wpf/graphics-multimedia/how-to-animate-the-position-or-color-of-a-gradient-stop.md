---
title: Jak animować położenie i kolor zatrzymania gradientu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: 2eb528127c8aa66976788ec1f4e5362ca3a1ef26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558671"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Jak animować położenie i kolor zatrzymania gradientu
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.GradientStop.Color%2A> i <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład animuje trzy gradientu wewnątrz <xref:System.Windows.Media.LinearGradientBrush>. W przykładzie użyto animacje trzy, z których każdy animuje różnych gradientu:  
  
-   Pierwszy animacji <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje pierwszy ograniczniku gradientu <xref:System.Windows.Media.GradientStop.Offset%2A> od 0,0 do 1,0, a następnie z powrotem do 0,0. W związku z tym pierwszy kolorów w gradientu przesunięcia od lewej do prawej krawędzi prostokąta, a następnie z powrotem do lewej.  
  
-   Drugi animacji <xref:System.Windows.Media.Animation.ColorAnimation>, animuje drugi ograniczniku gradientu <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> do <xref:System.Windows.Media.Colors.Yellow%2A> , a następnie z powrotem do <xref:System.Windows.Media.Colors.Purple%2A>. W związku z tym Środkowy kolor gradientu zmienia purpurowy żółty i z powrotem na fioletowo.  
  
-   Trzeci animacji innego <xref:System.Windows.Media.Animation.ColorAnimation>, animuje przezroczystość trzeci ograniczniku gradientu <xref:System.Windows.Media.GradientStop.Color%2A> przez wartość -1, a następnie ponownie. W związku z tym trzeci kolor gradientu zniknie i następnie ponownie staje się przezroczystości.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Media.LinearGradientBrush>, proces jest taki sam dla animacji <xref:System.Windows.Media.GradientStop> obiektów wewnątrz <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Aby uzyskać dodatkowe przykłady, zobacz [przykład pędzle](http://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.GradientStop>  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
