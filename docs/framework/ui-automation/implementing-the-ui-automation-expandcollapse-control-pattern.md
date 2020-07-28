---
title: Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika
description: Poznaj wytyczne dotyczące implementacji i konwencje dla wzorca kontroli ExpandCollapse dla w automatyzacji interfejsu użytkownika. Dowiedz się, jak zaimplementować IExpandCollapseProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 525b57816071ba2d879036676201a0506d1a29db
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165867"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).

W tym temacie przedstawiono wskazówki i konwencje dotyczące wdrażania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider> , w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.

<xref:System.Windows.Automation.ExpandCollapsePattern>Wzorzec kontrolki służy do obsługi kontrolek rozwijanych wizualnie, aby wyświetlić większą zawartość i zwinąć, aby ukryć zawartość. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji

Podczas implementowania wzorca kontroli ExpandCollapse dla należy zwrócić uwagę na następujące wytyczne i konwencje:

- Formanty agregujące — skompilowane z obiektami podrzędnymi, które udostępniają interfejs użytkownika z funkcjonalnością rozszerzania/zwijania — muszą obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> wzorzec kontrolki, w którym ich elementy podrzędne nie są. Na przykład kontrolka pola kombi jest skompilowana przy użyciu kombinacji pól listy, przycisków i kontrolek edycji, ale tylko nadrzędne pole kombi, które musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> .

  > [!NOTE]
  > Wyjątkiem jest formant menu, który jest agregacją pojedynczych obiektów MenuItem. Obiekty MenuItem mogą obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> wzorzec kontrolki, ale nie można wykonać kontrolki menu nadrzędnego. Podobny wyjątek dotyczy formantów elementów drzewa i drzewa.

- Gdy <xref:System.Windows.Automation.ExpandCollapseState> kontrolka jest ustawiona na <xref:System.Windows.Automation.ExpandCollapseState.LeafNode> , każda <xref:System.Windows.Automation.ExpandCollapsePattern> Funkcja jest obecnie nieaktywna dla kontrolki i jedyne informacje, które można uzyskać za pomocą tego wzorca kontrolki, to <xref:System.Windows.Automation.ExpandCollapseState> . Po dodaniu jakichkolwiek obiektów podrzędnych <xref:System.Windows.Automation.ExpandCollapseState> zmiany i <xref:System.Windows.Automation.ExpandCollapsePattern> funkcje zostaną aktywowane.

- <xref:System.Windows.Automation.ExpandCollapseState>odnosi się tylko do widoczności bezpośrednich obiektów podrzędnych. nie odnosi się do widoczności wszystkich obiektów zależnych.

- Funkcja rozwiń i Zwiń jest specyficzna dla kontrolki. Poniżej przedstawiono przykłady tego zachowania.

  - Menu osobiste pakietu Office może być potrójnym stanem MenuItem ( <xref:System.Windows.Automation.ExpandCollapseState.Expanded> <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> i <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded> ), gdzie formant określa stan do zastosowania, gdy <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływana.

  - Wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> elementu TreeItem może spowodować wyświetlenie wszystkich elementów podrzędnych lub tylko bezpośrednich elementów podrzędnych.

  - Jeśli wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> Kontrola zachowuje stan elementów podrzędnych, należy wysłać zdarzenie zmiany widoczności, a nie zdarzenia zmiany stanu, jeśli formant nadrzędny nie utrzymuje stanu elementów podrzędnych, gdy jest zwinięty, formant może zniszczyć wszystkie elementy podrzędne, które nie są już widoczne i powodują zniszczenie zdarzenia; lub może zmienić <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> dla każdego elementu podrzędnego i zgłosić zdarzenie zmiany widoczności.

- Aby zagwarantować nawigację, pożądane jest, aby obiekt znajdował się w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewie (z odpowiednim stanem widoczności) niezależnie od jego elementów nadrzędnych <xref:System.Windows.Automation.ExpandCollapseState> . Jeśli elementy podrzędne są generowane na żądanie, mogą pojawić się tylko w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewie po wyświetleniu po raz pierwszy lub tylko wtedy, gdy są widoczne.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>Wymagane elementy członkowskie dla IExpandCollapseProvider

Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider> .

|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Właściwość|Brak|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Metoda|Brak|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Metoda|Brak|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Wydarzenie|Ta kontrolka nie ma skojarzonych zdarzeń; Użyj tego delegata ogólnego.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Wyjątki

Dostawcy muszą zgłosić następujące wyjątki.

|Typ wyjątku|Warunek|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>Lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływana, gdy <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode> .|

## <a name="see-also"></a>Zobacz także

- [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
