---
title: 'Instrukcje: Animuj położenie i kolor zatrzymania gradientu'
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
ms.openlocfilehash: 6d8c1bb5cd133b2ee9d50a7e851d2ca3b4fff023
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368889"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Instrukcje: Animuj położenie i kolor zatrzymania gradientu
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.GradientStop.Color%2A> i <xref:System.Windows.Media.GradientStop.Offset%2A> z <xref:System.Windows.Media.GradientStop> obiektów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład animuje trzy ograniczniki gradientu wewnątrz <xref:System.Windows.Media.LinearGradientBrush>. W przykładzie zastosowano trzy animacji, z których każdy animuje różnych gradientu:  
  
-   Pierwszy animacji <xref:System.Windows.Media.Animation.DoubleAnimation>, animuje pierwszy zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Offset%2A> od 0,0 do 1,0, a następnie ponownie 0,0. Dlatego pierwszy kolor w gradientu przesunięcia od lewej do prawej krawędzi prostokąta, a następnie ponownie po lewej stronie.  
  
-   Drugiej animacji <xref:System.Windows.Media.Animation.ColorAnimation>, animuje drugi zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> z <xref:System.Windows.Media.Colors.Purple%2A> do <xref:System.Windows.Media.Colors.Yellow%2A> , a następnie ponownie do <xref:System.Windows.Media.Colors.Purple%2A>. W rezultacie kolor środkowy gradientu zmieni się z purpurowy żółty i ponownie purpurowy.  
  
-   Trzeci animacji innego <xref:System.Windows.Media.Animation.ColorAnimation>, animuje nieprzezroczystość trzeci zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> przez -1, a następnie ponownie. W rezultacie trzeci kolor gradientu zacieniony i następnie ponownie staje się nieprzezroczyste.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Mimo że w tym przykładzie użyto <xref:System.Windows.Media.LinearGradientBrush>, proces jest taki sam dla animowanie <xref:System.Windows.Media.GradientStop> obiektów wewnątrz <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Aby uzyskać więcej przykładów, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973).  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.GradientStop>
- [Animacja — przegląd](animation-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
