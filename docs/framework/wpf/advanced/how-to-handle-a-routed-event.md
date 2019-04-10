---
title: 'Instrukcje: Obsługa zdarzenia trasowanego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
ms.openlocfilehash: edb3d6724af89b7e85986c50b579084e3c4e5070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211598"
---
# <a name="how-to-handle-a-routed-event"></a>Instrukcje: Obsługa zdarzenia trasowanego
Ten przykład pokazuje, jak Propagacja pracy zdarzenia i jak napisać program obsługi, który może przetwarzać dane zdarzenia trasowanego.  
  
## <a name="example"></a>Przykład  
 W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elementy są uporządkowane w strukturze drzewa elementu. Element nadrzędny mogą brać udział w obsłudze zdarzeń, które są początkowo zgłoszony przez elementy podrzędne w drzewie elementów. Jest to możliwe z powodu routingu zdarzeń.  
  
 Zdarzenia trasowane zwykle należy wykonać jedną z dwóch strategii routingu, Propagacja i tunelowanie. Ten przykład koncentruje się na Propagacja zdarzeń i używa <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> zdarzenie, aby wskazać działa jak routingu.  
  
 Poniższy przykład tworzy dwie <xref:System.Windows.Controls.Button> kontroluje i używa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu składni, aby dołączyć program obsługi zdarzeń do wspólnego elementu nadrzędnego, czyli w tym przykładzie <xref:System.Windows.Controls.StackPanel>. Zamiast dołączać obsługi poszczególnych zdarzeń dla każdego <xref:System.Windows.Controls.Button> elementu podrzędnego w przykładzie użyto składni atrybutów do dołączenia programu obsługi zdarzeń do <xref:System.Windows.Controls.StackPanel> elementu nadrzędnego. Ten wzorzec obsługi zdarzeń pokazuje, jak używać zdarzenia routingu jako technika zmniejszenie liczby elementów, którego program obsługi jest podłączony. Propagacja zdarzeń dla każdego <xref:System.Windows.Controls.Button> Rozsyłanie za pomocą elementu nadrzędnego.  
  
 Należy pamiętać, że w nadrzędnej <xref:System.Windows.Controls.StackPanel> elementu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> nazwę zdarzenia, określony jako atrybut częściowo kwalifikuje się za pomocą nazw <xref:System.Windows.Controls.Button> klasy. <xref:System.Windows.Controls.Button> Klasa jest <xref:System.Windows.Controls.Primitives.ButtonBase> pochodne klasy, która ma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia w jego członków, wyświetlanie listy. Ta technika częściowe kwalifikacji do dołączania do obsługi zdarzeń jest konieczne, jeśli zdarzenie, które jest obsługiwane, nie istnieje w elementach członkowskich lista elementu, którego program obsługi zdarzeń trasowanych jest podłączony.  
  
 [!code-xaml[RoutedEventHandle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 Następujące uchwyty przykład <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.  Przykład raporty, który element obsługuje zdarzenie i element, który wywołuje zdarzenie. Program obsługi zdarzeń jest wykonywany, gdy użytkownik kliknie przycisk albo.  
  
 [!code-csharp[RoutedEventHandle#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.RoutedEvent>
- [Przegląd Dane wejściowe](input-overview.md)
- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
- [— Tematy porad](events-how-to-topics.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
