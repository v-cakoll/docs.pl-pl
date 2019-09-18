---
title: Typy formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 3c53d07cc6ebbd5259a4bfb5224c486481167c10
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71042232"
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
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Button](ui-automation-support-for-the-button-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Calendar](ui-automation-support-for-the-calendar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox](ui-automation-support-for-the-combobox-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataGrid](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Document](ui-automation-support-for-the-document-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Edit](ui-automation-support-for-the-edit-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Group](ui-automation-support-for-the-group-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Header](ui-automation-support-for-the-header-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu HeaderItem](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Hyperlink](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Image](ui-automation-support-for-the-image-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu List](ui-automation-support-for-the-list-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ListItem](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Menu](ui-automation-support-for-the-menu-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuBar](ui-automation-support-for-the-menubar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Pane](ui-automation-support-for-the-pane-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu RadioButton](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Separator](ui-automation-support-for-the-separator-control-type.md)  
  
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
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TreeItem](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Window](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType>
