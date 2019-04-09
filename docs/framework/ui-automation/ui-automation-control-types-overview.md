---
title: Typy formantów automatyzacji interfejsu użytkownika — omówienie
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: e9cbff2ec6496cabe827e075b737a8c6f16fee93
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147722"
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
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu dokument](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu grupa](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu nagłówek](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu HeaderItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu hiperłącze](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu obraz](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu menu](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu MenuBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu okienko](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu RadioButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu separator](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu suwak](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu pokrętło](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu karta](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu TabItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu tabela](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu tekst](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu miniatura](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu TitleBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ToolTip](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu drzewo](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu kontrolki TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu okno](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType>
