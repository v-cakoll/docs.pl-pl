---
title: Typy formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 643c89e8f6c5e34aa1fb3c5c7c6c750c72046277
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179937"
---
# <a name="ui-automation-control-types-overview"></a>Typy formantów automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]typy formantu są dobrze znane identyfikatory, które mogą służyć do wskazania, jaki rodzaj kontroli reprezentuje określonego elementu, takich jak pole kombi lub przycisk.  
  
 Posiadanie dobrze znanego identyfikatora ułatwia urządzeniom technologii ułatwionych określenie, jakie typy [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] formantów są dostępne w formancie i jak wchodzić w interakcje z formantami.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a>Wymagania typu kontroli automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]typy kontroli zapewniają zestaw warunków, które dostawcy muszą spełniać. Po spełnieniu tych warunków formant może użyć nazwy określonego typu formantu. Każdy typ formantu ma warunki dla następujących:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wzorce sterowania — które wzorce sterowania muszą być obsługiwane, które wzorce sterowania są opcjonalne i które wzorce sterowania nie mogą być obsługiwane przez formant.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wartości właściwości — które wartości właściwości są obsługiwane.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]struktura drzewa — [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wymagana struktura drzewa dla formantu.  
  
 Gdy formant spełnia warunki dla określonego <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> typu formantu, wartość właściwości wskazuje ten typ formantu.  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a>Bieżące typy sterowania automatyzacją interfejsu użytkownika  
 Poniższa lista zawiera bieżący zestaw typów formantów: [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Button](ui-automation-support-for-the-button-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Calendar](ui-automation-support-for-the-calendar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox](ui-automation-support-for-the-combobox-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Document](ui-automation-support-for-the-document-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Edit](ui-automation-support-for-the-edit-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Group](ui-automation-support-for-the-group-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Header](ui-automation-support-for-the-header-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu HeaderItem](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Hyperlink](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Image](ui-automation-support-for-the-image-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista](ui-automation-support-for-the-list-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Menu](ui-automation-support-for-the-menu-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuBar](ui-automation-support-for-the-menubar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Pane](ui-automation-support-for-the-pane-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu RadioButton](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla formantów typu separator](ui-automation-support-for-the-separator-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Suwak](ui-automation-support-for-the-slider-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Spinner](ui-automation-support-for-the-spinner-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tab](ui-automation-support-for-the-tab-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TabItem](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Table](ui-automation-support-for-the-table-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Text](ui-automation-support-for-the-text-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Thumb](ui-automation-support-for-the-thumb-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TitleBar](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolTip](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tree](ui-automation-support-for-the-tree-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu kontrolki TreeItem](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Window](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Automation.ControlType>
