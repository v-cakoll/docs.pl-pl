---
title: "Jak zastosować animacje do tekstu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d44565907904509a1b8f670453db5d7aa4e2583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-animations-to-text"></a>Jak zastosować animacje do tekstu
Animacji można zmienić wyświetlanie i wyglądu tekstu w aplikacji. W poniższych przykładach użyto różnych typów animacji wpływ na wyświetlanie tekstu w <xref:System.Windows.Controls.TextBlock> formantu.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> do animowania szerokość bloku tekstu. Wartość szerokości zmienia szerokość bloku tekstu na 0 przez dany okres 10 sekund, a następnie odwraca wartości szerokości i będzie kontynuowane. Ten typ animacji tworzy efekt czyszczenia.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> do Animuj przezroczystość bloku tekstu. Wartość nieprzezroczystości zmieni się z 1.0 0 przez dany okres 5 sekund, a następnie odwraca wartości nieprzezroczystość i będzie kontynuowane.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Na poniższym diagramie przedstawiono efekt <xref:System.Windows.Controls.TextBlock> kontroli zmiana jego nieprzezroczystość z `1.00` do `0.00` interwale 5 sekund zdefiniowane przez <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Tekst zmieniający nieprzezroczystość z 1,00 0,00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
Nieprzezroczystość tekstu zmiana z 1,00 na 0,00  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ColorAnimation> do animowania kolor pierwszego planu bloku tekstu. Wartość koloru pierwszego planu zmienia kolor na drugi kolor przez dany okres 5 sekund, a następnie odwraca wartości kolorów i będzie kontynuowane.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.DoubleAnimation> Obracanie bloku tekstu. Bloku tekstu wykonuje pełne obrotu w czasie trwania 20 sekund, a następnie kontynuuje Powtórz obrót.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
