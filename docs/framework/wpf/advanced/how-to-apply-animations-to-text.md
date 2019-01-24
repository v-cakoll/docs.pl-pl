---
title: 'Instrukcje: Zastosuj animacje do tekstu'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56336c45639168c6432b92fe555c6d37448cb7cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720512"
---
# <a name="how-to-apply-animations-to-text"></a>Instrukcje: Zastosuj animacje do tekstu
Animacji można zmienić ekran i wygląd tekstu w aplikacji. W poniższych przykładach używane różne rodzaje animacji wpływa na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> kontroli.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować szerokość blok tekstu. Wartość szerokości zmieni się z szerokość blok tekstu 0 dany okres 10 sekund, a następnie odwraca wartości szerokości i jest kontynuowane. Ten typ animacji tworzy efekt czyszczenia.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> animować nieprzezroczystość blok tekstu. Wartość nieprzezroczystości zmieni się z wersji 1.0 0 dany okres 5 sekund, a następnie odwraca nieprzezroczystość wartości i jest kontynuowane.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Na poniższym diagramie przedstawiono efekt <xref:System.Windows.Controls.TextBlock> kontroli, zmiana jego nieprzezroczystości od `1.00` do `0.00` podczas 5-sekundowego interwału definicją <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Tekst, zmiana nieprzezroczystość z 1,00 0,00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
Nieprzezroczystość tekstu zmiana z 1,00 0,00  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ColorAnimation> animować kolor pierwszego planu blok tekstu. Wartość koloru pierwszego planu zmieni się z jednego koloru na drugi kolor dany okres 5 sekund, a następnie odwraca wartości kolorów i jest kontynuowane.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> wymienić blok tekstu. Blok tekstu wykonuje pełne obrotu w czasie trwania wynoszącego 20 sekund i następnie w dalszym ciągu należy powtórzyć obrót.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Zobacz także
- [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
