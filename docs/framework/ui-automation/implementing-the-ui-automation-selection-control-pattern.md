---
title: Implementacja wzorca formantu wyboru automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: b1f7836eaecf098d5d960d080af52da7e304ace9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410341"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementacja wzorca kontrolki wyboru automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ISelectionProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.SelectionPattern> — Wzorzec formantu jest używana do obsługi formantów, które działają jak kontenery kolekcję elementów podrzędnych możliwy. Elementy podrzędne tego elementu musi implementować <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Podczas implementowania Selection — wzorzec formantu, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Określa, które implementują <xref:System.Windows.Automation.Provider.ISelectionProvider> zezwala na zaznaczanie elementów jednego lub wielu podrzędnych. Na przykład pole listy, widok listy i widok drzewa obsługuje wielokrotny pola kombi, suwak i Grupa przycisków radiowych wsparcie pojedynczego wyboru.  
  
-   Formanty, które ma minimalne, maksymalne i ciągły zakres, takich jak **woluminu** suwaka, powinien implementować <xref:System.Windows.Automation.Provider.IRangeValueProvider> zamiast <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
-   Formanty pojedynczego wyboru, które zarządzają formanty podrzędne, które implementują <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, takich jak **rozdzielczość ekranu** suwak w **właściwości wyświetlania** okno dialogowe lub **kolorów Selektor** formant wyboru z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (przedstawionym poniżej), należy zaimplementować <xref:System.Windows.Automation.Provider.ISelectionProvider>; ich elementy podrzędne powinien implementować jednocześnie <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> i <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Selektor kolorów z wyróżnionym żółty. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykładowe mapowanie ciągu próbnika kolorów  
  
-   Menu nie obsługują <xref:System.Windows.Automation.SelectionPattern>. Jeśli pracujesz z elementów menu, które obejmują zarówno grafiki i tekst (takich jak **okienko podglądu** elementy w **widoku** w menu [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) i trzeba przekazać stanu, należy zaimplementować <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Wymagane elementy ISelectionProvider  
 Następujące właściwości, metod i zdarzeń są wymagane dla <xref:System.Windows.Automation.Provider.ISelectionProvider> interfejsu.  
  
|Wymagane elementy członkowskie|Typ|Uwagi|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Właściwość|Powinna obsługiwać zdarzenia zmiany właściwości przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> i <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Właściwość|Powinna obsługiwać zdarzenia zmiany właściwości przy użyciu <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> i <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Zdarzenie|Wywoływane, gdy zaznaczenie w kontenerze zmienił znacząco i wymaga wysłania więcej zdarzeń Dodawanie i usuwanie niż <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> pozwala stała.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> i <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> właściwości może być dynamiczny. Na przykład stan początkowy formantu nie może być zaznaczone domyślnie, co oznacza, że <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> jest `false`. Jednak po wybraniu elementu formantu musi zawsze mieć co najmniej jednego wybranego elementu. Podobnie w rzadkich przypadkach formantu mogą zezwalać na wiele pozycji, aby wybrać podczas inicjowania, ale następnie zezwala tylko jednej opcji ma zostać wykonane.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Jeśli formant nie jest włączony.|  
|<xref:System.InvalidOperationException>|Jeśli formant jest ukryty.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementacja wzorca kontrolki SelectionItem dla automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
