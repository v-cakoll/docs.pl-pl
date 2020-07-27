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
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="4ffe0-103">Typy formantów automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="4ffe0-103">UI Automation Control Types Overview</span></span>
> [!NOTE]
> <span data-ttu-id="4ffe0-104">Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="4ffe0-105">Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="4ffe0-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="4ffe0-106">Typy formantów to dobrze znane identyfikatory, których można użyć do wskazania rodzaju kontrolki, która reprezentuje określony element, na przykład pole kombi lub przycisk.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-106">control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="4ffe0-107">Dobrze znany identyfikator ułatwia urządzeniom technologii pomocniczych Określanie, jakie typy formantów są dostępne w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] i jak korzystać z formantów.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-107">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="4ffe0-108">Wymagania dotyczące typów formantów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4ffe0-108">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="4ffe0-109">Typy formantów zapewniają zestaw warunków, które muszą spełniać dostawcy.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-109">control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="4ffe0-110">Po spełnieniu tych warunków formant może używać konkretnej nazwy typu formantu.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-110">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="4ffe0-111">Każdy typ formantu ma następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="4ffe0-111">Each control type has conditions for the following:</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="4ffe0-112">Wzorce formantów — które wzorce kontroli muszą być obsługiwane, które wzorce kontroli są opcjonalne i które wzorce kontroli nie mogą być obsługiwane przez formant.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-112">control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="4ffe0-113">wartości właściwości — wartości właściwości są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-113">property values—which property values are supported.</span></span>  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="4ffe0-114">Struktura drzewa — wymagana [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Struktura drzewa dla kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-114">tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="4ffe0-115">Gdy kontrolka spełnia warunki określonego typu formantu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> wartość właściwości będzie wskazywać ten typ formantu.</span><span class="sxs-lookup"><span data-stu-id="4ffe0-115">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="4ffe0-116">Bieżące typy kontrolek automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="4ffe0-116">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="4ffe0-117">Poniższa lista zawiera bieżący zestaw [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] typów formantów:</span><span class="sxs-lookup"><span data-stu-id="4ffe0-117">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
- [<span data-ttu-id="4ffe0-118">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk</span><span class="sxs-lookup"><span data-stu-id="4ffe0-118">UI Automation Support for the Button Control Type</span></span>](ui-automation-support-for-the-button-control-type.md)  
  
- [<span data-ttu-id="4ffe0-119">Obsługa automatyzacji interfejsu użytkownika dla formantów typu kalendarz</span><span class="sxs-lookup"><span data-stu-id="4ffe0-119">UI Automation Support for the Calendar Control Type</span></span>](ui-automation-support-for-the-calendar-control-type.md)  
  
- [<span data-ttu-id="4ffe0-120">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox</span><span class="sxs-lookup"><span data-stu-id="4ffe0-120">UI Automation Support for the CheckBox Control Type</span></span>](ui-automation-support-for-the-checkbox-control-type.md)  
  
- [<span data-ttu-id="4ffe0-121">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ComboBox</span><span class="sxs-lookup"><span data-stu-id="4ffe0-121">UI Automation Support for the ComboBox Control Type</span></span>](ui-automation-support-for-the-combobox-control-type.md)  
  
- [<span data-ttu-id="4ffe0-122">Obsługa automatyzacji interfejsu użytkownika dla typu formantu DataGrid</span><span class="sxs-lookup"><span data-stu-id="4ffe0-122">UI Automation Support for the DataGrid Control Type</span></span>](ui-automation-support-for-the-datagrid-control-type.md)  
  
- [<span data-ttu-id="4ffe0-123">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem</span><span class="sxs-lookup"><span data-stu-id="4ffe0-123">UI Automation Support for the DataItem Control Type</span></span>](ui-automation-support-for-the-dataitem-control-type.md)  
  
- [<span data-ttu-id="4ffe0-124">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu dokument</span><span class="sxs-lookup"><span data-stu-id="4ffe0-124">UI Automation Support for the Document Control Type</span></span>](ui-automation-support-for-the-document-control-type.md)  
  
- [<span data-ttu-id="4ffe0-125">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu edycja</span><span class="sxs-lookup"><span data-stu-id="4ffe0-125">UI Automation Support for the Edit Control Type</span></span>](ui-automation-support-for-the-edit-control-type.md)  
  
- [<span data-ttu-id="4ffe0-126">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu grupa</span><span class="sxs-lookup"><span data-stu-id="4ffe0-126">UI Automation Support for the Group Control Type</span></span>](ui-automation-support-for-the-group-control-type.md)  
  
- [<span data-ttu-id="4ffe0-127">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu nagłówek</span><span class="sxs-lookup"><span data-stu-id="4ffe0-127">UI Automation Support for the Header Control Type</span></span>](ui-automation-support-for-the-header-control-type.md)  
  
- [<span data-ttu-id="4ffe0-128">Obsługa automatyzacji interfejsu użytkownika dla typu formantu HeaderItem</span><span class="sxs-lookup"><span data-stu-id="4ffe0-128">UI Automation Support for the HeaderItem Control Type</span></span>](ui-automation-support-for-the-headeritem-control-type.md)  
  
- [<span data-ttu-id="4ffe0-129">Obsługa automatyzacji interfejsu użytkownika dla formantów typu hiperłącze</span><span class="sxs-lookup"><span data-stu-id="4ffe0-129">UI Automation Support for the Hyperlink Control Type</span></span>](ui-automation-support-for-the-hyperlink-control-type.md)  
  
- [<span data-ttu-id="4ffe0-130">Obsługa automatyzacji interfejsu użytkownika dla formantów typu obraz</span><span class="sxs-lookup"><span data-stu-id="4ffe0-130">UI Automation Support for the Image Control Type</span></span>](ui-automation-support-for-the-image-control-type.md)  
  
- [<span data-ttu-id="4ffe0-131">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu lista</span><span class="sxs-lookup"><span data-stu-id="4ffe0-131">UI Automation Support for the List Control Type</span></span>](ui-automation-support-for-the-list-control-type.md)  
  
- [<span data-ttu-id="4ffe0-132">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ListItem</span><span class="sxs-lookup"><span data-stu-id="4ffe0-132">UI Automation Support for the ListItem Control Type</span></span>](ui-automation-support-for-the-listitem-control-type.md)  
  
- [<span data-ttu-id="4ffe0-133">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu menu</span><span class="sxs-lookup"><span data-stu-id="4ffe0-133">UI Automation Support for the Menu Control Type</span></span>](ui-automation-support-for-the-menu-control-type.md)  
  
- [<span data-ttu-id="4ffe0-134">Obsługa automatyzacji interfejsu użytkownika dla typu formantu MenuBar</span><span class="sxs-lookup"><span data-stu-id="4ffe0-134">UI Automation Support for the MenuBar Control Type</span></span>](ui-automation-support-for-the-menubar-control-type.md)  
  
- [<span data-ttu-id="4ffe0-135">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem</span><span class="sxs-lookup"><span data-stu-id="4ffe0-135">UI Automation Support for the MenuItem Control Type</span></span>](ui-automation-support-for-the-menuitem-control-type.md)  
  
- [<span data-ttu-id="4ffe0-136">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu okienko</span><span class="sxs-lookup"><span data-stu-id="4ffe0-136">UI Automation Support for the Pane Control Type</span></span>](ui-automation-support-for-the-pane-control-type.md)  
  
- [<span data-ttu-id="4ffe0-137">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar</span><span class="sxs-lookup"><span data-stu-id="4ffe0-137">UI Automation Support for the ProgressBar Control Type</span></span>](ui-automation-support-for-the-progressbar-control-type.md)  
  
- [<span data-ttu-id="4ffe0-138">Obsługa automatyzacji interfejsu użytkownika dla typu formantu RadioButton</span><span class="sxs-lookup"><span data-stu-id="4ffe0-138">UI Automation Support for the RadioButton Control Type</span></span>](ui-automation-support-for-the-radiobutton-control-type.md)  
  
- [<span data-ttu-id="4ffe0-139">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar</span><span class="sxs-lookup"><span data-stu-id="4ffe0-139">UI Automation Support for the ScrollBar Control Type</span></span>](ui-automation-support-for-the-scrollbar-control-type.md)  
  
- [<span data-ttu-id="4ffe0-140">Obsługa automatyzacji interfejsu użytkownika dla formantów typu separator</span><span class="sxs-lookup"><span data-stu-id="4ffe0-140">UI Automation Support for the Separator Control Type</span></span>](ui-automation-support-for-the-separator-control-type.md)  
  
- [<span data-ttu-id="4ffe0-141">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu suwak</span><span class="sxs-lookup"><span data-stu-id="4ffe0-141">UI Automation Support for the Slider Control Type</span></span>](ui-automation-support-for-the-slider-control-type.md)  
  
- [<span data-ttu-id="4ffe0-142">Obsługa automatyzacji interfejsu użytkownika dla formantów typu pokrętło</span><span class="sxs-lookup"><span data-stu-id="4ffe0-142">UI Automation Support for the Spinner Control Type</span></span>](ui-automation-support-for-the-spinner-control-type.md)  
  
- [<span data-ttu-id="4ffe0-143">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton</span><span class="sxs-lookup"><span data-stu-id="4ffe0-143">UI Automation Support for the SplitButton Control Type</span></span>](ui-automation-support-for-the-splitbutton-control-type.md)  
  
- [<span data-ttu-id="4ffe0-144">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar</span><span class="sxs-lookup"><span data-stu-id="4ffe0-144">UI Automation Support for the StatusBar Control Type</span></span>](ui-automation-support-for-the-statusbar-control-type.md)  
  
- [<span data-ttu-id="4ffe0-145">Obsługa automatyzacji interfejsu użytkownika dla formantów typu karta</span><span class="sxs-lookup"><span data-stu-id="4ffe0-145">UI Automation Support for the Tab Control Type</span></span>](ui-automation-support-for-the-tab-control-type.md)  
  
- [<span data-ttu-id="4ffe0-146">Obsługa automatyzacji interfejsu użytkownika dla typu formantu TabItem</span><span class="sxs-lookup"><span data-stu-id="4ffe0-146">UI Automation Support for the TabItem Control Type</span></span>](ui-automation-support-for-the-tabitem-control-type.md)  
  
- [<span data-ttu-id="4ffe0-147">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu tabela</span><span class="sxs-lookup"><span data-stu-id="4ffe0-147">UI Automation Support for the Table Control Type</span></span>](ui-automation-support-for-the-table-control-type.md)  
  
- [<span data-ttu-id="4ffe0-148">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu tekst</span><span class="sxs-lookup"><span data-stu-id="4ffe0-148">UI Automation Support for the Text Control Type</span></span>](ui-automation-support-for-the-text-control-type.md)  
  
- [<span data-ttu-id="4ffe0-149">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu miniatura</span><span class="sxs-lookup"><span data-stu-id="4ffe0-149">UI Automation Support for the Thumb Control Type</span></span>](ui-automation-support-for-the-thumb-control-type.md)  
  
- [<span data-ttu-id="4ffe0-150">Obsługa automatyzacji interfejsu użytkownika dla typu formantu TitleBar</span><span class="sxs-lookup"><span data-stu-id="4ffe0-150">UI Automation Support for the TitleBar Control Type</span></span>](ui-automation-support-for-the-titlebar-control-type.md)  
  
- [<span data-ttu-id="4ffe0-151">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar</span><span class="sxs-lookup"><span data-stu-id="4ffe0-151">UI Automation Support for the ToolBar Control Type</span></span>](ui-automation-support-for-the-toolbar-control-type.md)  
  
- [<span data-ttu-id="4ffe0-152">Obsługa automatyzacji interfejsu użytkownika dla typu formantu ToolTip</span><span class="sxs-lookup"><span data-stu-id="4ffe0-152">UI Automation Support for the ToolTip Control Type</span></span>](ui-automation-support-for-the-tooltip-control-type.md)  
  
- [<span data-ttu-id="4ffe0-153">Obsługa automatyzacji interfejsu użytkownika dla formantów typu drzewo</span><span class="sxs-lookup"><span data-stu-id="4ffe0-153">UI Automation Support for the Tree Control Type</span></span>](ui-automation-support-for-the-tree-control-type.md)  
  
- [<span data-ttu-id="4ffe0-154">Obsługa automatyzacji interfejsu użytkownika dla typu kontrolki TreeItem</span><span class="sxs-lookup"><span data-stu-id="4ffe0-154">UI Automation Support for the TreeItem Control Type</span></span>](ui-automation-support-for-the-treeitem-control-type.md)  
  
- [<span data-ttu-id="4ffe0-155">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu okno</span><span class="sxs-lookup"><span data-stu-id="4ffe0-155">UI Automation Support for the Window Control Type</span></span>](ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="4ffe0-156">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ffe0-156">See also</span></span>

- <xref:System.Windows.Automation.ControlType>
