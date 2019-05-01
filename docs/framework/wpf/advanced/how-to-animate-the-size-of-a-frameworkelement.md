---
title: 'Instrukcje: Animowanie rozmiaru elementu FrameworkElement'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: d1995deec5ab2c9bf405911af43b4d242d599119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776912"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Instrukcje: Animowanie rozmiaru elementu FrameworkElement
Aby animować rozmiar <xref:System.Windows.FrameworkElement>, albo można animować jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości lub użycie animowanych <xref:System.Windows.Media.ScaleTransform>.  
  
 W poniższym przykładzie animuje rozmiar dwa przyciski, za pomocą tych dwóch metod. Jeden przycisk zmiany rozmiaru, animowanie jego <xref:System.Windows.FrameworkElement.Width%2A> właściwości, a drugi jest poddany zmianie rozmiaru przez animowanie <xref:System.Windows.Media.ScaleTransform> stosowane do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości. Każdy przycisk zawiera jakiś tekst. Początkowo tekstu pojawi się taka sama w obu przycisków, ale jako przycisków zmieniany jest rozmiar tekstu w drugi przycisk staje się zakłócona.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformanimations_snip#1](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Przekształcenie elementu są przekształcane cały element i jego zawartość. Gdy bezpośrednio zmienić rozmiar elementu, tak jak w przypadku pierwszego przycisku zawartością elementu są rozmiar nie zmieni, chyba że ich rozmiar i położenie są zależne od rozmiaru jego elementu nadrzędnego.  
  
 Animowanie rozmiaru elementu, stosując animowany przekształcenie do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwość zapewnia lepszą wydajność niż animowane jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> bezpośrednio, ponieważ <xref:System.Windows.UIElement.RenderTransform%2A> właściwość nie będzie wyzwalać przekazanie układu.  
  
 Aby uzyskać więcej informacji na temat Animowanie właściwości, zobacz [Przegląd animacja](../graphics-multimedia/animation-overview.md). Aby uzyskać więcej informacji na temat przekształceń, zobacz [przekształca Przegląd](../graphics-multimedia/transforms-overview.md).
