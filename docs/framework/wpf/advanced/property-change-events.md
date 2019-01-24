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
ms.openlocfilehash: cd7c9c514c90a94e3329bec9614624ee399481ed
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524003"
---
# <a name="property-change-events"></a>Zdarzenia zmiany właściwości
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] definiuje kilka zdarzeń, które są wywoływane w odpowiedzi na zmianę wartości właściwości. Często właściwość jest właściwość zależności. Samego zdarzenia jest czasami zdarzenia trasowanego i czasami jest to standard [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] zdarzeń. Definicja zdarzenia różni się zależnie od scenariusza, ponieważ niektóre zmiany właściwości bardziej odpowiednie są przesyłane za pośrednictwem drzewo elementów, natomiast inne zmiany właściwości są zwykle tylko z kwestią do obiektu, gdy zmianie właściwości.  
  
## <a name="identifying-a-property-change-event"></a>Identyfikowanie zdarzenia zmiany właściwości  
 Nie wszystkie zdarzenia, którzy raportują zmiana właściwości są jawnie oznaczone jako zdarzenie zmiany właściwości, albo na podstawie wzorca podpisu lub wzorca nazewnictwa. Ogólnie rzecz biorąc, opis zdarzenia w [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] dokumentacji wskazuje, czy zdarzenie jest bezpośrednio związany z zmiana wartości właściwości zawiera odsyłacze do właściwości i zdarzeń.  
  
### <a name="routedpropertychanged-events"></a>RoutedPropertyChanged Events  
 Wystąpienia określonych zdarzeń za pomocą typu danych zdarzeń i delegat jawnie używane w przypadku zdarzenia zmiany właściwości. Typ danych zdarzenia jest <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, i jest delegat <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Dane zdarzenia i delegata ma parametr typu ogólnego, który jest używany do określenia rzeczywisty typ zmiany właściwości podczas definiowania obsługi. Dane zdarzenia zawierają dwie właściwości <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> i <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, które są następnie przekazywany jako argument typu w zdarzeniu danych.  
  
 Część "Trasowane" nazwa wskazuje, że zdarzenie zmiany właściwości jest zdarzenia trasowanego. Zaletą routingu zdarzenie zmiany właściwości jest najwyższym poziomie formantu może odbierać zdarzenia zmiany właściwości zmiana wartości właściwości elementów podrzędnych (formantu złożonego części). Na przykład można utworzyć formant, który zawiera <xref:System.Windows.Controls.Primitives.RangeBase> takich jak kontrolować <xref:System.Windows.Controls.Slider>. Jeśli wartość <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zmiany właściwości w części suwaka, możesz zechcieć obsłużyć tej zmiany do kontrolki nadrzędnej, a nie część.  
  
 Ponieważ stara wartość i nowa wartość, może być kuszące do użycia tego programu obsługi zdarzeń jako moduł weryfikacji dla wartości właściwości. Jednak to nie zamiar projektowania większość zdarzenia zmiany właściwości. Ogólnie rzecz biorąc są udostępniane, dzięki czemu może działać na te wartości w innych obszarach logiki w kodzie, ale rzeczywistego zmieniania wartości z wewnątrz procedury obsługi zdarzeń nie jest zalecane wartości i może spowodować niezamierzone rekursji, w zależności od implementacji programu obsługi .  
  
 Jeśli Twoja własność jest właściwość zależności niestandardowej lub jeśli pracujesz z klasy pochodnej gdzie zdefiniowano kodu podczas tworzenia wystąpienia, jest znacznie lepiej mechanizm śledzenia zmian właściwości, które jest wbudowana w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system właściwości: wywołania zwrotne z systemu właściwości <xref:System.Windows.CoerceValueCallback> i <xref:System.Windows.PropertyChangedCallback>. Aby uzyskać więcej informacji na temat korzystania z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system właściwości do sprawdzania poprawności i wymuszenia, zobacz [zależność wartości wywołania zwrotnego i walidacji](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md) i [niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>DependencyPropertyChanged Events  
 Jest kolejną parę typy, które są częścią scenariusza zdarzenie zmiany właściwości <xref:System.Windows.DependencyPropertyChangedEventArgs> i <xref:System.Windows.DependencyPropertyChangedEventHandler>. Zdarzenia zmiany właściwości nie są trasowane; są one standardowego [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenia. <xref:System.Windows.DependencyPropertyChangedEventArgs> dane nietypowe zdarzenia typ raportowania, ponieważ nie pochodzi od <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> jest strukturą, nie klasę.  
  
 Zdarzenia, które używają <xref:System.Windows.DependencyPropertyChangedEventArgs> i <xref:System.Windows.DependencyPropertyChangedEventHandler> są nieco bardziej powszechne niż `RoutedPropertyChanged` zdarzenia. Na przykład zdarzenie, które korzysta z tych typów <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Podobnie jak <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> również raporty stare i nowe wartości dla właściwości. Ponadto tego samego rozwiązania kwestii dotyczących co można z wartościami zastosować; Ogólnie nie jest zalecane próba zmiany wartości na nadawcy w odpowiedzi na zdarzenie.  
  
## <a name="property-triggers"></a>Wyzwalacze właściwości  
 Ściśle powiązanych koncepcji zdarzenia zmiany właściwości jest wyzwalacza właściwości. Wyzwalacz właściwości jest tworzona w stylu lub szablonu i pozwala na tworzenie zachowania warunkowe na podstawie wartości właściwości, której przypisano wyzwalacza właściwości.  
  
 Właściwości wyzwalacza właściwości musi być właściwość zależności. Jego można (i często jest) właściwości zależności tylko do odczytu. Dobry wskaźnik dla po właściwości zależności udostępnianych przez kontrolkę jest co najmniej częściowo zaprojektowane jako wyzwalacz właściwości jest, jeśli nazwa właściwości zaczyna się od "Is". Właściwości, które mają ten nazewnictwa są często właściwości tylko do odczytu logiczna zależności gdzie podstawowy scenariusz dla właściwości zgłasza stan formantu, który może mieć konsekwencje do Interfejsu użytkownika w czasie rzeczywistym, a ten sposób jest kandydatem wyzwalacza właściwości.  
  
 Niektóre z tych właściwości również mają zdarzenia zmiany właściwości dedykowanych. Na przykład właściwość <xref:System.Windows.UIElement.IsMouseCaptured%2A> ma zdarzenie zmiany właściwości <xref:System.Windows.UIElement.IsMouseCapturedChanged>. Samą właściwość jest tylko do odczytu z jej wartością dostosowane przez system wejściowy, a system wejściowy zgłasza <xref:System.Windows.UIElement.IsMouseCapturedChanged> przy każdej zmianie w czasie rzeczywistym.  
  
 W porównaniu do zdarzenia zmiany właściwości wartość true, za pomocą wyzwalacza właściwości do działania po zmianie właściwości ma pewne ograniczenia.  
  
 Wyzwalacze właściwości pracy logiki dokładnego dopasowania. Należy określić właściwości i wartość, która wskazuje określoną wartość, dla których wyzwalacz będzie działać. Na przykład: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Z powodu tego ograniczenia większość właściwości wyzwalacza użycia będzie właściwości logiczne lub właściwości, które przyjmują wartości wyliczenia dedykowane, których zakres możliwych wartości jest zarządzany, aby zdefiniować wyzwalacz dla każdego przypadku. Wyzwalacze właściwości może istnieć tylko w przypadku wartości specjalne, np. gdy liczba elementów osiągnie zero, i będzie żaden wyzwalacz, który konta w przypadkach, gdy wartość właściwości ponownie zmienia się od zera (zamiast wyzwalaczy we wszystkich przypadkach, może okazać się kod Program obsługi zdarzeń w tym miejscu lub zachowanie domyślne, które zmienia powrót po awarii z stan wyzwalacza stanie się ponownie, gdy wartość jest różna od zera).  
  
 Składnia wyzwalacza właściwości jest analogiczne do instrukcji "if", podczas programowania. Jeśli warunek wyzwalacza ma wartość true, następnie "treść" wyzwalacz właściwości jest "wykonywane". "Treść" wyzwalacza właściwości nie jest kodem, znaczników. Ten kod znaczników jest ograniczona do przy użyciu co najmniej jeden <xref:System.Windows.Setter> elementy, aby ustawić inne właściwości obiektu, w której jest stosowany stylu lub szablonu.  
  
 Do warunku "if" wyzwalacza właściwości, który zawiera szeroką gamę możliwych wartości, jest na ogół do tej samej wartości właściwości domyślnie ustawiona na przy użyciu <xref:System.Windows.Setter>. W ten sposób <xref:System.Windows.Trigger> zawartej metody ustawiającej pierwszeństwo ma podczas spełnienie warunku wyzwalacza ma wartość true, a <xref:System.Windows.Setter> nie jest to w ramach <xref:System.Windows.Trigger> pierwszeństwo ma zawsze wtedy, gdy nie jest spełniony warunek wyzwalacza.  
  
 Wyzwalacze właściwości są ogólnie właściwe dla scenariuszy, w którym należy zmienić jedną lub więcej właściwości wyglądu, oparte na stanie innej właściwości w tym samym elemencie.  
  
 Aby dowiedzieć się więcej na temat wyzwalaczy właściwości, zobacz [Tworzenie szablonów i stylów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Zobacz także
- [Przegląd zdarzeń trasowanych](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
