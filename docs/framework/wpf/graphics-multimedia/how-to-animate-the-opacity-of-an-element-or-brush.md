---
title: "Jak animować nieprzezroczystość elementu lub pędzla"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 808d29292e176af8d3af1fc0f4a02c48ee05ea35
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Jak animować nieprzezroczystość elementu lub pędzla
Aby element framework zanikania i widoku, można animować jego <xref:System.Windows.UIElement.Opacity%2A> można animować właściwości lub <xref:System.Windows.Media.Brush.Opacity%2A> właściwość <xref:System.Windows.Media.Brush> (lub pędzle) używany do rysowania go. Animowanie nieprzezroczystość elementu ułatwia i jego elementów podrzędnych zanikania i widoku, ale animacji pędzel używany do rysowania elementu umożliwia bardziej selektywnie stopniowo część elementu. Można na przykład Animuj przezroczystość pędzla stosowaną tło przycisku. To spowodowałoby tło przycisku do zanikania i zmniejszanie widoku, pozostawiając całkowicie nieprzezroczyste jego tekstu.  
  
> [!NOTE]
>  Animowanie <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.Brush> zalety wydajności za pośrednictwem animacji <xref:System.Windows.UIElement.Opacity%2A> właściwości elementu.  
  
 W poniższym przykładzie dwa przyciski animowanych tak, aby ich stopniowe i widoku. Nieprzezroczystość pierwszy <xref:System.Windows.Controls.Button> jest animowany z `1.0` do `0.0` za pośrednictwem <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pięć sekund. Drugi przycisk jest również animowany, ale nieprzezroczystość SolidColorBrush używany do malowania jego <xref:System.Windows.Controls.Control.Background%2A> jest animowany zamiast nieprzezroczystości całego przycisku. Po uruchomieniu przykładzie przycisku pierwszej całkowicie stopniowo i widoku, gdy tło przycisku drugi stopniowo i widoku. Tekst i obramowania pozostają całkowicie nieprzezroczyste.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 W tym przykładzie kodu zostało pominięte. Pełny przykład przedstawiono również sposób Animuj przezroczystość <xref:System.Windows.Media.Color> w <xref:System.Windows.Media.LinearGradientBrush>.  Aby uzyskać pełny przykład, zobacz [animacji nieprzezroczystość przykład elementu](http://go.microsoft.com/fwlink/?LinkID=159968).
