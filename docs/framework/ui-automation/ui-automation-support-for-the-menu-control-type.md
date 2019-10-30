---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu menu
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu
- UI Automation, Menu control type
- Menu control type
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
ms.openlocfilehash: 155a2878dd71ab51f69d023594932ca715c073c4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040512"
---
# <a name="ui-automation-support-for-the-menu-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu menu
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera informacje o obsłudze [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] dla typu formantu menu. Opisuje ona strukturę drzewa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolki i udostępnia właściwości i wzorce kontroli dla konkretnych scenariuszy kontroli.  
  
 Kontrolka menu umożliwia hierarchiczna organizacji elementów skojarzonych z poleceniami i programami obsługi zdarzeń. W typowej aplikacji systemu Microsoft Windows pasek menu zawiera kilka przycisków menu (takich jak **plik**, **Edycja**i **okno**), a każdy przycisk menu wyświetla menu. Menu zawiera kolekcję elementów menu (takich jak **New**, **Open**i **Close**), które można rozszerzyć, aby wyświetlić dodatkowe elementy menu lub wykonać określoną akcję po kliknięciu.  
  
 Poniższe sekcje definiują wymaganą strukturę drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], właściwości, wzorce formantów i zdarzenia dla typu formantu menu. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] są stosowane do wszystkich kontrolek listy, czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok kontrolki i widok zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które odnoszą się do kontrolek menu, i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na temat drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok kontrolki|Widok zawartości|  
|------------------|------------------|  
|Menu<br /><br /> -MenuItem (1 lub wiele)|Nie dotyczy (chyba że formant menu jest menu kontekstowym, które jest elementem nadrzędnym obiektu, który nie jest elementem menu)<br /><br /> -MenuItem (1 lub wiele)|  
  
 Kontrolki menu są zawsze wyświetlane w widoku kontrolki i w widoku zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Typy kontrolek menu powinny być wyświetlane pod kontrolą, do której odwołują się te informacje. Klienci automatyzacji interfejsu użytkownika muszą nasłuchiwać `MenuOpenedEvent`, aby zapewnić spójność uzyskiwania informacji przekazywanych przez kontrolki menu. Kontrolki menu kontekstowego są szczególnym przypadkiem. Są one wyświetlane jako elementy podrzędne pulpitu.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicja jest szczególnie istotna dla typu formantu menu. Aby uzyskać więcej informacji na temat właściwości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Nieobsługiwane|Kontrolka menu nie wymaga ustawienia właściwości Name.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Nie jest przewidywana żadna etykieta z typowym formantem menu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menu|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Kontrolka menu nie jest zawarta w widoku zawartości drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Oznacza|Formant menu jest zawsze zawarty w widoku kontrolki drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce kontrolek automatyzacji interfejsu użytkownika  
 Brak wymaganych wzorców kontroli dla typu formantu menu.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 Kontrolki menu muszą podnieść `MenuOpenedEvent`, gdy pojawiają się na ekranie. `MenuOpenedEvent` będzie zawierać tekst kontrolki. `MenuClosedEvent` muszą być wywoływane, gdy menu znika z ekranu.  
  
 Poniższa tabela zawiera listę zdarzeń [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], które są wymagane do obsługi przez wszystkie kontrolki menu. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|Zdarzenie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Obsługa/wartość|Uwagi|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> zdarzenie zmiany właściwości.|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.Menu>
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
