---
title: Jak animować rozmiar FrameworkElement
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: 148e3d592e129984bd2f7ac062340c5169e48d30
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543988"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Jak animować rozmiar FrameworkElement
Aby animować rozmiar <xref:System.Windows.FrameworkElement>, albo można animować jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości lub użyj animowany <xref:System.Windows.Media.ScaleTransform>.  
  
 W poniższym przykładzie animuje rozmiar dwa przyciski, za pomocą tych dwóch metod. Jeden z przycisków zmieni się rozmiar przez animację jego <xref:System.Windows.FrameworkElement.Width%2A> właściwości i jedno zmieni się rozmiar przez animację <xref:System.Windows.Media.ScaleTransform> stosowane do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości. Każdy przycisk zawiera tekst. Początkowo tekstu pojawi się taka sama w obu przycisków, ale jak przyciski zmieniany jest rozmiar, zostaje zniekształcony tekst drugiego przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Przekształcenie elementu transformacji całego elementu i jego zawartość. Podczas bezpośrednio zmienić rozmiar elementu, tak jak w przypadku pierwszego przycisku zawartości elementu nie są zmieniany, chyba że ich rozmiar i położenie zależą od rozmiaru jego elementu nadrzędnego.  
  
 Animowanie rozmiar elementu, stosując animowany transformacji do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości zapewnia lepszą wydajność niż animowany jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> bezpośrednio, ponieważ <xref:System.Windows.UIElement.RenderTransform%2A> właściwości wyzwala przebieg układu.  
  
 Aby uzyskać więcej informacji na temat właściwości animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Aby uzyskać więcej informacji na temat transformacje, zobacz [przekształca omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).
