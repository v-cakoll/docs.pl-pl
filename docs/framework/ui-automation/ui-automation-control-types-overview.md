---
title: "Typy formantów automatyzacji interfejsu użytkownika — omówienie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c1a424f05f2d57f773e8367e102f553d69b7dc22
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-control-types-overview"></a>Typy kontrolek automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]typy formantów są dobrze znane identyfikatory, których można użyć w celu wskazania, jakiego rodzaju kontroli reprezentuje dany element, takich jak pole kombi lub przycisku.  
  
 Posiadanie dobrze znany identyfikator ułatwia ułatwianiem urządzeń ustalić, jakie typy formantów są dostępne w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] oraz sposoby interakcji z formantami.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>Wymagania typu formantu automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]typy formantów udostępniają zestaw warunków, które muszą spełniać dostawców. Gdy te warunki są spełnione, formantu można używać nazwy typu określonego formantu. Każdy typ formantu ma następujące warunki:  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]kontrolowanie wzorców — wzorce formantów, które muszą być obsługiwane, kontroli wzorce są opcjonalne i które wzorców formantu nie muszą być obsługiwane przez formant.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wartości właściwości — wartości właściwości, które są obsługiwane.  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Struktura drzewa — wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury formantu drzewa.  
  
 Jeśli formant spełnia warunki dla określonego typu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> wartość właściwości wskaże, że formant typu.  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>Bieżące typy formantów automatyzacji interfejsu użytkownika  
 Poniższa lista zawiera bieżący zestaw [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolowanie typów:  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu przycisk](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu CheckBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu dokument](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu Edycja](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu Grupa](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu Nagłówek](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu HeaderItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu hiperłącze](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu obraz](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu Lista](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu Menu](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu MenuBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu MenuItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu okienko](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ProgressBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu RadioButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ScrollBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu Separator](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu suwak](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu pokrętło](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu SplitButton](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu StatusBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu karta](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu TabItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu Tabela](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu tekst](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu Miniatura](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu TitleBar](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu paska narzędzi](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ToolTip](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu drzewa](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla typu formantu TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [Obsługa automatyzacji interfejsu użytkownika dla formantów typu okno](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.ControlType>
