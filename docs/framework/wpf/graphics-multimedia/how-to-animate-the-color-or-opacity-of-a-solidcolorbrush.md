---
title: 'Instrukcje: Animowanie koloru lub nieprzezroczystości elementu SolidColorBrush'
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 610a7c4879b4ffe54940e8bc744dcca0711e84d2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593397"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Instrukcje: Animowanie koloru lub nieprzezroczystości elementu SolidColorBrush
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto trzy animacji, aby animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.SolidColorBrush>.  
  
- Pierwszy animacji <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla do <xref:System.Windows.Media.Colors.Gray%2A> gdy wskaźnik myszy zostanie przesunięty prostokąta.  
  
- Dalej animacji innego <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla do <xref:System.Windows.Media.Colors.Orange%2A> gdy wskaźnik myszy opuszcza prostokąta.  
  
- Końcowe animacji <xref:System.Windows.Media.Animation.DoubleAnimation>, zmienia przezroczystość pędzla 0,0 po naciśnięciu lewego przycisku myszy.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Aby uzyskać pełniejszy przykład pokazuje, jak animować różnego rodzaju pędzle, zobacz [przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973). Aby uzyskać więcej informacji na temat animacji, zobacz [Przegląd animacja](animation-overview.md).  
  
 Aby zachować spójność z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt, do ich animacji. Jednak podczas stosowania pojedynczej animacji w kodzie, jest łatwiejszy w obsłudze <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>. Aby uzyskać przykład, zobacz [animować właściwości bez użycia scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz także

- [Animacja — przegląd](animation-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
- [Przykład pędzle](https://go.microsoft.com/fwlink/?LinkID=159973)
