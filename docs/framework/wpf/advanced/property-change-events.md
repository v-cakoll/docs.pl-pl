---
title: Zdarzenia zmiany właściwości
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], change events
- property value changes [WPF]
- change events [WPF], property
- events [WPF], change in property values
- creating property triggers [WPF]
- property change events [WPF], types of
- property change events [WPF]
- property triggers [WPF]
- identifying changed property events [WPF]
- property triggers [WPF], definition of
ms.assetid: 0a7989df-9674-4cc1-bc50-5d8ef5d9c055
ms.openlocfilehash: f8d0d5e65101ffda0edaaeabdea2870287ba0f1f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400843"
---
# <a name="property-change-events"></a>Zdarzenia zmiany właściwości
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]definiuje kilka zdarzeń, które są wywoływane w odpowiedzi na zmianę wartości właściwości. Często właściwość jest właściwością zależności. Wydarzenie jest czasami zdarzeniem kierowanym i czasami jest to standardowe zdarzenie środowiska uruchomieniowego języka wspólnego (CLR). Definicja zdarzenia różni się w zależności od scenariusza, ponieważ niektóre zmiany właściwości są bardziej odpowiednio kierowane przez drzewo elementów, podczas gdy inne zmiany właściwości są zwykle tylko dla obiektu, w którym zmieniono właściwość.  
  
## <a name="identifying-a-property-change-event"></a>Identyfikowanie zdarzenia zmiany właściwości  
 Nie wszystkie zdarzenia, które raportują zmianę właściwości, są jawnie identyfikowane jako zdarzenie zmiany właściwości, na podstawie wzorca podpisu lub wzorca nazewnictwa. Ogólnie rzecz biorąc, opis zdarzenia w [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] dokumentacji wskazuje, czy zdarzenie jest bezpośrednio powiązane ze zmianą wartości właściwości i zawiera odsyłacze między właściwością i zdarzeniem.  
  
### <a name="routedpropertychanged-events"></a>RoutedPropertyChanged Events  
 Niektóre zdarzenia używają typu danych zdarzenia i delegatów, które są jawnie używane do zdarzeń zmiany właściwości. Typem danych zdarzenia jest <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, a delegatem jest. <xref:System.Windows.RoutedPropertyChangedEventHandler%601> Dane zdarzenia i Delegaty mają parametr typu ogólnego, który służy do określania rzeczywistego typu właściwości zmiany podczas definiowania programu obsługi. Dane zdarzenia zawierają dwie właściwości, <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> a <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>następnie, które następnie są przesyłane jako argument typu w danych zdarzenia.  
  
 Część "kierowana" nazwy wskazuje, że zdarzenie zmiany właściwości jest rejestrowane jako zdarzenie trasowane. Zaletą routingu zdarzenia zmiany właściwości jest to, że najwyższego poziomu kontrolki może odbierać zdarzenia zmiany właściwości, jeśli właściwości elementów podrzędnych (części złożone kontrolki) zmieniają wartości. Na przykład można utworzyć formant, który zawiera <xref:System.Windows.Controls.Primitives.RangeBase> kontrolkę, taką <xref:System.Windows.Controls.Slider>jak. Jeśli wartość <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> właściwości zostanie zmieniona w części suwaka, możesz chcieć obsłużyć tę zmianę w formancie nadrzędnym, a nie na części.  
  
 Ze względu na to, że masz starą wartość i nową wartość, może być skłonny do użycia tego programu obsługi zdarzeń jako modułu sprawdzania poprawności dla wartości właściwości. Jednak to nie jest zamiarem projektu dla większości zdarzeń zmienionych właściwości. Ogólnie rzecz biorąc są podane wartości, dzięki czemu można działać na tych wartościach w innych obszarach logiki kodu, ale w związku z tym zmiana wartości z programu obsługi zdarzeń nie jest zalecana i może spowodować niezamierzone rekursję w zależności od sposobu implementacji programu obsługi .  
  
 Jeśli właściwość jest niestandardową właściwością zależności lub pracujesz z klasą pochodną, w której został zdefiniowany kod tworzenia wystąpienia, istnieje znacznie lepszy mechanizm śledzenia zmian właściwości, które są wbudowane w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system właściwości: wywołania zwrotne <xref:System.Windows.CoerceValueCallback> systemu właściwości <xref:System.Windows.PropertyChangedCallback>i. Aby uzyskać więcej informacji na temat sprawdzania poprawności i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wymuszania przy użyciu systemu właściwości, zobacz [wywołania zwrotne właściwości zależności i walidacja](dependency-property-callbacks-and-validation.md) oraz [niestandardowe właściwości zależności](custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged Events  
 Inna para typów, które są częścią scenariusza zdarzenia zmiany właściwości, to <xref:System.Windows.DependencyPropertyChangedEventArgs> i <xref:System.Windows.DependencyPropertyChangedEventHandler>. Zdarzenia dotyczące tych zmian właściwości nie są kierowane; są to standardowe zdarzenia CLR. <xref:System.Windows.DependencyPropertyChangedEventArgs>jest nietypowym typem raportowania danych zdarzeń, ponieważ nie pochodzi on <xref:System.EventArgs>od; <xref:System.Windows.DependencyPropertyChangedEventArgs> jest strukturą, a nie klasą.  
  
 Zdarzenia, które <xref:System.Windows.DependencyPropertyChangedEventArgs> używają <xref:System.Windows.DependencyPropertyChangedEventHandler> i są nieco bardziej typowe `RoutedPropertyChanged` niż zdarzenia. Przykładem zdarzenia, które korzysta z tych typów jest <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Podobnie <xref:System.Windows.RoutedPropertyChangedEventArgs%601>jak <xref:System.Windows.DependencyPropertyChangedEventArgs> w przypadku zgłaszania starej i nowej wartości właściwości. Należy również wziąć pod uwagę to, co można zrobić z wartościami; zazwyczaj nie zaleca się, aby ponownie spróbować zmienić wartości w nadawcy w odpowiedzi na zdarzenie.  
  
## <a name="property-triggers"></a>Wyzwalacze właściwości  
 Ściśle powiązane koncepcje dla zdarzenia zmiany właściwości jest wyzwalaczem właściwości. Wyzwalacz właściwości jest tworzony w ramach stylu lub szablonu i umożliwia tworzenie zachowań warunkowych na podstawie wartości właściwości, w której jest przypisany wyzwalacz właściwości.  
  
 Właściwość wyzwalacza właściwości musi być właściwością zależności. Może to być (i często) właściwość zależności tylko do odczytu. Dobrym wskaźnikiem, że właściwość zależności uwidoczniona przez formant jest co najmniej częściowo zaprojektowana jako wyzwalacz właściwości, to jeśli nazwa właściwości zaczyna się od "is". Właściwości, które mają takie nazewnictwo, są często właściwością zależności logicznej tylko do odczytu, w której głównym scenariuszem dla właściwości jest stan kontroli raportowania, który może mieć konsekwencje dla interfejsu użytkownika w czasie rzeczywistym i jest w ten sposób wyzwoleniem na kandydata.  
  
 Niektóre z tych właściwości mają również dedykowane zdarzenie zmiany właściwości. Na przykład właściwość <xref:System.Windows.UIElement.IsMouseCaptured%2A> ma zdarzenie <xref:System.Windows.UIElement.IsMouseCapturedChanged>zmiany właściwości. Sama właściwość jest tylko do odczytu, a jej wartość jest ustawiana przez system wejściowy, a system wejściowy <xref:System.Windows.UIElement.IsMouseCapturedChanged> zgłasza wszystkie zmiany w czasie rzeczywistym.  
  
 W porównaniu do rzeczywistego zdarzenia zmiany właściwości, użycie wyzwalacza właściwości do działania na zmianie właściwości ma pewne ograniczenia.  
  
 Wyzwalacze właściwości działają przez dokładną logikę dopasowywania. Należy określić właściwość i wartość, która wskazuje konkretną wartość, dla której wyzwalacz będzie działać. Na przykład: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Ze względu na to ograniczenie większość użycia wyzwalacza właściwości będzie dotyczyć właściwości logicznych lub właściwości, które mają dedykowaną wartość wyliczenia, gdzie możliwe jest, że możliwy do zarządzania zakresem wartości, aby zdefiniować wyzwalacz dla każdego przypadku. Wyzwalacze właściwości lub mogą istnieć tylko w przypadku wartości specjalnych, takich jak gdy liczba elementów osiągnie zero, a nie będzie wyzwalaczem dla przypadków, gdy wartość właściwości zmieni się z powrotem od zera (zamiast wyzwalaczy we wszystkich przypadkach, konieczne może być kod Procedura obsługi zdarzeń w tym miejscu lub domyślne zachowanie, które przełącza ponownie z stanu wyzwalacza, gdy wartość jest różna od zera.  
  
 Składnia wyzwalacza właściwości jest analogiczna do instrukcji "If" w programowaniu. Jeśli warunek wyzwalacza ma wartość true, wówczas "treść" wyzwalacza właściwości jest "wykonane". "Treść" wyzwalacza właściwości nie jest kodem, jest znacznikiem. Ten znacznik jest ograniczony do korzystania z co najmniej <xref:System.Windows.Setter> jednego elementu, aby ustawić inne właściwości obiektu, w którym jest stosowany styl lub szablon.  
  
 Aby przesunąć warunek "If" wyzwalacza właściwości, który ma szeroką gamę możliwych wartości, zazwyczaj zaleca się ustawienie tej samej wartości właściwości na wartość domyślną przy użyciu <xref:System.Windows.Setter>. W <xref:System.Windows.Trigger> ten sposób zawarte metody ustawiające mają pierwszeństwo, gdy warunek wyzwalacza ma wartość true <xref:System.Windows.Setter> , a element <xref:System.Windows.Trigger> , który nie znajduje się w elemencie, będzie miał pierwszeństwo za każdym razem, gdy warunek wyzwalacza ma wartość false.  
  
 Wyzwalacze właściwości są zwykle odpowiednie dla scenariuszy, w których co najmniej jedna Właściwość wyglądu powinna się zmieniać, na podstawie stanu innej właściwości w tym samym elemencie.  
  
 Aby dowiedzieć się więcej na temat wyzwalaczy właściwości, zobacz [Style i tworzenia szablonów](../controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
