---
title: Jak animować styl
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 0b29648bf15f0046adcdee610f9565f7deb24972
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744883"
---
# <a name="how-to-animate-in-a-style"></a>Jak animować styl

Ten przykład pokazuje, jak animować właściwości w stylu. Podczas animacji w obrębie stylu tylko element Framework, dla którego zdefiniowany jest styl, może być bezpośrednio kierowany. Aby określić obiekt docelowy obiektu Freezable, należy "kropka" na podstawie właściwości elementu style.

W poniższym przykładzie kilka animacji jest zdefiniowanych w stylu i stosowane do <xref:System.Windows.Controls.Button>. Gdy użytkownik przesuwa wskaźnik myszy nad przyciskiem, stopniowo przechodzi od nieprzezroczystego do częściowego odpółprzezroczystego i tyłu. Gdy użytkownik przesuwa przycisk myszy, staje się całkowicie nieprzezroczysty. Po kliknięciu przycisku jego kolor tła zmieni się z pomarańczowy na biały i z powrotem. Ponieważ <xref:System.Windows.Media.SolidColorBrush> użyta do malowania przycisk nie może być celem bezpośrednio, dostęp do niego odbywa się za pomocą kropkowanej wartości właściwości <xref:System.Windows.Controls.Control.Background%2A> przycisku.

## <a name="example"></a>Przykład

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

Należy pamiętać, że podczas animacji w stylu istnieje możliwość, że obiekty docelowe nie istnieją. Załóżmy na przykład, że styl używa <xref:System.Windows.Media.SolidColorBrush> do ustawiania właściwości tła przycisku, ale w pewnym momencie styl jest zastępowany, a tło przycisku jest ustawiane za pomocą <xref:System.Windows.Media.LinearGradientBrush>.  Próba animowania <xref:System.Windows.Media.SolidColorBrush> nie spowoduje wygenerowania wyjątku; Animacja po prostu zakończy się niepowodzeniem w trybie dyskretnym.

Aby uzyskać więcej informacji na temat składni docelowej scenorysu, zobacz [Omówienie scenorysów](storyboards-overview.md). Aby uzyskać więcej informacji na temat animacji, zobacz [Omówienie animacji](animation-overview.md). Aby uzyskać więcej informacji na temat stylów, zobacz [Style i tworzenia szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).
