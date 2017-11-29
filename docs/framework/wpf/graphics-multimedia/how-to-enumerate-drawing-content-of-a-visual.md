---
title: "Jak wykazać zawartość rysowania Visual"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e498bc8e425198e479d7ce0b2328e0efa3ede70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Jak wykazać zawartość rysowania Visual
<xref:System.Windows.Media.Drawing> Obiektu Podaj model obiektów dla wyliczania zawartość <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda pobierania <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i jej wyliczyć.  
  
> [!NOTE]
>  Gdy są wyliczania zawartość elementu wizualnego, są pobierane <xref:System.Windows.Media.Drawing> obiektów, a nie podstawowy reprezentację danych renderowania jako listę instrukcji grafiki wektorowej. Aby uzyskać więcej informacji, zobacz [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [Rysowanie obiekty — omówienie](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Przegląd renderowania grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
