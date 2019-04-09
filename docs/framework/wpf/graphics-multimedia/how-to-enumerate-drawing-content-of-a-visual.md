---
title: 'Instrukcje: Wyliczanie zawartości rysowania wizualizacji'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 4f0afc1075fe66c7f154fcef3cd883709db55316
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108007"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Instrukcje: Wyliczanie zawartości rysowania wizualizacji
<xref:System.Windows.Media.Drawing> Obiektu podaje modelu obiektu dla wyliczanie zawartości <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, która pobierze <xref:System.Windows.Media.DrawingGroup> wartość <xref:System.Windows.Media.Visual> i ją wyliczanie.  
  
> [!NOTE]
>  Gdy wyliczają to zawartość wizualizacji, są pobierane <xref:System.Windows.Media.Drawing> obiektów i nie podstawowej reprezentacji danych renderowania jako lista instrukcji grafiki wektorowej. Aby uzyskać więcej informacji, zobacz [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Przegląd Rysowanie obiektów](drawing-objects-overview.md)
- [Przegląd Renderowanie grafiki WPF](wpf-graphics-rendering-overview.md)
