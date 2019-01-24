---
title: 'Instrukcje: Wykaż zawartość rysowania Visual'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: a3131b6c86b0f6a7aa79cca305b9c3b2496346f4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54561951"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Instrukcje: Wykaż zawartość rysowania Visual
<xref:System.Windows.Media.Drawing> Obiektu podaje modelu obiektu dla wyliczanie zawartości <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, która pobierze <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i ją wyliczanie.  
  
> [!NOTE]
>  Gdy wyliczają to zawartość wizualizacji, są pobierane <xref:System.Windows.Media.Drawing> obiektów i nie podstawowej reprezentacji danych renderowania jako lista instrukcji grafiki wektorowej. Aby uzyskać więcej informacji, zobacz [Przegląd Renderowanie grafiki WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Rysowanie obiektów — przegląd](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
- [Renderowanie grafiki WPF — przegląd](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
