---
title: "Jak ustawić właściwości szerokości elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b27eb8f12e10f98d585f8f9bc445dba0118988fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>Jak ustawić właściwości szerokości elementu
## <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono wizualnie różnice między renderowania zachowanie spośród czterech właściwości związanych z szerokość [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  
  
 <xref:System.Windows.FrameworkElement> Klasa udostępnia cztery właściwości, które opisują cechy szerokość elementu. Te właściwości cztery mogą powodować konflikt, a gdy tak robią, wartość, która ma pierwszeństwo przed jest określane w następujący sposób: <xref:System.Windows.FrameworkElement.MinWidth%2A> wartość ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.MaxWidth%2A> wartość, która z kolei ma pierwszeństwo przed <xref:System.Windows.FrameworkElement.Width%2A> wartość. Właściwość czwarty <xref:System.Windows.FrameworkElement.ActualWidth%2A>, jest tylko do odczytu i raporty rzeczywista szerokość ustalany na podstawie interakcji z procesem układu.  
  
 Następujące [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] przykłady rysowania <xref:System.Windows.Shapes.Rectangle> elementu (`rect1`) jako element podrzędny <xref:System.Windows.Controls.Canvas>. Można zmienić właściwości szerokość <xref:System.Windows.Shapes.Rectangle> przy użyciu serii <xref:System.Windows.Controls.ListBox> elementy, które reprezentują wartości właściwości <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, i <xref:System.Windows.FrameworkElement.Width%2A>. W ten sposób pierwszeństwo każdej właściwości wizualnie jest wyświetlany.  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 W poniższych przykładach kodu powiązanego obsługiwać zdarzenia który <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> zgłasza zdarzenie. Każda metoda niestandardowych pobiera dane wejściowe z <xref:System.Windows.Controls.ListBox>, analizuje wartość jako <xref:System.Double>i dotyczy wartość określonej właściwości związanych z szerokości. Wartości szerokości są również konwertowana na ciąg i zapisywane w różnych <xref:System.Windows.Controls.TextBlock> elementów (definicja tych elementów nie znajduje się w wybranej XAML).  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 Pełny przykład, zobacz [przykład porównania właściwości szerokość](http://go.microsoft.com/fwlink/?LinkID=160050).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Ustawianie właściwości wysokości elementu](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [Przykład porównania właściwości szerokości](http://go.microsoft.com/fwlink/?LinkID=160050)
