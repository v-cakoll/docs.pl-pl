---
title: 'Instrukcje: Tworzenie niestandardowego zdarzenia trasowanego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401469"
---
# <a name="how-to-create-a-custom-routed-event"></a>Instrukcje: Tworzenie niestandardowego zdarzenia trasowanego
Aby niestandardowe zdarzenie obsługiwało routing zdarzeń, należy zarejestrować <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> za pomocą metody. W tym przykładzie przedstawiono podstawowe informacje na temat tworzenia niestandardowego zdarzenia kierowanego.  
  
## <a name="example"></a>Przykład  
 Jak pokazano w poniższym przykładzie, należy najpierw zarejestrować <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metodę przy użyciu metody. Zgodnie z Konwencją <xref:System.Windows.RoutedEvent> nazwa pola statycznego powinna kończyć się ***zdarzeniem***sufiksu. W tym przykładzie nazwa zdarzenia to `Tap` i strategia routingu <xref:System.Windows.RoutingStrategy.Bubble>zdarzenia. Po wywołaniu rejestracji można dostarczyć dla zdarzenia metody dostępu do zdarzeń środowiska uruchomieniowego języka wspólnego (CLR).  
  
 Należy zauważyć, że mimo że zdarzenie jest zgłaszane przez `OnTap` metodę wirtualną w tym konkretnym przykładzie, jak podnieść wydarzenie lub wpływ zdarzenia na zmiany zależy od Twoich potrzeb.  
  
 Należy zauważyć, że ten przykład zasadniczo implementuje całą podklasę <xref:System.Windows.Controls.Button>; ta podklasa jest tworzona jako oddzielny zestaw, a następnie tworzona jako Klasa niestandardowa na osobnej [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stronie. Jest to zilustrowanie koncepcji, które podklasy kontrolki mogą być wstawiane do drzew składających się z innych kontrolek, a w takiej sytuacji niestandardowe zdarzenia na tych kontrolkach mają takie same możliwości routingu zdarzeń jak każdy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] element macierzysty.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Zdarzenia tunelowania są tworzone w taki sam sposób, ale <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> z <xref:System.Windows.RoutingStrategy.Tunnel> ustawionym na wartość w wywołaniu rejestracji. Zgodnie z Konwencją, tunelowanie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń w programie jest poprzedzone wyrazem "Preview".  
  
 Aby zapoznać się z przykładem działania propagacji zdarzeń, zobacz temat [Obsługa zdarzenia kierowanego](how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Przegląd danych wejściowych](input-overview.md)
- [Tworzenie kontrolek — omówienie](../controls/control-authoring-overview.md)
