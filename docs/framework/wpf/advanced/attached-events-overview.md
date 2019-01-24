---
title: Przegląd Załączone zdarzenia
ms.date: 03/30/2017
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
ms.openlocfilehash: b82af44b1262f4eb2839efef85a4b35eba534524
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682959"
---
# <a name="attached-events-overview"></a>Przegląd Załączone zdarzenia
[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Definiuje składnika języka i typu zdarzenia o nazwie *dołączone zdarzenie*. Pojęcie dołączone zdarzenie umożliwia dodanie obsługi dla określonego zdarzenia do dowolnego elementu, a nie do elementu, który faktycznie definiuje lub dziedziczy zdarzenia. W tym przypadku obiekt potencjalnie podnoszonego zdarzenia ani docelowym wystąpienia obsługi definiuje lub w przeciwnym razie jego "właścicielem" zdarzenie.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że użytkownik przeczytał [Przegląd zdarzeń kierowane](../../../../docs/framework/wpf/advanced/routed-events-overview.md) i [Przegląd XAML (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Dołączone zdarzenie składni  
 Dołączone zdarzenia mają [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składnia i wzorzec pisania kodu, który musi być używany przez kod tworzenia kopii w celu zapewnienia obsługi użycia dołączone zdarzenie.  
  
 W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składni dołączone zdarzenie jest określona, nie tylko przez jego nazwę zdarzenia, ale przez jego typu, będącego właścicielem, a także nazwę zdarzenia, oddzielone kropką (.). Ponieważ nazwa zdarzenia jest kwalifikowana nazwą typu, będącego właścicielem, składnia dołączone zdarzenie umożliwia dowolne zdarzenie dołączonych do podłączenia do dowolnego elementu, który może być utworzone.  
  
 Na przykład Oto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] składnia dołączanie obsługi niestandardowych `NeedsCleaning` dołączone zdarzenie:  
  
 [!code-xaml[WPFAquariumSln#AE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Uwaga `aqua:` prefiks; prefiks jest niezbędne w tym przypadku ponieważ dołączone zdarzenie niestandardowe zdarzenie, które pochodzą z niestandardowych xmlns zamapowanego.  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Jak zdarzeń dołączonych implementuje WPF  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dołączone zdarzenia są wspierane przez <xref:System.Windows.RoutedEvent> pola, a następnie są przesyłane za pośrednictwem drzewa, po ich są wywoływane. Zazwyczaj źródłem dołączone zdarzenie (obiekt, który wywołuje zdarzenie) jest źródłem system lub usługę, a obiekt, który uruchamia kod, który wywołuje zdarzenie w związku z tym nie jest bezpośrednie częścią drzewa elementów.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scenariusze dotyczące zdarzenia dołączone  
 W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], dołączone zdarzenia znajdują się w niektórych obszarach funkcji w przypadku, gdy istnieje abstrakcji poziomu usług, takich jak zdarzenia włączone przez statyczną <xref:System.Windows.Input.Mouse> klasy lub <xref:System.Windows.Controls.Validation> klasy. Klasy, które interaktywnie lub korzystania z usługi można użyć zdarzenia w składni dołączone zdarzenie lub mogą wybierać uwidoczniony dołączone zdarzenie jako zdarzenie trasowane, który jest częścią jak klasa integruje się z funkcjami usługi.  
  
 Mimo że [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definiuje liczbę dołączone zdarzenia, scenariusze, w której będzie użycia lub uchwyt dołączone zdarzenie bezpośrednio są bardzo ograniczona. Ogólnie rzecz biorąc, pełni funkcję architektury dołączone zdarzenie, ale jest następnie przekazywany do niedołączonych (o [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzeń "otoki") zdarzenia trasowanego.  
  
 Na przykład podstawowa dołączone zdarzenie <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> więcej łatwo są obsługiwane w przypadku dowolnego danego <xref:System.Windows.UIElement> przy użyciu <xref:System.Windows.UIElement.MouseDown> na tym <xref:System.Windows.UIElement> zamiast rozwiązywania problemów związanych ze składnią dołączone zdarzenie albo w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] lub kodu. Dołączone zdarzenie pełni cel w architekturze, ponieważ zezwala ona na przyszłe rozszerzenia urządzenia wejściowego. Urządzenie hipotetyczny tylko musi zgłosić <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> w, aby symulować wejście myszy, a nie musi pochodzić od <xref:System.Windows.Input.Mouse> Aby to zrobić. Jednak ten scenariusz obejmuje kod obsługi zdarzeń, a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsługi dołączone zdarzenie nie została uwzględniona w tym scenariuszu.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Obsługa zdarzeń dołączonych w WPF  
 Proces obsługi dołączone zdarzenie, a kod procedury obsługi, który trzeba napisać, jest zasadniczo takie same jak dla zdarzenia trasowanego.  
  
 Ogólnie rzecz biorąc [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone zdarzenie nie jest bardzo różnią się od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia trasowanego. Różnice są, jak pochodzi zdarzenie oraz jego uwidaczniania przez klasę jako składową (która także ma wpływ na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Składnia programu obsługi).  
  
 Jednak jak wspomniano wcześniej, istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone zdarzenia nie są szczególnie przeznaczone do obsługi w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Częściej celem zdarzenia jest włączyć element złożone zgłosić stan elementu nadrzędnego w składania, w którym zdarzenie jest zazwyczaj zgłaszany w kodzie i również opiera się na obsługę w klasie nadrzędnej odpowiednie klasy. Na przykład elementów w obrębie <xref:System.Windows.Controls.Primitives.Selector> powinny zgłaszać dołączonego <xref:System.Windows.Controls.Primitives.Selector.Selected> zdarzenie, które jest następnie klasy obsługiwane przez <xref:System.Windows.Controls.Primitives.Selector> klasy, a następnie potencjalnie przekonwertowane przez <xref:System.Windows.Controls.Primitives.Selector> klasy do innego zdarzenia trasowanego <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Aby uzyskać więcej informacji na temat obsługi klasy i zdarzenia trasowane, zobacz [oznaczanie zdarzeń trasowanych jako Handled oraz obsługa klasy](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definiowanie zdarzeń dołączonych jako zdarzenia trasowanego  
 Jeśli są pochodząca z typowych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klas bazowych, dołączone zdarzenia można zaimplementować przy tym niektóre metody wzorca w klasie i za pomocą narzędzia metod, które zostały już znajduje się on na klas bazowych.  
  
 Wzorzec jest w następujący sposób:  
  
-   Metoda **Dodaj*EventName*obsługi** z dwoma parametrami. Pierwszy parametr musi ustalić zdarzenie, a zdarzeniu zidentyfikowani muszą odpowiadać nazwom z ***EventName*** w nazwie metody. Drugi parametr jest program obsługi do dodania. Metoda musi być `public` i `static`, bez wartości zwracanej.  
  
-   Metoda **Usuń*EventName*obsługi** z dwoma parametrami. Pierwszy parametr musi ustalić zdarzenie, a zdarzeniu zidentyfikowani muszą odpowiadać nazwom z ***EventName*** w nazwie metody. Drugi parametr jest obsługa do usunięcia. Metoda musi być `public` i `static`, bez wartości zwracanej.  
  
 **Dodaj*EventName*obsługi** metody dostępu ułatwia [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] podczas przetwarzania dołączone atrybuty są deklarowane w elemencie programu obsługi zdarzeń. **Dodaj*EventName*obsługi** i **Usuń*EventName*obsługi** metody umożliwiają również kod dostępu do magazynu programu obsługi zdarzeń dla dołączone zdarzenie.  
  
 Ten ogólny wzorzec nie jest jeszcze dokładne praktyczne implementacji w ramach, ponieważ dowolnej podanej [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] czytnika implementacji może mieć różne schematy do identyfikowania bazowego zdarzenia w pomocniczych języka i architektury. Jest to jedna z przyczyn, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzenia implementuje dołączonych jako zdarzenia trasowane; identyfikator na potrzeby zdarzenia (<xref:System.Windows.RoutedEvent>) został już zdefiniowany przez [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system zdarzeń. Ponadto routing zdarzeń jest rozszerzeniem implementacji fizycznych na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] poziomu języka koncepcji dołączone zdarzenie.  
  
 **Dodaj*EventName*obsługi** implementację [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone zdarzenie składa się z wywołaniem <xref:System.Windows.UIElement.AddHandler%2A> zdarzenia trasowanego i obsługi jako argumenty.  
  
 Ta strategia implementacji i systemu zdarzenia trasowanego ogólnie rzecz biorąc ograniczyć obsługę zdarzenia dołączone do albo <xref:System.Windows.UIElement> klas pochodnych lub <xref:System.Windows.ContentElement> pochodne klasy, ponieważ te mają tylko <xref:System.Windows.UIElement.AddHandler%2A> implementacji.  
  
 Na przykład, poniższy kod definiuje `NeedsCleaning` dołączone zdarzenie w klasie właściciela `Aquarium`przy użyciu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dołączone zdarzenia strategii deklarowania dołączone zdarzenie jako zdarzenie trasowane.  
  
 [!code-csharp[WPFAquariumSln#AECode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Należy pamiętać, że metoda ma być używany do ustanawiania pole identyfikatora dołączone zdarzenie <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>, jest faktycznie tej samej metody, które jest używane do rejestrowania zdarzenia trasowanego niedołączonych. Zdarzenia dołączone a zdarzenia trasowane wszystkie są rejestrowane do scentralizowanego magazynu wewnętrznego. Ta implementacja magazynu zdarzeń umożliwia uwagę koncepcyjny "zdarzenia, jak interfejs", opisanej w [Przegląd zdarzeń kierowane](../../../../docs/framework/wpf/advanced/routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Wywoływanie WPF dołączone zdarzenie  
 Zazwyczaj trzeba podnieść istniejące [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdefiniowane dołączone zdarzenia w kodzie. Te zdarzenia, wykonaj ogólne modelu koncepcyjnego "Usługa" i usługi takie jak klasy <xref:System.Windows.Input.InputManager> odpowiadają dla podnoszonego zdarzenia.  
  
 Jednak jeśli definiujesz dołączone zdarzenia niestandardowego na podstawie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zdarzeń dołączonych model oparty na <xref:System.Windows.RoutedEvent>, możesz użyć <xref:System.Windows.UIElement.RaiseEvent%2A> aby wywołać zdarzenie dołączonych za pomocą dowolnego <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>. Podnoszenie zdarzenia trasowanego (dołączone, lub nie) wymaga zadeklarujesz konkretnego elementu w drzewie elementów jako źródło zdarzenia; to źródło jest zgłaszana jako <xref:System.Windows.UIElement.RaiseEvent%2A> obiektu wywołującego. Określanie, który element jest zgłaszana jako źródła w drzewie odpowiada z usługą  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Szczegóły składni XAML](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)
- [Klasy XAML i niestandardowe dla WPF](../../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
