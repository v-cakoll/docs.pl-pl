---
title: "Jak animować grubość obramowania z wykorzystaniem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08950b2b92bfcbd28472327f12a2ee49abfd9fed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a>Jak animować grubość obramowania z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Controls.Control.BorderThickness%2A> właściwość <xref:System.Windows.Controls.Border>. Ta animacja używa trzech klatek kluczowych w następujący sposób:  
  
1.  Podczas pierwszego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> klasy stopniowo zwiększać grubość obramowania. W przykładzie użyto <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> utworzyć smooth wzrostu liniowego między wartościami.  
  
2.  Po zakończeniu następnego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> klasy nagle zwiększyć grubość obramowania. Odrębny klatek kluczowych, takich jak te pochodzące z <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> utworzyć nagłym przechodzi między wartościami, oznacza to, ruch animacji jest jerky.  
  
3.  Podczas końcowego dwusekundowe używa wystąpienia <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> klasę, aby zmniejszyć grubość obramowania. Ramek kluczowych krzywej składanej, takich jak te pochodzące z <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> utworzyć zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> właściwości. W tym klatek kluczowych animacji wolno rozpoczyna się i przyspiesza wykładniczo do końca segmentu czasu.  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>  
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>  
 [Omówienie klucza poklatkowych](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klucz ramki — tematy porad](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [Animowanie wartość BorderThickness](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)
