---
title: Jak zastosować przekształcenia do tekstu
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
ms.openlocfilehash: 867f39e3df8493014d8601530e91310c3bbbeeb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141617"
---
# <a name="how-to-apply-transforms-to-text"></a>Jak zastosować przekształcenia do tekstu
Transformacje mogą zmienić wyświetlanie tekstu w aplikacji. W poniższych przykładach użyto różnych typów przekształceń renderowania, aby wpłynąć na wyświetlanie tekstu w formancie. <xref:System.Windows.Controls.TextBlock>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia tekst obrócony względem określonego punktu na dwuwymiarowej płaszczyźnie x-y.  
  
 ![Tekst obrócony za pomocą rotateTransform](./media/how-to-apply-transforms-to-text/text-rotated-ninety-degrees.jpg)  
  
 Poniższy przykład kodu <xref:System.Windows.Media.RotateTransform> używa do obracania tekstu. Wartość <xref:System.Windows.Media.RotateTransform.Angle%2A> 90 obraca element o 90 stopni w prawo.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 W poniższym przykładzie pokazano drugi wiersz tekstu przeskalowany o 150% wzdłuż osi x, a trzeci wiersz tekstu przeskalowany o 150% wzdłuż osi y.  
  
 ![Tekst skalowany przy użyciu scaletransform](./media/how-to-apply-transforms-to-text/scaled-text-scaletransform.jpg)
  
 Poniższy przykład kodu <xref:System.Windows.Media.ScaleTransform> używa do skalowania tekstu z jego oryginalnego rozmiaru.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
> Skalowanie tekstu nie jest tym samym, co zwiększenie rozmiaru czcionki tekstu. Rozmiary czcionek są obliczane niezależnie od siebie w celu zapewnienia najlepszej rozdzielczości w różnych rozmiarach. Z drugiej strony skalowany tekst zachowuje proporcje tekstu o oryginalnym rozmiarze.  
  
 W poniższym przykładzie pokazano tekst pochylony wzdłuż osi x.  
  
 ![Tekst pochylony za pomocą skewTransform](./media/how-to-apply-transforms-to-text/skewed-transformed-text.jpg)

 Poniższy przykład kodu <xref:System.Windows.Media.SkewTransform> używa do pochylenia tekstu. Pochylenie, znany również jako ścinanie, jest transformacja, która rozciąga przestrzeń współrzędnych w sposób nieujemny. W tym przykładzie dwa ciągi tekstowe są pochylone -30° i 30° wzdłuż współrzędnej x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 W poniższym przykładzie przedstawiono tekst przetłumaczony lub przeniesiony wzdłuż osi x i y.  
  
 ![Przesunięcie tekstu przy użyciu translatetransform](./media/how-to-apply-transforms-to-text/transformed-text-x-y-axis.jpg)
  
 Poniższy przykład kodu <xref:System.Windows.Media.TranslateTransform> używa do przesunięcia tekstu. W tym przykładzie nieznacznie odsunięta kopia tekstu poniżej tekstu podstawowego tworzy efekt cienia.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
> Zapewnia <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> bogaty zestaw funkcji zapewniających efekty cienia. Aby uzyskać więcej informacji, zobacz [Tworzenie tekstu za pomocą cienia](how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Zobacz też

- [Stosowanie animacji do tekstu](how-to-apply-animations-to-text.md)
