---
title: Jak pobrać lub ustawić właściwości ustawienia kanwy
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Canvas control [WPF], setting positioning properties
ms.assetid: 1636b950-2b5a-4507-8a10-c5034cc58b1c
ms.openlocfilehash: 294b49d427a67da849ce930cf29a48f1735bf135
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551983"
---
# <a name="how-to-get-or-set-canvas-positioning-properties"></a>Jak pobrać lub ustawić właściwości ustawienia kanwy
Ten przykład przedstawia sposób użycia metody pozycjonowania <xref:System.Windows.Controls.Canvas> element, aby umieścić zawartość elementu podrzędnego. W tym przykładzie użyto zawartość <xref:System.Windows.Controls.ListBoxItem> do reprezentowania pozycjonowanie wartości i konwertuje wartości do wystąpienia <xref:System.Double>, który jest wymagany argument dla rozmieszczania. Wartości są następnie konwertowana do ciągów i wyświetlana jako tekst w <xref:System.Windows.Controls.TextBlock> elementu przy użyciu <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy <xref:System.Windows.Controls.ListBox> mającego jedenaście wybieralny element <xref:System.Windows.Controls.ListBoxItem> elementów. <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> Wyzwalacze zdarzeń `ChangeLeft` niestandardowej metody, która definiuje blok kodu kolejne.  
  
 Każdy <xref:System.Windows.Controls.ListBoxItem> reprezentuje <xref:System.Double> wartość, która jest jeden z argumentów który <xref:System.Windows.Controls.Canvas.SetLeft%2A> metody <xref:System.Windows.Controls.Canvas> akceptuje. Aby można było używać <xref:System.Windows.Controls.ListBoxItem> do reprezentowania wystąpienia <xref:System.Double>, należy najpierw przekonwertować <xref:System.Windows.Controls.ListBoxItem> poprawny typ danych.  
  
 [!code-xaml[CanvasPositioningProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml#1)]  
  
 Gdy użytkownik zmienia <xref:System.Windows.Controls.ListBox> zaznaczenia, wywołuje `ChangeLeft` niestandardowej metody. Ta metoda przekazuje <xref:System.Windows.Controls.ListBoxItem> do <xref:System.Windows.LengthConverter> obiektu, który konwertuje <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na wystąpienie <xref:System.Double> (Zwróć uwagę, że ta wartość została przekonwertowana na <xref:System.String> przy użyciu <xref:System.Windows.Controls.Control.ToString%2A> Metoda). Ta wartość jest następnie przekazywane z powrotem do <xref:System.Windows.Controls.Canvas.SetLeft%2A> i <xref:System.Windows.Controls.Canvas.GetLeft%2A> metody <xref:System.Windows.Controls.Canvas> aby można było zmienić jego położenie `text1` obiektu.  
  
 [!code-csharp[CanvasPositioningProperties#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasPositioningProperties/CSharp/Window1.xaml.cs#2)]
 [!code-vb[CanvasPositioningProperties#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasPositioningProperties/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.ListBoxItem>  
 <xref:System.Windows.LengthConverter>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)
