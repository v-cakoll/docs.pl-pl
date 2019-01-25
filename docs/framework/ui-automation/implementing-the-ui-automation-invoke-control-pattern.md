---
title: Implementacja wzorca formantu wywołania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Invoke control pattern
- control patterns, Invoke
- Invoke control pattern
ms.assetid: e5b1e239-49f8-468e-bfec-1fba02ec9ac4
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 23e8631fb19d3fd8fafe0ba2523e7c2dbc971ee3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592263"
---
# <a name="implementing-the-ui-automation-invoke-control-pattern"></a>Implementacja wzorca kontrolki wywołania automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IInvokeProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.InvokePattern> — Wzorzec kontrolki jest używana do obsługi formantów, które nie zachowują stan, po aktywowaniu ale raczej inicjowania lub wykonania akcji pojedynczego, jednoznaczną. Formanty, które zachowują stan, takich jak pola wyboru i przyciski radiowe, zamiast tego należy zaimplementować <xref:System.Windows.Automation.Provider.IToggleProvider> i <xref:System.Windows.Automation.Provider.ISelectionItemProvider> odpowiednio. Przykłady formantów, które implementują Invoke — wzorzec kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Podczas implementowania Invoke — wzorzec kontrolki, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Implementowanie kontrolek <xref:System.Windows.Automation.Provider.IInvokeProvider> jeśli takie samo zachowanie nie jest dostępna za pośrednictwem innego dostawcy wzorzec kontroli. Na przykład jeśli <xref:System.Windows.Automation.InvokePattern.Invoke%2A> metoda na formant wykonuje ta sama akcja co <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> metody, formant nie należy implementować <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
-   Wywoływanie kontrolki zwykle odbywa się przez kliknięcie, dwukrotne kliknięcie lub naciśnięcie klawisza ENTER, skrót klawiaturowy wstępnie zdefiniowanych lub alternatywne kombinacja klawiszy.  
  
-   <xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent> jest wywoływane na formant, który został aktywowany (jako odpowiedzi do formantu przeprowadzania jego skojarzone z akcją). Jeśli to możliwe powinno być generowane zdarzenie, po kontrolki ukończył akcję i zwrócony bez blokowania. Powinno być generowane zdarzenie wywoływany przed obsługi żądania Invoke w następujących scenariuszach:  
  
    -   Nie jest możliwe lub praktyczne czekać, aż do zakończenia akcji.  
  
    -   Akcja wymaga interakcji z użytkownikiem.  
  
    -   Akcja jest czasochłonne i spowoduje, że klienta wywołującego zablokować na znaczną ilość czasu.  
  
-   Jeśli wywołanie formantu znaczący efekty uboczne, te efekty uboczne powinny zostać ujawnione przez <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A> właściwości. Na przykład nawet jeśli <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> nie jest skojarzony z zaznaczoną opcję <xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> może spowodować, że inna kontrolka stają się wybrać.  
  
-   Zatrzymaj wskaźnik myszy (lub myszą) efekty ogólnie nie jest uznawany za wywołany. Jednak powinna obsługiwać formantów, które wykonują akcję (w przeciwieństwie do Przyczyna efekt wizualny) na podstawie stanu po wskazaniu wskaźnikiem <xref:System.Windows.Automation.InvokePattern> — wzorzec kontrolki.  
  
> [!NOTE]
>  Ta implementacja jest uznawana za zgłoszenie ułatwień dostępu, jeśli formant może być wywoływany tylko w wyniku związane z myszy efekt uboczny.  
  
-   Wywoływanie kontrolki różni się od zaznaczenie elementu. W zależności od kontrolki, wywołanie go może jednak spowodować element które mają zostać wybrana jako efekt uboczny. Na przykład, wywołanie [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] elementu listy dokumentów w folderze Moje dokumenty wybiera element i otwiera dokument.  
  
-   Element może zniknąć z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa natychmiast po wywoływana. Trwa żądanie informacji z elementu dostarczone przez wywołanie zwrotne zdarzeń może zakończyć się niepowodzeniem w wyniku. Wstępnie pobieranie informacji o pamięci podręcznej jest zalecaną praktyką.  
  
-   Kontrolki można zaimplementować wiele wzorców kontrolek. Na przykład kontrolka koloru wypełnienia w [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] narzędzi implementuje interfejsy <xref:System.Windows.Automation.InvokePattern> i <xref:System.Windows.Automation.ExpandCollapsePattern> kontrolować wzorców. <xref:System.Windows.Automation.ExpandCollapsePattern> Udostępnia menu i <xref:System.Windows.Automation.InvokePattern> wypełnia aktywnego zaznaczenia z wybranym kolorze.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iinvokeprovider"></a>Wymagane elementy IInvokeProvider  
 Poniższe właściwości i metod wymaganych do implementowania <xref:System.Windows.Automation.Provider.IInvokeProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A>|— metoda|<xref:System.Windows.Automation.Provider.IInvokeProvider.Invoke%2A> jest wywołanie asynchroniczne i musi zwracać się natychmiast bez blokowania.<br /><br /> To zachowanie jest szczególnie istotne dla formantów, które bezpośrednio lub pośrednio, uruchamianie modalnego okna dialogowego po wywołaniu. Klienta automatyzacji interfejsu użytkownika, który zainicjowanego zdarzenia pozostanie zablokowany do czasu zamknięcia modalne okno dialogowe.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Jeśli formant nie jest włączona.|  
  
## <a name="see-also"></a>Zobacz także
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Wywoływanie kontrolki przy użyciu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
