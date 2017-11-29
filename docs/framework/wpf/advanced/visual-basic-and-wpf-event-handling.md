---
title: "Obsługa zdarzeń Visual Basic oraz WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca55e31060388012e6bb94e40159c2e602484911
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-and-wpf-event-handling"></a>Obsługa zdarzeń Visual Basic oraz WPF
Dla [!INCLUDE[TLA#tla_visualbnet](../../../../includes/tlasharptla-visualbnet-md.md)] języka w szczególności można użyć określonego języka `Handles` — słowo kluczowe do skojarzenia z wystąpieniami, zamiast programów obsługi zdarzeń z atrybuty dołączanie lub przy użyciu programów obsługi zdarzeń <xref:System.Windows.UIElement.AddHandler%2A> metody. Jednak `Handles` technika dołączenie obsługi do wystąpienia mają pewne ograniczenia, ponieważ `Handles` składni nie obsługuje niektórych funkcji określonych kierowanego zdarzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń systemu.  
  
## <a name="using-handles-in-a-wpf-application"></a>Za pomocą "Uchwytów" w aplikacji WPF  
 Programy obsługi zdarzeń, które są podłączone do wystąpień i zdarzeń za pomocą `Handles` muszą być wszystkie zdefiniowane w ramach deklaracji klasy częściowej wystąpienia, która jest również wymagany dla programów obsługi zdarzeń przypisanych za pomocą wartości atrybutów w elementach. Można określić tylko `Handles` dla elementu na stronie, które ma <xref:System.Windows.FrameworkContentElement.Name%2A> wartość właściwości (lub [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md) zadeklarowana). Jest to spowodowane <xref:System.Windows.FrameworkContentElement.Name%2A> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tworzy odwołania do wystąpienia, które są niezbędne do obsługi *Instance.Event* format odwołania wymagane przez `Handles` składni. Jedynym elementem, który może służyć do `Handles` bez <xref:System.Windows.FrameworkContentElement.Name%2A> odwołanie jest wystąpienie elementu głównego, który definiuje klasy częściowej.  
  
 Tej procedury obsługi można przypisać do wielu elementów, oddzielając *Instance.Event* odwołuje się po `Handles` przecinkami.  
  
 Można użyć `Handles` można przypisać więcej niż jednej procedury obsługi do tej samej *Instance.Event*odwołania. Nie należy przypisywać żadnych znaczenie kolejności, w którym obsługi są podane w `Handles` odwołania; powinien założono, że programy obsługi, które obsłużyć tego samego zdarzenia można wywołać w dowolnej kolejności.  
  
 Aby usunąć program obsługi, który został dodany przy `Handles` w deklaracji, można wywołać <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Można użyć `Handles` dołączyć obsługi kierowane zdarzenia tak długo, jak dołączyć obsługi z wystąpieniami, które zdefiniowanie zdarzenia obsługiwane w tabelach ich elementy członkowskie. Dla kierowane zdarzenia, obsługi, które są dołączone do `Handles` zgodne z regułami routingu, jak programy obsługi, które są dołączone jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybuty, lub za pomocą wspólnego podpis <xref:System.Windows.UIElement.AddHandler%2A>. Oznacza to, że jeśli zdarzenie jest już oznaczona obsługiwany ( <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość w danych zdarzenia jest `True`), następnie dołączone do obsługi `Handles` nie są wywoływane w odpowiedzi na to wystąpienie zdarzenia. Zdarzenia można było oznaczyć obsłużonych przez obsługę wystąpienia na innym elementem w trasie lub przez klasę obsługi bieżący element lub elementy wcześniejszych wzdłuż trasy. Wejściowy zdarzeń, które obsługuje zdarzenia sparowanego tunelu/bąbelków trasy tunelowania może zostały oznaczone para zdarzeń obsługiwane. Aby uzyskać więcej informacji na temat kierowane zdarzenia, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Dodawanie programów obsługi ograniczeń "Dojść"  
 `Handles`Nie można odwoływać się do obsługi dołączone zdarzenia. Należy użyć `add` metodę dostępu dla tego zdarzenia dołączone lub *typename.eventname* zdarzeń atrybutów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 Dla kierowane zdarzenia można używać tylko `Handles` można przypisać programy obsługi dla wystąpień, w którym zdarzenie istnieje w tabeli elementów członkowskich wystąpienia. Jednak z kierowane zdarzenia ogólnie rzecz biorąc, element nadrzędny może być odbiornik zdarzenia z elementów podrzędnych, nawet, jeśli element nadrzędny nie ma w tabeli elementów członkowskich tego zdarzenia. W składni atrybutu, można określić to za pośrednictwem *typename.membername* atrybutu formularza, które kwalifikują się typu faktycznie definiuje zdarzenia mają być obsługiwane. Na przykład element nadrzędny `Page` (bez `Click` zdarzeń zdefiniowanych) można nasłuchiwania zdarzeń kliknięcia przycisków, przypisując obsługi atrybutu w formularzu `Button.Click`. Ale `Handles` nie obsługuje *typename.membername* formularza, ponieważ musi obsługiwać powodujące konflikt *Instance.Event* formularza. Aby uzyskać więcej informacji, zobacz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
 `Handles`Nie można dołączyć obsługi, które są wywoływane dla zdarzeń, które są oznaczone już obsługiwany. Zamiast tego należy użyć kodu i wywołanie `handledEventsToo` przeciążenia z <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
>  Nie używaj `Handles` składni w [!INCLUDE[vb_current_short](../../../../includes/vb-current-short-md.md)] kodem w przypadku określenia programu obsługi zdarzeń dla tego samego zdarzenia w języku XAML. W takim przypadku program obsługi zdarzeń jest wywoływana dwukrotnie.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Jak implementuje WPF "obsługuje" funkcji  
 Gdy [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strona ma być kompilowana deklaruje pliku pośredniego `Friend` `WithEvents` odwołań do każdego elementu na stronie, które ma <xref:System.Windows.FrameworkContentElement.Name%2A> zestaw właściwości (lub [x: Name — dyrektywa](../../../../docs/framework/xaml-services/x-name-directive.md) zadeklarowana). Każde wystąpienie nazwane potencjalnie jest przypisana do obsługi za pomocą elementu `Handles`.  
  
> [!NOTE]
>  W ramach [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], [!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] mogą być prezentowane ukończenia, dla którego elementy są dostępne dla `Handles` odwołania na stronie. Jednak może to potrwać jednym przebiegu kompilacji, aby plik pośredniego można wypełnić wszystkie `Friends` odwołania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.UIElement.AddHandler%2A>  
 [Oznaczanie kierowane zdarzenia, ponieważ obsługiwane i klasy obsługi](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Omówienie kierowane zdarzenia](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
