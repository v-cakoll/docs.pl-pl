---
title: Jak animować w stylu
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: e0741a869ab81875aaa25340de851ef939e11a6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-in-a-style"></a>Jak animować w stylu
W tym przykładzie pokazano, jak można animować właściwości w stylu. W przypadku działania animacji jest używana w stylu bezpośrednio można zastosować tylko element framework, dla którego styl jest zdefiniowany. Docelowy obiekt obiektu freezable, możesz musi "dot w dół" z właściwością styl elementu.  
  
 W poniższym przykładzie kilka animacje są zdefiniowane w stylu i stosowane do <xref:System.Windows.Controls.Button>. Gdy użytkownik przesuwa wskaźnik myszy nad przyciskiem, zniknie nieprzezroczyste częściowo przezroczyste i Wstecz ponownie, wielokrotnie. Gdy użytkownik przesuwa wskaźnik myszy poza przycisk, staje się całkowicie przezroczystości. Po kliknięciu przycisku kolor tła zmienia pomarańczowy do białe i z powrotem. Ponieważ <xref:System.Windows.Media.SolidColorBrush> używana do malowania przycisku nie może być celem bezpośrednio, jest dostępny przez dotting w dół od przycisku <xref:System.Windows.Controls.Control.Background%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Należy pamiętać, że gdy animacji w stylu, możliwe do obiektów docelowych, które nie istnieją. Załóżmy na przykład, używa własnego stylu <xref:System.Windows.Media.SolidColorBrush> ustaw właściwość tło przycisku, ale w niektórych punktu styl jest zastępowany i ustawiono tło przycisku <xref:System.Windows.Media.LinearGradientBrush>.  Próby animować <xref:System.Windows.Media.SolidColorBrush> nie będzie zgłaszać wyjątek; animacji po prostu nie powiedzie się trybie dyskretnym.  
  
 Aby uzyskać więcej informacji na temat scenorysu przeznaczonych dla składni, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Aby uzyskać więcej informacji na temat animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Aby uzyskać więcej informacji na temat stylów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).
