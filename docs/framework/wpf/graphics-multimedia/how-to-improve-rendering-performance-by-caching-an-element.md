---
title: "Jak poprawić wydajność renderowania przez zapisanie elementu w pamięci podręcznej"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9cd12b811ae4dd89c645ada1f4f70b06f73b9b13
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Jak poprawić wydajność renderowania przez zapisanie elementu w pamięci podręcznej
Użyj <xref:System.Windows.Media.BitmapCache> klasę, aby poprawić wydajność renderowania złożonego <xref:System.Windows.UIElement>. W pamięci podręcznej elementu, Utwórz nowe wystąpienie klasy <xref:System.Windows.Media.BitmapCache> klasy i przypisz je do elementu <xref:System.Windows.UIElement.CacheMode%2A> właściwości. Można użyć ponownie <xref:System.Windows.Media.BitmapCache> wydajnie w <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć złożonego elementu i pamięci podręcznej go jako mapa bitowa, co zwiększa wydajność, gdy element jest animowany. Element jest kanwy, która przechowuje mają geometrię kształt z wielu wierzchołków. A <xref:System.Windows.Media.BitmapCache> z domyślnej wartości jest przypisany do <xref:System.Windows.UIElement.CacheMode%2A> obszaru roboczego i zawiera animacji sprawne Skalowanie pamięci podręcznej mapy bitowej.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Instrukcje: używanie zachowanego w pamięci podręcznej elementu jako pędzla](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)
