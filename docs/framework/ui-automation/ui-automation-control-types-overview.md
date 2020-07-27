---
title: Typy formantów automatyzacji interfejsu użytkownika — omówienie
description: Zapoznaj się z omówieniem typów formantów automatyzacji interfejsu użytkownika, które są dobrze znane identyfikatory, których można użyć do wskazania rodzaju kontroli reprezentowanej przez element.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: 204e950fca74c4f7bd2c13dc8a8891152954c071
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166138"
---
# <a name="ui-automation-control-types-overview"></a>Typy formantów automatyzacji interfejsu użytkownika — omówienie
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Typy formantów to dobrze znane identyfikatory, których można użyć do wskazania rodzaju kontrolki, która reprezentuje określony element, na przykład pole kombi lub przycisk.  
  
 Dobrze znany identyfikator ułatwia urządzeniom technologii pomocniczych Określanie, jakie typy formantów są dostępne w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i jak korzystać z formantów.  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a>Wymagania dotyczące typów formantów automatyzacji interfejsu użytkownika  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]Typy formantów zapewniają zestaw warunków, które muszą spełniać dostawcy. Po spełnieniu tych warunków formant może używać konkretnej nazwy typu formantu. Każdy typ formantu ma następujące warunki:  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Wzorce formantów — które wzorce kontroli muszą być obsługiwane, które wzorce kontroli są opcjonalne i które wzorce kontroli nie mogą być obsługiwane przez formant.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]wartości właściwości — wartości właściwości są obsługiwane.  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Struktura drzewa — wymagana [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Struktura drzewa dla kontrolki.  
  
 Gdy kontrolka spełnia warunki określonego typu formantu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> wartość właściwości będzie wskazywać ten typ formantu.  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a>Bieżące typy kontrolek automatyzacji interfejsu użytkownika  
 Poniższa lista zawiera bieżący zestaw [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typów formantów:  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk](ui-automation-support-for-the-button-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz](ui-automation-support-for-the-calendar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox](ui-automation-support-for-the-combobox-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu dokument](ui-automation-support-for-the-document-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja](ui-automation-support-for-the-edit-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu grupa](ui-automation-support-for-the-group-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu nagłówek](ui-automation-support-for-the-header-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu HeaderItem](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla formantów typu hiperłącze](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla formantów typu obraz](ui-automation-support-for-the-image-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista](ui-automation-support-for-the-list-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem](ui-automation-support-for-the-listitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu menu](ui-automation-support-for-the-menu-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu MenuBar](ui-automation-support-for-the-menubar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu okienko](ui-automation-support-for-the-pane-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu RadioButton](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla formantów typu separator](ui-automation-support-for-the-separator-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu suwak](ui-automation-support-for-the-slider-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla formantów typu pokrętło](ui-automation-support-for-the-spinner-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla formantów typu karta](ui-automation-support-for-the-tab-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu TabItem](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu tabela](ui-automation-support-for-the-table-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu tekst](ui-automation-support-for-the-text-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu miniatura](ui-automation-support-for-the-thumb-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu TitleBar](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu formantu ToolTip](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla formantów typu drzewo](ui-automation-support-for-the-tree-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla typu kontrolki TreeItem](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu okno](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.ControlType>
