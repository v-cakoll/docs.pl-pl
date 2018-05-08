---
title: Jak obsłużyć zdarzenie trasowane
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: 80b3be439498c0dc448322d1e7daf30202a470dc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-handle-a-routed-event"></a>Jak obsłużyć zdarzenie trasowane
Ten przykład przedstawia sposób propagacji pracy zdarzenia i jak napisać programu obsługi, który może przetwarzać danych kierowanego zdarzenia.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elementy są rozmieszczane w strukturze drzewa elementu. Element nadrzędny mogą uczestniczyć w obsłudze zdarzeń, które są początkowo zgłoszony przez elementy podrzędne w drzewie elementu. Jest to możliwe z powodu zdarzenia routingu.  
  
 Zazwyczaj kierowane zdarzenia wykonaj jedną z dwóch strategii routingu propagacji lub tunelowania. W tym przykładzie koncentruje się na zdarzeń propagacji i używa <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> zdarzeń do wyświetlenia działa jak routingu.  
  
 Poniższy przykład tworzy dwa <xref:System.Windows.Controls.Button> formanty i używa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu dołączania program obsługi zdarzeń do wspólnego elementu nadrzędnego, który w tym przykładzie jest <xref:System.Windows.Controls.StackPanel>. Zamiast dołączanie obsługi poszczególnych zdarzeń dla każdego <xref:System.Windows.Controls.Button> elementu podrzędnego w przykładzie użyto Składnia atrybutu można dołączyć do programu obsługi zdarzeń <xref:System.Windows.Controls.StackPanel> elementu nadrzędnego. Ten wzorzec obsługi zdarzeń pokazano, jak używać zdarzeń routingu jako technika zmniejszenie liczby elementów, którego program obsługi jest podłączony. Wszystkie zdarzenia propagacji dla każdego <xref:System.Windows.Controls.Button> Rozsyłanie za pomocą elementu nadrzędnego.  
  
 Należy pamiętać, że w nadrzędnej <xref:System.Windows.Controls.StackPanel> elementu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Nazwa zdarzenia określony jako atrybut częściowo jest kwalifikowany za pomocą nazw <xref:System.Windows.Controls.Button> klasy. <xref:System.Windows.Controls.Button> Jest klasa <xref:System.Windows.Controls.Primitives.ButtonBase> klasy, która ma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia w jego elementów członkowskich wyświetlania. Ta technika częściowe kwalifikacji dołączanie program obsługi zdarzeń jest niezbędne, jeśli nie istnieje zdarzenie, które jest obsługiwane w elementach członkowskich wyświetlania elementu, w którym jest umocowana Obsługa kierowanego zdarzenia.  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 Następujący przykład uchwytów <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  Przykład raporty element, który obsługuje zdarzenie i który element wywołuje zdarzenie. Program obsługi zdarzeń jest wykonywany, gdy użytkownik kliknie przycisk albo.  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.RoutedEvent>  
 [Przegląd danych wejściowych](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [Szczegóły składni XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
