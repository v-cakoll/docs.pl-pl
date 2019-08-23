---
title: 'Instrukcje: Wyliczanie zawartości rysowania wizualizacji'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 25aa0c3706005c1e16cedd7e06914db764545ebb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930070"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Instrukcje: Wyliczanie zawartości rysowania wizualizacji
Obiekt udostępnia model obiektów do wyliczania zawartości <xref:System.Windows.Media.Visual>. <xref:System.Windows.Media.Drawing>  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodę, aby <xref:System.Windows.Media.DrawingGroup> pobrać wartość <xref:System.Windows.Media.Visual> a i wyliczyć ją.  
  
> [!NOTE]
> Gdy wyliczasz zawartość wizualizacji, pobierasz <xref:System.Windows.Media.Drawing> obiekty, a nie źródłowa reprezentacja danych renderowania jako listę instrukcji grafiki wektorowej. Aby uzyskać więcej informacji, zobacz [Omówienie renderowania grafiki WPF](wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Rysowanie obiektów — przegląd](drawing-objects-overview.md)
- [Renderowanie grafiki WPF — przegląd](wpf-graphics-rendering-overview.md)
