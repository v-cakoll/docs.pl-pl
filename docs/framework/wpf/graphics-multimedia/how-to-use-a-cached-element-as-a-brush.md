---
title: "Jak użyć zachowanego w pamięci podręcznej elementu jako pędzla"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BitmapCache [WPF], using
- cached element [WPF], use as a brush
- BitmapCacheBrush [WPF], using
- CacheMode [WPF], using
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d0f0c60e9df6a1ec816b1f9cf5769c93b382ae5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-cached-element-as-a-brush"></a>Jak użyć zachowanego w pamięci podręcznej elementu jako pędzla
Użyj <xref:System.Windows.Media.BitmapCacheBrush> klasy do ponownego użycia pamięci podręcznej elementu wydajnie. W pamięci podręcznej elementu, Utwórz nowe wystąpienie klasy <xref:System.Windows.Media.BitmapCache> klasy i przypisz je do elementu <xref:System.Windows.UIElement.CacheMode%2A> właściwości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje, jak do ponownego użycia elementu pamięci podręcznej. Element pamięci podręcznej jest <xref:System.Windows.Controls.Image> kontrolkę wyświetlającą duży obraz. <xref:System.Windows.Controls.Image> Kontroli pamięci podręcznej w postaci mapy bitowej przy użyciu <xref:System.Windows.Media.BitmapCache> klasy i pamięci podręcznej zostanie ponownie użyty przez przypisanie go do <xref:System.Windows.Media.BitmapCacheBrush>. Pędzel jest przypisany do tła przycisków dwadzieścia pięć pokazanie wydajne ponownego użycia.  
  
 [!code-xaml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.BitmapCache>  
 <xref:System.Windows.Media.BitmapCacheBrush>  
 <xref:System.Windows.UIElement.CacheMode%2A>  
 [Porady: poprawy renderowania wydajności przez buforowanie elementu](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)
