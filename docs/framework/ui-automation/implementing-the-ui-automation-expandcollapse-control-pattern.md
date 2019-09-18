---
title: Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 232bceba8286c2566a7df03b9001a5c43b348b20
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043460"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.

W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>dotyczące wdrażania, w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.

Wzorzec <xref:System.Windows.Automation.ExpandCollapsePattern> kontrolki służy do obsługi kontrolek rozwijanych wizualnie, aby wyświetlić większą zawartość i zwinąć, aby ukryć zawartość. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji

Podczas implementowania wzorca kontroli ExpandCollapse dla należy zwrócić uwagę na następujące wytyczne i konwencje:

- Formanty agregujące — skompilowane z obiektami podrzędnymi, które udostępniają interfejs użytkownika z funkcjonalnością rozszerzania/zwijania — muszą obsługiwać wzorzec kontrolki, w <xref:System.Windows.Automation.ExpandCollapsePattern> którym ich elementy podrzędne nie są. Na przykład kontrolka pola kombi jest skompilowana przy użyciu kombinacji pól listy, przycisków i kontrolek edycji, ale tylko nadrzędne pole kombi, które musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern>.

  > [!NOTE]
  > Wyjątkiem jest formant menu, który jest agregacją pojedynczych obiektów MenuItem. Obiekty MenuItem mogą obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> wzorzec kontrolki, ale nie można wykonać kontrolki menu nadrzędnego. Podobny wyjątek dotyczy formantów elementów drzewa i drzewa.

- Gdy kontrolka jest ustawiona na <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, każda <xref:System.Windows.Automation.ExpandCollapsePattern> funkcja jest obecnie nieaktywna dla kontrolki i jedyne informacje, które można uzyskać za pomocą tego wzorca kontrolki, <xref:System.Windows.Automation.ExpandCollapseState>to. <xref:System.Windows.Automation.ExpandCollapseState> Po dodaniu <xref:System.Windows.Automation.ExpandCollapseState> jakichkolwiek obiektów podrzędnych zmiany i <xref:System.Windows.Automation.ExpandCollapsePattern> funkcje zostaną aktywowane.

- <xref:System.Windows.Automation.ExpandCollapseState>odnosi się tylko do widoczności bezpośrednich obiektów podrzędnych. nie odnosi się do widoczności wszystkich obiektów zależnych.

- Funkcja rozwiń i Zwiń jest specyficzna dla kontrolki. Poniżej przedstawiono przykłady tego zachowania.

  - Menu osobiste pakietu Office może być potrójnym stanem MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>i <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>), gdzie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> formant określa stan do zastosowania, gdy lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływana.

  - Wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> elementu TreeItem może spowodować wyświetlenie wszystkich elementów podrzędnych lub tylko bezpośrednich elementów podrzędnych.

  - Jeśli wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> kontrola zachowuje stan elementów podrzędnych, należy wysłać zdarzenie zmiany widoczności, a nie zdarzenia zmiany stanu, jeśli formant nadrzędny nie utrzymuje stanu obiektów podrzędnych po zwinięciu, formant może Zniszcz wszystkie elementy podrzędne, które nie są już widoczne, i Zgłoś zniszczone zdarzenie; lub może zmienić <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> dla każdego elementu podrzędnego i zgłosić zdarzenie zmiany widoczności.

- Aby zagwarantować nawigację, pożądane jest, aby obiekt znajdował się [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] w drzewie (z odpowiednim stanem widoczności) niezależnie od jego <xref:System.Windows.Automation.ExpandCollapseState>elementów nadrzędnych. Jeśli elementy podrzędne są generowane na żądanie, mogą pojawić się tylko w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewie po wyświetleniu po raz pierwszy lub tylko wtedy, gdy są widoczne.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>Wymagane elementy członkowskie dla IExpandCollapseProvider

Następujące właściwości i metody są wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.

|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Właściwość|Brak|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Metoda|Brak|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Metoda|Brak|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Zdarzenie|Ta kontrolka nie ma skojarzonych zdarzeń; Użyj tego delegata ogólnego.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Wyjątki

Dostawcy muszą zgłosić następujące wyjątki.

|Typ wyjątku|Warunek|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> Lub jestwywoływana<xref:System.Windows.Automation.ExpandCollapseState> , = gdy. <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>|

## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
