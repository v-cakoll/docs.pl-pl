---
title: 'Instrukcje: Pobieranie lub ustawianie właściwości ustawienia kanwy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 06508e1198736ccb1cbda41641dff4bc634ef82b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194412"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>Instrukcje: Pobieranie lub ustawianie właściwości ustawienia kanwy
W tym przykładzie pokazano, jak używać metody pozycjonowania <xref:System.Windows.Controls.Canvas> element, aby umieścić zawartość elementu podrzędnego. W tym przykładzie użyto zawartość <xref:System.Windows.Controls.ListBoxItem> do reprezentowania pozycjonowanie wartości i konwertuje wartości wystąpienia elementu <xref:System.Double>, którego argument jest wymagany do pozycjonowania. Wartości są konwertowane do ciągów i wyświetlane jako tekst w <xref:System.Windows.Controls.TextBlock> elementu za pomocą <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ListBox> element, który ma jedenaście wybieralna <xref:System.Windows.Controls.ListBoxItem> elementów. <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Wyzwalaczy zdarzeń `ChangeLeft` niestandardowe metody, która definiuje blok kolejnych kodu.  
  
 Każdy <xref:System.Windows.Controls.ListBoxItem> reprezentuje <xref:System.Double> wartość, która jest jeden z argumentów, <xref:System.Windows.Controls.Canvas.SetLeft%2A> metody <xref:System.Windows.Controls.Canvas> akceptuje. Aby można było używać <xref:System.Windows.Controls.ListBoxItem> do reprezentowania instancji <xref:System.Double>, należy najpierw przekonwertować <xref:System.Windows.Controls.ListBoxItem> poprawny typ danych.  
  
 [!code-xaml[CanvasPositioningProperties#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 Gdy użytkownik zmienia <xref:System.Windows.Controls.ListBox> zaznaczenia, wywołuje ono `ChangeLeft` niestandardową metodę. Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.LengthConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> do wystąpienia <xref:System.Double> (należy zauważyć, że ta wartość została przekonwertowana na <xref:System.String> przy użyciu <xref:System.Windows.Controls.Control.ToString%2A> Metoda). Ta wartość jest następnie przekazywany do <xref:System.Windows.Controls.Canvas.SetLeft%2A> i <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody <xref:System.Windows.Controls.Canvas> Aby zmienić położenie `text1` obiektu.  
  
 [!code-csharp[CanvasPositioningProperties#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.ListBoxItem>
- <xref:System.Windows.LengthConverter>
- [Przegląd Panele](panels-overview.md)
