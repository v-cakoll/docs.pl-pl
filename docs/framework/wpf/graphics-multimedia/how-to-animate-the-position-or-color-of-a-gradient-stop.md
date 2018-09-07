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
ms.openlocfilehash: fcbb546b64810416d3f7dbe052da77b7bc941e7a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083988"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Jak animować położenie i kolor zatrzymania gradientu
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.GradientStop.Color%2A> i <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład animuje trzy ograniczniki gradientu wewnątrz <xref:System.Windows.Media.LinearGradientBrush>. W przykładzie zastosowano trzy animacji, z których każdy animuje różnych gradientu:  
  
-   Pierwszy animacji <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje pierwszy zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Offset%2A> od 0,0 do 1,0, a następnie ponownie 0,0. Dlatego pierwszy kolor w gradientu przesunięcia od lewej do prawej krawędzi prostokąta, a następnie ponownie po lewej stronie.  
  
-   Drugiej animacji <xref:System.Windows.Media.Animation.ColorAnimation>, animuje drugi zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> do <xref:System.Windows.Media.Colors.Yellow%2A> , a następnie ponownie do <xref:System.Windows.Media.Colors.Purple%2A>. W rezultacie kolor środkowy gradientu zmieni się z purpurowy żółty i ponownie purpurowy.  
  
-   Trzeci animacji innego <xref:System.Windows.Media.Animation.ColorAnimation>, animuje nieprzezroczystość trzeci zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> przez -1, a następnie ponownie. W rezultacie trzeci kolor gradientu zacieniony i następnie ponownie staje się nieprzezroczyste.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Media.LinearGradientBrush>, proces jest taki sam dla animowanie <xref:System.Windows.Media.GradientStop> obiektów wewnątrz <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Aby uzyskać więcej przykładów, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.GradientStop>  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Scenorysy — przegląd](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
