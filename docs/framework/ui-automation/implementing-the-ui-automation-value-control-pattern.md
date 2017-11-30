---
title: "Implementacja wzorca formantu wartości automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
caps.latest.revision: "25"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 23e71c4ce230221f82172a0e5429fc362379869c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementacja wzorca kontrolki wartości automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IValueProvider>, wraz z informacjami na właściwości i zdarzeń. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.ValuePattern> — Wzorzec formantu jest używana do obsługi formantów tym wewnętrznej nie obejmujących zakres wartości, który może być reprezentowany jako ciąg. Ten ciąg może być edytowalny, w zależności od formantu i jego ustawień. Przykłady formantów, które implementują ten wzorzec można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Gdy implementacja wzorca formantu wartości, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Określa, takich jak <xref:System.Windows.Automation.ControlType.ListItem> i <xref:System.Windows.Automation.ControlType.TreeItem> musi obsługiwać <xref:System.Windows.Automation.ValuePattern> Jeśli wartość któregokolwiek z elementów jest edytowalny, niezależnie od bieżącego trybu edycji kontrolki. Formant nadrzędny muszą również obsługiwać <xref:System.Windows.Automation.ValuePattern> Jeśli elementy podrzędne są edytowalne.  
  
 ![Edytowalny element listy. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Przykład edytowalny element listy  
  
-   Jednowierszowy edycyjnym obsługuje programowy dostęp do ich zawartość zaimplementowanie <xref:System.Windows.Automation.Provider.IValueProvider>. Jednak wiele wierszy edycyjnym nie implementują <xref:System.Windows.Automation.Provider.IValueProvider>; zamiast tego zapewniają dostęp do ich zawartości zaimplementowanie <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
-   Aby pobrać zawartość tekstową kontrolkę edycji wiele wierszy, musi implementować formantu <xref:System.Windows.Automation.Provider.ITextProvider>. Jednak <xref:System.Windows.Automation.Provider.ITextProvider> nie obsługuje ustawiania wartości formantu.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider>nie obsługuje pobierania formatowania informacji lub podciągu wartości. Implementowanie <xref:System.Windows.Automation.Provider.ITextProvider> w tych scenariuszach.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider>musi być implementowana przez formanty takie jak **próbnika kolorów** formant wyboru z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (ilustrowane poniżej), który obsługuje ciąg mapowanie między wartości koloru (na przykład "żółty") i równoważne wewnętrzny[!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)]struktury.  
  
 ![Selektor kolorów z wyróżnionym żółty. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykładowe mapowanie ciągu próbnika kolorów  
  
-   Formant powinny mieć jego <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> ustawioną `true` i jego <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> ustawioną `false` przed zezwoleniem na wywołanie <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Wymagane elementy IValueProvider  
 Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Brak|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> — Jeśli informacje specyficzne dla ustawień regionalnych jest przekazywany do formantu niepoprawny format, takie jak Data niepoprawnie sformatowany.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> — Jeśli nowa wartość nie można przekonwertować ciągu na format rozpoznaje formantu.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> -Gdy podejmowana jest próba do manipulowania formant, który nie jest włączona.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce formantów automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Wstaw TextPattern przykładowy tekst](http://msdn.microsoft.com/en-us/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
