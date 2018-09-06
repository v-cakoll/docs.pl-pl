---
title: Implementacja wzorca formantu wartości automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Value
- UI Automation, Value control pattern
- Value control pattern
ms.assetid: b0fcdd87-3add-4345-bca9-e891205e02ba
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 300d9df608553f9f8ae999287b3214c8a9eaea21
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862043"
---
# <a name="implementing-the-ui-automation-value-control-pattern"></a>Implementacja wzorca kontrolki wartości automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IValueProvider>, włącznie z informacjami o zdarzenia i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.ValuePattern> — Wzorzec kontrolki jest używana do obsługi formantów, w tym wewnętrznej nie obejmujących zakres wartości, które mogą być reprezentowane jako ciąg. Ten ciąg może być niemożliwa, w zależności od tego, czy formantem i jego ustawień. Przykłady formantów, które implementują ten wzorzec, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki wartości, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Określa, takich jak <xref:System.Windows.Automation.ControlType.ListItem> i <xref:System.Windows.Automation.ControlType.TreeItem> musi obsługiwać <xref:System.Windows.Automation.ValuePattern> w przypadku edycji wartości dowolnych elementów, niezależnie od bieżącego trybu edycji kontrolki. Kontrolki nadrzędnej również musi obsługiwać <xref:System.Windows.Automation.ValuePattern> Jeśli elementy podrzędne są edytowalne.  
  
 ![Element edytowalnej listy. ](../../../docs/framework/ui-automation/media/uia-valuepattern-editable-listitem.PNG "UIA_ValuePattern_Editable_ListItem")  
Przykład elementu edytowalnej listy  
  
-   Formanty edycji jednowierszowego obsługuje programowy dostęp do ich zawartości poprzez implementację <xref:System.Windows.Automation.Provider.IValueProvider>. Jednak nie należy implementować formantów edycji wielowierszowe <xref:System.Windows.Automation.Provider.IValueProvider>; zamiast tego zapewniają dostęp do swojej zawartości poprzez implementację <xref:System.Windows.Automation.Provider.ITextProvider>.  
  
-   Aby pobrać zawartość tekstową kontrolki edycji wielowierszowego, należy zaimplementować formant <xref:System.Windows.Automation.Provider.ITextProvider>. Jednak <xref:System.Windows.Automation.Provider.ITextProvider> nie obsługuje ustawiania wartości formantu.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> nie obsługuje pobierania formatowania informacji lub podciągu wartości. Implementowanie <xref:System.Windows.Automation.Provider.ITextProvider> w tych scenariuszach.  
  
-   <xref:System.Windows.Automation.Provider.IValueProvider> należy zaimplementować formantów takich jak **selektor kolorów** kontrolki wyboru z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (przedstawiono poniżej), obsługującą ciąg mapowania między wartość koloru (na przykład "żółty") i równoważne wewnętrzny[!INCLUDE[TLA#tla_rgb](../../../includes/tlasharptla-rgb-md.md)]struktury.  
  
 ![Selektor kolorów z żółtym wyróżnione. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Przykładowe mapowanie parametrów próbników kolorów  
  
-   Kontrolki powinny mieć jego <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> równa `true` i jego <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> równa `false` przed zezwoleniem na wywołanie <xref:System.Windows.Automation.Provider.IValueProvider.SetValue%2A>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-ivalueprovider"></a>Wymagane elementy IValueProvider  
 Poniższe właściwości i metod wymaganych do implementowania <xref:System.Windows.Automation.Provider.IValueProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ValuePattern.ValueProperty>|Właściwość|Brak|  
|<xref:System.Windows.Automation.ValuePattern.SetValue%2A>|Metoda|Brak|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> — Jeśli informacje specyficzne dla ustawień regionalnych jest przekazywany do formantu w ma niewłaściwy format, takie jak Data niepoprawnie sformatowany.|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> — Jeśli nowa wartość nie można przekonwertować ciągu na format kontrolki jest rozpoznawane.|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|<xref:System.Windows.Automation.ValuePattern.SetValue%2A><br /><br /> — W przypadku próby manipulowania formant, który nie jest włączona.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przykładowy tekst wstawienia TextPattern](https://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
