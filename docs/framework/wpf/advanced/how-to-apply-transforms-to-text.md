---
title: "Jak zastosować przekształcenia do tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c1e26b31907e7794492b88ea3a696d3db4d37d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-transforms-to-text"></a>Jak zastosować przekształcenia do tekstu
Transformacje można zmienić wyświetlanie tekstu w aplikacji. W poniższych przykładach użyto różnego rodzaju transformacje renderowania wpływ na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> formantu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono tekst obraca wokół punktu określonego w płaszczyźnie dwuwymiarowa x i y.  
  
 ![Tekst obrócony przy użyciu RotateTransform](../../../../docs/framework/wpf/advanced/media/transformedtext01.jpg "TransformedText01")  
Przykład tekstu obracany o 90 stopni  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.RotateTransform> obracania tekstu. <xref:System.Windows.Media.RotateTransform.Angle%2A> Wartość 90 obraca element 90 stopni w prawo.  
  
 [!code-xaml[TextTransformSample#TextTransformSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample1)]  
  
 W poniższym przykładzie pokazano drugi wiersz tekstu skalowania o 150% wzdłuż osi x, a trzeci wiersz tekstu skalowania o 150% wzdłuż osi y.  
  
 ![Tekst wyskalowany przy użyciu ScaleTransform](../../../../docs/framework/wpf/advanced/media/transformedtext02.jpg "TransformedText02")  
Przykład skalowana tekstu  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.ScaleTransform> na skali tekst z oryginalnego rozmiaru.  
  
 [!code-xaml[TextTransformSample#TextTransformSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample2)]  
  
> [!NOTE]
>  Skalowanie tekstu nie jest taka sama jak zwiększyć rozmiar czcionki tekstu. Rozmiary czcionek są obliczane niezależnie od siebie nawzajem w celu zapewnienia najlepsze rozwiązania w różnych rozmiarach. Skalowanie tekstu z drugiej strony, zachowuje proporcje o rozmiarze oryginalny tekst.  
  
 W poniższym przykładzie przedstawiono tekst niesymetryczna wzdłuż osi x.  
  
 ![Tekst niesymetryczna przy użyciu metody SkewTransform](../../../../docs/framework/wpf/advanced/media/transformedtext03.jpg "TransformedText03")  
Przykład spowodowałoby zafałszowanie tekstu  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.SkewTransform> fałszować tekstu. Zegara, znanej także jako Ścinanie jest transformację w sposób niejednolitego rozciąga się przestrzeni współrzędnych. W tym przykładzie dwa ciągi są spowodowałoby zafałszowanie-30 i 30 wzdłuż współrzędną x.  
  
 [!code-xaml[TextTransformSample#TextTransformSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample3)]  
  
 W poniższym przykładzie przedstawiono tekstu translacji lub przenieść wzdłuż x i y.  
  
 ![Przesunięcie, przy użyciu TranslateTransform tekstu](../../../../docs/framework/wpf/advanced/media/transformedtext04.jpg "TransformedText04")  
Przykład tłumaczenia  
  
 Poniższy przykład kodu wykorzystuje <xref:System.Windows.Media.TranslateTransform> do Przesunięcie tekstu. W tym przykładzie nieco przesunięcia kopię tekstu poniżej tekst podstawowy tworzy efektem cienia.  
  
 [!code-xaml[TextTransformSample#TextTransformSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTransformSample/CS/Window1.xaml#texttransformsample4)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> Zawiera bogaty zestaw funkcji do prezentowania efekty cienia. Aby uzyskać więcej informacji, zobacz [Tworzenie tekstu w tle](../../../../docs/framework/wpf/advanced/how-to-create-text-with-a-shadow.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Stosowanie animacji do tekstu](../../../../docs/framework/wpf/advanced/how-to-apply-animations-to-text.md)
