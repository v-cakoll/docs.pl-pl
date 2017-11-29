---
title: "Jak animować ciąg z wykorzystaniem klatek kluczowych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], strings with key frames
- strings [WPF], animating with key frames
- key frames [WPF], animating strings with
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8947669178de1252c10b6a8b2c01a6b55baa424
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-string-by-using-key-frames"></a>Jak animować ciąg z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować ciąg, który w tym przykładzie jest <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button> formantu przy użyciu klucza ramki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Controls.ContentControl.Content%2A> właściwość <xref:System.Windows.Controls.Button>.  
  
 Klatek kluczowych w tym przykładzie są używane <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> klasy, ponieważ animacji ciąg, który jest tworzony z klatek kluczowych można używać tylko odrębny klatek kluczowych. Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> utworzyć nagłym przechodzi między wartościami, oznacza to, zmiany w animacji wystąpić szybko i nie są niewielkie.  
  
 [!code-xaml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>  
 <xref:System.Windows.Controls.ContentControl.Content%2A>  
 <xref:System.Windows.Controls.Button>  
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>  
 [Omówienie klucza poklatkowych](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klucz ramki — tematy porad](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
