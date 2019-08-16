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
ms.openlocfilehash: 40e7bd34388bec06cd8a7c3610599d814aef101f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038155"
---
# <a name="attached-events-overview"></a>Przegląd Załączone zdarzenia

Extensible Application Markup Language (XAML) definiuje składnik języka i typ zdarzenia zwanego załączonym *zdarzeniem*. Koncepcja dołączonego zdarzenia umożliwia dodanie procedury obsługi dla danego zdarzenia do dowolnego elementu, a nie do elementu, który faktycznie definiuje lub dziedziczy zdarzenie. W takim przypadku ani obiekt, który potencjalnie nie może podnieść zdarzenia, ani docelowego wystąpienia obsługi definiuje lub w inny sposób "właścicielem" zdarzenia.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie założono, że masz [przegląd zdarzeń kierowanych](routed-events-overview.md) do odczytu i [Przegląd XAML (WPF)](xaml-overview-wpf.md).  
  
<a name="Syntax"></a>   
## <a name="attached-event-syntax"></a>Składnia dołączonego zdarzenia  
 Dołączone zdarzenia mają składnię języka XAML oraz wzorzec kodowania, który musi być używany przez kod zapasowy w celu obsługi dołączonego użycia zdarzenia.  
  
 W składni XAML, dołączone zdarzenie jest określone nie tylko przez jego nazwę zdarzenia, ale przez jego typ, a także nazwę zdarzenia, oddzieloną kropką (.). Ze względu na to, że nazwa zdarzenia jest kwalifikowana nazwą jego typu będącego właścicielem, podłączona składnia zdarzenia umożliwia dołączenie dowolnego dołączonego zdarzenia do dowolnego elementu, który można utworzyć wystąpienie.  
  
 Na przykład poniżej przedstawiono składnię XAML służącą do dołączania obsługi dla niestandardowego `NeedsCleaning` zdarzenia dołączonego:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Zwróć uwagę na prefiks; prefiks jest wymagany w tym przypadku, ponieważ dołączone zdarzenie jest zdarzeniem niestandardowym, które pochodzi z niestandardowego zamapowanego xmlns. `aqua:`  
  
<a name="WPFImplements"></a>   
## <a name="how-wpf-implements-attached-events"></a>Jak WPF implementuje dołączone zdarzenia

W WPF dołączone zdarzenia są obsługiwane przez <xref:System.Windows.RoutedEvent> pole i są kierowane przez drzewo po ich podniesieniu. Zazwyczaj źródłem dołączonego zdarzenia (obiektu, który wywołuje zdarzenie) jest system lub źródło usługi, a obiekt, który uruchamia kod, który wywołuje zdarzenie, nie jest częścią drzewa elementu.  
  
<a name="Scenarios"></a>   
## <a name="scenarios-for-attached-events"></a>Scenariusze dotyczące zdarzeń załączonych  
 W WPF dołączone zdarzenia są obecne w niektórych obszarach funkcji, w których istnieje Abstrakcja na poziomie usług, na przykład dla zdarzeń włączonych przez klasę statyczną <xref:System.Windows.Input.Mouse> <xref:System.Windows.Controls.Validation> lub klasę. Klasy, które współdziałają z usługą lub używają usługi, mogą albo użyć zdarzenia w składni dołączonego zdarzenia, albo mogą zdecydować się na załączenie dołączonego zdarzenia jako zdarzenia kierowanego, które jest częścią sposobu integracji możliwości usługi przez klasę.  
  
 Chociaż WPF definiuje wiele załączonych zdarzeń, scenariusze, w których będzie można użyć lub obsłużyć dołączone zdarzenie, są bardzo ograniczone. Ogólnie rzecz biorąc, dołączone zdarzenie służy do zastosowania architektury, ale jest następnie przekazywane do niedołączonego (przy użyciu zdarzenia CLR "otoka").  
  
 Na przykład, <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> bazowe dołączone zdarzenie może być łatwiej obsługiwane na <xref:System.Windows.UIElement> dowolnym z nich przy użyciu <xref:System.Windows.UIElement.MouseDown> , które <xref:System.Windows.UIElement> nie jest związane z załączoną składnią zdarzenia w języku XAML lub kodzie. Dołączone zdarzenie służy do osiągnięcia celu w architekturze, ponieważ pozwala na przyszłe rozszerzanie urządzeń wejściowych. Hipotetyczne urządzenie będzie musiało zostać podniesione <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> tylko w celu symulowania danych wejściowych myszy i nie musi pochodzić od <xref:System.Windows.Input.Mouse> tego do. Jednak ten scenariusz obejmuje obsługę kodu zdarzeń, a obsługa XAML dołączonego zdarzenia nie ma znaczenia dla tego scenariusza.  
  
<a name="Handling"></a>   
## <a name="handling-an-attached-event-in-wpf"></a>Obsługa dołączonego zdarzenia w WPF  
 Proces obsługi dołączonego zdarzenia oraz kod programu obsługi, który zostanie zapisany, jest zasadniczo taki sam jak w przypadku zdarzenia kierowanego.  
  
 Ogólnie rzecz biorąc, dołączone zdarzenie WPF nie różni się od zdarzenia trasowanego WPF. Różnice polegają na tym, jak Źródło zdarzenia i jak są udostępniane przez klasę jako element członkowski (co również ma wpływ na składnię procedury obsługi XAML).  
  
 Jednak jak wspomniano wcześniej, istniejące zdarzenia dołączone do platformy WPF nie są szczególnie przeznaczone do obsługi w WPF. Często celem zdarzenia jest włączenie elementu złożonego do raportowania stanu do elementu nadrzędnego w ramach składania, w którym to przypadku zdarzenie jest zwykle wywoływane w kodzie i opiera się na obsłudze klas w odpowiedniej klasie nadrzędnej. Na <xref:System.Windows.Controls.Primitives.Selector> przykład elementy w obrębie są oczekiwane na podnoszenie dołączonego <xref:System.Windows.Controls.Primitives.Selector.Selected> zdarzenia, które <xref:System.Windows.Controls.Primitives.Selector> następnie są obsługiwane przez klasę, a następnie mogą być konwertowane przez <xref:System.Windows.Controls.Primitives.Selector> klasę w inne zdarzenia kierowane, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> . Aby uzyskać więcej informacji o rutowanych zdarzeniach i obsłudze klas, zobacz [oznaczanie zdarzeń kierowanych jako obsłużone i obsługa klas](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>   
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definiowanie własnych załączonych zdarzeń jako zdarzeń kierowanych  
 Jeśli pochodzą ze wspólnych klas bazowych WPF, można zaimplementować własne dołączone zdarzenia przez dołączenie określonych metod wzorca w klasie oraz przy użyciu metod narzędziowych, które są już obecne w klasach bazowych.  
  
 Wzorzec jest następujący:  
  
- __Procedura Add*EventName*__ z dwoma parametrami. Pierwszy parametr jest wystąpieniem, do którego zostanie dodana procedura obsługi zdarzeń. Drugi parametr jest programem obsługi zdarzeń, który ma zostać dodany. Metoda musi być `public` i `static`bez zwracanej wartości.  
  
- __Procedura usuwania metody*EventName*__ z dwoma parametrami. Pierwszy parametr to wystąpienie, z którego jest usuwana procedura obsługi zdarzeń. Drugi parametr jest programem obsługi zdarzeń do usunięcia. Metoda musi być `public` i `static`bez zwracanej wartości.  
  
 Metoda dostępu do __procedury obsługi Dodaj*EventName*__ ułatwia przetwarzanie kodu XAML, gdy atrybuty programu obsługi zdarzeń dołączone są zadeklarowane w elemencie. Metody obsługi __Dodaj*EventName*__ i __Remove*EventName*__ umożliwiają również dostęp kodu do magazynu obsługi zdarzeń dla dołączonego zdarzenia.  
  
 Ten ogólny wzorzec nie jest jeszcze wystarczająco precyzyjny dla praktycznej implementacji w strukturze, ponieważ każda implementacja czytnika XAML może mieć różne schematy do identyfikowania podstawowych zdarzeń w języku i architekturze pomocniczej. Jest to jedna z powodów, w których WPF implementuje dołączone zdarzenia jako zdarzenia kierowane; Identyfikator do użycia dla zdarzenia (<xref:System.Windows.RoutedEvent>) jest już zdefiniowany przez system zdarzeń WPF. Ponadto kierowanie zdarzenia jest naturalnym rozszerzeniem implementacji na koncepcji poziomu języka XAML dołączonego zdarzenia.  
  
 Implementacja __programuobsługi Dodaj EventName__ dla zdarzenia dołączonego do platformy WPF składa <xref:System.Windows.UIElement.AddHandler%2A> się z wywołania z użyciem zdarzenia i procedury obsługi routingu jako argumentów.  
  
 Ta strategia implementacji i system zdarzeń kierowanych w ramach ogólnego ograniczenia obsługi dla dołączonych zdarzeń <xref:System.Windows.UIElement> do klas pochodnych <xref:System.Windows.ContentElement> lub klas pochodnych, ponieważ tylko te klasy <xref:System.Windows.UIElement.AddHandler%2A> mają implementacje.  
  
 Na przykład poniższy kod definiuje `NeedsCleaning` dołączone zdarzenie w klasie `Aquarium`Owner przy użyciu strategii zdarzeń dołączonej WPF w celu zadeklarowania dołączonego zdarzenia jako zdarzenia kierowanego.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Należy zauważyć, że metoda użyta do ustanowienia pola <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>identyfikatora dołączonego zdarzenia, jest w rzeczywistości tą samą metodą, która jest używana do rejestrowania niedołączonego zdarzenia kierowanego. Zdarzenia dołączone i zdarzenia kierowane są rejestrowane w scentralizowanym magazynie wewnętrznym. Ta implementacja magazynu zdarzeń umożliwia zagadnienia dotyczące pojęć "zdarzenia jako interfejs" omówione w temacie [Omówienie zdarzeń kierowanych](routed-events-overview.md).  
  
<a name="Raising"></a>   
## <a name="raising-a-wpf-attached-event"></a>Wywoływanie zdarzenia dołączonego do platformy WPF  
 Zazwyczaj nie trzeba zgłaszać istniejących zdarzeń, które zostały dołączone przez WPF z kodu. Te zdarzenia są zgodne z ogólnym modelem koncepcyjnym "usługa", a <xref:System.Windows.Input.InputManager> klasy usług, takie jak są odpowiedzialne za podnoszenie poziomu zdarzeń.  
  
 Jednak w przypadku definiowania niestandardowego zdarzenia dołączonego na podstawie <xref:System.Windows.RoutedEvent>modelu WPF z załączonych zdarzeń w programie można użyć <xref:System.Windows.UIElement.RaiseEvent%2A> , aby zgłosić dołączone zdarzenie z dowolnego <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>. Podnoszenie zdarzenia kierowanego (dołączonego lub nie) wymaga zadeklarowania określonego elementu w drzewie elementów jako źródła zdarzenia; to źródło jest zgłaszane jako <xref:System.Windows.UIElement.RaiseEvent%2A> obiekt wywołujący. Określenie, który element jest raportowany jako źródło w drzewie, jest odpowiedzialnością usługi  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
