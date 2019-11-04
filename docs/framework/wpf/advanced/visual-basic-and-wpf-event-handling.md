---
title: Obsługa zdarzeń Visual Basic oraz WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Visual Basic [WPF], event handlers
- event handlers [WPF], Visual Basic
ms.assetid: ad4eb9aa-3afc-4a71-8cf6-add3fbea54a1
ms.openlocfilehash: 9a3d579019db4d2b59a0252dbe63b4a6a0468849
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458301"
---
# <a name="visual-basic-and-wpf-event-handling"></a>Obsługa zdarzeń Visual Basic oraz WPF
W przypadku języka Microsoft Visual Basic .NET w konkretnym przypadku można użyć słowa kluczowego `Handles` specyficznego dla języka w celu skojarzenia programów obsługi zdarzeń z wystąpieniami, zamiast dołączać obsługi zdarzeń z atrybutami lub przy użyciu metody <xref:System.Windows.UIElement.AddHandler%2A>. Jednak technika `Handles` dołączania programów obsługi do wystąpień ma pewne ograniczenia, ponieważ składnia `Handles` nie może obsługiwać niektórych określonych funkcji zdarzeń kierowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systemie zdarzeń.  
  
## <a name="using-handles-in-a-wpf-application"></a>Używanie "dojść" w aplikacji WPF  
 Programy obsługi zdarzeń, które są połączone z wystąpieniami i zdarzeniami ze `Handles` muszą być zdefiniowane w deklaracji klasy częściowej wystąpienia, co jest również wymaganiem dla programów obsługi zdarzeń, które są przypisywane za pomocą wartości atrybutów dla elementów. Na stronie można określić tylko `Handles` dla elementu, który ma <xref:System.Windows.FrameworkContentElement.Name%2A> wartość właściwości (lub zadeklarowaną [dyrektywę x:Name](../../xaml-services/x-name-directive.md) ). Dzieje się tak, ponieważ <xref:System.Windows.FrameworkContentElement.Name%2A> w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tworzy odwołanie do wystąpienia, które jest niezbędne do obsługi *wystąpienia.* format odwołania zdarzenia wymagany przez składnię `Handles`. Jedynym elementem, który może być używany dla `Handles` bez odwołania <xref:System.Windows.FrameworkContentElement.Name%2A>, jest wystąpienie elementu głównego, które definiuje klasę częściową.  
  
 Tę samą procedurę obsługi można przypisać do wielu elementów, oddzielając *wystąpienia.* odwołania do zdarzeń po `Handles` przecinkami.  
  
 Za pomocą `Handles` można przypisać więcej niż jeden program obsługi do tego samego *wystąpienia.* odwołanie do zdarzenia. Nie należy przypisywać żadnej ważności do kolejności, w której procedury obsługi są podawane w odniesieniu do `Handles`; należy założyć, że programy obsługi, które obsługują to samo zdarzenie, mogą być wywoływane w dowolnej kolejności.  
  
 Aby usunąć program obsługi, który został dodany przy użyciu `Handles` w deklaracji, można wywołać <xref:System.Windows.UIElement.RemoveHandler%2A>.  
  
 Za pomocą `Handles` można dołączać procedury obsługi dla zdarzeń kierowanych, tak długo, jak program obsługi jest dołączany do wystąpień, które definiują obsłużone zdarzenie w tabelach elementów członkowskich. Dla zdarzeń kierowanych programy obsługi, które są dołączone do `Handles` są zgodne z tymi samymi regułami routingu jak programy obsługi, które są dołączone jako atrybuty [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub ze wspólną sygnaturą <xref:System.Windows.UIElement.AddHandler%2A>. Oznacza to, że jeśli zdarzenie jest już oznaczone jako obsłużone (<xref:System.Windows.RoutedEventArgs.Handled%2A> właściwość w danych zdarzenia jest `True`), a następnie programy obsługi dołączone do `Handles` nie są wywoływane w odpowiedzi na to wystąpienie zdarzenia. Zdarzenie może być oznaczone jako obsługiwane przez obsługę wystąpień dla innego elementu w marszrucie lub przez klasę obsługi w bieżącym elemencie lub wcześniejszych elementach na trasie. Dla zdarzeń wejściowych, które obsługują sparowane zdarzenia tunelu/bąbelków, trasa tunelowania mogła oznaczać, że jest ona obsługiwana przez parę zdarzeń. Aby uzyskać więcej informacji na temat zdarzeń kierowanych, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
## <a name="limitations-of-handles-for-adding-handlers"></a>Ograniczenia "dojść" w przypadku dodawania programów obsługi  
 `Handles` nie może odwoływać się do programów obsługi dla dołączonych zdarzeń. Należy użyć metody dostępu `add` dla tego dołączonego zdarzenia lub *atrybutu TypeName. EventName* w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Aby uzyskać szczegółowe informacje, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 W przypadku zdarzeń kierowanych można używać `Handles` do przypisywania programów obsługi dla wystąpień, w których to zdarzenie istnieje w tabeli elementów członkowskich wystąpienia. Jednak ze zdarzeniami kierowanymi ogólnie, element nadrzędny może być odbiornikiem zdarzenia z elementów podrzędnych, nawet jeśli element nadrzędny nie ma tego zdarzenia w tabeli elementów członkowskich. W składni atrybutów, można ją określić za pomocą atrybutu *TypeName. MemberName* , który jest zgodny z typem w rzeczywistości definiuje zdarzenie, które ma być obsługiwane. Na przykład nadrzędna `Page` (bez zdefiniowanego zdarzenia `Click`) może nasłuchiwać zdarzeń kliknięcia przycisku przez przypisanie obsługi atrybutu w `Button.Click`. Ale `Handles` nie obsługuje formularza *TypeName. MemberName* , ponieważ musi obsługiwać wystąpienie powodujące konflikt. formularz *zdarzenia* . Aby uzyskać szczegółowe informacje, zobacz [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
 `Handles` nie może dołączyć programów obsługi, które są wywoływane dla zdarzeń, które są już oznaczone jako obsługiwane. Zamiast tego należy użyć kodu i wywoływać `handledEventsToo` Przeciążenie <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29>.  
  
> [!NOTE]
> Nie należy używać składni `Handles` w kodzie Visual Basic podczas określania programu obsługi zdarzeń dla tego samego zdarzenia w języku XAML. W takim przypadku program obsługi zdarzeń jest wywoływany dwukrotnie.  
  
## <a name="how-wpf-implements-handles-functionality"></a>Jak WPF implementuje funkcje "Handles"  
 Po skompilowaniu strony [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] plik pośredni deklaruje `Friend` `WithEvents` odwołań do każdego elementu na stronie, który ma zestaw właściwości <xref:System.Windows.FrameworkContentElement.Name%2A> (lub zadeklarowana [dyrektywa x:Name](../../xaml-services/x-name-directive.md) ). Każde nazwane wystąpienie jest potencjalnie elementem, który można przypisać do programu obsługi za pomocą `Handles`.  
  
> [!NOTE]
> W programie Visual Studio technologia IntelliSense może pokazać, które elementy są dostępne dla `Handles` odwołanie na stronie. Jednak może to potrwać jeden przebieg kompilacji, aby plik pośredni mógł wypełnić wszystkie `Friends` odwołania.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.UIElement.AddHandler%2A>
- [Oznaczanie zdarzeń trasowanych jako obsłużonych oraz obsługa klasy](marking-routed-events-as-handled-and-class-handling.md)
- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Przegląd XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
