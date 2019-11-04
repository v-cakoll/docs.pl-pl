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
ms.openlocfilehash: 68be4c6bf7cce8a3aeb928e1f0b0e8131263320c
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459344"
---
# <a name="property-change-events"></a>Zdarzenia zmiany właściwości
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] definiuje kilka zdarzeń, które są wywoływane w odpowiedzi na zmianę wartości właściwości. Często właściwość jest właściwością zależności. Wydarzenie jest czasami zdarzeniem kierowanym i czasami jest to standardowe zdarzenie środowiska uruchomieniowego języka wspólnego (CLR). Definicja zdarzenia różni się w zależności od scenariusza, ponieważ niektóre zmiany właściwości są bardziej odpowiednio kierowane przez drzewo elementów, podczas gdy inne zmiany właściwości są zwykle tylko dla obiektu, w którym zmieniono właściwość.  
  
## <a name="identifying-a-property-change-event"></a>Identyfikowanie zdarzenia zmiany właściwości  
 Nie wszystkie zdarzenia, które raportują zmianę właściwości, są jawnie identyfikowane jako zdarzenie zmiany właściwości, na podstawie wzorca podpisu lub wzorca nazewnictwa. Ogólnie rzecz biorąc, opis zdarzenia w dokumentacji zestawu SDK wskazuje, czy zdarzenie jest bezpośrednio powiązane ze zmianą wartości właściwości i zawiera odsyłacze między właściwością i zdarzeniem.  
  
### <a name="routedpropertychanged-events"></a>Zdarzenia RoutedPropertyChanged  
 Niektóre zdarzenia używają typu danych zdarzenia i delegatów, które są jawnie używane do zdarzeń zmiany właściwości. Typ danych zdarzenia to <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, a delegat jest <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Dane zdarzenia i Delegaty mają parametr typu ogólnego, który służy do określania rzeczywistego typu właściwości zmiany podczas definiowania programu obsługi. Dane zdarzenia zawierają dwie właściwości, <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> i <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, które są następnie przenoszone jako argument typu w danych zdarzenia.  
  
 Część "kierowana" nazwy wskazuje, że zdarzenie zmiany właściwości jest rejestrowane jako zdarzenie trasowane. Zaletą routingu zdarzenia zmiany właściwości jest to, że najwyższego poziomu kontrolki może odbierać zdarzenia zmiany właściwości, jeśli właściwości elementów podrzędnych (części złożone kontrolki) zmieniają wartości. Na przykład można utworzyć formant, który zawiera kontrolkę <xref:System.Windows.Controls.Primitives.RangeBase>, taką jak <xref:System.Windows.Controls.Slider>. Jeśli wartość właściwości <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zostanie zmieniona w części suwaka, warto obsłużyć tę zmianę w formancie nadrzędnym, a nie na części.  
  
 Ze względu na to, że masz starą wartość i nową wartość, może być skłonny do użycia tego programu obsługi zdarzeń jako modułu sprawdzania poprawności dla wartości właściwości. Jednak to nie jest zamiarem projektu dla większości zdarzeń zmienionych właściwości. Ogólnie rzecz biorąc są podane wartości, dzięki czemu można działać na tych wartościach w innych obszarach logiki kodu, ale w związku z tym zmiana wartości z programu obsługi zdarzeń nie jest zalecana i może spowodować niezamierzone rekursję w zależności od sposobu implementacji programu obsługi .  
  
 Jeśli właściwość jest niestandardową właściwością zależności lub pracujesz z klasą pochodną, w której został zdefiniowany kod tworzenia wystąpienia, istnieje znacznie lepszy mechanizm śledzenia zmian właściwości, które są wbudowane w system właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: Właściwość wywołania zwrotne systemu <xref:System.Windows.CoerceValueCallback> i <xref:System.Windows.PropertyChangedCallback>. Aby uzyskać więcej informacji na temat sprawdzania poprawności i wymuszania przy użyciu systemu właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], zobacz [wywołania zwrotne właściwości zależności i walidacja](dependency-property-callbacks-and-validation.md) oraz [niestandardowe właściwości zależności](custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>Zdarzenia DependencyPropertyChanged  
 Inna para typów będących częścią scenariusza zdarzenia zmiany właściwości jest <xref:System.Windows.DependencyPropertyChangedEventArgs> i <xref:System.Windows.DependencyPropertyChangedEventHandler>. Zdarzenia dotyczące tych zmian właściwości nie są kierowane; są to standardowe zdarzenia CLR. <xref:System.Windows.DependencyPropertyChangedEventArgs> jest nietypowym typem raportowania danych zdarzeń, ponieważ nie pochodzi on od <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> jest strukturą, a nie klasą.  
  
 Zdarzenia, które używają <xref:System.Windows.DependencyPropertyChangedEventArgs> i <xref:System.Windows.DependencyPropertyChangedEventHandler>, są nieco bardziej typowe niż zdarzenia `RoutedPropertyChanged`. Przykład zdarzenia, które używa tych typów, jest <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Podobnie jak <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> również raportuje starą i nową wartość właściwości. Należy również wziąć pod uwagę to, co można zrobić z wartościami; zazwyczaj nie zaleca się, aby ponownie spróbować zmienić wartości w nadawcy w odpowiedzi na zdarzenie.  
  
## <a name="property-triggers"></a>Wyzwalacze właściwości  
 Ściśle powiązane koncepcje dla zdarzenia zmiany właściwości jest wyzwalaczem właściwości. Wyzwalacz właściwości jest tworzony w ramach stylu lub szablonu i umożliwia tworzenie zachowań warunkowych na podstawie wartości właściwości, w której jest przypisany wyzwalacz właściwości.  
  
 Właściwość wyzwalacza właściwości musi być właściwością zależności. Może to być (i często) właściwość zależności tylko do odczytu. Dobrym wskaźnikiem, że właściwość zależności uwidoczniona przez formant jest co najmniej częściowo zaprojektowana jako wyzwalacz właściwości, to jeśli nazwa właściwości zaczyna się od "is". Właściwości, które mają takie nazewnictwo, są często właściwością zależności logicznej tylko do odczytu, w której głównym scenariuszem dla właściwości jest stan kontroli raportowania, który może mieć konsekwencje dla interfejsu użytkownika w czasie rzeczywistym i jest w ten sposób wyzwoleniem na kandydata.  
  
 Niektóre z tych właściwości mają również dedykowane zdarzenie zmiany właściwości. Na przykład właściwość <xref:System.Windows.UIElement.IsMouseCaptured%2A> ma <xref:System.Windows.UIElement.IsMouseCapturedChanged>zdarzenia zmiany właściwości. Sama właściwość jest tylko do odczytu, a jej wartość jest ustawiana przez system wejściowy, a system wejściowy podnosi <xref:System.Windows.UIElement.IsMouseCapturedChanged> na każdą zmianę w czasie rzeczywistym.  
  
 W porównaniu do rzeczywistego zdarzenia zmiany właściwości, użycie wyzwalacza właściwości do działania na zmianie właściwości ma pewne ograniczenia.  
  
 Wyzwalacze właściwości działają przez dokładną logikę dopasowywania. Należy określić właściwość i wartość, która wskazuje konkretną wartość, dla której wyzwalacz będzie działać. Na przykład: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Ze względu na to ograniczenie większość użycia wyzwalacza właściwości będzie dotyczyć właściwości logicznych lub właściwości, które mają dedykowaną wartość wyliczenia, gdzie możliwe jest, że możliwy do zarządzania zakresem wartości, aby zdefiniować wyzwalacz dla każdego przypadku. Wyzwalacze właściwości lub mogą istnieć tylko w przypadku wartości specjalnych, takich jak gdy liczba elementów osiągnie zero, a nie będzie wyzwalaczem dla przypadków, gdy wartość właściwości zmieni się z powrotem od zera (zamiast wyzwalaczy we wszystkich przypadkach, konieczne może być kod Procedura obsługi zdarzeń w tym miejscu lub domyślne zachowanie, które przełącza ponownie z stanu wyzwalacza, gdy wartość jest różna od zera.  
  
 Składnia wyzwalacza właściwości jest analogiczna do instrukcji "If" w programowaniu. Jeśli warunek wyzwalacza ma wartość true, wówczas "treść" wyzwalacza właściwości jest "wykonane". "Treść" wyzwalacza właściwości nie jest kodem, jest znacznikiem. To oznakowanie jest ograniczone do użycia co najmniej jednego elementu <xref:System.Windows.Setter>, aby ustawić inne właściwości obiektu, w którym jest stosowany styl lub szablon.  
  
 Aby przesunąć warunek "If" wyzwalacza właściwości, który ma szeroką gamę możliwych wartości, zazwyczaj zaleca się ustawienie tej samej wartości właściwości na wartość domyślną przy użyciu <xref:System.Windows.Setter>. W ten sposób <xref:System.Windows.Trigger> zawartej metody ustawiającej będzie mieć pierwszeństwo, gdy warunek wyzwalacza ma wartość true, a <xref:System.Windows.Setter>, która nie znajduje się w <xref:System.Windows.Trigger> będzie miał pierwszeństwo za każdym razem, gdy warunek wyzwalacza ma wartość false.  
  
 Wyzwalacze właściwości są zwykle odpowiednie dla scenariuszy, w których co najmniej jedna Właściwość wyglądu powinna się zmieniać, na podstawie stanu innej właściwości w tym samym elemencie.  
  
 Aby dowiedzieć się więcej na temat wyzwalaczy właściwości, zobacz [Style i tworzenia szablonów](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd zdarzeń trasowanych](routed-events-overview.md)
- [Przegląd właściwości zależności](dependency-properties-overview.md)
