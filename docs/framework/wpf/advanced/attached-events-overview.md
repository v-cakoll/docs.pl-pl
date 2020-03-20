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
ms.openlocfilehash: e125c9a57090049f4319da96c7004f06606d0147
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141565"
---
# <a name="attached-events-overview"></a>Przegląd Załączone zdarzenia

Rozszerzalny język znaczników aplikacji (XAML) definiuje składnik języka i typ zdarzenia o nazwie *dołączone zdarzenie*. Koncepcja dołączonego zdarzenia umożliwia dodanie programu obsługi dla określonego zdarzenia do dowolnego elementu, a nie do elementu, który faktycznie definiuje lub dziedziczy zdarzenie. W takim przypadku ani obiekt potencjalnie wywoływania zdarzenia, ani wystąpienie obsługi docelowej definiuje lub w inny sposób "jest właścicielem" zdarzenia.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Wymagania wstępne  
 W tym temacie przyjęto założenie, że zapoznano się [z omówieniem zdarzeń routatrznych](routed-events-overview.md) i [przeglądem XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).  
  
<a name="Syntax"></a>
## <a name="attached-event-syntax"></a>Składnia dołączonego zdarzenia  
 Dołączone zdarzenia mają składnię XAML i wzorzec kodowania, który musi być używany przez kod zapasowy w celu obsługi użycia dołączonego zdarzenia.  
  
 W składni XAML dołączone zdarzenie jest określone nie tylko przez jego nazwę zdarzenia, ale przez jego typ posiadania plus nazwę zdarzenia, oddzielone kropką (.). Ponieważ nazwa zdarzenia jest kwalifikowana z nazwą jego typu posiadania, składnia dołączonego zdarzenia umożliwia dołączenia do każdego dołączonego zdarzenia do dowolnego elementu, który może zostać szesnasty.  
  
 Na przykład poniżej znajduje się składnia XAML dołączania `NeedsCleaning` programu obsługi dla niestandardowego zdarzenia dołączonego:  
  
 [!code-xaml[WPFAquariumSln#AE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquarium/Window1.xaml#ae)]  
  
 Zanotuj `aqua:` prefiks; prefiks jest konieczne w tym przypadku, ponieważ dołączone zdarzenie jest zdarzenie niestandardowe, które pochodzi z niestandardowych mapowane xmlns.  
  
<a name="WPFImplements"></a>
## <a name="how-wpf-implements-attached-events"></a>Jak implementuje w ramach WPF dołączone zdarzenia

W WPFWpfowania są wspierane <xref:System.Windows.RoutedEvent> przez pole i są kierowane przez drzewo po ich podniesiony. Zazwyczaj źródłem dołączonego zdarzenia (obiekt, który wywołuje zdarzenie) jest źródłem systemu lub usługi, a obiekt, który uruchamia kod, który wywołuje zdarzenie, nie jest zatem bezpośrednią częścią drzewa elementów.  
  
<a name="Scenarios"></a>
## <a name="scenarios-for-attached-events"></a>Scenariusze dla dołączonych zdarzeń  
 W WPFWUszone zdarzenia są obecne w niektórych obszarach funkcji, gdzie istnieje abstrakcja <xref:System.Windows.Input.Mouse> na poziomie <xref:System.Windows.Controls.Validation> usługi, takich jak dla zdarzeń włączonych przez klasę statyczną lub klasę. Klasy, które współdziałają z usługą lub korzystają z niej, mogą używać zdarzenia w składni dołączonego zdarzenia lub mogą wybrać powierzchnię dołączonego zdarzenia jako kierowanego zdarzenia, które jest częścią sposobu, w jaki klasa integruje możliwości usługi.  
  
 Chociaż WPF definiuje liczbę dołączonych zdarzeń, scenariusze, w których będzie można użyć lub obsłużyć dołączone zdarzenie bezpośrednio są bardzo ograniczone. Ogólnie rzecz biorąc dołączone zdarzenie służy ma na celu architektury, ale jest następnie przekazywane do nieprzyłączonego (kopii zapasowej ze zdarzeniem CLR "otoka") kierowane zdarzenie.  
  
 Na przykład podstawowe dołączone <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> zdarzenie może być łatwiej obsługiwane <xref:System.Windows.UIElement> na <xref:System.Windows.UIElement.MouseDown> dowolnym <xref:System.Windows.UIElement> podanym przy użyciu na tym, a nie do czynienia z dołączoną składnią zdarzeń w języku XAML lub kod. Dołączone zdarzenie służy celowi w architekturze, ponieważ pozwala na przyszłe rozszerzanie urządzeń wejściowych. Hipotetyczne urządzenie musiałoby tylko podnieść, <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> aby symulować wprowadzanie danych myszy i <xref:System.Windows.Input.Mouse> nie musiałoby się z tego prowadzać. Jednak ten scenariusz obejmuje obsługę kodu zdarzeń i obsługi XAML dołączonego zdarzenia nie jest istotne dla tego scenariusza.  
  
<a name="Handling"></a>
## <a name="handling-an-attached-event-in-wpf"></a>Obsługa dołączonego zdarzenia w WPF  
 Proces obsługi dołączonego zdarzenia i kod obsługi, który zostanie napisaniu, jest zasadniczo taki sam jak dla kierowanego zdarzenia.  
  
 Ogólnie rzecz biorąc WPF dołączone zdarzenie nie różni się bardzo od WPF kierowane zdarzenie. Różnice są jak zdarzenie jest pozyskiwane i jak jest narażony przez klasę jako element członkowski (co również wpływa na składnię programu obsługi XAML).  
  
 Jednak jak wspomniano wcześniej, istniejące zdarzenia dołączone do WPF nie są szczególnie przeznaczone do obsługi w WPF. Częściej celem zdarzenia jest włączenie kompozytowego elementu do raportowania stanu do elementu nadrzędnego w komponowaniu, w którym to przypadku zdarzenie jest zwykle wywoływane w kodzie, a także opiera się na obsłudze klasy w odpowiedniej klasie nadrzędnej. Na przykład elementy <xref:System.Windows.Controls.Primitives.Selector> w a oczekuje się <xref:System.Windows.Controls.Primitives.Selector.Selected> podnieść dołączone zdarzenie, które <xref:System.Windows.Controls.Primitives.Selector> jest następnie klasa obsługiwana przez klasę, a następnie potencjalnie konwertowane przez <xref:System.Windows.Controls.Primitives.Selector> klasę do innego zdarzenia kierowane, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>. Aby uzyskać więcej informacji na temat kierowanych zdarzeń i obsługi klas, zobacz [Oznaczanie zdarzeń kierowanych jako obsługiwane i Obsługa klas](marking-routed-events-as-handled-and-class-handling.md).  
  
<a name="Custom"></a>
## <a name="defining-your-own-attached-events-as-routed-events"></a>Definiowanie własnych dołączonych zdarzeń jako zdarzeń trasowanych  
 Jeśli pochodzą z typowych klas podstawowych WPF, można zaimplementować własne dołączone zdarzenia, w tym niektórych metod wzorca w klasie i przy użyciu metod narzędzia, które są już obecne w klasach podstawowych.  
  
 Wzór jest następujący:  
  
- Metoda __Dodaj*program obsługi nazwy zdarzenia*__ z dwoma parametrami. Pierwszy parametr jest wystąpieniem, do którego jest dodawany program obsługi zdarzeń. Drugi parametr jest program obsługi zdarzeń, aby dodać. Metoda musi `public` być `static`i , bez wartości zwracanej.  
  
- Metoda __Usuń program obsługi*nazwy zdarzenia*__ z dwoma parametrami. Pierwszy parametr jest wystąpienie, z którego program obsługi zdarzeń jest usuwany. Drugi parametr jest program obsługi zdarzeń do usunięcia. Metoda musi `public` być `static`i , bez wartości zwracanej.  
  
 Add __*EventName*Handler__ metody ułatwia przetwarzanie XAML, gdy dołączone atrybuty obsługi zdarzeń są zadeklarowane na element. Metody __Dodaj program obsługi*i*__ usuń obsługę __*zdarzeń*__ również włączyć dostęp do kodu do magazynu obsługi zdarzeń dla dołączonego zdarzenia.  
  
 Ten ogólny wzorzec nie jest jeszcze wystarczająco precyzyjne dla praktycznej implementacji w ramach, ponieważ każda implementacja czytnika XAML może mieć różne schematy do identyfikowania podstawowych zdarzeń w języku i architekturze obsługi. Jest to jeden z powodów, dla których WPF implementuje dołączone zdarzenia jako kierowane zdarzenia; identyfikator do użycia dla zdarzenia<xref:System.Windows.RoutedEvent>( ) jest już zdefiniowany przez system zdarzeń WPF. Ponadto routing zdarzenia jest naturalnym rozszerzeniem implementacji na poziomie języka XAML koncepcji dołączonego zdarzenia.  
  
 Implementacja __Dodaj program obsługi zdarzenia*Dla*__ zdarzenia dołączonego <xref:System.Windows.UIElement.AddHandler%2A> WPF WPF składa się z wywoływania z kierowanego zdarzenia i obsługi jako argumenty.  
  
 Ta strategia implementacji i kierowane systemu zdarzeń w ogóle <xref:System.Windows.UIElement> ograniczyć obsługę <xref:System.Windows.ContentElement> dołączonych zdarzeń do klas <xref:System.Windows.UIElement.AddHandler%2A> pochodnych lub klas pochodnych, ponieważ tylko te klasy mają implementacje.  
  
 Na przykład poniższy kod `NeedsCleaning` definiuje dołączone zdarzenie w `Aquarium`klasie właściciela , przy użyciu strategii zdarzenia dołączone WPF deklarowania dołączone zdarzenie jako zdarzenie routowane.  
  
 [!code-csharp[WPFAquariumSln#AECode](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#aecode)]
 [!code-vb[WPFAquariumSln#AECode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#aecode)]  
  
 Należy zauważyć, że metoda używana do ustanowienia <xref:System.Windows.EventManager.RegisterRoutedEvent%2A>dołączonego pola identyfikatora zdarzenia, jest w rzeczywistości tą samą metodą, która jest używana do rejestrowania nieprzyłączonego zdarzenia kierowanego. Dołączone zdarzenia i kierowane zdarzenia są rejestrowane w scentralizowanym magazynie wewnętrznym. Ta implementacja magazynu zdarzeń umożliwia "zdarzenia jako interfejs" uwagę koncepcyjną, która jest omówiona w [Przeglądzie zdarzeń routowanych.](routed-events-overview.md)  
  
<a name="Raising"></a>
## <a name="raising-a-wpf-attached-event"></a>Podnoszenie WPF Dołączone zdarzenie  
 Zazwyczaj nie trzeba podnieść istniejące zdarzenia dołączone zdefiniowane w UPF z kodu. Zdarzenia te są zgodne z ogólnym modelem koncepcyjnym "usługi" i klas usług, takich jak <xref:System.Windows.Input.InputManager> są odpowiedzialne za podnoszenie zdarzeń.  
  
 Jeśli jednak definiujesz niestandardowe dołączone zdarzenie na podstawie modelu WPF opartego <xref:System.Windows.RoutedEvent>na dołączonych zdarzeniach, można użyć <xref:System.Windows.UIElement.RaiseEvent%2A> do podniesienia dołączonego zdarzenia z dowolnego <xref:System.Windows.UIElement> lub <xref:System.Windows.ContentElement>. Wywoływanie kierowane zdarzenie (dołączone lub nie) wymaga zadeklarowania określonego elementu w drzewie elementów jako źródła zdarzenia; to źródło jest <xref:System.Windows.UIElement.RaiseEvent%2A> zgłaszane jako wywołujący. Określenie, który element jest zgłaszany jako źródło w drzewie, jest obowiązkiem usługi  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd Zdarzenia trasowane](routed-events-overview.md)
- [Szczegóły składni XAML](xaml-syntax-in-detail.md)
- [Klasy XAML i niestandardowe dla WPF](xaml-and-custom-classes-for-wpf.md)
