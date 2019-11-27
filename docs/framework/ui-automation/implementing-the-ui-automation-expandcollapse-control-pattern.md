---
title: Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 073ff0727fc6aab1189f73a254aa95da60820cc3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447151"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).

W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, w tym informacje o właściwościach, metodach i zdarzeniach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.

<xref:System.Windows.Automation.ExpandCollapsePattern> wzorzec kontroli służy do obsługi kontrolek rozwijanych wizualnie, aby wyświetlić większą zawartość i zwinąć, aby ukryć zawartość. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji

Podczas implementowania wzorca kontroli ExpandCollapse dla należy zwrócić uwagę na następujące wytyczne i konwencje:

- Formanty agregujące — skompilowane z obiektami podrzędnymi, które udostępniają interfejs użytkownika z funkcją rozwijania/zwijania, muszą obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> wzorzec kontroli, w którym ich elementy podrzędne nie są. Na przykład kontrolka pola kombi jest skompilowana przy użyciu kombinacji pól listy, przycisków i kontrolek edycji, ale tylko nadrzędne pole kombi, które musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern>.

  > [!NOTE]
  > Wyjątkiem jest formant menu, który jest agregacją pojedynczych obiektów MenuItem. Obiekty MenuItem mogą obsługiwać wzorzec kontrolki <xref:System.Windows.Automation.ExpandCollapsePattern>, ale nie jest to formant menu nadrzędnego. Podobny wyjątek dotyczy formantów elementów drzewa i drzewa.

- Gdy <xref:System.Windows.Automation.ExpandCollapseState> kontrolki jest ustawiony na <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, wszystkie funkcje <xref:System.Windows.Automation.ExpandCollapsePattern> są obecnie nieaktywne dla kontrolki i jedyne informacje, które można uzyskać przy użyciu tego wzorca kontrolki, są <xref:System.Windows.Automation.ExpandCollapseState>. Po dodaniu jakichkolwiek obiektów podrzędnych zostanie uaktywniona <xref:System.Windows.Automation.ExpandCollapseState> zmian i <xref:System.Windows.Automation.ExpandCollapsePattern> funkcji.

- <xref:System.Windows.Automation.ExpandCollapseState> odnosi się tylko do widoczności bezpośrednich obiektów podrzędnych. nie odnosi się do widoczności wszystkich obiektów zależnych.

- Funkcja rozwiń i Zwiń jest specyficzna dla kontrolki. Poniżej przedstawiono przykłady tego zachowania.

  - Menu osobiste pakietu Office może być przykładem Tri-State (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> i <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>), gdzie formant określa stan, który ma zostać przyjęty w przypadku wywołania <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>.

  - Wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> w TreeItem może wyświetlić wszystkie elementy podrzędne lub tylko bezpośrednie elementy podrzędne.

  - Jeśli wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> na kontrolce utrzymuje stan jej elementów podrzędnych, należy wysłać zdarzenie zmiany widoczności, a nie zdarzenia zmiany stanu, jeśli formant nadrzędny nie utrzymuje stanu obiektów podrzędnych po zwinięciu, formant może zniszczyć wszystkie elementy podrzędne, które nie są już widoczne i powodują zerwanie uszkodzonego zdarzenia; lub może zmienić <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> dla każdego elementu podrzędnego i zgłosić zdarzenie zmiany widoczności.

- Aby zagwarantować nawigację, pożądane jest, aby obiekt znajdował się w drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (z odpowiednim stanem widoczności) niezależnie od jego nadrzędnej <xref:System.Windows.Automation.ExpandCollapseState>. Jeśli elementy podrzędne są generowane na żądanie, mogą pojawić się tylko w drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] po wyświetleniu po raz pierwszy lub tylko wtedy, gdy są widoczne.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>Wymagane elementy członkowskie dla IExpandCollapseProvider

Do zaimplementowania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>są wymagane następujące właściwości i metody.

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
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływana, gdy <xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.|

## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
