---
title: "Jak animować w stylu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2aabe24b77a9016b5b8119646c80ea84eb73acb9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-in-a-style"></a>Jak animować w stylu
W tym przykładzie pokazano, jak można animować właściwości w stylu. W przypadku działania animacji jest używana w stylu bezpośrednio można zastosować tylko element framework, dla którego styl jest zdefiniowany. Docelowy obiekt obiektu freezable, możesz musi "dot w dół" z właściwością styl elementu.  
  
 W poniższym przykładzie kilka animacje są zdefiniowane w stylu i stosowane do <xref:System.Windows.Controls.Button>. Gdy użytkownik przesuwa wskaźnik myszy nad przyciskiem, zniknie nieprzezroczyste częściowo przezroczyste i Wstecz ponownie, wielokrotnie. Gdy użytkownik przesuwa wskaźnik myszy poza przycisk, staje się całkowicie przezroczystości. Po kliknięciu przycisku kolor tła zmienia pomarańczowy do białe i z powrotem. Ponieważ <xref:System.Windows.Media.SolidColorBrush> używana do malowania przycisku nie może być celem bezpośrednio, jest dostępny przez dotting w dół od przycisku <xref:System.Windows.Controls.Control.Background%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]  
  
 Należy pamiętać, że gdy animacji w stylu, możliwe do obiektów docelowych, które nie istnieją. Załóżmy na przykład, używa własnego stylu <xref:System.Windows.Media.SolidColorBrush> ustaw właściwość tło przycisku, ale w niektórych punktu styl jest zastępowany i ustawiono tło przycisku <xref:System.Windows.Media.LinearGradientBrush>.  Próby animować <xref:System.Windows.Media.SolidColorBrush> nie będzie zgłaszać wyjątek; animacji po prostu nie powiedzie się trybie dyskretnym.  
  
 Aby uzyskać więcej informacji na temat scenorysu przeznaczonych dla składni, zobacz [omówienie Scenorys](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Aby uzyskać więcej informacji na temat animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Aby uzyskać więcej informacji na temat stylów, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).
