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
ms.openlocfilehash: aeae33f5f3c8016808988f58d61969e9b6f05039
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452847"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>Jak animować położenie i kolor zatrzymania gradientu
Ten przykład pokazuje, jak animować <xref:System.Windows.Media.GradientStop.Color%2A> i <xref:System.Windows.Media.GradientStop.Offset%2A> obiektów <xref:System.Windows.Media.GradientStop>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umożliwia animowanie trzech zatrzymań gradientów wewnątrz <xref:System.Windows.Media.LinearGradientBrush>. W przykładzie są stosowane trzy animacje, z których każdy jest animowany w innym stopniu gradientu:  
  
- Pierwsza animacja, <xref:System.Windows.Media.Animation.DoubleAnimation>, Animuj pierwszy <xref:System.Windows.Media.GradientStop.Offset%2A> stopu gradientu od 0,0 do 1,0, a następnie z powrotem do 0,0. W efekcie pierwszy kolor w gradiencie zostanie przesunięty z lewej strony do prawej krawędzi prostokąta, a następnie z powrotem do lewej strony.  
  
- Druga animacja, <xref:System.Windows.Media.Animation.ColorAnimation>, Animuj <xref:System.Windows.Media.GradientStop.Color%2A> drugiego zatrzymania gradientu z <xref:System.Windows.Media.Colors.Purple%2A> do <xref:System.Windows.Media.Colors.Yellow%2A>, a następnie z powrotem do <xref:System.Windows.Media.Colors.Purple%2A>. W efekcie kolor środkowy w gradiencie zmieni się z purpurowy na żółty i z powrotem na purpurowy.  
  
- Trzecia animacja, inna <xref:System.Windows.Media.Animation.ColorAnimation>, Animuj nieprzezroczystość trzeciego zatrzymania gradientu <xref:System.Windows.Media.GradientStop.Color%2A> o-1, a następnie z powrotem. W efekcie trzeci kolor w gradiencie znika, a następnie zmienia się nieprzezroczystie.  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 Chociaż w tym przykładzie używa <xref:System.Windows.Media.LinearGradientBrush>, proces jest taki sam dla animacji obiektów <xref:System.Windows.Media.GradientStop> w <xref:System.Windows.Media.RadialGradientBrush>.  
  
 Aby uzyskać więcej przykładów, zobacz [przykład pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Media.GradientStop>
- [Animacja — przegląd](animation-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
