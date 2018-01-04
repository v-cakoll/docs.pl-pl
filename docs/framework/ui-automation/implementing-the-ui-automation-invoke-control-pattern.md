---
title: "Implementacja wzorca formantu wywołania automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
caps.latest.revision: "31"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1d40bc94887df604577c025181ae7f5f2776cdc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementacja wzorca kontrolki wywołania automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IInvokeProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.InvokePattern> — Wzorzec formantu jest używana do obsługi formantów, które nie zarządzania stanem po uaktywnieniu lecz inicjowania lub wykonania akcji jednej, jednoznaczne. Formanty, które zachowują stan, takich jak pola wyboru i przyciski radiowe, zamiast tego należy zaimplementować <xref:System.Windows.Automation.Provider.IToggleProvider> i <xref:System.Windows.Automation.Provider.ISelectionItemProvider> odpowiednio. Przykłady formantów, które implementują Invoke — wzorzec formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Podczas implementowania Invoke — wzorzec formantu, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Formanty zaimplementować <xref:System.Windows.Automation.Provider.IInvokeProvider> jeśli takie samo zachowanie nie jest dostępne za pośrednictwem innego dostawcy — wzorzec formantu. Na przykład jeśli <xref:System.Windows.Automation.InvokePattern.Invoke%2A> ta sama akcja co wykonuje metodę w formancie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> metody formantu nie powinny implementować <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
-   Wywoływanie formantu zwykle odbywa się przez kliknięcie dwukrotne kliknięcie lub naciśnięcie klawisza ENTER, skrót klawiaturowy wstępnie zdefiniowanych lub alternatywne kombinacji klawiszy.  
  
-   <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>jest uruchamiany w formancie, który został aktywowany (w odpowiedzi na jego skojarzony akcji formantu). Jeśli to możliwe zdarzenia powinien być zgłaszany po ukończył akcję kontrolki i zwracane bez blokowania. Zdarzenie Invoked powinien być wywoływany przed obsługi żądania Invoke w następujących scenariuszach:  
  
    -   Nie jest możliwe lub praktyczne poczekaj aż zakończy się akcja.  
  
    -   Akcja wymaga interakcji z użytkownikiem.  
  
    -   Akcja jest czasochłonne i spowoduje wywołanie klienta mają być blokowane dla znaczną ilość czasu.  
  
-   Jeśli wywoływanie formantu ma znaczący efekty uboczne, te efekty uboczne powinny zostać ujawnione za pośrednictwem <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> właściwości. Na przykład nawet jeśli <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> nie jest skojarzony z zaznaczenia, <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> może spowodować inny formant do zostaje zaznaczony.  
  
-   Umieść kursor (lub myszą) efekty zazwyczaj nie stanowią Invoked zdarzenia. Jednak powinna obsługiwać formantów, które wykonywania akcji (zamiast Przyczyna efektem) na podstawie stanu aktywowanego <xref:System.Windows.Automation.InvokePattern> — wzorzec formantu.  
  
> [!NOTE]
>  Ta implementacja jest uznawany za problemu ułatwień dostępu, jeśli formant może być wywoływany tylko w wyniku efekt uboczny związanych z myszą.  
  
-   Wywoływanie formantu różni się od zaznaczenie elementu. W zależności od tego formantu, wywoływanie jej może jednak spowodować elementu, który ma zostać wybrana jako efektem ubocznym. Na przykład wywoływania [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] elementu listy dokumentów w folderze Moje dokumenty wybiera element i otwiera dokument.  
  
-   Element może zniknąć z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa natychmiast po wywoływany. Żąda informacji z elementu udostępniane przez wywołanie zwrotne zdarzeń może zakończyć się niepowodzeniem w wyniku. Pobierania buforowanych informacji jest zalecaną praktyką.  
  
-   Formanty można zaimplementować wiele wzorców formantu. Na przykład kontrolka kolor wypełnienia w [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] narzędzi implementuje zarówno <xref:System.Windows.Automation.InvokePattern> i <xref:System.Windows.Automation.ExpandCollapsePattern> kontrolować wzorce. <xref:System.Windows.Automation.ExpandCollapsePattern>Udostępnia menu i <xref:System.Windows.Automation.InvokePattern> wypełnia active zaznaczenie z wybranego koloru.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iinvokeprovider"></a>Wymagane elementy IInvokeProvider  
 Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|— metoda|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>to wywołanie asynchroniczne i musi zwracać natychmiast bez blokowania.<br /><br /> To zachowanie jest szczególnie istotne dla formantów, które bezpośrednio lub pośrednio, uruchom modalnego okna dialogowego, gdy została wywołana. Automatyzacja interfejsu użytkownika klienta, który zainicjowanego zdarzenia pozostanie zablokowane do czasu zamknięcia modalnego okna dialogowego.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Jeśli formant nie jest włączony.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
