---
title: Typy formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 8269e93e3ce1d47509505bf1868afce62527a89c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680090"
---
# <a name="ui-automation-control-types-overview"></a>Typy formantów automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typy formantów są dobrze znane identyfikatory, które może służyć do wskazania, jakiego rodzaju formantu reprezentuje określony element, takie jak pola kombi lub przycisku.  
  
 Posiadanie dobrze znanego identyfikatora ułatwia urządzeń technologii pomocniczej ustalić, jakie rodzaje formantów są dostępne w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i sposób interakcji z kontrolkami.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>Wymagania typu kontrolki automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typy kontrolek zapewniają zestaw warunków, które muszą spełniać dostawców. Gdy te warunki są spełnione, kontrolki można używać nazwy typu określonego formantu. Każdy typ kontrolki ma następujące warunki:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolowanie wzorce — wzorców kontrolek, które muszą być obsługiwane, które określają wzorce są opcjonalne i wzorców kontrolek, które nie muszą być obsługiwane przez kontrolkę.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości — wartości właściwości, które są obsługiwane.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Struktura drzewa — wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury dla formantu drzewa.  
  
 Gdy formant spełnia warunki dla określonego typu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> wartość właściwości będą wskazywać tę kontrolkę typu.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Bieżące typy kontrolek automatyzacji interfejsu użytkownika  
 Poniższa lista zawiera bieżący zestaw [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolować typów:  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Button](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Calendar](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataGrid](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Document](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Edit](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Group](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Header](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu HeaderItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Hyperlink](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Image](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu List](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ListItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Menu](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Pane](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu RadioButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Separator](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Suwak](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Spinner](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tab](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TabItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Table](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Text](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Thumb](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TitleBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolTip](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tree](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Window](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Automation.ControlType>
