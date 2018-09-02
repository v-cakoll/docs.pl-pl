---
title: Jak animować nieprzezroczystość elementu lub pędzla
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 549d3eab0d6d75403e962eeb146be8d7995cc931
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421805"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>Jak animować nieprzezroczystość elementu lub pędzla
Aby element framework zanikanie i widok, można animować jego <xref:System.Windows.UIElement.Opacity%2A> można animować właściwości lub <xref:System.Windows.Media.Brush.Opacity%2A> właściwość <xref:System.Windows.Media.Brush> (lub pędzle) używany do rysowania go. Animowanie nieprzezroczystości elementu sprawia, że i jego elementów podrzędnych zanikanie pojęcie widoku, ale animowanie pędzel używany do rysowania elementu pozwala na należy przemyśleć zanika część elementu. Na przykład można animować nieprzezroczystość pędzel używany do rysowania tła przycisku. To spowoduje, że tło przycisku do zastosowania blaknięcia wewnątrz i na zewnątrz widoku, przy równoczesnym zachowaniu jego tekstu jest całkowicie nieprzezroczyste.  
  
> [!NOTE]
>  Animowanie <xref:System.Windows.Media.Brush.Opacity%2A> z <xref:System.Windows.Media.Brush> zapewnia korzyści w wydajności za pośrednictwem animowanie <xref:System.Windows.UIElement.Opacity%2A> właściwości elementu.  
  
 W poniższym przykładzie dwa przyciski są animowane tak, aby ich zanikanie pojęcie widoku. Nieprzezroczystość pierwszy <xref:System.Windows.Controls.Button> jest animowany z `1.0` do `0.0` za pośrednictwem <xref:System.Windows.Media.Animation.Timeline.Duration%2A> pięć sekund. Drugi przycisk również jest animowany, ale nieprzezroczystość SolidColorBrush używany do rysowania jego <xref:System.Windows.Controls.Control.Background%2A> jest animowany zamiast nieprzezroczystości całego przycisku. Po uruchomieniu przykładzie pierwszy przycisk całkowicie zanika pojęcie widoku, gdy jako tło drugi przycisk stopniowo zmienia się z widoku. Tekst i obramowanie pozostawać w całkowicie nieprzezroczyste.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 W tym przykładzie została pominięta kodu. Pełny przykład pokazuje również, jak animować nieprzezroczystość <xref:System.Windows.Media.Color> w ramach <xref:System.Windows.Media.LinearGradientBrush>.  Aby uzyskać pełny przykład, zobacz [animowanie nieprzezroczystości przykład elementu](https://go.microsoft.com/fwlink/?LinkID=159968).
