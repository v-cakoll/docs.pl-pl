---
title: "Jak animować rozmiar FrameworkElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17882494e48c5d692c8a774e6d77408557976c71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Jak animować rozmiar FrameworkElement
Aby animować rozmiar <xref:System.Windows.FrameworkElement>, albo można animować jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> właściwości lub użyj animowany <xref:System.Windows.Media.ScaleTransform>.  
  
 W poniższym przykładzie animuje rozmiar dwa przyciski, za pomocą tych dwóch metod. Jeden z przycisków zmieni się rozmiar przez animację jego <xref:System.Windows.FrameworkElement.Width%2A> właściwości i jedno zmieni się rozmiar przez animację <xref:System.Windows.Media.ScaleTransform> stosowane do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości. Każdy przycisk zawiera tekst. Początkowo tekstu pojawi się taka sama w obu przycisków, ale jak przyciski zmieniany jest rozmiar, zostaje zniekształcony tekst drugiego przycisku.  
  
## <a name="example"></a>Przykład  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Przekształcenie elementu transformacji całego elementu i jego zawartość. Podczas bezpośrednio zmienić rozmiar elementu, tak jak w przypadku pierwszego przycisku zawartości elementu nie są zmieniany, chyba że ich rozmiar i położenie zależą od rozmiaru jego elementu nadrzędnego.  
  
 Animowanie rozmiar elementu, stosując animowany transformacji do jego <xref:System.Windows.UIElement.RenderTransform%2A> właściwości zapewnia lepszą wydajność niż animowany jego <xref:System.Windows.FrameworkElement.Width%2A> i <xref:System.Windows.FrameworkElement.Height%2A> bezpośrednio, ponieważ <xref:System.Windows.UIElement.RenderTransform%2A> właściwości wyzwala przebieg układu.  
  
 Aby uzyskać więcej informacji na temat właściwości animacji, zobacz [omówienie animacja](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Aby uzyskać więcej informacji na temat transformacje, zobacz [przekształca omówienie](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).
