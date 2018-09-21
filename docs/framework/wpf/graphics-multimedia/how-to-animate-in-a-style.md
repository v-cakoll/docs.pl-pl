---
title: Jak animować w stylu (WPF)
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: a455bbfb9defbcf83f7e490f60031917a3b41779
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46516733"
---
# <a name="how-to-animate-in-a-style"></a>Jak animować w stylu

W tym przykładzie pokazano, jak animować właściwości stylu. Gdy animowanie w stylu, tylko element framework, dla którego zdefiniowano styl może być kierowany bezpośrednio. Pod kątem obiektu freezable, użytkownik musi "kropki w dół" z właściwości elementu ze stylem.

W poniższym przykładzie kilku animacji są zdefiniowane w stylu i zastosować do <xref:System.Windows.Controls.Button>. Gdy użytkownik przesuwa wskaźnik myszy nad przyciskiem, zniknie nieprzezroczyste częściowo półprzezroczyste i Wstecz ponownie, wielokrotnie. Gdy użytkownik przesuwa mysz wyłączanie przycisku, staje się całkowicie nieprzezroczysty. Po kliknięciu przycisku koloru jego tła zmieni się z pomarańczowy na biały i z powrotem. Ponieważ <xref:System.Windows.Media.SolidColorBrush> używany do rysowania przycisku nie będzie można wykonywać bezpośrednio, jest on dostępny po dotting szczegółów przy użyciu przycisku <xref:System.Windows.Controls.Control.Background%2A> właściwości.

## <a name="example"></a>Przykład

[!code-xaml[timingbehaviors_snip#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Należy pamiętać, że gdy animowanie w stylu, możliwe do obiektów docelowych, które nie istnieją. Załóżmy, że korzysta z własnego stylu <xref:System.Windows.Media.SolidColorBrush> ustaw właściwość tła przycisku, ale w pewnym momencie styl zostanie zastąpione i tło przycisku została ustawiona za pomocą <xref:System.Windows.Media.LinearGradientBrush>.  Podjęcie próby animować <xref:System.Windows.Media.SolidColorBrush> nie zgłasza wyjątku; animacji po prostu nie powiedzie się dyskretnie.

Aby uzyskać więcej informacji na temat określania wartości docelowej składnia scenorysu, zobacz [Przegląd Scenorysy](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md). Aby uzyskać więcej informacji na temat animacji, zobacz [Przegląd animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Aby uzyskać więcej informacji na temat style zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).
