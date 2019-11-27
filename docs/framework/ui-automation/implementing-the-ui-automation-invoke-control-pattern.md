---
title: Implementacja wzorca kontrolki wywołania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
ms.openlocfilehash: 30ae83aa4b73f36afce1251387598ef9b61816d8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435162"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementacja wzorca kontrolki wywołania automatyzacji interfejsu użytkownika

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).

W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IInvokeProvider>, w tym informacje o zdarzeniach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.

<xref:System.Windows.Automation.InvokePattern> wzorzec kontrolki służy do obsługi kontrolek, które nie utrzymują stanu po aktywowaniu, ale raczej inicjują lub wykonują jedną, niejednoznaczną akcję. Kontrolki, które utrzymują stan, takie jak pola wyboru i przyciski radiowe, muszą raczej zaimplementować odpowiednio <xref:System.Windows.Automation.Provider.IToggleProvider> i <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Aby zapoznać się z przykładami formantów implementujących wzorzec kontrolki Invoke, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji

Podczas implementowania wzorca kontrolki Invoke należy zwrócić uwagę na następujące wytyczne i konwencje:

- Kontrolki implementują <xref:System.Windows.Automation.Provider.IInvokeProvider>, jeśli takie samo zachowanie nie jest ujawniane za pomocą innego dostawcy wzorca kontroli. Na przykład jeśli metoda <xref:System.Windows.Automation.InvokePattern.Invoke%2A> formantu wykonuje tę samą akcję co <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>, formant nie powinien implementować <xref:System.Windows.Automation.Provider.IInvokeProvider>.

- Wywoływanie kontrolki jest zazwyczaj wykonywane przez kliknięcie lub dwukrotne kliknięcie lub naciśnięcie klawisza ENTER, wstępnie zdefiniowanego skrótu klawiaturowego lub alternatywnej kombinacji naciśnięć klawiszy.

- <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> jest wywoływane na kontrolce, która została aktywowana (jako odpowiedź na kontrolkę, która prowadzi do jej działania). Jeśli to możliwe, zdarzenie powinno być wywoływane po wykonaniu akcji przez formant i zwróceniem bez blokowania. Wywołane zdarzenie powinno zostać zgłoszone przed obsługą żądania Invoke w następujących scenariuszach:

  - Nie jest to możliwe ani praktyczne, aby poczekać na zakończenie działania.

  - Akcja wymaga interakcji z użytkownikiem.

  - Akcja jest czasochłonna i spowoduje, że klient wywołujący będzie blokował przez znaczący czas.

- Jeśli wywołanie formantu ma znaczące efekty uboczne, te efekty uboczne powinny być uwidaczniane za pomocą właściwości <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>. Na przykład mimo że <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> nie jest skojarzony z zaznaczeniem, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> może spowodować, że zostanie zaznaczona inna kontrolka.

- Efekty przemieszczania (lub przełączenia do trybu failover) zwykle nie stanowią wywoływanego zdarzenia. Jednak kontrolki, które wykonują akcję (w przeciwieństwie do efektów wizualnych), powinny obsługiwać wzorzec formantu <xref:System.Windows.Automation.InvokePattern>.

> [!NOTE]
> Ta implementacja jest uważana za problem z ułatwieniami dostępu, Jeśli kontrolka może być wywoływana tylko w wyniku efektu ubocznego związanego z myszą.

- Wywoływanie kontrolki różni się od wybrania elementu. Jednak w zależności od kontrolki wywoływanie jej może spowodować, że element zostanie wybrany jako efekt uboczny. Na przykład wywoływanie elementu listy dokumentów programu Microsoft Word w folderze Moje dokumenty powoduje wybranie elementu i otwarcie dokumentu.

- Element może zniknąć z drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] natychmiast po wywołaniu. Żądanie informacji z elementu dostarczonego przez wywołanie zwrotne zdarzenia może zakończyć się niepowodzeniem w wyniku. Zalecanym obejściem jest wstępne pobranie informacji w pamięci podręcznej.

- Kontrolki mogą zaimplementować wiele wzorców kontrolek. Na przykład kontrolka kolor wypełnienia na pasku narzędzi programu Microsoft Excel implementuje zarówno <xref:System.Windows.Automation.InvokePattern>, jak i <xref:System.Windows.Automation.ExpandCollapsePattern> wzorców kontrolek. <xref:System.Windows.Automation.ExpandCollapsePattern> uwidacznia menu, a <xref:System.Windows.Automation.InvokePattern> wypełnia aktywny wybór wybranym kolorem.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iinvokeprovider"></a>Wymagane elementy członkowskie dla IInvokeProvider

Do zaimplementowania <xref:System.Windows.Automation.Provider.IInvokeProvider>są wymagane następujące właściwości i metody.

|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|— metoda|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> jest wywołaniem asynchronicznym i musi zwrócić bezpośrednio bez blokowania.<br /><br /> To zachowanie jest szczególnie istotne dla formantów, które bezpośrednio lub pośrednio uruchamiają modalne okno dialogowe po wywołaniu. Każdy klient automatyzacji interfejsu użytkownika, który wykonał zdarzenie, pozostanie zablokowany do momentu zamknięcia modalnego okna dialogowego.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Wyjątki

Dostawcy muszą zgłosić następujące wyjątki.

|Typ wyjątku|Warunek|
|--------------------|---------------|
|<xref:System.Windows.Automation.ElementNotEnabledException>|Jeśli formant nie jest włączony.|

## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika](invoke-a-control-using-ui-automation.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
