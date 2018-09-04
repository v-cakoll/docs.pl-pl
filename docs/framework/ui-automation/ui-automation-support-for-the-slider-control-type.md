---
title: Obsługa automatyzacji interfejsu użytkownika dla formantów typu suwak
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Slider
- UI Automation, Slider control type
- Slider control type
ms.assetid: 045ea62f-7b50-46cf-a5a9-8eb97704355f
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 2b15698cb52022ea9e69dca7e182b18b4fc1f05a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525404"
---
# <a name="ui-automation-support-for-the-slider-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu suwak
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługi dla kontrolek typu suwak. W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ formantu to zestaw warunków, które kontrolki muszą spełnić, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości. Warunki obejmują konkretne wskazówki dotyczące [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości i typów formantów.  
  
 Kontrolka suwaka jest złożonym formantem za pomocą przycisków umożliwiających użytkownikowi za pomocą myszy Ustaw zakres wartości liczbowych albo wybierz go z zbiór elementów.  
  
 Poniższe sekcje definiują wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa struktury, właściwości, wzorców kontrolek i zdarzeń dla kontrolek typu suwak. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania mają zastosowanie do wszystkich kontrolek suwaka, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura drzewa automatyzacji interfejsu użytkownika wymagane  
 Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewo, które odnoszą się do suwaka kontroluje i w tym artykule opisano, jakie mogą być zawarte w każdym widoku. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Formant widoku|Widok zawartości|  
|------------------|------------------|  
|Suwak<br /><br /> — Przycisk (2 lub 4)<br />— Thumb (tylko 1)<br />-Element list (0 lub więcej)|Suwak<br /><br /> -Element list (0 lub więcej)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Właściwości automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicji jest szczególnie istotne suwak kontrolowanie typu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa wśród wszystkich kontrolek w aplikacji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrznej prostokąt, który zawiera całą kontrolkę.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi|Większość kontrolki suwaka, trzeba zwiększyć <xref:System.Windows.Automation.NoClickablePointException> ponieważ cały prostokąt otaczający kontrolki suwaka jest zajęta przez formantów podrzędnych.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Formant może otrzymywać fokus klawiatury, musi obsługiwać tę właściwość.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Nazwa kontrolki edycji zwykle jest generowany z etykiety tekst statyczny. Jeśli nie jest statyczny tekst etykiety, wartość właściwości `Name` musi zostać przypisany przez dewelopera aplikacji. `Name` Właściwość nigdy nie powinna zawierać zawartość tekstową kontrolki edycji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Zobacz uwagi.|W przypadku etykietę statyczny tekst skojarzony z formantem, ta właściwość musi ujawniać odwołanie do tego formantu. Jeśli text control to podskładnika innej kontrolki, nie będziesz mieć `LabeledBy` zestawu właściwości.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Suwak|Ta wartość jest taka sama dla wszystkich [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] struktur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"suwaka"|Zlokalizowany ciąg odpowiadający typowi kontrolki edycji.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Kontrolka edycji zawsze znajduje się w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Kontrolka edycji zawsze znajduje się w widoku kontrolnym [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorców, wymagane są obsługiwane przez wszystkie kontrolki suwaka. Aby uzyskać więcej informacji na temat wzorców kontrolek, zobacz [Przegląd wzorców kontrolki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|— Wzorzec kontrolki|Obsługa|Uwagi|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Zależy od|Suwak powinien obsługiwać wzorca kontrolki wyboru, jeśli zawartość reprezentuje jedną wartość między odrębny zestaw opcji. Gdy wzorca kontrolki wyboru jest obsługiwany, odpowiedni wybór muszą być widoczne jako jeden lub więcej podrzędnych elementów listy w suwaka.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Zależy od|Suwak powinien obsługiwać RangeValue — wzorzec kontrolki, jeśli zawartość może zostać ustawione na wartość zakresu wartości liczbowych.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Zależy od|Suwak powinien obsługiwać wzorca kontrolki wartości, jeśli zawartość reprezentuje jedną wartość między odrębny zestaw opcji.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Właściwości zdarzeń automatyzacji interfejsu użytkownika wymagane  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane są obsługiwane przez wszystkie kontrolki suwaka.  
  
 Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Zdarzenia|Obsługa|Uwagi|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> Zdarzenie zmiany właściwości|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> Zdarzenie zmiany właściwości|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> Zdarzenie zmiany właściwości|Wymagane|Brak|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> Zdarzenie zmiany właściwości|Zależy od|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType.Slider>  
 [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
