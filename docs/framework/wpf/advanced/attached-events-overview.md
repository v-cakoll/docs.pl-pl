---
title: "Przegląd Załączone zdarzenia"
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
- handling attached events [WPF]
- defining attached events as routed events [WPF]
- attached events [WPF], scenarios for
- attached events vs. routed events [WPF]
- backing attached events with routed events [WPF]
- attached events [WPF], definition
ms.assetid: 2c40eae3-80e4-4a45-ae09-df6c9ab4d91e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcfe0d97b86a27859d79685e035d8f3f765a965b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="attached-events-overview"></a>Przegląd Załączone zdarzenia
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]Definiuje składnika język i typ zdarzenia o nazwie *dołączone zdarzenie*. Pojęcie dołączone zdarzenie umożliwia dodanie obsługi dla określonego zdarzenia do dowolnego elementu, a nie do elementu, który faktycznie definiuje lub dziedziczy zdarzenia. W takim przypadku obiekt potencjalnie wywołaniem zdarzenia ani obsługi wystąpienia docelowego definiuje lub w przeciwnym razie "właścicielem" zdarzenia.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że znasz [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md) i [omówienie XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Dołączone zdarzenie składni  
 Dołączone zdarzenia mają [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składni i wzorzec kodowania, które mogą być używane przez kod zapasowy w celu zapewnienia obsługi użycia dołączone zdarzenie.  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składni, dołączone zdarzenie jest określona, nie tylko na podstawie nazwy zdarzenia, ale jego typ będący właścicielem plus nazwa zdarzenia, oddzielone kropką (.). Ponieważ nazwy zdarzenia jest kwalifikowany za pomocą nazwy typu jego właścicielem, składni dołączone zdarzenie umożliwia wszystkie dołączone zdarzenie jest dołączony do elementów, które można wdrożyć.  
  
 Na przykład poniżej przedstawiono [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składnię obsługi niestandardowych dołączanie `NeedsCleaning` dołączone zdarzenia:  
  
 [!code-xaml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Uwaga `aqua:` prefiksu; prefiks jest niezbędne w takim przypadku ponieważ dołączone zdarzenie niestandardowe zdarzenie, które pochodzą z niestandardowych xmlns mapowane.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Jak implementuje WPF dołączone zdarzenia  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dołączone zdarzenia bazują na <xref:System.Windows.RoutedEvent> pola i są wysyłane za pośrednictwem drzewa, po pojawienia się. Zazwyczaj źródło dołączone zdarzenie (obiekt, który wywołuje zdarzenie) jest źródłem system lub usługę, a obiekt, który uruchamia kod, który wywołuje zdarzenie w związku z tym nie jest bezpośrednio części drzewa elementu.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scenariusze dotyczące dołączone zdarzenia  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dołączone zdarzenia są obecne w niektórych obszarach funkcji w przypadku, gdy istnieje abstrakcji poziomu usług, takich jak zdarzenia włączane przez statycznych <xref:System.Windows.Input.Mouse> klasy lub <xref:System.Windows.Controls.Validation> klasy. Klasy, które interakcyjnie lub korzystania z usługi można użyć zdarzenia w składni dołączone zdarzenie lub mogą być powierzchni dołączone zdarzenie jako kierowanego zdarzenia, który jest częścią jak klasa integruje się z funkcjami usługi.  
  
 Mimo że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definiuje liczbę dołączone zdarzenia, scenariusze, w którym będzie używany lub obsłuż zdarzenie podłączonego bezpośrednio są bardzo ograniczony. Ogólnie rzecz biorąc, pełni funkcję architektura dołączone zdarzenie, ale są następnie przekazywane do niedołączoną (kopie z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń "otoki") kierowanego zdarzenia.  
  
 Na przykład podstawowa dołączone zdarzenia <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> więcej łatwo są obsługiwane na żadnym podane <xref:System.Windows.UIElement> za pomocą <xref:System.Windows.UIElement.MouseDown> na tej <xref:System.Windows.UIElement> zamiast zajmujących składni dołączone zdarzenie albo w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodu. Dołączone zdarzenie pełni cel architektury, ponieważ zezwala ona na przyszłe rozszerzenia urządzenia wejściowe. Urządzenie hipotetyczny tylko musi wywołać <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> w celu symulowania wejście myszy, a nie musi pochodzić od <xref:System.Windows.Input.Mouse> Aby to zrobić. Jednak ten scenariusz obejmuje kod obsługi zdarzenia, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Obsługa dołączone zdarzenie nie jest ważna dla tego scenariusza.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Obsługa dołączone zdarzenie na platformie WPF  
 Proces obsługi dołączone zdarzenie i kod obsługi, która zapisze, jest zasadniczo taki sam, jak w przypadku kierowanego zdarzenia.  
  
 Ogólnie rzecz biorąc [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone zdarzenie nie jest bardzo różnią się od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kierowanego zdarzenia. Różnice są jak zdarzenia są uzyskiwane i jak jest udostępniany przez klasę jako element członkowski (która także ma wpływ na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Składnia programu obsługi).  
  
 Jednak jak wspomniano wcześniej, istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone zdarzenia nie są szczególnie przeznaczone do obsługi w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Częściej cel zdarzenia jest umożliwienie połączone element zgłosić stan elementu nadrzędnego w składania, w którym przypadek zdarzenia jest zazwyczaj zgłaszany w kodzie i jest zależny także od klasy Obsługa w klasie nadrzędnej odpowiednie. Na przykład elementów w obrębie <xref:System.Windows.Controls.Primitives.Selector> powinny zgłaszać dołączonego <xref:System.Windows.Controls.Primitives.Selector.Selected> zdarzenie, który jest następnie klasy obsługiwane przez <xref:System.Windows.Controls.Primitives.Selector> klasy, a następnie potencjalnie przekonwertowane przez <xref:System.Windows.Controls.Primitives.Selector> klasy do różnych kierowanego zdarzenia <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Aby uzyskać więcej informacji na kierowane zdarzenia i obsługa klasa, zobacz [oznaczenie kierowane zdarzenia jako Handled i obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definiowanie własnych dołączone zdarzenia jako zdarzenia rozsyłane  
 Jeśli są pochodny typowe [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klas podstawowych można wdrożyć zdarzeń dołączonych przy tym niektórych metod wzorca w klasie i za pomocą narzędzia metod, które są już istnieje na klas podstawowych.  
  
 Wzorzec jest następujący:  
  
-   Metoda `Add*Handler` dwa parametry. Pierwszy parametr musi być zidentyfikowanie zdarzenia i określonych zdarzeń muszą odpowiadać nazwom z * w nazwie metody. Drugi parametr jest program obsługi do dodania. Metoda musi być publiczna i statyczna z Brak wartości zwracanej.  
  
-   Metoda `Remove*Handler` dwa parametry. Pierwszy parametr musi być zidentyfikowanie zdarzenia i określonych zdarzeń muszą odpowiadać nazwom z * w nazwie metody. Drugi parametr jest program obsługi do usunięcia. Metoda musi być publiczna i statyczna z Brak wartości zwracanej.  
  
 `Add*Handler` Metodę dostępu ułatwia [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] podczas przetwarzania dołączony atrybuty są zadeklarowane w elemencie programu obsługi zdarzeń. `Add*Handler` i `Remove*Handler` metody również włączyć dostęp do kodu w magazynie programu obsługi zdarzeń dla zdarzenia dołączone.  
  
 Ten wzorzec ogólne nie jest jeszcze dokładne dla wdrożeniem platformy, ponieważ żadnej podanej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] implementacji czytnika mogą mieć różnych systemów identyfikowanie podstawowej zdarzenia w obsługi language i architektury. Jest to jedna z powodów który [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia implementuje dołączone jako kierowane zdarzenia; identyfikator dla zdarzenia (<xref:System.Windows.RoutedEvent>) został już zdefiniowany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń systemu. Ponadto routingu zdarzenia to rozszerzenie implementacji fizycznych na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] poziom języka koncepcji dołączone zdarzenie.  
  
 `Add*Handler` Implementację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone zdarzenie składa się z telefoniczną <xref:System.Windows.UIElement.AddHandler%2A> kierowanego zdarzenia i obsługi jako argumenty.  
  
 Tej strategii wdrażania i systemu kierowanego zdarzenia ogólnie ograniczyć obsługę dołączone zdarzenia do albo <xref:System.Windows.UIElement> klas pochodnych lub <xref:System.Windows.ContentElement> pochodzi z klasy, ponieważ te mają tylko <xref:System.Windows.UIElement.AddHandler%2A> implementacji.  
  
 Na przykład poniższy kod definiuje `NeedsCleaning` dołączone zdarzenia w klasie właściciela `Aquarium`za pomocą [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone zdarzenie strategii zadeklarowanie zdarzenia dołączone jako kierowanego zdarzenia.  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Należy pamiętać, że metoda używany do ustanawiania pola Identyfikator dołączone zdarzenie <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, jest rzeczywiście sama metoda, która służy do rejestrowania-dołączony kierowanego zdarzenia. Dołączone zdarzenia i kierowane zdarzenia wszystkich jest zarejestrowany na centralny magazyn wewnętrzny. Ta implementacja magazynu zdarzeń umożliwia "zdarzenia jako interfejs" uwagę pojęciach, opisanej w [kierowane Przegląd zdarzeń](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Wywoływanie WPF dołączone zdarzenia  
 Zazwyczaj zbędna, nie wywołać istniejący [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdefiniowany dołączone zdarzenia z kodu. Te zdarzenia wykonaj ogólne modelu koncepcyjnego "Usługa", a usługa klas takich jak <xref:System.Windows.Input.InputManager> są odpowiedzialne za wywoływanie zdarzeń.  
  
 Jednak jeśli definiujesz niestandardowych dołączone zdarzenie na podstawie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] model tworzony dołączone zdarzenia na <xref:System.Windows.RoutedEvent>, można użyć <xref:System.Windows.UIElement.RaiseEvent%2A> aby wywołać zdarzenie dołączonych za pomocą dowolnego <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>. Wywoływanie kierowanego zdarzenia (dołączony lub nie) wymaga, aby zadeklarować określonego elementu w drzewie elementu jako źródło zdarzenia; to źródło jest raportowane jako <xref:System.Windows.UIElement.RaiseEvent%2A> wywołującego. Określanie, który element jest zgłaszana jako źródła w drzewie jest odpowiedzialny za usługi  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Szczegóły składni XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)  
 [Klasy XAML i niestandardowe dla WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
