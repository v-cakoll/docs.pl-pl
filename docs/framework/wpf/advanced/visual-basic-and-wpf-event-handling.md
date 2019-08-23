---
title: Obsługa zdarzeń Visual Basic oraz WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 8407958ec76be7e402025ece57371e67581e5291
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942129"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Obsługa zdarzeń Visual Basic oraz WPF
W przypadku języka Microsoft Visual Basic .NET w konkretnym przypadku można użyć słowa kluczowego `Handles` specyficznego dla języka, aby skojarzyć programy obsługi zdarzeń z wystąpieniami, zamiast dołączać obsługi zdarzeń <xref:System.Windows.UIElement.AddHandler%2A> z atrybutami lub za pomocą metody. Jednak technika dołączania programów obsługi do wystąpień ma pewne ograniczenia, `Handles` ponieważ składnia nie może obsługiwać niektórych określonych funkcji zdarzeń [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kierowanych w systemie zdarzeń. `Handles`  
  
## <a name="using-handles-in-a-wpf-application"></a>Używanie "dojść" w aplikacji WPF  
 Programy obsługi zdarzeń, które są połączone z wystąpieniami i zdarzeniami ze `Handles` wszystkimi elementami, muszą być zdefiniowane w deklaracji klasy częściowej wystąpienia, co jest również wymaganiem dla programów obsługi zdarzeń, które są przypisywane za pomocą wartości atrybutów dla elementów. Można określić `Handles` tylko dla elementu na stronie, który <xref:System.Windows.FrameworkContentElement.Name%2A> ma wartość właściwości (lub zadeklarowaną [dyrektywę x:Name](../../xaml-services/x-name-directive.md) ). Wynika to z faktu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , <xref:System.Windows.FrameworkContentElement.Name%2A> że w programie tworzony jest odwołanie do wystąpienia, które jest niezbędne do obsługi *wystąpienia.* format `Handles` odwołania zdarzenia wymagany przez składnię. Jedynym elementem, który może być użyty dla `Handles` <xref:System.Windows.FrameworkContentElement.Name%2A> bez odwołania, jest wystąpienie elementu głównego, który definiuje klasę częściową.  
  
 Tę samą procedurę obsługi można przypisać do wielu elementów, oddzielając *wystąpienia.* odwołania do zdarzeń po `Handles` przecinkach.  
  
 Można użyć `Handles` , aby przypisać więcej niż jeden program obsługi do tego samego *wystąpienia.* odwołanie do zdarzenia. Nie należy przypisywać żadnej ważności do kolejności, w której procedury obsługi są przyznawane `Handles` w odwołaniu. należy założyć, że programy obsługi, które obsługują to samo zdarzenie, mogą być wywoływane w dowolnej kolejności.  
  
 Aby usunąć program obsługi, który został dodany `Handles` w deklaracji, można wywołać. <xref:System.Windows.UIElement.RemoveHandler%2A>  
  
 Można użyć `Handles` , aby dołączyć procedury obsługi dla zdarzeń kierowanych, tak długo, jak w przypadku dołączania obsługi do wystąpień, które definiują obsłużone zdarzenie w tabelach elementów członkowskich. Dla zdarzeń kierowanych programy obsługi, które są dołączone `Handles` do tych samych reguł routingu jak programy obsługi, które są dołączane jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybuty lub <xref:System.Windows.UIElement.AddHandler%2A>ze wspólną sygnaturą. Oznacza to, że jeśli zdarzenie jest już oznaczone jako obsługiwane ( <xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość w danych zdarzenia jest `True`), `Handles` a następnie programy obsługi dołączone do nie są wywoływane w odpowiedzi na to wystąpienie zdarzenia. Zdarzenie może być oznaczone jako obsługiwane przez obsługę wystąpień dla innego elementu w marszrucie lub przez klasę obsługi w bieżącym elemencie lub wcześniejszych elementach na trasie. Dla zdarzeń wejściowych, które obsługują sparowane zdarzenia tunelu/bąbelków, trasa tunelowania mogła oznaczać, że jest ona obsługiwana przez parę zdarzeń. Aby uzyskać więcej informacji na temat zdarzeń kierowanych, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Ograniczenia "dojść" w przypadku dodawania programów obsługi  
 `Handles`nie można odwoływać się do programów obsługi dla dołączonych zdarzeń. Należy użyć `add` metody akcesora dla tego dołączonego zdarzenia lub atrybutów zdarzeń *TypeName. EventName* w. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Aby uzyskać szczegółowe informacje, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 W przypadku zdarzeń kierowanych można użyć `Handles` tylko do przypisania programów obsługi dla wystąpień, w których to zdarzenie istnieje w tabeli elementów członkowskich wystąpienia. Jednak ze zdarzeniami kierowanymi ogólnie, element nadrzędny może być odbiornikiem zdarzenia z elementów podrzędnych, nawet jeśli element nadrzędny nie ma tego zdarzenia w tabeli elementów członkowskich. W składni atrybutów, można ją określić za pomocą atrybutu *TypeName. MemberName* , który jest zgodny z typem w rzeczywistości definiuje zdarzenie, które ma być obsługiwane. Na przykład element nadrzędny `Page` (bez `Click` zdefiniowanego zdarzenia) może nasłuchiwać zdarzeń kliknięcia przycisku przez przypisanie obsługi atrybutu w formularzu `Button.Click`. Program `Handles` nie obsługuje jednak metody *TypeName* , ponieważ musi obsługiwać wystąpienie powodujące konflikt *. formularz zdarzenia* . Aby uzyskać szczegółowe informacje, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 `Handles`nie można dołączyć programów obsługi, które są wywoływane dla zdarzeń, które są już oznaczone jako obsługiwane. Zamiast tego należy użyć kodu i wywołać `handledEventsToo` <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>Przeciążenie.  
  
> [!NOTE]
> Nie należy używać `Handles` składni w Visual Basic kodzie podczas określania programu obsługi zdarzeń dla tego samego zdarzenia w języku XAML. W takim przypadku program obsługi zdarzeń jest wywoływany dwukrotnie.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Jak WPF implementuje funkcje "Handles"  
 `WithEvents` <xref:System.Windows.FrameworkContentElement.Name%2A> `Friend` [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Po skompilowaniu strony plik pośredni deklaruje odwołania do każdego elementu na stronie, który ma ustawioną właściwość (lub x:Nameą [dyrektywę](../../xaml-services/x-name-directive.md) ). Każde nazwane wystąpienie jest potencjalnie elementem, który można przypisać do programu obsługi przez `Handles`.  
  
> [!NOTE]
> W [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]programie technologia IntelliSense może pokazać, które elementy są dostępne `Handles` dla odwołania na stronie. Jednak może to potrwać jeden przebieg kompilacji, aby plik pośredni mógł wypełnić wszystkie `Friends` odwołania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Oznaczanie zdarzeń trasowanych jako obsłużonych oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Przegląd XAML (WPF)](xaml-overview-wpf.md)
