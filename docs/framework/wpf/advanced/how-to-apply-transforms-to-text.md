---
title: 'Instrukcje: Stosowanie przekształceń do tekstu'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], rotated text
- typography [WPF], scaled text
- skewed text [WPF]
- typography [WPF], translated text
- typography [WPF], shadowed text
- rotated text [WPF]
- translated text [WPF]
- shadowed text [WPF]
- transforms in text [WPF]
- typography [WPF], transforms
- scaled text [WPF]
- typography [WPF], skewed text
ms.assetid: 0d61678a-4185-4f2a-85c6-c1d020f96fa0
ms.openlocfilehash: b749d21c1b5940d216e244393eeb3c133dc153b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956470"
---
# <a name="how-to-apply-transforms-to-text"></a>Instrukcje: Stosowanie przekształceń do tekstu
Przekształcenia mogą zmieniać sposób wyświetlania tekstu w aplikacji. W poniższych przykładach są używane różne typy transformacji renderowania, które wpływają na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> kontrolce.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje tekst obrócony wokół określonego punktu w dwuwymiarowej płaszczyźnie x-y.  
  
 ![Tekst obrócony przy użyciu elementu RotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 Poniższy przykład kodu używa <xref:System.Windows.Media.RotateTransform> do obracania tekstu. Wartość <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 powoduje obrócenie elementu o 90 stopni w prawo.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Poniższy przykład pokazuje drugi wiersz tekstu skalowanego przez 150% wzdłuż osi x, a trzeci wiersz tekstu skalowany przez 150% wzdłuż osi y.  
  
 ![Tekst skalowany przy użyciu ScaleTransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg) 
  
 Poniższy przykład kodu używa <xref:System.Windows.Media.ScaleTransform> do skalowania tekstu z oryginalnego rozmiaru.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> Skalowanie tekstu nie jest takie samo, jak zwiększenie rozmiaru czcionki tekstu. Rozmiary czcionek są obliczane niezależnie od siebie w celu zapewnienia optymalnego rozwiązania w różnych rozmiarach. Z drugiej strony skalowanego tekstu zachowuje proporcje pierwotnego tekstu.  
  
 Poniższy przykład przedstawia tekst pochylony wzdłuż osi x.  
  
 ![Tekst skośny przy użyciu SkewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)
   
 Poniższy przykład kodu używa <xref:System.Windows.Media.SkewTransform> do pochylania tekstu. Skośność, nazywana również ścinaniem, to transformacja, która rozciąga przestrzeń współrzędnych w sposób niejednolity. W tym przykładzie dwa ciągi tekstowe są skośne — 30 ° i 30 ° wzdłuż współrzędnej x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Poniższy przykład pokazuje tekst przetłumaczony lub przenoszony, wzdłuż osi x i y.  
  
 ![Przesunięcie tekstu przy użyciu TranslateTransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 Poniższy przykład kodu używa <xref:System.Windows.Media.TranslateTransform> do przesunięcia tekstu. W tym przykładzie nieznacznie przesunięta kopia tekstu poniżej podstawowego tekstu tworzy efekt cienia.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Oferuje bogaty zestaw funkcji do zapewniania efektów cienia. Aby uzyskać więcej informacji, zobacz [Tworzenie tekstu przy użyciu cienia](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Zobacz także

- [Stosowanie animacji do tekstu](how-to-apply-animations-to-text.md)
