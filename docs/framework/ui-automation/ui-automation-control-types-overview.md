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
ms.workload: dotnet
ms.openlocfilehash: 39d76b5d68938569fbe2d5e35230ed70737fdecc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-control-types-overview"></a><span data-ttu-id="e71c8-102">Typy kontrolek automatyzacji interfejsu użytkownika — omówienie</span><span class="sxs-lookup"><span data-stu-id="e71c8-102">UI Automation Control Types Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="e71c8-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e71c8-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e71c8-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e71c8-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="e71c8-105">typy formantów są dobrze znane identyfikatory, których można użyć w celu wskazania, jakiego rodzaju kontroli reprezentuje dany element, takich jak pole kombi lub przycisku.</span><span class="sxs-lookup"><span data-stu-id="e71c8-105"> control types are well-known identifiers that can be used to indicate what kind of control a particular element represents, such as a combo box or a button.</span></span>  
  
 <span data-ttu-id="e71c8-106">Posiadanie dobrze znany identyfikator ułatwia ułatwianiem urządzeń ustalić, jakie typy formantów są dostępne w [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] oraz sposoby interakcji z formantami.</span><span class="sxs-lookup"><span data-stu-id="e71c8-106">Having a well-known identifier makes it easier for assistive technology devices to determine what types of controls are available in the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] and how to interact with the controls.</span></span>  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a><span data-ttu-id="e71c8-107">Wymagania typu formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e71c8-107">UI Automation Control Type Requisites</span></span>  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]<span data-ttu-id="e71c8-108">typy formantów udostępniają zestaw warunków, które muszą spełniać dostawców.</span><span class="sxs-lookup"><span data-stu-id="e71c8-108"> control types provide a set of conditions that providers must meet.</span></span> <span data-ttu-id="e71c8-109">Gdy te warunki są spełnione, formantu można używać nazwy typu określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="e71c8-109">When these conditions are met, the control can use the specific control type name.</span></span> <span data-ttu-id="e71c8-110">Każdy typ formantu ma następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="e71c8-110">Each control type has conditions for the following:</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="e71c8-111">kontrolowanie wzorców — wzorce formantów, które muszą być obsługiwane, kontroli wzorce są opcjonalne i które wzorców formantu nie muszą być obsługiwane przez formant.</span><span class="sxs-lookup"><span data-stu-id="e71c8-111"> control patterns—which control patterns must be supported, which control patterns are optional, and which control patterns must not be supported by the control.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="e71c8-112">wartości właściwości — wartości właściwości, które są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e71c8-112"> property values—which property values are supported.</span></span>  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="e71c8-113">Struktura drzewa — wymagane [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury formantu drzewa.</span><span class="sxs-lookup"><span data-stu-id="e71c8-113"> tree structure—the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure for the control.</span></span>  
  
 <span data-ttu-id="e71c8-114">Jeśli formant spełnia warunki dla określonego typu, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> wartość właściwości wskaże, że formant typu.</span><span class="sxs-lookup"><span data-stu-id="e71c8-114">When a control meets the conditions for a particular control type, the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> property value will indicate that control type.</span></span>  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a><span data-ttu-id="e71c8-115">Bieżące typy formantów automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="e71c8-115">Current UI Automation Control Types</span></span>  
 <span data-ttu-id="e71c8-116">Poniższa lista zawiera bieżący zestaw [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] kontrolowanie typów:</span><span class="sxs-lookup"><span data-stu-id="e71c8-116">The following list contains the current set of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] control types:</span></span>  
  
-   [<span data-ttu-id="e71c8-117">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Button</span><span class="sxs-lookup"><span data-stu-id="e71c8-117">UI Automation Support for the Button Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [<span data-ttu-id="e71c8-118">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Calendar</span><span class="sxs-lookup"><span data-stu-id="e71c8-118">UI Automation Support for the Calendar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [<span data-ttu-id="e71c8-119">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu CheckBox</span><span class="sxs-lookup"><span data-stu-id="e71c8-119">UI Automation Support for the CheckBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [<span data-ttu-id="e71c8-120">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ComboBox</span><span class="sxs-lookup"><span data-stu-id="e71c8-120">UI Automation Support for the ComboBox Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [<span data-ttu-id="e71c8-121">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataGrid</span><span class="sxs-lookup"><span data-stu-id="e71c8-121">UI Automation Support for the DataGrid Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [<span data-ttu-id="e71c8-122">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu DataItem</span><span class="sxs-lookup"><span data-stu-id="e71c8-122">UI Automation Support for the DataItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [<span data-ttu-id="e71c8-123">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Document</span><span class="sxs-lookup"><span data-stu-id="e71c8-123">UI Automation Support for the Document Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [<span data-ttu-id="e71c8-124">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Edit</span><span class="sxs-lookup"><span data-stu-id="e71c8-124">UI Automation Support for the Edit Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [<span data-ttu-id="e71c8-125">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Group</span><span class="sxs-lookup"><span data-stu-id="e71c8-125">UI Automation Support for the Group Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [<span data-ttu-id="e71c8-126">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Header</span><span class="sxs-lookup"><span data-stu-id="e71c8-126">UI Automation Support for the Header Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [<span data-ttu-id="e71c8-127">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu HeaderItem</span><span class="sxs-lookup"><span data-stu-id="e71c8-127">UI Automation Support for the HeaderItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [<span data-ttu-id="e71c8-128">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Hyperlink</span><span class="sxs-lookup"><span data-stu-id="e71c8-128">UI Automation Support for the Hyperlink Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [<span data-ttu-id="e71c8-129">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Image</span><span class="sxs-lookup"><span data-stu-id="e71c8-129">UI Automation Support for the Image Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [<span data-ttu-id="e71c8-130">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu List</span><span class="sxs-lookup"><span data-stu-id="e71c8-130">UI Automation Support for the List Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [<span data-ttu-id="e71c8-131">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ListItem</span><span class="sxs-lookup"><span data-stu-id="e71c8-131">UI Automation Support for the ListItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [<span data-ttu-id="e71c8-132">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Menu</span><span class="sxs-lookup"><span data-stu-id="e71c8-132">UI Automation Support for the Menu Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [<span data-ttu-id="e71c8-133">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuBar</span><span class="sxs-lookup"><span data-stu-id="e71c8-133">UI Automation Support for the MenuBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [<span data-ttu-id="e71c8-134">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu MenuItem</span><span class="sxs-lookup"><span data-stu-id="e71c8-134">UI Automation Support for the MenuItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [<span data-ttu-id="e71c8-135">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Pane</span><span class="sxs-lookup"><span data-stu-id="e71c8-135">UI Automation Support for the Pane Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [<span data-ttu-id="e71c8-136">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ProgressBar</span><span class="sxs-lookup"><span data-stu-id="e71c8-136">UI Automation Support for the ProgressBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [<span data-ttu-id="e71c8-137">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu RadioButton</span><span class="sxs-lookup"><span data-stu-id="e71c8-137">UI Automation Support for the RadioButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [<span data-ttu-id="e71c8-138">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ScrollBar</span><span class="sxs-lookup"><span data-stu-id="e71c8-138">UI Automation Support for the ScrollBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [<span data-ttu-id="e71c8-139">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Separator</span><span class="sxs-lookup"><span data-stu-id="e71c8-139">UI Automation Support for the Separator Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [<span data-ttu-id="e71c8-140">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Suwak</span><span class="sxs-lookup"><span data-stu-id="e71c8-140">UI Automation Support for the Slider Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [<span data-ttu-id="e71c8-141">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Spinner</span><span class="sxs-lookup"><span data-stu-id="e71c8-141">UI Automation Support for the Spinner Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [<span data-ttu-id="e71c8-142">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu SplitButton</span><span class="sxs-lookup"><span data-stu-id="e71c8-142">UI Automation Support for the SplitButton Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [<span data-ttu-id="e71c8-143">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu StatusBar</span><span class="sxs-lookup"><span data-stu-id="e71c8-143">UI Automation Support for the StatusBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [<span data-ttu-id="e71c8-144">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tab</span><span class="sxs-lookup"><span data-stu-id="e71c8-144">UI Automation Support for the Tab Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [<span data-ttu-id="e71c8-145">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TabItem</span><span class="sxs-lookup"><span data-stu-id="e71c8-145">UI Automation Support for the TabItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [<span data-ttu-id="e71c8-146">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Table</span><span class="sxs-lookup"><span data-stu-id="e71c8-146">UI Automation Support for the Table Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [<span data-ttu-id="e71c8-147">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Text</span><span class="sxs-lookup"><span data-stu-id="e71c8-147">UI Automation Support for the Text Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [<span data-ttu-id="e71c8-148">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Thumb</span><span class="sxs-lookup"><span data-stu-id="e71c8-148">UI Automation Support for the Thumb Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [<span data-ttu-id="e71c8-149">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TitleBar</span><span class="sxs-lookup"><span data-stu-id="e71c8-149">UI Automation Support for the TitleBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [<span data-ttu-id="e71c8-150">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolBar</span><span class="sxs-lookup"><span data-stu-id="e71c8-150">UI Automation Support for the ToolBar Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [<span data-ttu-id="e71c8-151">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu ToolTip</span><span class="sxs-lookup"><span data-stu-id="e71c8-151">UI Automation Support for the ToolTip Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [<span data-ttu-id="e71c8-152">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Tree</span><span class="sxs-lookup"><span data-stu-id="e71c8-152">UI Automation Support for the Tree Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [<span data-ttu-id="e71c8-153">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu TreeItem</span><span class="sxs-lookup"><span data-stu-id="e71c8-153">UI Automation Support for the TreeItem Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [<span data-ttu-id="e71c8-154">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu Window</span><span class="sxs-lookup"><span data-stu-id="e71c8-154">UI Automation Support for the Window Control Type</span></span>](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a><span data-ttu-id="e71c8-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e71c8-155">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType>
