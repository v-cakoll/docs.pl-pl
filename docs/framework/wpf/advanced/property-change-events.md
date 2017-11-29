---
title: "Zdarzenia zmiany właściwości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e415d5ab46bc354198135fc4e0902e3017923e20
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property-change-events"></a>Zdarzenia zmiany właściwości
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]definiuje kilka zdarzeń, które zostały zgłoszone w odpowiedzi na zmianę wartości właściwości. Właściwość jest często właściwości zależności. Samym zdarzeniu jest czasami kierowanego zdarzenia i czasami jest standardem [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] zdarzeń. Definicji zdarzenia może być różna w zależności od scenariusza, ponieważ niektóre zmiany właściwości odpowiedniej są wysyłane za pośrednictwem drzewo elementu inne zmiany właściwości są zwykle tylko dotyczących obiektów, których zmianie właściwości.  
  
## <a name="identifying-a-property-change-event"></a>Identyfikowanie zdarzenie zmiany właściwości  
 Nie wszystkie zdarzenia, które zgłosiły zmiany właściwości są jawnie oznaczone jako zdarzenie zmiany właściwości, albo na podstawie wzorca podpisu lub wzorzec nazewnictwa. Ogólnie rzecz biorąc, opisu zdarzenia w [!INCLUDE[TLA#tla_sdk](../../../../includes/tlasharptla-sdk-md.md)] dokumentacji wskazuje, czy zdarzenie jest bezpośrednio związany z zmiany wartości właściwości zawiera odsyłacze między właściwości i zdarzenia.  
  
### <a name="routedpropertychanged-events"></a>Zdarzenia RoutedPropertyChanged  
 Niektórych zdarzeń za pomocą typu danych zdarzenia i delegat jawnie używane w przypadku zdarzenia zmiany właściwości. Typ danych zdarzenia jest <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, i jest delegat <xref:System.Windows.RoutedPropertyChangedEventHandler%601>. Dane zdarzenia a obiektem delegowanym ma parametr typu ogólnego, który służy do określania rzeczywisty typ zmiany właściwości podczas definiowania program obsługi. Dane zdarzenia zawierają dwie właściwości <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> i <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>, które są następnie przekazywane jako argument typu zdarzeń danych.  
  
 Część "Trasowane" nazwy wskazuje, że zdarzenie zmiany właściwości jest kierowanego zdarzenia. Zaletą routingu zdarzenie zmiany właściwości jest najwyższym poziomem formant może odbierać zdarzenia zmiany właściwości zmiana wartości właściwości elementów podrzędnych (formantu złożonego części). Na przykład można utworzyć formantu, który zawiera <xref:System.Windows.Controls.Primitives.RangeBase> takie jak kontrolowanie <xref:System.Windows.Controls.Slider>. Jeśli wartość <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zmiany właściwości w części suwaka, może zaistnieć potrzeba obsłużyć tej zmiany w kontrolce nadrzędnej, a nie w części.  
  
 Masz stara wartość i nową wartością, dlatego może być kuszące do użycia tej obsługi zdarzeń jako moduł weryfikacji dla wartości właściwości. Jednak to nie jest zamiar projektowania większości zdarzenia zmiany właściwości. Ogólnie rzecz biorąc są udostępniane, aby można było z tych wartości w innych obszarach logiki kodu, ale faktycznie zmiana wartości z wewnątrz obsługi zdarzeń nie jest zalecane wartości i może spowodować niezamierzoną rekursji w zależności od implementowania programu obsługi .  
  
 Jeśli Twoje właściwość jest właściwością zależności niestandardowych lub jeśli pracujesz z klasy pochodnej której zdefiniowano kod wystąpienia, jest znacznie lepszą mechanizm śledzenia zmian właściwości, które korzysta z wbudowanej w [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] właściwości systemu: wywołania zwrotne systemu właściwość <xref:System.Windows.CoerceValueCallback> i <xref:System.Windows.PropertyChangedCallback>. Aby uzyskać więcej informacji na temat korzystania z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] system właściwości sprawdzania poprawności i wymuszenia, zobacz [wywołania zwrotne właściwości zależności i sprawdzania poprawności](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md) i [właściwości zależności niestandardowe](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md).  
  
### <a name="dependencypropertychanged-events"></a>Zdarzenia DependencyPropertyChanged  
 Kolejną parę typów, które są częścią scenariusza zdarzenie zmiany właściwości jest <xref:System.Windows.DependencyPropertyChangedEventArgs> i <xref:System.Windows.DependencyPropertyChangedEventHandler>. Zdarzenia te zmiany właściwości nie są trasowane; są one standardowe [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdarzenia. <xref:System.Windows.DependencyPropertyChangedEventArgs>Dane zdarzenia nietypowe typ raportowania, ponieważ nie pochodzi od <xref:System.EventArgs>; <xref:System.Windows.DependencyPropertyChangedEventArgs> jest strukturą, nie klasy.  
  
 Zdarzenia, które używają <xref:System.Windows.DependencyPropertyChangedEventArgs> i <xref:System.Windows.DependencyPropertyChangedEventHandler> są nieco częściej niż `RoutedPropertyChanged` zdarzenia. Na przykład zdarzenia, które korzysta z tych typów <xref:System.Windows.UIElement.IsMouseCapturedChanged>.  
  
 Podobnie jak <xref:System.Windows.RoutedPropertyChangedEventArgs%601>, <xref:System.Windows.DependencyPropertyChangedEventArgs> udostępnia również starej i nowej wartości właściwości. Ponadto te same informacje użytkownik może z wartościami kwestie; Zazwyczaj nie zaleca próbę zmiany wartości na nadawcy w odpowiedzi na zdarzenia.  
  
## <a name="property-triggers"></a>Wyzwalacze właściwości  
 Ściśle pojęciem zdarzenie zmiany właściwości jest wyzwalacza właściwości. Wyzwalacza właściwości jest tworzony w stylu lub szablonie i umożliwia utworzenie zachowanie warunkowego na podstawie wartości właściwości, którym przypisano wyzwalacza właściwości.  
  
 Właściwość dla wyzwalacza właściwości musi być właściwością zależności. Ona może być (i często) właściwości zależności tylko do odczytu. Dobry wskaźnik dla po właściwości zależności udostępnianych przez formant co najmniej częściowo została zaprojektowana jako wyzwalacz właściwości jest, jeśli nazwa właściwości rozpoczyna się od "Jest". Właściwości, które mają to nazw są często właściwości tylko do odczytu zależności logiczna gdzie podstawowego scenariusza właściwości zgłasza stan formantu, który może mieć konsekwencje do interfejsu użytkownika w czasie rzeczywistym i w związku z tym jest kandydatem wyzwalacza właściwości.  
  
 Niektóre z tych właściwości również mają zdarzenie zmiany właściwości dedykowanych. Na przykład właściwość <xref:System.Windows.UIElement.IsMouseCaptured%2A> ma zdarzenie zmiany właściwości <xref:System.Windows.UIElement.IsMouseCapturedChanged>. Samej właściwości z wartością dostosowane przez system wejściowy jest tylko do odczytu, a system wejściowy zgłasza <xref:System.Windows.UIElement.IsMouseCapturedChanged> po każdej zmianie w czasie rzeczywistym.  
  
 W porównaniu do zdarzenia zmiany właściwości wartość true, za pomocą wyzwalacza właściwości do działania na zmiany właściwości ma pewne ograniczenia.  
  
 Wyzwalacze właściwości pracy przy użyciu logiki dokładnego dopasowania. Należy określić właściwości i wartość, która wskazuje określoną wartość, dla której wyzwalacz będzie działać. Na przykład: `<Setter Property="IsMouseCaptured" Value="true"> ... </Setter>`. Z powodu tego ograniczenia będzie większość użycia wyzwalacza właściwości dla właściwości logicznych lub właściwości, które przyjmują wartość wyliczenia dedykowanych przypadku zarządzane, aby zdefiniować wyzwalania dla każdego przypadku możliwa wartość zakresu. Lub wyzwalacze właściwości może istnieć tylko wartości specjalnych, takich jak gdy liczba elementów osiągnie wartość 0, a nie byłoby żaden wyzwalacz, który kont w przypadkach, gdy wartość właściwości kierunku od zera ponownie (zamiast wyzwalaczy we wszystkich przypadkach, może okazać się kod Program obsługi zdarzeń w tym miejscu, lub zachowanie domyślne, które włącza od stanu wyzwalacza ponownie, gdy wartość jest różna od zera).  
  
 Składnia właściwości wyzwalacza jest odpowiednikiem instrukcję "if" podczas programowania. Jeśli warunek wyzwalacza jest spełniony, następnie "treść" wyzwalacza właściwości "wykonaniu". "Treść" wyzwalacza właściwości nie jest kodem, znaczników. Ten kod znaczników jest ograniczona do przy użyciu co najmniej jednego <xref:System.Windows.Setter> elementy, aby ustawić inne właściwości obiektu, w których są stosowane stylu lub szablonie.  
  
 Do przesunięcia "if" warunku wyzwalacza właściwości, który zawiera szereg różnych możliwych wartości, zaleca się zazwyczaj do określenia tej samej wartości właściwości domyślnego za pomocą <xref:System.Windows.Setter>. W ten sposób <xref:System.Windows.Trigger> zawartych w niej metody ustawiającej będą mieć pierwszeństwa, podczas warunku wyzwalacza ma wartość true i <xref:System.Windows.Setter> nie jest to poziomu <xref:System.Windows.Trigger> pierwszeństwo ma zawsze, gdy jest spełniony warunek wyzwalacza.  
  
 Wyzwalacze właściwości są zazwyczaj odpowiednie w scenariuszach, w której należy zmienić jedną lub więcej właściwości wygląd, na podstawie stanu inna właściwość w tym samym elemencie.  
  
 Aby uzyskać więcej informacji na temat właściwości wyzwalaczy, zobacz [stylami i tworzenia szablonów](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie kierowane zdarzenia](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
