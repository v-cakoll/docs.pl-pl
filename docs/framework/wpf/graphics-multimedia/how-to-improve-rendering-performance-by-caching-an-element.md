---
title: 'Instrukcje: Poprawianie wydajności renderowania przez zapisanie elementu w pamięci podręcznej'
ms.date: 03/30/2017
helpviewer_keywords:
- rendering performance [WPF], caching an element
- BitmapCache [WPF], improving rendering performance
- CacheMode [WPF], improving rendering performance
- performance [WPF], caching an element
- UIElement [WPF], caching
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
ms.openlocfilehash: 118e8b0cca52c44788c9d5b291d710f765e7af2a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153377"
---
# <a name="how-to-improve-rendering-performance-by-caching-an-element"></a>Instrukcje: Poprawianie wydajności renderowania przez zapisanie elementu w pamięci podręcznej
Użyj <xref:System.Windows.Media.BitmapCache> klasy, aby zwiększyć wydajność renderowania złożony <xref:System.Windows.UIElement>. Aby element w pamięci podręcznej, należy utworzyć nowe wystąpienie klasy <xref:System.Windows.Media.BitmapCache> klasy i przypisz je do elementu <xref:System.Windows.UIElement.CacheMode%2A> właściwości. Można użyć ponownie <xref:System.Windows.Media.BitmapCache> wydajnie w <xref:System.Windows.Media.BitmapCacheBrush>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak utworzyć element złożony i Buforuj go jako mapę bitową, co zwiększa wydajność, gdy element jest animowany. Element jest obszarem roboczym, który przechowuje kształt geometrii za pomocą wielu wierzchołków. A <xref:System.Windows.Media.BitmapCache> z domyślnej wartości jest przypisane do <xref:System.Windows.UIElement.CacheMode%2A> obszaru roboczego i animacji pokazuje płynne Skalowanie pamięci podręcznej mapy bitowej.  
  
 [!code-xaml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.BitmapCache>
- <xref:System.Windows.Media.BitmapCacheBrush>
- <xref:System.Windows.UIElement.CacheMode%2A>
- [Instrukcje: Użyj pamięci podręcznej elementu jako pędzla](how-to-use-a-cached-element-as-a-brush.md)
