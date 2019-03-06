---
title: 'Instrukcje: Zastosuj przekształcenia do tekstu'
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
ms.openlocfilehash: fd86293c539bf58ac93894e0b879dddb984825e1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378952"
---
# <a name="how-to-apply-transforms-to-text"></a>Instrukcje: Zastosuj przekształcenia do tekstu
Przekształcenia można zmienić wyświetlanie tekstu w aplikacji. W poniższych przykładach używane różne rodzaje transformacje renderowania wpływa na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> kontroli.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje tekst obrócony dotyczące określonego punktu na płaszczyźnie dwuwymiarowej x i y.  
  
 ![Tekst obrócony przy użyciu RotateTransform](./media/transformedtext01.jpg "TransformedText01")  
Przykład tekstu obróconą o 90 stopni  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.RotateTransform> Aby obrócić tekst. <xref:System.Windows.Media.RotateTransform.Angle%2A> Wartość 90 obraca element 90 stopni w prawo.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 Poniższy przykład pokazuje, drugi wiersz tekstu skalowania przez 150% wzdłuż osi x, a trzeci wiersz tekstu skalowania przez 150% wzdłuż osi y.  
  
 ![Tekst skalowane za pomocą ScaleTransform](./media/transformedtext02.jpg "TransformedText02")  
Przykład skalowany tekst  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.ScaleTransform> na tekst w skali od oryginalnego rozmiaru.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  Skalowanie tekst nie jest taka sama, jak zwiększyć rozmiar czcionki tekstu. Rozmiary czcionek są obliczane niezależnie od siebie, aby zapewnić najlepsze rozwiązania w różnych rozmiarach. Skalowany tekst zachowuje z drugiej strony, jeśli chodzi o rozmiarze oryginalny tekst.  
  
 Poniższy przykład pokazuje tekst skośny wzdłuż osi x.  
  
 ![Tekst skośny przy użyciu metody SkewTransform](./media/transformedtext03.jpg "TransformedText03")  
Przykładowy tekst skośny  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.SkewTransform> fałszować tekstu. Przesunięcia czasowego, znany także jako Pochyl jest przekształcenie, które rozciąga przestrzeni współrzędnych w sposób obsługuje technologię niejednolitego. W tym przykładzie dwa ciągi są niesymetryczne-30 i 30 wzdłuż współrzędną x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 Poniższy przykład pokazuje tekst przetłumaczony lub przeniesiona, wzdłuż osi x i y.  
  
 ![Przesunięcie, przy użyciu TranslateTransform tekstu](./media/transformedtext04.jpg "TransformedText04")  
Przykład przetłumaczonego tekstu  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.TranslateTransform> na przesunięcie tekstu. W tym przykładzie nieco przesunięcia kopię tekstu poniżej tekst podstawowy tworzy efekt w tle.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Zapewnia bogaty zestaw funkcji do prezentowania efekty. Aby uzyskać więcej informacji, zobacz [Utwórz tekst z cieniem](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Zobacz także
- [Stosowanie animacji do tekstu](how-to-apply-animations-to-text.md)
