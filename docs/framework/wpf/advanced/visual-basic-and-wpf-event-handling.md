---
title: Obsługa zdarzeń Visual Basic oraz WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 736542a4d12f96c40e836f84066dbeb8e66b9436
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358954"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Obsługa zdarzeń Visual Basic oraz WPF
W przypadku języka Microsoft Visual Basic .NET w szczególności można użyć określonego języka `Handles` — słowo kluczowe, aby skojarzyć procedury obsługi zdarzeń z wystąpieniami, zamiast dołączanie procedury obsługi zdarzeń za pomocą atrybutów lub za pomocą <xref:System.Windows.UIElement.AddHandler%2A> metody. Jednak `Handles` technika dołączanie obsługi do instancji mają pewne ograniczenia, ponieważ `Handles` składni nie obsługuje niektóre funkcje określonego zdarzenia trasowane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system zdarzeń.  
  
## <a name="using-handles-in-a-wpf-application"></a>Za pomocą "Obsługuje" w aplikacji WPF  
 Programy obsługi zdarzeń, które są połączone z wystąpieniami i zdarzeń za pomocą `Handles` wszystkie należy zdefiniować w obrębie deklaracji klasy częściowej wystąpienia, co jest także niezbędne do obsługi zdarzeń, które są przypisane do wartości atrybutów dla elementów. Można określić tylko `Handles` elementu na stronie, która ma <xref:System.Windows.FrameworkContentElement.Name%2A> wartość właściwości (lub [x: Name — dyrektywa](../../xaml-services/x-name-directive.md) zadeklarowana). Jest to spowodowane <xref:System.Windows.FrameworkContentElement.Name%2A> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tworzy odwołania do wystąpienia, które są niezbędne do obsługi *Instance.Event* format odwołania wymagane przez `Handles` składni. Jedynym elementem, który może służyć do `Handles` bez <xref:System.Windows.FrameworkContentElement.Name%2A> odwołanie jest wystąpienie elementu głównego, który definiuje częściowe klasy.  
  
 Tę samą procedurę obsługi można przypisać do wielu elementów, oddzielając *Instance.Event* odwołuje się po `Handles` przecinkami.  
  
 Możesz użyć `Handles` można przypisać więcej niż jeden program obsługi do tej samej *Instance.Event*odwołania. Nie przypisuj żadnych znaczenie kolejności, w której procedury obsługi są podane w `Handles` odwołanie; należy przyjąć, że programy obsługi, które obsługują te same zdarzenia mogą być wywoływane w dowolnej kolejności.  
  
 Aby usunąć program obsługi, który został dodany za pomocą `Handles` w deklaracji, można wywołać <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Możesz użyć `Handles` można dołączyć programy obsługi dla zdarzenia trasowane, tak długo, jak dołączyć obsługi do wystąpienia, które definiują przetwarzanego zdarzenia w tabelach ich elementy członkowskie. Dla zdarzenia trasowane, obsługi, które są dołączone za pomocą `Handles` wykonaj te same reguły routingu, jak programy obsługi, które są dołączone jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów, lub za pomocą wspólnego podpis <xref:System.Windows.UIElement.AddHandler%2A>. Oznacza to, że jeśli zdarzenie jest już oznaczony obsługiwanego ( <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość danych zdarzenia jest `True`), dołączone do programów obsługi, a następnie `Handles` nie są wywoływane w odpowiedzi na wystąpienia tego zdarzenia. Zdarzenia można oznaczyć jako obsługiwanego przez obsługi wystąpienia w innym elemencie w trasie, lub przez obsługę w bieżącego elementu lub elementów wcześniej wzdłuż trasy klasy. Dla zdarzeń wejściowych obsługujących sparowane tunelu/bąbelków zdarzeń trasy tunelowania może oznaczony pary zdarzenie obsługi. Aby uzyskać więcej informacji na temat zdarzenia trasowane, zobacz [Przegląd zdarzeń kierowane](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Ograniczenia "Uchwytów" Dodawanie programów obsługi  
 `Handles` Nie można odwoływać się programy obsługi dla zdarzenia dołączone. Należy użyć `add` metody dostępu dla tego zdarzenia dołączone, lub *typename.eventname* zdarzeń atrybutów w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aby uzyskać więcej informacji, zobacz [Przegląd zdarzeń kierowane](routed-events-overview.md).  
  
 Dla zdarzenia trasowane, można użyć tylko `Handles` można przypisać programy obsługi dla wystąpień, w której istnieje tego zdarzenia w tabeli składowych wystąpienia. Jednak ze zdarzeniami trasowanymi ogólnie rzecz biorąc, element nadrzędny może być odbiornika zdarzeń z elementów podrzędnych nawet, jeśli element nadrzędny nie ma tego zdarzenia w swojej tabeli elementów członkowskich. W składni atrybutów, można określić, to za pośrednictwem *typename.membername* atrybutu formularz, który kwalifikuje się, jakiego typu faktycznie definiuje zdarzenia mają być obsługiwane. Na przykład element nadrzędny `Page` (bez `Click` zdarzenia zdefiniowane) mogą nasłuchiwać zdarzeń kliknięcia przycisku, przypisując nieprawidłowego atrybutu w formularzu `Button.Click`. Ale `Handles` nie obsługuje *typename.membername* formularza, ponieważ sieć VPN musi obsługiwać powodujące konflikt *Instance.Event* formularza. Aby uzyskać więcej informacji, zobacz [Przegląd zdarzeń kierowane](routed-events-overview.md).  
  
 `Handles` Nie można dołączyć programów obsługi, które są wywoływane dla zdarzenia, które są już oznaczone obsługiwane. Zamiast tego należy użyć kodu i wywołania `handledEventsToo` przeciążenia <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
>  Nie używaj `Handles` składni w Visual Basic code po określeniu program obsługi zdarzeń dla tego samego zdarzenia w XAML. W takim przypadku program obsługi zdarzeń jest wywoływana dwa razy.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Jak implementuje WPF "obsługuje" funkcji  
 Gdy [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] strona jest skompilowana, deklaruje plik pośredni `Friend` `WithEvents` odwołania do każdego elementu na stronie, która ma <xref:System.Windows.FrameworkContentElement.Name%2A> właściwością (lub [x: Name — dyrektywa](../../xaml-services/x-name-directive.md) zadeklarowana). Każde wystąpienie nazwane jest potencjalnie element, który można przypisać do obsługi za pomocą `Handles`.  
  
> [!NOTE]
>  W ramach [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], [!INCLUDE[TLA2#tla_intellisense](../../../../includes/tla2sharptla-intellisense-md.md)] mogą być prezentowane zakończenia, dla której elementy są dostępne dla `Handles` odwołania na stronie. Jednak może to potrwać jednym przebiegu kompilacji tak, aby wypełnić wszystkie plik pośredni `Friends` odwołania.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.UIElement.AddHandler%2A>
- [Oznaczanie zdarzeń trasowanych jako obsłużonych oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
