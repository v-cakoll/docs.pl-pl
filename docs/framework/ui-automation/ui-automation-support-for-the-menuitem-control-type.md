---
title: Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem
description: Uzyskaj informacje na temat obsługi automatyzacji interfejsu użytkownika dla typu formantu MenuItem. Poznaj wymaganą strukturę drzewa, właściwości, wzorce formantów i zdarzenia.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
ms.openlocfilehash: 248fdacee42c3a67c6c3b2d5792b774dfdc8408f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166016"
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem

> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).

Ten temat zawiera informacje [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] na temat obsługi typu formantu MenuItem. Opisuje ona [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] strukturę drzewa kontrolki i udostępnia właściwości i wzorce kontrolki, które są wymagane dla typu formantu MenuItem.

Kontrolka menu umożliwia hierarchiczna organizacji elementów skojarzonych z poleceniami i programami obsługi zdarzeń. W typowej aplikacji systemu Microsoft Windows pasek menu zawiera kilka elementów menu (takich jak **plik**, **Edycja**i **okno**), a każdy element menu wyświetla menu. Menu zawiera kolekcję elementów menu (takich jak **New**, **Open**i **Close**), które można rozszerzyć, aby wyświetlić dodatkowe elementy menu, lub wykonać określoną akcję po kliknięciu. Element menu może być hostowany w menu, pasku menu lub pasku narzędzi.

W poniższych sekcjach opisano wymaganą [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strukturę drzewa, właściwości, wzorce formantów i zdarzenia dla typu formantu MenuItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wymagania stosują się do wszystkich kontrolek listy, zarówno [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] systemu Win32, jak i Windows Forms.

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Wymagana struktura drzewa automatyzacji interfejsu użytkownika

W poniższej tabeli przedstawiono widok kontrolki i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, które odnoszą się do kontrolek elementów menu, i opisano, co może być zawarte w poszczególnych widokach. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [drzewo automatyzacji interfejsu użytkownika — omówienie](ui-automation-tree-overview.md).

|Widok kontrolki|Widok zawartości|
|------------------|------------------|
|MenuItem — pomoc<br /><br /> <ul><li>Menu (podmenu elementu menu Pomoc)<br /><br /> <ul><li>MenuItem — tematy pomocy</li><li>MenuItem "informacje o notatniku"</li></ul></li></ul>|MenuItem — pomoc<br /><br /> -MenuItem "Tematy pomocy"<br />-MenuItem "informacje o notatniku"|

Widok kontrolki kontrolki elementu menu zawiera [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokazany powyżej strukturę drzewa. Należy zauważyć, że element menu **Pomoc** jest uwzględniany w celu lepszego zilustrowania struktury w typowym menu w hierarchii podmenu.

W widoku zawartości menu nie jest obecne w drzewie, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ponieważ nie przekazuje użytkownikowi końcowemu istotnych informacji.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Wymagane właściwości automatyzacji interfejsu użytkownika

Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, których wartość lub definicja jest szczególnie istotna dla kontrolek elementu menu. Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](ui-automation-properties-for-clients.md).

|Właściwość|Wartość|Opis|
|--------------|-----------|-----------------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Zobacz uwagi.|Wartość tej właściwości musi być unikatowa dla wszystkich kontrolek w aplikacji.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Zobacz uwagi.|Najbardziej zewnętrzny prostokąt, który zawiera cały formant.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobacz uwagi.|Obsługiwane, jeśli istnieje prostokąt ograniczający. Jeśli nie każdy punkt wewnątrz prostokąta ograniczenia jest klikany, a będziesz wykonywał wyspecjalizowane Testy trafień, a następnie przesłonić i udostępnić punkt kliknięcia.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Zobacz uwagi.|Jeśli formant może odbierać fokus klawiatury, musi obsługiwać tę właściwość.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Zobacz uwagi.|Kontrolka element menu jest zawarta w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa i jest przedstawiona przy użyciu nazwy.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Brak etykiety.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|MenuItem|Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"element menu"|Zlokalizowany ciąg odpowiadający typowi formantu MenuItem.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Prawda|Kontrolka element menu nigdy nie jest uwzględniona w widoku zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Prawda|Kontrolka element menu musi być zawsze uwzględniona w widoku kontrolki [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>Wymagane wzorce kontrolek automatyzacji interfejsu użytkownika

Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wzorców formantów wymaganych do obsługi przez formanty elementów menu. Aby uzyskać więcej informacji na temat wzorców kontroli, zobacz [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md).

|Właściwość wzorca kontrolki|Pomoc techniczna|Uwagi|
|------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Zależy od|Jeśli formant może być rozwinięty lub zwinięty, zaimplementuj <xref:System.Windows.Automation.Provider.IExpandCollapseProvider> .|
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Zależy od|Jeśli kontrolka wykonuje pojedynczą akcję lub polecenie, zaimplementuj <xref:System.Windows.Automation.Provider.IInvokeProvider> .|
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Zależy od|Jeśli formant reprezentuje opcję, którą można włączyć lub wyłączyć, zaimplementuj <xref:System.Windows.Automation.Provider.IToggleProvider> .|
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Zależy od|Jeśli formant jest używany do wyboru z listy opcji w elementach menu, zaimplementuj <xref:System.Windows.Automation.Provider.ISelectionItemProvider> .|

<a name="UI_Automation_Events_for_Menu_Item"></a>

## <a name="ui-automation-events-for-menu-item"></a>Zdarzenia automatyzacji interfejsu użytkownika dla elementu menu

Poniższa tabela zawiera listę [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] zdarzeń skojarzonych z formantem elementu menu.

|Wydarzenie|Pomoc techniczna|Wyjaśnienie|
|-----------|-------------|-----------------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Musi być zgłaszane, jeśli formant obsługuje wywoływanie wzorca kontrolki.|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>zdarzenie zmiany właściwości.|Zależy od|Musi być zgłaszane, Jeśli kontrolka obsługuje przełącznik wzorzec kontrolki.|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>zdarzenie zmiany właściwości.|Zależy od|Musi być zgłaszane, jeśli formant obsługuje wzorzec kontrolki Rozwiń Zwiń.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Zależy od|Brak.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Wymagane zdarzenia automatyzacji interfejsu użytkownika

Poniższa tabela zawiera listę [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzeń wymaganych do obsługi przez wszystkie kontrolki elementów menu. Aby uzyskać więcej informacji na temat zdarzeń, zobacz [Omówienie zdarzeń automatyzacji interfejsu użytkownika](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wydarzen|Obsługa/wartość|Uwagi|
|---------------------------------------------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Zależy od|Brak|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Zależy od|Brak|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Zależy od|Brak|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Zależy od|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>zdarzenie zmiany właściwości.|Wymagane|Brak|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>zdarzenie zmiany właściwości.|Zależy od|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Wymagane|Brak|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Wymagane|Brak|

<a name="Legacy_Issues"></a>

## <a name="legacy-issues"></a>Starsze problemy

Przełączenie wzorca będzie obsługiwane tylko wtedy, gdy element menu Win32 zostanie sprawdzony i może być programistycznie określony jako niezbędny do obsługi wzorca przełączania. Ponieważ element menu Win32 nie ujawnia, czy ma możliwość sprawdzenia, funkcja Invoke wzorzec będzie obsługiwana, gdy element menu nie zostanie zaznaczony. Zostanie wykonany wyjątek, aby zawsze obsługiwał wzorzec Invoke nawet dla elementów menu, które powinny obsługiwać tylko wzorzec przełączania. Wynika to z tego, że klienci nie stają się mylić, ponieważ element, który obsługiwał wzorzec Invoke (gdy element menu nie został zaznaczony), nie obsługuje już wzorca, gdy zostanie on sprawdzony.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType.MenuItem>
- [Wzorce formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Typy formantów automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-types-overview.md)
- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
