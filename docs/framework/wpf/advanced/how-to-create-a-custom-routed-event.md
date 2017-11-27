---
title: "Jak utworzyć niestandardowe zdarzenie trasowane"
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
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e901242b265e0012f9ad65d9eaab89b1b63b40ac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-routed-event"></a>Jak utworzyć niestandardowe zdarzenie trasowane
Niestandardowe zdarzenie w celu obsługi zdarzeń routingu, należy zarejestrować <xref:System.Windows.RoutedEvent> przy użyciu <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody. W tym przykładzie pokazano tworzenie niestandardowych kierowanego zdarzenia.  
  
## <a name="example"></a>Przykład  
 Jak pokazano w poniższym przykładzie, musisz najpierw zarejestrować <xref:System.Windows.RoutedEvent> przy użyciu <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody. Według konwencji <xref:System.Windows.RoutedEvent> Nazwa pola statyczne powinny kończyć się sufiksem ***zdarzeń***. W tym przykładzie nazwa zdarzenia jest `Tap` i strategii routingu zdarzenia jest <xref:System.Windows.RoutingStrategy.Bubble>. Po wywołaniu metody rejestracji, możesz podać dodawania i usuwania [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] metod dostępu zdarzeń dla zdarzenia.  
  
 Należy pamiętać, że mimo, że zdarzenie jest wywoływane za pośrednictwem `OnTap` wirtualnej metody w tym przykładzie, jak wywołać zdarzenie lub sposób odpowiadania przez zdarzenie zmiany zależy od potrzeb.  
  
 Należy też zauważyć, że w tym przykładzie zasadniczo implementuje całą podklasą klasy <xref:System.Windows.Controls.Button>; jest następnie utworzyć jako niestandardowej klasy na osobnym i utworzone jako osobny zestaw tego podklasy [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strony. Jest to w celu zilustrowania koncepcji, czy formanty będące podklasami można wstawiać do drzewa zawierający inne kontrolki, i czy w takiej sytuacji zdarzenia niestandardowe tych kontrolek mają bardzo takie same możliwości routingu zdarzeń jako dowolny native [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jest element.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Tunelowania powstają zdarzenia taki sam sposób, ale z <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> ustawioną <xref:System.Windows.RoutingStrategy.Tunnel> w wywołaniu rejestracji. Według Konwencji tunelowania zdarzeń w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] są poprzedzane prefiksem słowo "W wersji zapoznawczej".  
  
 Aby zapoznać się przykładem sposobu propagacji pracy zdarzeń, zobacz [obsługi zdarzenia rozsyłane](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie kierowane zdarzenia](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Dane wejściowe — omówienie](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Formant tworzenia — omówienie](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
