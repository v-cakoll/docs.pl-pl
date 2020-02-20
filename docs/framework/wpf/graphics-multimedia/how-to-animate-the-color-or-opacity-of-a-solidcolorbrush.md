---
title: Jak animować kolor lub nieprzezroczystość SolidColorBrush
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 08b85935e0cb1ababd1fb63b9d02518ea3fcfa17
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452886"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>Jak animować kolor lub nieprzezroczystość SolidColorBrush
Ten przykład pokazuje, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano trzy animacje do animowania <xref:System.Windows.Media.SolidColorBrush.Color%2A> i <xref:System.Windows.Media.Brush.Opacity%2A> <xref:System.Windows.Media.SolidColorBrush>.  
  
- Pierwsza animacja, <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla na <xref:System.Windows.Media.Colors.Gray%2A>, gdy wskaźnik myszy zostanie przesunięty do prostokąta.  
  
- Kolejna animacja, inna <xref:System.Windows.Media.Animation.ColorAnimation>, zmienia kolor pędzla na <xref:System.Windows.Media.Colors.Orange%2A>, gdy wskaźnik myszy opuszcza prostokąt.  
  
- Ostatnia animacja, <xref:System.Windows.Media.Animation.DoubleAnimation>, zmienia krycie pędzla na 0,0 po naciśnięciu lewego przycisku myszy.  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 Aby zapoznać się z bardziej kompletnym przykładem, który pokazuje, jak animować różne typy pędzli, zobacz [przykład pędzli](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes). Aby uzyskać więcej informacji na temat animacji, zobacz [Omówienie animacji](animation-overview.md).  
  
 Aby zapewnić spójność z innymi przykładami animacji, wersje kodu tego przykładu używają obiektu <xref:System.Windows.Media.Animation.Storyboard>, aby zastosować ich animacje. Jednak podczas stosowania pojedynczej animacji w kodzie, łatwiej jest używać metody <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> zamiast używać <xref:System.Windows.Media.Animation.Storyboard>. Aby zapoznać się z przykładem, zobacz [Animuj a Property bez używania scenorysu](how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też

- [Animacja — przegląd](animation-overview.md)
- [Scenorysy — przegląd](storyboards-overview.md)
- [Przykładowe pędzle](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
