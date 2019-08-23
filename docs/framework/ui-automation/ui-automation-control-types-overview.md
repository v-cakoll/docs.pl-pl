---
title: Typy formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 5274a2a090669a9c51c5247b68d2b0460625a494
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911568"
---
# <a name="ui-automation-control-types-overview"></a>Typy formantów automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Typy formantów to dobrze znane identyfikatory, których można użyć do wskazania rodzaju kontrolki, która reprezentuje określony element, na przykład pole kombi lub przycisk.  
  
 Dobrze znany identyfikator ułatwia urządzeniom technologii pomocniczych Określanie, jakie typy formantów są dostępne w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i jak korzystać z formantów.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>Wymagania dotyczące typów formantów automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Typy formantów zapewniają zestaw warunków, które muszą spełniać dostawcy. Po spełnieniu tych warunków formant może używać konkretnej nazwy typu formantu. Każdy typ formantu ma następujące warunki:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wzorce formantów — które wzorce kontroli muszą być obsługiwane, które wzorce kontroli są opcjonalne i które wzorce kontroli nie mogą być obsługiwane przez formant.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wartości właściwości — wartości właściwości są obsługiwane.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Struktura drzewa — wymagana [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktura drzewa dla kontrolki.  
  
 Gdy kontrolka spełnia warunki określonego typu formantu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> wartość właściwości będzie wskazywać ten typ formantu.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Bieżące typy kontrolek automatyzacji interfejsu użytkownika  
 Poniższa lista zawiera bieżący zestaw [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typów formantów:  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Button](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Calendar](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataGrid](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Document](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Edit](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Group](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Header](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu HeaderItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Hyperlink](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Image](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu List](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ListItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Menu](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Pane](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu RadioButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Separator](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Suwak](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Spinner](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tab](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TabItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Table](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Text](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Thumb](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TitleBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolTip](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tree](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Window](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType>
