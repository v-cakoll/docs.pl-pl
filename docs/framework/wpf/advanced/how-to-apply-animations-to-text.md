---
title: Jak zastosować animacje do tekstu
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174631"
---
# <a name="how-to-apply-animations-to-text"></a>Jak zastosować animacje do tekstu
Animacje mogą zmieniać wyświetlanie i wygląd tekstu w aplikacji. Poniższe przykłady używają różnych typów animacji, aby <xref:System.Windows.Controls.TextBlock> wpłynąć na wyświetlanie tekstu w formancie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania szerokości bloku tekstu. Wartość szerokości zmienia się z szerokości bloku tekstu na 0 w czasie trwania 10 sekund, a następnie odwraca wartości szerokości i kontynuuje. Ten typ animacji tworzy efekt czyszczenia.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania krycia bloku tekstu. Wartość krycia zmienia się z 1,0 na 0 w czasie trwania 5 sekund, a następnie odwraca wartości krycia i kontynuuje.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Na poniższym diagramie <xref:System.Windows.Controls.TextBlock> przedstawiono efekt zmiany `1.00` krycia formantu z do `0.00` <xref:System.Windows.Media.Animation.Timeline.Duration%2A>5-sekundowego interwału zdefiniowanego przez .  
  
 ![Zmiana krycia tekstu z 1,00 na 0,00.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.ColorAnimation> do animowania koloru pierwszego planu bloku tekstu. Wartość koloru pierwszego planu zmienia się z jednego koloru na drugi w czasie trwania 5 sekund, a następnie odwraca wartości kolorów i kontynuuje.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 W poniższym przykładzie użyto a <xref:System.Windows.Media.Animation.DoubleAnimation> do obracania bloku tekstu. Blok tekstu wykonuje pełny obrót przez 20 sekund, a następnie kontynuuje powtarzanie obrotu.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Animacja](../graphics-multimedia/animation-overview.md)
