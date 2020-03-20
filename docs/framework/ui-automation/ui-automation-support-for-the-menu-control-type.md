---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu menu
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu
- UI Automation, Menu control type
- Menu control type
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
ms.openlocfilehash: 3e3177f682ad75f4673870a72aee6d86c7b5ab60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179687"
---
# <a name="ui-automation-support-for-the-menu-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu menu
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] informacje na temat obsługi typu formantu Menu. Opisuje strukturę [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] drzewa formantu i zapewnia właściwości i wzorce kontroli dla określonych scenariuszy kontroli.  
  
 Formant menu umożliwia hierarchiczne organizowanie elementów skojarzonych z poleceniami i programami obsługi zdarzeń. W typowej aplikacji systemu Microsoft Windows pasek menu zawiera kilka przycisków menu (takich jak **Plik,** **Edycja**i **Okno),** a każdy przycisk menu wyświetla menu. Menu zawiera zbiór elementów menu (takich jak **Nowy,** **Otwórz**i **Zamknij),** które można rozwinąć, aby wyświetlić dodatkowe elementy menu lub wykonać określoną akcję po kliknięciu.  
  
 Poniższe sekcje definiują wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce kontroli i zdarzenia dla typu formantu Menu. Wymagania [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] dotyczą wszystkich formantów [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]listy, niezależnie od tego, czy , Win32 lub Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika  
 W poniższej tabeli przedstawiono widok formantu i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, który odnosi się do formantów menu i opisuje, co może być zawarte w każdym widoku. Aby uzyskać więcej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] informacji na temat drzewa, zobacz [Omówienie drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md).  
  
|Widok sterowania|Widok zawartości|  
|------------------|------------------|  
|Menu<br /><br /> - MenuItem (1 lub wiele)|Nie dotyczy (chyba że formant menu jest menu kontekstowe, który jest elementem nadrzędnym obiektu, który nie jest elementem menu)<br /><br /> - MenuItem (1 lub wiele)|  
  
 Formanty menu są zawsze wyświetlane w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku formantu i widoku zawartości drzewa. Typy kontroli menu powinny być wyświetlane pod kontrolą, do których odnoszą się ich informacje. Klienci automatyzacji interfejsu `MenuOpenedEvent` użytkownika muszą nasłuchiwać, aby upewnić się, że konsekwentnie uzyskiwać informacje przekazywane przez formanty menu. Kontrolki menu kontekstowego są szczególnym przypadkiem. Pojawiają się jako dzieci pulpitu.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono właściwości, których wartość lub definicja jest szczególnie istotne dla typu formantu Menu. Aby uzyskać [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] więcej informacji na temat właściwości, zobacz [Właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Właściwość|Wartość|Uwagi|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Nieobsługiwane|Formant menu nie wymaga name właściwości, aby ustawić.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Nie przewiduje się etykiety z typową kontrolą menu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menu|Ta wartość jest taka sama dla wszystkich struktur interfejsu użytkownika.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Formant menu nie jest uwzględniony w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku zawartości drzewa.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Formant menu jest zawsze zawarte w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] widoku sterowania drzewa.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce sterowania automatyzacją interfejsu użytkownika  
 Nie ma żadnych wymaganych wzorców kontroli dla typu formantu Menu.  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika  
 Kontrolki `MenuOpenedEvent` menu muszą zostać podsuwają się, gdy pojawią się na ekranie. Będzie `MenuOpenedEvent` zawierać tekst formantu. Musi `MenuClosedEvent` być podniesiona, gdy menu zniknie z ekranu.  
  
 W poniższej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tabeli wymieniono zdarzenia, które muszą być obsługiwane przez wszystkie formanty menu. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zdarzenie|Wsparcie/wartość|Uwagi|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie, które uległo zmianie właściwości.|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagany|Brak|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagany|Brak|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType.Menu>
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Typy kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
